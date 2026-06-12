---
title: "Fixing master boot record"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by Pas_sa on 2007-08-10
I recently upgraded my computer. My setup was a 500GB drive for Windows (three separate partitions) and a 120GB drive dedicated to Ubuntu. Everything worked rad.

After the upgrade, Windows of course would no longer boot (expected). Ubuntu of course, did (although while I'm on the topic, I saw no performance difference between my Pentium 4 3.2GHz proc and my new Core 2 Duo E6600 :( )

After some screwy problems with stupid ol' Windows installing again, I managed to get Windows back up and running, only after I disconnected the 120GB drive. I reconnected it and it doesn't go to GRUB anymore.. I'm assuming GRUB was put on the 500GB drive and now Windows Setup got rid of it.

My question is - how can I restore GRUB and get my old boot menu back? My system technically boots off my Games partition now rather than the System partition (E:\ and C:\ respectively) so I'm worried it is more complicated than a simple fix. Windows is on C:\, but the E:\ partition contains my bootloader, because the C:\ partition is actually defined on the drive as partition3 rather than partition1 (no idea why.. Games got partition1 during Windows install.. it works I suppose)..

ie my boot.ini looks like this:
```
[operating systems]
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional"
```

Anyhow, taking all this into account, how can I restore GRUB so I can get back onto my Ubuntu install which is on the 120GB drive, while still being able to boot into Windows without any qualms?

Thanks everyone!

---

### Post by ron999 on 2007-08-10
Hi
When I screwed up my GRUB I got it back using the Ubuntu LIveCD and used the instructions in the thread here:-[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by Pas_sa on 2007-08-10
Those instructions I don't think take into account the problems I'm dealing with - I can't just _recover_ GRUB, my Windows partitions have changed a lot now.

---

### Post by ron999 on 2007-08-10
Hi
Yes, but I also have my Windows installed on a different drive than Ubuntu.
So I have the PC boot from the Ubuntu drive and it displays Ubuntu's GRUB screen.
After I'd restored GRUB I had to add some extra lines to a file named menu.lst.
It's in Ubuntu's Boot folder and inside Grub folder.

The lines I've added are:-

[B]title		Windows 2000
root		(hd1,0)
makeactive
chainloader +1
map (hd0) (hd1)
map (hd1) (hd0)[/B]

To explain this, the **root (hd1,0) **is because Windows 2000 is installed on second drive, first partition.(First drive is hd0, second drive is hd1 etc, similarly with partitions).
The **map** instructions are to fool Windows into thinking that it is installed on the main drive.

---

