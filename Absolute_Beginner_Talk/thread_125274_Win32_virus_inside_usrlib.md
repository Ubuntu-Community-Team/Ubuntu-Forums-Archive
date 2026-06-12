---
title: "Win32 virus inside //usr/lib"
date: 2006-02-03
forum: Absolute Beginner Talk
---

### Post by user_of_gnomes on 2006-02-03
Hiya, folks

Because I am fairly new to Ubuntu and even though I read that Linux is not affected as easily by viruses as Windows I decided to install a virus scanner just in case.

I obtained aegis-virus-scanner from the Synaptic packet manager and installed it, tried to update it, but somewhere along the lines, that won't work. As a result I am stuck with +/- 200 days out of date virus definitions. Someone tell me how to fix this, please? 

I decided to scan anyway and ended up having found this: 

The file //usr/lib/win32/vp31vfw.dll is infected with the W32/Magistr.a@MM virus. 

Why does Linux have .DLL files? How could I have obtained this? So far I only downloaded files (apart from Rosegarden 4, Aegis anti virus and Thunderbird) that were recommended by either the forum's users or by Ubuntu wiki. 

Since it is a Win32 virus I have become rather concerned with the safety of my Windows computers on the same network. They share folders and neither of them have virus scanners. (They don't have to, because I know what's going on. Well, I knew what was going on until I replaced Windows XP with Ubuntu Linux on one PC) 

Any advise would be very much obliged as I haven't got a clue how to continue from here or how I can prevent this from happening again. 

Raptor

---

### Post by jrib on 2006-02-03
That's part of the w32codecs.  It is *probably* a false positive, but I guess you should make sure.

```
jasonr@luso:~$ md5sum /usr/lib/win32/vp31vfw.dll
d1fea82b115492d4a8ba002e2db31412  /usr/lib/win32/vp31vfw.dll
```

do the same to your file and see if you get the same md5sum.  If you do, then we both probably have the original file and it is most likely a false positive (or you can download the file again and make sure we haven't both been infected :)).  If you get something different, then it may have somehow been infected from your windows partition (guessing?).  So for the 10th time, it's probably just a false positive :P

---

### Post by user_of_gnomes on 2006-02-03
Thanks for your quick response, Jason. 

I was allready scanning my other computers using Trend Micro's online scanning services to make certain there's no infection. Still waiting on the result. 

As for the checksum: 

> root@Ubuntu:/home/raptor# md5sum /usr/lib/win32/vp31vfw.dll
d1fea82b115492d4a8ba002e2db31412  /usr/lib/win32/vp31vfw.dll


I did indeed download W32codecs when I just started using Ubuntu. 

Does us having the same checksum result mean I am not infected? I obtained the information about how to download the W32 codecs from the Ubuntu Wiki.

---

### Post by jrib on 2006-02-03
It means we have the same file.  So if you are infected, so am I :).  Now I got the w32codecs again and extracted the files and the md5sum matches up as well.  So the only two possibilites are that the w32codecs deb came already infected or it's not infected and the antivirus is throwing up a false positive.  I am going to reboot and load windows to scan this file myself to see what norton says.

---

### Post by jrib on 2006-02-03
Okay I survived and I'm back.  Scanned the file with norton and it said it was clean, so I wouldn't worry about your network.

---

### Post by user_of_gnomes on 2006-02-03
I scanned both Windows computers and there were no virus threats found. 

Thanks for helping me out, Jason.

I wonder if updating Aegis to the latest virus definitions manually (Can't seem to do it automatically) will help resolve the problem? I found the latest definitions _[here](http://jodrell.net/projects/aegis)_, but I do not know where I'd have to unpack them..

---

### Post by towsonu2003 on 2006-02-03
if you have time, try clamav... it's easy to refresh the database (and I don't really remember it, I think the command was clamfresh). I also had the feeling that it places clamfresh to cron for daily database updates (this stuff is intended for linux servers, so database updates are important not to infect surfers from the server).

---

### Post by user_of_gnomes on 2006-02-04
[QUOTE=towsonu2003]if you have time, try clamav... it's easy to refresh the database (and I don't really remember it, I think the command was clamfresh). I also had the feeling that it places clamfresh to cron for daily database updates (this stuff is intended for linux servers, so database updates are important not to infect surfers from the server).[/QUOTE]

I installed ClamAV and scanned the //usr/lib/win32 directory. No viruses found, it seems.

I wasn't able to update ClamAV when using freshclam command, though, I think it wants me to update the entire program. I'll have to look into that.. Some day... ;) 

Thanks for the help Jason & Towsonu.

---

