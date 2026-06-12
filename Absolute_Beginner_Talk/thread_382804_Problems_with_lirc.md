---
title: "Problems with lirc"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by roofchop on 2007-03-12
I now have 2 weeks on Ubuntu and Linux.  I am slowly starting to get things figured out, but I no longer know how to proceed with getting my Microsoft remote to work with Ubuntu and eventually MythTV.  I am getting nothing with irw.  Here is the code I have tried to get the remote to work.
```
sudo su
cd /usr/src
wget http://prdownloads.sourceforge.net/lirc/lirc-0.8.1.tar.bz2
bunzip lirc-0.8.1.tar.bz2
tar -xvf lirc-0.8.1.tar
cd lirc-0.8.1

./setup.sh
Menu Option # (1) - Driver Configuration (enter)
Menu Option # (8) - USB Devices (enter)
Menu Option # (h) - Windows Media Center Remotes (new version, Philips et al.) (enter)
Menu Option # (3) - Save your configuration and run configure (enter)
make
make install

modprobe lirc_mceusb2
lircd
lircd: there seems to already be a lircd process with pid 32389
lircd: otherwise delete stale lockfile /var/run/lircd.pid
irw

```

It looks to me like a problem with the lircd, but I am not sure how to fix this.  

It is the MS remote keyboard, I would eventually like to get it all to work, but I haven't been able to find enough information about mod_mce which I understand is needed for it to work. I understand that the lirc_mceusb2 will at least get the remote keys to work.

Could really use some help.
JJ

---

### Post by tribble222 on 2007-03-12
I don't know how to help you with your specific problem, but I got my remote working with Edgy in just a few minutes using the guide I found here [https://help.ubuntu.com/community/Install_Lirc_Edgy](https://help.ubuntu.com/community/Install_Lirc_Edgy) .

---

### Post by roofchop on 2007-03-13
I tried it out, tribble222, everything was going nice until the last 2 lines, mine looked like:
```
$ sudo /etc/init.d/lirc start 
#####################################################
## I couldn't load the required kernel modules     ##
## You should install lirc-modules-source to build ##
## kernel support for your hardware.               ##
#####################################################
## If this message is not appropriate you may set  ##
## LOAD_MODULES=false in /etc/lirc/hardware.conf   ##
#####################################################
Starting lirc daemon:. 
$ irw




```

I am not sure what to do, this is currently beyond my skills,, sounds like install lirc-modules-source to build kernel support for your hardware.

Would it be beneficial to reinstall Ubuntu and MythTV, to make this work.  Could all my trial and error be interfering with things? 

It would sure be nice to get this ugly keyboard out of my living room.

---

### Post by majoridiot on 2007-03-16
> **roofchop said:**
> I tried it out, tribble222, everything was going nice until the last 2 lines, mine looked like:
```
$ sudo /etc/init.d/lirc start 
#####################################################
## I couldn't load the required kernel modules     ##
## You should install lirc-modules-source to build ##
## kernel support for your hardware.               ##
#####################################################
## If this message is not appropriate you may set  ##
## LOAD_MODULES=false in /etc/lirc/hardware.conf   ##
#####################################################
Starting lirc daemon:. 
$ irw
```

I am not sure what to do, this is currently beyond my skills,, sounds like install lirc-modules-source to build kernel support for your hardware.

Would it be beneficial to reinstall Ubuntu and MythTV, to make this work.  Could all my trial and error be interfering with things? 

It would sure be nice to get this ugly keyboard out of my living room.

no need to reinstall mythtv...

that's a standard error if your modules aren't matching your config- i've done it by mistake myself.

do:

```
# sudo dpkg-reconfigure lirc-modules-source 
```

and make sure that the *only* module selected is mceusb2.  do **not** build the modules
and select "package maintainer's version" if prompted.

then:
```
# sudo nano /etc/lirc/hardware.conf
```

and make sure the following two lines match exactly:

```
LOAD_MODULES=true

MODULES="lirc_mceusb2"
```

then, re-build:

```
# sudo rm /usr/src/lirc*deb
# sudo m-a clean lirc
# sudo m-a update,prepare
# sudo m-a a-i lirc
# sudo depmod -a
```

if you've already taken care of the lircd.conf step, then you should be able to test with irw.

don't forget you will need a ~/.mythtv/lircrc file for mythtv interface.  the lirc guide link tribble222
posted has the info- it's a very good guide and all you should need to get mceusb2 working for you!

---

### Post by roofchop on 2007-03-20
It works, Thanks a lot majoridiot.  Finally I have regained an IR interface.  Now, can anybody help me out with mod_mce?

It is hosted on this sourceforge page without any documentation
[http://mod-mce.sourceforge.net/]("http://mod-mce.sourceforge.net/")

I have found a couple of similar posts as mine, but I don't completely follow what to do with the files once they are extracted:
[sourceforge.net/forum]("https://sourceforge.net/forum/forum.php?thread_id=1660191&forum_id=588333")
[ubuntuforums.org]("http://ubuntuforums.org/showthread.php?p=2086205")
[nabble.com]("http://www.nabble.com/MCE-keyboard----RC6-issue--t1857189.html")
[http://www.gossamer-threads.com/lists/mythtv/users/222741]("http://www.gossamer-threads.com/lists/mythtv/users/222741")

Can anybody help me out with some detailed directions on how to do this, it would be nice to see a good how-to for this.

---

