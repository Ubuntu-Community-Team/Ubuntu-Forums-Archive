---
title: "Vista won't startup now that ubuntu has been installed"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by Andross707 on 2007-06-22
Luckily I backed up before hand, but does anyone have something that could help me out with this error so maybe I won't have to go through with a complete restore from backup CD?

As far as I can tell the error feels fairly random. I booted into Vista from the grub loader as I had done yesterday (I'd say about 3 times I had gotten into Vista and exited this same way before with no issues). Today though, when I booted Vista I decided to work with some of my Max/MSP tutorials I have and use my USB MIDI keyboard. Everything was going fine until I started to get this problem where the left channel from my headphone port distorts no matter what the volume (I'm not 100% sure what the cause of this is but it was never really a problem because usually I can just restart and the problem will be fixed). So I decided to restart by pressing the start button and selecting restart after closing Max/MSP (one thing that I did notice was odd was that vista was requesting drivers be installed for a new 'unknown device' whenever it boots and on previous boots I tried to search for the driver and it couldn't find it etc so on this boot I just told it to not ask me about this device(I don't know what device its talking about the MIDI keyboard never needed drivers before and this message only started to appear after installing ubuntu on a separate partition)). 

Something that may be a problem is that I didn't unplug the MIDI keyboard before I restarted, but nonetheless for some reason I get a blue screen when Vista is loading (the screen that says microsoft corp with the scrolling green bar). Its a stop error (if that helps) and after a few seconds on the blue screen the computer restarts and I can't even load safeload or any other boot options any more.

So here I am in Ubuntu thinking about going upstairs to get the backup discs I burned but wondering just wtf happened as I'm guessing this is something Ubuntu related (though I may be wrong).

Any help is appreciated.

---

### Post by Crafty Kisses on 2007-06-22
> **Andross707 said:**
> Luckily I backed up before hand, but does anyone have something that could help me out with this error so maybe I won't have to go through with a complete restore from backup CD?

As far as I can tell the error feels fairly random. I booted into Vista from the grub loader as I had done yesterday (I'd say about 3 times I had gotten into Vista and exited this same way before with no issues). Today though, when I booted Vista I decided to work with some of my Max/MSP tutorials I have and use my USB MIDI keyboard. Everything was going fine until I started to get this problem where the left channel from my headphone port distorts no matter what the volume (I'm not 100% sure what the cause of this is but it was never really a problem because usually I can just restart and the problem will be fixed). So I decided to restart by pressing the start button and selecting restart after closing Max/MSP (one thing that I did notice was odd was that vista was requesting drivers be installed for a new 'unknown device' whenever it boots and on previous boots I tried to search for the driver and it couldn't find it etc so on this boot I just told it to not ask me about this device(I don't know what device its talking about the MIDI keyboard never needed drivers before and this message only started to appear after installing ubuntu on a separate partition)). 

Something that may be a problem is that I didn't unplug the MIDI keyboard before I restarted, but nonetheless for some reason I get a blue screen when Vista is loading (the screen that says microsoft corp with the scrolling green bar). Its a stop error (if that helps) and after a few seconds on the blue screen the computer restarts and I can't even load safeload or any other boot options any more.

So here I am in Ubuntu thinking about going upstairs to get the backup discs I burned but wondering just wtf happened as I'm guessing this is something Ubuntu related (though I may be wrong).

Any help is appreciated.

The first thing we need to do is figure out where the Windows partitions are in the partition table. You can do this by typing:
```
sudo fdisk -l
```
Then you should probably delete the Windows partition  and reinstall it, this happened to me before when I used to use Windows.

---

### Post by raul_ on 2007-06-22
> **Codename said:**
> Then you should probably delete the Windows partition  and reinstall it, this happened to me before when I used to use Windows.


Don't be so dramatic mate :)

---

### Post by Lord Illidan on 2007-06-22
Why oh why is it that when something goes wrong with Windows, we always blame Ubuntu? People have been having issues with Windows since before Linux was installed on their computer!

---

### Post by Andross707 on 2007-06-22
(sudo fdisk -l) results:

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         848     6809600   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         848        9931    72953856    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3            9931       12063    17123400   83  Linux
Partition 3 does not end on cylinder boundary.
/dev/sda4           12063       12161      793800    5  Extended
Partition 4 does not end on cylinder boundary.
/dev/sda5           12063       12161      793768+  82  Linux swap / Solaris

---

### Post by Crafty Kisses on 2007-06-22
> **Lord Illidan said:**
> Why oh why is it that when something goes wrong with Windows, we always blame Ubuntu? People have been having issues with Windows since before Linux was installed on their computer!

It's because when something goes wrong when they install Ubuntu, what else are they gonna blame? ;)

---

### Post by Andross707 on 2007-06-22
As an aside, I didn't mean to come off as blaming Ubuntu for this problem, but I just assumed that there is something I may have done wrong with the installation or partitioning or something that might cause vista's booting system to stop working because I never messed with the booting or partitioning or anything until installing Ubuntu.

(If you're wondering about my partitioning, I first backed everything up onto CDs and then used vista's partitioning system to shrink its partition and then use the free space created for ubuntu using the install to largest continuous free space feature) Its also strange to me that I could get in and out of Vista fine 2 days ago but just yesterday I now get bluescreens.

---

### Post by molly_001 on 2007-06-22
Andross707 --

Is your problem resolved at this time?    Friday 22 June / 22:31 UTC

---

### Post by Andross707 on 2007-06-22
> **molly_001 said:**
> Andross707 --

Is your problem resolved at this time?    Friday 22 June / 22:31 UTC

No not yet, though I'm about to go upstairs and get my backup CDs to see if there's an option to simply restore vista back to a state where it worked and leave my harddrive intact....but if someone has a solution other than that don't hesitate :)

---

### Post by Trojanman49 on 2007-06-22
I hope this can help.  I had vista installed first and then I could not see the boot option for it.  A buddy and I found this on the web and it worked for me.  It was rather easy.  I don't really have the time to explain it all but I hope it helps.


[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

:D

---

### Post by CheShA on 2007-06-22
> **Codename said:**
> 
Then you should probably delete the Windows partition  and reinstall it, this happened to me before when I used to use Windows.


If you do this, Windows will overwrite your MBR and you'll end up not being able to boot your Linux instead!!

---

### Post by Andross707 on 2007-06-22
yea I just restored from my backup CDs and I'm about to backup in the service partition given by Lenovo.....though I still have no idea how this error occoured but i'm not plugging in anything until I backup again.

---

### Post by molly_001 on 2007-06-22
I have not followed or read much of the above thread, but am just adding a few notes regarding dual-booting when there's trouble:

GAG Boot Manager is a bootable CD that you can use to install onto the MBR, an iconic way to boot into partitions which otherwise won't boot.  (Press Penguin icon for booting into Linux, press Flying Windows icon to boot into NTFS volume, etc.)  It doesn't always work, but when it does it's beautiful.    I've been using GAG all day (by installing it into the MBR) to boot into a seriously frizzled Windows installation; it was the first step in eventually getting me to be able to boot into Safe Mode.  (I'm leaving out several steps after GAG.)
I recovered about 80% of data and now its giving me NTLDR grief.  But at least I got that much.

---

