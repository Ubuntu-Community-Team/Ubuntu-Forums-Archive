---
title: "vmware or virtualbox"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by plainjane on 2007-05-12
I am a TOTAL noob.  I have done a search, but couldn't find the answer.  Which is easier to install, setup, use, vmware or virtualbox?  Thanks for the opinoins, and remember I'm really really really new to linux and Ubuntu.  Oh, and does it matter if I want to install XP Home or Pro, because I have both sitting here.  I need to run a scrapbooking program that I just can't get to run under Wine.  
                                    Thanks again!

---

### Post by emnaki on 2007-05-12
Virtual Box is easier to install, since I don't know if it is fixed yet but if you are running Feisty, if you want to get VMWare to work I've heard you need some sort of patch.

---

### Post by oilchangeguy on 2007-05-12
first you'll need to use a legal copy of windows. and virtual machines don't take full advantage of the computers resources (they are aloted a small part of ram, hard drive space, etc.). in my opinion a dual boot setup works best.

---

### Post by veloce on 2007-05-13
> **plainjane said:**
> I am a TOTAL noob.  I have done a search, but couldn't find the answer.  Which is easier to install, setup, use, vmware or virtualbox?  Thanks for the opinoins, and remember I'm really really really new to linux and Ubuntu.  Oh, and does it matter if I want to install XP Home or Pro, because I have both sitting here.  I need to run a scrapbooking program that I just can't get to run under Wine.  
                                    Thanks again!

i'm a vmware server fan.  vmware got easier to install recently with the addition of the vmware modules to the repositories.  I believe it's still a multi step process, but the result is worth it.  I've never used virtualbox so can't comment on relativities.  It has a lot of ardent supporters because it is free as in speech, whereas vmware is only free as in beer.  

An interesting side effect: on my machine, XP runs better as a vm than it did natively! Linux manages memory better than xp and also, relevant to me as I have a centrino duo, linux' smp is so much better it's not funny.

---

### Post by Ziox on 2007-05-13
to install vmware server:
sudo aptitude install vmware-server

to install virtualbox:
use automatix2 or go to [www.virtualbox.org](www.virtualbox.org) and download the feisty deb.

