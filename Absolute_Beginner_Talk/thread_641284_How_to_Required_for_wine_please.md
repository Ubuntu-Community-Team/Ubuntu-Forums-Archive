---
title: "How to Required for wine please"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by marcopolo1981 on 2007-12-15
Hi all. I need some help please.
How exactly do I use Wine??? I've installed it, uninstalled it and installed it again, tried to open .exe files with it and shouted at it! But, still, it just sits there looking useless! How do I get it to work? 
My aim is to install Micro$hite office 2003 pro for the missus. She's not happy with OpenOffice because the shortcuts work slightly differently. I can understand what she means to a degree, because she is paid for knowing all of the shortcuts and ins and outs of excel in particular. She says it would take her too long to mentally switch and learn the same in OOO which would disadvantage her at work. 
Would a virtual machine be a better? If so, which and - again, How?
I really hope somebody can help me, because she will switch back if it's not possible. At the moment, she dual boots. But she says she is always rebooting to switch OS's which is far from ideal.
Thanks in advance and hope
Mark

---

### Post by DezSP on 2007-12-15
Unfortunately, MS Office isn't supported by Wine, it's waist-deep in MS code and so is extremely hard to run outside of Windows. A virtual box might be feasible if your PC is strong enough to support it, otherwise, dual-boot.

---

### Post by popch on 2007-12-15
> **DezSP said:**
> Unfortunately, MS Office isn't supported by Wine, it's waist-deep in MS code and so is extremely hard to run outside of Windows. A virtual box might be feasible if your PC is strong enough to support it, otherwise, dual-boot.

That's not quite true. Wine does support MS Office. However, I do not know from off the top of my head if that particular version (Office 2003) is supported.

I am using wine for MS Access 2000, and it runs reasonably well. I cheated a bit: i bought Crossover Office which wraps Wine into some proprietary code and makes it much easier to install and use, IMO.

OP: Once you have installed Wine, you must install each application you want to use. Of course, there are exceptions: applications which also run in Windows without installing.

In Crossover, there's a special program to install applications. In plain Wine, you run the setup program off the CD, I presume.

---

### Post by jken146 on 2007-12-15
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=2736](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2736)

In short: not possible.  Dual boot or use a VM.  You could try Crossover Office (not sure which versions of MS Office are supported) if you want to pay.

---

### Post by PmDematagoda on 2007-12-15
Currently Cross-Over is known to only support upto MS OFFICE 2003, it cannot be used for MS OFFICE 2007.

---

### Post by bn127 on 2007-12-15
Try here:

[http://wiki.winehq.org/MicrosoftOffice2003](http://wiki.winehq.org/MicrosoftOffice2003)


bn127

---

### Post by marcopolo1981 on 2007-12-15
Thanks for the quick replies.
I have managed to execute the .exe file from the disc (Had to reboot after installing wine - DOH!!!). It has just been installed. In the installation process, it asked for my name, organisation, etc. I gave them. But when I try to run excel, (or any of the others - but I need excel to work!) I get a pop-up saying "Mocro$hite excel has not been installed for the current use. Please run setup to install the application." Can anybody explain how to fix this or why I get this message please?
Thanks again
Mark

---

### Post by popch on 2007-12-15
See this post: Excel 2003 does not yet run in Wine.

> **jken146 said:**
> [http://appdb.winehq.org/objectManager.php?sClass=version&iId=2736](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2736)

In short: not possible.  Dual boot or use a VM.  You could try Crossover Office (not sure which versions of MS Office are supported) if you want to pay.

I second the suggestion to use a VM. Since you already have a dual boot machine, I suggest that you have a look at VirtualBox. They have a very fine HowTo on their site which explains how to use a partition in a virtual machine which has been used for dual booting.

---

### Post by PmDematagoda on 2007-12-15
It is really simple to use a VM, it just takes a bit of time when you look at what the different buttons say, especially the different errors you get;).

I second Virtual Box.

---

### Post by marcopolo1981 on 2007-12-15
Ok. So virtualbox is the next option then. Are there any particular methods I need to use? And do I just use Synaptics package manager and search for Virtualbox? Do I need to download any special packages?
How do I set it Up?
Sorry for the 1001 questions, but I have absolutely no idea.
Mark

---

### Post by PmDematagoda on 2007-12-15
I just installed Virtual Box by downloading it from [here]("http://www.virtualbox.org/wiki/Downloads"). After the install I created a new user and put it into the vbox group. You can do the same or just put yourself into the vbox group, but I do not really know if that works properly.

---

### Post by marcopolo1981 on 2007-12-15
I Have got it virtualbox installed. I've restarted laptop and I am trying to install windows into it. It gave me an error message saying:

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules packages for your kernel and execute '/etc/init.d/vboxdrv start' as root.

VBox status code: - 1908 (VERR_VM_DRIVER_NOT_INSTALLED)

Result Code:        0x80004005
Component:         Console
Interface:             IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}


Does anybody know what this means and how to fix it?

---

