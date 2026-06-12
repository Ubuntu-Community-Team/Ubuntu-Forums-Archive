---
title: "Dual l booting with Windows XP"
date: 2006-06-03
forum: Absolute Beginner Talk
---

### Post by adwait on 2006-06-03
Hello,

I need to reinstall everything on a new computer including Windows XP and Dapper. Can anyone tell if this going to be easy or are there are any special tricks that I need to know? On my PC I use the ancient Win ME, and hence installing Ubuntu was just a matter of partitioning and installin and the rest was handled by the installer (this was way back with hoary).

At that time, I had tried to install Ubuntu on another friends PC with Win XP, but  couldn't get it to work because XP kept loading up when booting without asking whether to boot into windows or linux.

Adwait

---

### Post by skinnygmg on 2006-06-03
just make sure you install xp first, or else xp will kill ubuntu

---

### Post by u.b.u.n.t.u on 2006-06-03
I can only comment on XP. The install/setup is somewhat different with XP service release 2 as they patched it with a firewall (which I don't recommend using - sygate free is the best for windows), and also an "alert" system.

So your computer isn't safer now, you just get told about it (read pestered).

XP system requirements are much higher than ME.  On the good side, more devices are detected.

"Can anyone tell if this going to be easy" - it depends on what you know. I can install and configure XP without a sweat but maxed out being annoyed by it.

If you have a specific XP question perhaps I can assist. I am new to ubuntu so I can't be much help there, sorry.

---

### Post by CalvinChile on 2006-06-03
As  skinnygmg points out, you first install XP, leaving part of the disk free for later mounting Dapper. Once you have finished with XP, boot wit Dapper CD and choose to use the unformated or free space for installing Linux. During the final stage, the installer will setup GRUB to allow the dual boot.

---

### Post by Sasquatch2000 on 2008-04-14
> **CalvinChile said:**
> As  skinnygmg points out, you first install XP, leaving part of the disk free for later mounting Dapper. Once you have finished with XP, boot wit Dapper CD and choose to use the unformated or free space for installing Linux. During the final stage, the installer will setup GRUB to allow the dual boot.

By "leaving part of the disk free", do you mean another partition? Or just more space in the same partition? 

Is this also relevant for Windows 2000?
How about Ubuntu 8.04 Beta? 


Thank you!

---

### Post by OldTimeTech on 2008-04-14
I'm dual booting on a number of machines with Win 2000, WinXP and Vista....with both XP and Vista once they are loaded, you defrag and then make sure your CD is first in boot.  Place Live CD for Gutsy or feisty in machine....when you click on the install button....it will come up and ask you do you want whole disk, guided portion and it gives one that is largest free space, that is what you click on and the cd will take it from there.

---

### Post by Sasquatch2000 on 2008-04-14
Does that then eat up all my free space from Windows?

Also, does the new 8.04 do things any differently?

I don't want to overwrite or blow away my Windows, nor do I want to steal all my free space. 

Also, the installer says it will be degraded performance running it this way. Why, and what does this mean, and compared to what? Compared to installing using the command line?

Thanks.

---

### Post by stevezygote on 2008-04-14
[SIZE="4"]Is there a definitive guide to dual-booting an XP (first install) and Linux-ubuntu set up? How to do it, etc. Thanks.[/SIZE]

---

### Post by phidia on 2008-04-14
The many methods of installing are [here]("https://help.ubuntu.com/community/Installation").
Look at the bottom of that page, from the link above,"Other Installation guides" and "Windows dual boot".

---

### Post by Inxsible on 2008-04-14
> **stevezygote said:**
> [SIZE=4]Is there a definitive guide to dual-booting an XP (first install) and Linux-ubuntu set up? How to do it, etc. Thanks.[/SIZE]

Here's a couple more [Partitioning]("http://www.psychocats.net/ubuntu/partitioning") [Installing]("http://www.psychocats.net/ubuntu/installing")

---

### Post by jmore9 on 2008-04-14
Hello !

I dual boot winxp sp2 and ubuntu .  It is very easy to do , just install winxp then figure out where you want to put ubuntu.  I use a second drive and install ubuntu on that,  After you decide where you want ot install ubuntu you just run your cd / dvd of choice and install,  if will find your winxp and put both in  the grub menu.  Almost all versions of llinux today are very easy to dual boot with windows.  The grub menu will give you a choice of which one to boot. hope this helps.  Any questions just ask.

---

### Post by laffinet on 2008-04-14
> **Sasquatch2000 said:**
> By "leaving part of the disk free", do you mean another partition? Or just more space in the same partition? 

Is this also relevant for Windows 2000?
How about Ubuntu 8.04 Beta? 


Thank you!

Last question first: Ubuntu 8.04 works the same.

You can install windows using all the space on your hard drive, you then have two options when installing Ubuntu:
a) automatic install, which means Ubuntu will shrink your existing partition (you can choose the size, I think) and then creates new partitions to install Ubuntu in
b) manually partition the hard drive during installation, which gives you more control (plus the option of having a separate partition for home)

