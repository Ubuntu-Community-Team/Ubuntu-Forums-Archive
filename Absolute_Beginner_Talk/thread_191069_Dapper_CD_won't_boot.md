---
title: "Dapper CD won't boot"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by markfasano on 2006-06-07
This one's a real puzzler. I am trying to install Dapper Drake on a Dell Dimension 8300 with Windows already on it. I changed the boot order in BIOS to list CD player first, HD second and inserted my Live CD (which has successfully installed Dapper on another PC). The CD lights up first, indicating that BIOS is checking the CD player first, then the HD light, but *then[* BIOS whizzes right past the Live CD and begins starting up Windows. 

!!!???

I know the CD drive recognizes the Live CD because it registers in My Computer and its promo desktop runs on being double-clicked. And as I've said, this CD has successfully installed Dapper on another machine.

Help!

---

### Post by cam2009 on 2006-06-07
i just had this same problem. sorry to say I can't help much, but I tried a couple other CDs, too. I had 5.10 on a CD-RW, and Dapper on both a CD-R, and a CD-RW. Only the 5.10 (LiveCD) works. it's like it recognizes the CD, but doesn't see anything to boot, so it skips it, just like if you had a CD with photos on it or something. The boot order isn't the problem, since it will run some and not others

---

### Post by confused57 on 2006-06-07
[QUOTE=markfasano]This one's a real puzzler. I am trying to install Dapper Drake on a Dell Dimension 8300 with Windows already on it. I changed the boot order in BIOS to list CD player first, HD second and inserted my Live CD (which has successfully installed Dapper on another PC). The CD lights up first, indicating that BIOS is checking the CD player first, then the HD light, but *then[* BIOS whizzes right past the Live CD and begins starting up Windows. 

!!!???

I know the CD drive recognizes the Live CD because it registers in My Computer and its promo desktop runs on being double-clicked. And as I've said, this CD has successfully installed Dapper on another machine.

Help![/QUOTE]

On my Dell Dimension, I have to press "F12" during bootup to access boot from CD drive.

---

### Post by markfasano on 2006-06-07
Bump. Does anyone know what might be causing this?

---

### Post by drtvasudevan on 2006-06-08
i heard that the windows instalation is the problem.
some vendors make it impossible to install nay other os.
how they do it i dont know.
my friend bought a laptop in france and ran into the same problems.
i gave him a ubuntu live cd that wont run in his laptop
otherwise the cd is fine.

tv

---

### Post by markfasano on 2006-06-09
I put the Live CD in the DVD drive and the install screen came alive. When my BIOS indicated it checks the CD drive first upon booting, apparently it meant it checks the DVD drive first.

---

