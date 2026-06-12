---
title: "Trouble installing Ubuntu Studio 14.04.2 on a Macbook 7,1"
date: 2015-08-11
forum: Apple Hardware Users
---

### Post by RussellT.Rumbone on 2015-08-11
I've been working on this for weeks now and need some help/info. I've been using various versions of Linux for a number of years now, but have no formal computer training or schooling. I'm not the most advanced user, but I know my way around a command line and am a VERY fast learner. I don't just want my problems solved for me, I want to know how/why. Feed me knowledge.

I am trying to install Ubuntu Studio 14.04.2 alongside OsX Snow Leopard on a Macbook 7,1 (2010). I have been using the 64-bit version .iso by using a Terminal to dd the .iso to a USB stick. I was intending on testing a number of distros on it before settling on one, Ubuntu Studio being in the group.

First set of issues are related to booting:
I have trouble getting the Macbook to recognize/boot from certain distros, including Debian and vanilla Ubuntu. They do not appear on the menu found by holding the 'Option (alt)' button, and have not worked when the appeared on the menu of rEFIt or rEFInd. It DOES however recognize the Ubuntu Studio live version with this method, both on the Mac alt menu and rEFIs. Why? If I make a CD of another .iso with xfburn, it loads just fine. I just want to understand why certain distros don't seem to dd like others. UEFI? Location of vmlinuz?

The live version runs flawlessly. Wifi, Keys, SUSPEND/RESUME... everything works as desired. I invoke the installer. 
If I run the installer without an internet connection, the install fails on grub and gives an error message and never fully installs. If I do have a connection, grub installs without a problem, as does the OS (sort of). Logout. Shutdown. Remove USB. Restart.

EFI boots grub. grub generates list: 1.*ubuntu studio (lowlatency) 2.ubuntu studio (generic) 3.Advanced 4&5.OsX 32&64. Lowlatency & Advanced are the only ones that work. Boot lowlatency. Splash screen is chopped and rearranged. Background is one of three things until the wallpaper loads: 1.large black and white pixelated horizontal stripes, 2.the same but with the black stripes spotted with multi-colored tiny pixels, or 3.a chopped (similar to splash screen) version of WHATEVER I WAS JUST DOING ON OSX (webpages, skype calls, program windows) when I boot back and forth. How do I iron this out?
Sleep, Suspend, Hibernate, Resume... all broken. Probably my biggest headache. I would also like to know what the problem is here as well.

I will be happy to supply any reqested information, including Terminal output, screenshots, logs.... whatever. Just be specific in your request on where/how to get you the information. Or just tell me why I'm wasting my time.

Thanks in advance.

---

### Post by TheFu on 2015-08-11
I don't know anything about Apple hardware but expect the output from **boot-info** would be very helpful.

---

### Post by RussellT.Rumbone on 2015-08-14
> **TheFu said:**
> I don't know anything about Apple hardware but expect the output from **boot-info** would be very helpful.

Thank you for your prompt reply, I appreciate your time. I would be happy to give you the output you desire.

```
****:~$ boot-info
boot-info: command not found
```

My package manager has a package named "boot-info-script"... is this what I need to bring you said output? Please remember my need for specificity, as I have read many forums, but never asked anyone for help before. I want to follow forum protocol, I'm just not used to fetching info for pasting. Pardon any misuse on my part. And thank you again for your time.

---

