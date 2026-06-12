---
title: "dual booting woe: windows ubuntu"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by lumarh on 2007-04-05
Ok guys, ive had no luck at all trying like a maniac to dual boot windows with ubuntu.

after no success with ubuntu-master and windows-slave on primary  I have set up my drives as follows: 

Master - Ubuntu
Slave - nothing

Master - Windows
Slave - optical drive 

Is this the easiest way to dual boot? it seems there should be no interference between the OS's this way. 

I already have ubuntu installed, i did have windows already on the drive but i think i wrecked it (NTLDR is missing, couldnt fix it). What steps should i take from this position to be able to dual booth windows and ubuntu from grub. please note that installing windows seems to knock grub off, so if possible include steps to fix grub back up?
thanks all, this is really stressing me

---

### Post by Doug11 on 2007-04-05
How is your setup. Do you have two HDD or one that is just partitioned. Did you have to resize your windows partition or did you already have it partitioned?

---

### Post by Mowcius on 2007-04-05
If you have 2 hard drives:

if you take one out (say the one with windows booted on it) does ubuntu run correctly from the other drive?

and if you take out the ubuntu drive does windows run correctly?

---

### Post by lumarh on 2007-04-05
ok i was setting it all up as i described above , in terms of hardware, and wrecked one of the IDE cable connectors. long story short, my current setup is this:

-Primary-
Master: optical drive

-Secondary-
Master: Ubuntu
Slave: Windows drive

When i take out the windows drive, ubuntu boots fine. it also boots fine with the 'windows' drive in, although i think the boot info on the win drive is buggered. ill test 'windows drive only' now

---

### Post by mikeyphi on 2007-04-05
> **lumarh said:**
> Ok guys, ive had no luck at all trying like a maniac to dual boot windows with ubuntu.

I already have ubuntu installed, i did have windows already on the drive but i think i wrecked it (NTLDR is missing, couldnt fix it). What steps should i take from this position to be able to dual booth windows and ubuntu from grub. please note that installing windows seems to knock grub off, so if possible include steps to fix grub back up?
thanks all, this is really stressing me

If you've installed windows after Ubuntu look here for advice: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_restore_GRUB_menu_after_Windows_installation](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_restore_GRUB_menu_after_Windows_installation)

---

### Post by lumarh on 2007-04-05
when i took out the ubuntu drive, i got the same message that i have been getting when grub tries to boot into windows "NTLDR is missing' and it didnt boot. i guess this means i had it (grub) set up right, but my windows was kinda screwed.

when i put ubuntu drive back in, it kept using the win drive for boot up anyway (and not working), so i had to disconnect it. 

i think my situation is this : i need to put my windows drive in, format it, install windows, and then make sure grub loads and not just windows because windows loves to take things over. .. any advice?

mikeyphi: thanks for the link - i think i can do what i explained above without any help now, ill give it a go and report back

---

### Post by lumarh on 2007-04-05
i have windows working on the windows only drive. i did the reinstall grub thing from the link, but windows still tries to load and take priority when the drive is connected. so i have the windows drive dc'd atm. 
i dunno what to do about this

---

### Post by oilchangeguy on 2007-04-05
here's what i did. installed ubuntu on the master drive (at the time the only drive). removed that, installed xp pro on a drive set as master. re-installed the ubuntu drive set as master. re-located the xp drive and set it as slave, both on the same ide cable. and it works great.

---

### Post by Mowcius on 2007-04-05
glad it works for you

later in the year i'm going to be having three different opperating systems on three different drives.

I'm getting Vista, Xp Pro, and ubuntu on the same computer

Hopefully!!!!!!!!!!!!

---

### Post by Wiebelhaus on 2007-04-05
I'm a total noob and I was flabbergasted at how well mine went , Master drive has a vista installation I booted up to the live disk ran Ubuntu installation pointed at the slave drive and on the first re-boot I could boot into either OS.

---

### Post by lumarh on 2007-04-05
i got it working

thankyou and i love you all

---

### Post by Mowcius on 2007-04-05
'i love you all'

isn't that going a bit far!

---

### Post by J11Gyro on 2007-04-05
Somewhere in the forums there was advice to make sure you loaded Ubuntu to slave drive after windows was installed, it worked like a champ on my box with XP configured like that. Of course I cannot leave anything alone while learning new OS so I have had to re-install ubuntu more than once :lolflag:

---

