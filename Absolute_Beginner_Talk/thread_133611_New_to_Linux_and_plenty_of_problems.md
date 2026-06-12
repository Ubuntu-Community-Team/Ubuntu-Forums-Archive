---
title: "New to Linux and plenty of problems"
date: 2006-02-20
forum: Absolute Beginner Talk
---

### Post by XaeroVincent on 2006-02-20
Hello,

I'm very new to Linux and Ubuntu.

I've downloaded and installed Ubuntu 5.10. I now have a dual-boot Ubuntu and Windows XP system using the GRUB bootloader. Ubuntu is nice, but I've run into some ugliness almost instantly. This is probably typical for any linux distrobution, but nevertheless need them solved ASAP.

Heres a list of my problems:

1) Can't access my floppy drive. When I try to mount it I get an error.

2) Can't access my NTFS Windows harddrive. I don't even see two hard drives in the "Computer" panel. I just see "Filesystem". I got some help on this and was able to get a HDA icon to appear, but when I click on it, the contents window is blank.

3) Can't find 3D acclerator drivers for my ATI Radeon 9600 XT. I looked at the DRI project and it seems R-300 chipset support is experimental? Is there any official drivers I can use?

4) Can't play DVDs with the default media player and dont know how to build source packages for others like Mplayer or Xine.

5) Can't login as root. Is it possible to do this or do I have to always use the "sudo" command?

There are probably other things too like printer and scanner drivers. But I haven't checked this out yet.

Any ideas?


Thanks,
Vincent

---

### Post by Zimmer on 2006-02-20
Can help you with item 3. I have a 9600 radeon card.
I followed the instructions here for the  Ubuntu provided drivers.
[https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)
Make sure you read the troubleshooting notes....
As for item 5.
There are ways to become root, but generally it is not a good idea , if you look at my signature there are links to the documentation and starter guides which answer a lot of the questions we all have when we start using Ubuntu.
I have seen posts here before regarding floppy drives,try a search for them,  it may be necessary to alter the fstab file and put in a line to mount it at startup.
Regards

---

### Post by Robgould on 2006-02-20
2. You need to mount your drive. Read the Hremanzone link below. You should also check out the Automatix link it will help you with your dvd and music issues..
 
5. Just use sudo. You only to type your password like once for 15 minutes or 10 minutes...can't remember. Once you get used to it, its not big deal..
 
You could also read the wikki.

---

### Post by bscbrit on 2006-02-20
1) Can't access my floppy drive. When I try to mount it I get an error.

What error message do you get - it might be useful. :D 

2) Can't access my NTFS Windows harddrive. I don't even see two hard drives in the "Computer" panel. I just see "Filesystem". I got some help on this and was able to get a HDA icon to appear, but when I click on it, the contents window is blank.

[https://wiki.ubuntu.com/MountingWindowsPartitions](https://wiki.ubuntu.com/MountingWindowsPartitions)

3) Can't find 3D acclerator drivers for my ATI Radeon 9600 XT. I looked at the DRI project and it seems R-300 chipset support is experimental? Is there any official drivers I can use?

Don't know.

4) Can't play DVDs with the default media player and dont know how to build source packages for others like Mplayer or Xine.

Have you installed all the extras, such as codecs etc.  You have to enable additional repositories:  System -> Administration -> Synaptic Package Manager .... Settings .... Repositories .... Settings .... Show disabled software sources. 

5) Can't login as root. Is it possible to do this or do I have to always use the "sudo" command?

sudo is the preferred method, but if you must 'sudo su -i' will leave you in root mode. (Very Dangerous - be careful. The computer cannot protect you from any mistakes that you make!)

---

### Post by Coelocanth on 2006-02-20
As for 1) You should post the error here. That way some of the knowledgeable folk on the boards can help you figure it out.

As noted, Automatix will install everything for you. However, if you're like me and want to do it yourself, you should check out the following two links:

The [Restricted Formats](https://wiki.ubuntu.com/RestrictedFormats) Wiki entry and the [How To](http://easylinux.info/wiki/Ubuntu#How_to_install_DVD_playback_capability) guide for DVD playback capability. These are what I used to get it working and  although I encountered a couple of minor bumps in the road, I got it up and running in rather shoprt time (and I'm a total Linux noob).

---

### Post by XaeroVincent on 2006-02-20
Wow... replies already? I heard alot of great things about this community and how helpful they are; I can see why. :D 

I'll look through all these suggestions and reply back soon with any success or not.

Cheers,
Vincent

---

### Post by XaeroVincent on 2006-02-26
Success! :D 

I was able to get full 3D acceleration using the ATI fglrx driver, mount my Windows NTFS and floppy drive, get DVD playback with Gxine+CSS, get MP3 support, package converter, printer drivers, WINE (ran some windows apps) and a DOS emulator (ran some DOS apps)!

Excellent!


Regards,
Vincent

---

