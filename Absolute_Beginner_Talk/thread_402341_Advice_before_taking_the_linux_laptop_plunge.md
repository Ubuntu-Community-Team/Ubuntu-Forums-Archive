---
title: "Advice before taking the linux laptop plunge"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by mm07@earthlink.net on 2007-04-05
Hi all,

First post! What a really nice community you guys have here.

I have some statements, and two questions.

I just purchased a reasonably priced new laptop. Dell Inspiron 6400 2gig, intel950 graphics, for the express purposes of running Ubuntu on it. 
Now this may sound a little crazy, but I am not going to dual boot. The purpose of this project is to become more proficient under linux and I don't want the windows crutch to fall back on when something doesn't work, so I'm forcing myself into a sink or swim situation  The first thing I'm going to do it wipe the harddrive soon as I get the machine (after verifying all the hardware works).
So I will either have a nice linux box, or an expensive paperweight at the end of this!!
Now don't try and talk me out of it! I already have a 2 winxp laptops, 1 xp PC, and a new Vista PC at my house.. so I don't really need dual boot. Plus, I've done some research and people have gotten my exact config working no problem.. so here's looking forward to it.
Is this really smart or stupid?? 
Advice, comments or insults are appreciated.... :) 

Now on to my questions:
1) When I repartition the HD, do I need to preserve any of the dell partitions for anything? Like I said, not going to use the installed OS or the recovery mode. I can't think of anything I'd need from the HD, but its so destructive, I thought I'd ask just in case.

2) How's this look for a parition table on a 100gig drive.
 a) root  50gig
 b) swap 3 gig
 c) home 47gig

This way, It is a relatively simple install, but I can still retain my stuff in home if I need to reinstall the os from scratch. Am I overlooking anything?

Thanks again..
-Mike

---

### Post by insane_alien on 2007-04-05
Its inadvisable to go straight to linux but this is ubuntu. it'll make it as easy as possible and as always its your choice.i won't talk you out of it.

1/ when you load the live CD and start installing you'll be given the option to wipe the drive and auto partition or manually partition.

2/ you'll want manual partitioning. just delete the preexisting partitions and create the ones you want (its pretty self explanitory and there are guides on the net).

3/enjoy.

you'll probably run into a few problems like everybody and it will seem backwards for a bit but in a week or two you'll be using it like your were born using it.

---

### Post by mrmonday on 2007-04-05
> **mm07@earthlink.net said:**
> Is this really smart or stupid?? 

If you insist on wiping the hard drive and getting rid of windows, I would make a backup of your recovery partition, (the partition that is not xp or vista). This is just in case, as that's a very expensive paper weight, if something goes wrong. You could always make grub boot straight to Ubuntu, so Its as if there is no windows there. I don't think you need all that space for your root partition... I'm not sure, I have everything in one partition. As for your swap partition, It depends on the amount of memory in your PC, I am not sure what the ratio for RAM:SWAP is for linux.

---

### Post by johnc4510 on 2007-04-05
Well, my first thought is great. My second thought is if this is a new Dell, your warranty might be void without the original OS.
 
Don't know about the dell partitions and what is on them.

Your root partition is way to big. Somewhere between 7 and 10 gigs is worlds of room.

Swap should be twice your ram. ie 512x2=1024mbs is 512 is your ram.

Make the rest of the free space your home partition. This is where all your personal data will be stored.

Hope this helps

---

### Post by insane_alien on 2007-04-05
he has 2 gig of ram. 3 gig of swap is sufficient as its a 1.5x -2x thing with swap to ram. besides, with 2 gig he'll never even get close to touching the swap. i barely scrape it with 1 gig of ram.

---

### Post by rbhigday on 2007-04-05
Welcome I also took the plunge and wiped my hard drive and took on Ubuntu on my laptop to learn, now I have a dual boot on my desktop and use windows for games and some school.

     Now on to my questions:
     1) When I repartition the HD, do I need to preserve any of the dell partitions for anything?       
     Like I said, not going to use the installed OS or the recovery mode. I can't think of anything   
     I'd need from the HD, but its so destructive, I thought I'd ask just in case.

I cleared mine on the laptop mostly to prevent me from going back and pushing me to learn more about linux

     2) How's this look for a parition table on a 100gig drive.
     a) root 50gig
     b) swap 3 gig
     c) home 47gig

While you will get many discussions on the size of the swap partition being anywhere from 1gig to  4 or 5 I guess your 3 is ok. I think I did a 1 gig, laptop is at home and I am at work so I do not remember off the top of my head

for the root I only used 20 gigs and I used the rest for home. To use 50 in root I believe would be a real waste of hard disk space

---

### Post by Homie Bongo on 2007-04-05
If you do not want your Windows anymore, I think you can just reformat your HD. I don't know Dells, but for example my Lenovo has on its hidden partition some diagnostic tools, Windows restoration but it also contains Opera browser (!) for finding help.

Just make sure you have the latest BIOS installed since the update utility will be probably only for Windows.

Regarding your partitioning: I think having 50GB root is way too much, 15GB should be fine with a great reserve, swap should fit into 1 or 2 gigs also, I think (I am not sure whether anything really needs 3GB swap).

---

### Post by nik on 2007-04-05
Warranty is not void if you install linux. They might refuse to repair it without windows installed, but I doubt it...

You'r plan looks good. I agree with previous poster, make your root partition 7-10 gig (mine is 5, and that's ok, but I'm running out of space after installing lots of stuff).

I think it's great to just remove windows. you won't have too many problems with ubuntu, and this way you'll probably fix the few you run into faster than if you were dual booting.

