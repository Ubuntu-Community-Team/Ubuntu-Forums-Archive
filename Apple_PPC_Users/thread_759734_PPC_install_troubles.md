---
title: "PPC install troubles"
date: 2008-04-19
forum: Apple PPC Users
---

### Post by richiewrt on 2008-04-19
Ok, I just purchases a powermac g4 867mhz w/ 256 ram and 40gb hd. I am tring to install ubuntu and I am having no success whatsoever. I first tried the live cd for 6.06 and it just continually hangs and gives me a blank white screen even when i use the live video=of*** command it says when it first tries to load. I thought ok, I will try the 7.10 alt install cd. Everything seems to go fine until it attempt to partition the disk and for some reason it hangs every time when trying to create the / partition. It immediatly jumps to 33% and sits there. I have installed ubuntu several times on Intel pc but never on a mac. Is there something that I am missing or not doing correctly. I have tried using both the option of using the full disk and also reloaded osx 10.4 back on a 6gb partition and leaving the rest free space and using that free space. Hangs at 33% every time.  Any suggestions?  Thanks

EDIT** This is also jst going to be a simple server install for my personal testing so if there is a ppc server disk out there could someone point me to it?

---

### Post by stream303 on 2008-04-19
Don't sweat it hanging at 33%.  Just walk away for a awhile.  It is still doing something, and I wish that the installer had a "spinner" along with a gas gauge.  Same thing happens in Debian too.  It's a test of your sincerity to install. :)

