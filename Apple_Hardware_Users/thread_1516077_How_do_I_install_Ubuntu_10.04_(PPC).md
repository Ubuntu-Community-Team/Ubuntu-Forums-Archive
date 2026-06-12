---
title: "How do I install Ubuntu 10.04 (PPC)?"
date: 2010-06-23
forum: Apple Hardware Users
---

### Post by DarianMac on 2010-06-23
Hello. How do I install Ubuntu 10.04 PPC on my system? My system at the signature below.
The problem is that nothing appears after boot from a CD. Absolutely nothing, not even a text message. I understand somewhere that may be because Ubuntu 10.04 has nouveau driver. What can I do? May send kernel parameters, so I can start the GUI?
I mention that I checked the disc (MD5 sum), I burn at low speed (4x). Ubuntu 9.04 I have no problem, boots normally (live mode) and installed properly.
__________________

---

### Post by linuxopjemac on 2010-06-23
First of all, try to connect the monitor via the VGA output. I read problems with ADC. Maybe 10.04 has problems with ADC...

---

### Post by DarianMac on 2010-06-23
Weird. I tried Kubuntu 10.04, works in live mode. But Kubuntu has problems after installing it does not work at all, nothing appears, just like Ubuntu 10.04.
Unfortunately, I can not connect via VGA. Anyway, what does it have? I find that it takes the video driver (nouveau), and Kernel Mode Settings. I say this because I installed Fedora 12 PPC and succeed only if they stop KMS. And if enable nv driver instead of nouveau.

---

### Post by linuxopjemac on 2010-06-23
I would go for nouveau with KMS turned off. then you need a working xorg.conf file. We are working in the other thread about this. If you have the same monitor, check that thread.

To stop KMS at boot you have to add the following
```
nomodeset
```

---

### Post by DarianMac on 2010-06-23
Xorg.conf can not reach, if Ubuntu does not start. How can I change the video driver to use nv? Nouveau does not work either I think it my system. How do I disable nouveau and KMS? You can specify the exact sequence of commands?

---

### Post by linuxopjemac on 2010-06-23
why don't you do a CLI installation without X ?

---

### Post by DarianMac on 2010-06-23
Because there is nothing, not even a bash prompt. No CLI or GUI, nothing.

---

### Post by linuxopjemac on 2010-06-23
How did you get Kubuntu installed then ? ;)

---

### Post by DarianMac on 2010-06-23
Was referring to Ubuntu 10.04. I want to install, but nothing appears, as I said. Kubuntu 10.04 is just a test. Him not want to install it, but I mentioned that you spoke of ADC.
I mean the whole problem is related to Ubuntu 10.04, which does not start at all in live mode. How do I set the boot video driver and how do I disable the KMS? Say that a prompt appears ( like the boot: ) but after you press ENTER, there is nothing.

---

### Post by linuxopjemac on 2010-06-23
Just install from a netboot or something, much easier. You can edit X later then.

