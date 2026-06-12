---
title: "LAMP and anti virus"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by takeuaway on 2007-05-12
Hi. Could anyone tell me is there any program for ubuntu which will install apache, mysql, php for me automatically configured? I use Developerside when i was using Windows.

And is there any anti virus program i can install in ubuntu?

Thanks a lot!

---

### Post by DaveyG on 2007-05-12
You can install apache, mysql & php using the synaptic package manager, (No configuration needed)

anti virus??? there are hardly any viruses for Linux.... there are some anti virus software but i have no idea were to get it from

Davey

---

### Post by hyper_ch on 2007-05-12
What do you want antivirus for?

---

### Post by mcduck on 2007-05-12
If you are running 7.04, just go to Synaptic, select Edit/Mark Packages by Task and then enable 'LAMP Server'. Then click the 'Apply'-button in Synaptic. :)

Antivirus? Why? :D

---

### Post by john_spiral on 2007-05-12
If you only install software from the 'synaptic package manager', you don't need to worry about viruses.

---

### Post by 3rdalbum on 2007-05-12
If you want to check for viruses on your Windows partition (if any), you can download the KlamAV package from the repositories. It will take a while but it's worth it.

If you're worried about viruses on Linux, then don't! Use your bandwidth to download some games :-)

---

### Post by quinnten83 on 2007-05-12
If you Really really really want an antivirus, you can try with AVG from grisoft.
I don;t know if it is in the repository, and i don;t remember where i got it from, but it's running on my pc.

---

### Post by BlaineM on 2007-05-12
from what I have read about antivirus and Linux, the only semi-risky reason to run one is if you are running emulation type software like wine, or vm, or similar.  I know that wine operates with the windows directory structure, but from this [article]("http://os.newsforge.com/article.pl?sid=05/01/25/1430222&from=rss"), many of the viruses listed do not give the same grief in Linux, and after shutting down wine, they stop from doing their business altogether.

I know there are probably some other articles out there for info on antivirus and linux, but wine would be the only reason that I would want to run one to stay clean.

---

### Post by BlaineM on 2007-05-12
here are some free installers for antivirus software made from professional companies

[AVG free for Linux]("http://free.grisoft.com/doc/5390/lng/us/tpl/v5#avg-anti-virus-free")
[Panda for Linux]("http://www.pandasoftware.com/download/linux/linux.asp")

McAfee makes one that costs money.
[McAfee for Linux]("http://www.mcafee.com/us/enterprise/products/anti_virus/file_servers_desktops/linuxshield.html")

Other antivirus makers
[f-prot]("http://www.f-prot.com/products/home_use/linux/")
[clam]("http://www.clamav.net/download/packages/packages-linux")

Im sure there are probably more out there...

---

### Post by nickpaton on 2007-05-12
Have a read of[ this]("http://ubuntuforums.org/showthread.php?t=72598") article and [this]("http://librenix.com/?inode=21") one as well on the real life effect of virus's on Linux distros.

Makes interesting reading!

---

### Post by takeuaway on 2007-05-13
Woah, thanks a lot. 

However, while i was loading ubuntu, it says error reading usb. I got a usb external hard drive and usb mouse connected. Then after ubuntu is fully loaded, my mouse motion became very sulky, and my external hard drive isn't there. 

Can teach me how to resolve the problem? Thanks!

---

### Post by nickpaton on 2007-05-13
May I suggest you start a new thread for your USB problems in the beginners section.

Supply the make and model of your PC, and which version of Ubuntu you've installed.  it may be that your particular PC has a USB problem in Ubuntu.

Also can you put the following command in a terminal (Applications > Accessories > Terminal):

```
sudo lshw
```

lshw has a capital L.

This will give the list of all your installed hardware. 
Please post the section for USB (it may read USB0 USB1 etc) and this will help others more knowledgeable than me to sort out your problem.

EDIT: Just done a search for USB problems and found [this]("http://ubuntuforums.org/showthread.php?t=418575") useful post about USB HDD's.

Good luck!

---

