---
title: "Options BIOS"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by c4taclysmicPr0posal on 2007-07-06
I've been ghosting this site for about 20 hours straight (lots of caffine)  looking to fix my ubuntu box.  I'm completely new to linux, I've never used it before, allready i've learned a ton about the terminal and .iso's.  To be completely honest, i'm comfertable in winblows, but I need to switch, cuz i'm really starting to hate how much it sucks.

Now that we've got that out of the way.  Here's my story.

Last night, i wanted to set up an ubuntu server.  So I dl'd the iso, installed it on my 500gig hd.  the install went fantastic, no problems there, however..when i restarted my box after the install, i got grub error 18.  I know what this is, my harddrive is too big for my BIOS to read.(woot for googling)  My box is really old. HP Pavilion7867 P3 1Ghz 512RAM 500gig hd.  The hd only has ubuntu on it.

I need to know my options (not throw it out..i love that box)


Whether or not i can update my BIOS with WINE.  I need to do something simple.  I'm not that comfertable with the terms yet, but I cant run the server edition until i update the BIOS.  

Help me PLEASE!!!


Note:  The only way I can get on this box at all is with Dapper live CD.

---

### Post by Rocket2DMn on 2007-07-06
True, the BIOS can only read so far into the disk, but the linux kernel does not suffer this limitation.  Basically, you need to set it up so that your boot partition is at the beginning of the disk, so once the kernel takes over, everything else can be loaded fine.  This might be as simple as popping in the live cd and running the install, and when you get the the partitioning portion, have Ubuntu use the whole drive and keep the boot sector at the top.
That's all I can offer at this time.

---

### Post by c4taclysmicPr0posal on 2007-07-06
Thank you very much for your prompt response, i appreciate it.  How do I make it so that it keeps the boot sector at the top.

---

### Post by trak87 on 2007-07-06
The BIOS has nothing to do with Wine, Windows or Linux. The BIOS is a chip you access before any OS starts. You access it with a keystroke while you are booting up. On most desktop systems it's the Del key. On others it may be F2 or Esc. Consult your computer manual or look at the screen as it's booting up and it *may* show what key to press to access it. Otherwise, look up the manual online. Most motherboard manufacturers post them online in PDF format.

I'm not sure how to solve the grub error, however when you install Ubuntu it may help to create a separate partition -- the first one -- for /boot (about 100meg max), and then separate partitions for / (the root partition: 8 gig will do it) and /home (whatever size you want here) as well. Don't forget a swap partition that is twice your installed RAM. You can set all this up by selecting the install option to manually set up your disk partitions. I believe the problem is the boot partition needs to be within 8 gig or so of the beginning of the drive otherwise the older BIOS cannot address areas beyond that (at least in booting up). So separating the boot partition and making it the first partition on the drive may fix it.

---

### Post by Nekiruhs on 2007-07-06
Make a /boot partition at the very beginning of the drive.

---

### Post by c4taclysmicPr0posal on 2007-07-06
I dont know how to make the partitions, that is a setback when doing this.

I'm not looking for a straight answer on the partition one, If someone has a link to a tutorial or something, i'd be more than happy to learn it.

Thank you

---

### Post by trak87 on 2007-07-06
> **c4taclysmicPr0posal said:**
> I dont know how to make the partitions, that is a setback when doing this.

I'm not looking for a straight answer on the partition one, If someone has a link to a tutorial or something, i'd be more than happy to learn it.

Somebody will post a link I'm sure with specific instructions, but generally speaking, during the install process, when it asks you how you want to set up the disk go into the option to manually set up the partitions. Then you want the following partitions:

/boot - 100 meg
/ - (root partition) 8 gig
swap partition - 1 gig
/home - whatever size you want, perhaps 1 gig or more, or you can use the rest of your HD's free space.

It's a bit confusing the first time. Don't worry. You'll get it.

---

### Post by c4taclysmicPr0posal on 2007-07-07
but if you mess it up its no harm no foul right?

---

### Post by c4taclysmicPr0posal on 2007-07-07
Sorry about the double post, trak87's instructions fixed it beautifully.  Thank you very much for your help.  I recommend that this gets put in some sort of archives, or his instructions do, there seem to be alot of questions regarding the grub error18.  


Thank you very much again.

---

