---
title: "Bsd"
date: 2005-12-12
forum: BSD
---

### Post by xequence on 2005-12-12
I am interested in BSD, and want to learn more about it.

Who here has used BSD before? Which have you used? Did the version (as in Net, Free, PC, etc) include a DE? Was it easy to install? How is hardware recignition? Is it easy to install programs? How stable is it? How does it differ from linux, how is it the same? Anything else I havnt asked? :P

I just realised... Bob in the sky with diamonds!

---

### Post by miscz on 2005-12-12
I tried using FreeBSD 5.4 on my desktop computer. All the hardware worked well, I think I had to configure manually my sound card (SB Live) but everything else worked out of the box. The installation is kinda weird IMO, you have to read a bit about BSDs before because even tough Linux and BSD are very similar there are some major differences like UFS2 (FBSD filesystem) being a bit like LVM, some names of devices are different. It's pretty straight forward after you do it once ;)
During the installation process you are asked which precompiled packages you would like to install, you can choose from Gnome, KDE and many others. Once you have it up and running you can install programs via ports (set of instructions to compile program from source), they are similar to Gentoo Portage but it's a bit less automagical :) You can also install binaries with pkgadd utility.
One thing that surprised me very much was FreeBSD's speed. It f***ing fast. The other nice thing is Linux compatibility layer. At the beggining you'll have to copy lots of libs from Linux (it was no big deal since I had installed on the same computer), then you run Linux binaries just as if they were native. I tried it with Quake 3 (nVidia releases their drivers for FBSD too!) and Stepmania, both worked faster than on Ubuntu!
The thing that was showstopper for me was the fact that even tough my dance mat was recognized, it didn't work with Linux programs. I can't live without Stepmania so I returned to Linux. I miss the speed of FreeBSD tough :\

---

### Post by LinuxSwede on 2005-12-13
[QUOTE=xequence]I am interested in BSD, and want to learn more about it.

Who here has used BSD before? Which have you used? Did the version (as in Net, Free, PC, etc) include a DE? Was it easy to install? How is hardware recignition? Is it easy to install programs? How stable is it? How does it differ from linux, how is it the same? Anything else I havnt asked? :P

I just realised... Bob in the sky with diamonds![/QUOTE]

I use and recommend OpenBSD for security critical tasks, in fact, it's the only OS i would use for security.

For desktop use, FreeBSD, the ports system is easy to handle and you'll find that what isn't already in the ports is easily accessible through the compatibility layer.

NetBSD is the choice for the more obscure platforms, the support for different types of platforms is incredible, haven't been using it much but it doesn't feel that different from the other two BSD distros.

The most interesting BSD flavor right now is DragonflyBSD, i'm going to install that on several machines this week to see what all the hype is about.

I think all of the flavors are fairly easy to install, all include a DE and the documentation is excellent.

---

### Post by -Rick- on 2005-12-13
I have NetBSD and FreeBSD.

FreeBSD's installation is quite easy. The installer also asks if you want to install binary packages, so you can have a full DE, some browsers and other stuff at the first boot. :)
NetBSD's installation was a bit harder, the text menu's where a bit less handy imo.
Just remember that BSD's need a primary partition and that their boot loaders aren't as fancy as grub(I recommend keeping grub if you already have that).

FreeBSD is my main OS. Its hardware support is progressing, for me atleast all my hardware is supported(CD and DVD burner, wired and wireless network, nvidia gfx card). FreeBSD can handle load much better than any other OS I tried(that is if you encode a movie you can just continue with other stuff without really noticing it). FreeBSD can install binary packages and compile them with the 'ports' system. With ports you have access to very much "Free" and "non-Free" software.

NetBSD is also a nice and clean OS, but IMO if you're not going to use it on some weird kind of hardware it doesn't really have something 'special'. I don't think you can get 3d on NetBSD. NetBSD can also install binaries as in the same way as FreeBSD('pkg_add'). And uses 'pkgsrc' to compile and install software. I didn't really liked it in comparisation with the ports system because it has far less things to install and doesn't have a proper way to upgrade your system. On the other hand its cool that you can use it on many other unix/linux systems too :)

Both BSD's can run linux binaries just fine(ut2004 runs atleast as fast as with ubuntu). There is also wine support, but doesn't work as good as on linux.

As for differences with linux...BSD has a different license, has its own 'base system' and is more unix like. Therefore most console apps differ slightly from the GNU ones. The default shell for root is the c shell(csh) and for any other users its plain sh. You can easily change to bash though.
Updating the base system can be a little bit harder, but the docs discuss this very well.

Always check the excellent documentation :) Especially FreeBSD has lots of docs for preperation, installation and things you can do after installation(burn a dvd for example).

---

### Post by DoeRayMe on 2005-12-13
I tried PC-BSD, its pretty good, you install programs in thier own directory, using .PBI files

[www.pbidir.com](www.pbidir.com) for info

Would still be on it but couldnt get eciadsl working ;)

---

### Post by xequence on 2005-12-13
> It f***ing fast.

That looks like a reason to try it =)

Maybe il delete windows and try freebsd.

---

