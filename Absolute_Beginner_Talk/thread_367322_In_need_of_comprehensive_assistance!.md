---
title: "In need of comprehensive assistance!"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by nchung66 on 2007-02-22
I'm completely new to linux but would like to switch from Windows XP (i hate it). At the moment, I have a Gateway 6020GZ laptop. I've installed Fedora Core 5 dual boot but I couldn't install the internet so I deleted it. Can anyone please walk me through internet installation? I use wireless right now and when I used FC it didnt recognize my hardware. I've done some research online but I don't really understand the guides out there. 

Also, is the Ubuntu iso really only 1 cd? FC is like 4. How does ubuntu compare to FC? What are the main differences? What are the main differences between linux and windows? What are the essential things I learn first about linux? 

Thanks!

---

### Post by aysiu on 2007-02-22
[One of the few threads I found about the Gateway 6020GZ and Linux](http://72.14.253.104/search?q=cache:HHAaV2P5Cr4J:www.linuxforums.org/forum/linux-laptops/64620-totally-new-linux-i-have-gateway-6020gz-laptop-compatible-fedora.html+gateway+6020gz+linux&hl=en&ct=clnk&cd=1&gl=us&lr=lang_en) seemed to indicate you need to use *ndiswrapper* to get wireless working.

**Graphical way to install [i]ndiswrapper:**

First, go to *System > Administration > Synaptic Package Manager*

Then, in the *Edit* menu (I think it's in there--it's in one of the menus), select *Add CD-ROM*

Put in your Ubuntu CD

Click *Reload*

Search for *ndiswrapper-utils*

Right-click and mark it for installation

Click *Apply*

**Terminal way to install [i]ndiswrapper:**

Go to [the terminal](http://www.psychocats.net/ubuntu/terminal)

Type in these commands: ```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install ndiswrapper-utils
exit
```

**Using *ndiswrapper***:
Then, follow [this guide](http://ubuntuforums.org/showthread.php?t=85378)

Best of luck.

---

### Post by nchung66 on 2007-02-22
I tried ndiswrapper and it was extremely complicated? Can you explain the overall synopsis of ndiswrapper? What exactly is it and what are the commands that I'm typing? Also, how does Ubuntu compare to Fedora? I really liked the gui of fedora and the screenshots for ubuntu seem to indicate that it is inferior to fedora in terms of its gui

---

### Post by aysiu on 2007-02-22
> an you explain the overall synopsis of ndiswrapper? What exactly is it and what are the commands that I'm typing?  I've never used *ndiswrapper* before, but this is the description from [Wikipedia](http://en.wikipedia.org/wiki/Ndiswrapper): > NdisWrapper is an open source driver wrapper that enables the use of most wireless network cards on Linux by implementing the Windows kernel and NDIS APIs and dynamically linking the vendor's Windows drivers to this implementation. This is an important project because many vendors do not release Linux supported drivers for their wireless network cards. There is a list available of all the wireless network cards known to work with NdisWrapper. Also available is a FreeBSD and NetBSD-based equivalent called Project Evil, which functions in the same manner as NdisWrapper &#8212; Project Evil is not available in OpenBSD however, due to the project's anti-binary blob policy.

Most Linux distributions distribute NdisWrapper. I gave you commands as an alternative to the point-and-click instructions. You don't need to use the commands if you don't want to. If you want to understand things, read this:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

> Also, how does Ubuntu compare to Fedora? I really liked the gui of fedora and the screenshots for ubuntu seem to indicate that it is inferior to fedora in terms of its guiNo Linux distro's GUI is inferior to any other Linux distro's GUI. They all use the same GUIs with the same theme compatibility and window managers. You may not like the *default* theme or icons in Ubuntu, but you can easily swap those out for something else (try [http://www.gnome-look.org](http://www.gnome-look.org) or [http://art.gnome.org](http://art.gnome.org)). And beyond Gnome, any Linux distro can use KDE, XFCE, IceWM, Fluxbox, and a host of other window managers.

> Also, is the Ubuntu iso really only 1 cd? FC is like 4. Yes, Ubuntu is only one CD. Many consider that to be a disadvantage, actually, especially people who have a slow internet connection or no internet connection. One CD with no/slow internet makes it very difficult to install software. > How does ubuntu compare to FC? What are the main differences? Linux distros are not really that different when it comes down to it. They usually differ in terms of hardware detection, release cycle, cost, number of CDs, package management, community support, funding, and default applications. > What are the main differences between linux and windows? Linux is open source, varied, and usually cost-free. Windows is closed source, monolithic, and costly. > What are the essential things I learn first about linux? Focus on one problem at a time. Don't overwhelm yourself. Learn things slowly. Don't rush yourself into it.

---

### Post by nchung66 on 2007-02-22
Ok so let me clarify some things. When I try and install a windows component on Linux, I have to use ndiswrapper? Does this mean I can install any driver (video card, etc) on Linux through ndiswrapper? Do I need to have a copy of my windows drivers on a cd? Does it need to be linux format (rpm)? Or do I just type in the set of commands posted above?

---

