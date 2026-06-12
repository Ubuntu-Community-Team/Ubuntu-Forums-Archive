---
title: "Absolute Noob: Questions about Ubuntu in VMWare"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by Ballping on 2007-09-11
Ok, so i'm absolutely brand new to Linux, i've been wanting to try it out for a long time and finally found a way to bite the bullet and give it a go.

I've installed VMware Player on my Windows XP Pro machine and have installed a pre-created VM of Ubuntu on it.

After figureing out that Zone Alarm wasn't going to play nice with VMWare player and disabling it i've managed to get Ubuntu seeing my internet connection and am now updating the various software on it. (It won't let me upgrade to version 7 of Ubuntu so it looks like i'm stuck playing around with version 6.10 for now)

Now i'm planning on trying to install Beryl cause lets face it, i like pretty graphics, and was wondering if i'd have any issues with trying to install any software on this VM version of Ubuntu, or if it'll act just like a full version of the OS would act.

Also apart of that question the sound inside the Ubuntu VM doesn't work, i'm guessing because my sound card drivers aren't installed on the VM. If i attempt to install those drivers on the VM will that affect my XP Pro system at all, and if not would someone be kind enough to point me to a link where i can get instructions on how to install drivers onto Ubuntu OS?

As you can tell i'm a complete noob to not only Linux but the VM world as well. I'm sure i'll be comming back to these forums quite often as i screw things up. :-)

P.S. the reason i'm running Ubuntu on a VM and not uninstalling windows is first, i'm a huge time gamer, and i want to see how well i can make games work on Linux before i go all out and scrap the windows, and two, i have serious Hard Drive space issues, as well as Money issues which prevent me from buying a Partition software to set up a dual boot system.

---

### Post by jordanmthomas on 2007-09-11
It is my understanding that you will not get 3d acceleration in a VM, so beryl is out.  Otherwise, it should act like a full install, except it uses the VMWare drivers instead of the normal drivers it would use.  

Anything you do in the VM will not affect your Windows installation, so feel free to experiment.

As for getting your sound drivers, have you tried installing the VMware tools?  I haven't used VMware, but I believe I've read something about installing something so the guest OS will use your hardware correctly.  (VM --> Install VMware tools, then double click on the package it plops on your desktop)

After doing that, I believe your sound should work.

**edit** and welcome to the forums.

---

### Post by Irihapeti on 2007-09-11
You don't need money for partition software. Get the Gparted LiveCD. (can't remember the link, but someone else will tell you, or you can google it)

---

### Post by jordanmthomas on 2007-09-11
Also, gparted is included on the Ubuntu CD, so you don't even need to get the gparted CD.  :)

And don't take your results in a VM too seriously when you're considering game performance.  It will probably be abysmal in a VM (see above about 3d acceleration).  If you plan to do much gaming in Linux, don't plan on your Windows games running...just consider it a treat if they happen to.

---

### Post by bodhi.zazen on 2007-09-11
> **Ballping said:**
> Ok, so i'm absolutely brand new to Linux, i've been wanting to try it out for a long time and finally found a way to bite the bullet and give it a go.

Welcome :)

> I've installed VMware Player on my Windows XP Pro machine and have installed a pre-created VM of Ubuntu on it.

After figureing out that Zone Alarm wasn't going to play nice with VMWare player and disabling it i've managed to get Ubuntu seeing my internet connection and am now updating the various software on it. (It won't let me upgrade to version 7 of Ubuntu so it looks like i'm stuck playing around with version 6.10 for now)

Now i'm planning on trying to install Beryl cause lets face it, i like pretty graphics, and was wondering if i'd have any issues with trying to install any software on this VM version of Ubuntu, or if it'll act just like a full version of the OS would act.

Well, at the moment, you can not run Beryl on virtual machines. This is because the virtual machine includes a virtual graphic card and this virtual graphics card does not yet run beryl (ie the virtual machine does not have access to your physical graphics card). So, no beryl/Compiz unless you install.

> Also apart of that question the sound inside the Ubuntu VM doesn't work, i'm guessing because my sound card drivers aren't installed on the VM. If i attempt to install those drivers on the VM will that affect my XP Pro system at all, and if not would someone be kind enough to point me to a link where i can get instructions on how to install drivers onto Ubuntu OS?

This is a "problem" with you VMWare configuration.

[http://www.vmware.com/community/message.jspa?messageID=561283](http://www.vmware.com/community/message.jspa?messageID=561283)

> As you can tell i'm a complete noob to not only Linux but the VM world as well. I'm sure i'll be comming back to these forums quite often as i screw things up. :-)

P.S. the reason i'm running Ubuntu on a VM and not uninstalling windows is first, i'm a huge time gamer, and i want to see how well i can make games work on Linux before i go all out and scrap the windows, and two, i have serious Hard Drive space issues, as well as Money issues which prevent me from buying a Partition software to set up a dual boot system.

You can partition with gparted. The only $$ may be a new hard drive, which are not too much ...

Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)

Gparted is on the Ubuntu live CD (as well as a gparted live CD)

HTH

---

### Post by Ballping on 2007-09-11
> **jordanmthomas said:**
> It is my understanding that you will not get 3d acceleration in a VM, so beryl is out.  Otherwise, it should act like a full install, except it uses the VMWare drivers instead of the normal drivers it would use.  

Anything you do in the VM will not affect your Windows installation, so feel free to experiment.

