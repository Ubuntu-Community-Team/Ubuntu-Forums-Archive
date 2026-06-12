---
title: "Pidgin and Moblock"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by Ohwii on 2008-02-10
Hi Guys ,

i just installed moblock and I am using it. 
The problem is that cannot use pidgin anymore. 
I checked out the link at the bottom and added the ports to the Whitelist(?) , but it does not work. 
Could anyone tell what else I have to do so that pidgin would work with moblock on. 

that would really help, 

Thanks,

Oh WII

***************************
Link : [Pidgin and Moblock]("http://ubuntuforums.org/showthread.php?t=640077")


```
############################### Whitelist ports ###############################

# Whitelist ports by port number or with the associated service name
# (using iptables with the target RETURN)
# Seperate several entries with whitespace (" ")
# Port ranges are specified in the format "port:port"
# Up to 15 ports can be specified. A port range (port:port) counts as two
# ports.

# This section works only for IPTABLES_SETTINGS="1"
# Do a "moblock-control restart" when you have changed these settings.

WHITE_TCP_IN=""
WHITE_UDP_IN=""
WHITE_TCP_OUT=""
WHITE_UDP_OUT=""
# This is an example to whitelist outgoing web traffic (port 80 is the service
# http, 443 is https) and the port range 1000-1024:
WHITE_TCP_OUT="80 443 1000:1024 5190 1863"
WHITE_TCP_FORWARD=""
WHITE_UDP_FORWARD=""
```

---

### Post by cuby on 2008-02-11
moblock blocks connections from/to hosts listed in a file in peerguardian format.... The IPs of the messaging servers may be on that list, hence pidgin won't work... 
You need to find and remove them from the list.

note: if the IP of one of your buddies is listed there, you will be unable to communicate with him.

---

