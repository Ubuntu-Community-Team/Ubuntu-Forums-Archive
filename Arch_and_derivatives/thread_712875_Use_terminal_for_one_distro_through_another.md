---
title: "Use terminal for one distro through another?"
date: 2008-03-02
forum: Arch and derivatives
---

### Post by MONODA on 2008-03-02
I recently installed Arch Linux on my laptop as a dual boot with ubuntu and sometimes I feel like I need to do something in one distro while im in another. Is there anyway for me to use a terminal to work in Arch while running ubuntu? thanks in advance I know this sounds like a wacky question.

---

### Post by RebounD11 on 2008-03-02
if it were running on another computer you could through ssh... but I think the OS has to be running in order to be able to do that. And in your case I can't see how both systems can run at the same time.

---

### Post by MONODA on 2008-03-02
yeah i kinda doubted that it would be possible but ive seen videos of people running mac and then they press something and then windows comes up

---

### Post by erginemr on 2008-03-02
I don't know if it will help your case, but I now that people are using the command "chroot" to change the running environment (on CLI only) to the installed one while running the Ubuntu Live CD.

---

### Post by MONODA on 2008-03-02
hmmm thanks i think ill read the man pages

---

### Post by odiseo77 on 2008-03-02
Well, there are virtual boxes that allow you to run an OS inside another OS (I've never used it), but if all you want is to use the Arch command line while on Ubuntu, the solution is quite simple: all you have is to chroot your Arch installation.
Here's a simple example of how it would be:

```
sudo mount /dev/ARCH_PARTITION /mnt/ARCH_MOUNTPOINT
sudo -s
chroot /mnt/ARCH_MOUNTPOINT /bin/bash
```

Start typing  your Arch commands and you're done (be careful, since you're working as root). I've even dist-upgraded Debian from Ubuntu in this way :)

---

### Post by MONODA on 2008-03-02
awesome it works thanks :D

---

### Post by odiseo77 on 2008-03-02
Yeah, linux has lots of surprises inside ;)

---

### Post by MONODA on 2008-03-02
yeah thats one of the things i like most about it :)

---

### Post by handy on 2008-06-11
I use the Arch install CD, which is quite minimal, to access non-bootable partitions via chroot for editing.

Boy, I wish I had known how to do that a long time ago.

---

### Post by Dr Small on 2008-06-11
> **odiseo77 said:**
> Well, there are virtual boxes that allow you to run an OS inside another OS (I've never used it), but if all you want is to use the Arch command line while on Ubuntu, the solution is quite simple: all you have is to chroot your Arch installation.
Here's a simple example of how it would be:

```
sudo mount /dev/ARCH_PARTITION /mnt/ARCH_MOUNTPOINT
sudo -s
chroot /mnt/ARCH_MOUNTPOINT /bin/bash
```

Start typing  your Arch commands and you're done (be careful, since you're working as root). I've even dist-upgraded Debian from Ubuntu in this way :)
That is an excellent example. Now I just wish I had a dualboot somewhere that I could try it on :D Thanks for sharing the hint!

Dr Small

---

### Post by Barrucadu on 2008-06-11
I thought you had to fiddle around to get /dev and suchlike working inside the chroot environment. I must be wrong, now I know how easy it is :)

---

### Post by odiseo77 on 2008-06-11
> **Dr Small said:**
> That is an excellent example. Now I just wish I had a dualboot somewhere that I could try it on :D Thanks for sharing the hint!

Dr Small

You're welcome; I'm happy someone finds it useful :)

> **Barrucadu said:**
> I thought you had to fiddle around to get /dev and suchlike working inside the chroot environment. I must be wrong, now I know how easy it is :)

Well, I've noticed that sometimes /dev doesn't work in a chrooted environment and sometimes it does. There's even a command that populates /dev in chrooted environments (as well as other system's directories like /proc); I know I used it once, but now I forgot which command it was. 

