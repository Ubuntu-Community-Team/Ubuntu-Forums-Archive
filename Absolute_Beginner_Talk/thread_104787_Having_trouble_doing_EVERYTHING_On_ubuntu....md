---
title: "Having trouble doing EVERYTHING On ubuntu..."
date: 2005-12-16
forum: Absolute Beginner Talk
---

### Post by Dann7391 on 2005-12-16
Basically I need the run down on Ubuntu. I am having troubles with everything even installing something as simple as AMSN.

I want to install WINE, as I want to be able to play games such as F.E.A.R or WoW on the ubuntu PC.

My system specs are here:
athlon 64 3000+
2x512 geil ddr400 ram
80gb samsung spinpoint p sata150 hd (i have a 250gb seagate but its unplugged as all my media from having windows is on there)
nvidia geforce 6800le.
running ubuntu 5.04 (dont wanna upgrade)
I have had some experience with linux before, mainly gentoo only because of portage :)

but anyway if anyone can help i will be greatly thankful.

---

### Post by ninotob on 2005-12-16
You really have to be more specific.  Can you browse?  Email?  Ok, games are an issue on linux and if you're a hardcore gamer, you might want to consider dual booting.  It's been my experience that everything about wine is hard.  But if you need help w/ a specific game, your best bet is probably google, e.g. "[wine wow linux](http://www.google.com/search?hs=9fQ&hl=en&lr=&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&q=wine+wow+linux&btnG=Search)"

---

### Post by Dann7391 on 2005-12-16
obviously i can browser as im posting this. but thats because firefox was already installed :)

well gaming....hmm dont wanna dual boot as ive done it in the past and really couldnt care less for it.

can anyone help me install skype btw?
[http://www.skype.com/products/skype/linux/](http://www.skype.com/products/skype/linux/)

---

### Post by kwaanens on 2005-12-16
Skype:

Add this:
```
deb http://public.planetmirror.com/pub/plf/ubuntu/plf/ breezy free non-free
```
in /etc/apt/sources.list

Then:
sudo apt-get update
then
sudo apt-get install skype

Or run Synaptic to install it.

-Ketil

---

### Post by Dann7391 on 2005-12-16
sigh...i forgot to emphasize on how big a n00b i am...

do you have aim or msn or something where we can get in more detail?

---

### Post by d1337 on 2005-12-16
Dual booting is cake.  If you feel that you are too much of a noob to add a source in /etc/apt/sources.list you're gonna be lost in either wine or Cedega to get games going.  I would also strongly recommend dual booting if gaming is your thing.  But that's just my opinion.

d1337

---

### Post by Mustard on 2005-12-16
[QUOTE=Dann7391]sigh...i forgot to emphasize on how big a n00b i am...

do you have aim or msn or something where we can get in more detail?[/QUOTE]

Gaim is already installed by default and allows you to connect using your MSN login.  It doesn't have all the functionality of MSN proper, but you can chat and see your buddies online.  It works for AIM too and more.  Its got all the common messengers in one interface.

---

### Post by ninotob on 2005-12-16
[QUOTE=d1337]Dual booting is cake.  If you feel that you are too much of a noob to add a source in /etc/apt/sources.list you're gonna be lost in either wine or Cedega to get games going.  I would also strongly recommend dual booting if gaming is your thing.  But that's just my opinion.

d1337[/QUOTE]

I'll second the dual booting (redundant I know but let me expand).  It seems to me that for gamers, there only a few non-perfect options, from easiest to hardest:

1.  Consoles.
2.  Dedicated wintendo machine.
3.  Dual booting.
4.  Wine or Cedega (non-free).  

I've never used Cedega but I've tried wine at various times and it's a really hard trip.  The difficulty in going from #3 above to #4 isn't a single step.  It's like this:

easiest <--1-2-3-----------------------------------4--> hardest

Anyway, I burnt out on video games about a decade ago, so linux does all I could ever want.  But if you are a gamer, and really want to use linux, there are no perfect solutions.

---

### Post by Estariel on 2005-12-16
Hi!

I'm sure you know, but let me nevertheless point out that you cannot run windows programs on linux, other than using wine (or cedega).

In most cases, using wine is not a very clean solution, things won't run smoothly and will be rather unstable.

So don't do this if you cannot somehow avoid it. Linux is not meant to run windows programs. You can find a Linux program that is equivalent or better to most windows programs.

For example, for instant messaging just use GAIM - it can hook up to almost all instant messaging protocols.

Using cedega (a non free version of wine that has been modified to better support directx) for your games is fairly easy.

Buy cedega ([www.transgaming.com)](www.transgaming.com)).
Download the .deb file.
Install it. (Open a terminal, move to the directory in which the .deb is, and type "dpkg -i filename.deb")
Start Cedega. (Select it from the applications menu, or type "cedega" in a terminal. 
A nice graphical interface will appear. Put your Game CD into your PC. Hit the install button in cedega. Install the game...

---

### Post by Dann7391 on 2005-12-16
d1337 helped me over AIM but my plan was to install windows and then dual boot using grub, i would say yes to adding grub to the master boot record...and then whenever i would start up it would say error loading operating system.

so i just said screw it and installed XP...maybe ill try it in a while...

---

### Post by Fibre on 2005-12-17
I'm a noobie to Ubuntu or any other linux for that matter. But I do know a bit about XP and when I had problems on my first install of Ubuntu trying to set up dual boot through Ubuntu before installing it and finally stuffing up my XP Partition lol.

I just inserted XP and made a partition on my hard drive for XP - installed XP on it and then made 2 partitions on the free space remaining with ubuntu - made one Fat32 and then put Ubuntu on the other. So the theory was to use the FAT32 with both O/S and if I get in trouble XP is there to fall back on.

I still want to be able to play games from Ubuntu though as well and I'm stumped and getting nowhere fast LOL.

Good Luck with the whole thing I to had a lot of frustrating moments with the installation but when it goes it goes OK.

few minor issue's to kill.

---

### Post by Dann7391 on 2005-12-17
SUCCESS! I tried it one more time and made a bootdisk incase I had to clear the MBR....this time it worked perfectly yet the only thing I did different was leave 10gb free space....so Anyway...if anyone wants to get on AIM or MSN and talk to me through installing some apps...please IM me.

AIM -Dann7391
MSN - [email]computergen7@hotmail.com[/email]

---

### Post by Bartender on 2005-12-17
That's the spirit, Dann -
Your thread starts with frustration and wraps up with your offer to go the extra mile helping others.  Good job.

Group hug ;)

---

