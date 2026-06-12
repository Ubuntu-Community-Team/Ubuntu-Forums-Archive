---
title: "no makefile found?"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by miao on 2007-10-22
Hello,
I'm trying to install a driver that I downloaded in .tar.gz form. I've gotten it extracted and I'm in the directory, but typing ./config yeilds:
bash: ./configure: no such file or directory

and typing make yeilds:
make: *** No targets specified and no makefile found.  Stop.

I cant find any info on this.
Cheers,
Kat

---

### Post by Maestro23 on 2007-10-22
Install build-essential, then try again.

> sudo apt-get install build-essential

---

### Post by llamakc on 2007-10-22
What sort of other files are in the directory? cut/paste the list here.

---

### Post by Lord_Dicranius on 2007-10-22
Is there a README or INSTALL file?  I'd check those for instructions on installation.

---

### Post by miao on 2007-10-22
heh, I was just going to say, I did install build-essential

---

### Post by Maestro23 on 2007-10-22
> **miao said:**
> heh, I was just going to say, I did install build-essential

LOL.. Ok, then as suggested above, is there a README/INSTALL doc?

---

### Post by miao on 2007-10-22
> **llamakc said:**
> What sort of other files are in the directory? cut/paste the list here.

> **Maestro23 said:**
> LOL.. Ok, then as suggested above, is there a README/INSTALL doc?

There is- but it's not very clear and I'm new and scared, hah. In the dir there's the readme.txt, a relnote.txt, and  sis190.c

---

### Post by Lord_Dicranius on 2007-10-22
I'd read through the readme.txt.  From the terminal, type

```

less read.txt

```
..and then you can use the up/down arrow keys to scroll through it.  Or if you're looking at it through a window manager, just double-click on it hehe  It can't hurt to read it.  Some of those are super easy to read through and are very simple to follow, while to be honest, otheres are very confusing.

---

### Post by Maestro23 on 2007-10-22
> **miao said:**
> There is- but it's not very clear and I'm new and scared, hah. In the dir there's the readme.txt, a relnote.txt, and  sis190.c

Readme.txt shoud contain the instructions.  If you can, post it here so we can take a look at it.

---

### Post by miao on 2007-10-22
here's the readme: (Disclaimer: There is a distinct possibility that this isn't even the driver I want. (It's for a NIC which works when I boot XP but not in Ubuntu- rather, unbuntu sees it and I can ping external servers but I cant d/l anything or load any pages) This is the linux version of the driver that windows is happily using, gotten from the company's site)
Thanks for the help :)

//** Install sis190 module into linux kernel. **//

1. Install Fedora Core 3. (Currently only FC3 can be installed on 965 demo board.)

2. Download Linux kernel 2.6.9 or latter version from [http://www.kernel.org](http://www.kernel.org). The follwing examples are based on linux-2.6.9.

3. copy the kernel source to the location /usr/src/linux-2.6.9.

4. cp sis190.c /usr/src/linux-2.6.9/drivers/net

5. Edit the file "/usr/src/linux-2.6.9/drivers/net/Kconfig".
    a. Serach for the string "config SIS900"
    b. Add the following item below the item of SIS190.

config SIS190
        tristate "SiS 191/190 PCI Gigabit/Fast Ethernet Adapter support"
        depends on NET_PCI && PCI
        select CRC32
        ---help---
          Say Y here if you have a SiS 191/190 PCI Gigabit/Fast Ethernet adapter.

          To compile this driver as a module, choose M here: the module
          will be called sis190.  This is recommended.

6. Edit the file "/usr/src/linux-2.6.9/drivers/net/Makefile".
    a. Search for the string "obj-$(CONFIG_SIS900) += sis900.o".
    b. Insert "obj-$(CONFIG_SIS190) += sis190.o" to next line.

7. cd /usr/src/linux-2.6.9

8. Input the command 'make menuconfig'. Then the Linux Kernel configuration menu will be popped.
    a. Select "Device Drivers -->", "Networking support -->", "Ethernet (10 or 100Mbit) -->".
    b. Goto the item "SiS191/190 PCI Gigabit/Fast Ethernet Adapter support".
    c. Press space key to make this item marked with <M>.
    d. Save and exit the kernel configuration menu.

9. Make kernel and modules. Input the command 'make bzImage modules modules_install install'.

10. Reboot and Select the boot item "2.6.9".


//** Probe sis190 module **//

1. Input the command 'rmmod sis190'.

2. Input the command 'modprobe sis190'.

3. Input the command 'ifconfig eth0 <ip_addr>'.
    a. <ip_addr> is the IP address of sis190.
    b. example: 'ifconfig eth0 192.168.209.1'.

---

### Post by Lord_Dicranius on 2007-10-22
1) This is an old driver.  Fedora Core 3 came out November 2004?
2) It's having you recompile your kernel, which I would leave til a last resort.

So it sounds like you're having problems loading webpages?  You can ping external addresses though?

---