### Post by popch on 2007-12-15
How did you install VirtualBox? I used Add/Remove in Ubuntu's Application menu, hoping that this would take care of all prerequisites as well. It did for me with the exception that I had to add my user account to the group which allows users to run VMBox (see a few posts above this one). I don't recall the error message I got before I added my account to that group.

---

### Post by PmDematagoda on 2007-12-15
Yes, I gave the answer in my previous post. 

**_After the install I created a new user and put it into the vbox group. You can do the same or just put yourself into the vbox group, but I do not really know if that works properly._**

You have to do the same.

---

### Post by marcopolo1981 on 2007-12-15
PmDematagoda - sorry, I was still writing my post when you replied. Thank you. 

I have just created the new user and added him to vbox group. 

I'm just about to have another attempt.

Mark

PS I used the add/remove to get vbox

---

### Post by linuxlizard on 2007-12-15
Hey- this isn't wine related, but you might try abiword in add/remove  instead of openoffice. My wife hates open office for the same reason- the shortcuts are very different. She likes Abiword because it has shortcuts that more closely match, and it's faster starting up to boot.

---

### Post by marcopolo1981 on 2007-12-15
hi linux wizard.

Unfortunately, she needs an excel type, not word. Thanks anyway. Do you know if there is a more similar excel equivelant out there? I'm not having much luck setting Virtualbox or Wine up.

---

