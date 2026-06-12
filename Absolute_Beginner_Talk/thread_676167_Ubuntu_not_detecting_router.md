---
title: "Ubuntu not detecting router"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by Juran on 2008-01-23
I've downloaded and installed Wubi (Which installed the latest distro of Ubuntu)

And I was hoping to get my internet up and running on it.. Needless to say..

It doesn't detect my modem, or my router. Both of which are ethernet cables.

Any help?

---

### Post by Juran on 2008-01-23
Givin' a little bump!

---

### Post by philinux on 2008-01-23
Boot the live cd to see if get internet access.

---

### Post by Juran on 2008-01-23
I don't have a live-CD?

When I did, it worked and connected to the internet just fine.

---

### Post by Hospadar on 2008-01-23
if it worked fine off the livecd, probably the best thing to do would be dump the wubi instal and do a standard dual-boot installation, with resizing of your windows partition, etc. (Assuming you want to keep windows).

---

### Post by Juran on 2008-01-23
The last time I tried that it really ended quite horribly, that's why I'm trying the Wubi.

---

### Post by Juran on 2008-01-23
Any help?

---

### Post by warrior24 on 2008-01-23
did you try typing 192.168.0.1 in we adress bar.

---

### Post by max renn on 2008-01-23
Do you mean the computer does not connect to the router/modem/Internet?

I assume you cannot ping your router from the computer?

Does your router assign the IP address to your NIC (DHCP)?  Is your NIC configured to automatically receive an IP or is your NIC manually configured for a IP subnet different from your router?  

What is your router's IP and subnet mask?  
What is your NIC's IP and subnet mask?

---

### Post by louieb on 2008-01-23
Not familiar with wubi  really don't know how it works but if you can
Post the output of these 2 commands: Application>Accessories>terminal
 List all your network interfaces
```
ifconfig
```and try to use DHCP to acquire an IP address
```
sudo dhclient
```

---

### Post by Juran on 2008-01-24
Okay. Will have that soon as possible. Wubi is just a way of creating a partition and stuff on your hdd to install Ubuntu, runs off a virtual disk, so I think it works just the same, to the best I've known (I think it's nice, easier on me)..

But as I connect my modem to my router, through ethernet cables (There is an ethernet cable connected to my PC from my router). I have tried just putting the modem's ethernet cable into the PC, but still nothing from Ubuntu.

---

