---
title: "ubuntu ultimate dvd problem?"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by m3t3ors on 2008-04-17
ive just downloaded the ubuntu ultimate gamers dvd but its in 2 parts and says i need to join them. but noting i try seems to work
heres where i got it from
[http://proyectos.pixelamigo.com/software/Ubuntu/UltimateGamersEdition/down_url_gamers1.php](http://proyectos.pixelamigo.com/software/Ubuntu/UltimateGamersEdition/down_url_gamers1.php)
and heres what it says to join them
On Windows just type:
type thedirect_ubuntu-ultimate-gamers.iso_part0* > ubuntu-ultimate-gamers.iso

any help here guys would be appreciated

---

### Post by erginemr on 2008-04-17
This may work. From a terminal:
```
cd "the directory where your files are"
cat thedirect_ubuntu-ultimate-gamers.iso_part0* > ubuntu-ultimate-gamers.iso
```

---

### Post by m3t3ors on 2008-04-17
> **erginemr said:**
> This may work. From a terminal:
```
cd "the directory where your files are"
cat thedirect_ubuntu-ultimate-gamers.iso_part0* > ubuntu-ultimate-gamers.iso
```

sorry (forget to say ) i downloaded it to my windows machine

---

### Post by alecz20 on 2008-04-17
does it have a part0 and part1 ?

If so, it's probably a rar archive. You need to download winrar for Winzode, install, then right-click on part0 and chose any of the "Extract" options.

---

### Post by m3t3ors on 2008-04-17
they came down as iso's part 00 + part 1. power iso will open 00 but wont open part 1 as they not joined yet

---

### Post by m3t3ors on 2008-04-17
i could install my linux box but then would have to install it agen when i burn the ultimate

---

### Post by alecz20 on 2008-04-17
Could you try using one of the ubuntu live cd's?

---

### Post by m3t3ors on 2008-04-17
yeh i thought of that and tried pclinuxos but cant remember the user and password to run the live cd

---

### Post by mangurt on 2008-04-17
Hmm....you should be able to put them together with winrar or 7zip for windows.

As for the user name and password for pclinuxos is guest and guest or root and root.

Hope that helps you...

---

### Post by m3t3ors on 2008-04-17
got ubuntu studio live running but my files i need to join are on my external hdd
how do i cd into the drive

---

### Post by m3t3ors on 2008-04-17
ok now this is doing ma head in
in windows 7zip says "unexpected end of archive"?
does anyone know where i can get a working copy of this dvd please

---

### Post by alecz20 on 2008-04-17
when you connect the hard drive it should appear on the desktop. You open it, and then in the window manager look at the address, you might have to press a button to activate the address (it's no on by default on Ubuntu 7.10 as far as ai know)

it should be something like /media/hda1

so when you cd you should probably do:

"cd /media"
"dir" or "ls"
then try all of them :) this should work, I'm not on Linux now, cause I'm at work, so I might be a little off.

Hope it helps!

---

### Post by alecz20 on 2008-04-17
> **m3t3ors said:**
> ok now this is doing ma head in
in windows 7zip says "unexpected end of archive"?
does anyone know where i can get a working copy of this dvd please

did you try with Winrar as i suggested a couple post earlier?

Also you could install winrar on the live session simply using the Add/Remove feature, and search for winrar. Then go to the iso parts, with the window manager, right-click and extract.

---

### Post by m3t3ors on 2008-04-17
> **alecz20 said:**
> did you try with Winrar as i suggested a couple post earlier?

Also you could install winrar on the live session simply using the Add/Remove feature, and search for winrar. Then go to the iso parts, with the window manager, right-click and extract.


i think the files are corrupt
both winrar and 7zip say unexpected end of archive
im downloading a new version from torrent so see wat happens

---

### Post by alecz20 on 2008-04-17
That is also a possibilty, or maybe the files are not archives. I haven't really had any experience with such files. Form torrents you can download huge files withtout problems, even 20 GB blu-ray images for that matter, so you should get the whole image in one file. Might take longer, but should work fine.

This edition of ubuntu sounds pretty large... I've never tried it though.

---

### Post by m3t3ors on 2008-04-17
thanks guys for all your advice. im downloading part 1 again as thats the part with the errors
if still no good il go with the torrent

---

### Post by m3t3ors on 2008-04-18
thanx again guys i have a working distro now. will install it over thw weekend

---

### Post by m3t3ors on 2008-04-19
just burnt ultimate gamers edition 1.6
burnt using poweriso at the slowest speed (4x)  think
when i tried it on my xp machine it booted into the live dvd and ran smooth
so tried installing to my linux box but after the splash screens all im getting is a command prompt
any help appreciated guys

---

