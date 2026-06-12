---
title: "organizing data, harddrives, partitions"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by stairwayoflight on 2006-08-06
hi,

does anyone have any ideas for me?

i have done ok getting things to work, but its not as clean and organized as it could be.

right now i have a 40g and a 200g hd. ubuntu is installed on 40g, along with my home folder. i have media and docs in my home folder, and some on my 200g. both are ext3.

i would like to put my media in my 200g, possibly have docs on both drives for backup.

honestly, stuff is all over the place, it looks like shit. also i need to figure out a plan to have everything in a good place, so i can reinstall ubuntu and have everything clean, neat, and working. right now i've got kubuntu, xubuntu, etc., but i don't fancy them so much anymore.
probably i'll do a fresh install, xorg 7 savage driver isn't playing nicely either so i might downgrade x or go back to breezy, though i prefer dapper.

can someone reccommend a good scheme for drives, partitions, and folders? i am pretty much the only user, my girlfriend uses the internet sometimes. my media (music and vids) is really important to me. i am thinking of setting up a samba share to share with a win box in the house, maybe share with my gf's ibook too if i can.

also, before reinstalling and playing with my data, folders, etc., i'll probably have to make all my files on the drive world-writable, i'm not sure how. i can't read some folders unless i am root.

also, if i'm going to reinstall, how much stuff can i make persistent into the new install? can i copy my .mozilla directory and stuff like that? if so, how? (i don't use evolution yet)

thanks for the help

---

### Post by orb9220 on 2006-08-06
Well I have a 120GB that is fat32 to share with XP. Here is my folder structure.

Folders
--------

Downloads - Everything I download goes there where I can install from.
Temp - Where I can uncompress stuff to.

Images - with folders created for subject type Landscapes,Family,Etc..

Multimedia - Music with folders by genre>Artist>Album
.........    Videos with folders by subject
.........    Movies with ISO's of movies ripped to be burned

Ubuntu - sub-Folders  Configs for all system files like xorg.conf,fstab
---------             Themes
---------             wallpaper
---------             programs like deb's and windows .exe to use with wine
---------             Docs
---------             Apps-Backups for backing up apps like firefox
---------             System-Backup for compressed backup of ubuntu

Spend the time to create a folder structure before you need them. Later is not a good idea. Always in a hurry to do it in a meaniful way. And just dumping and I'll do it later never works for me.

Hope this helps

---

### Post by wombat20 on 2006-08-06
How you organise it all is really up to you.  There are some guides for how much to dedicate to swap (is it twice your RAM size?).

I'd say the best way is to back everything up onto either another HD or a bunch of DVDs or CDs, or whatever you can get hold of.  The .mozilla* files are available in your home directory and if you press Ctrl+H you can see them.  If you copy them into your new home directory before you run Thunderbird for the first time, it should pick up where you left off.  Once you're safely backed up you can start again and do what you like.

---

### Post by Ocxic on 2006-08-06
setup you drives to use LVM then you can creat as many partions as you want. combining the space of the drives/partions

ex if you have a 40 gb and a 200 gb hard drive the  it would become  a 240gb lvm group with what ever partions you would like.

if you do this creat a sepreat partion for your /boot as ex3 grub has problem booting from lvm groups

---

### Post by stairwayoflight on 2006-08-07
@orb: thnx, that sounds good. yes you never want to wait till you have to dump before knowing where you will take that dump ;-)

@wombat: my swap is 1.6g.  i have 768mb ram. thats a little more than 2x ram. also, i have 2 7200rpm drives i believe. is it going to be faster for me to use swap on one than on the other?

@Oxcic, at this point i don't see an advantage for me to do that. but it sounds cool.

i guess it makes sense to install apps, everything on the 40 still as i have it now. what i don't know is if i should keep my home directory there and symlink to media directories in the 200, or what?

also, there are certain folders i can only access as root. i have heard someone say, use /etc/fstab correctly and i don't need to chmod anything. is there any way to easily and quickly restore permissions to my new user after the reinstall of ubuntu, though i do not have access to everything now?

also, is this a good configuration, considering in future i would like my box hooked up to the tube? (for playing, pvr is out for now.)

---

