---
title: "Slimserver - can't access music on NTFS"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by jason442 on 2007-12-14
Hey folks,

I having a weird issue with Slimserver. Slimserver is installed and running. For some reason I cannot set the music folder to my NTFS drive - which contains all my music. It's mounted at /media/sdc5/Music. slimserver says "ops - "/media/sdc5/Music" doesn't seem to be a valid directory. Try again.

I can browse to that location and also play music using the default ubuntu media player. So what's the deal?

I did a search and found somebody with the same problem...but I did not see a solution.

here is my fstab file:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=ef957c9a-4c77-493c-8e9a-d550732d741c /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=16F84F77F84F5461 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb1
UUID=BD45E74BF382FD95 /media/sdb1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdc5
UUID=684F9B48F1CF5917 /media/sdc5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=df94e11e-1201-479a-864f-e496df528d53 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0



Please help!
Thanks!
Jason

---

### Post by jason442 on 2007-12-14
I'll repost this to multimedia&video

---

### Post by taurus on 2007-12-14
What's the output of this command from a terminal?

```
ls -la /media/sdc5
```

---

### Post by jason442 on 2007-12-14
jason@jason-desktop:~$ ls -la /media/sdc5
total 1058904
drwxrwx--- 1 root plugdev     12288 2007-12-13 21:41 .
drwxr-xr-x 7 root root         4096 2007-12-14 21:14 ..
-rwxrwx--- 2 root plugdev 276942637 2006-09-22 19:35 01 Gay Witch Hunt.m4v
drwxrwx--- 1 root plugdev      4096 2007-11-05 20:33 Audio Books
drwxrwx--- 1 root plugdev      8192 2007-09-22 14:04 Audio Record
drwxrwx--- 1 root plugdev      4096 2007-12-12 18:39 Backup
-rwxrwx--- 2 root plugdev 366278656 2007-04-24 02:59 David Blaine - Street Magic.avi
drwxrwx--- 1 root plugdev         0 2007-11-12 18:03 Diskeeper
drwxrwx--- 1 root plugdev     28672 2007-12-11 19:44 Documents
drwxrwx--- 1 root plugdev      4096 2007-09-08 16:54 E-Books
drwxrwx--- 1 root plugdev      4096 2007-12-10 20:47 Guitar Tab
-rwxrwx--- 2 root plugdev 440479340 2002-12-14 15:19 jason&kenny.mpg
drwxrwx--- 1 root plugdev      4096 2007-09-15 19:22 Mom&Dad
drwxrwx--- 1 root plugdev         0 2007-09-18 21:33 MSOCache
drwxrwx--- 1 root plugdev      4096 2007-11-06 19:59 Music
drwxrwx--- 1 root plugdev      4096 2007-09-20 21:41 My RoboForm Data
drwxrwx--- 1 root plugdev      4096 2007-12-01 22:21 Pictures
drwxrwx--- 1 root plugdev         0 2007-09-08 09:27 $RECYCLE.BIN
drwxrwx--- 1 root plugdev      4096 2007-12-13 20:22 RECYCLER
drwxrwx--- 1 root plugdev      4096 2007-12-12 22:04 System Volume Information
-rwxrwx--- 1 root plugdev      6144 2007-10-17 20:53 Thumbs.db
drwxrwx--- 1 root plugdev    503808 2007-10-20 02:35 Wallpaper
drwxrwx--- 1 root plugdev      4096 2007-09-22 12:51 Web Site Suff
drwxrwx--- 1 root plugdev         0 2007-09-08 16:30 Website templates
drwxrwx--- 1 root plugdev      4096 2007-09-18 14:36 WINDOWS
jason@jason-desktop:~$ 
jason@jason-desktop:~$

---

### Post by taurus on 2007-12-14
Looks like you don't have permissions to access Music directory.  You will probably get an error message when you run this command.

```
ls -la /media/sdc5/Music
```

---

### Post by jason442 on 2007-12-14
I don't get any errors. I get the directory listing:

jason@jason-desktop:~$ ls -la /media/sdc5/Music
total 152
drwxrwx--- 1 root plugdev   4096 2007-11-06 19:59 .
drwxrwx--- 1 root plugdev  12288 2007-12-13 21:41 ..
drwxrwx--- 1 root plugdev  16384 2007-12-11 18:36 FLAC
drwxrwx--- 1 root plugdev   8192 2007-09-08 15:57 Maricors Moms CDs to MP3
drwxrwx--- 1 root plugdev 110592 2007-12-07 21:13 MP3s
drwxrwx--- 1 root plugdev   4096 2007-11-09 21:13 Ripped CDs
jason@jason-desktop:~$ 

