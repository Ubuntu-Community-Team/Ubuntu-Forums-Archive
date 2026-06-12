---
title: "I really want to switch, but..."
date: 2006-06-01
forum: Absolute Beginner Talk
---

### Post by cabcard on 2006-06-01
If you take the time to read this and help, thank you so much in advance.

So here's my situation. The main reason why I would like to switch to linux is for the freedom. However, I'm a college student and there are several things that I would still have to use Windows for. (Programming classes, I play online poker, etc..) Maybe there are alternatives for these that I do not know about.

One option is to dual boot and that's fine and dandy, but I would still not have my freedom, the whole reason for switching. I would have to keep my anti-virus up to date, deal with Windows update, and have spyware protection. That irks me as I want to switch, but just feel like I can't.

I want to be able to use Ubuntu only, it just doesn't seem like it can happen. Maybe I've answered my own question and I just can't. I'm looking to see if anyone as some helpful advice.

Also, I'm going to be purchasing a new computer within the next month, so maybe you guys could help me with a setup that would be best for dual booting. ($1500 or less is around what I'm wanting to spend)

Thanks for listening

---

### Post by IYY on 2006-06-01
You could try buying a computer with Ubuntu pre-installed (there are several online vendors that do this). Of course, to dual boot with XP you'll have to remove Ubuntu first, but installation will be very easy since all the hardware is known to be supported.

---

### Post by spin2cool on 2006-06-01
Dual booting is easy.  This is typically how I set up a new machine:

1) Grab a Linux LiveCD (the Ubuntu install disk doubles as one now!)

2) Resize your partitions as desired.  I usually do the following:
    - 10 GB windows (fat32)
    - 10 GB linux (ext3)
    - 1GB swap
    - remaining space data (fat32)

The reason for using fat32 is that it allows you to read and write to that space from linux, unlike ntfs.  Feel free to make your OS partitions a little bigger if you have plenty of space.  15Gb should be plenty.  (remember, all your documents/music/vids/etc will be stored on your data partition!)

3) Reinstall windows to the correct partition

4) install Ubuntu to the correct partition

If you use programs like Thunderbird, Firefox, and Gaim, you can set them up to store their info on your data partition, which means that you'll have the same experience in either OS.  

Both windows and linux will run easily on a large variety of hardware, so focus more on getting good hardware for your money.  It's unlikely that you'll find too many compatibility issues in desktops these days.

---

### Post by nalmeth on 2006-06-01
If the online poker software is flash or java based, you should still be able to use it. If it is a seperate program, it may make things tricky.
What kind of programming do you do? A lot of programming utilities exist for linux. I'm not a programmer myself, but I know they are out there. Look around.

I won't guarantee it, but wine may be of use to you. It's a Window's Compatibility Layer than run's some windows programs.

