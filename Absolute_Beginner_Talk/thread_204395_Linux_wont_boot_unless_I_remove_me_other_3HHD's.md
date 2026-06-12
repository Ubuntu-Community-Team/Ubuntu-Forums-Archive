---
title: "Linux wont boot unless I remove me other 3HHD's"
date: 2006-06-26
forum: Absolute Beginner Talk
---

### Post by IDontKnow9998 on 2006-06-26
When I have my other HDD, it will not boot. There are 2 Ubuntus (why?) and 2 safemodes. All 4 of them will not work. When I click on then, I get the dos thing. Then I get the Linux splash screen:

> Loading essential Drivers.... OK
Mounting root file system...
Waiting for root file system...

I do not get ok on the second or the third. 

If I remove my 3 hdds, it will boot (I am in Ubuntu right now).

---

### Post by jrd on 2006-06-26
And the other one on the same channel is set to slave?

---

### Post by IDontKnow9998 on 2006-06-27
My main is a SATA.....

Then I ahve a other SATA.... Then I have two others: one does not have a jumper the other is slave....

---

### Post by IDontKnow9998 on 2006-06-27
It also will not boot if I remove my 2 IDE HDDs and keep my SATA....

---

### Post by siccness on 2006-06-27
How damn odd. Does it boot with CD-ROM devices?

---

### Post by Xell on 2006-06-27
have you checked bootsequence in BIOS? I have an AUSUSmobo that will not check for any more bootable disks once it's reached the first HDD in the bootsequence.

Also, you may want to check that the SATA is marked as bootable in the SATA controller BIOS.

---

### Post by IDontKnow9998 on 2006-06-27
[QUOTE=Xell]have you checked bootsequence in BIOS? I have an AUSUSmobo that will not check for any more bootable disks once it's reached the first HDD in the bootsequence.

Also, you may want to check that the SATA is marked as bootable in the SATA controller BIOS.[/QUOTE]

Yeah my lanparty is like that 2... I get a hal.dll missing or something like that.... But I know its right or else I could not get into win xp.... Also, grub is on that HDD....

Not to mention I had to setthat back up yesterday because something about my cpu settings changed for some reason...

---

### Post by IDontKnow9998 on 2006-06-27
[QUOTE=siccness]How damn odd. Does it boot with CD-ROM devices?[/QUOTE]
;) 

Yes, booting with cd-rom works perfectly. 

Also, this is not odd for me.

My linux attemps:

1# Resized my main. It worked. But when I updated it, it went on the shitz
2# Tried to install again from the partition I created in step 1. Never worked.
3# Resized the wrong HDD, yet it also did not work.
4# Tried to install on main, but it screwed my HDD, had to format (lost win xp :( :( :( :( :( ).
5# Removed all my HDD but main. Formatd main, installed win xp, resized and installed linux (working, even after update this time).

---

