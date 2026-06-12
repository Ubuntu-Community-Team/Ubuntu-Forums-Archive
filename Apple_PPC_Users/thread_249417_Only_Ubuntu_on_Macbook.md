---
title: "Only Ubuntu on Macbook"
date: 2006-09-02
forum: Apple PPC Users
---

### Post by hendrixiano on 2006-09-02
It's possible install only Ubuntu on Macbook and remove Mac Os X?
Do Ubuntu support bluetooth and isight?

Thanks and excused me for bad english (i'm italian).

---

### Post by jeremylh on 2006-09-02
If you have an Ubuntu Desktop CD, I would assume all you have to do is insert the CD and hold down the "c" key while starting up your MacBook. When you're installing Ubuntu, it'll ask you if you want to erase the entire hard drive and install Ubuntu or partition your hard drive (so you can have OSX and Ubuntu on your Macbook).

---

### Post by hendrixiano on 2006-09-02
And the bootloader? I must install only elilo or other?

---

### Post by emrys on 2006-09-02
Have someone tried this yet?

I'm interested on running only Ubuntu in my MacBook too.

It seems there are some problems with grub as of now: [http://ubuntuforums.org/showthread.php?t=243783](http://ubuntuforums.org/showthread.php?t=243783)

---

### Post by omns on 2006-09-02
...

---

### Post by emrys on 2006-09-02
> **manicka said:**
> Is it an intel or ppc machine?

Mine is an intel MacBook

---

### Post by omns on 2006-09-02
.

---

### Post by momo66 on 2006-09-02
yes you can.  I have Ubuntu installed but havent tried bluetooth or isight.

Try the ubuntu live cd first to see if you like before removing osx.

---

### Post by hendrixiano on 2006-09-07
> **momo66 said:**
> yes you can.  I have Ubuntu installed but havent tried bluetooth or isight.

Try the ubuntu live cd first to see if you like before removing osx.

And the bootloader? Only eLilo or i have install rEFIt?

---

### Post by hendrixiano on 2006-09-10
Up... :(

---

### Post by monotux on 2006-09-10
First of all, you need to install rEFIt from OS X, and then either use a patched GRUB or a plain LILO.

I'm pretty sure that bluetooth works out of the box in Ubuntu, but the iSight might be a bit more tricky (I'm not sure, tho).

There are tons of documentation on the subject on the net, good hunting :)

---

### Post by aoao on 2006-09-10
If you plan to install only Ubuntu on your macbook, you may want to have a look at this old post:
[http://ubuntuforums.org/showthread.php?t=233243](http://ubuntuforums.org/showthread.php?t=233243)
I have both Ubuntu and osX on my macbook and boot with lilo, so haven't tried yet.
Good luck,
Andrea

---

### Post by deleted1028 on 2006-09-10
I've had just ubuntu on a ppc mac, wasn't any problem. If you decide you don't like it just reinstall osx or something else... scott

---

### Post by Entity on 2006-09-11
In order to obtain an Ubuntu Dapper only installation go to [http://www.ubuntuforums.org/showthread.php?t=233243](http://www.ubuntuforums.org/showthread.php?t=233243)

---

### Post by tribaal on 2006-09-11
Ubuntu uses GRUB as a bootloader, not lilo like other projects. 
The default installation should take care of this by default.

Hope this sort of helps

- trib'

---

