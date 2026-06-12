---
title: "Further install problems"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by toontastic on 2007-06-01
Further to my problems where I lost Windows I'm now up and running again. I ran the install again having defragmented a few times and used the guided partition. I pressed forward and got all the way to step 6 I think it was and then pressed forward. The screen then jumped about a bit and I entered up back at a partition screen with only the ratio button manual available. Not wanting to do anything else as I assumed the partition was sorted I came out of the install program as it was obvious I wasn't going to be able to install the software.

Anyway after a reboot to check Windows was ok I noticed that about 30gb was missing which would be just right for the partition Ubuntu was meant to make. So I rebooted back into the live CD and tried the install again. This time I got an extra option when it came to the partition section which said 

Guided - Use biggest available free space (or something along those lines)

I guessed that meant it had found the free space it had created before and chose that option. I then got the screen which asked if I wanted to import files, I tried choosing yes to my account but it crashed. I then tried not choosing any and it crashed again. Also the very first time I tried to install and it got to step 6 it couldn't find any accounts to import from, this time it found them, not sure if this is important but thought I should mention it.

I did send the reports off when the system crashed but I don't know how to check if they have been sent before so I don't know if there is a fix.

Would anyone be able to help me get past this point and get Ubuntu installed ? Thanks.

---

### Post by zvacet on 2007-06-01
Use manual way to install.
1.root =10GB                           mountpoint /
2.swap = 2xRAM
3. home = rest of free space     mountpoint /home

---

### Post by toontastic on 2007-06-01
Isn't that just partitions ? The partitions seem to be set up fine, I don't really understand how to manually set them up it doesn't make sense to me. If I go into Gparted on the live CD I can see

/dev/sda1 - ntfs - size 207.61GiB - used 164.69 GiB
/dev/sda2 - ext3 - size 24.18 GIB - used 1.80 GiB - Flags boot
/dev/sda3 - Extended - size 1.09 GiB (this one has a padlock next to it)
      /dev/sda5 - Linux-swap 1.09 GiB )this also has a padlock)

I also tried running the alternative installer. I get the error

Configuring Gnome-Applets

Installation step failed.

An installation step failed. You can try to run the failing item again (which I did with no luck) from the menu, or skip it and choose something else. The failing step is Select and Install software.

It seemed to fail at about 6%.

Any ideas ?

Thanks.

---

### Post by toontastic on 2007-06-01
I've just noticed the ATI thread, I have a Radeon X850XT Platinum card may this be the source of my problems ? Read the ATI thread to fix the problems I have to finish the install but that's where I'm getting stuck so now I'm confused :)

---

### Post by toontastic on 2007-06-02
<Bump> just it was sent late last night

---

### Post by toontastic on 2007-06-02
Followed instructions in another post on how to Install the ATI stuff and it worked. It's now installed.

---