[http://ports.ubuntu.com/ubuntu-ports/dists/lucid/main/installer-powerpc/current/images/powerpc/netboot/mini.iso](http://ports.ubuntu.com/ubuntu-ports/dists/lucid/main/installer-powerpc/current/images/powerpc/netboot/mini.iso)

[http://mac.linux.be/content/mint-lxde-debian-lenny-ppc](http://mac.linux.be/content/mint-lxde-debian-lenny-ppc)

Just opt for a minimal installation. Once you have a running system, you simply add the desktop:

```
sudo apt-get install ubuntu-desktop
```

Follow the other thread for X issues.

---

### Post by DarianMac on 2010-06-23
Well, thanks for everything. I'll try that.

---

### Post by DarianMac on 2010-06-28
Hello. I'm not good with minimal version of Ubuntu, pure and simple can not. However, Ubuntu can not start 10.04 (Live CD)? All I know is how to set the video driver to the boot prompt. One example is how do this in Fedora 12:

```
boot:** xdriver=nv** nomodeset
```

I emphasized in bold command sets the video driver, in this case nv. What is the command to do the same in Ubuntu? That I want to know.

---

### Post by martinez6341 on 2010-06-28
> **DarianMac said:**
> Hello. How do I install Ubuntu 10.04 PPC on my system? My system at the signature below.
The problem is that nothing appears after boot from a CD. Absolutely nothing, not even a text message. I understand somewhere that may be because Ubuntu 10.04 has nouveau driver. What can I do? May send kernel parameters, so I can start the GUI?
I mention that I checked the disc (MD5 sum), I burn at low speed (4x). Ubuntu 9.04 I have no problem, boots normally (live mode) and installed properly.
__________________
I have ubuntu on both of my mac computers. I had to purchase VMWARE FUSION, runs like 50 bucks

---

### Post by DarianMac on 2010-06-29
I do not think VMWare working on my architecture (PPC). You have no idea how to set up video driver, as shown they can do in Fedora?

I want to set nv driver instead of the nouveau driver, the prompt that appears before you start live mode. That's all I want.

---

### Post by linuxopjemac on 2010-06-29
I would do a CLI installation from the alternate CD and add GUI later.

---

### Post by DarianMac on 2010-06-30
Perhaps you are right. It seems that only the alternate version will work. I tried all sorts of parameters for live cd. Nothing worked. Out of curiosity: why not start in single mode even?
I tried this and it did not work. I thought that single mode does not depend on the video driver, just the CLI.
I typed this:
 
```
Linux single

```
If the single mode operation probably would have solved the problem

---

### Post by DarianMac on 2010-07-07
I got out of patience. I downloaded the alternate version and I installed it. Well, either way does not work. So we could start the installer, I've used, but after finishing the installation and restart, nothing appears on screen.

And I installed with the option "cli-powerpc". So would be no trace of the GUI. But after reboot it behaves exactly like the live version, that nothing appears. How could it be? I think that may have a bug and not work on my configuration. Tell me if others have PowerMac G4 Macs were able to install Ubuntu 10.04.
I think a last resort, to install Ubuntu over OS X and is the only OS on the system. So you think would work? If not, let everything go and moving on Debian, which could perform better.

---

### Post by linuxopjemac on 2010-07-07
Your problem lies in the fact that X does not work. I see in your footer that you have an Apple Studio Display. You have to connect it by VGA, not with ADC. And you need an xorg.conf file, which is suitable for your setup. All PPC computers have this X problem. Tell me which Studio Display you have, maybe I can help you.

---

### Post by DarianMac on 2010-07-07
I have an Apple Studio Display monitor, [this]("http://www.everymac.com/monitors/apple/studio_cinema/specs/apple_studio_display_17_cl.html"). Still do not understand what does it. We installed in text mode, without GUI. And yet the problem persists. What might not work even with a bash shell?

---

### Post by linuxopjemac on 2010-07-07
I am not sure whether it will work with ADC. You might want to try this xorg.conf file. Please let me know if it works:

```
 Section "Device"
        Identifier "Configured Video Device"
        BusID   "PCI:0:16:0"
        Driver  "nouveau"
        Option "NoInt10" "true"
        EndSection

        Section "Monitor"
            Identifier    "StudioDisplay17"
            Option "DPMS"
            HorizSync   30-80
            VertRefresh   50-100
           # 1280x1024 59.89 Hz (CVT 1.31M4) hsync: 63.67 kHz; pclk: 109.00 MHz
           Modeline "1280x1024_60.00" 109.00 1280 1368 1496 1712 1024 1027 1034 1063 -hsync +vsync

           # 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
           Modeline "1024x768_60.00" 63.50 1024 1072 1176 1328 768 771 775 798 -hsync +vsync

           # 800x600 59.86 Hz (CVT 0.48M3) hsync: 37.35 kHz; pclk: 38.25 MHz
           Modeline "800x600_60.00" 38.25 800 832 912 1024 600 603 607 624 -hsync +vsync

           # 640x480 59.38 Hz (CVT 0.31M3) hsync: 29.69 kHz; pclk: 23.75 MHz
           Modeline "640x480_60.00" 23.75 640 664 720 800 480 483 487 500 -hsync +vsync
Option "PreferredMode" "1280x1024_60.00"    
EndSection

        Section "Screen"
            Identifier    "Default Screen"
            Monitor        "StudioDisplay17"
            Device        "Configured Video Device"
                DefaultDepth    24
                   SubSection       "Display"
                     Depth            24
                     Modes             "1280x1024" "1024x768" "800x600" "640x480"
                   EndSubSection
                   SubSection        "Display"
                     Depth            16
                     Modes             "1280x1024" "1024x768""800x600" "640x480"
                   EndSubSection
        SubSection "Display"
              Depth      15
              Modes      "1280x1024" "1024x768" "800x600" "640x480"
           EndSubSection
        SubSection "Display"
              Depth      8
              Modes      "1280x1024" "1024x768" "800x600" "640x480"
           EndSubSection
        SubSection "Display"
              Depth      4
              Modes      "1280x1024" "1024x768" "800x600" "640x480"
           EndSubSection
        SubSection "Display"
              Depth      1
              Modes      "1280x1024" "1024x768" "800x600" "640x480"
           EndSubSection
        EndSection

        Section "ServerLayout"
           Identifier   "Default Layout"
           Screen      "Default Screen"
        EndSection

        Section "DRI"
           Mode   0666
        EndSection 
```

you have to have the nouveau driver installed for this to work:
```
sudo apt-get install xserver-xorg-video-nouveau
```

---

### Post by DarianMac on 2010-07-07
Thank you for your patience and suggestions. To clarify: I can not get into the system, I can not login to create an xorg.conf file or nouveau video driver installed. The problem is that after installing the alternate version in CLI mode, nothing appears that is no bash prompt, to get even the CLI interface. Nothing, just nothing. I want an explanation, depends on the CLI (bash shell) of a video driver?
I thought that in text mode does not take any video driver. Should work, regardless of the presence of an xorg.conf file, eh? Just talk to bash, not GUI. How can I get a bash environment?

---

### Post by dzon65 on 2010-07-07
Same happened to me for an imac G3.Had to edit xorg first.With lenny I installed just the base system,then apt-get install lxde,then nano /etc/X11/xorg.conf
I edited the file and rebooted,worked.So in ubuntu would be (? not sure ) sudo nano /etc/X11/xorg.conf,make the changes,ctrl+x,J (whatever letter of your native language for yes) and reboot,not before you made the changes to the xorg.conf.Should work.
Had to try several xorg.confs though.

---

### Post by linuxopjemac on 2010-07-07
I am afraid you won't have a video signal on the ADC bus. If I were you I would attach a VGA monitor with the DVI->VGA cable.

---

### Post by DarianMac on 2010-07-07
The problem is that I can not get any basic system after installation. Again, I only installed the CLI environment, without anything else. Without GUI desktop. And even so, nothing appears. Understand? Nothing, no error message, no bash prompt login. That trying to say.
How can that not work either bash?

I do not think video is a problem because PPC Fedora 12 works well. I can tell you what I noticed: after I installed Kubuntu test (PPP 10.04) graphically, appears briefly as a splash, which then disappears immediately. Both.

Let me be clear: I did get several versions of Ubuntu (Kubuntu Live, Ubuntu Live, Ubuntu alternate), which we tried. Bash's problem relates to the alternate version.
But other versions do not work:
Ubuntu Live does not start at all when you boot from the CD (not shown anything, as we all told), Kubuntu Live CD starts, but after installing it is not anything (except that brief splash, and this only if inserted nomodeset parameter at boot prompt), also start Ubuntu alternate CD and install it to the text only, but even so nothing appears to reboot.

Do not know what to do.

---

### Post by linuxopjemac on 2010-07-07
For the record, while installing the base system, you had a signal on your monitor?

---

### Post by dzon65 on 2010-07-07
So,you install the basesytem,and there it stops?I mean,during install it asks you to remove the disc,wright?Take it out,click next.(Don't reboot,don't shutdown).And then nothing happens,no prompt,nothing?

---

### Post by DarianMac on 2010-07-07
> **linuxopjemac said:**
> For the record, while installing the base system, you had a signal on your monitor?

Of course I signal, as otherwise it would be installed? But something happens: you get to install kernel, the screen goes black and only if I press a key (any) image reappears. I thought it was a screensaver.

[QUOTE="dzon65"]So,you install the basesytem,and there it stops?I mean,during install it asks you to remove the disc,wright?And then nothing happens,no prompt,nothing?[/QUOTE]

Yes, go to the end. Install bootloader, then remove the disc and asks me to reboot. And then nothing appears.

I mean to say that the alternate version.

---

### Post by linuxopjemac on 2010-07-07
Maybe you have to disable KMS (kernel mode setting):
echo options nouveau modeset=0 > /etc/modprobe.d/nouveau-kms.conf
([https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)).

Were you ever able to have Ubuntu 9.04 installed on this machine? I read that in your footer.

---

### Post by dzon65 on 2010-07-07
There should be:take the install medium out,click on the next button,(again,do not reboot yourself),let the system do it)it should start the commandline.Let's install something:,sudo apt-get update,sudo apt-get install xorg lxde,sudo nano /etc/X11/xorg.conf,edit the file,ctrl+X (you want to save?),Y,ctrl+D,sudo /etc/init.d/gdm start (or service gdm start)
It will now reboot into a login screen (provided you have a good xorg.conf,like I said,tried several myself)
Now,unless something has changed in the 10.04 minimal/alternate installation,this should work.If after the"take medium out,click next evrything just goes black,there's either something with the cd either with the videomode.You could try the 9.10 version.Make sure you burn the iso at 2X speed.

---

### Post by dzon65 on 2010-07-07
It should be pretty much like this:[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by DarianMac on 2010-07-07
> **linuxopjemac said:**
> Maybe you have to disable KMS (kernel mode setting):
echo options nouveau modeset=0 > /etc/modprobe.d/nouveau-kms.conf
([https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)).

Were you ever able to have Ubuntu 9.04 installed on this machine? I read that in your footer.

Command that may have given her a place at the yaboot prompt, before installation? Because the only time they can bring something. I can not do anything during installation and after it ends, nothing is, no login prompt, no message.

Yes, Ubuntu 9.04 installs and boots normally. So Ubuntu 9.10. I have problems only with Ubuntu 10.04.

---

### Post by dzon65 on 2010-07-07
Then it's the disc.Or badly burned ,or something's wrong with the iso.Have you checked it?

---

### Post by linuxopjemac on 2010-07-07
during installation you can enter a tty (CTRL-ALT-F1). There you can issue commands.

---

### Post by DarianMac on 2010-07-07
Yes, I checked the disc and I burned at low speed (4x), so always do.

So can enter configuration commands during installation? I tried this with Kubuntu 10.04.

---

### Post by otakuj462 on 2011-02-04
> **linuxopjemac said:**
> Maybe you have to disable KMS (kernel mode setting):
echo options nouveau modeset=0 > /etc/modprobe.d/nouveau-kms.conf
([https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)).

Were you ever able to have Ubuntu 9.04 installed on this machine? I read that in your footer.

Thanks for this. I was having the same issue, and disabling KMS resolved it for me. PPC Ubuntu on my PowerBook G4 is now working great.

---

