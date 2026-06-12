---
title: "Hoary to Breezy Problem - Help"
date: 2006-05-08
forum: Absolute Beginner Talk
---

### Post by KeyboardJockey on 2006-05-08
:sad: 

HI I wonder if I can get some help with a really brain numbing problem.  I had a dual boot system with win xp and hoary and breezy installed - no problem. It started playing up hanging in windows and not starting at all in breezy or hoary.  All I was getting was the message 'not syncing' 'kernel panic' 'attempt to kill initdt'

The HD was starting to make some noises so I assumed that the problem was withthe hard drive.  I got a new hard drive and have at last managed to load hoary onto the new drive.  I've set the old drive as a slave and I'm trying to install breezy ontothe new drive so I can use the 'Disks' facility in admin to extract my data from the old drive so that I can disconnect it.

However, I've got the 5.10 iso disc that I made previously and I can't for the life of me work out out how to install it.  Ive tried to use add CD in synaptic and it doesn't recognise the disc and I get the error message 'not a debian disc'.  It then refuses to eject the disc nd I have to restart. 

Is there any way to upgrade to breezy using the terminal window?

There is no way for me in hoary to access the other drive to get my data out except by using breezy as far as I can make out.

What makes it worse is I've got friends who are windows users saying 'it serves you right for using a bogus operating system'  I don't want to lose face andhave to go crawling back to micro$oft.

can any one advise on this please.

many thanks in advance.

---

### Post by aysiu on 2006-05-08
[QUOTE=KeyboardJockey]
Is there any way to upgrade to breezy using the terminal window?[/quote] Yes. Type ```
sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
wget -c http://www.psychocats.net/ubuntu/breezy.list
sudo cp breezy.list /etc/apt/sources.list
sudo apt-get update
sudo apt-get dist-upgrade
```

> 
There is no way for me in hoary to access the other drive to get my data out except by using breezy as far as I can make out. You can always access another drive to get the data out unless the hard drive is somehow physically damaged. Do you know what the partition table location is of the drive? Well, let's assume it's /dev/hdb1, for the sake of this example. In Hoary, type ```
sudo mkdir /recovery
sudo mount -t ext3 /dev/hdb1 /recovery
sudo chown -R 775 /recovery
``` Then, your old drive should be in a folder called /recovery--just copy over what you need.

By the way, there's no point in "saving face" with your friends. If they're ignorant enough to think your problems stem from "using a bogus operating system," they would find some other excuse to hate Ubuntu, even if you weren't having any problems.

---

### Post by KeyboardJockey on 2006-05-08
Thank you so much for this I shall do this tonight. :) 

As soon as I update from Hoary to Breezy I'm going to delete the Hoary programme as having the two OS's on the same drive may have contributed to problems with the other drive.

I'm sure I can find out on here how to delete the old OS.

---

### Post by adam.tropics on 2006-05-08
As far as I am aware you don't need to delete anything as the 'dist-upgrade' basically upgrades your environment installing 'replacement' packages. You may want to uninstall (via terminal or synaptic) any kernels you are not using, though they won't cause any problems, they just waste space.

As for your friends, I would have to agree with Aysiu, and as a Dapper/Xgl/Compiz user (as I *think* Aysiu is also), stick with Ubuntu and Linux. The future is looking pretty incredible. Because of the way Linux and by extension, Ubuntu is developed, we have an extremely solid foundation, upon which everything is possible, and quickly! Enjoy Breezy, but remember, not long till Dapper official release, and it's already extremely impressive. Fastest successful linux graphical install I've ever seen!

---

### Post by steve.horsley on 2006-05-08
There should be something on the Wiki about upgrading Hoary to Breezy. It may go someting like:
> sudo apt-get dist-upgrate
sudo apt-get update
sudo apt-get upgrade
But I can't remember for sure.

Dapper is due out in a few weeks. Flight 7 test version is available for download, if you're feeling adventurous.



> What makes it worse is I've got friends who are windows users saying 'it serves you right for using a bogus operating system' I don't want to lose face andhave to go crawling back to micro$oft.
Ask them what the command is to upgrade from Win2k to XP.

---

### Post by adam.tropics on 2006-05-08
> Ask them what the command is to upgrade from Win2k to XP.

One thing they'll have in common, both commands start with '$' !!

---

### Post by gr0kzer0 on 2006-05-08
> Ask them what the command is to upgrade from Win2k to XP.

> One thing they'll have in common, both commands start with '$' !!

Hehe, I like that!

I'm not so keen though on your worries about your friends gloating over you abandoning this "bogus operating system".

