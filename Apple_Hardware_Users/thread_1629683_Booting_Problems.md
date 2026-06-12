---
title: "Booting Problems"
date: 2010-11-24
forum: Apple Hardware Users
---

### Post by -nat- on 2010-11-24
I added an extra partition to my internal hard drive today, leaving me with:
[OSX] [Ubuntu 8.10] [Ubuntu 10.10] [Empty Partition]

Initially I could only boot into OSX, with 8.10 displaying "GRUB_" on a black screen (and not booting) and 10.10 just a black screen.
I got 8.10 working by re-installing GRUB, but 10.10 still won't boot (and doesn't show up in 8.10's GRUB), and when selecting it from the rEFIt menu it just hangs on the grey Tux logo. (I've done the rEFIt synchronizing tables stuff, but still no luck). **[EDIT]** Okay, after a couple of reboots it's not hanging on the logo anymore, but instead going to GRUB, which looks the same as when I boot into 8.10 (i.e. 10.10 doesn't show up in the list)

I'm not entirely sure what the problem is, as all the files on the 10.10 partition look to be intact, so I think either GRUB isn't installed on the partition or rEFIt is having problems.

So any ideas on where to go from here? I was thinking to re-install GRUB on the 10.10 partition (I'm not sure how to do it though) or upgrade GRUB on the 8.10 partition to GRUB2 ( I tried following a guide to do this, but the files don't seem to be in the 8.10 repos anymore - I just got 404 errors in Synaptic).

*Edit: just realized I gave this the [lubuntu] heading accidentally. could it be changed if possible? apologies!*

---

### Post by Zookalicious on 2010-11-24
Is there a reason you're using rEFIt and GRUB? I think it would greatly simply things if you just used rEFIt (unless of course, there is a reason I'm missing :P ).

---

### Post by -nat- on 2010-11-24
> **Zookalicious said:**
> Is there a reason you're using rEFIt and GRUB? I think it would greatly simply things if you just used rEFIt (unless of course, there is a reason I'm missing :P ).

As far as I know/thought you have to go through GRUB no matter what.

---

### Post by Stu09 on 2010-11-24
> **-nat- said:**
> As far as I know/thought you have to go through GRUB no matter what.

I was under that impression aswell. How do you remove GRUB2? This might solve all my boot issues.

---

### Post by Zookalicious on 2010-11-24
Sorry I wasn't very clear. Yes you are right GRUB is necessary, I was just referring to the fact that it sounds like you have multiple menus (refit > grub > boot). You can't remove grub, but you can set it to automatically boot into the chosen OS (I can explain that later, assuming we get you booting period).


Now as for the 10.10 partition, we want to re-install GRUB2, so your best bet would be to boot a liveCD, select "try Ubuntu", open a terminal and type 
```

sudo mount /dev/sd** /mnt
sudo grub-install --root-directory=/mnt /dev/sd*

```
Make sure to replace the *'s with the letter and number of the partition with 10.10 on it. 

run "sudo fdisk -l" if you do not know the name of your partition. 


For example, my Linux install is located at /dev/sda3
```

sudo mount /dev/sda3 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

```

Once that is done, you'll probably want to run update-grub (to rebuild your grub.cfg). 

Assuming your partition is still mounted type in the following commands, if not, mount it again by following the first command above and then continue
```

mount -o bind /dev /mnt/dev
mount -o bind /proc /mnt/proc
chroot /mnt bash
sudo update-grub

```

Try rebooting after that. If all goes well, GRUB2 should be restored to your 10.10 partition. You may need to run rEFIt's partition sync tool, I'm not too sure about that.

---

### Post by -nat- on 2010-11-24
Thanks for the help, but I've ended up wiping both 8.10 and 10.10 off my hard drive and going for a fresh install of 10.10

---