### Post by popch on 2007-12-15
I have read favorable reports about [http://www.softmaker.de](http://www.softmaker.de). They take much pride from publishing very compatible office products. They are neither open source nor free, however, but the prices of their products are nothing to scream about when you are used to competitors' prices. They also claim that their products are much faster than their competitors'.

---

### Post by PmDematagoda on 2007-12-15
What is the problem you are facing when trying to use Virtual Box?

---

### Post by marcopolo1981 on 2007-12-15
VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules packages for your kernel and execute '/etc/init.d/vboxdrv start' as root.

VBox status code: - 1908 (VERR_VM_DRIVER_NOT_INSTALLED)

Result Code: 0x80004005
Component: Console
Interface: IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

I tried adding the new user as suggested and allocating it to the VMBox group, but this error just comes up everytime. Also, since adding the other user account, my sound has died. Don't know if it's related or not but I'm currently trying to fix that.
Mark

---

### Post by linuxlizard on 2007-12-16
> Do you know if there is a more similar excel equivelant out there?

I don't know for sure how close it matches it as it's been a while since I used excel, but you might try gnumeric, again available from the add/remove. Like abiword, it's a popular alternative to open office.

---

### Post by marcopolo1981 on 2007-12-16
Thank linuxlizard, gnumeric seems to have settled her for the time being. She's been using it all afternoon with no grumbles so far.

Many thanks to all who advised me. I don't know why I can't use Virtual box or Wine. I will continue trying tho - I'm like a dog with a bone!
Mark

---

### Post by AndyCooll on 2007-12-16
> **PmDematagoda said:**
> I just installed Virtual Box by downloading it from [here]("http://www.virtualbox.org/wiki/Downloads"). After the install I created a new user and put it into the vbox group. You can do the same or just put yourself into the vbox group, but I do not really know if that works properly.

1. VirtualBox is in the repositories. It no longer needs downloading directly from the website. 
2. It isn't necessary to create a new user to use VirtualBox. You simply go to System > Administration > Users & Groups > Manage Groups. Look for vboxusers and place a tick against those profiles you wish to give permission to use the app (e.g. yourself).

:cool:

---

### Post by AndyCooll on 2007-12-16
> **marcopolo1981 said:**
> VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules packages for your kernel and execute '/etc/init.d/vboxdrv start' as root.

VBox status code: - 1908 (VERR_VM_DRIVER_NOT_INSTALLED)

Result Code: 0x80004005
Component: Console
Interface: IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

I tried adding the new user as suggested and allocating it to the VMBox group, but this error just comes up everytime. Also, since adding the other user account, my sound has died. Don't know if it's related or not but I'm currently trying to fix that.
Mark

If you open up Synaptic (System > Administration > Synaptic Package Manager) and then do a search for VirtualBox. Check that both virtualbox-ose and virtualbox-ose-modules-2.6.22 are installed. If they are, you can always try a re-installation (right-click on each item and select "Mark for Reinstallation". Also see above for my comments about users.

:cool:

---

### Post by marcopolo1981 on 2007-12-17
> **AndyCooll said:**
> If you open up Synaptic (System > Administration > Synaptic Package Manager) and then do a search for VirtualBox. Check that both virtualbox-ose and virtualbox-ose-modules-2.6.22 are installed. If they are, you can always try a re-installation (right-click on each item and select "Mark for Reinstallation". Also see above for my comments about users.

:cool:

Thanks for the tip, but I still have a problem. In the synaptics, there are two virtualbox-ose-modules. One is "generic" and the other is "server". Which is applicable to my needs? Also, installing the server version updated my kernel to server from generic (???) and now I don't get sound. I had the exact same problem installing the previous kernel - but the same fix doen't work. Normally, I would use terminal and input:

* sudo apt-get install libc6-dev
* sudo apt-get install patch
* wget ftp:// ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2 (remove the space after the double-slash)
* tar xvpjf alsa-driver-1.0.15.tar.bz2
* cd alsa-driver-1.0.15
* ./configure --with-cards=hda-intel,emu10k1
* make
* sudo make install

Is there a different method for this new kernel version? Or have I made a mistake and need to revert?
Thanks, Mark

---

### Post by linuxlizard on 2007-12-18
I don't know anything about how to solve your current virtualbox problems.

I do know this though- I got my copy of virtualbox from the website, rather than the ubuntu repositories. If you click the link below and scroll down you will find an installable binary for gutsy gibbon or what ubuntu you have. Click on it and firefox will ask you if you want to use GDebi Package installer to install it. Just click ok and away you go. Worked great for me, first try, no problems after several weeks of use.

[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

The reason I went that route is because the one in the repositories is the Open Source Edition. Which is great if that's a big deal to you, but to get all the bells and whistles easily, it's simpler to just install the regular binary, which is free, but not entirely open source. The binary will allow you to install virtualbox software inside windows once you have windows installed that make it simpler to use windows inside ubuntu simultaneously.

---

### Post by marcopolo1981 on 2007-12-18
Thanks linuxwizard!
I fixed my sound by just reverting back to the original kernel and then alterred the grub list to make it default. The sound just worked again.
I followed the link, and now have virtualbox with windows installed. I have got office 2003 up and running apart from outlook. It needs internet, but I can't access the web from inside the vbox??? It keeps asking for the drivers for the ethernet and to install the driver disc or download from web. BUT.... I can't download from web - no web
      And when I try to install the drivers from disc, I get an error saying that it isn't compatible with my hardware. It's the exact same hardware I had when I was just a windows user and it worked then??? 
Anyone got any idea how to fix this?
Mark

---

### Post by avanrens on 2007-12-18
You can just use Add/Remove to install VirtualBox but doing it this way you don't get USB. If you need USB go onto the Virtualbox site and download it from there.

---

### Post by Tyke91 on 2007-12-18
it actually isn't the same hardware, it's virtual hardware running for your Virtual Machine.


to get an internet connection if you don't have one already, you would need to download the ethernet drivers for your computer (if you have a dell, you can search it on dell.com)

I don't know why you went through all the trouble though. My virtual box runs perfectly and all I did was install it through Applications>Add/Remove (searched for Virtual Box) I think your problem is that you missed some dependencies earlier on when you were installing and forgot whatever controls ethernet connections. I recommend you just wipe virtual box off and install it thru add/remove (It was put there to be very easy)

---

### Post by AndyCooll on 2007-12-18
> **linuxlizard said:**
> I don't know anything about how to solve your current virtualbox problems.

I do know this though- I got my copy of virtualbox from the website, rather than the ubuntu repositories. If you click the link below and scroll down you will find an installable binary for gutsy gibbon or what ubuntu you have. Click on it and firefox will ask you if you want to use GDebi Package installer to install it. Just click ok and away you go. Worked great for me, first try, no problems after several weeks of use.

[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

The reason I went that route is because the one in the repositories is the Open Source Edition. Which is great if that's a big deal to you, but to get all the bells and whistles easily, it's simpler to just install the regular binary, which is free, but not entirely open source. The binary will allow you to install virtualbox software inside windows once you have windows installed that make it simpler to use windows inside ubuntu simultaneously.

There are actually two versions of VirtualBox available in the repositories. Both "bells and whistles" and the OSE version.

:cool:

---

### Post by linuxlizard on 2007-12-18
Not sure how network works in 2003. XP set it up automatically for me.

I do know if you open virtualbox, and click on the settings icon before you boot your machine, and then click on network in the left column there, mine says:

Adaptor0
x Enable Network Adaptor
Mac Address (and it's got one there)
x Cable connected

If you don't have an x next to network adaptor probably you probably should put one there and maybe cable connected.

---

### Post by marcopolo1981 on 2007-12-20
Hi again.
I have the x next to them, have tried adding x's to the other 3 network tab options so as to try and activate them independantly whilst in Virtualbox, but still won't connect to the net. I have also downloaded the Dell ethernet drivers for this machine and it comes back with an error saying no compatible hardware found. 
Well, atleast she's got her beloved excel working now. She will just have to continue using Evolution as her mail client.:)
Thanks for all of your Advice - it is very much appretiated (I just love the spirit of Ubuntu!!!)
Mark

---

### Post by AndyCooll on 2007-12-21
The Dell ethernet drivers wouldn't make any difference simply because your virtual XP image doesn't actually see or use the hardware on your machine. It sees a "virtual" ethernet card, i.e fake ethernet settings given to it by VirtualBox. Just the same as if you had a top of the range video card, your VirtualBox XP image would still only report back a bog-standard video card because this is what emulated by the VirtualBox app software.

:cool:

---