Just remember... _they_ are the ones using the "bogus" system. And if, God forbid, something ever happened that forced you to (temporarily) stop using Ubuntu, make sure you tell your friends that - that you have had to temporarily stop using Ubu... but that you'll be reinstallling very soon... something that's easy, and free, unlike with _their_ bogus system!

---

### Post by adam.tropics on 2006-05-08
..Plus, i'd put money on it that it'll still be you they come running to for help when they either a)run into wintrouble, or b)realise they've just wasted $350 on an os (if ms actually fully release the thing!)that won't run to its full potential on their 1 year old machines!!!
But basically be comfortable in the knowledge that you're running a safe stable and evolving system.It's not for everyone I guess. their loss.not your problem!

---

### Post by KeyboardJockey on 2006-05-08
[QUOTE=aysiu]Yes. Type ```
sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
wget -c http://www.psychocats.net/ubuntu/breezy.list
sudo cp breezy.list /etc/apt/sources.list
sudo apt-get update
sudo apt-get dist-upgrade
```

.[/QUOTE]


Tried this.  ](*,)  No joy.  All I get is a monochrome screen with mush after a total of 6 hours plodding at this tonight.  I'm getting error messages saying 'LC' problems and locale prolbems.  It refuses to boot Breezy despite going through the procedure above. I'v re installe hoary so that could actually get a working system and wipe the new drive so that there would be nothing left on there that might have caused me problems.

I've been using ubuntu since february and it still doesn't do what I need it to do (won't print either despite much faffing around).  I'm beginning to wonder if there is something basic that I'm doing wrong.  I've disconnected the old drive so that it only writes to the new drive when I install hoary but I really need breezy as hoary will not be suported for long.

---

### Post by KeyboardJockey on 2006-05-08
[QUOTE=steve.horsley]There should be something on the Wiki about upgrading Hoary to Breezy. It may go someting like:

But I can't remember for sure.

Dapper is due out in a few weeks. Flight 7 test version is available for download, if you're feeling adventurous.
.[/QUOTE]

I aint going to touch dapper - I'm having too much trouble with breezy. :mad:

---

### Post by KeyboardJockey on 2006-05-08
[QUOTE=steve.horsley]There should be something on the Wiki about upgrading Hoary to Breezy. It may go someting like:

But I can't remember for sure.

.[/QUOTE]

No that just goes to look for hoary again :mad:

---

### Post by catlett on 2006-05-08
[http://www.ubuntuforums.org/showthread.php?t=92672](http://www.ubuntuforums.org/showthread.php?t=92672)
Try this thread. It will basically give you a new resource list. Once you edit in your new list you can run the upgrade command and you will have hoary replaced by breezy. All you have to do after the source list change is ```
sudo apt-get update
```
And then ```
sudo apt-get dist-upgrade
```
That will get you from hoary to breezy.

---

### Post by aysiu on 2006-05-08
[QUOTE=KeyboardJockey]Tried this.  ](*,)  No joy.  All I get is a monochrome screen with mush after a total of 6 hours plodding at this tonight.  I'm getting error messages saying 'LC' problems and locale prolbems.  It refuses to boot Breezy despite going through the procedure above. I'v re installe hoary so that could actually get a working system and wipe the new drive so that there would be nothing left on there that might have caused me problems.[/quote] Maybe ```
sudo apt-get install locales
``` might help?

---

### Post by adam.tropics on 2006-05-09
I am gonna backtrack a bit here. (re-read your post!). Please someone correct me if I am wrong, but I seem to remember one could add the breezy cd to your sources.list,,,,,,The Dapper cd, no, but Breezy, I believe so.  Anyway, that said, are you not able to boot to cd? In your shoes, bandwidth allowing of course, I have to admit I'd be inclined to re-download the iso, re-burn it, and try booting to it and so install Breezy straight up, without going via Hoary.
It seems an unnecessarily arduous way of doing it to me...

I don't know your location, but if you're bandwidth is an issue, and you are anywhere near Australia I can happily send you a tested and working ShipIt Ubuntu cd.

---

### Post by KeyboardJockey on 2006-05-09
I'm going to try the locales  thing above but I'm wondering if maybe I should look at another distro.  The thing is I like using Ubuntu (when it actually *&(*&*9 works that is).

The 

sudo apt-get install locales 

command  do I do this after I've wiped the hard disc again and re installed hoary or do I not wipe and reinstall and just run this in hoary as it is.  Will this allow me to download breezy using the instructions earlier in the thread?

thanks

---