You can grab the Feisty server install here:
[http://cdimage.ubuntu.com/ports/releases/7.04/release/](http://cdimage.ubuntu.com/ports/releases/7.04/release/)

Personally, I like to see boot messages rather than the ubuntu logo, so I usually just add this at the second-stage boot: prompt
```
Linux nosplash
```

---

### Post by richiewrt on 2008-04-19
i wish that were the problem, but I let it sit for about 5 hours (i went to bed and got back up) and it didn't move, and no movement from the cd drive. I have now added to my list fedora 8 (white screen) ubuntu 6.06 server (white screen) xubuntu 6.06 (white screen). Now I'm downloading 7.04 server and alt to try, hopefully one will work. Still looking for a solution.

---

### Post by stream303 on 2008-04-19
That's odd, especially for one with an nvidia video card.

Since it seems to happen across all distros, and the use of Linux video=ofonly doesn't work, I wonder if it is a hardware thing?  Have you zapped the pram/nvram, or done any smu/pmu resets - who knows what the original owner had in there before, and maybe the system doesn't know about the addition/removal of hardware?

[http://docs.info.apple.com/article.html?artnum=2238](http://docs.info.apple.com/article.html?artnum=2238)
and
[http://docs.info.apple.com/article.html?artnum=86760](http://docs.info.apple.com/article.html?artnum=86760)

Tried the links myself and had to tell my firefox "no-script" extension to temporarily allow apple.com so I could see the graphics...

---

### Post by richiewrt on 2008-04-19
i just tried zapping the pram, thanks for the link, but there appears to be no change. I lock up on any live cd i try to use, ubuntu or otherwise, and can only get to the 33% partitioned for / with the 7.04 alt installer cd. On a side note, it took me several times to get to that point with the alt installer as it kept hanging up a various times prior to attempting to format the disk. I don't know what the problem is, I installed os x 10.4 fine so I don't think I have a hardware issue, but i suppose its possible. any other suggestions? possibly a different distro?

---

### Post by stream303 on 2008-04-19
Live-cd's have been problematic for some, have you tried the "alternate" images, which are install-only are don't need as much ram?  I think you got to the partitioning stage once, so I'm scratching my head too...

Is everything else unplugged - no external firewire disks attached, or any usb sticks attached, etc?

It shouldn't matter, but what keyboard and mouse are you using?

---

### Post by richiewrt on 2008-04-19
Nothing connected to the mac except for the monitor keyboard and mouse. I just tried a different hd, thought maybe the hd was bad, but I am getting the same problem. This is using the alt install cd (the only one I can get to get to any type install. Makes it all the way to the partitioner, i choose use entire disk, and it starts doing its thing and immediatly goes to 33% the second it switches to that screen, then just sits there. same place I left it for 5 hours last night. i'm pulling my hair out here. I have installed ubuntu on like 4 differnt pc's with no prob. Didn't realize it would be such a headach on the mac.

---

### Post by oswaldkelso on 2008-04-19
I have a similar machine and have had the dreaded "white screen of death"  If  the usual pram zapping battery removal fails I always resort to unplugging hard drives My scsi is the main culprit it sort of lock its self up once started  no more white screen.  I notice if the machine has been swittched off for long periods it can struggle to boot  and I have to unplug hardware. Some times I have to remove all connecting cables before it will boot but once up runs fine for weeks.

---

### Post by Caraibes on 2008-04-19
If I were you, I would install Debian Testing. It officially supports PPC. I too tried at first Ubuntu, but was really disappointed by the buggy PPC release. Once I had Debian, things went much better...

Get your iso here and install it !
[http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/powerpc/iso-cd/](http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/powerpc/iso-cd/)

---

### Post by richiewrt on 2008-04-19
Well, i took your advice and decided to try debian. Install appears to be going the same. Stuck at 33% on the partitioning.  Going to let it sit for a while, but I don't here any disk movement cd or hd. After that, may be time to just reinstall os x and use it as my webserver, but I really wanted to avoid that.

---

### Post by oswaldkelso on 2008-04-20
Have  you tried using a mac os cd/dvd disk to format your drive? then install ing to an already empty drive.

---

### Post by Caraibes on 2008-04-20
Rich, you might have some hardware issues. My advice wasn't of any help, then. 
Sorry.

---

### Post by richiewrt on 2008-04-20
I have tried formatting through the os x install disk with no problems, I can install osx without any problems on either of the 2 hard drives I have tried. For some reason, It just will not partition through the linux installation process. The utility in os x will not allow me to format an entire hd as freespace, but I have tried using every format option there, and then trying to use the entire disk during the install. I don't know what to do. I really don't think it is a hardware issue since os x installs fine on either disk. At this point I just don't know.  I am now working on configuring the apache server that comes with os x so I guess that is what I am going with. I really wanted linux on here, but oh well at this point it isn't worth the headach. I have maybe 15 different distro's burned to cd sitting in front of me that should have worked and spend prob close to 40 hours on this. :( Oh well, I still have ubuntu on my pc

---

### Post by oswaldkelso on 2008-04-20
> **richiewrt said:**
> I have tried formatting through the os x install disk with no problems, I can install osx without any problems on either of the 2 hard drives I have tried. For some reason, It just will not partition through the linux installation process. The utility in os x will not allow me to format an entire hd as freespace, but I have tried using every format option there, and then trying to use the entire disk during the install. I
Just checking that you did look under the partition section and not just the erase section of the disk utility  options. I was not 100% sure from your post. If its just disk utility wont let you create just 1 free space partition (whole disk)You could create 2 either  sacrifice some small space or set aside some for  a  linux  partition to use later. 
Just clutching at straws really but you never know.

---

### Post by stream303 on 2008-04-21
I think I found your trouble - that machine seems to have multiple hard drive controllers, which yaboot currently seems to have problems with, even though your machine only came with one drive installed:

[http://www.everymac.com/systems/apple/powermac_g4/stats/powermac_g4_867_dp_mdd.html](http://www.everymac.com/systems/apple/powermac_g4/stats/powermac_g4_867_dp_mdd.html)

A yaboot developer has submitted a patch, but it may or may not show up in time for hardy release - possibly for the next spin, 8.04.1.  See pxwpxw's response in:
[http://ubuntuforums.org/showthread.php?t=758301](http://ubuntuforums.org/showthread.php?t=758301)

This might be the reason why no distro seems to work.  Hang in there - looks like help is on the way, but it may be a little while longer...

---

