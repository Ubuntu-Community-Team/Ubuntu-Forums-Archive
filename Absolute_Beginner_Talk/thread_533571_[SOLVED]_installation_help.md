---
title: "[SOLVED] installation help"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by deepblue80 on 2007-08-24
right
Hardware: Asus P5NE SLI Mobo, E2160 Intel Processor, 2GB Ram, 2 ide cd drives, 1 ide hdd 80 gb

Background:
Now i was running windows xp on my old system when i decided to upgrade to this setup above. i just replaced the parts and obviously windows doesnt like it when you change mobos. so i decided to go for Ubuntu Fiesty Fawn 7.04. 
it installed from the live cd and i choose the first option in the hdd which read 'resize ide1 to 50%'. the remaining space on hdd was seen as 'file' in Ubuntu Fiesty Fawn later on after the install. everything worked great, it was razor fast and awesome. 

Problem:
I then decided to do a clean install of ubuntu to use my entire HDD so i popped in the same ubuntu 7.04 Fiesty fawn cd, rebooted from the cd drive and it gave the familiar startup screen with 5 options i selected the first one start/install ubuntu. then i started installing Ubuntu, it asked me the partiion options i selected second one, format entire ide1 82 gb. this is where the problem started. i cannot run the complete install process, it runs till about 31% and then hangs. i do not know why. again i repeated the install with different option in the format hdd pop up window and same problem yet again.
then i got my Suse 9.02 dvd out and tried to install suse but without luck. 

anyone can help me do A clean install please? i think as windows xp was running on hdd formatted as ntfs, its coming up with all sorts of crap. how do i perform a clean install - do not know any commands for the terminal!
thanks in advance!

---

### Post by swoll1980 on 2007-08-24
if ubi is already on there just use gparted to expand its partition if it's borked use gparted to wipe it clean make the patitions you want then install on existing partitions you can download gparted on distrowatch.com

---

### Post by deepblue80 on 2007-08-24
> **bloor75 said:**
> if ubi is already on there just use gparted to expand its partition if it's borked use gparted to wipe it clean make the patitions you want then install on existing partitions you can download gparted on distrowatch.com

GParted didnt work when i did my first install. it just wouldnt re-size or do anything to the other partition. hence i decided to re-install from the beginning to have a clean slate. at present i can only run live cd, nothing else and i cannot run firefox - so no question of downloading from the website. i may be able to download stuff from terminal using apt-get but i am not sure, what i do know however is Gparted didnt work :-(

---

### Post by swoll1980 on 2007-08-24
were there locks on the partitions you were trying to format? did you hit apply after you finished all you task?

---

### Post by deepblue80 on 2007-08-24
> **bloor75 said:**
> were there locks on the partitions you were trying to format? did you hit apply after you finished all you task?

hmm,
i selected the hdd options and then pressed install. i cannot say if there were locks on partions but surely if its a clean install it should just re-format the HDD i would have thought or am i being stupid? the thing is it doesnt hang at formatting, it formats and then starts installing and then hangs at 31% exact, everytime!
also i did just to boot from the hdd to see if the first install (see my first post for details!) would boot; it doesnt and gives me a black window with the message GRUB error 22.
so effectively we can presume that the first ubuntu install is dead or corrupted.

ALSO I JUST REMEMBERED - when i tried installing Suse 9.04, it gave me message saying an existing linux install has been detected. then it gave me 4 options - i choose the repair install even though its a different distro. didnt work. then i selected install to do a clean install and it did an HDD check. it came back saying existing ext3 partition corrupted. which only reinforces that the first ubuntu install is gone!

---

### Post by swoll1980 on 2007-08-24
im talking about when you used gparted live cd gparted works and your going to have to use it to fix this problem so what we have to do is figure out why it did not work the first time you used it. or  you can use the manual partitioning option on ubi live cd

---

### Post by jw5801 on 2007-08-24
Give the GParted LiveCD a shot (see the link in my sig.), that way you can just wipe the hard-drive and format it then reinstall. When you run GParted in Ubuntu it'll keep trying to mount any drives you've got (unless you kill gnome-volume-manager), so the LiveCD tends to work much better. Plus it's a much newer version of GParted than the one in the repos.
So yeah, get live cd, wipe drive, reformat to ext3, install Ubuntu!

---

### Post by deepblue80 on 2007-08-24
Bloor75 -
I now understand what you mean. i opened the Gparted in the live cd installation and tried to re-size and reformat the drive as ext3. it didnt go through and gave a message - drive mounted, cannot format or something to that effect. i didnt see the partion locked to answer your first question.

jw5801
i am downloading the Gparted live cd from the link in your sig. i presume i should burn it to a cd as an iso image and then run it, do a clean format and then run the Ubuntu install? Is that what you suggest?

---

### Post by jw5801 on 2007-08-24
> **deepblue80 said:**
> jw5801
i am downloading the Gparted live cd from the link in your sig. i presume i should burn it to a cd as an iso image and then run it, do a clean format and then run the Ubuntu install? Is that what you suggest?
Yup! Let us know how it goes when you format.
> Bloor75 -
I now understand what you mean. i opened the Gparted in the live cd installation and tried to re-size and reformat the drive as ext3. it didnt go through and gave a message - drive mounted, cannot format or something to that effect. i didnt see the partion locked to answer your first question.
That's the issue I was mentioning in my first post. You have the partition that you're trying to edit mounted, therefore you can't do anything to it. If you unmount it while running on the Ubuntu LiveCD, then the gnome-volume-manager process will remount it again.

---

### Post by deepblue80 on 2007-08-25
> **jw5801 said:**
> Yup! Let us know how it goes when you format.

That's the issue I was mentioning in my first post. You have the partition that you're trying to edit mounted, therefore you can't do anything to it. If you unmount it while running on the Ubuntu LiveCD, then the gnome-volume-manager process will remount it again.

to update the nice people who wrote in to help me!
1. successfully used DBAN to wipe my HDD clean but it takes ages!!!! mine took 11 hours on an 80gb ide hdd and thats using the quick erase option in DBAN

2. installed fiesty fawn successfully and whilst i am haivng issues with firefox (posted in another thread) i am using opera for now satisfactorily.

now to find myself a good irc and a torrent client and got to downloading the good stuff!!

---

### Post by jw5801 on 2007-08-25
Gaim the default IM app lets you use irc, I find it works quite well!
I use rTorrent for all my torrenting needs, it's has reasonable functionality (not quite to utorrent standards, but almost). It is a commandline type interface though, so that may be disconcerting. Else good old Azureus runs quite well I'm led to believe!

Congrats on the install, enjoy!

---

