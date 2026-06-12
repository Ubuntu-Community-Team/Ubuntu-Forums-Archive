---
title: "Stuck on Partitioning"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by billyt on 2007-05-20
Hey guys! My free CDs of Ubuntu 7.04 just arrived yesterday. I'm trying to partition my hard drive that currently has Windows on it. I've defragged it a few times too. When I go to parition it, there's this weird little partition just sitting there. It's 8mb in size. Anyway, when I try to make a new partition, nothing happens. That little 8mb partition just stays there. 

Here's a screenie: 

[[IMG]http://img111.imageshack.us/img111/7759/screenshotqo1.th.png[/IMG]](http://img111.imageshack.us/my.php?image=screenshotqo1.png)

---

### Post by blu3ness on 2007-05-20
Hello, I have had similar problems, chances are that you have a recovery partition from your manufacturer that is used to recover windows in case of a system failure?

if that is the case, what I did was I called HP and asked for an OEM windows xp installation disk and formatted my harddrive with that, deleted all the partitions and installed windows on top of that, then the partitioner in ubuntu shows up correctly.. hope that helps..:p

---

### Post by oilchangeguy on 2007-05-20
8mb is not a recovery partition. does this show up in windows, under my computer?

---

### Post by starcraft.man on 2007-05-20
> **blu3ness said:**
> Hello, I have had similar problems, chances are that you have a recovery partition from your manufacturer that is used to recover windows in case of a system failure?

if that is the case, what I did was I called HP and asked for an OEM windows xp installation disk and formatted my harddrive with that, deleted all the partitions and installed windows on top of that, then the partitioner in ubuntu shows up correctly.. hope that helps..:p

Lol, don't even bother phoning a company for one of those OEM disks they always give a hassle... just get one via bit torrent. While I don't condone piracy, I'd say getting an OEM disk is fairuse/play. Those companies should equally stop loading pcs up with crap when they ship them to you.

I don't think its a recovery partition though, they are usually a few gigabytes big and store the whole image with their extra crap. I don't think it can hurt though, prolly easiest just to ignore it.

Edit: Ya, I agree with oilchange. Maybe its just some random thing... I've seen weirder things happen in paritions >.>.

---

### Post by billyt on 2007-05-20
The hard drive that I have now isn't the original. I bought about 6 months ago at CompUSA when they were closing. I got a really good deal, about $.25-.30/GB.  Anyway, whatever that little partition is, it wasn't put there by Dell. 

I've installed 7.04/CentOS on other PCs without any troubles. That's what annoys me the most.

---

### Post by billyt on 2007-05-20
> **oilchangeguy said:**
> 8mb is not a recovery partition. does this show up in windows, under my computer?No, it's just free space.

---

### Post by starcraft.man on 2007-05-20
Wait, hold on, that one little partition is stopping you from partitioning? Thats super weird. There must be some error on it...

I got a one step fix for you. [DBAN.]("http://dban.sourceforge.net/") Boot and NUKE! as they say :D. I assume theres no valuable data, just point the thing to that drive and let it zero the drive. Then go back to the installer and try again. There is no way it doesn't work after a nuke. I would send you to the gparted live cd (google if you want a copy) but I doubt it works if the live CD won't.

So make the drive go boom :D

Oh and be careful not to nuke the wrong drive, you can't ever recover data from a DBAN erase.

---

### Post by billyt on 2007-05-21
Thanks, I'll give it a shot. :D

Oh and, uh, thanks for the positive reinforcement. :p
[quote=starcraft.man]Oh and be careful not to nuke the wrong drive, you can't ever recover data from a DBAN erase.[/quote]

---

### Post by Inxsible on 2007-05-21
Since you are already in the installation mode for Ubuntu, I was just wondering.......
 
You have just one partition on your drive. Do you intend to nuke Windows or create a dual boot?
 
If dual boot, what you can try is shrink the drive with the Windows partitioner, and check if the 8 MB merges with the *new* freespace that you create.
 
If you are going to nuke Windows, then simply format the entire drive and see if the 8MB still remains

---

### Post by Inxsible on 2007-05-21
Beware:
 
> 
1.0 About Darik's Boot and Nuke
--------------------------------
 
Darik's Boot and Nuke ("DBAN") is a self-contained boot floppy that securely
wipes the hard disks of most computers. DBAN will automatically and completely
delete the contents [COLOR=red]of any hard disk that it can detect[/COLOR], which makes it an
appropriate utility for bulk or emergency data destruction.

 
> 
Enter "autonuke" at the boot prompt to automatically [COLOR=red]wipe all devices in the[/COLOR]
[COLOR=red]computer without confirmation[/COLOR].


---

### Post by starcraft.man on 2007-05-21
Uh... I already did warn him that it is a dangerous program, and you don't have to wipe all drives... there are options. There are a lot of people who use this for mass drive erasure though, and thus the autonuke feature is useful.

---

### Post by BHelts on 2007-05-21
that 8MB 'partition' is put there by an OEM windows installation disk.  It acts as a data cache during the installation.  DBAN will make it a non factor.

---

### Post by Inxsible on 2007-05-21
> **starcraft.man said:**
> Uh... I already did warn him that it is a dangerous program, and you don't have to wipe all drives... there are options. There are a lot of people who use this for mass drive erasure though, and thus the autonuke feature is useful.
 
Oh yeah, I know you warned him.. I just didnt find any info on how to wipe just one drive. My bad !

---

### Post by BHelts on 2007-05-21
active kill disk on [UBCD]("http://ultimatebootcd.com") will write zero's to any drive you want.  not as comprehensive, but it will wipe out all partition structure.  and you don't have to worry about whacking every drive in the room.

---

### Post by starcraft.man on 2007-05-21
> **Inxsible said:**
> Oh yeah, I know you warned him.. I just didnt find any info on how to wipe just one drive. My bad !

There is a readme and a faq on the main site, the autonuke feature is the most popular because its used most often for people who want to donate old computers and can't be bothered to use the command line (the average user) to target right drive, so they put a one word command. I would submit that while DBAN can be dangerous, I've seen a lot of people wipe their windows partitions when picking wrong choice in the automatic installer of Ubuntu :p

Anyway, all software is somewhat dangerous, you never know when it goes boom and takes your whole computer! Just have to make sure you know how to work it before committing :p

Edit: Call me old fashioned bhelts, I like my NUKE!!! :D *pets miniature nuke*

---

### Post by Inxsible on 2007-05-21
> **starcraft.man said:**
> There is a readme and a faq on the main site, the autonuke feature is the most popular because its used most often for people who want to donate old computers and can't be bothered to use the command line (the average user) to target right drive, so they put a one word command. I would submit that while DBAN can be dangerous, I've seen a lot of people wipe their windows partitions when picking wrong choice in the automatic installer of Ubuntu :p
 
Anyway, all software is somewhat dangerous, you never know when it goes boom and takes your whole computer! Just have to make sure you know how to work it before committing :p
 
Edit: Call me old fashioned bhelts, I like my NUKE!!! :D *pets miniature nuke*
 
 
I agree totally !
 
You can do weird things with seemingly innocuous software :)

