---
title: "Running window$ XP under Ubuntu. This for real?"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by ROUBOS on 2007-09-18
Hi I looked at this video on youtube (search ubuntu running windows xp) and also found this link:

[https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo](https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo)

So is this really possible? Can I run window$XP under my Ubuntu box without dual boot?

This would be awesome for everyone who wants to run games and Adobe products and yet use Ubuntu as the main OS.

---

### Post by Dr Small on 2007-09-18
You should be able to run windows xp under VirtualBox if you had a mind to.

Dr Small

---

### Post by aysiu on 2007-09-18
Just make sure you have enough RAM!

---

### Post by jombeewoof on 2007-09-18
you can run XP under qemu or vmware, but games do not work well without 3d video. 
which cannot be emulated... yet

---

### Post by ROUBOS on 2007-09-18
so we just install qemu or vmware, then windowsXP through them and then just install adobe products? 

My specs:

Athlon 64 3500+
2GB RAM
ATI RADEON X1950pro 512

QEMU is free, VMWARE not?

---

### Post by irish_flu on 2007-09-18
Looks like a pretty nice machine; you can also use VMWare or VirtualBox; as somebody else noted though, 3D games just don't fly in Virtual Machines (yet).

EDIT:  VMWARE is "free" as in "costs no money" but it is not "free" as in "open source".

---

### Post by ROUBOS on 2007-09-18
so which would be the best one in your opinion?

---

### Post by irish_flu on 2007-09-18
I'm not qualified to say; I have far more experience with VMWare than with the others (read: almost none with the others).

---

### Post by qpieus on 2007-09-18
Vmware and virtualbox are both very good. I happen to like virtualbox better...
Try them both, they're both easy to get running. I have no experience with qemu so I can't offer an opinion on that.

---

### Post by jombeewoof on 2007-09-18
I personally prefer Vmware (not free, even as in beer but there are ways around that, legal ways even)
qemu didn't really work as well as I thought it should have. most likely operator error though.

but yea, that's basically the process, install the vm program of choice then install the os of choice into that VM.

---

### Post by ROUBOS on 2007-09-18
ok cool. will look into it. I hope it does not get me to the poing of re-formating and installin Ubuntu again from the start.

---

### Post by graigsmith on 2007-09-18
you can also use qemu, or kvm.  kvm is similar to qemu  i think, but somehow integrated into the kernel, so that it goes faster.  requires your cpu to have virtuialization tech.

---

### Post by ROUBOS on 2007-09-18
SO if I want to download the Linux host which do I get? AMD64 or get 32bit instead since I'm running 32bit ubuntu. My CPU is AMD64 3500+

---

### Post by HermanAB on 2007-09-18
Here is some dope on VM systems:
Virtualbox is based on Qemu.
Both work, but Virtualbox is more polished.
Both can run WinXP, but Win2003 may crash after a while.

VMware comes in many almost identical flavours:
VMware server is free and can do anything.
VMware player is free and can play pre-existing virtual machines (created with VMware server or VMware Workstation)
VMware workstation has a few extra features and can do anything.
Various other VMware flavours have special tools for datacentres for example, but most people can make do with VMware server and player.

Xen needs special hardware to work properly.  If you have a modern server then it will probably work.

Various other types of virtual tools can run Linux on Linux, but cannot run Windows on Linux, so those are besides the point here.

I bought VMware Workstation and think it was money well spent.  I also use VMware server on many machines.  At least 6 of my machines have VMware of some flavour running on them and have multiple virtual machines ranging from a variety of Linux distributions, WinXP and Win2003.

So why the heck would you run a Linux virtual machine on a Linux machine??? Firstly, this is good for experimentation.  It is very easy to backup a virtual machine.  Just stop the thing and make a tar ball of the machine directory.  With VMware Workstation, one can take a 'snapshot' without stopping the machine.  So I have just about every flavour of Linux at my fingertips - I can just start it up.  

This is also a good way to deploy complex services like email and CRM applications - install once, use many times. It saves you many, many hours of install time when you simply copy a pre-installed system from a DVD onto a server and start it up for a new client.

