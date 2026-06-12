---
title: "Gusty/Vista dual-boot roadblock"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by will_hoaccio on 2007-11-28
Hi, so my computer was running Vista, and i had a free partition lying around so i decided to put Gutsy on it. 
No problems with gutsy per se, but my computer just boots strait into Ubuntu every time, i have yet to see a GRUB screen actually, so... am i up the creek on this?

---

### Post by Partyboi2 on 2007-11-28
You could try restoring the grub, not sure if that helps.
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by ijason on 2007-11-28
no, you're still ok. when you install ubuntu it puts boot flag on the ubuntu partition (this can be changed in >system>admin>partition manager, if you've downloaded gparted through synaptic) and the GRUB screen is loading, it's just going by too quickly for you to see it. you won't need to edit the boot flag, that's just why it's booting straight to ubuntu.

edit /boot/grub/menu.lst with the editor of your choice. look for "##timeout" or similar, and then you can bump that value up to 5 or so, and it'll give you 5 seconds to hit escape at the GRUB loading screen. although, for me, putting a 5 there only gave me 3 seconds. weird. still plenty of time.

---

### Post by will_hoaccio on 2007-11-28
K, thanks for all the help with this. I finally managed to get into GRUB, but to my horror there was no option to boot vista. I know it is, or at least *was* installed on one of my partitions. Is there any way to get GRUB to recognize it?

---

### Post by Partyboi2 on 2007-11-28
you will have to probably add manually vista to the grub menu
have a look at this tread it will explain how to
[http://ubuntuforums.org/showthread.php?t=404202](http://ubuntuforums.org/showthread.php?t=404202)

---

### Post by aun on 2007-11-28
If you want to verify that you still have a vista partition, open a terminal and type:

 ```
sudo blkid
```

This will give you a list of partitions.  If you're lucky you will see a LABEL entry that makes it obvious, but as long as you see a partition of type ntfs, you should be OK.  Now it's just a question of getting in there.

As for that, the GRUB menu entry should say Windows Vista/Longhorn (loader) or something to that effect.  Reboot and see it it's there.  If so, select that, and you're on your way.  If not, when the system is back up, use your file manager of choice and navigate to /boot/grub and open the file menu.1st.  As long as you don't do this as root there is nothing to worry about - you can't edit this as a regular user.  This is the file that defines your GRUB menu.  If there's a windows entry there you probably missed it during boot.

If you decide you need to edit it, be careful.  If you do it wrong you can make the system unbootable.

---

### Post by will_hoaccio on 2007-11-28
ok, i am going to give it a shot after i finished downloading some articles (high value school work and tempermental OSs do not mix).

I still have an NTFS partition (several actually, but wtv)
but just from editing the menu.lst file, the one problem i can see is that i havent specified a kernel, i followed the guide posted earlier, but it didnt adress this. do i need to link to my vista kernel? if so where do i find that?

---

### Post by will_hoaccio on 2007-11-28
Okay, yea, after actually  trying that the option shows up in GRUB @ boot, but when i try it basicly says there is nothing there.

---

### Post by aun on 2007-11-28
No, you wont need to specify a vista kernel.  Also, if you have several ntfs partitions, BE SURE that one of them is not a manufacturer's restore partition.  If you boot into one of those, you're probably in trouble.  I have a couple of different machines with slightly different configurations for this, but probably all you absolutely *need* is an entry like:

```
title Windows XP
	root (hdx,y)
	chainloader +1
```
 
where x is the hard drive number (probably 0 if you only have one), and y is the proper partition.  I'm a little rusty on this, so double check it first.  Also, you'll have to figure out which is the proper partition.

---

### Post by will_hoaccio on 2007-11-29
Im pretty sure i have the right partition selected, my menu .lst reads:

title 		Windows Vista
root 		(hd1,0)
savedefault
makeactive
chainloader +1
 
when i run the diagnostic someone else posted, i get:

/dev/sda1: UUID="3fb55967-0220-4be4-b975-d594f969fc4e" TYPE="ext2" 
/dev/sda2: UUID="9810F5A010F58612" LABEL="South Central" TYPE="ntfs" 
/dev/sda3: UUID="D23804153803F6EF" LABEL="Rexdale" TYPE="ntfs" 
/dev/sda5: TYPE="swap" UUID="d8dc0bdf-18d1-4f57-96b3-f5ce9cfecef5" 
/dev/sdb1: UUID="5AC288B4C28895C3" LABEL="Kormak" TYPE="ntfs" 

I know vista is installed on sdb1 "kormak", but whenever i try to run this in GRUB it says "BOOTMGR Missing", any thoughts?

---

### Post by logos34 on 2007-11-29
try this:
> 
title Windows Vista
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader +1

---

### Post by Partyboi2 on 2007-11-29
This is what I would try

title 		Windows Vista
root 		(hd0,0)
savedefault
makeactive
chainloader +1

---

### Post by aun on 2007-11-29
Hopefully you had some luck with one of the last two suggestions.  The GRUB manual entry for Map explains where these are heading.  

> — Command: map to_drive from_drive

    Map the drive from_drive to the drive to_drive. This is necessary when you chain-load some operating systems, such as DOS, if such an OS resides at a non-first drive. Here is an example:

              grub> map (hd0) (hd1)
              grub> map (hd1) (hd0)
         

    The example exchanges the order between the first hard disk and the second hard disk.

You can find the single page HTML GRUB manual here:

[http://www.gnu.org/software/grub/manual/grub.html]("http://www.gnu.org/software/grub/manual/grub.html#map")

---

