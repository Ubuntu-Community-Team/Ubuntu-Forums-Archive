---
title: "VMWare : Ubuntu in Virtual Machine"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by moogyd on 2006-11-01
Hello,

I have an acer1683 running windows XP home edition. 
It want/need access to Linux for work and hobbies (HW and SW programming), and have read some good reviews of Ubuntu.

I am considering installing Ubunutu in a Virtual Machine (for seamless switching between Windows and Linux), and am hoping that someone can povide a link to some installation guides/notes, and whether anyone has this configuration successfully running.

My initial question is do I need VMWare player or server ?

Note that I need windows to be the host operating system as the laptop is a familiy computer.

Thanks,

Steven

---

### Post by HereInOz on 2006-11-01
You technically cannot use VMWare server on Windows XP, although I have seen it working.  I don't know if it will throw up troubles from time to time or not.  VMWare Server is designed for server systems such as Linux or Windows 2003 Server.

The version you should use is VMWare Desktop, but you will have to pay for that.  I would have a go at installing VMWare Server on XP and see how it goes, and if it does OK, stay with it.  Bear in mind, though, that you could be contravening the licencing by doing that.

Pity you need XP as the host.  You would get much better performance with Ubuntu as the host and XP running in a VM.  VMWare Server would then perform beautifully and also be legal.

The installation of VMWare Server is straightforward, and setting up a virtual machine is also very easy.   You should have no trouble with it.  I run XP in a VM on Ubuntu, and that is a great way to go.  Pity you need to run it the other way around - the performance is not as good.

Cheers,

Alan

---

### Post by the_priest on 2006-11-01
*Off topic*

Dont mean to hijack this thread just thought i'd ask a quick question seeing as it kinda fits in with HereinOz's suggestion.

Could you run XP in VM and achieve the same as if you were dual booting? Coz the only reason i still have XP is for my games. So if i could full screen VM/XP in Ubuntu and play my games I'd get rid of that ntfs partition REALLY quickly :P. What about things like drivers and such for XP in VM? Like i want to softmod my 9500 using radeon drivers.

---

