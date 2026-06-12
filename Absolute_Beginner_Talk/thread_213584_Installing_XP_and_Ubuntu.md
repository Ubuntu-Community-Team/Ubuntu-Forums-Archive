---
title: "Installing XP and Ubuntu"
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by Emceay on 2006-07-11
I have two serial ATA drives and an IDE.

--Originally, I had Ubuntu installed on the IDE and XP on one SATA, but I've lost the ability to boot into XP. I tried all the fixes, and I'm pretty sure my MBR is messed up because I get the ntdlr message when I try to start windows. Luckily, the windows drive was mountable in ubuntu and I've transferred everything important to a second blank SATA.

Here's the thing: I want to dual boot Ubuntu and Windows with each on it's own respective hard drive and have grub offer options between the two.

I know I should install XP first so that grub can detect it, but is that all there is to it? Because grub didn't detect XP the first time when I put ubuntu on the IDE.

Should I disconnect all drives except the one I'm installing XP to? Would it write an MBR to another drive if I don't?

I'm really confused about all this, but I **really** want to get Ubuntu set up and working happily with windows so that I can actually enjoy Ubuntu instead of cursing it's drive distorting existence.

How do I start on the right foot?

---

### Post by digby on 2006-07-11
The first thing to check is the boot order in your BIOS.  You want to make sure that your computer is trying to boot off the SATA drives before it tries the PATA (IDE).  Then, when you install ubuntu, you'll have to tell it to install grub onto sda (the first SATA drive) if it doesn't want to do that automatically.

---

### Post by Emceay on 2006-07-11
So... are you saying to install grub to the SATA that has windows on it? Because I thought windows was supposed to be installed first..?
At this point I have a working XP on a SATA and I'm about to put Ubuntu on the other SATA. Needless to say, I'm scared, I don't want to lose XP again and end up back at square one again.

I've disconnected the IDE which has it's own copy of ubuntu so that Nothing gets confused until the SATAs are taken care of. I plan to wipe the copy of ubuntu on the IDE once it's installed to the second SATA.

Any suggestiongs before I attempt to not kill my computer again?

---

### Post by digby on 2006-07-11
Ok - I misunderstood - I thought you were putting ubuntu on the other (not sata) drive.  Ok - this shouldn't be hard (and is very similar to my former setup).

I had windows on my first SATA drive (/dev/sda) and ubuntu on my second (/dev/sdb).  If windows is installed and nothing else, you should just be able to install ubuntu to the second drive (you may have to do just a bit of manual work at the partitioning stage to make sure it knows to install to the second drive, but it will list drives and what is on them, so it will be easy to pick).  Near the end, when the installer wants to install grub, it will give a list of operating systems it has found.  If it finds windows, all is well.

You want it to install grub to your windows drive, because grub is capable of chainloading windows (i.e. grub will call the windows bootloader).  The only other real option is to make a copy of the linux boot sector, put it on your c:\ drive and edit boot.ini by hand.  Not terrible complicated, but not nearly as easy.

Does that make any sense?

---

### Post by Average_Joe on 2006-07-11
dual boot on 2 drives [http://tinyurl.com/kr8x2](http://tinyurl.com/kr8x2)

---

### Post by Emceay on 2006-07-11
Thank you two, I'm sitting in front of an empty XP desktop. And now i'm making the 'touchdown' gesture with my arms. Y'all rock.

---

### Post by Average_Joe on 2006-07-11
Just send a private message to confused57 ... to thank him, as he is the one who put together that excellent tutorial for dual boot on 2 drives.

---

### Post by Emceay on 2006-07-11
I would, but he's out of town :D He was helping me earlier when I put ubuntu on IDE.

I'm actually surprised it went so smoothly, only took 45 minutes.

Moral of the story: Two SATAs are better than SATA and IDE for dual boot.

Though I'm curious what happens when I fire up the IDE and have dueling ubuntus...

---