Good luck :)

---

### Post by Hortinstein on 2007-04-05
I actually did the same thing less than a month ago since I needed a programming platform, and I didn't want to dual boot my XP desktop, that I only use for media and gaming.  

I completely wiped the dell partitions, and the entire hard drive, since it shipped with vista basic and put ubuntu on there, and with the exception of altering the boot config a little bit, getting my wireless card working with NDISWrapper, installing updated graphics driver, it was pretty painless.  

I would never even think of putting windows back on it since I am used to Beryl and all the freedom I have with Ubuntu.  Trust me when I say it's pretty hard to go back to using a windows computer after some quality time with linux + beryl.  Just get ready to spend some time in the forums getting everything working right.

Not sure, but I would also reccomend installing 7.04 or waiting for the offical release, since its gonna be a lot better for laptops

---

### Post by mm07@earthlink.net on 2007-04-05
Hey, now you guys have got me scared that dell might give me trouble repairing it if I wipe the OS.

So is there a way I can shrink the OS partition (C:) drive down to a very small size, like 2-5 gig, or whatever a little more than the OS size is?

If so, I will shrink the OS partition down to whatever size it currently occupies, plus 2 gig... it will be for emergencies and after my 1 year warranty, bye bye, and I'll get that space back.. Which after 1 year, I'll probably need it...

I mean, I know there is a way, but does the ubuntu installer allow you to do that? Or do I need to get another utility, and if so what is it?
I 
Also, everyone says 7-10 gig is enough for root. But isn't root where all the application software and log files go? Or do you install stuff to your home? Or is it your choice??

So I could potentially hit that root size limit if I install tons of applications right? Is there a way to grow the linux file system on the fly? Reiser FS I guess it is?
But I agree with everyone's recommendations at 20 gig should be overkill.

-Mike

---

### Post by ramjet_1953 on 2007-04-05
Why not think outside the square?
The advice that you have been given so far is sound, but another option is to just buy another hard drive and take the original out.

Hard drives are cheap and this option allows you the freedom to fiddle with your new Ubuntu installation, without any risk of hosing your Dell-Installed Vista installation.

Also, if there is any problem with your PC, you can just put the original hard drive back in and send it to Dell for service.

On laptops hard drive replacement is very easy, as there is usually just a "trap-door" underneath and the hard drive just unplugs. You usually have a "carrier" that the hard drive sits in, and you just remove 4 screws and place the new hard drive into the carrier. The whole operation just takes a couple of minutes.

Regards,
Roger :cool:

---

### Post by mrmonday on 2007-04-06
> **mm07@earthlink.net said:**
>  
Also, everyone says 7-10 gig is enough for root. But isn't root where all the application software and log files go? Or do you install stuff to your home? Or is it your choice??


Yes it is where all your software and log files go. Programs on Linux don't use up gigabytes of spae like windows. I don't think you get a choice of where to install stuff... I think it is all over the place.

> The advice that you have been given so far is sound, but another option is to just buy another hard drive and take the original out.

Good idea. Also, when your 1 year warranty runs out, you have an extra 100GB of free space, for whatever you like!

---

### Post by rich.bradshaw on 2007-04-06
THe dell partition si exactly the same as what's on the recovery CD, so if you have that you are fine.

---

### Post by Ubluedog on 2007-04-06
i reformatted my armada and plunged into ubuntu and havent looked back, i use it as a web browser and online chat machine.
make sure you have the recovery cds , toshibas for instance make you burn your own recovery cds from an app on the desktop.
once you have organised the backups then go ahead and experiment .
i am in the repair business , if the laptop stuffs up , see if you can execute the recovery cd b4 sending it back for warranty service, if you cant get the machine to boot , whack the hd into another and reformat it, then send the lot back for service.
point being , once you have the recovery disks you can return the machine to original status.
warranty will not be void
enjoy

---

### Post by j2satx on 2007-04-06
> **mm07@earthlink.net said:**
> Hey, now you guys have got me scared that dell might give me trouble repairing it if I wipe the OS.

So is there a way I can shrink the OS partition (C:) drive down to a very small size, like 2-5 gig, or whatever a little more than the OS size is?

If so, I will shrink the OS partition down to whatever size it currently occupies, plus 2 gig... it will be for emergencies and after my 1 year warranty, bye bye, and I'll get that space back.. Which after 1 year, I'll probably need it...

I mean, I know there is a way, but does the ubuntu installer allow you to do that? Or do I need to get another utility, and if so what is it?
I 
Also, everyone says 7-10 gig is enough for root. But isn't root where all the application software and log files go? Or do you install stuff to your home? Or is it your choice??

So I could potentially hit that root size limit if I install tons of applications right? Is there a way to grow the linux file system on the fly? Reiser FS I guess it is?
But I agree with everyone's recommendations at 20 gig should be overkill.

-Mike

Buy a separate hard disk to use just for Linux.  If you have to send the laptop in for repair, re-install the original hard disk.

---

### Post by thefoolisme on 2007-04-06
Dell doesn't usually ship the restore disks anymore, so either 1.  make the restore disks from the recovery tool and verify that they work; 2.  Resize the Windows partition with gparted, and keep it in place for the time being, or 3.  buy an extra hard drive.  

Just food for thought, another reason to have the recovery disks or keep the windows info might be for resale down the road.  I don't know if you plan on keeping the laptop until it dies, or will be selling it in a year or 1 on eBay and upgrading.  However, a lot of people would be more interested in it with the Windows option, than just Linux.

---