I've also noticed the following: I'm currently triple booting Ubuntu 64 bits, Arch 64 bits and Debian Lenny 32 bits. I can chroot Arch (64 bits) from Ubuntu (64 bits) without any problems (and vice versa), but if I attempt to chroot Ubuntu or Arch from Debian (32 bits) I get an error, something about /bin/bash, but I don't remember it exactly (and I'm not home atm to reproduce it). So, my guess is that you can't chroot a 64 bits box from a 32 bits box (and probably, vice versa); something worth to know, just in case.

Greetings.

---

### Post by handy on 2008-06-12
> **odiseo77 said:**
> 
I've also noticed the following: I'm currently triple booting Ubuntu 64 bits, Arch 64 bits and Debian Lenny 32 bits. I can chroot Arch (64 bits) from Ubuntu (64 bits) without any problems (and vice versa), but if I attempt to chroot Ubuntu or Arch from Debian (32 bits) I get an error, something about /bin/bash, but I don't remember it exactly (and I'm not home atm to reproduce it). So, my guess is that you can't chroot a 64 bits box from a 32 bits box (and probably, vice versa); something worth to know, just in case. 

I got a bash error whilst booting last night from my arch64 install CD, to access an arch64 installation, done for the purpose of refreshing my personal memory on doing so in the interest of tell someone else how-to, which is of course how I found this thread.

I don't believe I have ever had the error below before.  Though I now understand why, I think, see below.

Last night at the Arch boot CD bash prompt I used:

[B][I]mkdir /mnt/sda3
mount /dev/sda3 /mnt/sda3
chroot /mnt/sda3 /bin/bash[/I][/B]

Producing the following error:

[B][I]bash: if[ -f /etc/bash_completion ]: No such file or directory
bash: /root/.bashrc: line 4: syntax error near unexpected token 'fi'
bash: /root/.bashrc: line 4: 'fi'[/I][/B]

Which looking at it after some sleep ;-) is all to do with bash_completion, & is in practice inconsequential for (at least) my needs when editing a non-booting partition.

Is that the same error that you got ***odiseo7***7?

P.S. I've added those ever so simple 3 lines to my Addresses on my iPod, so in 3 months time I won't have to reinvent the wheel, or go looking for this thread!

---

### Post by odiseo77 on 2008-06-12
> **handy said:**
> I got a bash error whilst booting last night from my arch64 install CD, to access an arch64 installation, done for the purpose of refreshing my personal memory on doing so in the interest of tell someone else how-to, which is of course how I found this thread.

I don't believe I have ever had the error below before.  Though I now understand why, I think, see below.

Last night at the Arch boot CD bash prompt I used:

[B][I]mkdir /mnt/sda3
mount /dev/sda3 /mnt/sda3
chroot /mnt/sda3 /bin/bash[/I][/B]

Producing the following error:

[B][I]bash: if[ -f /etc/bash_completion ]: No such file or directory
bash: /root/.bashrc: line 4: syntax error near unexpected token 'fi'
bash: /root/.bashrc: line 4: 'fi'[/I][/B]

Which looking at it after some sleep ;-) is all to do with bash_completion, & is in practice inconsequential for (at least) my needs when editing a non-booting partition.

Is that the same error that you got ***odiseo7***7?

P.S. I've added those ever so simple 3 lines to my Addresses on my iPod, so in 3 months time I won't have to reinvent the wheel, or go looking for this thread!

Well, this error is a bit different. I'm currently on Debian 32 bits and in an attempt to chroot my Ubuntu 64 bits installation, located on /dev/sda8, I got this:

```
vicente@debian-box:~$ sudo mount /dev/sda8 /mnt/sda8
vicente@debian-box:~$ su
Contraseña:
debian-box:/home/vicente# chroot /mnt/sda8 /bin/bash
chroot: cannot run command `/bin/bash': Exec format error
debian-box:/home/vicente# chroot /mnt/sda8
chroot: cannot run command `/bin/bash': Exec format error
debian-box:/home/vicente#
```

Note that in the last command I omitted the shell to use, just in case Ubuntu's default shell was other than bash and allow it to use it, but I got the same error.

