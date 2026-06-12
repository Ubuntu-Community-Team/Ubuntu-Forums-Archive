---
title: "Ubuntu install toooo slow =/"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by TrIde2188 on 2006-08-30
Ive downloaded the iso from the site, put it on a disc run it. i get  to the gui eventually after waiting agess for it to laod..then i click install on the desktop, eventuall it also loads, but then when i get to the choose keyboard part.. i click forward... and it jsut ... crashes kidna.. it just never laods i even bothereds waiting 30 mins for it to try and load while watchign a film =P but still no response

any help is welcomed :)


-TrIde

---

### Post by bruce89 on 2006-08-30
What are the specs of the computer in question?

---

### Post by Jussi Kukkonen on 2006-08-30
Less than 200MB of memory might be the reason -- use Alternate Install if this is the case.

---

### Post by PPAAUULL on 2006-08-30
I doubt it would be the less then 200mb of RAM because I installed it fine on a computer with P-III 128mb RAM.

---

### Post by TrIde2188 on 2006-08-30
WEll ive isntalled other distros perfectly :P

erm not too sure about the specs its a laptop - a friend of mines who had ubuntu installed on it before i bought it off him =]

is there a way of starting the install in the command line - i mena after ive pressed alt+ctrl+f1 ?


-TrIde

---

### Post by PPAAUULL on 2006-08-30
Not sure about that but did you check the cd for Defects and check the MD5 sum before burning it? The CD might be at fault.

---

### Post by TrIde2188 on 2006-08-30
May jsut be my stupidity =/ but i cant see an md5 on this site in the download section =/ lol

---

### Post by PPAAUULL on 2006-08-30
Well have you done a defect check with the CD? It can check its self too.
I will find the MD5 sum for you.

---

### Post by bruce89 on 2006-08-30
The CD can check itself AFAIK, it's one of the options in the boot menu for it.

---

### Post by PPAAUULL on 2006-08-30
Here you go. Check it against which ever one you downloaded.

b9a5be3a5858ade278d664d41310a4ab  ubuntu-6.06.1-alternate-amd64.iso
6cb8582aa5615ed4616165743a0868d7  ubuntu-6.06.1-alternate-i386.iso
0b5b3df02da3d9ed6f4ac482cf541f04  ubuntu-6.06.1-alternate-powerpc.iso
50e3912c555f98f7bca56b2a0200b205  ubuntu-6.06.1-desktop-amd64.iso
fb3af44c21f1f68cc25fda7edb8c1bd3  ubuntu-6.06.1-desktop-i386.iso
502911770ad173dbe82c698379ed7d11  ubuntu-6.06.1-desktop-powerpc.iso
8254b0f3696ed17c52a2cb59c9ebd2cc  ubuntu-6.06.1-server-amd64.iso
5ad76d8b380ab5be713e5daa9ea84475  ubuntu-6.06.1-server-i386.iso
6d1c3b5cb41661365b3db5cf12bb2836  ubuntu-6.06.1-server-powerpc.iso
2ccc1ec608040e6aac8913a016c31bed  ubuntu-6.06.1-server-sparc.iso

---

### Post by TrIde2188 on 2006-08-30
Hmm i dont think its the md5 coz the cd loads up fine, jus tit wont let me isntall it well it would.. just goes uber slow and im wondering if theres a code i can type in to start the install in the cmd line non gui side of linux (i.e. the alt+ctrl+f1 :P)

---

### Post by PPAAUULL on 2006-08-30
But did you check the CD for defects? You should check it anyways.

---

### Post by TrIde2188 on 2006-08-30
I'm doing the check now

---

### Post by PPAAUULL on 2006-08-30
Ok good.

---

### Post by TrIde2188 on 2006-08-30
It seems to be err stuck on 
Checking ./casper/filesystem.squashfs

---

### Post by bruce89 on 2006-08-30
> **TrIde2188 said:**
> It seems to be err stuck on 
Checking ./casper/filesystem.squashfs

That file takes a long time as it is practically the entire disk.

---

### Post by TrIde2188 on 2006-08-30
Ah right ok fair enough 

0 checksums failed ...
any more ideas? =/

---

### Post by PPAAUULL on 2006-08-30
The CD is in good condition right?

---

