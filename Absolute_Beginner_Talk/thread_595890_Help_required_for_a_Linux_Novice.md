---
title: "Help required for a Linux Novice"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by JohnO'L on 2007-10-29
Hi

I'm looking for some quick help and responses, I've installed Ubuntu 6.06.1 Server edition (LAMP) on an IBM X335 dual core.

I have a small time window to actually sit in front of the machine and configure the basics. I need to configure the network interface and basic remote access (Telnet or SSH ??) so that I can continue my Web server build remotely.

I'm a complete Unix novice never having even used a txt editor !!! :(

Are there any GUI tools I could use to get these functions configured quickly ?? not a complete desktop but just GUI front end to the linux IPconfig equivalent ?? Telnet also ??

Apologies for the cry for help but If I won't get another chance to physically access the box for another week !!

Thanks in advance

---

### Post by hyper_ch on 2007-10-29
> **JohnO'L said:**
> I need to configure the network interface and basic remote access (Telnet or SSH ??) so that I can continue my Web server build remotely.
Ieeeeks, telnet... you want to remove that... use SSH
```

sudo apt-get remove telnet && sudo apt-get install openssh-server

```
You can login now with your normal user/passwd

> **JohnO'L said:**
> 
I'm a complete Unix novice never having even used a txt editor !!! :(
Use nano, it's simple
```

nano file.txt

```
Press ctrl-x for exiting nano, you'll then be prompted if you want to save the file and what the filename shall be...

> **JohnO'L said:**
> Are there any GUI tools I could use to get these functions configured quickly ?? not a complete desktop but just GUI front end to the linux IPconfig equivalent ?? Telnet also ??
There is, but you only need to edit those files:

/etc/network/interfaces
/etc/resolv.conf
/etc/hosts

the interfaces file contains the actual network adapter setup. The resolv.conf contains the list of nameservers that shall be querried and the hosts file... well, that's the local loopback and some other static routing of domain names.

And use next time a descriptive thread title... no just a "need help"

---

### Post by JohnO'L on 2007-10-29
Hi

Thanks for the reply, apologies for the thread title, I'll be more descriptive in future.

For expediency what are the GUI tools you suggested were available ?

Thanks

---

### Post by hyper_ch on 2007-10-29
I did not recommend any gui tools ;)

---

### Post by steve.horsley on 2007-10-29
If you install the server version of Ubuntu, it doesn't install a GUI at all. You need to use a text editor (like nano) to edit the required files. JohnO'L listed the files, but you need to know what should be in them of course. 
Do you want your server to be DHCP or to have a static IP address? If static, what IP address, subnet mask, default gateway do you want. and which DNS servers do you want to use?

---

### Post by JohnO'L on 2007-10-29
Hi Steve

I haven't got the details to hand at the moment but I know the static IP, mask, gateway and DNS. Will the interfaces file have a "sample" coz I won't know the syntax etc.....

Thanks

---

### Post by steve.horsley on 2007-10-29
Here's a sample from my /etc/network/interfaces file, for a fixed IP address:
> auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.8.101
netmask 255.255.255.0
gateway 192.168.8.1

auto eth0


Your DNS servers go in /etc/resolv.conf, one line per DNS server like this (not my real servers addresses):
> nameserver 1.2.3.4
nameserver 1.2.3.5

It is important that your host name in /etc/hostname matches a loopback address in /etc/hosts. Frinstance, my hostname here is StevesPC (thats the overall contents of /etc/hostname), and I have these entries in /etc/hosts:
> 127.0.0.1       localhost
127.0.1.1       StevesPC


I think that should do the trick for you. Good luck.

---

### Post by timcredible on 2007-10-30
if you want a gui to remotely access your machine (it's the easiest way), please see my how-to on using xdm:  [http://linux--help.org/joomla2/index.php?option=com_content&task=view&id=12&Itemid=1](http://linux--help.org/joomla2/index.php?option=com_content&task=view&id=12&Itemid=1)

---

### Post by spinnekoppeke on 2007-12-11
Hi,

Question concerning x335 ibm serie 61x : I tried to install it today with a 2.4-kernel with debian : problems to detect the raid-controller/harddisks and the broadcom ethernet interface, which made installation impossilbe. Any experiences with ubuntu-server-version, especially concerning detecting hardware and further installation ? ARe drivers (redhat-rpm's ?) necessary ? 

Greetings,
Johan

---

### Post by hyper_ch on 2007-12-12
Why do you still use a 2.4 kernel? For Debian Sarge 3.1 you can directly install a 2.6 kernel and Debian Etch features only 2.6 kernels if I'm not mistaken.

Ubuntu Gutsy comes also with 2.6 kernels.

You can't use RPMs on debian/ubuntu... well you could try to convert them with alien but that should not be necessary.

I think if you use a 2.6 kernel it should run fine.

---

### Post by njparton on 2007-12-12
Try installing webmin, there's a .deb file available on their website:

[http://www.webmin.com]("http://www.webmin.com")

You can then administer your server from a remote browser using a GUI of sorts.

---