BTW..thanks for looking at this. Any other thoughts?

---

### Post by taurus on 2007-12-14
> **jason442 said:**
> I don't get any errors. I get the directory listing:

jason@jason-desktop:~$ ls -la /media/sdc5/Music
total 152
drwxrwx--- 1 root plugdev   4096 2007-11-06 19:59 .
drwxrwx--- 1 root plugdev  12288 2007-12-13 21:41 ..
drwxrwx--- 1 root plugdev  16384 2007-12-11 18:36 FLAC
drwxrwx--- 1 root plugdev   8192 2007-09-08 15:57 Maricors Moms CDs to MP3
drwxrwx--- 1 root plugdev 110592 2007-12-07 21:13 MP3s
drwxrwx--- 1 root plugdev   4096 2007-11-09 21:13 Ripped CDs
jason@jason-desktop:~$ 

BTW..thanks for looking at this. Any other thoughts?

So, you have more directories under Music.  Now, are you trying to access the MP3s directory?

```
ls -la /media/sdc5/Music/MP3s
```

---

### Post by jason442 on 2007-12-14
I actually want to set the music folder to Music ..so it has has access to FLAC, MP3, all directories. That is how I had it setup in windows.I've tried to set it to FLAC or MP3 just to see if I can get it to work...but no luck.

BTW. One weird thing. I can set the music folder to /media/sdc5  but that is as far as I can go. once I try /media/sdc5/music or /media/sdc5/flac or whatever... it doesn't like it.

---

### Post by jason442 on 2007-12-14
More directories! :)

