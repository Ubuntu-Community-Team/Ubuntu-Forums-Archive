---
title: "Re-formatting Windows partition from Ubuntu"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by antihero on 2007-02-06
Hey!  I just got a Dell Inspiron E1405 laptop about a month ago.  I dual booted Windows XP MCE and Ubuntu Dapper.  It's my first time running Linux.

I haven't installed much at all on either O/S.  I haven't really had time.  Just the other day I installed the K-Lite codec pack on XP and now I can't boot into Windows.  I can't boot in safe mode, I can't boot to the installation CD, nothing.  I'm getting a blue screen of death with a STOP: 0x000000CA error stating "Plug and Play detected an error most likely caused by a faulty driver."

All of my system diagnostics come back clean and Ubuntu still runs like a champ, so I know its my Windows installation that is crapped out.

I figured my best bet was to reformat the partition that I have Windows installed from Ubuntu.  Can anyone point in the right direction?

My next dilemma is whether to reinstall XP or stick solely with Ubuntu.  I also have Vista.

Thanks for the help!

---

### Post by sankarv on 2007-02-06
There's a tool called GParted in ubuntu. See if its there in your ubuntu system else download from net using synaptic packet manager. You can reformat your windows drive but you will lose all the data. You can install Vista i suggest.

---

### Post by g3k0 on 2007-02-06
You might as well throw in the Vista cd and just format as part of the install process.  You will probably have to reinstall grub afterwards so that you can access your ubuntu again.  

Here is a link if your grub gets killed.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

This is the part you will probably need to use... unless vista doesnt kill grub.. which I doubt

1. Boot from a Live CD, like Ubuntu Live, Knoppix, Mepis, or similar.

2. Open a Terminal. Open a root terminal (that is, type "su" in a non-Ubuntu distro, or "sudo -i" in Ubuntu). Enter root passwords as necessary.

3. Type "grub" which makes a GRUB prompt appear.

4. Type "find /boot/grub/stage1". You'll get a response like "(hd0)" or in my case "(hd0,3)". Use whatever your computer spits out for the following lines.

5. Type "root (hd0,3)".

6. Type "setup (hd0,3)". This is key. Other instructions say to use "(hd0)", and that's fine if you want to write GRUB to the MBR. If you want to write it to your linux root partition, then you want the number after the comma, such as "(hd0,3)".

7. Type "quit".

8. Restart the system. Remove the bootable CD.

---

