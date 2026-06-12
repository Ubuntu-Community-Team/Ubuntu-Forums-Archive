---
title: "Aluminium iMac Help"
date: 2008-03-24
forum: Apple Intel Users
---

### Post by Aquastus on 2008-03-24
Hello. I have just installed Ubuntu 7.10 on my 20'' 2.0GHz Aluminum iMac. It boots fine, but I have some issues.
As I have read, I have the same issues as most other users with the same computers. Bad graphics, no sound and no wifi.
I have read all of the posts about how to fix them, but they are way too complicated for me.
If anyone could please explain to me step-by-step how to fix these, I would appreciate it.
Thank you!

I also posted this on the Absolute beginners section, but nobody replied so I thought that this might be a better place to post this. :-D

---

### Post by Aquastus on 2008-03-24
Isn't there anyone who can help me? I can't get the wifi to work. I've tried some of the codes, but it says I'm missing a whole bunch of files and in order to get the files I must connect to the internet, which is exactly what I am trying to do.
I finally got the right resolution for my screen, but it is still quite laggy.
And still no sound.
Sorry, but I just thought that Ubuntu would be an user friendly OS, but right now it seems worse than Windows.

---

### Post by cyberdork33 on 2008-03-24
It is the fact that you are installing it on a Mac that makes it difficult (and will make it difficult with any distro). You will need to connect to the network (hardwire) temporarily to get WiFi working.

I think the sound requires a patch still, the user nicfagn has posted several in the forums here. I believe this issue is fixed in Hardy.

You need to install the proprietary drivers (fglrx) for your graphics to work properly. This can be done with the restricted drivers manager or you can try using [envy]("http://www.albertomilone.com/nvidia_scripts1.html").

---

### Post by Aquastus on 2008-03-25
But I don't have wired connection in my house. Is there any way I could download the necessary files from the internet manually?

---

### Post by cyberdork33 on 2008-03-25
> **Aquastus said:**
> But I don't have wired connection in my house. Is there any way I could download the necessary files from the internet manually?you can do that too, but you will have to make sure you get all the dependencies too:
packages.ubuntu.com

you might be able to use the install cd as a source for some packages. You will have to edit the /etc/apt/sources.list file to use it though (uncomment the cd-rom lines at the top).

---

