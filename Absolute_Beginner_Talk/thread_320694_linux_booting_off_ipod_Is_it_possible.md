---
title: "linux booting off ipod? Is it possible?"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by greenimacg3 on 2006-12-17
Uh, I want to format my drive, but linux is on it. So I cannot have it delete it self and I cannot  find my live CD so, can I copy the files to my ipod and boot it off of that?

---

### Post by raul_ on 2006-12-17
Wouldn't it be easier to download an image, burn it, boot from the live cd and format? i don't know, it's just a sugestion :) (plus it would make your life so much easier to reinstall, if u want)

---

### Post by greenimacg3 on 2006-12-17
Um yea, how big is the image?

---

### Post by raul_ on 2006-12-17
600mb i think...
U can download it from ubuntu's site

[http://www.ubuntu.com]("http://www.ubuntu.com")

---

### Post by robinl on 2006-12-17
Uhhh the standard 700mb Ubuntu Live/Install CD? By formatting your drive do you mean wiping it clean and start over? If you do mean that it can be done in both Ubuntu installation and Windows installation, just delete that partition.

---

### Post by raul_ on 2006-12-17
He couldn't find his live cd...and u can't format a mounted drive, hence the need of creating a new live cd :P

---

### Post by greenimacg3 on 2006-12-19
Uh, 600 megs on dialup? I don't think so. I am cleaning my room tomorow I think to find my microphone, and while I am, I may find it.

---

### Post by Pobega on 2006-12-19
Can you boot off of an iPod?

---

### Post by Bachstelze on 2006-12-19
An iPod is an external USB drive like any other, so I can't see why you couldn't boot off it, if your MoBo supports booting from USB of course.

---

### Post by greenimacg3 on 2006-12-19
Will Il just have to copy whats on HD1 to my ipod then format HD1 and then format my ipod? I hope it suports it. Anybody know how to get past a bios password? I got this laptop used.

---

### Post by Bachstelze on 2006-12-19
You can use Gparted LiveUSB which is very light and will run perfectly from your iPod - that is, if your MoBo supports booting from USB.

---

### Post by AndrewB on 2006-12-19
There is a small utility called DBAN that will wipe your drives. [http://dban.sourceforge.net/]("http://dban.sourceforge.net/") shouldn't hurt too much on a dial up connection. 

Good luck with the ipod idea:)

---

### Post by xyz on 2006-12-19
[How to install Ubuntu Edgy to USB, to boot from any USB bootable machine]("http://www.ubuntuforums.org/showthread.php?t=308027&highlight=install+external+drive")

---

### Post by liljoe76 on 2006-12-19
most bios have a password backdoor, ask your question in google :)

---

### Post by antgul3382 on 2006-12-31
you have linux on your ipod??? can someone help me do this i have an ipod video 30 gb  (5g)

---

### Post by neowolf on 2006-12-31
If your sure you want to do this check out Rockbox, Linux for MP3 players.
[http://www.rockbox.org/](http://www.rockbox.org/)

---

### Post by antgul3382 on 2006-12-31
im not sure is it any good??? will it screw it up??? what do you think about it???

---

### Post by teejay17 on 2006-12-31
I would like to know which one is preferred and/or more stable: RoxBox or iPodLinux?

---

### Post by raul_ on 2006-12-31
i think rockbox is more advanced, hence more stable

---

### Post by Good Ol' Ramos on 2006-12-31
To get past your BIOS password, you have to reset the CMOS jumper. Find it first, then pull it out, and, well, here's a sorta picture...

o [oo]    - the o's are the pins, and the [  ] is the jumper. Pull the jumper out...
o o o   - plug the jumper in, one space over...
[oo] o   - then unplug, and put back where it was...
o [oo]   -  Everything will be reset to default settings, but you'll at least be able to go in there and change things around to your liking. Also, if you just keep hitting F8 in the boot screen, it gives you a "select which device to boot" menu.

---

### Post by califman831 on 2006-12-31
> **greenimacg3 said:**
> Uh, 600 megs on dialup? I don't think so. I am cleaning my room tomorow I think to find my microphone, and while I am, I may find it.


have ubuntu mail u the cds, both the cds and shipping are free, but it takes a while to recieve them.

---

### Post by antgul3382 on 2006-12-31
both rockbox and ipod linux say that the g5 ipods arent supported, i have the ipod video 30 gig   has anyone done it yet???

---

### Post by pizlo on 2006-12-31
I use and have used Ipodlinux for years, it is very safe and stable, check out their forums at ipodlinux.org it is simple to fin the latest version for any ipods with a screen, if you have any questions pm me or just post there, they have an active forum.
I do not knw much about rockbox but most people at IPL know some or allot about it.

---

### Post by raul_ on 2006-12-31
I use rockbox...it..erm...rocks :) It takes some time to get used to, but the themes make the transition much easier. It's really nice to have your ipod themed. This thread isn't about this though

---

### Post by teejay17 on 2007-01-01
I have a 60 gig iPod, but the type that was out just before the video iPods were released; it has a colour screen, good display, etc. and it was made for photos, basically.
What I want to know is if it's possible to get video to play on this sucker, with either RoxBox or iPodLinux? 
It would be wicked if I could get video on an iPod that isn't "supposed" to have video on it!

---

### Post by raul_ on 2007-01-01
[http://www.engadget.com/2004/11/09/how-to-play-movies-on-an-ipod-photo/]("http://www.engadget.com/2004/11/09/how-to-play-movies-on-an-ipod-photo/")

Don't get to excited..It's cute but pointless though. The answer to your question is in the first line =p "no"

---

### Post by teejay17 on 2007-01-01
> **raul_ said:**
> [http://www.engadget.com/2004/11/09/how-to-play-movies-on-an-ipod-photo/]("http://www.engadget.com/2004/11/09/how-to-play-movies-on-an-ipod-photo/")

Don't get to excited..It's cute but pointless though. The answer to your question is in the first line =p "no"

Yes, I see what you mean. The long answer is no...and it would be a very complicated process. 
Perhaps there's some ingenious way that hasn't been discovered yet (optimism = :D ).

---

### Post by shanepardue on 2007-01-01
I had bad luck with rockbox. Great idea, but it froze at least once every 30 minutes of playback. Very annoying!

---

### Post by Frak on 2007-01-01
I've installed it on my iPod before, your supposed to install it via disc mode, which on mine is center button, up botton held while starting the iPod, and then use Casper Cow to boot.

---

### Post by teejay17 on 2007-01-15
Overall, though, what's the experience like having Linux on an Ipod. Does it play/perform better than the Mac software that it comes with?

---

### Post by shanepardue on 2007-01-15
I have got Rockbox to work much better with a build that disables cpu scaling. my rockbox never freezes now. [http://mikeage.net/content/rockbox/](http://mikeage.net/content/rockbox/)

---

### Post by teejay17 on 2007-01-15
> **shanepardue said:**
> I have got Rockbox to work much better with a build that disables cpu scaling. my rockbox never freezes now. [http://mikeage.net/content/rockbox/](http://mikeage.net/content/rockbox/)
Cool. How hard is it to configure everything, to get it just right?

---

### Post by shanepardue on 2007-01-15
well, rockbox isn't linux for the record, but there's barely any configuring once you get it setup..it may be a little hard to set up if you've never done it before, but if you're a linux user, I'm sure you don't shy away from a little challenge. :)

---