### Post by Goddess_of_Linux on 2005-12-13
What do you all think about DesktopBSD, you can find it at [www.desktopbsd.net?](www.desktopbsd.net?)

What do you all think about Darwin-x86, you can find it here... [www.opendarwin.org?](www.opendarwin.org?)
- Note: Darwin is the same thing the Mac OSX runs on. They make a x86 and PPC version called OpenDarwin...

---

### Post by xequence on 2005-12-13
[QUOTE=Goddess_of_Linux]What do you all think about DesktopBSD, you can find it at [www.desktopbsd.net?](www.desktopbsd.net?)

What do you all think about Darwin-x86, you can find it here... [www.opendarwin.org?](www.opendarwin.org?)
- Note: Darwin is the same thing the Mac OSX runs on. They make a x86 and PPC version called OpenDarwin...[/QUOTE]

Ive heard darwin was really hard to install.

---

### Post by poofyhairguy on 2005-12-13
[QUOTE=Goddess_of_Linux]What do you all think about DesktopBSD, you can find it at [www.desktopbsd.net?](www.desktopbsd.net?)
[/QUOTE]

Sounds really cool. Competition is good, Linux could use some more on the Desktop.

---

### Post by majikstreet on 2005-12-13
[QUOTE=xequence]I just realised... Bob in the sky with diamonds![/QUOTE]
It's lucy in the sky with diamonds you gesundheit (had to look up how to spell gesundheit)

-m

---

### Post by benplaut on 2005-12-13
i want to try it once i have 2 systems, and thus can afford to have one down ;)

---

### Post by Goddess_of_Linux on 2005-12-13
How hard is it to install BSD... just curious...

---

### Post by xequence on 2005-12-13
[QUOTE=majikstreet]It's lucy in the sky with diamonds you gesundheit (had to look up how to spell gesundheit)

-m[/QUOTE]



Thats the point.

LSD = Lucy in the sky with diamonds
BSD = Bob in the sky with diamonds

---

### Post by LinuxSwede on 2005-12-13
[QUOTE=Goddess_of_Linux]How hard is it to install BSD... just curious...[/QUOTE]

That's like asking how hard it is to install Linux, there is not one answer to your question, it depends on the BSD flavor.

Personally i find Net and OpenBSD to be the easiest to install, it's fairly straightforward and the documentation is, like i said earlier, excellent. 

IOW, if you can read it's very easy. ;)

---

### Post by almahtar on 2005-12-14
[QUOTE=LinuxSwede]That's like asking how hard it is to install Linux, there is not one answer to your question, it depends on the BSD flavor.

Personally i find Net and OpenBSD to be the easiest to install, it's fairly straightforward and the documentation is, like i said earlier, excellent. 

IOW, if you can read it's very easy. ;)[/QUOTE]

Really? I had a much easier time with FreeBSD.  In general I have been very happy with BSD, especially when it comes to (as someone but I can't remember who, and I blame it on beer) load balancing.  FreeBSD did a great job of balancing cpu usage so you didn't notice lag if a process (like encoding a huge movie file, etc) was being really CPU intensive.

---

### Post by LinuxSwede on 2005-12-14
[QUOTE=almahtar]Really? I had a much easier time with FreeBSD.  In general I have been very happy with BSD, especially when it comes to (as someone but I can't remember who, and I blame it on beer) load balancing.  FreeBSD did a great job of balancing cpu usage so you didn't notice lag if a process (like encoding a huge movie file, etc) was being really CPU intensive.[/QUOTE]

I think this is individual and depends where you are coming from. 

No matter which one you decide to use i'd say it's wise to make preparations,  get to know the installation procedure through documentation and make a plan before you start installing. The documentation makes this very easy.

---

### Post by Gandalf on 2005-12-14
check this [Windows vs FreeBSD vs Linux](http://www.google.com//url?sa=t&ct=res&cd=4&url=http%3A//layerone.info/2005/presentations/BPotter-L1-05.ppt&ei=6NafQ8SkNrioQfjwrOUK&sig2=LjZ9JKbcXPYJvlM7MSbsww) :O Ubuntu classified most vulnerable :roll: DUH!!

---

### Post by majikstreet on 2005-12-14
[QUOTE=xequence]Thats the point.

LSD = Lucy in the sky with diamonds
BSD = Bob in the sky with diamonds[/QUOTE]
AHHHHHHHHHHHHHHH.... could be confused with LSD the drug..

---

### Post by xequence on 2005-12-14
[QUOTE=majikstreet]AHHHHHHHHHHHHHHH.... could be confused with LSD the drug..[/QUOTE]

Yea. The beatles were into drugs at the time they wrote Lucy in the sky with diamonds. Most people agree it is about LSD. (Read the lyircs, its so obvious ;))

---

### Post by majikstreet on 2005-12-14
[QUOTE=xequence]Yea. The beatles were into drugs at the time they wrote Lucy in the sky with diamonds. Most people agree it is about LSD. (Read the lyircs, its so obvious ;))[/QUOTE]
I know that :)

Btw, I am obsessed with classic rock.

It is a very druggy/high song..

---

