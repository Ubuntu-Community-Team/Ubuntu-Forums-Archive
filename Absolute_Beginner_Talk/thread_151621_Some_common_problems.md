---
title: "Some common problems"
date: 2006-03-28
forum: Absolute Beginner Talk
---

### Post by noobzoar2.0 on 2006-03-28
Well as my name says i am totally a noob to Linux, and im sick of windows constantly crapping on me. So the last time it crapped on me i decided to install a fresh new copy of Linux Ubuntu on my 160 GB hardrive. So far i really am clueless on how to do anything but surf the web and use gaim. I was wondering if a more experienced user could reply to questions like:

1. Will games like Battlefield 2,MX vs. ATV unleashed, GTA: Vice City, and Battlefront 2 still work?

2. How exactly do I install something in linux? I'm kinda new to the whole command line thing, but i am interested to learn more about it.

3. Can i run normal .exe files or setups on linux

4. How do i use both of my hardrives (my 160 Gig has linux on it, while my 20 Gig has windows XP on it) at the same time and import data from them. All of my previous music, pictures, videos, etc. are on my 20 Gig and i cant seem to find a way to efficiently create some kind of shortcut.

5 is there any way of using microsoft word or its documents in linux. The school i got to currently only supports microsoft word and i do alot of printing and editing there.

**Yes i have searced the forums and 1 i didnt get very pleasing results and 2 i kinda need to access some of my files in a timely matter.**

Any help would be greatly appreciated! thanks guys...



AMD Athlon XP +1800
160 Gig Ultra ATA 100 Seagate HDD
20 GIg Seagate Barracuda Iltra ATA 100 HDD
Sapphire Radeon 9200SE 128MB video card
512 MB RAM

---

### Post by meborc on 2006-03-28
try the link in my sig... also try reading the **HELP**, which is quite good to give some initial advice on how to install and go about in linux... you find it under system menu if i'm not mistaken...

the exe files will not work :mrgreen: they are for windows and therefore evil!

openoffice, which is included in ubuntu (apps -> office) is able to open all ms office files... well all that you need anyway... give it a go

EDIT: almost forgot... check [this video ]("http://video.google.com/videoplay?docid=5253052326994067125&q=ubuntu&pl=true")for instructions how to install stuff in ubuntu

---

### Post by IYY on 2006-03-28
[QUOTE=noobzoar2.0]
1. Will games like Battlefield 2,MX vs. ATV unleashed, GTA: Vice City, and Battlefront 2 still work?
[/quote]

Some developers are nice enough to make their games work natively on Linux (Doom, Unreal, Quake), but most just go with the mainstream. So, your only solution is to use something like an emulator (not exactly, but it's a good analogy). The problem is that it might be buggy with some games, might not work at all with some games and isn't too easy to set up. The most common app people use to do this is Wine. See if your games are supported on this site: [http://appdb.winehq.org/appbrowse.php](http://appdb.winehq.org/appbrowse.php) .

> 2. How exactly do I install something in linux? I'm kinda new to the whole command line thing, but i am interested to learn more about it.


Several ways. The easiest is to get it from the repositories using the tool called Synaptic. It's already installed on your system. Additionally, you can compile from source (this tends to be difficult for beginners) or download binaries (but they have to be Ubuntu/Debian binaries).

> 3. Can i run normal .exe files or setups on linux

Once again, the solution is Wine, but don't be surprised if some things don't work as expected.

> 
4. How do i use both of my hardrives (my 160 Gig has linux on it, while my 20 Gig has windows XP on it) at the same time and import data from them. All of my previous music, pictures, videos, etc. are on my 20 Gig and i cant seem to find a way to efficiently create some kind of shortcut.


Assuming that your drives are formatted with the NTFS filesystem (that's the most common one for Windows users these days, another option is FAT32):
The solution, along with many others, is in the [Unofficial Ubuntu Guide]("http://ubuntuguide.org/"). The heading is called "How to mount/unmount Windows partitions (NTFS) manually, and allow all users to read only?"

> 5 is there any way of using microsoft word or its documents in linux. The school i got to currently only supports microsoft word and i do alot of printing and editing there.

OpenOffice, which comes installed on Ubuntu, is a great tool that can read word and write word documents. If you still prefer to use MS Word, you can install it using Wine. It's actually one of the applications that runs nearly flawlessly on it.

---

### Post by Scunizi on 2006-03-28
To get access to your windows partitions check out the Wiki.  It took me a while to find the Wiki but it has lots of good info.  [Check out this]("https://wiki.ubuntu.com/AutomaticallyMountPartitions?highlight=%28mount%29") for how to automatically mount your partitions on boot.  Word of warning, you can't save/write and information to a NTFS partition.  It's a good idea when installing to create a small vFat (fat32) partition to be able to transfer "stuff" from one system to another since Windows can't easily see a Linux file system.

If you're a skype user the wiki also has a great section on how to install skype. I'm 3 weeks into linux and the learning curve can be STEEP even for an experienced Windows/Dos user like myself.  Patients overcomes most everything.  I've hosed my install several times just trying things out and have had to reinstall.  Don't give up, this stuff is addicting!

---

### Post by noobzoar2.0 on 2006-03-28
SO since im a total noob i really cant figure out how to run wine or what it even does...im also having problems with this whole mounting business..i mounted my HDD but now it says i dont have the permissions necessary?

---

### Post by RedKnight on 2006-03-28
If you really want to run .exe  files like adobe photoshop and microsoft office I recommend buying:

[http://www.codeweavers.com/products/]("http://www.codeweavers.com/products/")

I personally have a copy of this and there is nothing hard about it, it install's the .exe files as if you were on windows.

It also add's shortcuts to your applications menu :)

Stuart.

---

### Post by noobzoar2.0 on 2006-03-28
well thanks for all of your help guys...i have realized though that until i can take some college classes to learn how to use this stuff..im just going back to windows xp yes i know i am an impatient conforming snob..but this is just to comlicated for me. im gonna stick to what i know, thanks anyway

---

### Post by IDipSkoalMint on 2006-03-28
[QUOTE=noobzoar2.0]well thanks for all of your help guys...i have realized though that until i can take some college classes to learn how to use this stuff..im just going back to windows xp yes i know i am an impatient conforming snob..but this is just to comlicated for me. im gonna stick to what i know, thanks anyway[/QUOTE]

I think you should stick it out. I, as a college student, can attest that the time you have for experimenting decreases significantly if you start a computer science degree. So if I were you, I'd keep this on the back burner and tinker with it whenever you got some time to kill. Keep at it, and you'll learn eventually. It just takes some time. Think back to when you first started using Windows? How good were you at it? Depending on what timeframe you come from, you may or not know anything about MS-DOS, but that's how I started out on computers. Then I was lucky enough to get a copy of Windows 3.1 haha. Anyway, as I said, maybe stick to Windows for the majority of the time, but at least keep this so you can play with it and learn it bit by bit. Trust me, you'll wish you had done this a long time ago once college comes along (as it only gets harder as time passes).

---

