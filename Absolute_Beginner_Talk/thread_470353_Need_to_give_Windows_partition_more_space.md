---
title: "Need to give Windows partition more space"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by nabla on 2007-06-10
Hi,
   I have a dual boot setup with Windows XP in the beginning of the drive (20 GBs), followed by Ubuntu root partition (10GBs) and a home partition (~40 GBs).  I need to give windows about 5 GB's more, so I would need to "shift" the root and home partitions about 5 GBs in order to free some for windows. What would be the best way to go about this?, can anybody point me to some tutorial? I've looked all over the place and googled it for a while and havent come up with anything.

thanks.

---

### Post by p_quarles on 2007-06-10
[COLOR=Black]I'm fairly new to this, but I'm pretty sure that resizing any used partition is pretty dangerous to your data. Unless someone else comes along with better advice, I'd suggest backing everything up and reinstalling both XP (first) and then Ubuntu. [/COLOR]

---

### Post by nabla on 2007-06-10
Well if anything I would only need to reinstall Ubuntu as I can easily resize Windows If I did not care for my ubuntu partition.
So thats too much work, I already have Ubuntu the way I want it. I dont have much in my Home partition and what i have I can move over to my NTFS partition before doing this. If there is a way to do this even if its risky I'll take it, worst case I'll have to reinstall Ubuntu only.

---

### Post by 444 on 2007-06-10
Backup any way you go. You shouldn't have to reinstall XP unless some accident happens to it in the process. GParted does resizing. You can't move the start of a partiton though.

Route #1: Reinstall Ubuntu (easier), after you delete the old one expand Windows partition (with gparted?), then reinstall.

Route #2: Make an image of the Ubuntu root partition, save it to windows partition, expand windows partition into root partition's place, shrink home partition by 10gb, copy image to this last 10gb.

---

### Post by p_quarles on 2007-06-10
[COLOR=Black]Looks like 444's advice is the "better advice" I referred to. Follow those directions.

I'll add one thing, though: make sure you backup your Ubuntu /home files to a CD or a USB drive. This is where all your personal settings are stored, and being able to reload them will save you a lot of time. 
[/COLOR]

---

### Post by 444 on 2007-06-10
Reading your second post...

Route #3, as root do:
 tar cf /media/windows/home.tar /home/* #make copy of home on windows drive since it's small

Then delete home partition. Make a new root and home partition, then copy the old root to the new one from a live cd, and the extract the copy of home to the new home. Then  you'll have to reconfigure grub so it boots from the new partition. After you move over to the new partition succesfully, delete the old one and expand windows to take the space.

---

### Post by nabla on 2007-06-10
> **444 said:**
> 

Route #2: Make an image of the Ubuntu root partition, save it to windows partition, expand windows partition into root partition's place, shrink home partition by 10gb, copy image to this last 10gb.

How would I go around making an image of the root partition and then restoring it?

---

### Post by 444 on 2007-06-10
I was thinking using the dd command, but then I realized that using the tar command same way as was done with the home partition would be better. So run that command from a live cd, it's easier that way. And then create the new root partiton then extract the copy to it. But then there's the problem of there being NTFS write support on said cd... could be solved with some juggling, heh.

---

### Post by nabla on 2007-06-10
Thanks 444, looks like that was what I was looking for. But a quick question, would doing it that way retain my file permissions ?

---

### Post by konungursvia on 2007-06-10
Just download gparted and burn its iso using "gnomebaker". Then boot with the gparted disk in the cd drive, and shrink your x partition, and grow the windows partition. Then apply. It should be safe.

---

### Post by 444 on 2007-06-11
When you run tar to extract as root it preserves permissions (as a user you have to use the -p option).

---

### Post by Tripletaco on 2007-06-11
nabla,

I partitioned my XP for about 21 GB on a 80 Gb harddrive. Ubuntu takes the rest of the space.   I also need more room for XP.  I was wondering how the advice these guys gave worked for you?

---

### Post by Tripletaco on 2007-06-12
Konungursvia,

I did what you said and it worked good for me.  No problems so far!  Hope I didn't speak too soon.  thanks!

---

### Post by nabla on 2007-06-13
> **Tripletaco said:**
> nabla,

I partitioned my XP for about 21 GB on a 80 Gb harddrive. Ubuntu takes the rest of the space.   I also need more room for XP.  I was wondering how the advice these guys gave worked for you?

Hi, sorry for the late reply, I haven't done this yet as I haven't found the time, hopefully this weekend, I'll report how it went.

---

### Post by nabla on 2007-06-13
> **Tripletaco said:**
> Konungursvia,

I did what you said and it worked good for me.  No problems so far!  Hope I didn't speak too soon.  thanks!

Good stuff, althought what Konungursvia said doesn't work for me as I cant just expand the windows partition.

---

### Post by Tripletaco on 2007-06-15
nabla,

No, I couldn't just expand it either, until I shrunk Ubuntu.  Both XP and Ubuntu have been working good for a few days now!  I was able to defrag my XP now that I made a little room for it =).  

This would probably be another topic, but does anyone know if you ever need to defrag Ubuntu/Linux?

---

### Post by nabla on 2007-06-15
> **Tripletaco said:**
> nabla,

No, I couldn't just expand it either, until I shrunk Ubuntu.  Both XP and Ubuntu have been working good for a few days now!  I was able to defrag my XP now that I made a little room for it =).  

This would probably be another topic, but does anyone know if you ever need to defrag Ubuntu/Linux?

Great that it worked for you, I suppose you had to edit your grub config right?

On the defragging, Linux file systems are much much more resilient to fragmentation by the way it allocates hard disk space, so no you don't have to defrag Ubuntu.

---

