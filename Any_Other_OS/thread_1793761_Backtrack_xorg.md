---
title: "Backtrack xorg"
date: 2011-06-30
forum: Any Other OS
---

### Post by uenvymenow on 2011-06-30
I am trying to load up the GUI to install Backtrack 5 and it starts to load after &quot;startx&quot; however, it spits me back to the text mode screen with the following text. Sorry it's a long message.
X.Org X Server 1.7.6
Release Date: 2010-3-17
X Protocol Version 11, Revision 0 Build Operating System: Linux 2.6.24-28-server x86_64 Ubuntu 
Current Operating System: Linux root 2.6.38 #1 SMP Thu Mar 17 22:59:29 EDT 2001 x86_64
Kernel Command Line: file=/cdrom/preseed/custom.seed boot=casper initrd=/casper/initrd.gz text splash vga=7 91-- BOOT_IMAGE=/casper/vmlinuz
Build Date: 08 March 2011 08:22:34AM
xorg-server 2:1.7.6-2ubuntu7.6 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support))
Current version of pixman: 0.16.4
     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
     to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting, (++) from command line, (!!) notice, (II) informational, (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: &quot;/var/log/Xorg.0.log&quot;, Time: Thu Jun 30 00:45:38 2011
(==) Using config directory: &quot;/usr/lib/X11/xorg.conf.d&quot;
(II) [KMS] Kernel modesetting enabled.

waiting for X server to shut down ddxSigGiveUp: Closing log   

root@root:~# 



So that is the error I receive after typing &quot;startx&quot;. Any advice would be much appreciated.

---

### Post by uenvymenow on 2011-06-30
Still can't figure this out... I've tried browsing around on forums, but most problems occur AFTER the installation has completed... Any help is greatly appreciated

---

### Post by Dangertux on 2011-06-30
Try nomodeset in the boot loader configuration.

---

### Post by uenvymenow on 2011-06-30
> **Dangertux said:**
> Try nomodeset in the boot loader configuration.

 Unfortunately I do not see that option available in the boot loader. The following options are all I see: <br />
BackTrack Text - Default Boot Text Mode <-- Typically Use
BackTrack Stealth - No Networking enabled <br />
BackTrack Forensics - No Drive or Swap Mount <br />
BackTrack Text - Default Boot Text Mode <br />
BackTrack Debug - Safe Mode <br />
BackTrack Memtest - Run memtest <br />
Hard Drive Boot - boot the first hard disk <br /><br /><br />

Sorry I am new to Linux. I may just end up trying to work with Ubuntu 11.04.

---

### Post by Dangertux on 2011-06-30
> **uenvymenow said:**
> Unfortunately I do not see that option available in the boot loader. The following options are all I see: <br />
BackTrack Text - Default Boot Text Mode <-- Typically Use
BackTrack Stealth - No Networking enabled <br />
BackTrack Forensics - No Drive or Swap Mount <br />
BackTrack Text - Default Boot Text Mode <br />
BackTrack Debug - Safe Mode <br />
BackTrack Memtest - Run memtest <br />
Hard Drive Boot - boot the first hard disk <br /><br /><br />

Sorry I am new to Linux. I may just end up trying to work with Ubuntu 11.04.

Ok so -- what I mean by adding nomodeset would be doing something like this in your grub.cfg 

```

menuentry "Back Track 5 Revolution" {
        insmod ext2
        set root='(hd0,4)'
        search --no-floppy --fs-uuid --set 9c4488a7-1053-42d1-80d3-48cbc280936f
        linux /boot/vmlinuz-2.6.38 root=UUID=9c4488a7-1053-42d1-80d3-48cbc28093c280936f ro **nomodeset**
        initrd /boot/initrd.img-2.6.38
}

```

Additionally -- if you are new to Linux , I do not suggest starting off with Back Track, it is a very specific distirbution designed for security auditing and penetration testing. There is almost no need for a day to day user to be using it. Also alot of the default policies that exist on regular Ubuntu don't exist in Back Track, those policies are there for your security and should only be forsaken if you know what you're doing with it.

---

### Post by uenvymenow on 2011-06-30
I decided to switch to 11.04 rather the BT Thanks for your help though, will keep this thread in mind for future reference.

---

### Post by Dangertux on 2011-06-30
> **uenvymenow said:**
> I decided to switch to 11.04 rather the BT Thanks for your help though, will keep this thread in mind for future reference.

No problem, just focus on learning more about the operating system. There really isn't anything special you can do with Back Track that you can't do with Ubuntu (note Back Track 5 is based on Lucid).

Back Track, just puts alot of commonly used tools in one place, so it makes it convenient for professionals. 

Good luck in your journey.

---

### Post by SergeyIIh on 2011-07-02
if you use KDE edition, try to run:
rm -r /root/.kde/cache-*
before startx
prooflink: [http://www.backtrack-linux.org/wiki/index.php/VirtualBox_Install](http://www.backtrack-linux.org/wiki/index.php/VirtualBox_Install)

---

### Post by uRock on 2011-07-02
Moved to *"Other OS/Distro Talk".*

Please be aware that the **rm -r** command is dangerous and anything deleted by the command will not be recoverable, so it is imperative to check the syntax before hitting enter.

---

