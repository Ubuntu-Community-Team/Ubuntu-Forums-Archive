---
title: "fresh install 7.04 over edgy duel boot XP"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by tekno62 on 2007-04-30
I have Edgy and would like to do a fresh install over the edgy with the new 7.04  - I have a duel boot with XP. 

I have search so if its there please link

---

### Post by starcraft.man on 2007-04-30
Thats easy, all ya need to do is pop in the live cd or alternate and when you get to the partition delete your old / (root file) and then make a new one. If you have a seperate /home partition just remount it to /home. You can leave the swap file as it is, and when your at the grub part it should redetect your xp install.

Clean installs are always better than upgrades, good of you to decide to go this way.

---

### Post by bulldog on 2007-04-30
> **starcraft.man said:**
> Thats easy, all ya need to do is pop in the live cd or alternate and when you get to the partition delete your old / (root file) and then make a new one. If you have a seperate /home partition just remount it to /home. You can leave the swap file as it is, and when your at the grub part it should redetect your xp install.

Clean installs are always better than upgrades, good of you to decide to go this way.

Rather not  'delete' the root folder,but mount it again as /  and set it to format ext3,but I'm sure you mend that too.
Mount the swap as swap again and your /home if you have one as /home.

---

### Post by tekno62 on 2007-04-30
I tried that but get the popup that says no root file system is defined

---

### Post by starcraft.man on 2007-04-30
> **bulldog said:**
> Rather not  'delete' the root folder,but mount it again as /  and set it to format ext3,but I'm sure you mend that too.
Mount the swap as swap again and your /home if you have one as /home.

Hehe, my bad, I did mean to format the partition, thanks for catching that. If theres any problems tekno feel free to post again :).

EDIT: hehe, posted right before me... ummm, when do you get this pop up? At the gparted partitioner? If thats the case then you have to make a new partition, just select the free space and create a new partition defined as / (root) and format it for ext3. If thats not it, please be more specific for the "popup".

---

### Post by tekno62 on 2007-04-30
So I cant just pop in the new Ubuntu DVD and run the install?

---

### Post by starcraft.man on 2007-04-30
You should be able to... isn't that how you got the popup during the install? Or was that a problem when you were just booting up? Need to be specific for us to know for sure >.<.

---

### Post by bulldog on 2007-04-30
Ubuntu doesn't like to format partitions which has data on it.
Maybe you should use the gparted live cd and format the / partition first.
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

When you come to the partition part of the installer,choose manual partition,and mount your partition on the right spot,set them to reformat to be sure,and continue the install.
It could be wise to set the bootflag to yes on the / partition,just to be sure.

---

### Post by tekno62 on 2007-04-30
Im using the partitioner that comes with the install dvd. 

I get 

/dev/hda
       /dev/hda1        ntfs        /media/hda1   
       /dev/hda2        ext3       /media/hda2
      /dev/hda5         swap

---

### Post by starcraft.man on 2007-04-30
> **tekno62 said:**
> Im using the partitioner that comes with the install dvd. 

I get 

/dev/hda
       /dev/hda1        ntfs        /media/hda1   
       /dev/hda2        ext3       /media/hda2
      /dev/hda5         swap

Ok, thats fine. I believe that your first one NTFS must be your xp install. Your hda2 is your root directory from edgy and hda5 is your old swap. The swap is mounted fine it seems, and you can leave your xp partition mounted to hda1 and it will be a drive on your desktop. Remount your hda2 so it reads /, so that there is no media/had2 after it, and ensure that right under the format (ext3 at the top of its properties) that it reads "yes, reformat the partition". 

That should do it :D.

---

### Post by MaskedMarauder on 2007-04-30
> **starcraft.man said:**
> Clean installs are always better than upgrades, good of you to decide to go this way.

I have to disagree with this.  

When was clobbering the user database to upgrade ever a good idea?  Recreating 20-30 user accounts with passwords, special shells and other things is just plain barbaric.  Never mind the customized server configurations.  An upgrade shouldn't clobber installed data unless there's a very very very good reason to do so, not just because its "easier" in some sense.

---

### Post by tekno62 on 2007-04-30
MaskedMarauder  


for me this is best..., Im a newbie and I have killed more Linux boxes then I have fingers... I just need to keep the XP till I get it right.

---

### Post by tekno62 on 2007-04-30
Also thanks for the help guys.. I get the fresh install and didnt lose XP.

---

### Post by starcraft.man on 2007-04-30
Got the partitions all fixed Tekno? Anything else I can help you with?

To Masked marauder : Ya, I suppose in that situation it would save you time not to have to recreate all those accounts. I guess I was a bit vague, I meant overall for users who do not have extenuating circumstances. As a whole, if you have your data backed up and you only use one or two accounts a clean install usually makes the least problems.

Edit: Ah ok Tekno, have fun with Ubuntu and feel free to ask another question :).

---

