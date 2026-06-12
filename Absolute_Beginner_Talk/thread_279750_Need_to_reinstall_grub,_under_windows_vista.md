---
title: "Need to reinstall grub, under windows vista"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by Foudre on 2006-10-18
Ok i got bored and downloaded windows vista beta rc1, now when windows reinstalls it seams to take the grub loader with it, now i need some way to reinstall my grub, hopefully with out reinstalling kubuntu. I feel sort of shamefull for downloading the vista, but its free so is it ok? well i only keep windows around to play on anyways, i do my work on linux, so having a waste of resources windows is fine by me the transperancies are cool and so is bitching at microsft telling them that most of it doesn't work. But i sort of need my grub back, i've treid to find away to install it from windows that works with vista (not much luck) if some has an iso to boot from that like has a grub installer that would be great or some other brilliant idea, you guys are awesome and way more fun then looking around windows forums for bad advice and people with retarded questions.

---

### Post by PriceChild on 2006-10-18
Check this out: [http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

(personally... i physically removed the power from my ubuntu drive before inserting the vista disc into my machine. Make sure you do this with the machine off and power unplugged completely!!!)

---

### Post by bulldog on 2006-10-18
Do you have one hdd for dual booting?

I understand Vista and GRUB aren't working well together.
But if you don't mind to lose Vista try this,

Boot into the live Ubuntu cd. 

When you get to the desktop open a terminal and enter. 


```
sudo grub
```


This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands


```
find /boot/grub/stage1
```

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)


```
root (hd?,?)
```

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr


```
setup (hd0)
```

Finally exit the grub shell


```
quit
```

That is it. Grub will be installed to the mbr.

---

### Post by PriceChild on 2006-10-18
> **bulldog said:**
> I understand Vista and GRUB aren't working well together.I've heard this... but my vista's running fine through the old xp chainloader setup.

---

### Post by bulldog on 2006-10-18
> **PriceChild said:**
> I've heard this... but my vista's running fine through the old xp chainloader setup.

Well I tried it only once and it didn't work out.

There are some ways to get it working but after two days of Vista I removed it and will never install it again.

Keep a copy of XP for emergency's and a little gaming though.

---

### Post by Foudre on 2006-10-18
> **PriceChild said:**
> I've heard this... but my vista's running fine through the old xp chainloader setup.

how did you use the xp loader? or did you just reinstall xp, i'm on a laptop so i have no more partitions left in which to add them, i have one left but like no real space availible. And why would installing grub like what bulldog said make me loose my vista? I mean i got admit vista is sort of cool (except being microsft, and it crashing alot, its confused by region codes of dvds of the same region its set to) its mainly just cool because so few people have and all the transperancy, and i don't mind its unstableness due to the fact i only use windows to play games? after i get back from class i'll have to try what bulldog said, but why would it make me loose vista? and is there a way to not touch the mbr.:-({|=  
not a big fan of smileys but this dude is cool because he play the violin

---

### Post by bulldog on 2006-10-18
> **Foudre said:**
> how did you use the xp loader? or did you just reinstall xp, i'm on a laptop so i have no more partitions left in which to add them, i have one left but like no real space availible. And why would installing grub like what bulldog said make me loose my vista? I mean i got admit vista is sort of cool (except being microsft, and it crashing alot, its confused by region codes of dvds of the same region its set to) its mainly just cool because so few people have and all the transperancy, and i don't mind its unstableness due to the fact i only use windows to play games? after i get back from class i'll have to try what bulldog said, but why would it make me loose vista? and is there a way to not touch the mbr.:-({|=  
not a big fan of smileys but this dude is cool because he play the violin

You can have the same transparancy with Beryl and Emerald with Ubuntu.:D 

Okay,it seems Vista uses another type of bootloader as XP did.
GRUB can boot XP splendid but Vista is a little bit of trouble.

If you install GRUB over your Vista bootloader you can't normally boot Vista anymore.

But if you do a search on the Ubuntu forums,there should be a way to boot Vista with GRUB.

I have no link because I'm not intending to do so.

Bust as I said it should be possible to do so.

---

### Post by Kateikyoushi on 2006-10-18
He means the vista bootloader plays well with the grub settings we formarly used to load XP.

Here is mine.
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

Worked flawlessly with it for a month till I deleted windows so I do not know what might go wrong.

---

### Post by Foudre on 2006-10-18
no joy....

i get my bios thingy saying missing operating system

i even tried using gparted live cd, set the partition that has kubuntu on it's flag to boot

missing operating system. 

I know the operating system is still there because that partition still has 14.8 gigs used

i wonder if vista some how purposely damaged the files need to boot kubuntu

despiste having this is kinda cool and the fact some minor hardware problems are taken care off, its increased speed, i may have to get rid of vista. unless anyone has any good ideas? i'm reaching my limit

---

### Post by Foudre on 2006-10-19
i really can't think of anything else other then getting rid of vista, that will let it work

---

### Post by lonelypauly on 2006-11-08
hey Bulldog, i followed your directions for restoring grub as well since i installed vista recently.  now my kubuntu partition wont boot...its on a completely seperate HD if that makes any difference.  i get the following message now:

root (hd1,0)
Filesystem type unknown, partition type 0x7
kernel  /boot/vmlinuz-2.6.15-27-386 root=/dev/sdb1 ro quiet splash

Error 17: Cannot mount selected partition


Any ideas?

---

### Post by Elrohir on 2006-11-13
lonelypauly, play with the second value in (hd?,?) thingy...

---

### Post by bulldog on 2006-11-13
> **lonelypauly said:**
> hey Bulldog, i followed your directions for restoring grub as well since i installed vista recently.  now my kubuntu partition wont boot...its on a completely seperate HD if that makes any difference.  i get the following message now:

root (hd1,0)
Filesystem type unknown, partition type 0x7
kernel  /boot/vmlinuz-2.6.15-27-386 root=/dev/sdb1 ro quiet splash

Error 17: Cannot mount selected partition


Any ideas?

If the trouble persist,give a reply.

Sorry,but I saw this posting just now.:-?

---

### Post by lonelypauly on 2006-11-13
thanks for the reply.  i really had no luck using grub config, but not for a lack of trying...anyway, i did manage to find a solution. i made a super grub boot disk:
[http://forjamari.linex.org/frs/?group_id=61]("http://forjamari.linex.org/frs/?group_id=61")
and then just left it in one of my cd trays and now i can boot into any of the 3 OS's installed on my machine with no problem.  i think thats how i will do things from now on if i have more OS's than just kubuntu and xp.

---

