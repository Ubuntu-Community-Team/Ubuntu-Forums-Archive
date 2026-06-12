---
title: "DeVeDe only converts fraction of .avi to DVD"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by Bazzaah on 2007-05-25
I'm using DeVeDe on Edgy. I burned 15 or so episodes of heroes to DVD without problem but now DeVeDe has started converting only a fraction of each show, say, 8 out of 45 minutes. The weird thing is that if I burn that video to DVD I can watch the whole episode from my PC but my DVD player won't even recognise the disc.

Any ideas why DeVeDe has started doing this and what I can do about it? 

Unfortunately, It's starting to look like another thing that Windows does better as I did a control under XP and the episodes that have proved problematic under Ubuntu/DeVeDe get converted under my XP-based software just fine.

---

### Post by Bazzaah on 2007-05-25
bump

anyone?

---

### Post by Bazzaah on 2007-05-25
found a solution - did it under XP.

---

### Post by kinematic on 2007-05-25
that's not a solution.....that's working around the problem because you can't fix it.

---

### Post by Bazzaah on 2007-05-25
my goal was to be able to convert some .avi files to dvd without spending hours/days trawling the net for a solution to a problem that I only have under Linux. Xp solved it just fine.

I really like Ubuntu/Linux and it will stay as my OS of choice but there are some random things that are just peculiar and irritating and an inefficient use of my time to solve.

This I'm afraid is one of them.

---

### Post by MrKlean on 2007-05-25
hmmmm... I welcome the learning experience.  I don't consider it a waste of my time ; )

---

### Post by Bazzaah on 2007-05-31
I would too but it's all a question of how much time one has to solve the problem against the improtance of solving that problem. 

Anyway, no matter, if anyone has any comments on the actual problem i would welcome them.

---

### Post by aeiah on 2007-05-31
have you launched devede from the terminal to look for errors?

it never really worked for me. i use tovid now. i use the gui version for episodic stuff and an automated script for a film (in one or two parts) onto a dvd. its been pretty much trouble free for me.

---

### Post by Bazzaah on 2007-05-31
the funny thing is I get exactly the same problem with avidemux.

It's really weird.

Will try devede for errors but given the error reproduces with avidemux I'm minded to think the problem is not application specific.

---

### Post by Bazzaah on 2007-06-02
No errors in devede if I start in terminal. 

ok here's a log from Nero Linux - as you can see from the log below, some files are not being created; this is the case with DeVeDe, Avidemux and Tovid. The log below comes from using Tovid from terminal. 

I used the following command to 'convert' the .avi (it's Heroes if you're wondering what all the fuss is about).

tovid -dvd -pal -in {.avi filename}.avi -out {new filename}

as far as i can tell, that means i instructed tovid to make the necessary files for a PAL DVD to be created from the .avi file. But that hasn't happened as key video files are missing. Any idea how I can find out where the problem is? 

Any tips hints for this kind of problem solving? This problem occurs on both my Edgy and Feisty installs by the way so I'm baffled at this point. The weird thing is it used to work and has now stopped. 

I'm going to file this problem as a bug.

2CA0-731M-1800-2000-406M-5EM7-****

Linux 2.6.20-16-generic
Nero API version: 7.5.14.4
Using interface version: 7.5.0.2
Installed in: /usr/lib/nero/
Application: Nero AG\Nero Linux
Internal Version: 7, 5, 14, 4

Recorder:             <SONY DVD RW AW-G170A>    Version: 1.60 - HA 0 TA 0 - 0.0.0.0
 Adapter driver:      <ide-cdrom>               HA 0
 Drive buffer  :      2048kB
 Bus Type      :      default (0) -> ATAPI, detected: ?
Excluded drive IDs: 
WriteBufferSize: 83886080 (0) Byte
BUFE           : 0
Physical memory     : 2027MB (2076092kB)
Free physical memory: 1558MB (1595752kB)
Memory in use       : 23 %
Uncached PFiles: 0x0
Use Inquiry    : 1
Global Bus Type: default (0)
Check supported media : Disabled (0) 

2.6.2007
NeroAPI
13:23:03	#1 DVDREALLOC -21 File DVDVideoCompilation.cpp, Line 1013
	Required file 'VIDEO_TS.IFO' is not present
	
13:23:03	#2 DVDREALLOC -21 File DVDVideoCompilation.cpp, Line 1013
	Required file 'VIDEO_TS.BUP' is not present
	
13:23:03	#3 Phase 117 File ExtendedProgress.cpp, Line 537
	DVD-Video files compliance test failed

---

### Post by JoBangles on 2007-06-02
Hi, I have converted xvid_telesync avi vidio to mpg using  ffmpeg " ffmpeg -i yourfilename.avi -target pal-vcd outputfilename.mpg " which produced an mpg file with: stream0 - codec:mpgv ; stream 1 - codec: A52 . The file plays well with Totem. I tryed converting to DVD using DeeVeeDee to create ISO and K3b to burn disc, but resulting DVD disc is unrecognised by DVD player and PC DVD burner/player will not even  recognise that a disc has been inserted. I tried to play ISO on hdb but system reported unrecognised file type. Thanks in advance for any guidance.

---

