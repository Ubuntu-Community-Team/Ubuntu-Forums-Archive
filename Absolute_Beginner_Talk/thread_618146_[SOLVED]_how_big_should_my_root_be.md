---
title: "[SOLVED] how big should my root be?"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by natehatewindows on 2007-11-20
ok i am switching my partitions around. i have mandriva and gusty. i have separate /home for both. right now both of my / are about 9 and 10 GB...is this a waste of space? seel my gparted screenshot, mandriva is on the left and ubuntu at the end, today i will be moving ubuntu and making the free space a etx3 for my pictures and music to share between mandriva and gusty.

thanks in advance!


ps 
im also going to make it so i only have one swap.

---

### Post by indytim on 2007-11-20
My recommendation is to re-size to ~5G.  Should allow ample room for growth.  I'm running about 3.16G on Kubuntu 7.10 pretty well configured.  As always, a matter of personal choice.

IndyTim

---

### Post by Paqman on 2007-11-20
5GB is fine under normal conditions. If you do some things like ripping DVDs you might find it'll create some stupidly large temp files during the process, so you'll benefit from a larger root.

---

### Post by natehatewindows on 2007-11-20
i use k9copy, should i leave it at 8 or whatever gb? i always have the files (the files it make the .iso from) and .iso go to my desktop.....and that should be on my /home right? so would i still need the temp room on / ?


thanks!

---

### Post by indytim on 2007-11-20
If you have a separate "/home" with adequate storage space, then you could still shrink your "/boot" down.  The version of K9Copy built with Kubuntu 7.10 seems to restrict writing the iso to only the "/home" folder.  If on the other hand your "/home" is located within your "/", then I'd suggest leaving things the way they are.

IndyTim

---

### Post by indytim on 2007-11-20
Sorry about that, change "/boot" to "/" :).

IndyTim

---

### Post by hyper_ch on 2007-11-20
Well, I made my / folder 20gb in size with a seperate 1gb /boot partition... the 20 Gb are approximately 2% of my total diskspace so I don't worry much ;)

---

### Post by natehatewindows on 2007-11-20
i dont have 2TB of space ;)  .......wish i did :)

---

### Post by hyper_ch on 2007-11-20
it's 1 TB actually ;)  [distributed among 4 harddisks]

---

### Post by natehatewindows on 2007-11-20
oh..2%....im a little slow i guess :)

so as far as my root being 5GB what if i download something thats 6? does firefox use temp files?

---

### Post by natehatewindows on 2007-11-20
hey you use debian too....

do you know why the debian live cd wont load x server on my toshiba satellite?

---

### Post by anaconda on 2007-11-20
5GB soungs too small!!!

My root partition is 20GB and home is 80GB. 

And now I have used  10,4GB on my root partition and 4,7GB on my home partition (it is my work machine, so no movies etc..)

I have used already more that 10GB on the "/" partition.. And I haven't  even got that much extra stuff..   I have installed lots of programs, and I admit that I havent cleaned the apt-cache or emptied the root-trash for a while. But still.. if I had only 5GB root partition I would be deep in ****..

---

### Post by Banacek on 2007-11-20
> **hyper_ch said:**
> Well, I made my / folder 20gb in size with a seperate 1gb /boot partition... the 20 Gb are approximately 2% of my total diskspace so I don't worry much ;)


The most a "/boot" partition would ever need would be 100MB and you might even be able to get away with making it only fifty or sixty but a hundred is standard just to be safe.




My "/" partition is 1.5GB (as is my "/tmp" partition). One gig probably would have been just fine. Then again my "/usr" partition is 11.5GB. My "/var" is about 6GB and "/home" is at least 90GB. I've got one gig of DDR400 SDRAM; so, my swap partition is 2GB. There's no further boost in using more than twice your RAM for your swap partition.

---

### Post by natehatewindows on 2007-11-20
ok well now im just really confused....see these are my plans:

i have a separate /home for both madriva and ubuntu to store documents and small things that i only need in that os (ubuntu for ubuntu and mandriva for mandriva).

i have / for mandriva and ubuntu (separate of course)

and all the rest of the free space im makeing a ext3 partiton for the stuff i wil use in both os's.

i guess im just not clear on what the root does and what the /home does....i mean what gets saved on them. i.e. where do system settings, program files, and stuff i save to my desktop for example go?

a good explatation or a link would be dandy.

thanks again guys!

---

### Post by natehatewindows on 2007-11-20
> nd I admit that I havent cleaned the apt-cache or emptied the root-trash for a while. But still.. if I had only 5GB root partition I would be deep in ****..

how do i do these things? and just wondering...i have NEVER heard of anyone using more root space than home space. are you sure your saving your files on your /home?

---

### Post by anaconda on 2007-11-20
> **natehatewindows said:**
> how do i do these things? and just wondering...i have NEVER heard of anyone using more root space than home space. are you sure your saving your files on your /home?

Well. actualy I noticed that 2,8GB of the 10,4GB was on a different partition (usb-memory) but still "/" takes a lot more than home.
The reason that "/" takes more than home is that this is my work machine, so there isn't any torrent-downloads, movies, mp3, DVD-rips on this machine.. And I think the >4GB in home is quite a lot.. work documents, pictures, a few linux install CD:s etc..(I should clean unnecessary files more often.)

And because I install lots of programs, and almost all of them go  to the root partition it takes space.   

to empty roots trash: (these remove the whole directories, but they will be recreated as soon as they are needed.)
sudo rm -R /root/.Trash
sudo rm -R /.Trash-root 