### Post by LaLLi on 2006-11-01
If I were you I would use VirtualPC 2004 for your virtualization needs. It's very easy to use and you can use it to install Ubuntu. VPC2004 is free for download so you don't need to pay for VMware. VPC2004 is designed by MS for MS OS.
[http://www.microsoft.com/windows/virtualpc/downloads/sp1.mspx](http://www.microsoft.com/windows/virtualpc/downloads/sp1.mspx)

@the_priest
No you can't use VM for gaming. As far as I know no VM supports 3D acceleration. That kind of rules out all the modern games that use 3D effects. If you want to ditch XP I suggest you give Cedega a try.

---

### Post by gn2 on 2006-11-01
> **the_priest said:**
> *Off topic*

Dont mean to hijack this thread just thought i'd ask a quick question seeing as it kinda fits in with HereinOz's suggestion.

Could you run XP in VM and achieve the same as if you were dual booting? Coz the only reason i still have XP is for my games. So if i could full screen VM/XP in Ubuntu and play my games I'd get rid of that ntfs partition REALLY quickly :P. What about things like drivers and such for XP in VM? Like i want to softmod my 9500 using radeon drivers.

No joy I'm afraid very limited graphics in VM's

---

### Post by davmac on 2006-11-01
I have had VMWare server running on WinXP with no troubles whatsoever. You can download it from [http://www.vmware.com/download/server/](http://www.vmware.com/download/server/) and register for your free serial numbers. Just download the "VMware Server for Windows Operating Systems" install it and you'll be away.

The most complex thing I found was, once you've set up your virtual Ubuntu machine, installing the VMWare tools, but if you search these forums for "vmware tools" you'll find plenty of advice for getting through this.

Hope this helps,

Dave Mac

---

### Post by davmac on 2006-11-01
> **gn2 said:**
> No joy I'm afraid very limited graphics in VM's

And no support for USB2.0 which is what killed this configuration option for me.

Dave Mac

---

### Post by sixteensix on 2006-11-01
Steven, if it was me I would go with VMPlayer if its just for testing purposes? VMWare player is not as heavy as VMWare Server, and Virtual PC/Server is alot slower (Please no flames just my opinion). 

You can use [http://www.easyvmx.com/]("http://www.easyvmx.com/") to create a vmware config. Easyvmx has alot more info so take a look.

Cheers

Tim

---

### Post by gn2 on 2006-11-01
> **moogyd said:**
> Hello,

I have an acer1683 running windows XP home edition. 
It want/need access to Linux for work and hobbies (HW and SW programming), and have read some good reviews of Ubuntu.

I am considering installing Ubunutu in a Virtual Machine (for seamless switching between Windows and Linux), and am hoping that someone can povide a link to some installation guides/notes, and whether anyone has this configuration successfully running.

My initial question is do I need VMWare player or server ?

Note that I need windows to be the host operating system as the laptop is a familiy computer.

Thanks,

Steven

You need VMWare Server for Windows free edition: [http://www.vmware.com/products/server/](http://www.vmware.com/products/server/)
Player only lets you play pre-configured "Appliances" which have to be downloaded.

Or try Parallels if not enough functionality with VMWare (I couldn't get sound to work) Free Trial: [http://www.parallels.com/](http://www.parallels.com/)

Another alternative would be to install to an external hard drive, not simple in Ubuntu, but automated in PCLinuxOS.

---

### Post by jinx099 on 2006-11-01
> **HereInOz said:**
> You technically cannot use VMWare server on Windows XP, although I have seen it working.  I don't know if it will throw up troubles from time to time or not.  VMWare Server is designed for server systems such as Linux or Windows 2003 Server.

The version you should use is VMWare Desktop, but you will have to pay for that.  I would have a go at installing VMWare Server on XP and see how it goes, and if it does OK, stay with it.  Bear in mind, though, that you could be contravening the licencing by doing that.

Pity you need XP as the host.  You would get much better performance with Ubuntu as the host and XP running in a VM.  VMWare Server would then perform beautifully and also be legal.

The installation of VMWare Server is straightforward, and setting up a virtual machine is also very easy.   You should have no trouble with it.  I run XP in a VM on Ubuntu, and that is a great way to go.  Pity you need to run it the other way around - the performance is not as good.

Cheers,

Alan

What are you talking about?  VMware server for windows works perfectly on XP, is free, and legal...  :-k

---

### Post by clarkth on 2006-11-01
I've downloaded VMware server for Windows and have it running on my XP Pro laptop.  I've set up a couple of Ubuntu servers and am wondering how much disk space do I really need?  I have a web server, php, ftp, mySQL, webmin now, and eventually will add other things to test them out before I add them to my "real" ubuntu home server.  Thanks.

---

### Post by moogyd on 2006-11-01
Hi,

Thanks for the responses. I have now got Linux in a virtual machine, just not the distro I planned.

I downloaded VMWare Player, and then the ubuntu-server-6.06.1.-i386 virtual machine. Unfortunately I got a hang when I attempted to start, that is possibly related to the problem described here:
[http://www.vmware.com/community/thread.jspa?messageID=419923](http://www.vmware.com/community/thread.jspa?messageID=419923)
I tried the adding the following switches to the grub command line
acpi=off noapic nolapic
to no avail :( 
I then downloaded the Fedore Core 5 VM from :
[http://www.vmadvisor.com/prebuilt.html](http://www.vmadvisor.com/prebuilt.html)
and it worked straight away :) (Note that the root password is not as reported on this page - it is Fedora).

Thanks again for replies and suggestions.

Steven

---

### Post by Chayak on 2006-11-01
I haven't had any problems running vmware server on XP or 2k3 the only issues I've had on the windows side is running it on 2k.  The legal route to get a Ubuntu VM to your tastes would be to install the VMware workstation demo, create your VM then use VMware player to run it.  VMware Server works but you take a visual performance hit at times because of the way it connects to the VM as opposed to Workstation.

---

### Post by gn2 on 2006-11-01
> **Chayak said:**
> I haven't had any problems running vmware server on XP or 2k3 the only issues I've had on the windows side is running it on 2k.  The legal route to get a Ubuntu VM to your tastes would be to install the VMware workstation demo, create your VM then use VMware player to run it.  VMware Server works but you take a visual performance hit at times because of the way it connects to the VM as opposed to Workstation.

VmWare are now offering a free VmWare Server for windows on their website.
[http://www.vmware.com/products/server/](http://www.vmware.com/products/server/)

---

### Post by dacovale on 2006-11-02
If you want windows for the rest of the Family but Linux for yourself, simply install Linux, and set the other family members logins to autostart VMware with Windows resumed in fullscreen.
Perhaps not totally transparent. (the login-screen would have to be skinned to get am MS-friendly look) But it should work ok otherwise.

---

### Post by Chayak on 2006-11-02
> **gn2 said:**
> VmWare are now offering a free VmWare Server for windows on their website.
[http://www.vmware.com/products/server/](http://www.vmware.com/products/server/)

I'm aware ;) I was just stating you'll get better visual performance with VMware workstation over VMware Server and the version of VM type created will be different as the workstation side has more features when it comes to multiple snapshots.

---

### Post by LaLLi on 2006-11-02
You could make a new VM with VMware Server and use it with VMware Player. Or make a new VM with qemu so you dont need to install VMware Server. VMware Player supports lots of different VM machine formats if I remember correctly.

---

### Post by gn2 on 2006-11-02
> **Chayak said:**
> I'm aware ;) I was just stating you'll get better visual performance with VMware workstation over VMware Server and the version of VM type created will be different as the workstation side has more features when it comes to multiple snapshots.

Yep, re-read your post and see that now. Good idea using the higher spec job on trial to create a better VM.

As Borat would say "I like, is niiiice" :)

---

