---
title: "help needed pls - dual boot (ubuntu+winxp) accessing ubuntu from winxp"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by ishwar on 2007-05-04
hi folks,,
i am using ubuntu for few months now.. running fine and happy with it.. it allows me to browse thru the ntfs system my problem is setting up samba to browse ubuntu from windows(mainly i needed to write some mp3 cd, but the music is in ubuntu.. its a quite large collection) and various other reasons like accessing docs. etc.. 
well now when i m in winxp it does not seem to recognize the other partion file system atal.. ( from control pannel windows show the swap and ext3 partion as unknown file system) 
pls help me setting up samba config file .. i read thru few topics but the chages did not make any better.

thanx in advance
regards
ishwar

---

### Post by mi_were on 2007-05-04
> **ishwar said:**
> hi folks,,
i am using ubuntu for few months now.. running fine and happy with it.. it allows me to browse thru the ntfs system my problem is setting up samba to browse ubuntu from windows(mainly i needed to write some mp3 cd, but the music is in ubuntu.. its a quite large collection) and various other reasons like accessing docs. etc.. 
well now when i m in winxp it does not seem to recognize the other partion file system atal.. ( from control pannel windows show the swap and ext3 partion as unknown file system) 
pls help me setting up samba config file .. i read thru few topics but the chages did not make any better.

thanx in advance
regards
ishwar

I found a nice work around to the same problem by using Explore2fs. It installs in windows and allows you to browse your Ubuntu partitions.

[http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)

I hope it helps!

---

### Post by ishwar on 2007-05-04
wow it looks promising

thanx a million ..

i have to try it yet!

regards

---

### Post by darkrose on 2007-05-04
If you are trying to access an Ubuntu partition on the same computer as windows Samba won't do you any good, as it is for sharing between 2 (or more) computers.
To read your Ubuntu partition with windows you will need to install Ext2IFS on windows, you can get it from [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by ishwar on 2007-05-04
hi,, thanx for the help but it only allows me to browse through the partition, i want to use the files in the sence that i want to copy to windows and i want them to be modyfialble. like how i could do from ubunto !

i think samba will let me do that i would like to know the right settings!

cheers

---

### Post by jordanmthomas on 2007-05-04
Did you check darkrose's link? 
The driver at fs-driver.org mounts ext3 partitions and they are transparently integrated.  It becomes whatever drive you give it and you can copy, edit, move, whatever you need from it.

Samba is for sharing files over a network, which doesn't sound like what you want.

---

### Post by ishwar on 2007-05-04
hi thank u very much for the reply.. it was great and it works wonderfull
ext2 installable file system works well.. 

thank u all for the timely help.!
this forum rocks
cheers:guitar:

---

