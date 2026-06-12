---
title: "Best method for my dual-boot installation"
date: 2006-04-06
forum: Absolute Beginner Talk
---

### Post by lummoxcooties on 2006-04-06
My only experience has been the ubuntu live CD, installing a single OS (xp home), but never 2 OS's on 1 computer.

My HD has 4 GB of unpartitioned space, and I was wondering if this is enough space for using ubuntu with xp on the used drive?

What is the easiest/best way to put Ubuntu on there using the CD that shipped to me. I dont want to harm the other partitions in any way or lose data, unless shrinking my used partition is safe. 
How do I create a swap partition?

Is there a way to have xp be the primary boot (meaning that it will load on startup automatically), -I just found my answer [https://wiki.ubuntu.com/GrubHowto/ChangeDefaultOS]("https://wiki.ubuntu.com/GrubHowto/ChangeDefaultOS") but what and where is the terminal?

---

### Post by catlett on 2006-04-06
The terminal is where you enter commands. In windows it is the command line c:\. You find it by going to the panel at the top of the screen. Click on " Applications". Scroll down to the first entry "accessories". A box will slide out. Move over and scroll down to "terminal". Click on terminal and a window with the terminal will appear. That is where you will enter commands. To make it easier in the future right click on the terminal when you scroll down to it. This will give you an option box. You can choose an option to add it to the panel. This will put an icon for the terminal on the panel so you don't have to scroll through the menu for it.

This is a good how to. [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by htinn on 2006-04-06
If you only have 4 GBs of free space, you will definitely be pushing it. In my experience, you will need about 1.5 GBs for the swap partition, which will leave 2.5 GBs for the rest. The install will take about 1 GB, leaving about 1.5 GBs for whatever else you want.

---

### Post by MacV on 2006-04-06
[QUOTE=htinn]If you only have 4 GBs of free space, you will definitely be pushing it. In my experience, you will need about 1.5 GBs for the swap partition, which will leave 2.5 GBs for the rest. The install will take about 1 GB, leaving about 1.5 GBs for whatever else you want.[/QUOTE]

Just curious, why would you need over a gig of swap space?

---

### Post by htinn on 2006-04-06
MacV, I like to run a lot of apps at the same time. Firefox, the GIMP, OpenOffice, etc. They really give my swap a workout, too. :P

Actually, I tend to prefer about 2 GBs of swap, myself.

---

### Post by MacV on 2006-04-06
[QUOTE=htinn]MacV, I like to run a lot of apps at the same time. Firefox, the GIMP, OpenOffice, etc. They really give my swap a workout, too. :P

Actually, I tend to prefer about 2 GBs of swap, myself.[/QUOTE]

Ah, that would explain it. Thanks.:)

---