---

### Post by bt224 on 2008-04-14
Piece of cake, really. During install do not select the option to use all your space. Do manual and you can pick out how much you want to allocate for Ubuntu. The great thing about doing everything fresh is that if you totaly dork it, your just out a few hours and nothing else is lost. Give it a try and just pay attention during the Ubuntu install. If you have a question, stop until you get it answered.

---

### Post by Sasquatch2000 on 2008-04-15
This is still very unclear. The installer doesn't really make it that clear either. 

Another question: Is there a way to share a volume/directory/folder between BOTH Windows and Linux? If so, how?


The thing I fear is that if I hit the button to do any of this, it will either cause data loss, or at the least, a large time loss recovering from this.

Thanks.

---

### Post by lil0tik on 2008-04-15
Hey Sasquatch -

As far as interaction between the XP and Ubuntu partitions goes, the genral rule is that you can access your Windows partition just fine from Ubuntu, but not the other way around.  As far as i know, the two OSes have to be set up on separate partitions unless you're using something like VM Ware to run XP in Ubuntu...

I've set up a dual boot (Vista & Gutsy) on my PC a couple times now, and I've found the easiest way is to 

1)  install windows onto a partition of at least 1/2 your total available HDD space (for some reason, I always run into trouble if I give Windows the smaller half of the disc)
2) once that's done, install Ubuntu on a second partition, using the "Use Largest Contiguous free Space" option in the installer, rather than messing around with re-sizing the Windows partition or trying to guess the exact amount of free space.  

The process should go quite smoothly, if my own experience is anything close to typical.

Good luck,
-p.

---

### Post by Paqman on 2008-04-15
> **Sasquatch2000 said:**
> 
Another question: Is there a way to share a volume/directory/folder between BOTH Windows and Linux? If so, how?


That's pretty simple, it turns out. Just create a separate partition and format it as NTFS. Both Windows and Ubuntu can use NTFS. Windows will automatically mount it as D:\ drive (or some such). During Ubuntu installation you can use the manual partitioning option to pick a mount point for it. If you pick /media/something it'll show up on your desktop when you boot.

Since it's an NTFS drive it'll get fragmented. Just run the Windows defragger through it every so often to keep it all shiny.

---

### Post by Sasquatch2000 on 2008-04-16
> **lil0tik said:**
> ...As far as interaction between the XP and Ubuntu partitions goes, the genral rule is that you can access your Windows partition just fine from Ubuntu, but not the other way around.  As far as i know, the two OSes have to be set up on separate partitions unless you're using something like VM Ware to run XP in Ubuntu...

This seems strange, as it was accessible from Windows before Ubuntu.


> **lil0tik said:**
> 
I've set up a dual boot (Vista & Gutsy) on my PC a couple times now, and I've found the easiest way is to 

1)  install windows onto a partition of at least 1/2 your total available HDD space (for some reason, I always run into trouble if I give Windows the smaller half of the disc)
2) once that's done, install Ubuntu on a second partition, using the "Use Largest Contiguous free Space" option in the installer, rather than messing around with re-sizing the Windows partition or trying to guess the exact amount of free space.  ...

Again, does this now leave zero free space for Windows? STILL unclear. Sorry to be a pain about this, but I just want to make sure all the i's are dotted and t's are crossed before even attempting this.

---

### Post by Paqman on 2008-04-16
> **Sasquatch2000 said:**
> 
Again, does this now leave zero free space for Windows? STILL unclear. Sorry to be a pain about this, but I just want to make sure all the i's are dotted and t's are crossed before even attempting this.

No, you'd want to leave Windows some free space when you create the partitions. Several GB, preferably.

---

### Post by Ravensound on 2008-04-16
Not sure if this is relevant, I discovered on a new Acer laptop with Vista that it appears to have some sort of recovery partition on the hard disk.  When loading Ubuntu the GRUB boot loader starts  the recovery system (which will wipe all your personal stuff) instead of Vista start-up.  If this happens I found that changing the GRUB boot text line "hard drive 0,0" to "hard drive 0,1" solves it.

---

