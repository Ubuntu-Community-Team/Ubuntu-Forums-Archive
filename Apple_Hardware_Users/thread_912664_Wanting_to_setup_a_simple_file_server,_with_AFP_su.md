---
title: "Wanting to setup a simple file server, with AFP support"
date: 2008-09-06
forum: Apple Hardware Users
---

### Post by Apocrathia on 2008-09-06
First off, is AFP even possible in linux? or is it a totally proprietary protocol. Now,

Problem:
I have a massive collection of media scattered amongst several PC's in my house. I want to centralize it all, but also be able to have a NAS time capsule. I was thinking just an AFP share that I could use as a time machine drive.

Solution:

A: Get an external drive (I was looking at a Drobo to hook into my WRT610N's usb port. Problem with that is that my router doesn't do AFP)
B: Setup my old desktop PC as a Linux file server. Include support for AFP so that my mac's can use it as a Time Machine backup.

So throw me some ideas. I'm up for it. I've already been posting on tom's hardware to get some opinions from there. Apparently the Drobo fails, and it fails, and it fails, and it fails. I would want to run a "headless" file server that I could simply VNC into for maintenance.

---

### Post by Qloor on 2008-09-07
Try this thread: [http://ubuntuforums.org/showthread.php?t=410274]("http://ubuntuforums.org/showthread.php?t=410274").

---

### Post by cyberdork33 on 2008-09-07
check out netatalk.
you don't have to use AFP for Time Machine though. Samba shares will work too.

---

### Post by Apocrathia on 2008-09-08
I've already started looking into netatalk, and I know how to enable unsupported shares for time machine, but I'd rather just use an afp share.

I'm building a setup in a vmware machine right now, I can't seem to get any server services like ssh, or even apache installed on ubuntu desktop edition. and the server edition makes me nervous, although i would probably "aptitude install xubuntu-desktop" to add the gui.

I want to setup a vmware player running as well, running FreeNAS. I really REALLY like it, but don't see myself getting much else out of it, and i'd like to be able to set up multiple things.

heres all I really want to do:
*file sharing for pc's and macs (smb & afp)
*vnc for server maintenance
*FreeNAS via VMwarePlayer
*some sort of a UPnP media server for my PS3 & AppleTV
*I'd REALLY like some sort of a software raid, I love datarobotics' BeyondRAID software that they use for the Drobo's but its proprietary :( 

I have a 4 drive hotswap bay the computer I am using, and I would like to be able to add drives to a raid if need be, without having to re-raid the whole thing. 

I'm new to all of this, so if anyone has any suggestions I am up for it.

---

### Post by Apocrathia on 2008-09-08
Just got a VM of ubuntu server up and running and already feel overwhelmed, toyed with Xubuntu and it really isnt much either. I really want to stick with the desktop version, but get all of the server functionality out of it. Can I install openssh, apache, etc... through the synaptics manager somehow? I am pretty much baffled on compiling source.
The system I am running for the purpose is a bit of overkill anyways, so I don't have to worry about weight. (1.8 Athlon XP, 1gb pc2700 for a simple file server)
Since it's all the same thing under the hood, each version of ubuntu simply differs in the packages included, I am going to stick with the desktop version.

---

### Post by cyberdork33 on 2008-09-09
I guess you are setting everything up in a VM as a testbed? Why don't you just install to the machine natively?

All the same software is available in the repos whether you are running Ubuntu Desktop, Server, Kubuntu, xubuntu, etc.
To install and ssh server, you just have to ```
sudo apt-get install openssh-server
``` that's it.

I don't have a lot of experience with other servers, but they are all there in the repos (accessible by synaptic, apt, etc)

You are correct about adding all the desktop apps to a server install. there is also ubuntu-desktop and kubuntu-desktop and probably others.

---

### Post by Apocrathia on 2008-09-10
I've got a lot of data still on the machine that I will be using. So I am simply vmware'ing to test out different configurations right now and see if i can get everything running how I need it. I have a wubi setup on the machine right now, but that was just to test performance on the actual machine. I will probably start adding more and more to that install as I go along and just resize partitions once I get some new hdd's.
I looked into windows server 2003 and several others and havent found much use for those other than being annoyances. Windows home server had a feature called "disk extender", which seemed like a good idea but I know how micro$oft's implementations of good ideas go. I setup home server in a vmware and wasnt pleased at all.

The only way I am going to get the functionality I want is to just put together a linux setup. While I would prefer something I don't have to mess with, the linux setup is going to be more rewarding in the end.

I figure most of these programs I am going to have to compile from source to get them. I really don't have a big problem with that, it's just a new playing field for me. I am going to my schools library later today to request a book on ubuntu. If you know of any good ones, let me know and I will gladly add them to the list. I need to start soaking up information.

---

### Post by cyberdork33 on 2008-09-10
> **Apocrathia said:**
> I figure most of these programs I am going to have to compile from source to get them.

I don't think you will.

---

### Post by Apocrathia on 2008-09-10
> **cyberdork33 said:**
> I don't think you will.

I've tried searching for a lot of things through just the add/remove programs synaptics manager and haven't found much. My worry with compiling and installing from source is that I never know where the program goes after that because I still am not totally familiar with the unix file system.

All I really need is openssh, netatalk, and a print server. I would like to do an iCal server, but I already have mobileme, so I'm taken care of on that one.

---

### Post by cyberdork33 on 2008-09-10
> **Apocrathia said:**
> I've tried searching for a lot of things through just the add/remove programs synaptics manager and haven't found much. My worry with compiling and installing from source is that I never know where the program goes after that because I still am not totally familiar with the unix file system.

All I really need is openssh, netatalk, and a print server. I would like to do an iCal server, but I already have mobileme, so I'm taken care of on that one.
Don't look though the Add/Remove Programs interface. It is very limited. Make sure all the repos are enabled, and use the synaptic package manager (System > Administration > Synaptic Package Manager)

You can also make sure aptitude is installed and you can search with it.

```
sudo apt-get install aptitude
```
To Search:
```
sudo aptitude search openssh
```
The result will probably be more than one package, but you can read the descriptions to decide which one you are looking for. ("openssh-server" in this case). Then you can install with ```
sudo apt-get install openssh-server
```

You can also look through the online package repository web interface:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

