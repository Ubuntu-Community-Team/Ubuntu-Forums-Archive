---
title: "Remove Ubuntu completely and reinstall from scratch?"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by Uridian on 2007-04-19
i know there has been a ton of "upgrade vs. fresh install" threads lately what with 7.04 and all, but i think i could use a little more help.

i installed dapper dual booted with windows a while ago just to mess around with linux, then upgraded to edgy a little while afterward and that's been going fine, but i'm from the school of windows and 'upgrades are messy', and i want to wipe out everything and start fresh and try out the default install.  plus, i'm sure i have a bunch of stuff i screwed up while i was learning, extra files i downloaded into places i shouldn't... general clutter, etc... 

anway... i want to completely erase and start fresh.  i have no home partition, just system, a 'data' partition and swap.  i want to clear it all.  i don't remember the install for dapper, but can i format the partition i want to install to during the install itself?  how will grub react?  at this point i have 3 different kernels listed i can boot to, plus safe mode and windows, etc, and it just looks messy.  if i format my linux partition will it clear and 'reset' grub, or do i need to go somewhere else to do that?

on a another note, if i were to abandon linux altogether, could i just remove my linux partitions and give them back to NTFS and be rid of grub as well?  or, again, do i need to go somewhere else to handle grub?

thanks in advance!

---

### Post by devnulljp on 2007-04-19
Yes on most counts.
The grub menu settings are held in /boot/grub/menu.list and can be edited by hand if you like. If youformat that partition it will wipe out those settings, but ubuntu installer usuallyauto recognises your windows install too and adds that. If youwant to remove ubuntu altogether, boot into windows recoveryconsole and type fixmbr, that will reset you to the standard windows boot loader. You can use partiiton magic to fix the partiitons the way you want too.

---

### Post by Skrynesaver on 2007-04-19
> **Uridian said:**
> I have no home partition, just system, a 'data' partition and swap.
A home partition is really worthwhile, I have a tendency to play with a few distributions and having a home partition saves a lot of work.  However I'm sure you have this data backed up safely ;)
> **Uridian said:**
> can i format the partition i want to install to during the install itself?
Yes
> **Uridian said:**
>  how will grub react?  
As you'll be wiping /boot grub will also be reinstalled 
> **Uridian said:**
>   if i format my linux partition will it clear and 'reset' grub, or do i need to go somewhere else to do that?
Yes grub will be reinstalled if you reformat the partitions, to change the number of options in grub you have to edit /boot/grub/menu.list
> **Uridian said:**
> on a another note, if i were to abandon linux altogether, could i just remove my linux partitions and give them back to NTFS and be rid of grub as well?  or, again, do i need to go somewhere else to handle grub?

You would have to reformat them as vfat or NTFS but yes, that would eliminate grub, however you now wouold have no bootloader and would have to do a recovery with your XP disc

---

### Post by moxiot on 2007-04-19
do not forget to install the windows bootloader first. just pop in your windows cd and select "r" for repair when asked. then type in the comand "FIXMBR" to re-install your windows loader. afterwards you can delete the ubuntu partition altogether from windows. that will make it much easier when you reinstall ubuntu. it's what worked for me anyways.

---

### Post by Uridian on 2007-04-19
awesome, thanks all...  that's exactly what i wanted to hear.

oh, ps... my /home is not backed up, but i don't have anything there worth saving... i want to set everything back up for repetition and i haven't actually done any work, just messing around.  perhaps this time i'll set up a /home partition before i reinstall)

---

### Post by s9am_me on 2007-04-19
how do you set up /home on a different partition? I wasn't aware you can do that?  What are the advantages of doing it?  I have only 2 partitions: winxp(20gb) and edgy (20gb)

---

### Post by kodoku on 2007-04-26
> **s9am_me said:**
> how do you set up /home on a different partition? I wasn't aware you can do that?  What are the advantages of doing it?  I have only 2 partitions: winxp(20gb) and edgy (20gb)

During the ubuntu installation process, you manually edit your partition tables to have one partition for the ubuntu system (mount point being "/"), and another partition for home (mount point being "/home")

Having a separate home partition makes it much easier to do a fresh install while keeping all your personal files and configurations (to an extent).  Basically, you can have an edgy installed with a separate home partition, wipe the edgy partition, install feisty on the system partition, set the feisty install to mount the /home partition on your existing home (WITHOUT reformatting), and voila, when you boot up, you'll be missing the applications that you may have apt-gotten before, but the instant you install them, they'll be exactly as how you left them before the reinstallation.

---

