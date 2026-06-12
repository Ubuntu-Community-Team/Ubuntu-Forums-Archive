---
title: "Memory problems"
date: 2006-02-18
forum: Absolute Beginner Talk
---

### Post by lucidite on 2006-02-18
Hi,

I currently have a 120GB drive. However I was doing something today that gave me an error message saying that I don't have enough memory.
I opened up "KDiskFree" & it tells me that:
/dev/hda3 has 18.6GB, of which most is used and
/tmpfs has 251.9MB.

Since both numbers don't add up to 120, I seem to have a problem...
How do I find out where the "missing" memory is?

---

### Post by nalmeth on 2006-02-18
Is ubuntu the only partition on your drive? When you installed, did you erase and use the whole disk? Or create a small partition for it?

gparted should be installed already (i think) but if not, open terminal

sudo apt-get install gparted
gparted

this should give you some detailed info, report the results

---

### Post by lucidite on 2006-02-18
[QUOTE=nalmeth]Is ubuntu the only partition on your drive? When you installed, did you erase and use the whole disk? Or create a small partition for it?
[/QUOTE]

Ubuntu is the only thing running on this box -- I should have 3 partitions, one for my home, one for swap & one for my program files. I have to admit I'm not 100% sure of the partitions as it's a friend that installed Ubuntu & configured it. 
And didn't need to erase it since it was a brand new drive - Window's wasn't even installed.

Ran GParted & this is what it told me:
Partition        Filesystem    Size (MB)  Used(MB)  Unused(MB)   Flags
/dev/hda1     ext3                 9,994     3,430       6,564
/dev/hda2     extended         87,848
/dev/hda5     linux-swap         1.992        ---          --- 
/dev/hda6     ext3                84,992    27,410    57,582
/dev/hda7     linux-swap            863        ---          ---
/dev/hda3     ext3                19,399    12,405      6,994        boot

Hope this is what you were  looking for!

(oh, and how can I get a screen shot of my desktop? That was next time I can simply take one?)

---

### Post by nalmeth on 2006-02-18
Yeah, this seems setup in a funny way. I'm kinda busy at work right now, but I'm getting off soon, and will try to help you out when I get home. 

If you're using gnome, you can add a snapshot utility to your panel, just rightclick on panel, and click -add to panel- and find the util.

I use ksnapshot, even in gnome. Its really good.

Be Back soon!

---

### Post by lucidite on 2006-02-18
[QUOTE=nalmeth]Yeah, this seems setup in a funny way. I'm kinda busy at work right now, but I'm getting off soon, and will try to help you out when I get home. 

If you're using gnome, you can add a snapshot utility to your panel, just rightclick on panel, and click -add to panel- and find the util.

I use ksnapshot, even in gnome. Its really good.

Be Back soon![/QUOTE]

Thank you! 

One more thing I know how to do in Ubunto!

---

### Post by nalmeth on 2006-02-18
> /dev/hda1 ext3 9,994 3,430 6,564
/dev/hda2 extended 87,848
/dev/hda5 linux-swap 1.992 --- ---
/dev/hda6 ext3 84,992 27,410 57,582
/dev/hda7 linux-swap 863 --- ---
/dev/hda3 ext3 19,399 12,405 6,994 boot

I can't understand why your harddrive is partitioned like this. You should ask your buddy what is up with this. Did he install another distro aswell? Or two?

A regular ubuntu hardrive will have one ext3, one swap, and one extended. Your swap should be about the size of your ram.

There are a couple of things you can do:
-Figure out which partition is actually the ubuntu you log into, get rid of the other ones, and resize the right one to the full extent.
-Create a partition for your home folder, remember what apps you have installed, and redo the install. Having a /home partition has advantages and disadvantages. In this case, you'll save all your current settings. This will require assistance. 
-Start over from scratch. If you don't have one, grab the breezy install image, burn it to disk, and install from scratch, telling the installer to "erase entire disk". This would be a good experience to see the install first hand. I would not recommend this if you have special hardware you needed your friend to setup for you or something.

Either way, get a hold of buddy and figure out what happened in the install, and make a decision from there.

BTW --> hockey fan? Theodore out 6-8 weeks! Slipped on driveway!! Unbelieveable upset by Swiss team! I don't understand it!

"My spoon is too big!"
"I'm a banana!"

---

### Post by lucidite on 2006-02-18
[QUOTE=nalmeth]I can't understand why your harddrive is partitioned like this. You should ask your buddy what is up with this. Did he install another distro aswell? Or two?[/QUOTE]

No, that was my fault actually -- when I upgraded from Hoary to Breezy, I had to reinstall it from scratch. So that's my fault... (Hey, I am a newbie after all!) I let it reinstall itself, but could the fact that we had partitionned it manually before cause the problem?

[QUOTE=nalmeth]There are a couple of things you can do:
-Figure out which partition is actually the ubuntu you log into, get rid of the other ones, and resize the right one to the full extent.[/QUOTE]

I think this might be the best solution.
How would I do that? I know already that my /home has 20GB from checking it
with KDiskFree so I'm assuming that /dev/hda3 would be my /home, right?

[QUOTE=nalmeth]-Create a partition for your home folder, remember what apps you have installed, and redo the install. Having a /home partition has advantages and disadvantages. In this case, you'll save all your current settings. This will require assistance. 
-Start over from scratch. If you don't have one, grab the breezy install image, burn it to disk, and install from scratch, telling the installer to "erase entire disk". This would be a good experience to see the install first hand. I would not recommend this if you have special hardware you needed your friend to setup for you or something.[/QUOTE]

I was planning on getting him over here soon and reinstalling everything, but I haven't gotten around to doing it yet...

[QUOTE=nalmeth]BTW --> hockey fan? Theodore out 6-8 weeks! Slipped on driveway!! Unbelieveable upset by Swiss team! I don't understand it![/QUOTE]

No, not a hockey fan -- one of the few people in Montreal who couldn't tell you if/when the Canadians won...
(But the Swiss won? I'm in shock!)

---

### Post by nalmeth on 2006-02-18
Living in montreal, not a hockey fan.. I thought it was a given.. I guess I'm another ignorant westerner! Oh ya, its 'les Canadien's', not canadian's, right? I know some montrealers who would freak out about that. 

I don't want to tell you to format, resize anything specifically, because you need to be 100 % sure that you've got the right partition(s), and you know exactly what you want to do with it all. Also, because I haven't done this before, and wouldn't want to assume what steps you should take. Essentially, you'll be using gparted, or one of its cohorts (partman, fdisk, cfdisk are some others). Partitions need to be unmounted to resize them.
As far as I know, it is safe to resize ubuntu partitions, but I won't guarantee that (as opposed to windows partitions, were you *need* to defrag). Naturally, the first thing you should do when considering the partitioning process is backup your personal data, in case of unforseen problems. 

Before you take a run at this, I would recommend doing some reading about the whole process, and have a quick chat with your friend too.
Google for some topics similar to your situation, and do what you can to be sure you've got the right partitions, and you know what to do with them. And since you backed up your data, if something goes wrong, all you've lost is some time, and you'll have gained some knowledge and experience! Sometimes you have to touch the fire to know how hot it is! If you choke too much space out of your home folder, you will not even be able to log in. I don't want to make this seem like a minefield, but things can go wrong.
Maybe first you would just want to shrink some of the other partitions, to get a hang of the program, and to be able to know for sure what to keep and what to toss.

I am very busy today or I would help you more directly, but I will bookmark this and check back to see how its going.

---

