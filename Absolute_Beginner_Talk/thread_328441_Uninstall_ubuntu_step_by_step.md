---
title: "Uninstall ubuntu step by step"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by taco_truck on 2006-12-30
Ok.  I have ubuntu 6.06 dual booted with windows xp.   I need to uninstall ubuntu and resize my xp ntfs partition to its max size.  I think (37Gigs)  Can someone please walk me through the process *step-by-step* of uninstalling ubuntu and reinstalling windows just like i had it before..  I do have a xp reinstall disk.

Thank you.

---

### Post by raul_ on 2006-12-30
Just slam the Live CD into the drive and load it. Then go to System->Administration->Gnome Partition Manager (or something like that), format your ubuntu partition (the ext one) and then resize the ntfs partition...it's pretty straightforward...I hope you're coming back to ubuntu though, right? :)

---

### Post by taco_truck on 2006-12-30
Dont i have to put the windows disk in and do some recovery fixmbr command?  When does that come into play?

---

### Post by raul_ on 2006-12-30
If resizing is the only thing you want to do, i don't think that's necessary

---

### Post by d3v1ant_0n3 on 2006-12-30
> **taco_truck said:**
> Dont i have to put the windows disk in and do some recovery fixmbr command?  When does that come into play?

After you've deleted the Ubuntu partition. reboot the comp with the Windows restore disk in, keep wading thru the options pressing seemingly random F keys until it asks you if you want to Repair an existing installation. Select that option and it will dump you into a recovery console where you do the whole fixmbr thing. Then reboot and all *should* be back to its previous XPness.

---

### Post by taco_truck on 2006-12-30
So you are sure i format the linux partition and not erase it?  Or is that the same thing...

---

### Post by raul_ on 2006-12-30
i still can't see why resizing it with gparted wouldn't do the trick :P

---

### Post by d3v1ant_0n3 on 2006-12-30
> **taco_truck said:**
> So you are sure i format the linux partition and not erase it?  Or is that the same thing...

If I'm correct (you might want to wait for confirmation of that) you need to just delete the partiton. When all is well with windows again you can resize your NTFS partition back to full size using the now free disk space. If you reformat the Ubuntu partiton it will just leave you with an extra partition.

---

### Post by taco_truck on 2006-12-30
OK.  Lemme make sure i got this down.

1)Erase/Format linux partition w/ gparted
2)Resize windows/ntfs partition w/ gparted
3)Go to recovery console and do fixmbr
4)Reboot and ubuntu is completely off

Is that all correct?  :D

---

### Post by raul_ on 2006-12-30
I think so :mrgreen:

---

### Post by taco_truck on 2006-12-30
Thanx.  I really need a definite answer like yes or no because i dont want to screw something up.  I will probably try it tomorrow.  I am going to bed now and i wanna wait to see what other people say as well.  But thank you Raul and deviant for your help.  :p

---

### Post by raul_ on 2006-12-30
I *still* don't think that you need to go through the recovery console thingy in XP, and that deleting the ubuntu partition and resizing it would do the trick, but i don't think there would be any harm in doing it. this is a definite "yes" answer btw

---

### Post by d3v1ant_0n3 on 2006-12-30
> **raul_ said:**
> I *still* don't think that you need to go through the recovery console thingy in XP, and that deleting the ubuntu partition and resizing it would do the trick, but i don't think there would be any harm in doing it. this is a definite "yes" answer btw


Well AFAIK, by just removing the Ubuntu partition (deleting/formatting/however), you're not removing Ubuntu's GRUB- so you get GRUB Error 17 (?) where it can't find an OS that it's expecting. You need to run fixmbr to reinstall Windows MBR.

I might be very wrong, but I'm sure thats what I've had to do in the past. Although it *IS* saturday night;)

---

### Post by raul_ on 2006-12-30
oh well, if you have done it :) i confess that i switched to ubuntu and never looked back. I just keep resizing my ubuntu partition by taking space from the windows one :mrgreen:

---

### Post by eddin on 2006-12-30
Firstly on resizing the ntfs partition, you will need to first delete the Ubuntu partition. I don't think it's necessary to re-format it before the deletion, but if you want to be safe, then by all means do that. Resize thereafter. (All this can be archieved with gparted.)

Grub would still be installed in your MBR but you would not be able to boot using Grub because grub relies on /boot/grub/menu.lst to determine where to partitions are and this file is gone once the Ubuntu partition is removed. 

Now to remove grub, google usually return results that tell you to use the windows recovery disk. if you don't have one, download a utility call Super Grub disk. The program comes in an iso file, burn it into a CD. The CD is then bootable. You need to
1) delete the MBR, and
2) make the windows partition bootable.
After you have done so, restart your computer. After the POST, your BIOS will first try to read the MBR and upon finding it empty, it looks for a bootable partition and boot from there.

---

### Post by taco_truck on 2006-12-31
Thanx guys i got everything working.  :D 

But i have noticed it does take a lot longer for windows to load..

---