With Windows 2003, it really comes into its own.  Many companies use Windows  domain authentication and email, but being a Microsoft product, it is unreliable and screws up from time to time.  A VM is easy to backup, so when it screws up beyond repair, simply start up a backup VM from a day or two ago when it was still working.  If it wasn't for tools like VMware, Sysadmins would be crowding the insane asylums...

Cheers,

Herman

---

### Post by asmoore82 on 2007-09-18
I use VirtualBox OSE(**O**pen **S**ource **E**dition) which is completely Free.

I compiled it under my home folder(~/src/) and installed only the kernel module to the system.

Then I created a file "/etc/modprobe.d/virtualbox" to load the kernel module at boot
and set ownership of the virtualbox device(so only "admin" users can use it) ...
```
~$ cat /etc/modprobe.d/virtualbox 
alias virtualbox vboxdrv

install vboxdrv /sbin/modprobe --ignore-install vboxdrv && \
        { while [ ! -e /dev/vboxdrv ]; do sleep 0.2; done; \
                chown 0:admin /dev/vboxdrv ; }

#End of File
```

Then I created a lancher script to run the VBox backend and frontend ...
```
~$ cat ~/bin/VirtualBox 
#!/bin/bash

me="${0##*/}:"
vruntime="$HOME/src/VirtualBox-OSE-1.4.0/out/linux.x86/release/bin"

if [ ! -d "$vruntime" ]; then
        echo "$me" "Virtual Box OSE Runtime Not Found ... Aborting." 1>&2
        exit 1;
fi

cd "$vruntime"
export LD_LIBRARY_PATH=.
./VBoxSVC &
sleep 1
./VirtualBox
kill %%
wait

#End of File
```

And finally, I created a Custom App Launcher on my desktop that calls the script I wrote ...
```
~$ cat ~/Desktop/VirtualBox\ OSE.desktop 

[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Terminal=true
Name[en_US]=VirtualBox OSE
Exec=/home/asmoore/bin/VirtualBox
Icon[en_US]=/usr/share/pixmaps/tsclient.png
Name=VirtualBox OSE
Icon=/usr/share/pixmaps/tsclient.png
```

You'll notice that I have it set to "run in terminal" to check for any extra features(bugs)
in my script ... but I think its about time to take of the training wheels. :D

---

### Post by ROUBOS on 2007-09-18
all this looks a little complex for a noob like me

---

### Post by ROUBOS on 2007-09-18
so is all this scripting necessary? can't we just install and run on demand?
Once installed don't we insert the XP cd and fire away as normal?

---

### Post by HermanAB on 2007-09-18
I would be misleading you if I say that it is easy to install a VM system the first time.  However, it does work and some are easier to install than others.  

In order of easyness to install:
1. VMware
2. Virtualbox
3. Qemu
4. Xen

In order of speed:
1. Xen
2. Virtualbox and Qemu
3. VMware

In order of robustness:
1. VMware
2. Virtualbox and Qemu
3. Xen

Note that you can only install *one* of them and in order to try another one, you would likely have to re-install your host system first.  So be careful which one you pick, since are likely going to be using it for some time unless you have many machines to play with.

'Hope that helps!

Cheers,

H.

---

### Post by ROUBOS on 2007-09-18
sounds like trouble to me. 
I just want to be able to run photoshop and illustrator

---

### Post by HermanAB on 2007-09-18
Photoshop and illustrator run on wine.  So go to codeweavers.com, buy a copy of crossover office and be happy.  It works really well and it is easy to install.

---

### Post by ROUBOS on 2007-09-18
talking about CS3????

---