### Post by miao on 2007-10-22
> **Lord_Dicranius said:**
> 1) This is an old driver.  Fedora Core 3 came out November 2004?
2) It's having you recompile your kernel, which I would leave til a last resort.

So it sounds like you're having problems loading webpages?  You can ping external addresses though?

This is what I guessed it was telling me to do, which I thought was a bit silly.

Yeah- the core issue I'm trying to fix is that I can't load any websites, or download any of the system updates. But, I can ping my router, external IPs, and [www.google.com](www.google.com) so I don't see this as a DNS problem. It's been suggested that it's a browser issue, but If that were the case I imagine I'd at least be able to download the updates. So that's what led me to try and update the driver. Any other ideas?

---

### Post by llamakc on 2007-10-22
What's your network consist of? Are you at home, school, work? Behind a router? Do you require a proxy server?

---

### Post by miao on 2007-10-22
> **llamakc said:**
> What's your network consist of? Are you at home, school, work? Behind a router? Do you require a proxy server?

I'm at home- cable internet. Linksys router, wired connection between me and the router. The router feeds 4 computers-  2 windows machines here that are wireless, another ubuntu (feisty) that's also wired, and my dual (XP/Dapper) box. The only connection that has any problems is Dapper. XP connects fine, so it's not a cable/router/NIC problem. No proxy server.

---

### Post by Lord_Dicranius on 2007-10-22
Just gonna take one issue here at a time hehe  See if we can get any kind of Internet activity on this machine.

Do you get any kind of error when you try to update?  What happens when you type "sudo apt-get update" from the terminal?

---

### Post by miao on 2007-10-22
> **Lord_Dicranius said:**
> 
Do you get any kind of error when you try to update?  What happens when you type "sudo apt-get update" from the terminal?

It immediately says "44%  connecting to us.archive.ubuntu.com (99.181.88.31)" but then after a few minutes it times out:
"err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates release.gpg could not to connect to us.archive.ubuntu.com:80 connection has timed out"

It'll keep trying until I tell it to stop.

---

### Post by Lord_Dicranius on 2007-10-22
Are you actually using Dapper?  Or are you using Gutsy?

---

### Post by miao on 2007-10-22
> **Lord_Dicranius said:**
> Are you actually using Dapper?  Or are you using Gutsy?

Dapper. I could easily update to feisty if that would make a difference.

---

### Post by Maestro23 on 2007-10-23
> **miao said:**
> Dapper. I could easily update to feisty if that would make a difference.

If you are going to update to Feisty from Dapper... you must 1st upgrade to Edgy then Feisty.

If you want to do a clean install of Feisty and have theFeisty disc, then those steps will not be needed.:)

---

### Post by miao on 2007-10-23
I have a feisty disk, and don't mind doing a clean install. I haven't updated because I haven't had the need.

But if Feisty's network manager has a better chance of working properly with my internet, then I'm all for it.

---

### Post by Maestro23 on 2007-10-23
> **miao said:**
> I have a feisty disk, and don't mind doing a clean install. I haven't updated because I haven't had the need.

But if Feisty's network manager has a better chance of working properly with my internet, then I'm all for it.

If you can, I would make that jump to Feisty.

---

### Post by miao on 2007-10-23
> **Maestro23 said:**
> If you can, I would make that jump to Feisty.

Done and Done. The install went peachy. 

But now it's even stranger: google loads fine- it'll do searches. gmail too- I can send emails. but no other pages load. I'm really confused.

---

### Post by Lord_Dicranius on 2007-10-23
What do you get when you try this?
```

nslookup www.arin.net

```

And/or are you able to load [www.arin.net?](www.arin.net?)

---

### Post by miao on 2007-10-23
I can't load the site.

But nslookup gives:

server:68.87.76.178
address:68.87.76.178#53

Non-authoritative answer:
name: [www.arin.net](www.arin.net)
address: 192.149.252.7
name: [www.arin.net](www.arin.net)
address: 199.43.0.202

---

### Post by miao on 2007-10-23
Think I'll start a new thread, cuz this is a whole new issue that what I started with :)

---

### Post by miao on 2007-10-23
Just kidding! I found another thread that adressed (and fixed!) this problem.

I'm posting this from Ubuntu :) 

Thanks for all your help!

---

### Post by Maestro23 on 2007-10-23
> **miao said:**
> Just kidding! I found another thread that adressed (and fixed!) this problem.

I'm posting this from Ubuntu :) 

Thanks for all your help!

Good deal man.  Please mark this thread SOLVED using the Thread Tools.

Thanks.:)

---

### Post by Lord_Dicranius on 2007-10-24
> Just kidding! I found another thread that adressed (and fixed!) this problem.

I'm posting this from Ubuntu :)

Thanks for all your help!
Awesome!  Glad to hear you got it working!  You mind posting which thread you find your solution in?  I've come across a couple of these threads where people can load some sites, but not others and would like a thread to direct them to :)

> Please mark this thread SOLVED using the Thread Tools.
I didn't know there was an option in thread tools.  I always told ppl to edit the subject line on the first post heh

---

