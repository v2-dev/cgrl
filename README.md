# CGRL
The project required the emulation of a network in the image below using the Netkit platform.


![Image of Network](https://raw.githubusercontent.com/v2-dev/cgrl/master/network.png)


## Addressing 

LAN1:	
  10.0.0.0/24	

LAN2:	
  10.0.1.0/24	
  
LAN3:	
  10.0.2.0/24	
  
DMZ:	
  160.80.103.0/24	
  
p2p-­link:	
  2.34.1.228/31	

Other configurations:

* PCs are configured with DHCP
* servers also use DHCP but with static binding 
* public access to Internet with TAP (be careful with the address you will use on your local machine!)


## NAT 

* Masquerade private LANs
* DNAT for ServerPriv {SSH and port 80}

## Firewall on R1

* Default on DROP
* Unlock all services on DMZ (including ICMP)
* Unlock all the traffic between DMZ and the LANs but only if the traffic is initialized by LANs
* Unlock all the traffic between LANs
* Unlock the following traffic generated from LAN to Internet: WEB, DNS, SSH, ICMP, FTP.
* Unlock the following traffic addressed to R1: SSH and ICMP.

## Server DNS

* 1st level. Choose the domain. DN for all servers.
* DNS is also resolver for the PC configured in DHCP. Queries for external names must be forwarded to other DNS servers.


## SSH server 

* All routers and servers must have an SSH server
* Create a "sysadmin" account on the machines with SSH server. Access with public key to those machines must be configured.


## Server WEB

* Create a HTTPS virtual host (choose name, create certificates)


## ServerPriv

* Default: server WEB Apache 