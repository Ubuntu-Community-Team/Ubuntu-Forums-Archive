---
title: "Installing Ubuntu on a new system"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by mramsey on 2007-03-05
I have some questions about installing Ubuntu on a new, never configured system.  I am new to linux and fairly savy when it comes to windoze.  I am building a new system from scratch for linux so that I can have a "learning tool" for linux without the pressure from my wife not to screw up our main pc. Now for the questions...

Once I have assembled all of the compatible components, how do I do the install of Ubuntu?  Most of what I have read leans more toward installing on a windoze machine as a dual boot system. Do I need to have a version of DOS?:confused: Initial bios settings before installation? Will ubuntu format the HDD?

I appreciate your help with my noob ramblings.

---

### Post by indytim on 2007-03-05
There's an option in the install to install the ops across the whole h/d (will wipe out the entire contents).  From what you mentioned in your post this seems to be where you want to go.

Having said that, here's another curve to consider early on.  A lot of the communiy likes to explore other versions of the Ubuntu family.  The usual scenerio is to have a stable everyday ops and try out other versions / flavors.  What I'm leading toward is that, for a fresh h/d you may want to pre-configure the h/d with a number of ext3 partitions and one swap.  I'd recommend taking the partition count above 4 initially so you force extended partitions.  That way, you can do sufficient exploration without boxing yourself in.  

We've got several excellent tools for partitioning.  My personal preference is GParted Live (it's bootable).  Can be found at [http://gparted.sourceforge.net/index.php]("http://gparted.sourceforge.net/index.php")

Hope this helps and welcome aboard.

IndyTim

---

### Post by Ek0nomik on 2007-03-05
I am new to Linux as well, and here is what I have done:

Last Summer I ran strictly Ubuntu on one of my boxes.  I downloaded 6.10, ran the LiveCD, and from the LiveCD I installed Ubuntu (I also reformatted the drive).

Currently I am running Ubuntu on my Laptop.  I am currently dual booting (although after this good experience I want to get rid of Windows).  If you can't afford to reformat, try to defrag your harddrive in Windows a few times.  Try to clean up the files and get them towards the front of the drive.

If you can afford to reformat (which, these days everyone should be able to, harddrives are cheap), I would put in your Windows installation disc.  Reformat the entire drive (NTFS, I wouldn't do NTFS Quick), and proceed with installing Windows.  Than, I would boot into the Ubuntu LiveCD, and install it.  There are plenty of guides on how to setup your partitions, so that I will leave to you.

Hope some of that helps!

Cheers!

---

### Post by Icarosaurus on 2007-03-05
You don't need any DOS, or any other operating system.
Linux is an operating system itself.
Just put your ubuntu dvd or cd in your machine, set up the bios so that it can boot from cd first and install.
You can choose how to partition in the installation process. 
Good Luck!

---

### Post by Gerard Barberi on 2007-03-05
If you're going to use it as a "learning tool", maybe you would want to mount the /home on a separate partition?  It will keep your data and config settings even if you need to reinstall the system ever.

---

### Post by Ek0nomik on 2007-03-05
Good point, I forgot to mention that.

DOS was an OS itself.  (Disc Operating System)  [http://en.wikipedia.org/wiki/MS-DOS](http://en.wikipedia.org/wiki/MS-DOS)

Linux is a completely separate OS.  You have probably just seen the Terminal and relate it to that.  :)

Cheers!

---

### Post by vincentvee on 2007-03-05
no dude, you don't need DOS
if you only want ubuntu on the machine, you can just fill the whole brand new drive by selecting "erase entire disk" during install, which i am sure will be better if you are new, this will use the whole hard drive for you ubuntu install
> **mramsey said:**
> I have some questions about installing Ubuntu on a new, never configured system.  I am new to linux and fairly savy when it comes to windoze.  I am building a new system from scratch for linux so that I can have a "learning tool" for linux without the pressure from my wife not to screw up our main pc. Now for the questions...

Once I have assembled all of the compatible components, how do I do the install of Ubuntu?  Most of what I have read leans more toward installing on a windoze machine as a dual boot system. Do I need to have a version of DOS?:confused: Initial bios settings before installation? Will ubuntu format the HDD?

I appreciate your help with my noob ramblings.

---

### Post by mramsey on 2007-03-05
Thanks for all of the quick replies folks!  The support in this forum is the best I have ever had. 

I like IndyTim's idea of 3 or 4 partitions to taste the other flavors.  It seems like this is pretty straight forward for the install.  I will finish purchasing my components this week for the build. 

This should work well with my NAS, it is Linux as well.  :) 

How about video requirments? Onboard video good enough? I guess what I am asking is (based on windoze) can i just add an AGP or PCI video card later if needed? when it comes to adding hardware, aside from the obvious being linux supported, is it pretty much plug and play?

---

### Post by Icarosaurus on 2007-03-05
Well, onboard video should be good enough...it depends on performances you want.
Usaully integrated video boards are not the top. Of course, you can add pci or agp cards later, but you should document first on the modules needed etc... you could find yourself with a black terminal, and this could be hard for a newbie.

Choose your hardware well, I saw some "hardware compatibility list" in internet.
Nvidia video cards are better supported than ati ones under linux :)

---

### Post by drs305 on 2007-03-05
I am in the same situation as the original poster, mramsey. If I partition my new hard drive correctly, you are saying I could set up partitions for both 32 bit AND 64 bit or Fiesty AND Edgy, with one swap partition and one home partition? That would be great!

Thanks.

---

### Post by Icarosaurus on 2007-03-05
You can try, but lot of programs store their settings in your home partition, so you could have problems (not very big problems, of course) with different settings of the applications in your different flavours.
If you don't plan to set differently your linux flavours, it should work.
:)

---

### Post by vincentvee on 2007-03-05
> **Ek0nomik said:**
> Good point, I forgot to mention that.

DOS was an OS itself.  (Disc Operating System)  [http://en.wikipedia.org/wiki/MS-DOS](http://en.wikipedia.org/wiki/MS-DOS)

Linux is a completely separate OS.  You have probably just seen the Terminal and relate it to that.  :)

Cheers!
i always thought DOS was derived from QDOS which meant Quick Dirty Operating System

---