jason@jason-desktop:~$ ls -la /media/sdc5/Music/MP3s
total 48568
drwxrwx--- 1 root plugdev   110592 2007-12-07 21:13 .
drwxrwx--- 1 root plugdev     4096 2007-11-06 19:59 ..
drwxrwx--- 1 root plugdev     8192 2007-09-08 16:01 2Pac
drwxrwx--- 1 root plugdev   155648 2007-09-08 16:02 80's
drwxrwx--- 1 root plugdev     8192 2007-09-08 16:02 Adam Sandler
drwxrwx--- 1 root plugdev    16384 2007-09-08 16:02 Aerosmith
drwxrwx--- 1 root plugdev     4096 2007-09-08 16:02 Aimee Mann
drwxrwx--- 1 root plugdev    20480 2007-09-14 20:34 Alanis Morissette
drwxrwx--- 1 root plugdev    16384 2007-09-14 20:33 Alan Jackson
drwxrwx--- 1 root plugdev    12288 2007-09-14 20:48 Alice in Chains
drwxrwx--- 1 root plugdev    20480 2007-12-07 17:19 Alicia Keys
drwxrwx--- 1 root plugdev    16384 2007-12-07 22:06 Alicia Wiley
drwxrwx--- 1 root plugdev     4096 2007-09-08 16:02 Alien Ant Farm
drwxrwx--- 1 root plugdev     4096 2007-09-08 16:02 America
drwxrwx--- 1 root plugdev     4096 2007-09-14 20:32 Anna Nalick
drwxrwx--- 1 root plugdev     4096 2007-09-08 16:02 AudioSlave
drwxrwx--- 1 root plugdev    24576 2007-09-08 23:09 Avril Lavigne
drwxrwx--- 1 root plugdev     4096 2007-09-09 13:00 Baby Face
drwxrwx--- 1 root plugdev     8192 2007-09-08 16:02 Barenaked Ladies
drwxrwx--- 1 root plugdev    40960 2007-09-08 16:03 Beatles
drwxrwx--- 1 root plugdev    12288 2007-09-08 16:03 Beck
drwxrwx--- 1 root plugdev     8192 2007-09-14 21:02 Better Than Ezra
drwxrwx--- 1 root plugdev    12288 2007-12-07 21:13 Beyoncé
drwxrwx--- 1 root plugdev     8192 2007-09-08 16:03 Björk
drwxrwx--- 1 root plugdev     4096 2007-09-08 23:00 Black Crows
drwxrwx--- 1 root plugdev     8192 2007-09-08 16:03 Black Eyed Peas
drwxrwx--- 1 root plugdev        0 2007-09-08 16:03 Blind Melon
drwxrwx--- 1 root plugdev        0 2007-09-08 16:03 Blink 182
drwxrwx--- 1 root plugdev     8192 2007-09-09 13:24 Bob Dylan
drwxrwx--- 1 root plugdev    24576 2007-09-08 16:03 Bob Seger
drwxrwx--- 1 root plugdev     4096 2007-09-08 16:03 Bond
drwxrwx--- 1 root plugdev    12288 2007-09-08 23:01 Bon Jovi
drwxrwx--- 1 root plugdev     8192 2007-09-08 16:03 Boston
drwxrwx--- 1 root plugdev        0 2007-09-08 16:04 Boys II Men
drwxrwx--- 1 root plugdev    12288 2007-09-08 23:01 Brad Paisley - 5th Gear
drwxrwx--- 1 root plugdev     8192 2007-09-08 16:04 Bread
drwxrwx--- 1 root plugdev    28672 2007-09-12 19:29 Brian McKnight
drwxrwx--- 1 root plugdev    16384 2007-09-08 23:02 Brooke Hogan
drwxrwx--- 1 root plugdev     8192 2007-09-08 23:02 Bruce Springsteen
drwxrwx--- 1 root plugdev    24576 2007-09-08 16:04 Bush
drwxrwx--- 1 root plugdev     8192 2007-09-08 16:04 Candle Box
drwxrwx--- 1 root plugdev     4096 2007-09-08 16:04 Cantrell, Jerry
drwxrwx--- 1 root plugdev     4096 2007-09-08 16:04 Chris Isaak
drwxrwx--- 1 root plugdev    16384 2007-09-08 16:04 Christina Aguilera
drwxrwx--- 1 root plugdev    36864 2007-09-09 20:43 Christmas music
drwxrwx--- 1 root plugdev     4096 2007-09-08 16:05 Clash, the
drwxrwx--- 1 root plugdev    28672 2007-09-09 13:30 Coldplay
drwxrwx--- 1 root plugdev    28672 2007-09-08 16:05 Collective Soul
drwxrwx--- 1 root plugdev    36864 2007-09-12 19:45 Comedy
drwxrwx--- 1 root plugdev     8192 2007-09-08 16:05 Cornershop
drwxrwx--- 1 root plugdev     8192 2007-11-26 20:35 Counting Crows
drwxrwx--- 1 root plugdev    45056 2007-09-08 16:05 Cranberries, The
drwxrwx--- 1 root plugdev     8192 2007-09-08 16:05 Creed
drwxrwx--- 1 root plugdev     4096 2007-09-08 16:05 Crosby, Stills, Nash & Young
drwxrwx--- 1 root plugdev    28672 2007-09-08 16:06 Cure, the
drwxrwx--- 1 root plugdev     8192 2007-09-08 16:06 Dashboard Confessional
drwxrwx--- 1 root plugdev     4096 2007-10-05 22:52 Daughtry
drwxrwx--- 1 root plugdev    40960 2007-09-09 13:38 Dave Matthews Band
drwxrwx--- 1 root plugdev    24576 2007-09-08 16:06 Days of the New
drwxrwx--- 1 root plugdev     8192 2007-09-08 16:06 Death Cab For Cutie
drwxrwx--- 1 root plugdev     8192 2007-09-08 16:06 Def Leppard
drwxrwx--- 1 root plugdev    16384 2007-10-07 09:15 Diana Krall
drwxrwx--- 1 root plugdev     4096 2007-09-08 16:06 Dido
drwxrwx--- 1 root plugdev     8192 2007-09-08 23:08 Dire Straits
drwxrwx--- 1 root plugdev    24576 2007-09-08 16:06 Dixie Chicks
drwxrwx--- 1 root plugdev    16384 2007-09-08 16:07 Donald Fagen
drwxrwx--- 1 root plugdev     8192 2007-09-08 16:07 Don Henley
drwxrwx--- 1 root plugdev     8192 2007-09-08 23:08 Donnas, The
drwxrwx--- 1 root plugdev     4096 2007-09-08 16:07 Doors, The
drwxrwx--- 1 root plugdev     4096 2007-09-08 16:07 Eagles, The
drwxrwx--- 1 root plugdev    16384 2007-09-08 16:07 Electric Light Orchestra
drwxrwx--- 1 root plugdev    16384 2007-09-08 16:07 Elton John
drwxrwx--- 1 root plugdev     8192 2007-09-08 16:07 Emerson Lake and Palmer
drwxrwx--- 1 root plugdev    24576 2007-09-08 16:07 Eminem
drwxrwx--- 1 root plugdev    32768 2007-09-08 16:07 Enigma
drwxrwx--- 1 root plugdev    12288 2007-09-08 16:08 Enya
drwxrwx--- 1 root plugdev    28672 2007-09-08 16:08 Eric Clapton
drwxrwx--- 1 root plugdev     4096 2007-09-08 23:08 Eurythmics
drwxrwx--- 1 root plugdev     8192 2007-09-08 16:08 Evanescence
drwxrwx--- 1 root plugdev        0 2007-09-08 16:08 Eve 6
drwxrwx--- 1 root plugdev     4096 2007-09-08 16:08 Faithless
drwxrwx--- 1 root plugdev     4096 2007-09-08 16:08 Fall out boy
drwxrwx--- 1 root plugdev     8192 2007-09-08 16:08 Fergie
drwxrwx--- 1 root plugdev        0 2007-09-08 16:08 Filter
drwxrwx--- 1 root plugdev    12288 2007-09-09 13:45 Fiona Apple
drwxrwx--- 1 root plugdev     8192 2007-09-08 16:08 Fleetwood Mac
drwxrwx--- 1 root plugdev     4096 2007-09-08 16:08 Flickerstick
drwxrwx--- 1 root plugdev     8192 2007-09-08 16:08 Foo Fighters
drwxrwx--- 1 root plugdev     4096 2007-09-08 23:08 Foreigner
drwxrwx--- 1 root plugdev     4096 2007-09-08 16:08 Fourplay
drwxrwx--- 1 root plugdev     4096 2007-09-08 16:08 Fray,the
drwxrwx--- 1 root plugdev    16384 2007-09-08 16:09 Fuel
drwxrwx--- 1 root plugdev        0 2007-09-08 16:09 Garbage
drwxrwx--- 1 root plugdev     8192 2007-09-08 16:09 Garth Brooks
drwxrwx--- 1 root plugdev     4096 2007-09-08 16:09 Gary wright
drwxrwx--- 1 root plugdev    12288 2007-09-08 16:09 Genesis
drwxrwx--- 1 root plugdev     8192 2007-09-08 16:09 Gin Blossoms
drwxrwx--- 1 root plugdev     8192 2007-09-14 21:03 Godsmack
drwxrwx--- 1 root plugdev    12288 2007-09-08 23:05 Goo Goo Dolls
drwxrwx--- 1 root plugdev     4096 2007-09-08 16:09 Guess Who, the
drwxrwx--- 1 root plugdev     8192 2007-09-08 16:09 G- Unit
drwxrwx--- 1 root plugdev     8192 2007-09-08 16:09 Guns N' Roses
drwxrwx--- 1 root plugdev     4096 2007-09-08 16:09 Heart
drwxrwx--- 1 root plugdev     4096 2007-09-08 16:09 Humble Pie
drwxrwx--- 1 root plugdev     4096 2007-09-08 16:09 Iggy Pop
drwxrwx--- 1 root plugdev     4096 2007-09-08 16:09 Incubus
drwxrwx--- 1 root plugdev     4096 2007-09-08 16:09 Iron Butterfly
drwxrwx--- 1 root plugdev    24576 2007-09-14 21:10 Jack Johnson
drwxrwx--- 1 root plugdev     4096 2007-09-09 12:51 Jackson Browne
drwxrwx--- 1 root plugdev     4096 2007-09-13 20:39 James Blunt
drwxrwx--- 1 root plugdev     4096 2007-09-08 16:10 James Taylor
drwxrwx--- 1 root plugdev        0 2007-09-08 16:10 Jane's Addiction
drwxrwx--- 1 root plugdev     8192 2007-09-09 13:49 Jars of Clay
drwxrwx--- 1 root plugdev    49152 2007-09-08 16:10 Jazz
drwxrwx--- 1 root plugdev     4096 2007-09-08 16:10 Jazz Mandolin Project
drwxrwx--- 1 root plugdev     8192 2007-09-08 16:10 Jewel
drwxrwx--- 1 root plugdev    32768 2007-09-08 16:10 Jim Croce
drwxrwx--- 1 root plugdev     8192 2007-09-08 16:10 Jimi Hendrix
drwxrwx--- 1 root plugdev        0 2007-09-08 16:10 Jimmy Eat World
drwxrwx--- 1 root plugdev     8192 2007-09-08 16:11 Jimmy Page & Robert Plant
drwxrwx--- 1 root plugdev     4096 2007-09-08 16:11 Joe Cocker
drwxrwx--- 1 root plugdev     8192 2007-09-08 16:11 Joe Satriani
drwxrwx--- 1 root plugdev     4096 2007-09-09 13:52 John Coltrane
drwxrwx--- 1 root plugdev     4096 2007-09-08 16:11 John Cougar Mellencamp
drwxrwx--- 1 root plugdev    12288 2007-12-07 18:41 John Legend
drwxrwx--- 1 root plugdev    24576 2007-09-08 16:11 John Mayer
drwxrwx--- 1 root plugdev     4096 2007-09-14 21:16 JoJo
drwxrwx--- 1 root plugdev     4096 2007-09-14 21:05 Jonny Lang
drwxrwx--- 1 root plugdev    61440 2007-09-14 21:04 Journey
drwxrwx--- 1 root plugdev    20480 2007-09-09 13:53 Jude
drwxrwx--- 1 root plugdev    16384 2007-09-08 16:12 Justin Timberlake
drwxrwx--- 1 root plugdev     4096 2007-09-08 16:12 Kansas
drwxrwx--- 1 root plugdev    24576 2007-09-08 16:12 Kelly Clarkson
drwxrwx--- 1 root plugdev     8192 2007-09-09 13:56 Kittie
drwxrwx--- 1 root plugdev     4096 2007-09-08 16:12 K's Choice
-rwxrwx--- 2 root plugdev       83 2001-03-28 15:13 KSUA - UAF RADIO.m3u
drwxrwx--- 1 root plugdev    57344 2007-09-08 16:13 Led Zeppelin
drwxrwx--- 1 root plugdev     8192 2007-09-08 23:05 Lenny Kravitz
drwxrwx--- 1 root plugdev     8192 2007-09-08 16:13 Letters To Cleo
drwxrwx--- 1 root plugdev     4096 2007-09-08 16:13 Lili Haydn
drwxrwx--- 1 root plugdev     4096 2007-09-08 16:13 Linkin Park
drwxrwx--- 1 root plugdev    40960 2007-09-08 16:13 Live
drwxrwx--- 1 root plugdev     4096 2007-09-08 16:13 Low
drwxrwx--- 1 root plugdev    20480 2007-09-08 16:13 Mary J Blige
drwxrwx--- 1 root plugdev    32768 2007-12-08 23:09 Matchbox Twenty
drwxrwx--- 1 root plugdev     4096 2007-09-14 21:05 Meat Loaf
drwxrwx--- 1 root plugdev    24576 2007-09-09 20:30 Metallica
drwxrwx--- 1 root plugdev     4096 2007-09-08 16:14 Michael Jackson
drwxrwx--- 1 root plugdev    16384 2007-09-08 16:14 Michelle Branch
drwxrwx--- 1 root plugdev    49152 2007-09-08 16:14 MISC Classic Rock
drwxrwx--- 1 root plugdev     4096 2007-09-09 13:59 MISC Country
drwxrwx--- 1 root plugdev    40960 2007-09-14 21:09 MISC Pop singles
drwxrwx--- 1 root plugdev     4096 2007-09-08 16:14 Moby
drwxrwx--- 1 root plugdev     8192 2007-09-08 16:14 Moody Blues, the
drwxrwx--- 1 root plugdev     8192 2007-09-08 16:14 natalie imbruglia
drwxrwx--- 1 root plugdev    12288 2007-09-09 14:01 Neil Young
drwxrwx--- 1 root plugdev     4096 2007-09-08 16:14 Nelly
drwxrwx--- 1 root plugdev     8192 2007-09-14 21:03 Nelly Furtado
drwxrwx--- 1 root plugdev    24576 2007-09-09 14:02 NEW
drwxrwx--- 1 root plugdev    20480 2007-12-08 22:53 Nickelback
drwxrwx--- 1 root plugdev     4096 2007-09-14 21:06 Night Ranger
drwxrwx--- 1 root plugdev    12288 2007-09-08 16:15 Nirvana
drwxrwx--- 1 root plugdev    12288 2007-09-08 16:15 No Doubt
drwxrwx--- 1 root plugdev    12288 2007-09-08 16:15 Norah Jones
drwxrwx--- 1 root plugdev     4096 2007-09-08 16:15 Oasis
drwxrwx--- 1 root plugdev        0 2007-09-08 16:15 Offspring
drwxrwx--- 1 root plugdev     8192 2007-09-08 16:15 Ozzy
drwxrwx--- 1 root plugdev    20480 2007-09-14 21:06 Pat Benatar
drwxrwx--- 1 root plugdev     4096 2007-09-08 16:16 Paula Cole
drwxrwx--- 1 root plugdev    20480 2007-09-08 16:15 Paul Oakenfold
drwxrwx--- 1 root plugdev     4096 2007-09-08 16:16 Paul Schwartz
drwxrwx--- 1 root plugdev    28672 2007-09-14 21:06 Pearl Jam
drwxrwx--- 1 root plugdev     8192 2007-09-08 16:16 Perfect Circle
drwxrwx--- 1 root plugdev     4096 2007-09-09 14:04 Peter Frampton
drwxrwx--- 1 root plugdev     4096 2007-09-08 16:16 Peter Gabriel
drwxrwx--- 1 root plugdev     4096 2007-09-08 16:16 Phil Collins
drwxrwx--- 1 root plugdev     8192 2007-09-08 16:16 Pink
drwxrwx--- 1 root plugdev    77824 2007-09-08 16:17 Pink Floyd
drwxrwx--- 1 root plugdev     4096 2007-09-08 16:17 Placebo
drwxrwx--- 1 root plugdev    20480 2007-11-14 22:19 Plain White T's
-rwxrwx--- 2 root plugdev  9265195 2007-10-21 22:04 Plain White T's - Hey There Delilah.mp3
drwxrwx--- 1 root plugdev     8192 2007-09-08 16:17 Plant, Robert
drwxrwx--- 1 root plugdev     8192 2007-09-08 16:15 P.O.D
drwxrwx--- 1 root plugdev     8192 2007-09-08 16:17 Poe
drwxrwx--- 1 root plugdev     8192 2007-09-08 16:17 Portishead
drwxrwx--- 1 root plugdev     4096 2007-09-08 16:17 Prince
drwxrwx--- 1 root plugdev     4096 2007-09-14 21:06 Puddle of Mudd
drwxrwx--- 1 root plugdev     8192 2007-09-08 16:17 Pussycat Dolls
drwxrwx--- 1 root plugdev    12288 2007-09-14 21:18 Queen
drwxrwx--- 1 root plugdev    12288 2007-09-09 20:35 Queensryche
drwxrwx--- 1 root plugdev     8192 2007-09-08 16:17 Radiohead
drwxrwx--- 1 root plugdev    49152 2007-09-08 16:18 Red Hot Chili Peppers
drwxrwx--- 1 root plugdev     8192 2007-09-08 16:17 R.E.M
drwxrwx--- 1 root plugdev     4096 2007-09-08 16:18 REO Speedwagon
drwxrwx--- 1 root plugdev    28672 2007-11-04 21:03 Rihanna
drwxrwx--- 1 root plugdev     8192 2007-09-08 16:17 R Kelly
drwxrwx--- 1 root plugdev     8192 2007-09-08 16:18 Robin Trower
drwxrwx--- 1 root plugdev     4096 2007-09-08 16:18 Rolling Stones
drwxrwx--- 1 root plugdev    12288 2007-09-08 16:18 Rush
drwxrwx--- 1 root plugdev    12288 2007-09-08 16:18 Sade
drwxrwx--- 1 root plugdev    20480 2007-09-08 16:18 Sammy hagar
drwxrwx--- 1 root plugdev     4096 2007-09-08 16:18 Santana
drwxrwx--- 1 root plugdev     8192 2007-09-08 16:18 Sarah Brightman
drwxrwx--- 1 root plugdev    28672 2007-10-05 22:54 Sarah McLachlan
drwxrwx--- 1 root plugdev     4096 2007-09-08 16:18 Scorpions
drwxrwx--- 1 root plugdev        0 2007-09-08 16:18 Seven Mary Three
drwxrwx--- 1 root plugdev     8192 2007-09-08 16:19 Sherly Crow
drwxrwx--- 1 root plugdev     4096 2007-09-08 16:19 singles
-rwxrwx--- 1 root plugdev 37140608 2007-08-29 20:44 Sleep.mp3
drwxrwx--- 1 root plugdev    36864 2007-09-08 16:19 Smashing Pumpkins
drwxrwx--- 1 root plugdev    16384 2007-09-08 16:19 Snoop Dogg
drwxrwx--- 1 root plugdev    40960 2007-09-08 16:19 Snow Patrol
drwxrwx--- 1 root plugdev        0 2007-09-08 16:19 Soul Asylum
drwxrwx--- 1 root plugdev     8192 2007-09-08 16:19 Sounds
drwxrwx--- 1 root plugdev     4096 2007-09-08 16:19 Sound Tracks
drwxrwx--- 1 root plugdev     4096 2007-09-08 16:19 Space Hog
drwxrwx--- 1 root plugdev     4096 2007-09-08 16:19 Spoon
drwxrwx--- 1 root plugdev     8192 2007-09-08 16:19 Staind
drwxrwx--- 1 root plugdev     8192 2007-09-14 21:04 Steely Dan
drwxrwx--- 1 root plugdev     8192 2007-09-08 16:20 Sting
drwxrwx--- 1 root plugdev    12288 2007-09-08 16:20 Stone Temple Pilots
drwxrwx--- 1 root plugdev    28672 2007-09-08 16:20 Styx
drwxrwx--- 1 root plugdev     4096 2007-09-08 16:20 Sugar Ray
drwxrwx--- 1 root plugdev     4096 2007-09-08 16:20 Super Tramp
drwxrwx--- 1 root plugdev    28672 2007-09-09 20:46 Suze Orman
drwxrwx--- 1 root plugdev     8192 2007-09-08 16:20 Tantric
drwxrwx--- 1 root plugdev     4096 2007-09-08 16:20 The Verve Pipe
drwxrwx--- 1 root plugdev    20480 2007-09-08 19:32 Third Eye Blind
drwxrwx--- 1 root plugdev    12288 2007-09-08 16:20 Three Doors Down
drwxrwx--- 1 root plugdev     4096 2007-09-08 16:20 Toad the Wet Sprocket
drwxrwx--- 1 root plugdev     8192 2007-09-08 16:20 Tom Petty and The Heartbreakers
drwxrwx--- 1 root plugdev    61440 2007-09-08 16:21 Tom Waits
drwxrwx--- 1 root plugdev     8192 2007-09-08 16:21 Tonic
drwxrwx--- 1 root plugdev     4096 2007-09-08 16:21 Tool
drwxrwx--- 1 root plugdev     4096 2007-09-08 16:21 Trace Atkins
drwxrwx--- 1 root plugdev     8192 2007-09-08 16:21 Tracy Chapman
drwxrwx--- 1 root plugdev    12288 2007-09-13 21:37 Train
drwxrwx--- 1 root plugdev    24576 2007-09-08 16:21 U2
drwxrwx--- 1 root plugdev     4096 2007-09-08 16:21 Urge Overkill
drwxrwx--- 1 root plugdev    16384 2007-09-08 16:21 Van Halen
drwxrwx--- 1 root plugdev    45056 2007-11-13 20:40 Van Morrison
drwxrwx--- 1 root plugdev     8192 2007-09-08 16:22 Various
drwxrwx--- 1 root plugdev     4096 2007-09-08 16:22 WallFlowers
drwxrwx--- 1 root plugdev     4096 2007-09-08 16:22 Weezer
drwxrwx--- 1 root plugdev    28672 2007-09-08 16:22 Who, the
drwxrwx--- 1 root plugdev        0 2007-09-08 16:22 Wings
drwxrwx--- 1 root plugdev        0 2007-01-06 16:49 WUTemp
drwxrwx--- 1 root plugdev        0 2007-09-08 16:22 Xtreme

---

### Post by taurus on 2007-12-14
> **jason442 said:**
> I actually want to set the music folder to Music ..so it has has access to FLAC, MP3, all directories. That is how I had it setup in windows.I've tried to set it to FLAC or MP3 just to see if I can get it to work...but no luck.

BTW. One weird thing. I can set the music folder to /media/sdc5  but that is as far as I can go. once I try /media/sdc5/music or /media/sdc5/flac or whatever... it doesn't like it.

Make sure you use /media/sdc5/**M**usic instead of /media/sdc5/_m_usic.  I think you probably get an idea how to access those directories now.

---

### Post by jason442 on 2007-12-14
I am using /media/sdc5/**M**usic

I actually cut and pasted that path from the "explore" so I made sure.

Anymore thoughts taurus? Again, I appreciate the help.

---

