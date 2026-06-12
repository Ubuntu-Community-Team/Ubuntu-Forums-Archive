---
title: "Serious Problem With Grub!!"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by infin?ty on 2006-11-08
Hi friends.

A couple of days back i reported a problem that my grub has gone
because of a windows reinstall. I tried the stuff given in the wiki about
restoring grub from the grub prompt thru a live CD (i typed sudo grub).

But it couldnt find /boot/grub/stage1 file. 

Then i tried to reinstall ubuntu without formating the root partition,
but by mistake i formatted the boot partition. Then during the installation the installer crashed
with a big error message which dint make any sense to me. I tried the 
installer 3-4 times after that but the same problem cropped up every
time.

Then i read about the super grub disk (SGD), i used it to restore grub
but dint workout, even it gave the same problem of file not found
(but this time its bcoz i formatted the boot partition).

But while exploring the SGD i was able to boot up my ubuntu 
(i dont remember which option was that ), So that means that something 
can still be done about restoring grub, despite of me formatting the
boot partition.

Please someone shed some light on this problem

---

### Post by subzero79 on 2006-11-08
Post exactly what did you do from your liveCD.

For example: for me restoring Grub is like this:

sudo grub
root (hd3,2)   #pointing to my linux install
setup (hd0)    #installing grub to mbr in my first HD.
quit
reboot

that's all.

---

### Post by Bachstelze on 2006-11-08
I'd rather go like this :

1. Become root : *sudo -i*

2. Create a mountpoint for your root partition : *mkdir /mnt/root*

3. Mount it : *mount -t ext3 /dev/whatever /mnt/root*

3b. If you have a separate /boot partition, mount it too : *mount -t ext3 /dev/whatever /mnt/root/boot*

4. Reinstall GRUB : *grub-install --root-directory=/mnt/root /dev/whatever*

5. Reboot :)

---

### Post by infin?ty on 2006-11-08
Ok heres exactly what i did

Attempt 1:

sudo grub
find /boot/grub/stage1
 this returned file not found

But i knew where my boot partition is so i did
root (hd0,7)
 this returned some ext2fs or summin
setup (hd0)
   /boot/grub/stage1 not found

Attempt 2:
  as i said i tried to reinstall ubuntu, but i dint format the root partiotion so that all the data stays intact. But here the installer crashed. But unfortunately i formatted my boot partition.

So presently my boot partition contains nothing so i dont think any of these commands are going to work bcoz they work by finding out where the stage1 is.

So can anyone tell me some other method, bcoz i feel still something can be done, bcoz the super grub disk booted my ubuntu, but from the boot disk not from the hard disk.

---

### Post by Foudre on 2006-11-08
i've had some grub issues the past week but luckily i managed thru it, my question is you try to restore the gurb right? well it can't find the stage one but you can still try to just boot from live disk, terminal

grub

root (?,?)  which would be where you have you linux installed though you can make it a different partition if you really want to

setup (hd0)

after i did this it tried reconized all the oses i had installed but not how to boot them, so i had to edit those

i did so by hiting the 'e' button one the os option on the grub menu, i had to change the partion it was trying to boot the location of the vmlinux thingy, and to make the changed permanent i went to the terminal sudo kwrite /boot/gurb/menu.list

scrolled down to the bottom where it has all the actual settings and changed them to match what i did to boot in the first place. (warning never use wingrub, thats what broke it in the first place i thought i would try the easy way from windows but wingurb just sort of screwedt things up, i too just had reinstalled windows downgrading from vista back to xp, and tried to restore grub from a windows enviroment and it just made alot of hassle, the linux way keeps things working)

but the dude above me probally has the better way, this is just what i did,

---

### Post by Foudre on 2006-11-08
oh i started typeing before he replied back, hmm can't find stage one? well the easy way would be to just reinstall with formating, but you can save your data, if you can get ahold of a knoppix cd, they always gave me access to the hard drive (knoppix is a live cd distro, for the most part it is) umm back up all the stuff you want to save, wait idea,

on knoppix if you can get a hold of one, and see if you can write to your hard drive. if so i can just like email you the grub i have, and help you modify it for your system to work if you want

---

### Post by infin?ty on 2006-11-08
Hmmm is there really no other way?? This idea did come to my mind but i dint like it. I want to restore this system only.

Please someone tell me about the super grub disk bcoz it is booting my linux properly just like it was before i reinstalled windows, the only problem is that i need the disk to boot. Can i not something with the grub disk.

I have one more idea, i have a frnd who has ubuntu dual boot with winXP wat about copying his boot partition into mine(as mine is empty now), and then trying to run the setup and grub-install commands. Will that work??

---

### Post by Foudre on 2006-11-08
> **infin?ty said:**
> Hmmm is there really no other way?? This idea did come to my mind but i dint like it. I want to restore this system only.

Please someone tell me about the super grub disk bcoz it is booting my linux properly just like it was before i reinstalled windows, the only problem is that i need the disk to boot. Can i not something with the grub disk.

I have one more idea, i have a frnd who has ubuntu dual boot with winXP wat about copying his boot partition into mine(as mine is empty now), and then trying to run the setup and grub-install commands. Will that work??

if you read my second post you would have noticed i just suggested the same damn thing

---

### Post by infin?ty on 2006-11-08
Hey sorry man, dint realise that even u were saying the same thing. But plz tell me something abt the SGD i still think i can restore it thru the SGD bcoz its booting my ubuntu.

---

### Post by Herman on 2006-11-09
Hello infin?ty,
If you can boot Ubuntu with Super Grub Disk , and you have no Grub in your /boot directory, (or partition),  you can make your own (empty) directory to install Grub in with this command, ( in a terminal in Ubuntu), 'sudo mkdir /boot/grub',```
sudo mkdir /boot/grub
```Then, you can install all your Grub files again to your /boot/grub directory with 'sudo grub-install /dev/hda', if you have an IDE hard disk. (Replace 'hda' with 'sda' if it is SCSI or Sata). ```
sudo grub-install /dev/hda
``` Finally, to make a new menu.lst file, you just use 'sudo update-grub' ```
sudo update-grub
``` Then, if you need to, you can edit the new menu.lst file to suit your needs.

Regards, Herman :D

---

### Post by infin?ty on 2006-11-09
Ok done thanks a lot, this is working. But only a slight problem is there, i have a dual boot system but now the grub menu is not showing the boot windows option. 
What to do now??

---

### Post by infin?ty on 2006-11-09
ok..i guess i need to modify my menu.lst file. BUt the problem is i dont kno wat all commands are to be written in it to chain load winXp.

Can neone who has a dual boot with XP on hd0,0 post here the contents of menu.lst file. 

Thanks

---

### Post by infin?ty on 2006-11-09
Hey thanks a lot everyone. I finally managed to put everything in place. My system is running perfectly now. Thanks a lot again

Cheers!!!

---

