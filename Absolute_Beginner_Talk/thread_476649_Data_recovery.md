---
title: "Data recovery"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by kingfoot on 2007-06-17
So i have 3 hard drives.

1- 250gb
1-120gb
1-10gb

I was using windows vista for a while and decided to switch back to xp pro. the drives were split up like this before i installed xp again;

C-200gb - unpartitioned-37gb
E-70gb (vista installed here
D-40gb

So i decided to clean it up a little. first i formatted the 120gb drive to be the full 110 usable in 1 partition. Xp does its thing (when booted from disk) and it restarts to finish install. I get the error "A disk read error occurred" so then i formatted the 37gb space and got the same message. so i installed my 10gb drive, and installed xp just fine on it. now, my 110gb drive is readable in xp, but the 233gb drive (usable space that is) is showing as just 37gb total, and i have to format it to use it. The 200gb are missing, and have all my pictures and music that i need.

So i have an idea, use my ubuntu live cd to get the files. I boot up the disc, and low and behold i can see my files! however, when i try to transfer the 70gb worth of files to my readable 110gb drive, it tells me i dont have permission to do so. How do i transfer these files!? Is there a repair command i can use with the windows disc (recovery console off the disc) that can fix the drive and be read in xp? or can linux do it? i think its important to note that i can not install ubuntu and add ntfs read/write support as ubuntu wont connect online.

---

### Post by allix on 2007-06-17
No permissions huh? You could try copying them as root-user. Just press alt+F2 and type "gksudo nautilus" and the copy the files.

EDIT: And remember to mount another HDD, don't copy the files to the home-folder on the live-cd because you will run out of RAM quite fast that way. :)

---

### Post by FleetAdmiral74 on 2007-06-17
Hehe, this guy has 16 posts. Lets assume he is new. 

Telling him to just run in root and move files around, probably not the best idea! ;)

---

### Post by allix on 2007-06-17
> **FleetAdmiral74 said:**
> Hehe, this guy has 16 posts. Lets assume he is new. 

Telling him to just run in root and move files around, probably not the best idea! ;)

That doesnt matter since he will be running from a CD and not an installed system. I don't think he'll f-up the live session. And Windows is root/admin all the time so there's no difference there.

---

### Post by kingfoot on 2007-06-17
ok, I had restarted the computer when the live cd wasnt transferring files, and I booted into xp again. (then i came and posted this) and once I got your response, I restarted and booted the cd again. It booted up all fine, but this time I looked and saw only my 110gb drive, the 10gb drive, and the filesystem. the other drive was missing! and Gparted showed the 233gb drive unformatted... :'( im booting into the cd again after booting windows one more time, to try it again.

also, how would i do this? "And remember to mount another HDD, don't copy the files to the home-folder on the live-cd because you will run out of RAM quite fast that way."

---

### Post by ryanVickers on 2007-06-17
> And Windows is root/admin all the time so there's no difference there.Ha ha!  It's true!

Type "sudo mount /dev/sda1" (1, and even "sda" would be replaced by the real name (shown in gparted)

---

### Post by allix on 2007-06-17
> **kingfoot said:**
> also, how would i do this? "And remember to mount another HDD, don't copy the files to the home-folder on the live-cd because you will run out of RAM quite fast that way."

The Ubuntu live-cd stores all files and programs in the RAM during the live session. That means you'll run out of RAM fast(and ubuntu will crash) if you copy files to the home-folder. 

The solution is to copy the files from the borked partition *directly* to one of the other harddrives. To do this you have to mount the target(the drive you want to copy the files *TO*). I'm not running Ubuntu nor Gnome right now so I can't give you specific instructions. But if I remember correctly, GParted has a feature for mounting disks, look for "set mount point" or something similar.

One alternative is using the **mount** command in the terminal. First you have to create a folder, or mount point. 

```
sudo mkdir /media/target
```

Then mount the disk(replace hdXX with your harddrive/partition id, could be /dev/sdXX too)
```
sudo mount /dev/hdXX /media/target
```

Now you just have to copy the files to /media/target. Hopefully someone with Gnome/Gparted installed can give you more specific help. :)

---

### Post by kingfoot on 2007-06-17
The only problem now is, Windows isnt seeing the rest of the 200gb of space on the drive (where my files are) and ubuntu isnt seeing my files. I cant mount the partition if ubuntu isnt seeing it!

Edit: Would the fixmbr command in the windows recovery console fix that? or COULD it fix that? or the fixboot command? (just trailing thoughts as I sit here worried about loosing my data!)

