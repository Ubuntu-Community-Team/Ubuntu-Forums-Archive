---
title: "Getting an iMAC G3 to be thin client on Edubuntu LTSP"
date: 2009-02-18
forum: Apple Hardware Users
---

### Post by lmowery on 2009-02-18
Hello,

We are a school district with about a bazillion iMAc G3 computer labs.  (Specs around 333Mhz for the processor and 32-128MB of RAM.

I have created a thin client lab that I am loving with Ubuntu/Edubuntu 8.10 combo discs for an LTSP server.  It works great.  I have used it for old i386 pcs that were going to be trashed.

I now want to create an Edubuntu LTSP server for a test classroom of iMACs.  If it works good, I can roll out a server for each lab and use those computers.  For now they are so old that they can't get the latest flash update4s for educational websites.  As a thin client.....*crosses fingers*

Here is my question.  I am following [https://help.ubuntu.com/community/UbuntuLTSP/LTSPCrossArchSetup]("https://help.ubuntu.com/community/UbuntuLTSP/LTSPCrossArchSetup") Guide, and it says to > gksudo gedit /etc/exports

edit:

/opt/ltsp       *(ro,no_root_squash,async)

to be:

/opt/ltsp       *(rw,no_root_squash,async)

However there is not "/etc/exports" document to edit....
Does anyone know how to do what I want?  I know I need to update the processor architecture to allow the LTSP server to service powerpcs.  

I have alternate disk Ubuntu 8.1 installed with the LTSP option and the Edubuntu 8.1 add on cd installed on my server.  It has 2 NICS.  I have a G3 with alternate Xubuntu 7.1 powerpc installed I can use to do the client build.

I am stuck and really need help, suggestions, or references to more complete guides.  Thank you.

---

### Post by PhirePhly on 2009-03-15
LTSP doesn't use NFS anymore, so you just have to install nfs-kernel-server on both, then create the file /etc/exports and add the one line.  

I just tried to do it this afternoon, but have been having all kinds of problems with the mirrors moving to ports.ubuntu.com/ (without /ubuntu/)

I think the CrossArch guide is also missing instructions telling you to copy over the /var/lib/tftpboot/ stuff for powerpc.  I'll keep you updated as I get stuff working.

---

### Post by SimonHova on 2009-03-17
> **PhirePhly said:**
> I just tried to do it this afternoon, but have been having all kinds of problems with the mirrors moving to ports.ubuntu.com/ (without /ubuntu/)


I have been working on that step as well, if you can update this thread when you get a workaround, I would appreciate it!

---

### Post by PhirePhly on 2009-03-17
I used apt-cacher-ng on another desktop to work around the /ubuntu/ problem by commenting out the two default remaps and adding
```
# in /etc/apt-cacher-ng/acng.conf
Remap-ubu: /ubuntu /ubuntu/ubuntu ; http://ports.ubuntu.com
```
and restarting it. I don't *think* you need the /ubuntu/ubuntu, but these tools keep assuming they can just tack /ubuntu/ on the end of anything.

Then pointing ltsp-build-client at this local mirror, in my case at 192.168.1.149:
```
sudo rm -r /opt/ltsp/powerpc
sudo ltsp-build-client --mirror http://192.168.1.149:3142/ubuntu --security-mirror http://192.168.1.149:3142/
```

I also got pretty much as far by mounting an alternate cd and accessing it over apache2 locally:
```
sudo apt-get install apache2
sudo mount -o loop /path/to/ubuntu-8.04.1-alternate-powerpc.iso /var/www/
```

But now the ltsp-client package fails because one of its dependencies is uninstallable:
```
The following packages have unmet dependencies:
 ltsp-client: Depends: acpid but it is not installable
E: Broken packages
```

So I think we're pretty much SOL for now.  Like so many things in PowerPC land, this is fundamentally broken.
My next thought is to try and build an image from Debian or Dapper, but it being finals week really cuts into my free time right now.

Notes: 
I'm not bothering with the NFS mount, but just building everything locally, then will copy /opt/ltsp/powerpc/ and /var/lib/tftpboot/ltsp/ manually over ssh.

---

### Post by SimonHova on 2009-03-18
That is awful. Thanks for the updates, you saved me hours of work.

Still, I am going to have to mothball this project, and start Edubuntu LTSP with the few PC clients we have, and I'll try to work in the 50+ iMacs we have over the next month or so. Hopefully, some of the bug reports can be cleaned up by then.

-Simon

> **PhirePhly said:**
> I used apt-cacher-ng on another desktop to work around the /ubuntu/ problem by commenting out the two default remaps and adding
```
# in /etc/apt-cacher-ng/acng.conf
Remap-ubu: /ubuntu /ubuntu/ubuntu ; http://ports.ubuntu.com
```
and restarting it. I don't *think* you need the /ubuntu/ubuntu, but these tools keep assuming they can just tack /ubuntu/ on the end of anything.

Then pointing ltsp-build-client at this local mirror, in my case at 192.168.1.149:
```
sudo rm -r /opt/ltsp/powerpc
sudo ltsp-build-client --mirror http://192.168.1.149:3142/ubuntu --security-mirror http://192.168.1.149:3142/
```

I also got pretty much as far by mounting an alternate cd and accessing it over apache2 locally:
```
sudo apt-get install apache2
sudo mount -o loop /path/to/ubuntu-8.04.1-alternate-powerpc.iso /var/www/
```

But now the ltsp-client package fails because one of its dependencies is uninstallable:
```
The following packages have unmet dependencies:
 ltsp-client: Depends: acpid but it is not installable
E: Broken packages
```

So I think we're pretty much SOL for now.  Like so many things in PowerPC land, this is fundamentally broken.
My next thought is to try and build an image from Debian or Dapper, but it being finals week really cuts into my free time right now.

Notes: 
I'm not bothering with the NFS mount, but just building everything locally, then will copy /opt/ltsp/powerpc/ and /var/lib/tftpboot/ltsp/ manually over ssh.

Even once we do build the images, I'm going to put money on it suffering from [Bug #26426]("https://bugs.launchpad.net/ubuntu/+source/yaboot/+bug/26426"), so you'll need to replace yaboot with [my patched version]("https://bugs.launchpad.net/ubuntu/+source/yaboot/+bug/26426/comments/18").

---

### Post by e05-0150 on 2009-03-20
Hi, I had this problem when I tried to do a cross arch setup. The acpid problem is listed as a launchpad bug. I followed the instructions and the clients built fine for me but they still don't boot as I get stuck at a busybox prompt.

link to launchpad:
[https://bugs.launchpad.net/ubuntu/+source/ltsp/+bug/213014](https://bugs.launchpad.net/ubuntu/+source/ltsp/+bug/213014)

---

### Post by PhirePhly on 2009-03-21
I can confirm that the workaround works, but I find it strange that the bug is marked fixed. I'm using version 5.0.40-bzr... but it's still broken.  Haven't gotten a chance to try booting it yet, so all I can say is that it built successfully.  I'll try booting it once I drive home this afternoon.

---

### Post by PhirePhly on 2009-03-22
I've hit an issue with nbd_server (network block device, which replaced nfs).  I haven't figured out how to tell it to serve /opt/ltps/image/powerpc.img instead of ./i386.img, but as a workaround I just renamed powerpc.img as i386.img, which is obviously not useful for multiple arch support.

I also had to move /var/lib/tftpboot/ltsp/powerpc/yaboot.conf to .../tftpboot/yaboot.conf, since yaboot was looking for it there...

It booted (slowly), and now only says
```
(ldmgtkgreet:3329): Gtk-WARNING **: cannot open display: :6
```
I can't ctrl-alt-F1 into a terminal, or really make it respond at all.

---

### Post by PhirePhly on 2009-04-12
I have retried everything using Jaunty.

I have figured out that the nbd (network block device) file is defined in /etc/inetd.conf, but that still doesn't by itself solve the problem of serving different images to different clients.

When it comes up and is about to start the gdmgreeter, it instead displays:
```
Loading, please wait...
IP-Config: eth0 hardware address 00:50:e4:30:d4:0e mtu 1500 DHCP RARP
IP-Config: eth0 complete (from 192.168.1.1):
 address: 192.168.1.15 [ed: SNIP DHCP info]
 rootserver: 192.168.1.12 rootpath:
 filename  : yaboot
Negotiation: ..size = 172668KB
bs=1024, sz=172668
Kernel call returned: Broken pipe Reconnecting
Negotiation: ..size = 172668KB
Error: Ioctl/1.1a failed: Bad file descriptor

Ubuntu jaunty (development branch) KWF5 tty1
KWF5 login:
```

With 192.168.1.1 my DHCP server, 192.168.1.12 (KWF2) my tftp and nbd server, and 192.168.1.15 (KWF5) my powerbook G3 client. I couldn't find any logins that worked on the prompt on the client...
This is beyond me, so I'm stuck again...

---

### Post by LinuxJediMaster on 2011-02-15
It seems building a PowerPC client has been broken for quite some time. I attempted to install 10.04 Alternate on a G4 and it will not build a client image. I may attempt to build one by hand.

---

### Post by LinuxJediMaster on 2011-02-17
I am not experienced with LTSP in general, and certainly not Ubuntu LTSP. But the great part about Linux? ts free, I can download it, experiment, AND sometimes the old technology very useful. So, what I have set upon for myself to do, is to teach myself LTSP, and become very good at troubleshooting it. i don't know if this is still true, but it seems many schools and institutions who still have working G3s, G4, and G5s, coud turn these boat anchors into usable terminals again, by using LTSP.

I have learned that there are claim LTSP worked well using K12linux, based on Fedora (see [https://fedorahosted.org/k12linux/wiki/](https://fedorahosted.org/k12linux/wiki/)). I am going to install an older version (but not too old) to see if I can build a work PPC client image. Then i will do some comparisons and see if I can make the Ubuntu system work from what I learn from the Fedora implementation.

---

