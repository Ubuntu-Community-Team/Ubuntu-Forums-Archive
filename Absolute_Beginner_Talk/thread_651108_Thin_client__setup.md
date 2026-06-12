---
title: "Thin client  setup"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by William S on 2007-12-27
Hello
I am trying to set up a thin client machine just for testing using Edubuntu, to be honest it is an Ubuntu machine where I have downloaded the server from Synaptic. 
But the problem  is that my server wouldn't start, I am using the instructions provided by the Edubuntu website except I don't have two network cards on my server as I got both plugged into the router and Internet. I am just using the default configuration file as you can see because when I change it to the settings which suits my networking (IP adresses etc) it didn't like that at all so I changed it back to default, and it just says failed when it tries to start the server. 
```

# Default LTSP dhcpd.conf config file.
#
authoritative;

    subnet 192.168.0.0 netmask 255.255.255.0 {
      range 192.168.0.20 192.168.0.250;
      option domain-name "example.com";
      option domain-name-servers 192.168.0.1;
      option broadcast-address 192.168.0.255;
      option routers 192.168.0.1;

      option subnet-mask 255.255.255.0;

    filename "/ltsp/pxelinux.0";
    option root-path "/opt/ltsp/i386";
    }
]
```

---

### Post by William S on 2007-12-28
Any ideas?

---