As for getting your sound drivers, have you tried installing the VMware tools?  I haven't used VMware, but I believe I've read something about installing something so the guest OS will use your hardware correctly.  (VM --> Install VMware tools, then double click on the package it plops on your desktop)

After doing that, I believe your sound should work.

**edit** and welcome to the forums.

Hmm, all i have installed in VMware Player, it doesn't have a VM menu, all it has is a VMware Player menu and there is no option to install VMware tools under it. Could i be running the wrong version of VMware Player or do i need to be running VMware server?

Also Thanks for the extremely fast responce guys. :-) Already i'm loving the features i'm seeing in Unbuntu and now i'm already loving the community.

---

### Post by jordanmthomas on 2007-09-11
You might need to be running VMware Server.  Like I said, I am pretty much unfamiliar with VMs, so sorry for any confusion.  :)

After a quick search, it appears that for the Player you need to go and find the tools yourself.

---

### Post by Ballping on 2007-09-11
> **bodhi.zazen said:**
> Welcome :) 

Thanks!

> **bodhi.zazen said:**
> 

You can partition with gparted. The only $$ may be a new hard drive, which are not too much ...

Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)

Gparted is on the Ubuntu live CD (as well as a gparted live CD)

HTH

Hmm, hell i may just not deal with the whole VM issues then and try and partition my hard drive. What is the absolute minimum i'd need partition wise to run Ubuntu with Beryl and have some room to say, install Oblivion and give it a try running on wine?

Currently i have 12gigs left of an 80 gig hard drive, i want to keep atleast 5 gigs in reserve for xp cause of its whole memory allocation issues.

---

### Post by Ballping on 2007-09-11
> **jordanmthomas said:**
> You might need to be running VMware Server.  Like I said, I am pretty much unfamiliar with VMs, so sorry for any confusion.  :)

After a quick search, it appears that for the Player you need to go and find the tools yourself.

Ok cool thanks. I might end up going ahead and trying to partition my hard drive and try Ubuntu for real since yall have pointed me towards a free partition software, i'm just hoping i have enough disk space to do that.

---

### Post by ubuntu27 on 2007-09-11
Helllo Ballping, welcome to the UBuntu forums and community.

There are few things to clarify:
1) You do not need to buy any partition software as the Ubuntu CD or DVD already has one. [gparted]

2) If you have enough space on your hard drive, you will be able to do a dual boot, meaning you can have two (or more) operating systems in a single computer.
 
3) You can try out Ubuntu (or many other GNU/Linux distribution) without installing by using a LiveCD or a DesktopCD. 

4) In order to get a ubuntu CD or DVD, you will need to download an iso from the ubuntu page, and then burn it as image. [Here is a detailed guide (with pictures)]("http://www.psychocats.net/ubuntu/iso")
[Ubuntu Tutorials:]("http://www.psychocats.net/ubuntu/index.php") A few essential HowTos and links for users starting with [Ubuntu]("http://www.ubuntu.com/") [Linux]("http://www.getgnulinux.org/").

---

### Post by Mach1US on 2007-09-15
Can any one tell me how to properly install vmware tools in Ubuntu , my initial installation failed and now i can't even reinstall it , is there something i should be paying particular attention to ?

---

### Post by bodhi.zazen on 2007-09-16
There are a few how-to' on the web, they are hard to follow.

Boot your Ubuntu guest from your virtual hard drive (nothing in the CD-ROM)

In the VM menu VM -> Install VMware Tools

That will mount the .iso and display two files, a rpm and a tar.

Exit.

naviagate to the CDROM and copy the rpm to your home directory.

Then install with alien :

```
sudo apt-get install build-essential alien
```

Then :

```
alien -i --scripts *.rpm
```

wait ... wait ... 

It appears to be doing nothing ... 

Once installed, the post install configuration is a follows :

```
sudo vmware-config-tools.pl
vmware-toolbox &
```

viola.

---

### Post by Mach1US on 2007-09-16
It did ran the script to intall rpm and after a while it came back with:
```
m@Ubuntu:~/Desktop$ sudo alien -i --scripts *.rpm
dpkg: error processing vmwaretools_6532-44357_i386.deb (--install):
 subprocess pre-installation script returned error exit status 1
[: 45: abort-install: bad number
Errors were encountered while processing:
 vmwaretools_6532-44357_i386.deb

```
I'm guessing it isn't going well ?

---

### Post by Mach1US on 2007-09-16
I have finally created new virtual ubuntu and this time i'm taking advantage Snapshot feature.
In new copy this trick work excellent and now i have VMware tools installed , thanks **bodhi.zazen**.
Regardless can anyone tell me how to enable video acceleration , my virtual ubuntu with just one window open is very chappy and copying and pasteing between gest and host does not work. 
I have allocated 512 MB of mem to it an made sure the tab for disabling acceleration is unchecked but still Very C H A P P P P Y . . .  desktop.
Any help ?

---

### Post by bodhi.zazen on 2007-09-16
You have to be actively running "vmware-toolbox" on the guest *all the time*. You can minimize the window, but not close it. That should enable copy-paste, I am not sure about your video problem though ...

---

### Post by Mach1US on 2007-09-26
Thanks for your help:)
Running vmvare tools in fafct helps with handlong the pointers but still no luck with cuttinfg and pasteing and video accelerfation sill very chappy:(
Any ideas?

---