I googled for this error and although I didn't find an explanation for this, I did notice all the errors were related to people attempting to chroot a 64 bits installation from a 32 bits installation or live-cd, so I guess when you chroot you use your current OS shell (bash) in the chrooted environment, but a shell designed for 32 bits can't be used in a 64 bits environment? (In case someone is interested, [these]("http://www.google.com/linux?hl=en&q=chroot%3A+cannot+run+command+%60%2Fbin%2Fbash%27%3A+Exec+format+error&btnG=Search") are the results of my search).

Greetings :)

---

### Post by Barrucadu on 2008-06-12
I would imagine it is because you are on a 32 bit operating system trying to run programs on a 64 bit one.

---

### Post by mips on 2008-06-22
> **Dr Small said:**
> That is an excellent example. Now I just wish I had a dualboot somewhere that I could try it on :D Thanks for sharing the hint!

Dr Small

Just use a LiveCD.

I'm about to try it on my new arch install as my GRUB is broken and from what I gather it was caused by nano, more here [http://bbs.archlinux.org/viewtopic.php?id=47709](http://bbs.archlinux.org/viewtopic.php?id=47709)

---

### Post by mips on 2008-06-22
> **handy said:**
> 
Which looking at it after some sleep ;-) is all to do with bash_completion, & is in practice inconsequential for (at least) my needs when editing a non-booting partition.

How do I edit a /boot partition?

That is the current dilemma I have. The Arch installer will not reinstall it either as it cannot find it. It is there though.

---

### Post by odiseo77 on 2008-06-22
> **mips said:**
> How do I edit a /boot partition?

That is the current dilemma I have. The Arch installer will not reinstall it either as it cannot find it. It is there though.

Sorry if I'm not getting the whole situation, but what I understand is you have /boot in a separated partition, so when you chroot the "/" partition it can't find the /boot partition? Is this the problem?

I think I had a similar situation before, last year. I don't remember quite well how I fixed it (or if I ever managed to fix it), but if the above is your problem, you could try to create a /boot directory in the chrooted environment (which would create it in the root of "/"), then mount your "/boot" partition inside the /boot directory you just created and attempt to reinstall grub (I think, when I had the problem I mention above, that was one of the things I attempted to do, but as I said, I don't remember if it fixed it).

Also, could you tell us exactly what is broken (grub, your menu.lst or anything else), how's your system's setup (partitions, etc) and what are you trying to do? (Again, excuse me if I don't get the whole situation; I'm just trying to figure it out) :)

EDIT: Well I think there's no need of creating the /boot directory because it should be there already (empty, of course), so all you would have to do would be to mount the /boot partition inside it.

EDIT2: I forgot this, but in case you have /boot in a separated partition and you attempt to install grub in the chrooted environment as I describe above, you will probably find these couple of links useful; they describe how to populate and use /dev in a chrooted environment:

[http://tldp.org/LDP/lfs/LFS-BOOK-6.1.1-HTML/chapter06/devices.html](http://tldp.org/LDP/lfs/LFS-BOOK-6.1.1-HTML/chapter06/devices.html)

[http://www.linuxfromscratch.org/hints/downloads/files/stages-stop-and-resume.txt](http://www.linuxfromscratch.org/hints/downloads/files/stages-stop-and-resume.txt)

---

### Post by handy on 2008-06-22
@ ***mips***:  I use the Arch core install CD & bash commands as per post_14 above:

[I]At the Arch install CD bash prompt I use the following:

**mkdir /mnt/sda3**  (using the Arch CD, means your hard disk drive partitions will start at sda3 )
[B]mount /dev/sda3 /mnt/sda3
chroot /mnt/sda3 /bin/bash
[/B][/I]

Using this strategy I can navigate to  whichever partition I choose by mounting it (sda4, sda5 & so on) & then chroot to it, after which I can edit the config' files with nano, or whatever.

I have found the above method using the Arch install CD to work great on a variety of distro's.  It is quick & simple, which suits me fine. ;-)

***[Edit:]** Having just read the post above, it seems I missed the point of your post :redface: As far as /boot goes, I use it as a directory these days, so I have not had the problem of not being able to access it.*

---