### Post by TrIde2188 on 2006-08-30
Brand new cd-r =]

---

### Post by PPAAUULL on 2006-08-30
hmmm What are your computers specs?

---

### Post by TrIde2188 on 2006-08-30
AMD K6/2 500mhz
128mb ram
20GB HDD

---

### Post by PPAAUULL on 2006-08-30
Ya that 128mb of ram might be your problem. How many times have you tryed to install it?

---

### Post by bruce89 on 2006-08-30
That is nowhere nearly enough RAM, you'd be better off with Xubuntu, but it might not work either.

Ubuntu recommends at least 256MiB.

---

### Post by PPAAUULL on 2006-08-30
I tend to agree with bruce although I don't know if it is the same but I used flux box on the same setup as you have and it wouldn't run either so you could try Xubuntu. I am not sure if it will work. anyone know how it compares to Fluxbox?

---

### Post by jdong on 2006-08-30
You do not have enough RAM to be using the Live (Desktop) installer.

Ubuntu's installer is fairly unique that it boots a full-blown Ubuntu desktop from the CD and gives you that desktop to use while installing. This takes a considerable amount of RAM, and I really don't recommend people with less than 256MB of RAM to attempt it. Else, you risk extreme slowness and crashing.


After install, if you are using the default GNOME desktop, I don't think 128MB of RAM would make you happy either, though I can see a bit of swap space helping you pull that off. As others have said, you might want to give a lighter Ubuntu variant, like Xubuntu a try.


And as always, use the 'alternate' CD. It's less pretty, but requires far less RAM.

---

### Post by TrIde2188 on 2006-08-30
=/ hnmmmmy mate was able to use ubuntu perfectly then he gave it to me, and he uninstalled it - dunno why =/ so yea..

---

### Post by PPAAUULL on 2006-08-30
That is weird that he uninstalled it. I would have left it if I had have known that you would have wanted it.

---

### Post by firezip on 2006-08-30
> **TrIde2188 said:**
> AMD K6/2 500mhz
128mb ram
20GB HDD

When I tried installing ubuntu on my old Dell laptop with 128 it just froze when trying to install. My suggestion is the download the Alternative install cd which is basically text-ui install.

---

### Post by TrIde2188 on 2006-08-30
Indeed - well thanks anyway for you help

---

### Post by PPAAUULL on 2006-08-30
I installed Ubuntu on my brothers PC using the alternative CD and it had 128mb of ram. It works perfectly but is a little slow campared to my system.

---

### Post by TrIde2188 on 2006-08-30
Can anyone give me the link or ... what do you mean by the alternative cd =/

---

### Post by PPAAUULL on 2006-08-30
Look for this "Alternate install CD" here or on any country selection [http://ubuntu-releases.cs.umn.edu//6.06/](http://ubuntu-releases.cs.umn.edu//6.06/)

It is one of the titles like "Desktop CD"

Hope that helps

---

### Post by jdong on 2006-08-30
The "Desktop CD", the one you're using, boots up into a pretty graphical interface and has a point-and-click installer designed for ease-of-use. The cost is that it requires around 256MB of RAM to run.


The "alternate CD" uses an old fashion, keyboard driven installer. It's not as friendly looking, but gets the job done and uses far less RAM.


The Ubuntu alternate CD is at [http://releases.ubuntu.com/6.06.1/ubuntu-6.06.1-alternate-i386.iso](http://releases.ubuntu.com/6.06.1/ubuntu-6.06.1-alternate-i386.iso). Note that after installing it, the Ubuntu desktop (called "GNOME") probably won't run too smoothly with 128MB of RAM, so your system might feel slow.


An alternative solution is to use Xubuntu, which is Ubuntu with a lighter, simpler, alternative desktop that uses less RAM. You can find its installer CD at [http://cdimage.ubuntu.com/xubuntu/releases/6.06.1/release.1/xubuntu-6.06.1-alternate-i386.iso](http://cdimage.ubuntu.com/xubuntu/releases/6.06.1/release.1/xubuntu-6.06.1-alternate-i386.iso)


Whichever one you choose is your choice. Naturally, Ubuntu will be somewhat more user-friendly than Xubuntu, but that's all pretty pointless if the system is so slow that it's not usable!

If you have time, I'd recommend you try both :)

---

