---
title: "how  to dual boot vista and ubuntu?"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by bojox on 2007-01-23
hi!i've just installed ubuntu in my hp pavilion dv1000 laptop 3 days ago and am feelin really lost here...first,my cam and mic doesnt work :cry: and i dont know how to dual boot to vista either...er,i didnt do any manual partitioning before i installed ubuntu...i just chose the "resize and use the freed space..."which uhmn...please excuse my stupidity :oops: ...but does this mean i still have my vista or do i have to re-install it again?

---

### Post by Happy_Man on 2007-01-23
First off, we need to see some stuff

```
sudo fdisk -l
```

Put that into a terminal and post the output here. We'll work from there ;)

---

### Post by oilchangeguy on 2007-01-23
with vista being totally different from xp, there's alot of new stuff to learn. why try to learn two new operating systems. and if you've upgraded xp to vista there may be problems that you're not even aware of yet (it's always better to do a clean install rather than upgrade). if it were me i'd learn vista for a while before trying to jump in and learn ubuntu at the same time. also since vista has not been released to the public yet are you using a beta version (bad mistake)?

---

### Post by bojox on 2007-01-23
woah,that was quick...thanks a lot!:D here goes:

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6412    51504358+   7  HPFS/NTFS
/dev/sda2            6413       11976    44692830   83  Linux
/dev/sda3           11977       12161     1486012+   5  Extended
/dev/sda5           11977       12161     1485981   82  Linux swap / Solaris

---

### Post by Happy_Man on 2007-01-23
First, some good news: You didn't wipe Vista. The install partitioner worked perfectly. You can breathe now. Now then, to the next part: Can you describe your webcam and mic? eg brand, model, etc.

---

### Post by bojox on 2007-01-23
i have an HP 1000 webcam.the mic and cam are both embedded to the laptop...thanks again.ur so nice:guitar:

---

### Post by bojox on 2007-01-23
hi,there oilchangeguy!):P i have vista ultimate build 6000 which i've just activated til august so really...i see no point of goin through all that trouble just to clean install another OS this early.plus,i already know my way around vista and have already started tweakin it so...

---

### Post by Happy_Man on 2007-01-23
Oooh... I'm not sure whether there are drivers for those types of embedded stuff. Since I'm at a loss, you might want to search these forums and google for further information. Sorry I can't help you. :frown:

---

### Post by bojox on 2007-01-23
ok...thanks anyway.so how can i dual boot to vista then?

---

### Post by Buck2348 on 2007-01-23
I don't know what the installer does when you let it do its own thing, but normally with Ubuntu installed on a functioning Windows machine, it installs a program called Grub, which when you turn the machine on, after several seconds you get a screen showing the operating systems available and offering for you to choose one using the arrow keys and <Enter>.  You have 10 seconds to choose and if you don't it boots Ubuntu.  If your machine isn't doing this you're going to have to install Grub.

Buck

---

### Post by bojox on 2007-01-23
> **Buck2348 said:**
> I don't know what the installer does when you let it do its own thing, but normally with Ubuntu installed on a functioning Windows machine, it installs a program called Grub, which when you turn the machine on, after several seconds you get a screen showing the operating systems available and offering for you to choose one using the arrow keys and <Enter>.  You have 10 seconds to choose and if you don't it boots Ubuntu.  If your machine isn't doing this you're going to have to install Grub.

Buck


....it does that but vista is not on the list

---

### Post by Spr0k3t on 2007-01-23
You may have to manually edit the menu.lst

Have a look at the file /boot/grub/menu.lst

Don't edit this file until you know what it means and what areas you can change or add.  Since I'm a bit of a new user, I'm going to let the more knowledgeable take over.

---

### Post by bojox on 2007-01-23
> **Spr0k3t said:**
> You may have to manually edit the menu.lst

Have a look at the file /boot/grub/menu.lst

Don't edit this file until you know what it means and what areas you can change or add.  Since I'm a bit of a new user, I'm going to let the more knowledgeable take over.

thanx...i've actually been doin that since yesterday but i just cant seem to get it right.dude,this is like a nightmare](*,)

---

### Post by seshomaru samma on 2007-01-23
```
sudo gedit /boot/grub/menu.list

```

add these lines at the bottom:
```
title         "Vista"
root         (hd0,0)
chainloader      +1
```

save and reboot
should work.....

---

### Post by bojox on 2007-01-24
> **seshomaru samma said:**
> 

```
title         "Vista"
root         (hd0,0)
chainloader      +1
```

tried it but didnt work.thanx though

---

### Post by ajmorris on 2007-01-24
> **bojox said:**
> tried it but didnt work.thanx though

This should work. (this is what i use in grub for Vista)

title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


Title can be whatever you want. mine is that because it was automatically added.

---

### Post by bojox on 2007-01-24
> **ajmorris said:**
> This should work. (this is what i use in grub for Vista)

title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


Title can be whatever you want. mine is that because it was automatically added.

didnt work either...said error 13...anyways,i think i've had enough of this already so can anyone just tell me how to uninstall ubuntu please?i just really wanna chat with my sister and be able to hear her voice and see her face is all...thanks!

---

### Post by seshomaru samma on 2007-01-24
I'm sorry it didn't work out for you
I'm sure you can talk and see your sister with Wengo on Ubuntu but if chatting is important to you , then keeping a Windows partition is a good idea as MSN is the best IM client by far.
Uninstalling Ubuntu is easy ,just format the partition Linux is on. You can use Gparted on the live CD (if it's not there just go 'sudo apt-get install gparted')
The problem is that your MBR will still have Grub on it
If you were running XP then I would tell you to use the XP CD and use the command 'fix mbr' to restore Windows boot menu. I would imagine that Vista has a similar option but I'm not sure. Try to boot from the Vista CD and instead of installing see if they have some sort of rescue mode. If its like XP you will get a terminal where you can put the command 'fixmbr' . Sorry I cant help more I am not so familliar with Vista.

---

### Post by bojox on 2007-01-24
> **seshomaru samma said:**
> I'm sorry it didn't work out for you
I'm sure you can talk and see your sister with Wengo on Ubuntu but if chatting is important to you , then keeping a Windows partition is a good idea as MSN is the best IM client by far.
Uninstalling Ubuntu is easy ,just format the partition Linux is on. You can use Gparted on the live CD (if it's not there just go 'sudo apt-get install gparted')
The problem is that your MBR will still have Grub on it
If you were running XP then I would tell you to use the XP CD and use the command 'fix mbr' to restore Windows boot menu. I would imagine that Vista has a similar option but I'm not sure. Try to boot from the Vista CD and instead of installing see if they have some sort of rescue mode. If its like XP you will get a terminal where you can put the command 'fixmbr' . Sorry I cant help more I am not so familliar with Vista.

thanks a lot..i'll try that one...really like the graphics in ubuntu  though(better than vista,i say!)but since i cant get both my embedded mic and cam to work too,i guess i'll just have to stick with vista...maybe i'll try another linux distro someday...when i've finally moved on from feelin so frustrated:lolflag: anyways,thank you all for bein so helpfull...if there's one more thing i like about this distro,it's the community...

---

