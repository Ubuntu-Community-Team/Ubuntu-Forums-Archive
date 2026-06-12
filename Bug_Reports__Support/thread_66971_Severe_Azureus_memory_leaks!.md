---
title: "Severe Azureus memory leaks!"
date: 2005-09-19
forum: Bug Reports / Support
---

### Post by meldroc on 2005-09-19
For some reason, when I use Azureus, I get a very serious memory leak.  I mean I'm running one full gigabyte of RAM, plus a 2GB swap partition, and if I let Azureus run long enough, it'll use it ALL.

If I use ps or top, it shows the memory being consumed not by Azureus itself, but by the X server.  But it only happens when I run Azureus.  I'm thinking either Azureus, or various Java libraries & runtimes are invoking X API calls that use memory, but don't go back and tell X to release its resources.

Does anyone know how to fix this?

---

### Post by jdong on 2005-09-19
Azureus does have severe memory draining issues.

---

### Post by cosimo on 2005-10-21
Hello,
 After much testing on different systems we have come to the realization that azureus indeed uses an excess of memory and swap file just by running the application. Left to run it does increase it's useage of, particularly, swap file.This is again just runing the app NOT using it in anyway.
 So fella, the one that wrote it has no issues, your incorrect off base
 thanks
 Coz

---

### Post by Darrena on 2005-10-22
Azureus is a memory hog, but it shouldn't be that bad.

Couple of things to try:
1) Which version of Java are you running?  From a terminal type Java -version   If it is less than 1.5 there was a problem with that version and Azureus which resulted in higher memory utilization
2) Check the FAQ on the Azureus site, it has some tips on reducing memory consumption.
2) Try Rufus, it is a lighter BT client.

---

### Post by GeneralZod on 2005-10-23
I've had severe issues with Azureus, but the really weird thing is that it seems to be X memory it's taking up - xrestop was listing Azureus as using several hundred megabytes of X-server memory.  Very odd indeed.

---

### Post by psusi on 2005-11-07
From what I have seen, Azureus, like every other app written in java, is a slow, klunkey beast of a pig.  

I recommend bit tornado instead, and stay clear of anything to do with java.

---

### Post by strikeforce on 2005-11-07
Ok personal plug.

I recommend [Rufus]("http://www.ubuntuforums.org/showthread.php?t=57590")

There is a thread included plus some deb's for you to install.  Just install the dependancies :)

Personal plug over

If you want a less memory hog program try any python based bittorrent client.  Generally they don't use nearly as much resources as what Azureus does.

---

### Post by The Warlock on 2005-11-07
I like Azureus, though. It's what I'm used to; it's the program I run under Windows, etc. Why is this screwing up? Is it a java issue? Would using Sun's java be better than using Blackdown's java?

---

### Post by Darrena on 2005-11-11
[QUOTE=The Warlock]I like Azureus, though. It's what I'm used to; it's the program I run under Windows, etc. Why is this screwing up? Is it a java issue? Would using Sun's java be better than using Blackdown's java?[/QUOTE]

YES!  Blackdown is still at 1.42 which had some serious issues with Azureus look in the Howto/customization forum for instructions on rolling your own Java 1.5 package.

---

### Post by liontooth on 2005-11-24
I can confirm a severe Azureus memory leak, also with version 2.3.0.5 B70. Xorg memory usage goes up like clockwork until 75% of memory is used; then that is held steady while the swap is used; when that is exhausted, the application crashes.

I get this on Debian too; the problem is clearly Azureus, but perhaps xorg could resist what it's doing?

Dave

---

### Post by GothicX on 2005-11-24
I confirm the same bug (crash sometimes).. and please update to kernel 2.6.14 =)

---

### Post by GothicX on 2005-11-25
Can't kill some java process, and my azureus is crashing so much times.. I'm using latest version " sun-j2re1.5_1.5.0+update05_i386.deb ".

Fixed on new kernel. please update to 2.6.14 =)

