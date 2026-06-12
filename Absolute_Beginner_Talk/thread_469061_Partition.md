---
title: "Partition"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by Tyke91 on 2007-06-09
Now that i've used ubuntu for over a month... i realize that there is almost no way that i am going to go back to windows, but i'd like to have a small windows partition on my machine so that i can play games.

Here's my plan: 

Use Gparted to delete and format my windows partition 

Create a smaller partition (20 or so gigs)

install windows on that.



My only worry is that this will somehow delete Grub, and i want to know if theres a way i can solve that problem without reformatting my Ubuntu drive as well (i've finally got ubuntu with all the stuff i want on it)

---

### Post by diatribe on 2007-06-09
if all the partitons are on the same drive, you can boot with the ubuntu livecd and just use gparted to resize your  windows/linux partitions; then you won't have to bother formatting

---

### Post by starcraft.man on 2007-06-09
Ok, sounds like a fine plan to me. I assume your reinstall cuz ya want a clean copy rather than a resize. I concur, clean is always better with Windows (especially with how fast the registry bogs down, at least my experience). I wouldn't worry about messing up GRUB, when you reinstall XP it will of course overwrite GRUB. After that you can just use the Live CD to reinstall grub to hda or whatever is your master drive.
[URL="http://ubuntuforums.org/showthread.php?t=224351&highlight=grub"]
Here's a quick guide.[/URL] I assume you have the live CD so it won't require anything extra other than that.

If there is an emergency and that doesn't work or some other situation unforeseen, [GAG]("http://gag.sourceforge.net/") is my back up, has never failed yet to automatically detect every OS on my system and boot em all.

That should do it, don't worry too much, we are always reachable via the live CD if anything goes wrong :D.

---

### Post by Tyke91 on 2007-06-09
lol... i just realized that i have no clue how to use Gparted :)

i have it at the point where it shows all 4 of my partitions (Windows, Ubuntu, Swap, and one that dell put on my comp for some reason)

every one of these boxes has a small lock next to them... what do i do next to wipe windows (and that dell one too)

---

### Post by starcraft.man on 2007-06-09
> **Tyke91 said:**
> lol... i just realized that i have no clue how to use Gparted :)

i have it at the point where it shows all 4 of my partitions (Windows, Ubuntu, Swap, and one that dell put on my comp for some reason)

every one of these boxes has a small lock next to them... what do i do next to wipe windows (and that dell one too)

Have a [read through this]("http://gparted.sourceforge.net/larry/generalities/gparted.htm") and you will understand all the options. Just be sure you know exactly what your doing before you apply, there are no do overs :p.

Oh and uh, make sure that dell partition isn't a service partition you need to use system restore disks. If not, then by all means nuke it at your pleasure :).

Have fun. 

Oh and this is the[ index of documentation]("http://gparted.sourceforge.net/documentation.php") :). I only linked ya to the general page.

---

### Post by Tyke91 on 2007-06-09
actually... i'm pretty sure it is. good call :D

thx for all the help

---

### Post by starcraft.man on 2007-06-09
> **Tyke91 said:**
> actually... i'm pretty sure it is. good call :D

thx for all the help

No problem. If I were you I'd get my own copy of the install disk though, I hate those system disks companies give. You know, they just do that so each time you reload your forced to have that crap they load your PC with. It's not right. I remember a time when they willingly gave you the windows installer disks......

I'd just go on a torrent site and get the OEM version of whatever windows your using... I think its fair use to have the install disk, you paid enough I'm sure for your computer not to get screwed by the company. Once you have the install CD you can then delete the partition and toss the disks...  your key works most of the time long as you get the right OEM copy, worked for me. Be sure to try before doing anything permanent >.>.

---

### Post by Tyke91 on 2007-06-09
I just looked through it, i looks like i can't unmount the windows partition

[[IMG]http://images7.pictiger.com/thumbs/7a/f0110d0448cca37f3e2d066021603e7a.th.png[/IMG]](http://server7.pictiger.com/img/269560/picture-hosting/-home-mykola-desktop-1-.php)

is there a way to manually do it?

---

### Post by starcraft.man on 2007-06-09
> **Tyke91 said:**
> I just looked through it, i looks like i can't unmount the windows partition

[[IMG]http://images7.pictiger.com/thumbs/7a/f0110d0448cca37f3e2d066021603e7a.th.png[/IMG]](http://server7.pictiger.com/img/269560/picture-hosting/-home-mykola-desktop-1-.php)

is there a way to manually do it?

Are you booted into your regular Ubuntu session? The custom red leaves me to believe its not a live CD or gparted live cd. If your logged in regularly you are running of those partitions and you will be very limited (you can't for instance unmount anything thats being used by the file system).

[Here,]("http://gparted.sourceforge.net/download.php") download and burn the latest build of the live CD. Or alternatively boot into the Live CD (if you have one) and install gparted and then run it. You can't do it effectively while logged in default though. I always use my gparted live CD but thats me.

---

### Post by Tyke91 on 2007-06-09
lol... i have the cd :) thx for telling me

---

### Post by starcraft.man on 2007-06-09
> **Tyke91 said:**
> lol... i have the cd :) thx for telling me

No problem :D

Just make sure you double check everything you change in partitions before applying. No undo button :p.

I think that should be it for here... off I go to other threads, best of luck. :).

---

### Post by Tyke91 on 2007-06-09
grr :) 

it seems as if i cannot grow my partition... i think this is because of where it is placed on the disk, i need to move the partition to the front, but i can't do it.

this is what it looks like (and yes... i realize i have an enormous amount of swap space... i didnt know what it was for at the time and i wanted to have enough ;) )

[[IMG]http://images7.pictiger.com/thumbs/6b/214f5dd1f6a665512b40eb8221a2576b.th.png[/IMG]](http://server7.pictiger.com/img/269826/picture-hosting/-home-ubuntu-desktop-1-.php)

---

### Post by Tyke91 on 2007-06-09
turns out it still thinks my linux partition is mounted.

what i'm trying to do is

-copy the liunx partition
-paste it into free space
-delete the current linux partition
-grow the new one into the old one
-install windows on the rest.

this is what i get when i try to do it.
[[IMG]http://images6.pictiger.com/thumbs/a6/94471daabb91ffeac72122c62ea313a6.th.png[/IMG]](http://server6.pictiger.com/img/270215/picture-hosting/-home-ubuntu-desktop-2-.php)

---

