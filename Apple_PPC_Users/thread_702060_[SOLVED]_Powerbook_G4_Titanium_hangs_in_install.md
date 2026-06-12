---
title: "[SOLVED] Powerbook G4 Titanium hangs in install"
date: 2008-02-19
forum: Apple PPC Users
---

### Post by powerbookluv111 on 2008-02-19
Hello there. This is my first post.
I have a Powerbook G4 Titanium 667 Mhz, 768mb, 30Gb, CD-RW/DVD.

I have tried to install Ubuntu 6.06 and 6.10, both with no luck. I can boot to both discs fine and launch the installer. I can also partition fine, and enter all other settings. But, in the middle of the installation it just stops at a certain percentage and thats that. In 6.10 it refuses to install past 55% in 6.06 its 37% or something around there. What in the world is going on? I know I had problems with other PPC's installing Ubuntu. Any help would be greatly appreciated! :confused:

---

### Post by stmiller on 2008-02-19
There were (are) tons of problems with those past versions of Ubuntu and powerpc. Try 7.04- most have had better success with it.

[http://cdimage.ubuntu.com/ports/releases/feisty/release/](http://cdimage.ubuntu.com/ports/releases/feisty/release/)

---

### Post by stream303 on 2008-02-20
Sometimes you just need to give it more time, although waiting an hour would be unreasonable.

Most of my installs on various drives usually look like they are hanging at 33% or so, sometimes without any drive activity and then bingo - whatever it is doing (or not doing) times out, and the install procedes.

When doing an install with the "alternate" images, you can freak yourself out if you stare at the red/blue gas gauge too long. :)

---

### Post by powerbookluv111 on 2008-02-21
I read someplace that there wasn't a 7.04 for PPC, but subconsciously knew that was wrong, and had seeen it someplace. Anyways, I found Kubuntu 7.04 and like it, so am installing it right now. I also found that letting the powerbook sit for a little bit after an error, will yield better results. I think it has to do with it overheating, which the Titanium and all G4 powerbooks are good at! 
Thanks for you help!

---

### Post by powerbookluv111 on 2008-02-21
I take that back. I still cannot get a complete install! Everytime it gets close, the machine will lock up. Right now, the mouse won't even move and it's completely stuck at 76%. Wow, Im starting to think Ubuntu isn't nearly as good as  anyone says. No matter what I do, nothing works on PPC. Ridiculous! And they want more people to use it. Ha.

---

### Post by Cows on 2008-02-21
Actually Ubuntu is a excellent distro. I have a Powerbook G4 667 Mhz , 40 GB ram, 512 MB SD-RAM and all Ubuntu distros work. Debian 4.0 works as well.

Try to clear out NV-RAM by doing the following :

Turn on the computer and when you hear the sound hold Command(Apple) + Option + O + F

When open firmware opens type the following :

reset-nvram
reset-all
shut-down

Then after that try to install.

If you want Ubuntu alone then just select "Use the entire disk" if you want Mac OS X and Ubuntu make sure that your partitions are as follows :

/dev/hda1 = Boot Partition
/dev/hda2 = Apple Partition
/dev/hda3 = Ubuntu
/dev/hda4 = Swap

for me it's 

/dev/hda1 = Boot Partition
/dev/hda2 = NewWorld Partition
/dev/hda3 = Apple Partition
/dev/hda4 = Ubuntu
NO-SWAP

check out my blog for more info

[http://fearedbliss.blogspot.com/](http://fearedbliss.blogspot.com/)

---

### Post by stream303 on 2008-02-22
> **powerbookluv111 said:**
> Right now, the mouse won't even move and it's completely stuck at 76%. Wow, Im starting to think Ubuntu isn't nearly as good as  anyone says. No matter what I do, nothing works on PPC. Ridiculous! And they want more people to use it. Ha.

I would definitely recommend you use the "alternate" text based installer rather than the live-cd.

Don't sweat the frustration - we've all been there.  I went "back to Mac" a few times just to teach Linux a lesson.  The penguin just smiled and said "you'll be back". :)

---

### Post by powerbookluv111 on 2008-02-22
Completely new problem now!
Booting the 7.10 disc! I get past the boot menu, but then it just sits at some funky white mutli-colored screen that looks like some sort of unworking visual affect. What is this, how do I get past it? I tried several of the live-nosplash-powerpc, and live video=ofonly, to no avail.

Thanks

---

### Post by BladeMelbourne on 2008-02-22
As already suggested, it is best to use the "alternate" installation CD rather than try booting the "live" CD to perform an installation.

Quite a few people also report easier installs with Feisty 7.04 than Gutsy 7.10.

---

### Post by stream303 on 2008-02-22
And don't worry about the multi-colored Ubuntu splash screen.  That's quite common to see even for successfull installs.  You can fix the splash screen later if you really desire to.

---

### Post by powerbookluv111 on 2008-02-22
Is the alternate install cd a text-based installer through command though? I am a linux newb, so I can run commands to install. I found a way to get past the strange screen, but now I can't find it again.
Also, after entering "live-nospalsh video=ofonly" at the boot menu, one it loads the initrd command line,what do I type to load the Live CD? This is how I did it before, but had a different problem that has since been solved.

---

### Post by stream303 on 2008-02-23
I guess you could say that text-based is kind of a misnomer.

The "alternate" install uses older vga-style graphics with menu choices in boxes for the initial install.  You navigate around in it if necessary using your arrow keys, tabs, and space bar to select/unselect items if necessary.  "gas gauges' keep you informed of the progress, and don't freak out if you think the system is locked up at a certain percentage point.  give it some time.

Don't tear your hair out with the live-cd.

---

