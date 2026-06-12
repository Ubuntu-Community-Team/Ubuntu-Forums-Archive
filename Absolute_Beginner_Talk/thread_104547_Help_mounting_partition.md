---
title: "Help mounting partition"
date: 2005-12-16
forum: Absolute Beginner Talk
---

### Post by DiscoKiller on 2005-12-16
I was wondering if it is possible to mount a partition of a broken linux install to edit the xorg.conf file so i can use my copy of breezy again? i`m running the live hoary cd and i need to alter the xorg.conf file on my installation of breezy. otherwise i`m looking at a complete re load and i need to have this sorted b4 i go home (in 3 1/2hrs). is this possible? can u tell me how to do it step by step as i`m useless with command line at the moment. i have a bad short term memory span so i forget all the commands pretty much straight away :S

thx DK

oh yeah just remembered. the boot sequence doesnt get as far as GRUB so i cant use the recovery mode

---

### Post by DiscoKiller on 2005-12-16
anyone help me? i`m desperate

---

### Post by linbetwin on 2005-12-16
Using the LiveCD, open:

System -> Administration -> Disks

On the Partitions tab look for the Linux partition, select it and click Enable

I'm not sure this works. Please post the results.

---

### Post by DiscoKiller on 2005-12-16
i cannot find said 'disks' util, is there something i can get from synaptic that will do the trick? i immediately thought of gparted but it isnt possible to mount in this prog.

---

### Post by bscbrit on 2005-12-16
I don't think that you are going to have any success.  If your boot does not even reach 'grub' then it is getting nowhere near to needing to access the xorg.conf, but Good Luck anyway.  Let us know how you get on!

---

### Post by linbetwin on 2005-12-16
Try this command in the terminal:

sudo mount -a

---

### Post by DiscoKiller on 2005-12-16
looks like i`m gonna have to do a reload
number 4 i think this will be

---

### Post by DiscoKiller on 2005-12-16
sudo mount -a didnt work, i`m guessing this is because the partition isnt in fstab,i have no clue how to edit that either :s. i`m merely looking for someone to tell me definately that i cant fix it so i`ll just have to do a complete reload. potentially losing alot of data.  all i need to do is get some kind of terminal to edit my files to either use my backup of xorg.conf or copy stuff to a different drive...grrr i wish i didnt click so much stuff!

gonna try anther reboot to see if i can reach GRUB.....l8rs

---

### Post by kaamos on 2005-12-16
Boot with the live cd.
Open a terminal and type:
```
ls /dev/ | grep hda
```
This will show you your partitions. If you have more than one hard disk, the second one is hdb and so on. Try to remember the partition where you installed ubuntu (for example hda1 is the first partition on the drive). Once get that, type:
```
sudo mount /dev/**hda1** /mnt/
```
..replacing hda1 with your partition. The sudo requires no passwd, and the contents of your drive is now visible in the folder /mnt/. If you got the partition wrong, type
```
sudo umount /dev/**hda1**
```
..and try again. I'm sorry I know this isn't a very user friendly way to do this, but it's the only way I know. And it works.

---

### Post by DiscoKiller on 2005-12-16
I`d like to sincerely apologise for wasting your time. I`m a complete retard and 'just didnt notice' GRUB. My monitor is broken so it only comes on once it has cooled down so i missed the grub menu on reboot. I shoud have realised there was no way i could have possibly seen the ubuntu splash screen without passing through GRUB. all i need to do now is copy my backup xorg.conf file and i`m fixed. I have the info to do so, again i apologise for wasting your time.

*kicks himself hard in the face with a big granite boot*

---

### Post by linbetwin on 2005-12-16
Put that boot down and cool your monitor!

---

### Post by DiscoKiller on 2005-12-16
Ahoy hoy, back in breezy!!.....i really must think b4 i speak. Sorry again and thank you for trying to come to my aid, sadly there is no hope for me :D no doubt i will have broken linux again by the time i return to the internet, so i`ll look forward to seeing you guys in the new year (i have no internet at home and i`m going home for xmas from uni) may i wish you all a pleasant holiday and hope you bring the new year in whilst enjoying yourself! Thank again guys and dare i say it

  Merry Christmas - home time for me i think.

---

### Post by linbetwin on 2005-12-16
Merry Christmas and a Happy New Year, DiscoKiller!

---

### Post by bscbrit on 2005-12-16
DiscoKiller - there is no need to apologise.  You are back in the land of linux and online.  What more is necessary?

p.s.  You could ask for a new monitor if someone is looking for ideas for a present....

---

### Post by DiscoKiller on 2005-12-17
Hee hee, i snook on to the net at my mum's work....I will be looking into the idea of a new monitor soon but i need a new graphics card first, the old RIVA TNT 2 is a bit shoddy these days. I appologised because thats who i am, you guys ran to my aid and i didnt need it in the end, thought it would be polite :D mummy brought me up well. I`m currently having a fight with a server & tape drive in my mums office, the bastard thing wont do what i say, still thats why we dont use windows to run servers :S. oh well, i`m sure i`ll get my bonce round it sooner or later. Have a good xmas all and i`ll see you soon!

---