[http://www.ussg.iu.edu/hypermail/linux/kernel/0504.3/0849.html](http://www.ussg.iu.edu/hypermail/linux/kernel/0504.3/0849.html)

Thanks!

---

### Post by jdong on 2005-11-25
the posted patch is for x86_64 platforms only ([http://www.ussg.iu.edu/hypermail/linux/kernel/0504.3/0886.html](http://www.ussg.iu.edu/hypermail/linux/kernel/0504.3/0886.html))

Are you using an AMD64 with Ubuntu AMD64?

---

### Post by GothicX on 2005-11-27
No, I'm using an AMD Athlon XP (with latest kernel -k7) and I've problems to kill sometimes.. today is "wish", not java.. :-(

I tested with root too, doesn't work! :(

kmos@bash:~$ ps xua |grep wish
kmos      8423  6.9  2.8  42416 29204 ?        R    15:38  11:53 wish /home/kmos/amsn/amsn
kmos     10212  0.0  0.0   2988   604 pts/2    R+   18:28   0:00 grep wish
kmos@bash:~$ killall -9 wish

kmos@bash:~$ ps xua |grep wish
kmos      8423  7.0  2.8  42416 29204 ?        R    15:38  11:59 wish /home/kmos/amsn/amsn
kmos     10216  0.0  0.0   2988   596 pts/2    R+   18:28   0:00 grep wish

*****

root@kmos:/home/kmos# ps xua |grep wish
kmos      8423 11.7  2.8  42416 29204 ?        R    15:38  21:11 wish /home/kmos/amsn/amsn
root@kmos:/home/kmos# killall -9 wish
root@kmos:/home/kmos# ps xua |grep wish
kmos      8423 11.8  2.8  42416 29204 ?        R    15:38  21:25 wish /home/kmos/amsn/amsn
root     10336  0.0  0.0   2984   596 pts/2    R+   18:38   0:00 grep wish
root@kmos:/home/kmos# 

***

kmos@bash:~$ ps xua |grep azureus
kmos      8430  0.0  0.1   4396  1652 ?        S    19:45   0:00 /bin/bash /home/kmos/azureus/azureus
kmos      8451 65.1  6.4 382872 66416 ?        R    19:45   5:14 java -Xms16m -Xmx128m -cp /home/kmos/azureus/Azureus2.jar:/home/kmos/azureus/swt.jar:/home/kmos/azureus/swt-mozilla.jar:/home/kmos/azureus/swt-pi.jar -Djava.library.path=/home/kmos/azureus -Dazureus.install.path=/home/kmos/azureus org.gudy.azureus2.ui.swt.Main
kmos      8599  0.0  0.0   2988   604 pts/2    R+   19:53   0:00 grep azureus
kmos@bash:~$ killall -9 java

kmos@bash:~$ ps xua |grep azureus
kmos      8430  0.0  0.1   4396  1652 ?        S    19:45   0:00 /bin/bash /home/kmos/azureus/azureus
kmos      8451 65.8  6.4 382872 66416 ?        R    19:45   5:24 java -Xms16m -Xmx128m -cp /home/kmos/azureus/Azureus2.jar:/home/kmos/azureus/swt.jar:/home/kmos/azureus/swt-mozilla.jar:/home/kmos/azureus/swt-pi.jar -Djava.library.path=/home/kmos/azureus -Dazureus.install.path=/home/kmos/azureus org.gudy.azureus2.ui.swt.Main
kmos      8602  0.0  0.0   2984   604 pts/2    S+   19:54   0:00 grep azureus
kmos@bash:~$ 

You see? =)

---

### Post by dodongo on 2005-11-27
In which Backports repository is Azureus located?  I can't see it.

---

### Post by jdong on 2005-11-27
None; I want to see the PLF import this into their repositories... That's the most appropriate place for now, and when Ubuntu Dapper gets GCC  4.1, we may finally have native Free Azureus!

For now, installing the .deb from packages.debian.org works well, since Java is Java is Java.

---

### Post by GothicX on 2005-11-27
How about to fix the problem about kill some processes with AMD Athlon XP ?! kernel 2.6.14 is the best thing to do.. and dapper will have 2.6.15, or a better one, because it's only in april...

---

### Post by jdong on 2005-11-27
Umm, the patch you linked to only affects AMD64... I'm not so sure a newer kernel would fix your  problem.

Try compiling your own kernel, or using ubp-build.py to backport linux-image-2.6.15 and linux-restricted-modules-2.6.15, and see if that works any better.


I cannot officially backport kernels, that's a very dumb decision... I made that mistake back in the Warty days.

---

### Post by GothicX on 2005-11-27
I've a recent kernel 2.6.14 in fedora core 4, and I don't have these problems.. so it can only be something about the kernel, and that AMD64 problem is suspicious don't you think ?!

I'm getting boring of that, can't kill a process is strange and only with a reboot I can fix it! :-(

Maybe I'll try 2.6.15 when I've time for it...

---

### Post by jdong on 2005-11-27
well, each distro's kernel is patched to varying degrees... Fedora/Redhat kernels are very heavily patched, so you can't judge just by the vanilla version...

---

### Post by GothicX on 2005-11-27
Exactly.. but it doesn't happen at FC4, the distro I used before... There I can kill anything. I like very much Ubuntu, but maybe these bugs must be analyzed by the team. Let's see if someone else have these problems.. I really don't know any solution without change my kernel version..

Another question.. dapper will have a new init system !? like initg, to boot faster..!?

---

### Post by jdong on 2005-11-27
First try the 686 and 386 kernels... that could do it on some odd systems


As far as initng, i don't know... ask some developers...

---

### Post by GothicX on 2005-11-28
[QUOTE=liontooth]I can confirm a severe Azureus memory leak, also with version 2.3.0.5 B70. Xorg memory usage goes up like clockwork until 75% of memory is used; then that is held steady while the swap is used; when that is exhausted, the application crashes.

I get this on Debian too; the problem is clearly Azureus, but perhaps xorg could resist what it's doing?

Dave[/QUOTE]

It's like that you describe here :-)

---

### Post by macleod199 on 2005-11-29
[QUOTE=jdong]None; I want to see the PLF import this into their repositories... That's the most appropriate place for now, and when Ubuntu Dapper gets GCC  4.1, we may finally have native Free Azureus!

For now, installing the .deb from packages.debian.org works well, since Java is Java is Java.[/QUOTE]

Oh man, I never even thought to look at the official debian repositories for it. Awesome, thank you.

---

### Post by macleod199 on 2005-11-29
[QUOTE=jdong]None; I want to see the PLF import this into their repositories... That's the most appropriate place for now, and when Ubuntu Dapper gets GCC  4.1, we may finally have native Free Azureus!

For now, installing the .deb from packages.debian.org works well, since Java is Java is Java.[/QUOTE]

Oh man, I never even thought to look at the official debian repositories for it. Awesome, thank you.

---

### Post by dodongo on 2005-11-29
Evidently I'm a total old fart.  I'm just running it off source.  :)

---

### Post by GothicX on 2005-12-13
I've updated j2re to the last version (update 06) and now azureus doesn't crash =) maybe it's fine now.. try to update to the last version.

---

### Post by cowlip on 2005-12-29
This problem seems to have appeared for me one Dapper in an insane way.  I've had to increase my swap file from what used to be 370mb to over 1 gb, because of Azureus swap usage.

(I am looking for another bittorrent client)

---

### Post by dodongo on 2005-12-29
[QUOTE=cowlip](I am looking for another bittorrent client)[/QUOTE]

You can find it [here]("http://pingpong-abc.sourceforge.net/").*

Seriously, though, have you, by any chance, attempted to install Sun's JRE 1.5?  I can't tolerate working with the other JRE systems in use with Ubuntu, so I gutted them and moved to Sun.  It's possible that the interpreter you're using is at fault, and not speciifcally Azureus.  Do you know if you use any other Java-based programs?  Do they result in similar memory leaks?

---

### Post by cowlip on 2005-12-29
Hey, yes I am using Sun's jre 1.5-6.  I don't use any other java programs so I'm sorry not to be of help there...

---

### Post by dodongo on 2005-12-29
[QUOTE=cowlip]Hey, yes I am using Sun's jre 1.5-6.  I don't use any other java programs so I'm sorry not to be of help there...[/QUOTE]

I'm not sure what to suggest, then.  Anyone else?

---

### Post by cowlip on 2005-12-29
Hey dodongo thanks for the link of ABC.  I downloaded hte latest win32 source version and followed this post: [http://sourceforge.net/forum/forum.php?thread_id=1410799&forum_id=399114](http://sourceforge.net/forum/forum.php?thread_id=1410799&forum_id=399114)

and it worked great.

EDIT: Actually it turns out going back to breezy solved this...I think Dapper's xorg has a swap bug for radeons

---

### Post by ijanos on 2006-01-15
[QUOTE=meldroc]If I use ps or top, it shows the memory being consumed not by Azureus itself, but by the X server.  But it only happens when I run Azureus.  I'm thinking either Azureus, or various Java libraries & runtimes are invoking X API calls that use memory, but don't go back and tell X to release its resources.[/QUOTE]

I got EXACTLY the same problem since I reinstalled my ubuntu [size=1](NEVER try to force up a debian like but not debian package on your system!)[/size] my prevoius system  had the same packages but now the azureus eats my memory. All of it.

---

### Post by coulix on 2006-02-11
Hi, same pb here on hoary 2.6.10, i tried the last jre 1.5-6 still crash after a while (the hd start swapping so bad the system becomes unusable and i have to wait fot azureus to crash).
will tempt an update to breezy with hope :/
The only thing i want is a bittorent client which would run on a server, with or without graphical interface and an acces via web, any hope ?

---

### Post by ijanos on 2006-02-14
[QUOTE=coulix]The only thing i want is a bittorent client which would run on a server, with or without graphical interface and an acces via web, any hope ?[/QUOTE]

MLdonkey

---

### Post by apollo2011 on 2006-03-23
I am having this problem on Kubuntu 5.10, I upgraded Java to JRE 1.5-update6. Unfortunately, this doesn't seem to have fixed my problem. When I run Azureus in Konsole, it shows that it found the new version of JRE, but X persists to slowly eat up my memory in my RAM and swap until there isn't any left.
](*,)

---

### Post by GothicX on 2006-03-23
[QUOTE=apollo2011]I am having this problem on Kubuntu 5.10, I upgraded Java to JRE 1.5-update6. Unfortunately, this doesn't seem to have fixed my problem. When I run Azureus in Konsole, it shows that it found the new version of JRE, but X persists to slowly eat up my memory in my RAM and swap until there isn't any left.
](*,)[/QUOTE]


Try to update to Ubuntu Dapper Drake =) It will fix some of your problems...

---

### Post by apollo2011 on 2006-04-01
[QUOTE=GothicX]Try to update to Ubuntu Dapper Drake =) It will fix some of your problems...[/QUOTE]
I upgraded to Dapper, and after fixing some minor problems, ran Azureus, and still had the memory leak...

---