---

### Post by kingfoot on 2007-06-17
ok well, windows is still only seeing a 32gb total drive (its 250...) so thats a problem, and then linux will only see the 31gb partition on that drive, the rest is unallocated space (200gb) but there ARE files on there... WHY! wont it see it!? :'( im so sad. i realized that on my ipod is holding ALMOST all my music. so thats not SO bad. however i am missing some videos that i couldnt put on it. not horrible. BUT! ALL my pictures are GONE!!!! :'(

10gb of photos. (i am a photographer) so these are all really important either career wise and sentimental wise. from my first photo, to my first sold photo, to my first photo with a new camera, to all the pics of family and friends. this saddens me to no end. but the thing is, they are still there. i know it because i didnt delete anything, and nothing was formatted where they exist. could a new install of xp see the whole drive and maybe the files? im almost desperate to get them!

---

### Post by ryanVickers on 2007-06-17
ooo, Are you *sure* ubuntu can't just mount the partition and then burn them to DVD's or something?

---

### Post by kingfoot on 2007-06-17
well i dont get how i can mount an unallocated partition! gparted sees the 250 drive as 1 partition of 32gb (which is all windows sees of that drive) and the rest isnt a partition.

---

### Post by kingfoot on 2007-06-18
Last night, I had an epiophony!

What if I formated the whole drive. then used a data recovery program that has a reputation for working, on the drive. thats the ONLY thing ive come up with.

---

### Post by kingfoot on 2007-06-18
so no one gonna comment and let me know what you think about the idea or suggest your own ideas? thats cool i guess.

---

### Post by southernman on 2007-06-18
One word... or is it two? hmmmm 

Testdisk

You can d/l the livecd of systemrescue cd, which has testdisk on it. I just recovered nearly 18gb of data from an old drive my brother thought was toast. When I called him and told him the news of getting his files, he nearly cried! *wink*

Now, I just started playing with testdisk and stumbled upon how to recover files... DO NOT ask me how I did so, couldn't tell ya.

FGS, don't format/partition anything until you have your data. Are ya crazy? *wink*

---

### Post by kingfoot on 2007-06-19
how did you undelete??? (the only reason i thought of format is because it doesnt actually delete data.)

i downloaded testdisk (xp edition) and am gonna try it. by played around with do you mean it was simple to figure out? cause im a good "played around with" type of person!!! lol, and thank you for this HOPE! however false it might end up being.

---

### Post by kingfoot on 2007-06-19
bump

---

### Post by southernman on 2007-06-19
First of all, I didn't "undelete" anything. I simply copied files that were on a hdd that is no longer of any valueable service... eg - can read from but not write to. 

I have no faith in using testdisk in windows. <hint>It's not testdisk that I have qualms with. You should consider using the livecd I mentioned earlier, or installing testdisk in a linux distro <Ubuntu> of your choice.

While it's true that formatting a partition/drive doesn't actually erase data, the more you write on it could make the data unrecoverable. It's your data so do as you like.

It was pure happenstance that I discovered being able to retrieve the data. Had been tinkering with old dead hdd(s) seeing if they could be resurected. 

Afterall, it's only false hope anyway, right! *raspberry*

---

### Post by kingfoot on 2007-06-20
well im gonna burn the systemrec cd and ill boot it. ill try it out. does anyone else have any other suggestions incase it doesnt work?

---

### Post by kingfoot on 2007-06-20
no other suggestions anyone?

---

### Post by az on 2007-06-21
Use parted to try to look for lost partitions on the drive.

sudo parted /dev/whatever


rescue START END

where start are where you tyhink the beginning of the partition was and END was the end.  Just put zero and the size of the whole disk if unsure.  If it finds what it thinks is a partion, it will offer to add it to the partition table.  Say yes.  When it's done, quit and see if you can mount the partition.

If not, use foremost to try to recover jpegs.  You can also try recoverjpg


sudo apt-get install foremost recoverjpeg
[http://ubuntuforums.org/showpost.php?p=2400566&postcount=3](http://ubuntuforums.org/showpost.php?p=2400566&postcount=3)

recoverjpeg:

sudo recoverjpeg /dev/whatever

never mind about the filesystem, both those toold just look for files, without using the filesystem.  You will end up with many many files, as intact files are on your drive even if you have deleted them and formatted the filesystem.




You will need another drive onto which you will put the recovered files.

---