And to clean apt cache..
sudo apt-get clean

---

### Post by Sef on 2007-11-20
> And because I install lots of programs, and almost all of them go to the root partition it takes space.

to empty roots trash: (these remove the whole directories, but they will be recreated as soon as they are needed.)
sudo rm -R /root/.Trash
sudo rm -R /.Trash-root

And to clean apt cache..
sudo apt-get clean

```
sudo apt-get autoremove
```

to get rid of old dependencies.

---

### Post by natehatewindows on 2007-11-20
SEF...

you have helped me before.....how big sould my / be? thanks! :)

---

### Post by natehatewindows on 2007-11-20
home@home-laptop:~$ sudo rm -R/root/.Trash
rm: invalid option -- /
Try `rm --help' for more information.
home@home-laptop:~$ sudo apt-get clean
home@home-laptop:~$ sudo rm -R/.Trash-root
rm: invalid option -- /
Try `rm --help' for more information.

---

### Post by hyper_ch on 2007-11-20
> **natehatewindows said:**
> home@home-laptop:~$ sudo rm -R/root/.Trash
home@home-laptop:~$ sudo rm -R/.Trash-root


Between the -R and the "/" there's a space " " needed.

---

### Post by natehatewindows on 2007-11-20
:) i feel dumb

---

### Post by Sef on 2007-11-20
> you have helped me before.....how big sould my / be?

I usually make mine 8 - 10 gb just to have extra room.   You can make it smaller, but with the size of the hard disks today, what take a chance on making it too small.

---

### Post by hyper_ch on 2007-11-20
you know, you could just coyp'n'paste commands ;)

---

### Post by natehatewindows on 2007-11-20
i could just copy/paste but then i dont learn as well.....i am still trying to learn all this stuff and if i type them maybe i will remember them better or something ???

i think i will just make them both 8GB to be safe, that gives me extra room for my ext3 sahred partition and room incase ubuntu and mandriva need to grom a little.

thanks for all the help.

maybe could someone tell me exactly what the / is used for and what the /home is used for. i.e. when i install things, set settings, rip a dvd....download...you get the point.  thanks!

---

### Post by hyper_ch on 2007-11-20
The "/" is the root folder... that's the most basic folder in the whole Linux File System organisation.

/home means it's a folder named "home" can it's parten directory is "/". In the /home folder normally all the user files are stored e.g. your configuration settings for various programs, your documents, music, video and so on... ( /home/USERNAME )

---

### Post by Banacek on 2007-11-20
The reason why "/" is larger on some peoples' systems is because their directories such as "/usr," "/var," "/tmp" and sometimes even "/home" are not set up as separate partitions. Some don't even have a separate swap partition; which can be very inefficient indeed. If you don't have separate partitions for those directories, then they will be contained within your "/" partition. I have separate partitions for "/boot," "/usr," "/var," swap, "/home" and "/tmp" as I feel it lends to more stability and at times I allow family to use my machine.

Most of your applications are installed in "/usr" but a few of your core executables and shell scripts such as gunzip, cp, archdetect, chmod, chown, su, bash, dash, csh, gzip, more, ls, mv, cat, dmesg, kill, mkdir, mknod, nano and such can be found in "/bin." Typically, "/bin" takes up less than 5MB. My "/usr" partition is filled to a bit under 3GB but I've made it rather larger than that to accomodate new installations as I go along (even so, it might still be a bit over-sized). A few other chores are handled from "/sbin" but that seems to be less than 9MB. The "/etc" has some system settings and configuration files. Six to seven MB being typical. The "/lib" is under 150MB. My "/proc" seems to take up a touch less than 900MB and "/sys" is about 428MB. The remaining directories on my "/" partition are very small indeed; some being mere KBs in size or even empty.

The "/var" directory is for handling multimedia, web content, file sharing and webserving capabilities. It has a cache and another "/tmp" to help with streaming multimedia and perhaps for some downloading. Currently, my "/var" partition is filled to less than 700MB but I've made it six GB should I wish to have a small FTP server in the future.

My "/home" parition is about 90GB for all my documents, pictures, videos and such. The swap partition is 2GB to match my one GB of DDR SDRAM. I have a "/tmp" partition of 1.5GB which is sufficient for most downloading purposes. Hence, with "/boot," "/usr," "/var," swap, "/home" and "/tmp" all being separate partitions I really have no need for my "/" partition to be much larger than 1.5GB.

So, as to how much space you should allocate for your root partition, it depends on the manner in which you set your system up, really.

---

### Post by Banacek on 2007-11-21
Another thing, I find it very difficult to believe that my "/proc" directory is almost 900MB. I used to have an install of Fedora 7 with a one GB "/" partition that was filled to only about 600 or 700MB. Ubuntu has a reputation of being more streamlined in comparison to Fedora. As "/proc" would be within my "/" partition there's no way it could be that large. Although Fedora has some dead wood that it could stand to have cleared out, it also has a few nice things and perks that you'll find missing from Ubuntu. It seems that one of those things is Fedora has the ability to report (at least to us humans; the machine doesn't need a report on everything and just "knows" what it is or what to do with it) more accurately on some of the more irregular file and data types or some things that show up as not even being files. Perhaps Ubuntu just doesn't know as well what to tell us about those and in the confusion of trying to interpret it to people the size gets exaggerated or even doubled. I believe the same thing may be going on for "/sys" which also lies within the root partition. Hence, the amount the "/" partition is filled may actually be less than what it appears.

---

### Post by natehatewindows on 2007-11-21
wow....thanks a lot....that cleared so many things up for me :)

---

