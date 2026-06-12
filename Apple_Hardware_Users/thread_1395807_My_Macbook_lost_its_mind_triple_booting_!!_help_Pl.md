---
title: "My Macbook lost its mind triple booting !! help Please !!"
date: 2010-02-01
forum: Apple Hardware Users
---

### Post by ankit.minglani on 2010-02-01
Few days back i was searching for triple booting my mac through this ubuntu forum.
and i ran into command name *bless*

it was like :

bless /dev/disk0s3 --setboot -- device --verbose

i ran it on the terminal after booting it from a Leopard installation DVD in a hope to run linux on my macbook(macbook white..intel m/c 160gb HD..2 GB RAM) after trying all the stuff and eventually everything has stopped booting neither leopard nor windows.

i can see the grub for ubuntu loading up but after selecting the option for ubuntu, ubuntu is also not working.

i was using refit as well.


i cannot even boot from my leopard installation dvd..windows that was priorly installed using bootcamp is corrupted too.

Please help !!!

---

### Post by ankit.minglani on 2010-02-01
i followed it from here :

[http://ubuntuforums.org/showpost.php?p=5166788&postcount=21](http://ubuntuforums.org/showpost.php?p=5166788&postcount=21)

---

### Post by linuxopjemac on 2010-02-01
Try booting with the "x" key pressed (force MacOSX to boot):

[http://www.tech-recipes.com/rx/2818/os_x_ten_boot_options_for_leopard/](http://www.tech-recipes.com/rx/2818/os_x_ten_boot_options_for_leopard/)

---

### Post by ankit.minglani on 2010-02-01
everytime i try to boot leopard from disk or from installation DVD .. the apple logo appears for a while ..it keeps on loading and then .. the apple logo disappears and it turns into a "no entry" kind of sign. like a circle showing only one diameter.

i will try x for force booting. but can there be any serious problem ?

---

### Post by ankit.minglani on 2010-02-01
the problem got resolved itself i think.. thankz for the reply though :)

God bless :)

---

### Post by linuxopjemac on 2010-02-02
I can imagine how you felt. I am experiencing problems myself now. My complete Karmic crashed, inode errors all over the place. I will try to copy everything back with an old clonezilla copy. Hopefully that works.....

---

### Post by Nohtanhoj on 2010-02-02
Yeah, I know what you mean. I ended up crashing my entire Mac when trying to get Ubuntu booting... I lost all my Pro Apps (Final Cut Studio, Logic Studio, Adobe CS4 Master Collection), and most of my files. Thank God I had an external drive with my music/movies/photos on it.

Had to call Apple and plead with them to give me new serial numbers, as apparently their central server said that mine were already registered (they were, I guess); had to do the same thing with Adobe....

The hazards of messing with your partition table, I guess. Immediately after I got this whole mess under control, I went out and bought a Time Capsule. =D

---

### Post by linuxopjemac on 2010-02-02
Time Capsules die.....

I run an old Dell with [Clarkconnect]("http://www.clarkconnect.com/") and I update with [luckybackup]("http://luckybackup.sourceforge.net/") every day from every Mac with anacron. Time Capsules are expensive and unreliable.

[http://timecapsuledead.org/](http://timecapsuledead.org/)

PS I can recommend Clonezilla, that's the way I got my Linux partition back without any sweat. It can clone a complete HD with different partitions (EFI, HFS, ext4). Together with that little server of mine, I got all my photos and emails back without losing one single day, GREAT.

---

