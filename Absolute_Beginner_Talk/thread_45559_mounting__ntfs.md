---
title: "mounting  ntfs"
date: 2005-06-30
forum: Absolute Beginner Talk
---

### Post by dplastico on 2005-06-30
hi 

my problem is :

i have 2 ntfs partition on /dev/hda1 and /dev/hda6 i want to mount this partition on boot-up and allow all users to read and write, but i dont know how

i tried with  

/dev/hda5       /music_stuff    ntfs          umask=000             0       0
/dev/hda1       /win                 ntfs         umask=000              0       0


but it doesnt work

somebody please help me :P

p.d : sorry for my english , im from chile :)

---

### Post by poofyhairguy on 2005-06-30
[QUOTE=dplastico]
/dev/hda5      ** /music_stuff **   ntfs          umask=000             0       0
/dev/hda1      ** /win **                ntfs         umask=000              0       0
[/QUOTE]

I bolded what the problem is. Those don't sound like real directories. Ubuntu has to mount the drive to a real dircetory.

Use something like:

/media/music/

and 

/media/win/

instead. (always put in media). Plus you also have to make those directories. In the command line, this will do it:

> sudo mkdir /media/music/

> sudo mkdir /media/win/

---

### Post by Jussi Kukkonen on 2005-06-30
[QUOTE=dplastico]hi 

i have 2 ntfs partition on /dev/hda1 and /dev/hda6 i want to mount this partition on boot-up and allow all users to read and write, but i dont know how
[/QUOTE]
 You can't mount NTFS read/write in Linux. Either mount read-only or change your disks to FAT.

---

### Post by Darkscot on 2005-07-01
[QUOTE=poofyhairguy]

SNIP

instead. (always put in media). Plus you also have to make those directories. In the command line, this will do it:[/QUOTE]

Why should you put it in media?  I thought (in my ignorance) that /mount was the obvious place.  Isnt that where other distros (Mandrake) put it?

---

### Post by poofyhairguy on 2005-07-01
[QUOTE=Darkscot]Why should you put it in media?  I thought (in my ignorance) that /mount was the obvious place.  Isnt that where other distros (Mandrake) put it?[/QUOTE]

Because media is where your other drives are mounted. Nothing more than consistancy.

---

### Post by sickdude on 2005-07-06
[QUOTE=Jussi Kukkonen]You can't mount NTFS read/write in Linux. Either mount read-only or change your disks to FAT.[/QUOTE]

thats not true there is a way, and crap im looking for it (of course) 

i heard that it was experimental but it seems to work. i was kinda impressed and started searching. but i cant find it on this forum so lets google :p

anyway if someone knows more, let us know where dieing to know

---

### Post by poofyhairguy on 2005-07-06
[QUOTE=sickdude]thats not true there is a way, and crap im looking for it (of course) 
[/QUOTE]

[http://www.jankratochvil.net/project/captive/](http://www.jankratochvil.net/project/captive/)

Its really a dead end I think.

---

### Post by Bl0wn2b1ts on 2005-07-06
Hi,

I have a floppy boot disk which is linux and allows you to read/write ntfs - it certainly allows you to modify the windows registry and reset the windows admin passwords! so it must be possible???

Thanks

Bl0wn2b1ts

---

### Post by sickdude on 2005-07-06
[QUOTE=Bl0wn2b1ts]Hi,

I have a floppy boot disk which is linux and allows you to read/write ntfs - it certainly allows you to modify the windows registry and reset the windows admin passwords! so it must be possible???

Thanks

Bl0wn2b1ts[/QUOTE]

what kind of cool floppy is that?

anyway i installed the captive, im still trying to let it work i hope that it work because i dont want to reboot and boot on windooowz to edit and delete some stuff

---

### Post by Bl0wn2b1ts on 2005-07-06
[http://home.eunet.no/~pnordahl/ntpasswd/](http://home.eunet.no/~pnordahl/ntpasswd/)

for the disk stuff

---

### Post by sickdude on 2005-07-06
[QUOTE=Bl0wn2b1ts][http://home.eunet.no/~pnordahl/ntpasswd/](http://home.eunet.no/~pnordahl/ntpasswd/)

for the disk stuff[/QUOTE]
 kewl thnx :)

still no luck with the dam captive prog :( damned

---

### Post by sickdude on 2005-07-13
ok doesnt work for me, i dont know why it doesnt work but i cant get it running :(

maybe someone had more luck?

---

### Post by Punkt on 2005-07-13
[QUOTE=sickdude]ok doesnt work for me, i dont know why it doesnt work but i cant get it running :(

maybe someone had more luck?[/QUOTE]
 Hi guy's!

Captive install isn't that hard you think.
There was a howto in these forums here, but i can't find it yet.

You had to install the linux header's for your kernel an create a user and a group called captive.

I got to install captive again, as soon i found the howto i will post it here.

//edit: so here it is :-)

[http://www.ubuntuforums.org/showthread.php?t=10175](http://www.ubuntuforums.org/showthread.php?t=10175)

---

