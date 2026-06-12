---
title: "Amarok Problem"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by SilverDragon on 2007-07-10
I'm not sure why Amarok is not working for me anymore. It used to work when I had Ubuntu installed before. 

Anyways, Amarok will load up fine and it will detect my iPod. After connecting the playlists and artists show just like it should. The problem comes when I try to select playlist and drag and drop over to the playlist on Amarok. It will say I need to install mp3 support but will then crash. I get this message on the Knotify The KDE-Crash Handler. 

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1232750896 (LWP 7536)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[KCrash handler]
#6  0xb667da3b in KAudioManagerPlay::KAudioManagerPlay ()
   from /usr/lib/libartskde.so.1
#7  0xb673ad03 in KNotify::restartedArtsd () from /usr/lib/kde3/knotify.so
#8  0xb673b01d in KNotify::KNotify () from /usr/lib/kde3/knotify.so
#9  0xb673b85a in kdemain () from /usr/lib/kde3/knotify.so
#10 0x0804e6bf in ?? ()
#11 0x00000001 in ?? ()
#12 0x0807dc28 in ?? ()
#13 0x00000001 in ?? ()
#14 0x00000000 in ?? ()


Another thing I am confused about is why is it KDE? I thought Ubuntu came with Gnome as a default and I could change it to KDE if I wanted to.

Any insight into my problem would be helpful :-)

---

### Post by SilverDragon on 2007-07-11
The only other thing I believe I did differently is when installing Linux I used the boot parameter noapic instead of nolapic. I don't believe this makes a difference but it might.

---

### Post by sugarland2k on 2007-07-11
Amarok is really a KDE program but it is the most excellent music player.  It will run in Ubuntu with Gnome or Kubuntu under KDE.    

Check this page for adding MP3 and other multimedia codecs, see
[http://ubuntuforums.org/showthread.php?t=413626](http://ubuntuforums.org/showthread.php?t=413626)


:guitar:

---

### Post by sugarland2k on 2007-07-11
On the NOAPIC issue.  If you have installed Ubuntu, you can try this.  But caution - there are a lot of Ubuntu users that know this area better than I do!!!

Turn on your computer and keep pressing "ESC" until you get to the GRUB menu.

Select your kernel with your keyboard arrows (DO NOT PRESS ENTER) and Press "e".
Then you will see 3 lines:

Code:
root (hd0,0)
kernel	/boot/vmlinuz-2.6.12-10-k7 root=/dev/hdb1 ro quiet splash
initrd	/boot/initrd.img-2.6.12-10-k7Select the line which begins with the word "kernel" and press "e" to edit it.

Add one [ONLY ONE i.e. only 1) or only 2) ] of the following things at the end of the line:

1) noapic nolapic
so that it will look like this:

Code:
kernel	/boot/vmlinuz-2.6.12-10-k7 root=/dev/hdb1 ro quiet splash noapic nolapicOR
2) noapic acpi=noirq
OR
3) noapic acpi=off
OR
4) noapictimer
OR
5) noapictimer irqpoll
OR
6) noapic acpi=off
OR
7) noapic acpi=noirq nolapic
OR
8 ) clock=pmtmr notsc
OR
9) notsc

Then get off the text field and press "b" to boot the kernel.

See if it works. 
If Ubuntu DOESN'T boot, it hangs or you can't use your internet connection just reboot and follow the instructions again but try with option 2) or 3), 4), etc. until you solve your problem.

When you find the boot options which work for you [ 1), 2) or 3), etc. ] you have to set them permanently (because the options you have jsut set will only last until you reboot).

---

### Post by MeanStreak on 2007-11-28
> **sugarland2k said:**
> 
Check this page for adding MP3 and other multimedia codecs, see
[http://ubuntuforums.org/showthread.php?t=413626](http://ubuntuforums.org/showthread.php?t=413626)


That URL quoted is dead. Could you please repost the correct link or could we re-open this thread - I'm having the same problem as SilverDragon. I'm running Amarok under Ubuntu 7.10.

The problem comes when I try to select a playlist and drag and drop over to the playlist on Amarok - I get this message on the Knotify The KDE-Crash Handler. Any help to resolve would be much appreciated.

---