---

### Post by starcraft.man on 2007-05-21
> **Inxsible said:**
> I agree totally !
 
You can do weird things with seemingly innocuous software :)

Especially with software containing the words "genuine" and "microsoft", your screen can just spontaneously turn blue for no reason at all :p

---

### Post by Inxsible on 2007-05-21
> **starcraft.man said:**
> Especially with software containing the words "genuine" and "microsoft", your scren can just spontaneously turn blue for no reason at all :p
 
 
I have been a victim of that quite a few times. Anything with Microsoft in it, I don't trust !
 
Vista really gets on my nerves !

---

### Post by billyt on 2007-05-21
Sorry for the confusion guys. I should have stated this better. I want to shrink the XP partition, but for some reason I can't. I've tried using gparted too, but it won't let me either.

---

### Post by Happy_Man on 2007-05-21
Staring critically at your original screenshot... it seems that the GParted can't figure out how much of your drive is used. This is probably why it's not letting you partition, it's afraid it will kill data by mistake. 

@starcraft and friends: yes, the nuke talk is very manly and all, and i loves a good nukin' as much as the next guy, but at least look at the info before telling him to wipe the drive.... sheesh.

---

### Post by houstonbofh on 2007-05-21
What does a screenshot of Gpartd look like?  This is what I use for shrinking...

---

