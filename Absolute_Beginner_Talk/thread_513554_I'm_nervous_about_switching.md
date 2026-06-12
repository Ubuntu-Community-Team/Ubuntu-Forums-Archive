---
title: "I'm nervous about switching"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by pilate on 2007-07-30
I want to switch. At least I think I do. I'm a computer science major, and it's always seemed like I was the odd man out still on my Windows machine. But I'm so comfortable there. I know how to use it, install stuff, and I even know a little bit of fancyness like ipconfig and my favorite telnet(don't know what I use it for, but I like knowing it exists). 
Now I've tried switching once or twice. Maybe three times. Onces with some live cd I can't remember, then Ubuntu live cd, then Ubuntu on a left over box. All three times I eventually gave up. For various reason. Sure I could get my email, and check the web, but what about when I want to install a vnc server and can't find the solution? I just wasn't willing to read 50 forum posts of conflicting solutions, only to find out at the end that every thing I read didn't apply to the most current version.
So I went back to the teet that is windows and sucked the sour milk again and again.
Until right now. I think I'm ready to make the jump. I just don't know which way I should jump. So I need some help.

First let me tell you what I need to do in the end. Bullet points style. I'm not asking for a solution to each individual problem, and I'm not looking for replacement programs. I'm just giving you a general idea what the box has to do.
*Have wireless internet (I'll get to my machine in a bit)
*Print to HP Laserjet printers, that may or may not be connected to a windows box
*Share files to and from a windows box
*Program. Mostly Java, C++, PHP, MySQL
* Watch videos. Like, all of them. Divx, dvd, avi, mov, and just about anything else
*Download podcasts and sync my ipod. 
*Open pdf's
*Run adobe cs3. (I know about gimp. but I need my photoshop)

So here are my options for before I switch. I currently have a Dell Inspiron 1501 with Windows Xp. I have to reformat (which is why I want to switch) because windows doesn't like wired connections, and it's just generally buggy after only 2 months. I have the option to return this laptop (which I kinda want to do, because I've already had to replace the hard drive and the motherboard), or keep it and just reformat.
If I return it, should I get a Dell laptop with Ubuntu already installed? I'm leaning towards the 1420 N, or find a laptop I like with Windows and install Ubuntu.
Finally, since I need to be able to run a windows app (cs3, and just would like to have it in general), which way should I go about it? Buy a Windows box, and add Ubuntu? Buy a Ubuntu box and dual boot with Windows? Run Wine in Ubuntu? Install Ubuntu with Wubi?

Sorry for the huge post, but hopefully you were able to make it through it. I appreciate any guidance you can give me as I make the bone chilling departure from the familiar to the unknown.

---

### Post by rich.bradshaw on 2007-07-30
I do all you mention except java. Linux won't run CS3, but you can run Windows in a virtual machine to do that.

Wireless works fine, buying Dell will ensure it works. (some chipsets aren't well supported)

HP release drivers for Linux. Easy.

Samba is for sharing with Windows

Programming is easy.

Codecs for video are in restricted-extras

iPod works out of box

pdf is open format anyway, so it works out the box

CS3 run in Windows using Vmware


Wubi is easy. No hibernate/suspend though.

Buy Dell+linux for easiness if you want, it's easy to install though!

Good luck!

---

### Post by compiledkernel on 2007-07-30
cs2 runs in wine relatively easy. 

[http://luiscosio.com/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps](http://luiscosio.com/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps)

Other than that, all your other stuff should work out of the box.

---

### Post by pilate on 2007-07-31
Thanks guys. So the next question is, do I stay with my 1501 since it's been known to work with Ubuntu, or do I get a new Vostro 1500?

---

### Post by medley on 2007-07-31
> **pilate said:**
> Thanks guys. So the next question is, do I stay with my 1501 since it's been known to work with Ubuntu, or do I get a new Vostro 1500?

I'm typing this on a Dell M1210 that I set up as a dual boot with XP and Kubuntu 6.10. I was pleasantly surprised to discover by running the Live CD that everything worked perfectly, including the wireless card. The only driver I had to install was for my NVidia 7400 Go, and that was only to take advantage of 3d acceleration. And this was easy with the 'envy' script.

I generally use Kubuntu for most things and I also have Beryl running, which is just sweet. I find the 3d desktop cube infinitely useful and find myself intuitively trying to rotate to a free desktop when I'm using one of my XP machines. I also run Kubuntu on two other machines, one set up primarily for audio recording.

Setting up a dual boot is child's play with (K)Ubuntu because it detects another OS when you opt to install it, and offers to set up a dual boot for you.

I understand the nervousness; if you want to play it safe, and also need CS3, which apparently doesn't work under Wine, dual boot may be a good compromise for you. I find that the performance of apps under VMware run a bit slower than in the native OS.

At any rate, I'd try the Live CD first to see if your hardware works OK, then make a decision. If your wireless works right away, that's half the battle. On one system I had to wrestle with that one for a few days.

Good luck. I think you'll be pleasantly surprised if you opt to move toward Ubuntu or any of the other user-friendly distros (I hear Fedora is quite good these days too).

Cheers

Phil

---

### Post by pilate on 2007-08-03
So there is something I've been wondering about. If I dual boot Ubuntu and XP, whats the process of getting files between the two? Do I need to have my drive formatted in a specific way?

---

### Post by Rocket2DMn on 2007-08-03
Both systems can read/write FAT32 out of the box.
Linux can read/write NTFS file systems if you install ntfs-3g and enable writing by going to Applications->System Tools->NTFS Configuration Tool
Windows can read/write ext2/3 file systems using the driver from [http://www.fs-driver.org](http://www.fs-driver.org) but it mounts your ext3 as an ext2, so problems CAN arise, but I'm not sure how likely that is.

Using these allows you to keep your current partitions so you can access all partitions from both OSes.

Always keep good backups.

---

### Post by n.aggel on 2007-08-03
go ahead man...most of the things you said ubuntu does out of the box...also if you are a computer science major it will be nice to have an experience with a unix-like os!

---

### Post by jdrodrig on 2007-08-03
> **pilate said:**
> 
 I have the option to return this laptop (which I kinda want to do, because I've already had to replace the hard drive and the motherboard), or keep it and just reformat.

So what is left from the original machine, the screen? LOL!

I do not see any benefit from keeping such computer. Just return it and get a new one (even if it is the same configuration)

d.

---

### Post by dca on 2007-08-03
Hey, it's not like you're going down to get a Tetanus shot...
 
Go for it!

---

### Post by pilate on 2007-08-03
> **n.aggel said:**
> also if you are a computer science major it will be nice to have an experience with a unix-like os!
Ya I know. I'm just too lazy to learn! Atleast until now. I'm downloading both Ubuntu and Kubuntu to see which one I like better.
And I guess I'll just put windows on its own partition, ubuntu on its own partition, then have a fat32 partition where I save all my files. Any reason that's a bad idea?

---

### Post by ericesque on 2007-08-03
I second the motion to get rid of the troubled notebook.  There is no sense in keeping something that is known to be broken.   Besides, since you're having trouble after 2 months, it's likely more hardware issues on the verge of erupting. 

I've had issues with ext drivers for XP.  I'm using the NTFS driver for ubuntu and Samba.  It works well.

It looks like you'd be in good shape if those are your requirements.  Synaptic is great for installing software, but get to know and use Add/Remove...  it has helped me find all kinds of software.  Also, don't forget that there are sites like [www.gnomefiles.org](www.gnomefiles.org)  which house information on even more software that may be just the ticket for you.

---

### Post by ericesque on 2007-08-03
Isn't  fat32 going to come with the 4GB filesize limit?  Might be a pain if you have DVD or game .iso to store.  Trust me on the NTFS driver and Samba.  Just make that partition a network shared drive.

---

### Post by pilate on 2007-08-03
Ok NTFS it is. But you confused me. Why do I need to make it a network shared drive if it's in the same machine?

---

### Post by ericesque on 2007-08-04
#-o  haha.  you don't.   I was thinking of my setup -- Ubuntu in a VM on XP.

---

### Post by rockin_goliath on 2007-08-04
Dude, I was in the exact same situation last November that you are in now. What it took for me was really nice people on the forums, Ubuntu, and A LOT OF PATIENCE. Try and find a buddy in the computer science department (or maybe even a professor, score some brownie points) to sit down with you and explain some stuff to you, like the command line. Pretty much everything in your list will work without too much hassle. I use Automatix to install audio and video codecs, and also dual boot with Windows and Ubuntu (although I haven't actually booted into Windows in about 3 months). Ubuntu can read NTFS drives out of the box, but cannot write to them without NTFS-3g. I have successfully gotten my nVidia card working pretty easilly using the restricted drivers manager and nVidia's x.org config GUI (type in the terminal "sudo nvidia-configure" i believe, which comes with the driver). Don't be afraid! Have fun and learn a lot!

---

### Post by Brunellus on 2007-08-04
> **pilate said:**
> Ya I know. I'm just too lazy to learn! Atleast until now. I'm downloading both Ubuntu and Kubuntu to see which one I like better.
And I guess I'll just put windows on its own partition, ubuntu on its own partition, then have a fat32 partition where I save all my files. Any reason that's a bad idea?
if you're too lazy to learn, then don't bother trying a new operating system.

You need to go in with the right mentality.  A new OS is like learning a new language, or moving to a foreign country.  If you are willing to operate somewhat outside of your comfort zone, you will ifnd that you learn many valuable lessons.  Some of those lessons will come in handy in other parts of your life.

But if you come in with the attitude that your new home should be *exactly* the same as your old home, and that any difference, no matter how trivial or superficial, is evidence of the manifest inferiority of your new environment to the old one, well, you're going to abandon the effort very quickly.

Given your use profile, you are likely going to be fine switching to Ubuntu--EXCEPT for Photoshop.  You can use CS2 through WINE or Crossover Office, but you cannot--as yet-- use CS3 in Linux.  

If that's a total deal-breaker, then dual-boot or don't migrate at all.

If you depend on a lot of proprietary software, don't migrate.  If you depend on DRMed media--don't migrate.  If you or your colleagues require obscure and difficult features in certain proprietary packages--don't migrate.

But if you're looking for something to learn, migrate.

---

### Post by belikralj on 2007-08-04
Well said :)

---

### Post by pilate on 2007-08-11
> **Brunellus said:**
> if you're too lazy to learn, then don't bother trying a new operating system.


Thanks. I was too lazy. But like I said in that post you quoted, I'm not any longer. I'm tried of dealing with windows all the time.
So I finally got my new laptop. A Vostro 1500 (freakin sweet btw). And I'm wondering, since I have a Core 2 duo, do I want the 64 bit version of ubuntu or do I want the 32bit? At least in my windows world I know that some programs and drivers won't run on the 64bit os. And I don't need to do anything(yet atleast) that really "requires" 64bit processing. Or is the linux world different and applications and drivers have no problem in either os?

---

### Post by Paul133 on 2007-08-11
32-bit. Do not ge tthe 64 bit. I'm running an Inspiron 1501 (just like you) with dual core 64-bit processor, and I still use 32-bit Ubuntu. Why? Because 64-bit Ubuntu is just nowhere near as good as 32-bit. Good luck with Ubuntu. And we'll eb here on the forums to help you out.

---

### Post by jfinkels on 2007-08-11
> **pilate said:**
> I want to switch. At least I think I do. I'm a computer science major, and it's always seemed like I was the odd man out still on my Windows machine. But I'm so comfortable there. I know how to use it, install stuff, and I even know a little bit of fancyness like ipconfig and my favorite telnet(don't know what I use it for, but I like knowing it exists). 
Now I've tried switching once or twice. Maybe three times. Onces with some live cd I can't remember, then Ubuntu live cd, then Ubuntu on a left over box. All three times I eventually gave up. For various reason. Sure I could get my email, and check the web, but what about when I want to install a vnc server and can't find the solution? I just wasn't willing to read 50 forum posts of conflicting solutions, only to find out at the end that every thing I read didn't apply to the most current version.
So I went back to the teet that is windows and sucked the sour milk again and again.
Until right now. I think I'm ready to make the jump. I just don't know which way I should jump. So I need some help.

First let me tell you what I need to do in the end. Bullet points style. I'm not asking for a solution to each individual problem, and I'm not looking for replacement programs. I'm just giving you a general idea what the box has to do.
*Have wireless internet (I'll get to my machine in a bit)
*Print to HP Laserjet printers, that may or may not be connected to a windows box
*Share files to and from a windows box
*Program. Mostly Java, C++, PHP, MySQL
* Watch videos. Like, all of them. Divx, dvd, avi, mov, and just about anything else
*Download podcasts and sync my ipod. 
*Open pdf's
*Run adobe cs3. (I know about gimp. but I need my photoshop)

So here are my options for before I switch. I currently have a Dell Inspiron 1501 with Windows Xp. I have to reformat (which is why I want to switch) because windows doesn't like wired connections, and it's just generally buggy after only 2 months. I have the option to return this laptop (which I kinda want to do, because I've already had to replace the hard drive and the motherboard), or keep it and just reformat.
If I return it, should I get a Dell laptop with Ubuntu already installed? I'm leaning towards the 1420 N, or find a laptop I like with Windows and install Ubuntu.
Finally, since I need to be able to run a windows app (cs3, and just would like to have it in general), which way should I go about it? Buy a Windows box, and add Ubuntu? Buy a Ubuntu box and dual boot with Windows? Run Wine in Ubuntu? Install Ubuntu with Wubi?

Sorry for the huge post, but hopefully you were able to make it through it. I appreciate any guidance you can give me as I make the bone chilling departure from the familiar to the unknown.

It's really up to you on whether you want to get a new laptop with Ubuntu pre-installed or install it yourself. Before installing it yourself, you may want to search around and see if anyone has had any problems with that particular model laptop.

Most wireless cards will work, though some may require installing a driver first. You will have to just test it out and see (again, search around to see if other people have had problems with your particular model of wireless card).

The 'samba' system allows you to communicate with Windows computers for file and printer sharing. It is fairly easy to install. Some printers do not have drivers for Linux (e.g. Dell All-In-One printers). Again, search around for your particular model (or just try it out).

Programming is a million times easier with *nix systems than with Windows systems because most languages were designed on Unix system and many are designed for use on Unix systems first and other systems second (Microsoft Windows, though it holds a majority market share, in fact does many things differently from the rest of the world, and it is very hard to work with). I'm a computer science student, too, and you will really appreciate the simplicity and ease of programming on Linux.

See the link in my signature about restricted formats to read about installing codecs for video formats. It's as easy as one simple command (most things in Ubuntu are).

I don't know about podcasts, sorry, but iPod support is there in most major music management software projects.

Yes, you can open pdfs in Ubuntu :D

It's something of a hassle to run Windows programs on Ubuntu, you can install wine (an application compatibility layer) and try to use that to install and run Photoshop, or you can run Windows in a virtual machine and install and run Photoshop from within that, or you can create a Windows partition and boot into that if you need to (bleh :D). Or you can abandon your predilections and learn the GIMP (unless you are a serious graphic artist, in which case the GIMP may not be up to the task, but for most people the GIMP is fully featured and quite usable). Just curious, what do you use Photoshop for mainly?

Read some of the links in my signature, they will help. And welcome!

EDIT: btw, I suggest sticking with the 32-bit version of Ubuntu. There is really no reason for a user to have 64-bit addressing unless you're doing some huge statistical calculations or sub-atomic particle physics modeling or something.

---

### Post by pilate on 2007-08-11
> **jfinkels said:**
>  Just curious, what do you use Photoshop for mainly?


I do a fair amount of graphic design. Shirts, hats, logos, image editing. And this point I'm so comfortable with Photoshop and illustrator that I would hate to have to learn something new. Plus there are tons of tutorials that I read through based on photoshop. Basically it's worth the extra work to me to have photoshop.
And I'm downloading the 32bit version now, thanks!

---

### Post by pilate on 2007-08-11
Sorry to double post, but I'm trying to install the newest version of ubuntu 32bit, and I'm getting an error. After clicking start or install a command prompt comes up for BusyBox. It says "/bin/sh: can't access tty; job control turned off"
Sorry if this is the wrong forum, I didn't want to waste another thread.
Thanks

---

### Post by Paul133 on 2007-08-11
So, you downloaded the .iso, burned it to a disk, restarted the computer, set BIOS to boot from disk, ran the LiveCD, and clicked on Install, and this came up? It appears it can't access the console to install, but I don't know why.

---

### Post by pilate on 2007-08-11
> **Paul133 said:**
> So, you downloaded the .iso, burned it to a disk, restarted the computer, set BIOS to boot from disk, ran the LiveCD, and clicked on Install, and this came up? It appears it can't access the console to install, but I don't know why.

Exactly right. The same thing happens if I try to run "Check Cd for defects"

---

### Post by Paul133 on 2007-08-11
Did you do the md5checksum when you downloaded the .iso?

---

### Post by entangled on 2007-08-11
Try this link
[http://ubuntuforums.org/showthread.php?t=501353](http://ubuntuforums.org/showthread.php?t=501353)

Some weeks ago I had this message booting the CD in parallels but not in vmware and not direct on the hardware. Seems some systems are affected, most aren't.
Should be about time for it to be fixed - or do we have to install Gutsy?.

---

### Post by pilate on 2007-08-11
> **Paul133 said:**
> Did you do the md5checksum when you downloaded the .iso?
Ya they match.
@entangled: I did what that thread said, and I get an error when installing. Something about xserver not working. and it asks if I would like to view the error output. Then it tells me that the error is no screens were found.

---

### Post by Paul133 on 2007-08-11
I suppose you could try installing the alternate CD. I don't know if that would work, but it might.

---

### Post by pilate on 2007-08-11
> **Paul133 said:**
> I suppose you could try installing the alternate CD. I don't know if that would work, but it might.
I'll give it a shot. Whats the differences?

---

### Post by Paul133 on 2007-08-11
The main difference is that the alternate CD does not have a LiveCD "mode"; it just installs Ubuntu. It might work, although I have to admit I can't tell why your system is acting the way it is.

---

### Post by pilate on 2007-08-11
> **Paul133 said:**
> The main difference is that the alternate CD soes not have a LiveCD; it just installs. It might work, although I have to admit I can't tell why your system is acting the way it is.
Well damn.
If it doesn't work where do I go next to try and fix it? Or do I just have to wait until the next release and hope it resolves it's self?

---

### Post by Paul133 on 2007-08-11
So you go to the menu on the alternate CD, but you had the same problem as the LiveCD? You'll probably have to modify the booting (not too hard, if you know what to do), but I don't know what your specific problem is, so I can't tell you what to do. Sorry. All I can say is it's due to your hardware.

---

### Post by pilate on 2007-08-11
[Looks like I'm not the only one having a problem with this laptop.]("http://ubuntuforums.org/showthread.php?t=516084&highlight=Vostro+1500")

I'll give then things in this thread a shot. Hopefully everything will be ok.
@paul: I should have worded that better. The text-based install does work. I was asking what should I do **if** it did not. I made that post while the alt-cd was downloading.

---

### Post by Paul133 on 2007-08-11
So you installed Ubuntu using the alternate CD and it works but you have a completely black screen or ydo you have a commandline but no graphics? And sorry it's not working, but we should be able to figure something out. :)

---

### Post by pilate on 2007-08-11
> **Paul133 said:**
> So you installed Ubuntu using the alternate CD and it works but you have a black screen?
No. [Based on this post]("http://ubuntuforums.org/showpost.php?p=3174090&postcount=9"), I've decided to wait until some more advice comes around.
It did get farther though then the regular cd did. But I canceled it.

---

### Post by jfinkels on 2007-08-12
> **pilate said:**
> I do a fair amount of graphic design. Shirts, hats, logos, image editing. And this point I'm so comfortable with Photoshop and illustrator that I would hate to have to learn something new. Plus there are tons of tutorials that I read through based on photoshop. Basically it's worth the extra work to me to have photoshop.
And I'm downloading the 32bit version now, thanks!

GIMP and Inkscape are not so different from Photoshop and Illustrator, you should give them a chance (it will help you move away from Windows/expensive proprietary software). There are plenty of GIMP tutorials out there.

FYI, there's a rule of thumb on Wikipedia that says "Wikipedia is not a paper dictionary." In essence, that means, don't be afraid to make a new article for something that might not be in your standard Encyclopaedia Britannica. Same goes here: Always make a new thread with a descriptive title and which describes precisely and succinctly your problem. It will help others more easily see your problems and offer solutions.

---