[http://www.winehq.com/](http://www.winehq.com/)

If you do have this money to spend, you can purchase CrossOver Office, which may run some of the more difficult window's program's in linux. Unless you can acquire it another way. Or a VMWare workstation might be attractive, you can run window's inside of linux, or the other way around.

---

### Post by aysiu on 2006-06-01
Get VMPlayer, and you can run Ubuntu on Windows or Windows on Ubuntu.

If you still want to do a dual-boot, read these two:
[http://www.psychocats.net/ubuntu/windowstoubuntu.html](http://www.psychocats.net/ubuntu/windowstoubuntu.html)
[http://www.psychocats.net/ubuntu/partitioning.html](http://www.psychocats.net/ubuntu/partitioning.html)

---

### Post by Jason_25 on 2006-06-01
As aysiu said, if you use vmware you can do anything you need.  My friend uses windows xp installed in vmware running on ubuntu and uses it to play bodog poker.  We could not get it installed in wine.

---

### Post by cabcard on 2006-06-01
@nalmeth, vb.net is the only language I use that I don't believe I can do in Ubuntu. Someone correct me if I'm wrong.

VMware sounds really interesting and may be just what I need.  Which way is better; install windows and get VMware for windows or install Ubuntu and get VMware for linux, or does it really matter.

Thanks so much everyone

---

### Post by unbuntu on 2006-06-02
[QUOTE=cabcard]@nalmeth, vb.net is the only language I use that I don't believe I can do in Ubuntu. Someone correct me if I'm wrong.

VMware sounds really interesting and may be just what I need.  Which way is better; install windows and get VMware for windows or install Ubuntu and get VMware for linux, or does it really matter.

Thanks so much everyone[/QUOTE]

Mono is ".NET for Linux"...but they're not 100% exactly the same.  
From what I see, running a VM would be a reasonable choice but with a compromise of performance.

---

### Post by uzi09 on 2006-06-02
[QUOTE=cabcard]If you take the time to read this and help, thank you so much in advance.

So here's my situation. The main reason why I would like to switch to linux is for the freedom. However, I'm a college student and there are several things that I would still have to use Windows for. (Programming classes, I play online poker, etc..) Maybe there are alternatives for these that I do not know about.

One option is to dual boot and that's fine and dandy, but I would still not have my freedom, the whole reason for switching. I would have to keep my anti-virus up to date, deal with Windows update, and have spyware protection. That irks me as I want to switch, but just feel like I can't.

I want to be able to use Ubuntu only, it just doesn't seem like it can happen. Maybe I've answered my own question and I just can't. I'm looking to see if anyone as some helpful advice.

Also, I'm going to be purchasing a new computer within the next month, so maybe you guys could help me with a setup that would be best for dual booting. ($1500 or less is around what I'm wanting to spend)

Thanks for listening[/QUOTE]


hey man, i know ***exactly*** what you're talking about! i had the same exact feelings.

imho, heres what you should do:

1...dual boot!
the reason why i say so is (i'm assuming) that you're a linux newbie. and you know what - newbies often run into problems. i did myself as well. if you have windows there in the background, you atleast have somethin to fall back on.

2...TRY IT!
the reason for this is, that i can pretty much bet you anything that you haven't *really* tried out linux. like you probably haven't tried to spend a few days straight on linux without touching windows (unless u absolutly had to, ex: couldn't get it to run, or were just switchin to play a game like CS, etc).
i thought that i'd be flippin back and forth too, but when i started to use it, except to get my internet up, i ended up not even touching windows! and the more i used it, the less and less i had to switch.
and if you're worried about "not totally free" -- in reality, no, we're aren't always. a lot of the more advanced users know enough to not have to rely on windows for things, but for us newbies, sometimes we just gotta. not only that, if you're only going to be using it that little, you don't really have to worry about getting all this spy ware and viruses. just try to make sure you limit your internet usage and you should be good.

---

### Post by wastern on 2006-06-02
talk to some professors about it

i know a lot of CS majors in college had to install SuSe linux for their programing class for C or C++ i think, the prof wanted them to program in a linux environment.  Ubuntu would work just as well

however if you have some MS partnership you'll probably have to do a lot of VB.Net as well, and in my case i was required to do things with MS Project, Visio and some other XP only apps, although i used some linux apps in place of Visio on a couple things


i think the poker should be OK, depending on the site you are on. load up a LiveCD and see if it works on the site you play (you might need plugins though in which case you'd have to instal to test

for a new computer you might want to look at a MacBook, you could Triple boot OS X, Windows, and Linux.  and 2 out of those 3 systems will let you have that freedom of no AV and countless patches every week

---

### Post by vidak on 2006-06-02
for online poker you could use the java based poker games.yahoo.com (this is just a suggestion, wasn't meant to be an ad :))

---

### Post by cromestant on 2006-06-03
I used to be like you, wanting, waiting, but still stuck with my xp for programming.Then I decided to try gentoo, ( used it for 3 years,). great distro, too much hasle though. So i switched to ubuntu dapper.
Now, if you are a CS student, ( as I am, in venezuela), I strongly recommend you give linux a chance, this is why :
-You have support for hundreds of languajes to program in. I personally program with C, C++, Java, Servlets, Jsp PHP, Asm, Lisp, Scheme, prolog, and the only ones i have to have windows for Asp, ASP.net, VB ( BTW they all suck...IMHO).
-CVS : This is really "la créme de la créme". Say you have a prog project, to do with a group. You install a cvs server, add your buddies to you computer ( creat accounts), and give them access to your cvs. Now, you can all program at the same time, and just by comiting updates to the cvs you can all use a centralized project repository... This and skype ( or akiga) speed up devlopment time, like you have no idea.
- Mysql and Postgresql : both great DBS that work perfeclty under linux and are FREE...
- ORCALE DB, incredibly, oracle runs faster on linux that it does on windows.
- GCC, great compiler for C++
- anjuta, or kdevelop : IDE for C and C++ both great ( comparable to VS.)
-Eclipse ( for java )
-multiple desktops ( or virtual desktops..) : Imagine this, you have your ide open on a desktop, your xmms running on the fourth, firefox open on the second(googling info to help you..), and your program tester on the third.
Now imagine the same scenario on windows, and see that your only desktop is so cluttered that you can't seem to find the exact thing that you are looking for...


Well that's just my two cents...

By the way, you probably won't be using VB all the time.. and if you have a choice, to learn something else... please do. VB is too limited, and really once you lear another programming languaje you'll find it hard to go back to VB.

Hope you can give linux a try... really I have not regreted it never.. ( btw I boot back on windows just to play CS 1.6 XD)

---

### Post by garner_nc on 2006-06-03
You could install Window$ through QEMU ([http://qemu.org)](http://qemu.org)). QEMU is similar to VMWare in that it allows you to run different operating systems through emulation on 1 PC. Probably not quite as clean as VMWare but if you only need 1 or 2 Window$ applications it may be a good FREE alternative for you.

   If you search the archives at [www.linuxjournal.com](www.linuxjournal.com) they did a story on how to set this up within the past 3 months.

All the Best,
Doug White

---

### Post by Rackerz on 2006-06-03
I'm using Dapper pretty much all the time now, but if ever I need to use Windows I just load it up on VMware, go full screen and it's like I'm back on my Windows partition again.

---