Personally, I believe virtualbox works better because it is able to emulate from the kernel level, where vmware emulates on top of the kernel, which is slower. (don't about sources on this, but I do remember reading about it somewhere)

---

### Post by sefs on 2007-05-17
> **veloce said:**
> i'm a vmware server fan.  vmware got easier to install recently with the addition of the vmware modules to the repositories.  I believe it's still a multi step process, but the result is worth it.  I've never used virtualbox so can't comment on relativities.  It has a lot of ardent supporters because it is free as in speech, whereas vmware is only free as in beer.  


Hi does this mean I can now install vmware server on feisty without using the any-any patch? if so can you give a step by step.  I tried installing the modules from synaptic and then running the vmware install script but it still cannot find any modules and tries to compiles and of course fails.

How did you get it to work on feisty.

Thanks.

---

### Post by OffHand on 2007-05-17
For most users VB is much better than VMWare.

---

### Post by veloce on 2007-05-17
> **OffHand said:**
> For most users VB is much better than VMWare.

What is your basis for this assertion?

Does most mean all?  If not, for whom is vmware better?

---

### Post by veloce on 2007-05-17
> **sefs said:**
> Hi does this mean I can now install vmware server on feisty without using the any-any patch? if so can you give a step by step.  I tried installing the modules from synaptic and then running the vmware install script but it still cannot find any modules and tries to compiles and of course fails.

How did you get it to work on feisty.

Thanks.

No you don't need the any-any patch.  No, you don't run the vmware install script - synaptic does that for you.

Detailed instructions
[LIST=1]
[*]Get a serial number from the vmware site.
[*]Uninstall any copies of vmware (server or player) on your machine 
[*]Add the commercial repository to your apt sources file
```
gksudo gedit /etc/apt/sources.list
then add the line:
deb http://archive.canonical.com/ubuntu feisty-commercial main
save and close
```
[*] run synaptic package manager and install "vmware-server" (it will select the appropriate kernel stuff)
[*] at some point in the install, it will ask you for that serial number, copy or enter it as requested.
[*] Run vmware-console from the Applications - System Tools menu
[/LIST]

Only issues I had are that I don't use the default virtual network settings.  If you want to change them the command is now:

```
sudo vmware-config-network.pl
```

---

### Post by OffHand on 2007-05-17
> **veloce said:**
> What is your basis for this assertion?Personal experience. 
> **veloce said:**
> 
Does most mean all?  If not, for whom is vmware better?
Most is most, not all. VMWare used to have a bit more functionality iirc. This might have changed though.
In any case.... if you just want to run a virtual machine I would pick VB.

---

### Post by sefs on 2007-05-18
Thank you very much worked like a charm so to speak.  I also installed the kernel modules for the vmware-tools, although i didnt see vmware-tools themselves.  I ran into some problems though which is this.  After updating the vmware tools in a windows 2000 and vista vm .. these VM's now crashed... and its due to the SVGA II driver.  They give the vm's a blue screen of death.

Did you get this in any of your windows VMs?

Thanks.

> **veloce said:**
> No you don't need the any-any patch.  No, you don't run the vmware install script - synaptic does that for you.

Detailed instructions
[LIST=1]
[*]Get a serial number from the vmware site.
[*]Uninstall any copies of vmware (server or player) on your machine 
[*]Add the commercial repository to your apt sources file
```
gksudo gedit /etc/apt/sources.list
then add the line:
deb http://archive.canonical.com/ubuntu feisty-commercial main
save and close
```
[*] run synaptic package manager and install "vmware-server" (it will select the appropriate kernel stuff)
[*] at some point in the install, it will ask you for that serial number, copy or enter it as requested.
[*] Run vmware-console from the Applications - System Tools menu
[/LIST]

Only issues I had are that I don't use the default virtual network settings.  If you want to change them the command is now:

```
sudo vmware-config-network.pl
```

---

### Post by Rob Lindsay on 2007-05-18
I have used VMWare Player and Server for sometime to run MS Access, which I need at work, on a Win XP VMX. However I have recently moved to VB and found it relatively straight forward to configure. It is fast and the NAT file sharing works. You have to remember that if after closing the VMX you hibernate ubuntu, file sharing will not be available when you restart from a hibernated state. If you want file sharing, you have to reboot ubuntu and then start VB and your VMX. The other thing that took a little while to sort was USB. However, there is a lead on this forum that gives you the /ect/fstab modification required to make it work. USB on VB is significantly quicker than on VMWare Player/Server.

---

### Post by derred on 2007-05-18
VirtualBox seems to work better for me also.

PS: I know this isn't exactly on topic but:
What scrapbook program are you talking about? maybe there's a way to make it work under wine.

---

### Post by geekphreak on 2007-05-18
I haven't used VirtualBox too extensively, but what I like about vmware option is that if you dual boot with say XP, you can download a free vm converter and convert your physical xp into a vm and use it inside Ubuntu.

---

### Post by kfries6 on 2007-05-18
I have used mostly VMWare on my Dell Laptop.  Its performance has been hit or miss.  I have tried KVM but never got it to work correctly, then I tried Xen, but the version in Ubuntu is too old to use the good administrative tools.  Then I discovered VirtualBox.  I started to eveluate it, and like it.  I am seriously considering a change-over.  I will discuss my reasons, and hopefully this will help you in your decision.

  * First, the graphica user interface in both VMW and VB are very similar.  I like the user interface better in VB by a hair.  It does a better job of showing the current settings in a single view.  I also like the way items (like cd "iso"s) are registered, and easy to reuse.  When setting up many VMs, all running Ubuntu Server for example, it is handy having the iso registered and on the dropdown.

  * The VB command line interface is unbelievable!  You have got to see this to believe it!  Hands down, this makes scripting the management of VMs extremely powerful

  * I like the SDL interface.  Sometimes you just want to run the host's desktop.  VMW makes you install a special client.  The VB package includes the client, and is able to use most if not all of the command line interface to create a very customizable setup.  And because it is all command line, it can easily be attached to a desktop icon.

Areas of concern that are making me go slowly:

  * There is only one... Host only (i.e. no access of the host to the larger network) seems overly complicated in VB.  In VMW it is extremely easy.  However, I have not been successful in doing this in VB.  This could simply my lack of familiarity with VB.  While it is definately harder, since I have yet to get it working, it is unclear exactly how hard it is.

How I use virtual machines:

First of all, I run one VMW machine with WinXP that exports Visio to the desktop via the 2X Application services.  So I rarely ever see the XP desktop.  In addition, I run several Linux test servers used for R&D type development.  None of the virtual machines ever gain access to the outside world.  My machine acts as a Linux fronted network in a box.

I hope that my experience and observations can be of use to you.

Kevin Fries

---

### Post by theicyj on 2007-05-18
I use VMWare Server on Feisty from the repositories.  I have never had any problems with it and the performance for office type programs is not to bad on my  2 year old system.

If you have money to burn, you could always try Crossover Office.

---

### Post by xpod on 2007-05-18
Another Virtualbox vote from me.

I`d  considered the other options but they still seemed a bit complicated for me at the time.Came across VB though and it couldn`t possibly be any more straightforward .

---

### Post by dawdler on 2007-05-18
Has nobody else seen frequent pseudo-random crashes using Virtual Box?  Whenever I run different VM Linux distros, the VM will crash with some sort of malloc exception recorded in VB's log.

Has anyone tried the VMWare workstation edition in Linux?  I use the workstation version in Windows, and it flies!  The product is very stable and performance is super (in Windows).

---

### Post by lazyart on 2007-05-18
This virtualization thing is becoming a hot-button topic.  They seem pretty easy to set up (I've only done VirtualBox as I mistakenly though VMWare was a paid solution).

Doesn't really look like there is a wrong answer here.

---

### Post by veloce on 2007-05-18
> **sefs said:**
> Thank you very much worked like a charm so to speak.  I also installed the kernel modules for the vmware-tools, although i didnt see vmware-tools themselves.  I ran into some problems though which is this.  After updating the vmware tools in a windows 2000 and vista vm .. these VM's now crashed... and its due to the SVGA II driver.  They give the vm's a blue screen of death.

Did you get this in any of your windows VMs?

Thanks.

No, I've never had those sorts of issues.  However, I tend not to use the vmware consol to access my vms - I use gnome-rdp to access the vm across the host only network.  Thus, most of the time I'm not worried about vmware-tools (some of my vms don't even have them installed).

The original reason was that I was using rdp to access some physical machines as well as virtual ones, and it worked with xinerama better than vmware console. Now I use it because it is just more responsive. 

So I start the vmware console, get my vms running, then log into them with gnome-rdp.  I often close vmware console as it just clutters things up!

---

### Post by direwolf08 on 2007-06-27
I started by trying virtualbox.  I was able to install VB fine, but when it came time to install XP, my computer would freeze.  So I switched to trying VMWare server.

Followng the instructions in the [Ubuntu VMWare server How-To]("http://ubuntuforums.org/search.php?searchid=22784507"),

combined with instructions to install the patch found [here]("http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto")

I was able to get Windows XP up and running in VMware pretty quickly.  Might I also say, it runs pretty darn fast!  Boot-up and login on my VM (on an AMD64x2 3800+) is much quicker than a clean, native install on my other PC (a 2.6GHz P4).  Also, internet connectivity, cdrom drive and sound were really easy to get working.  The only thing not configured automatically was the internet, which is taken care of during setup-just choose your network device of choice to connect to the network bridge VMW creates, in my case eth0. Sound was really easy to setup inside the VMware program.  Have yet to try usb devices . . . 

Shortly after that, I had Rosetta Stone installed and running.  I vote VMware by a mile!

---

### Post by tarek on 2007-06-27
Hi, I use vmware, it's easy and works just fine with Windows XP and Ubuntu.

I created an easy tutorial to install vmware on Ubuntu: 
[http://blog.csmonkey.com/2007/06/how-to-install-vmware-server-on-ubuntu.html]("http://blog.csmonkey.com/2007/06/how-to-install-vmware-server-on-ubuntu.html")

---

### Post by Seisen on 2007-06-27
I like VirtualBox myself but that is me. I would say try both and decide which one works better for you.

---

### Post by Eggnog on 2007-06-29
I'm pretty new to the world of Linux and Ubuntu but I've tried both Virtualbox and VMware over the last several days in a effort to see which worked better for me to run XP in order to be able to use Quicken and a couple of other indispensible apps I can't seem to give up.

XP installed just fine in both but Virtualbox gave me USB fits that I couldn't seem to get resolved.  Configuring the USBs in VMware was much easier and so I've stuck with it.  I like both, though.

All in all, I don't think you can go wrong either way.  I'm probably going to give Virtualbox another try just to play around with it.

---