### Post by Shazaam on 2007-09-19
VMware Player is fun. I did this one rainy day.....
[http://ubuntuforums.org/showthread.php?t=508061](http://ubuntuforums.org/showthread.php?t=508061)

---

### Post by ROUBOS on 2007-09-19
interesting read thanks. in your thread they mention innotek virtualbox too... cool

---

### Post by Brightbelt on 2007-09-19
Check this out for CrossOver. I run PS 7.0 on it and it runs very well. I know it's not CS3 but I have heard that some have tried to run CS3 on CrossOver - I can't say what success there has been or not....

[http://www.codeweavers.com/compatibility/browse/cat/?cat_id=19](http://www.codeweavers.com/compatibility/browse/cat/?cat_id=19)

---

### Post by ROUBOS on 2007-09-19
I was actually after CS3. Anyway I just installed Innotek Virtualbox. Now reading the manual to see how to set it up and get winXP running. 
The install was straight forward... crossing my fingers on seting it up though...

---

### Post by ahmatti on 2007-09-19
For me Virtualbox is by far the best emulator. The installation couldn't be any easier : Just download the ubuntu deb package and double click it to install!

Virtualbox is fast and the newest version even has "seamless mode", which is great!

---

### Post by HermanAB on 2007-09-19
With Virtualbox you should be fine with WinXP.  Nice and fast.

I use VMware since I need Win2003, which crashes on Qemu/Virtualbox.  Sslooooowww, buuut ssuuuree is ssooometimees beeeetteeerrr... :)

---

### Post by ROUBOS on 2007-09-19
DO I need my WinXP CD to install it?

---

### Post by ahmatti on 2007-09-19
You'll need XP cd or cd image.

---

### Post by exile on 2007-09-19
I've had winxp running under qemu and vmware about a year ago. qemu was the more difficult to set up then but wasn't that hard. Vmware was very straight forward. XP ran ok, nothing stellar but there simply wasn't any reason to keep it since there was nothing that XP had that ubuntu didn't (for me anyway). I never tried any games and sound support was scratchy in my experience. Qemu's most difficult part was setting up the networking while vmware requires kernel support - both were easily solvable by reading a good how-to.

Good luck

---

### Post by ROUBOS on 2007-09-19
Cool. Got to go home and get it. Then I guess that the install of winXP appz will be straight forward right? Like inseart cd and just do like you'd normally do in winXP

---

### Post by ahmatti on 2007-09-19
> **ROUBOS said:**
> Cool. Got to go home and get it. Then I guess that the install of winXP appz will be straight forward right? Like inseart cd and just do like you'd normally do in winXP

Yeah, that's right. You can use the cdrom of the host in the virtual machine and also share folders with the host.

I wouldn't recommend using qemu, since it is really quite slow even with kvm. In principle I always prefer the opensource alternatives, but in this case as compared to Virtualbox the speed penalty is just too high.

---

### Post by ROUBOS on 2007-09-19
What about the CD KEY? Will my official cd key of winXP work and activate? Or will it detect it as a different machine and will not activate since my winXP copy has been activated before?

---

### Post by ahmatti on 2007-09-19
I use XP pro so I don't really know , I guess the cd key problem is only for XP home.

---

### Post by ROUBOS on 2007-09-19
I also have XP pro. So it should just activate OK.
Have you tried any adobe apps. ? and or games?

---

### Post by Shazaam on 2007-09-19
My XP Home installs have authenticated fine just don't do a lot of them. I have an activated physical XP install and two vmware installs that are activated.

---

### Post by ahmatti on 2007-09-19
Well at least I didn't have any problems and as far as I know XP pro should work fine. 

Photoshop  CS2 runs fine and so  does acrobat pro. I haven't tried any games, but I have read that 3d doesn't really work.

---

### Post by ROUBOS on 2007-09-19
Cool
All I need is Photoshop and Illustrator to work. I have 2GB RAM. I should let VirtualBox use 1G and ubuntu 1G when running.

Do we have to worry about all those issues with winXP, viruses, os being unstable etc?

---

### Post by Straylit Me on 2007-09-19
Use VirtualBox. VirtualBox is very simple and to the point. VMware is very extensive with a lots of stuff to confiure to make things work better. But because you just want Windows on your linux box im sure your not familar with alot of the features vmware offers. Make your life a little more simple and use virtualbox.

As far as RAM goes, give ubuntu 500mb. 1gb is too much, windows will benefit from it better.

And as far as virus's go, it works like this. The whole operating system and the registry are in a few files. Each of the files with their own extention that only Virtualbox can understand. A virus that comes through linux will not be able to affect the windows operating system because it doesnt know what that extension means. But a virus you would get while using Windows would do the same to winodws as it normally would. Its bittersweet. All your programs will work fine, but so will spyware, adware, and a virus. Try not to think of it as a complex thing. Its simply Windows with imaginary hardware, virtual.

---

### Post by Shazaam on 2007-09-19
Yep. Windows is Windows. But it shouldn't affect your linux host.

---

### Post by anaconda on 2007-09-19
> **ROUBOS said:**
> Cool
All I need is Photoshop and Illustrator to work. I have 2GB RAM. I should let VirtualBox use 1G and ubuntu 1G when running.

Do we have to worry about all those issues with winXP, viruses, os being unstable etc?

Yep, the virtualmachine is vulnerable to viruses etc.. just like real XP, but if you only use adobes products you could do like me. I have setup my virtualmachine NOT to have a network adapter by default.. XP is Lots of safer without a net connection.

If I need net for the virtual machine I just select "VM>removable devices>ethernet1>Connect" this is in vmware.

Another thing is that once you have the virtualmachine setup as you like you might want to make a restore point. So that if you ever get viruses, or trash your XP, you can restore with one click..  Safe way to experiment with windows viruses... :)

