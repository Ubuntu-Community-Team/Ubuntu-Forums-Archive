---
title: "Installing a Virtual Machine"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by Tyke91 on 2007-06-04
hey, i'd like to install a windows virtual machine on fiesty, but i have no clue how to do it.


are there any step by step instructions i could use?

---

### Post by smoker on 2007-06-04
hi, i use virtualbox, and there are complete instructions and a comprehensive user manual available here:
[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

hope this helps:-)

---

### Post by Seisen on 2007-06-04
I recommend VirtualBox also its easy to use and setup.

---

### Post by thelocust on 2007-06-04
Automatix2 will install your choice of Virtualbox or VMware server and set up everything for you (like groups and stuff). I suggest you go with Virtualbox. [Heres]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#Automatix2") the install instructions I suggest using the alternate instructions (so that you get updates).

---

### Post by Tyke91 on 2007-06-04
hurray for automatix!

---

### Post by Tyke91 on 2007-06-04
hmm... virtualbox seems to be running great, but i dont know how to configure it.


i've got some screenshots of what i've done. can someone tell me what's wrong?

[[IMG]http://images3.pictiger.com/thumbs/b2/f7af89246806439dbf7ced170ab245b2.th.png[/IMG]](http://server3.pictiger.com/img/1049824/picture-hosting/-home-mykola-desktop-screenshot.php) 

[[IMG]http://images3.pictiger.com/thumbs/60/4e33e12aa7c8ccd642a21dc82cb2b660.th.png[/IMG]](http://server3.pictiger.com/img/1049825/picture-hosting/-home-mykola-desktop-more-info.php) 

[[IMG]http://images3.pictiger.com/thumbs/d9/74de4b3691aa274733afc4b6a6be7ed9.th.png[/IMG]](http://server3.pictiger.com/img/1049826/picture-hosting/-home-mykola-desktop-uh-oh.php) 

[Photos Gallery - PicTiger](http://www.pictiger.com)

---

### Post by HotShotDJ on 2007-06-04
After you create the proper virtual machine, you need to install something in it.

---

### Post by Tyke91 on 2007-06-04
how? it won't even start

---

### Post by smoker on 2007-06-04
hi, have you mounted your cd drive in virtual xp? i had a prob before and find it easier to convert the xp install disk to an iso and mount that from the option in the cd drive settings.

also, for other distros of linux, saves burning the disks from iso,

---

### Post by Tyke91 on 2007-06-04
whoa! backup.

what i've done sofar -

1. downloaded automatix

2. used automatix to get virtual box

3. started virtualbox and set it to the configurations shown.

where does an iso disk come into this at all?

---

### Post by smoker on 2007-06-04
you need to install xp, to have a virtual xp, so you need an xp install disk in the cd rom  and the cd rom mounted in your virtual xp. once virtualbox finds the xp disc, it will begin an install of xp.

regarding iso's, in the cd drive options, you can either mount the cd drive with a disk inserted, or with an iso image (which i prefer!) sorry if i caused confusion.

---

### Post by HotShotDJ on 2007-06-04
I take it you didn't look at the user's manual that was mentioned earlier in the thread?  Ok... put your Windows installation disk in your CD-ROM. Next, in VirtualBox, click on CD/DVD Drive... now, make sure "Mount CD/DVD Drive" and "Host CD/DVD Drive" are ticked.  Make sure the path to the CD/DVD drive is correct (probably /dev/cdrom).  Click Ok.  Now click the start button.

---

### Post by thelocust on 2007-06-04
Put in what ever cd you want to install from go to VM>Mount CD> /dev/cdrom (it's not exact I'm doing it from memory because I'm not on my computer right now. Could somebody verify). Then hit start.

---

### Post by Tyke91 on 2007-06-04
lol.. i didn't even see the user manual. thx for the heads up.

---

### Post by Tyke91 on 2007-06-04
sorry for bugging you guys, but that link to the complete online guide seems to be broken


anyway. i've made sure it's booting from the disk and that the disk is mounted.

but i still get this
[[IMG]http://images7.pictiger.com/thumbs/9d/3025e9629bf58eac1bc49fb66eec8e9d.th.png[/IMG]](http://server7.pictiger.com/img/236262/picture-hosting/-home-mykola-desktop-xp--.php)

---

### Post by Tyke91 on 2007-06-04
lol. scratch that. i was using the wrong cd drive (i've got 2)

---

### Post by HotShotDJ on 2007-06-04
> **Tyke91 said:**
> lol. scratch that. i was using the wrong cd drive (i've got 2)LOL.  I hate it when that happens. ;)

---

### Post by Tyke91 on 2007-06-04
just one more question (happily chugging along with the install now)

will i be able to get viruses from this? (just so that i avoid checking email-etc in the VM)

---

### Post by HotShotDJ on 2007-06-04
> **Tyke91 said:**
> will i be able to get viruses from this?
Yuppers!  It will run everything that XP normally can run, including viruses.  BUT, they will only effect the Virtual Disk you created for Windows.   Just delete the Virtual Disk and start again.   I keep a known-clean-backup of my virtual disks so that I can delete the infected one (hasn't happened, but you never know) and drop in the backup.  Takes all of 60 seconds. :)

---

### Post by smoker on 2007-06-04
after you do an install, you can make a 'snapshot' which will reset your xp to a new clean state again:-)

---

### Post by HotShotDJ on 2007-06-04
I learn something new everyday.  Smoker's method is WAY easier. :)

---

### Post by Tyke91 on 2007-06-04
great :D

i've got it running now, but it won't go above 1024 by 768 pixels.

this isn't a real problem, but it's annoying having to click in a tiny little window (my usual is 1600x1420)

any way to make the window stretch to fit my whole monitor (and hopefully shrink back? the full screen button only adds white space)



it really becomes an issue when i play starcraft, which is only 640x(some other small number... can't remember)

---

### Post by XxTaylorxLovelyxX on 2007-06-04
Here is the easeyest way delete Ubuntu and use windows.

---

### Post by Tyke91 on 2007-06-04
hey taylor. please don't try to get my thread locked as well. I use windows to play games, and it's kinda dumb having to play them in little boxes so I'm asking for help.

i'd still never switch back to windows completely if you gave it to me for free (because this is free and it's better :p)

---

### Post by bodhi.zazen on 2007-06-04
Tyke91 ~ Install the Additions and you will be good to go.

I am trying to maintain a wiki page on VirtualBox here :

[http://doc.gwos.org/index.php/VirtualBox](http://doc.gwos.org/index.php/VirtualBox)

(See the additions section for your resolution problem)

comments additions welcome :)

---

### Post by godd4242 on 2007-06-04
> **XxTaylorxLovelyxX said:**
> Here is the easeyest way delete Ubuntu and use windows.

How is that helpful at all?

and why the spelling errors and lack of punctuation?

I smell some viral marketing :3

---

### Post by Tyke91 on 2007-06-04
please... let's not bring that up again in this thread :)

well... you can bring it up again, but not untill my problem is fixed ;)


btw bodhi, nice job on the wiki :D please keep it up so that newbs like me can learn and crawl out of this ditch of newbdom

---

### Post by Tyke91 on 2007-06-04
woot! problem solved... 


but now my CD drive wont work. 

how do i *unselect* the additions? it only gives me the options to refresh or add.

---

### Post by Tyke91 on 2007-06-04
also, whenever i try to run the game Starcraft, i get this bug

[[IMG]http://images7.pictiger.com/thumbs/98/7af4b43b7c08721350311105158d2698.th.png[/IMG]](http://server7.pictiger.com/img/237651/picture-hosting/-home-mykola-desktop-screenshot-1-.php)

---

### Post by jerrylamos on 2007-06-04
May issue of Linux Format magazine shows a little on Virtual Box, says there's a place on the screens you show above which is labelled "CD/DVD ROM", click on that, and see if you can select either your CD or a .iso image.  I haven't done it.  The magazine also mentions Qemu which I have run a little bit.  I'd need a much faster machine than this 1.2 MHZ Celeron.
Cheers, Jerry

---

### Post by Tyke91 on 2007-06-04
lol jerry ;) i did that, but now the starcraft is angry because it cannot change my resolution

---

### Post by galleonway on 2007-06-12
Has anyone tried DragonDictate 9 with Virtual Box?

---

### Post by bodhi.zazen on 2007-06-12
> **galleonway said:**
> Has anyone tried DragonDictate 9 with Virtual Box?

Dragon works of VirualBox 1.3.8. For some reason I can not get it to work on 1.4.0.

At any rate, you need to install the low latency kernel (on your linux host).

I used DNS 8 on virtual box for a week. The program ran just fine, not problems that way. However, accuracy and speed were poor, even with the low latency kernel (without the low latency kernel you will not be able to set up a new user).

The best raw performance is Dragon 7 + wine (dragon 8 and 9 do not work with wine, dragon 7 on wine is buggy in terms of the gui, dictation is fast and accurate).

---

### Post by galleonway on 2007-06-24
It looks like I will have to keep dual booting with Windows XP if I want to use DragonDictate.  What a drag!

---

