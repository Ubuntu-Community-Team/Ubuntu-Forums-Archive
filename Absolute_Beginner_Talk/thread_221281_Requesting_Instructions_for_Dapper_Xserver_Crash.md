---
title: "Requesting Instructions for Dapper Xserver Crash"
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by dpack on 2006-07-22
I used to run Breezy and never had this problem. Since day one of a clean install of Dapper Drake I have had continuous xserver crashes. I scanned around and have found people talking about NVIDIA or missing fonts and changing glx to vesa.

I have an ATI Radeon 8500 video card, not an NVIDIA. When I boot into Dapper and get past the splash screen I am supposed to get the logon screen. 7 out of 10 times I am greeted with a blank screen instead of the login screen. After a while the system automatically reboots. Under syslog I have the following:

```
Jul 22 20:46:38 Antec gdm[5111]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
Jul 22 20:46:38 Antec gdm[4533]: deal_with_x_crashes: Running the XKeepsCrashing script
Jul 22 20:51:00 Antec gdm[4533]: Failed to start X server several times in a short time period; disabling display :0
```

For us noobs, can someone please write out step by step how to resolve this issue, whether it is changing glx to vesa or the missing fonts, or both, or if it is something entirely different? Thanks a bunch!

---

### Post by Kilz on 2006-07-22
> **dpack said:**
> I used to run Breezy and never had this problem. Since day one of a clean install of Dapper Drake I have had continuous xserver crashes. I scanned around and have found people talking about NVIDIA or missing fonts and changing glx to vesa.

I have an ATI Radeon 8500 video card, not an NVIDIA. When I boot into Dapper and get past the splash screen I am supposed to get the logon screen. 7 out of 10 times I am greeted with a blank screen instead of the login screen. After a while the system automatically reboots. Under syslog I have the following:

```
Jul 22 20:46:38 Antec gdm[5111]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
Jul 22 20:46:38 Antec gdm[4533]: deal_with_x_crashes: Running the XKeepsCrashing script
Jul 22 20:51:00 Antec gdm[4533]: Failed to start X server several times in a short time period; disabling display :0
```

For us noobs, can someone please write out step by step how to resolve this issue, whether it is changing glx to vesa or the missing fonts, or both, or if it is something entirely different? Thanks a bunch!

Just a question, what video drivers are you running?

---

### Post by taurus on 2006-07-22
> **Kilz said:**
> Just a question, what video drivers are you running?
It says "I have an ATI Radeon 8500 video card, not an NVIDIA."

Maybe you need to reconfigure your X again...

```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by Kilz on 2006-07-22
> **taurus said:**
> It says "I have an ATI Radeon 8500 video card, not an NVIDIA."

Maybe you need to reconfigure your X again...

```

sudo dpkg-reconfigure xserver-xorg

```

Yes, but is the person running 8.24.8, 8.25.18 or 8.26.18. Are they using the one from the repositories, or one made by the ati-driver-installer. Or are they running just what the Ubuntu disk installed.

---

### Post by SuperMike on 2006-07-22
You aren't by chance using a system with a motherboard video adapter as well as another video adapter, are you? I was. Under Breezy, I used to have an onboard video adapter and I also put in two other videocards. I was using that instead of the onboard video adapter. One was nVidia and the other was ATI. I was running Xinerama mode with special xorg.conf file. I learned that Xinerama doesn't work well in Dapper and isn't scheduled to be fixed until Edgy. When I upgraded to Dapper, my system went blank right when XWindows was loading. Here's what I did to fix my problem as well as return it back to Xinerama mode:

[http://www.ubuntuforums.org/showpost.php?p=1279482&postcount=138]("http://www.ubuntuforums.org/showpost.php?p=1279482&postcount=138")

---

### Post by dpack on 2006-07-23
To answer everyone's questions: How do I tell what driver version I'm running for the video? I went into Device Manager and I see the ATI card listed, but it gives me no driver version info. Whatever driver it is using is what it installed from the Ubuntu disc during the installation.

I have done the **sudo dpkg-reconfigure xserver-xorg** at least 4 times now turn frame buffer on and off and playing with other items. I even did the **sudo dpkg-reconfigure gdm**. No change from that.

No, my motherboard does not have on-board video.

This is so damn odd that Breezy worked just fine. I never had this problem. Good thing I'm dual-booting Windows and Dapper right now. I was hoping to make Dapper my main and only system, but I can't run it at all if it's a game of chance just to get to the desktop! LOL

---

### Post by dpack on 2006-07-25
Any suggestions?

---

### Post by dpack on 2006-08-11
I wiped Ubuntu off my system and downloaded Fedora Core 5. At the beginning of the installation for Fedora it went out and probed my video card and monitor for the GUI install screen. It successfully detected both: ATI Radeon 8500 and NEC MultiSync LCD1920NX. The next steps it listed was to start X Server. My screen went black a few times and then it said it failed to start X Server. I then ended up with the Fedora setup screen with the flat blue background (the non-graphical installer).

I went ahead and just stopped right there. At least I now know it is not Ubuntu. Something has been changed in the X Server since the Breezy release.

I did find this listed bug:
[https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-ati/+bug/37519](https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-ati/+bug/37519)

But it says it's fixed. Well, at least on my system it's not.

Oh well, back to Windows XP we go. Maybe I'll take a look at Vista when it's released. ](*,)

---

