# arpnamer
Arpnamer is a layer 2 network scanner used to log  mac, vender, ip address and dns names.
It can output its data to local or remote syslog, a text file or a json file.
Supports scanning multiple interfaces on different networks.

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. See deployment for notes on how to deploy the project on a live system.

### Prerequisites
* CentOS 7 physical or virtual machine attached to one or many network segments
* "arp-scan" package from the [EPEL](https://fedoraproject.org/wiki/EPEL)
* "bind-utils" package which is found in your default CentOS repository


```
## RHEL/CentOS 7 64-Bit ##
# wget http://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
# yum install epel-release-latest-7.noarch.rpm -y
# yum clean all
# yum install arp-scan -y
# yum install bind-utils -y
```

### Installing
* Clone the repository
```
git clone https://github.com/panaman/arpnamer.git
```
* Change into the arpnamer directory
```
cd arpnamer
```
* Run the installer (requires full sudo or run as root)
```
sudo bash install-arpnamer
```
* Review/Edit the config file as needed
/etc/arpnamer/arpnamer.conf

* Enable the arpnamer service
```
sudo systemctl enable arpnamer
```
* Start the arpnamer service
```
sudo systemctl start arpnamer
```

Example output file
/opt/arpnamer/output/arpnames.txt
```
2018-01-17T20:29:57	cisco.panaman.org	10.0.0.2	00:13:4c:8d:47:ff	Cisco Systems, Inc
2018-01-17T20:29:57	server1.panaman.org	10.0.0.4	00:50:56:6a:8b:5d	VMware, Inc.
2018-01-17T20:29:57	mac.panaman.org		10.0.0.5	00:6d:04:63:bc:2f	Apple, Inc.
```
Syslog and json output are written to /var/log/arpnamer directory

### Upgrading
Same process as installing. Installer will not overwrite your config file, instead it will just create a new one "/etc/arpnamer/arpnamer.conf.new"
You should review the new config file with your current and merge any needed changes.

## Authors

* **Panaman** - *Initial work* - [Panaman](https://github.com/panaman)

## License

This project is licensed under the MIT License - see the [LICENSE](https://github.com/panaman/arpnamer/blob/master/LICENSE) file for details
