---
title: "Linux DC++ problem"
date: 2005-12-20
forum: Absolute Beginner Talk
---

### Post by plcdfa on 2005-12-20
Starting to feel a bit frustrated... If someone ever thinks he's good with computers just let him install Linux, his confidence will go away quickly...;) 
I'm just posting one silly quetion after another on the forums, and it's embrassing, even though I manage to solve many things on my own.
But enough of whining, here's my problem, you'll be able to help surely:
when connecting to a hub with many thousends of users with a direct connect client (I tried both Valknut and Linux DC++  -same problem) the CPU usage jumps to 100% and stays there forever. If I don't add to the priority of DC even the mouse lags. Anyhow, the client works extremely slowly, complately unusable, and I've just entered the main chat room, no search or anything. It's not the hashing, that's finished by then. In ksysguard I see two DC processes, both with high user cpu usage. According to firestarter there's only one connection live (the hub itself I suppose), though once I saw some 70-80 kB/s incoming activity. (It was only once, might be just coincidence, a strange one though - I didn't have anything else running.) Searched the forums, googled around, but haven't find anything like my problem.  I used Valknut in Hoary, and it worked like a charm, really weird thing. I find Breezy less "friendly" all around, but that's just my personal impression. If any of you have a workaround please post, thx in advance.

---

### Post by plcdfa on 2005-12-24
Come on lads, just gimme some tips! Should I post it elsewhere, or should I change distro? ;) By the way, Merry Christmas for everyone!

---

### Post by bscbrit on 2005-12-24
Perhaps nobody on the 'Absolute Beginners' forum knows what DC++ is.  I certainly don't.  Sorry I cannot help.  Might there be a more appropriate forum?

---

### Post by xmastree on 2005-12-24
Seen this thread?
[http://www.ubuntuforums.org/showthread.php?t=42084](http://www.ubuntuforums.org/showthread.php?t=42084)

---

### Post by kaamos on 2005-12-24
Sorry to say this, but I have never gotten dc++ to work properly on linux. The cpu hogging usually stops after a couple of minutes when it has connected to the hubs, but the problem is that dc++ does not use the port that is set in configs. So bye bye to active mode.. This is (was? don't know) a filed bug. Have tried both release and cvs versions..

Nevertheless, merry christmas! :)

---

### Post by plcdfa on 2005-12-24
[QUOTE=bscbrit]Perhaps nobody on the 'Absolute Beginners' forum knows what DC++ is.  I certainly don't.  Sorry I cannot help.  Might there be a more appropriate forum?[/QUOTE]
It seems I'll really have to go somewhere else for help... :( 
[QUOTE=xmastree]
Seen this thread?
[http://www.ubuntuforums.org/showthread.php?t=42084](http://www.ubuntuforums.org/showthread.php?t=42084)[/QUOTE]
Yes, I saw it before, but nobody seems to have this problem...
[QUOTE=kaamos]	
Sorry to say this, but I have never gotten dc++ to work properly on linux. The cpu hogging usually stops after a couple of minutes when it has connected to the hubs, but the problem is that dc++ does not use the port that is set in configs. So bye bye to active mode.. This is (was? don't know) a filed bug. Have tried both release and cvs versions..

Nevertheless, merry christmas! :)[/QUOTE]
But I had Valknut working properly in Hoary! That's why I'm so confused.

Thx for the answers anyway!

---

### Post by loftx on 2006-01-02
Don't know much about Valknut, but Linux DC++ is still a very early release - around the 0.1 stage.  There's been a few bugfixes since the 20050809cvs ubuntu release posted by mird, so maybe wait for the next ubuntu release and try that.

---

### Post by ububaba on 2006-04-26
Linux DC++ is acting strange. When I try to upload files to "MyShare" folder, a popup
message says "*Subfolders would be removed*". Even if I have the possibility of sharing 
**100GB**s I can barely share **5GB**s at the most! This really drives one nuts. 

Has someone else faced the same problem and even solved it?:-k Suggestions awaited.

---

### Post by strutzz on 2007-11-11
I have the same problem as.plcdfa , in addition torrents don't seem to work. i think it's something with my network config, .... in windows everything works fine 
( gutsy gibon , amd athlon xp , 256 Mb ram , 2Gb swap, lan , isp giganet , romania.)

---

### Post by sultanoswing on 2007-11-11
Sorry to hear your problems, lads. ldcpp works fine for me, mind you I'm using an older build date (0.691 core) due to hub compatibility issues with the new cores.

---