### Post by Aquastus on 2008-03-26
Well, I found a way to get wired, but things still didn't function.
I downloaded all the necessary packages for Envy to work, but it didn't get me the driver. It downloaded something, but seemingly didn't install it correctly. (I don't remember what it said, but I might get wired tomorrow too so I might be able to tell.) I have the correct pixel resolution, but even moving windows around doesn't display correctly (kind of like games get laggy)
I tried installing wifi (with the help of the article provided in the Apple FAQ section) but after downloading, it said that such a file doesn't exist in the ndiswrapper directory.
The sound patch didn't work too. I couldn't even find that libc6 (?) thing.

---

### Post by paullinux on 2008-03-27
This [howto]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.2_Driver_Manually") helped me get a correct resolution (1050x1680) on my Imac Alu 20 inch.  Do it exactly as posted with the manual install-version.  Do  not use the 'Ubuntu way' .  However, don't expect 3D acceleration.  So no Compiz things yet possible.  

Still looking for the sound though....

---

### Post by magic-neophyte on 2008-03-27
There are ways of fixing the wifi in another thread:

[http://ubuntuforums.org/showthread.php?t=735846](http://ubuntuforums.org/showthread.php?t=735846)

---

### Post by cyberdork33 on 2008-03-27
> **paullinux said:**
> This [howto]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.2_Driver_Manually") helped me get a correct resolution (1050x1680) on my Imac Alu 20 inch.  Do it exactly as posted with the manual install-version.  Do  not use the 'Ubuntu way' .  However, don't expect 3D acceleration.  So no Compiz things yet possible.  

Still looking for the sound though....The stuff in the how to is the same thing that envy does, although it sound like there was an issue when trying to execute it.

---

### Post by paullinux on 2008-03-27
Managed to get sound out of my Imac Alu: [use this howto]("http://ubuntuforums.org/showpost.php?p=3697702&postcount=5"), but use the most recent version of alsa= 'alsa-driver-1.0.16' and 'patch ' alsa-1.0.16-imac.txt' .  After applying this howto my sound is working fine, including the audio jack. I'm using ubuntu 7.10 

I know it looks difficult but at the moment there's no easy way....

---

### Post by Aquastus on 2008-03-27
But I don't know where the patch I'm supposed to copy is. And there is no file called alsa-1.0.15-imac.txt in that directory.
Anyway I'm trying the wifi instructions magic-neophyte gave me. That seems a lot more easier.

EDIT: OK, tried the wifi instructions but it didn't work. I did everything as said and after that nothing happened, nothing changed. Everything stayed the same.

EDIT: I finally got the graphics good. And even compiz works.

---

### Post by e-tip on 2008-03-28
you can use deb package with driver i've made... you need to install it and than reload all alsa modules.
Cheers [File deb]("http://www.e-tip.net/blog/wp-content/uploads/2008/03/alsa-modules-2622-14-generic_1016-0ubuntu22622-1452_amd641.deb")
That packet is for amd64 operating sistems
Later i'll upload package in my ppa and in mactel-linux archive

---

### Post by paullinux on 2008-03-28
Has anyone gotten compiz to work with the radeon HD 2600 graphics card?

---

### Post by cyberdork33 on 2008-03-28
> **paullinux said:**
> Has anyone gotten compiz to work with the radeon HD 2600 graphics card?
Yes, it works fine... Please start a new thread if you have a new question.

---

### Post by Aquastus on 2008-03-30
So there is no way to fix the wifi and sound? Considering that none of the instructions work.
Or is it just that I don't understand them?

---

### Post by cyberdork33 on 2008-04-01
> **Aquastus said:**
> So there is no way to fix the wifi and sound? Considering that none of the instructions work.
Or is it just that I don't understand them?I can't tell. You do not give any information about what you are doing, and what happened. You just state "it doesn't work" that is not very helpful. Since the posted methods have worked for several other people, I would guess that is something you are not doing correctly. e-tip posted a deb file which is pretty much the easiest way to fix it... (just install the package).

For WiFi, you are going to have to give more details. You have to use ndiswrapper and follow the directions for the Macbook SantaRosa:
[https://help.ubuntu.com/community/MacBook_Santa_Rosa#head-2f7056245889dcedf7dc1d286118bfda214af23b](https://help.ubuntu.com/community/MacBook_Santa_Rosa#head-2f7056245889dcedf7dc1d286118bfda214af23b)

If you have a problem with a certain part of the process, you need to state what command failed, and the error message given.

---

### Post by Aquastus on 2008-04-01
About e-tip's tip, I don't know what are alsa modules, so I don't know how to reload them.
And about wifi, I did everything exactly as said in two instructions, but nothing happened. It didn't display any messages. Just nothing happened.

EDIT: The link e-tip gave me is broken.

---

### Post by cyberdork33 on 2008-04-01
> **Aquastus said:**
> About e-tip's tip, I don't know what are alsa modules, so I don't know how to reload them.rebooting should do it.
> **Aquastus said:**
> And about wifi, I did everything exactly as said in two instructions, but nothing happened. It didn't display any messages. Just nothing happened.Please post the output of ndiswrapper -l (thats a lowercase letter L not I) and ifconfig.

---

### Post by Aquastus on 2008-04-01
ndiswrapper -l
```

bcmwl : invalid driver!
bcmwl5 : driver installed
	device (14E4:4328) present (alternate driver: ssb)

```

ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:1b:63:a6:5f:8b  
          inet addr:192.168.1.77  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:63ff:fea6:5f8b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1090 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1183 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:846858 (827.0 KB)  TX bytes:165915 (162.0 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2000 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2000 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100000 (97.6 KB)  TX bytes:100000 (97.6 KB)


```

NOTE: I just upgraded to 8.04.

---

### Post by cyberdork33 on 2008-04-01
> **Aquastus said:**
> ndiswrapper -l
```

bcmwl : invalid driver!
bcmwl5 : driver installed
    device (14E4:4328) present (alternate driver: ssb)

```
NOTE: I just upgraded to 8.04.

Ok, first remove the invalid driver:
```
sudo ndiswrapper -r bcmwl
```

In Hardy there is a bug with ndiswrapper. You have to unload and reload the modules in a different order.

There is a thread here:
[http://ubuntuforums.org/showpost.php?p=4557950&postcount=72](http://ubuntuforums.org/showpost.php?p=4557950&postcount=72)

---

### Post by Aquastus on 2008-04-02
I did everything as said in the instructions you provided and nothing happened.

---

### Post by cyberdork33 on 2008-04-02
> **Aquastus said:**
> I did everything as said in the instructions you provided and nothing happened.
please define "nothing happened". Give output, etc. Did you reboot? ifconfig still shows nothing? is ndiswrapper loading (lsmod)?

---