---

### Post by mysticmatrix on 2007-09-19
> **ROUBOS said:**
> Cool
All I need is Photoshop and Illustrator to work. I have 2GB RAM. I should let VirtualBox use 1G and ubuntu 1G when running.

Do we have to worry about all those issues with winXP, viruses, os being unstable etc?

Windows is Windows, that won't change. 
The main idea is to keep a snapshot of your virtual machine after you just installed windows and required software(CS3 for example).
As for games, none of the games above DirectX 6.1 runs. This makes AOE2 playable for me :guitar:

So when your Virtual Machine starts crying, just restore it. This is why Vmware and Virtualisation are sucessful. They use your existing system resources well, and also saves headache of running Win*LOSE*

---

### Post by TitanKing on 2007-09-19
In my opinion,

Virtualbox works best! With seemless integration you wont even know you are in Linux. Really worth the try!

---

### Post by ROUBOS on 2007-09-19
OK cool.
So I guess I have to install windows and then drivers for all the hardware as well? 

Dotnet-framework
SB Audigy drivers
ATI card drivers
Mobo drivers etc

???????

If I don't have to install any drivers for hardware then I should be OK with the network disabled in windows. What about automatic windows updates and all? hmmmm

I HATE WINDOWS..... and ADOBE IS CRAP TOO for not making Linux versions.

Is corel better at that at least?

And what about uninstalling windows? Is is as simple as deleting a folder?

---

### Post by irish_flu on 2007-09-19
All I can speak for is VMWare here, but yeah the VM is contained in a big file and a configuration file.

If you're worried about viruses in your VM, and you have plenty of disk space, and you would like network access to the Windows VM, then what I'd do is make a backup (a zip or tar file) of the VM when you know it's in a good state, then if something happens to it (it gets a virus, you break it, whatever man) you can just revert to that copy.

IMHO that's the lovely thing about the VM.

---

### Post by ROUBOS on 2007-09-20
What settings do people normally use for the VirtualBox running winXP.
I used 20GB of HD space and 1.5g RAM. Now the Graphics RAM is set to 8 by default and it says that it should be enough.
What do people use? Should I enter 128???

Can those settings be changed later?

---

### Post by insane_alien on 2007-09-20
you can change those settings later. might as well keep the graphics RAM at 8. it's not as if you can use it to play games(unless they don't reqire 3d).

---

### Post by ROUBOS on 2007-09-20
OK I have isntalled winXP. All sweet.
Now do turn it off, do I shutdown winXP and then closing VirtualBox with Save Machine State???

---

### Post by starfry on 2007-09-20
Use virtualbox and search these forums for Seamless RDP. You can get a setup where you have both XP and Linix "aparently" running together on the same desktop at the same time. Very nice!

---

### Post by ROUBOS on 2007-09-20
I insert a CD and I can browse it in windows but can not copy the data off it.
How do we do that? And how do we access file in the winXP system from Ubuntu?

---

### Post by ROUBOS on 2007-09-20
This will do for sharing:
[http://www.blog.arun-prabha.com/2007/05/21/configuring-virtualbox-for-sharing-and-mouse-control/](http://www.blog.arun-prabha.com/2007/05/21/configuring-virtualbox-for-sharing-and-mouse-control/)

and mounting the CDROM I was doing it OK. But I guess it required a restart of the system

---

### Post by ROUBOS on 2007-09-20
Well I'm a happy man.
Got things working with a little reading onilne and the VirtualBox Manual

I"M A HAPPY MAN :)

---

