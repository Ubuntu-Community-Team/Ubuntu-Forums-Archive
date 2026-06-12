---
title: "Recording with Streamtuner"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by RichPicker on 2007-07-12
I have streamtuner and streamripper and XMMS installed.
I can play from Streamtuner, but can't record. When I first clicked record, I noticed that it was doing so in the terminal window. I couldn't play it back (if it actually recorded). And I couldn't stop the record action without closing Streamtuner.

So... I changed the record application in the preferences - tried gnusound and audacity - but it doesn't work. It opens the application, but it crashes or just doesn't record.

Then I noticed more of the command structure of streamripper -  that I should specify in which directory to put the recorded material.? Right?

But I mucked up the record application text string in the preferences. I don't remember what it was with the termiinal-window-streamripper text.

Can you tell me that text string, and give me some pointers on how to record with streamripper from the terminal window?

Thanks,

---

### Post by Gen2ly on 2007-07-12
I can probably look up the text stream but I'm going to recommend something far simpler.  Try the app exaile.  You can easily add the plugin streamripper to it.  Where you see installed plugins you can specify where you would like to streams to download to.

Edit:: I found it:  in preferences you need to specify something like this.  i.e. change the download folder:
```
streamtuner save to right directory
x-terminal-emulator -e streamripper %q -d /mnt/Shared_Disk/Music/Recorded -r -q
```

---

### Post by RichPicker on 2007-07-12
Embarrassing, but I don't understand what you are telling me.

---

### Post by RichPicker on 2007-07-12
I copied the second line you gave, and pasted it into streamtuner.  (recored stream application)
I get an error in the terminal when I record, but the terminal closes before I can read what the error says.

---

### Post by RichPicker on 2007-07-12
I typed exaile! in the spot for the record stream application in the preferences, but it gives an error that says the file does not exist.

---

### Post by RichPicker on 2007-07-12
But that was after I loaded the app exaile and added the streamripper plugin to it.

---

### Post by yabbadabbadont on 2007-07-12
In your terminal window, run ```
streamripper http://URL-TO-BE-RIPPED-HERE -d /mnt/Shared_Disk/Music/Recorded -r -q
```
Also, you should probably read the streamripper manpage for information on the various options available when running it.  "man streamripper" in a terminal window to view the manpage.  ('q' to quit viewing the manpage, in case you didn't know already)

---

### Post by RichPicker on 2007-07-12
rich@rich-laptop:~$ streamripper [http://URL-TO-BE-RIPPED-HERE](http://URL-TO-BE-RIPPED-HERE) -d /mnt/Shared_Disk/Music/Recorded -r -q
Connecting...

error -6 [SR_ERROR_CANT_RESOLVE_HOSTNAME]
bye..
shutting down
rich@rich-laptop:~$

---

### Post by yabbadabbadont on 2007-07-12
:roll:

Replace [http://URL-TO-BE-RIPPED-HERE](http://URL-TO-BE-RIPPED-HERE) with the correct URL for the stream you wish to rip....

---

### Post by RichPicker on 2007-07-12
The original text string is in the preference box in streamtuner.

When I try to record, the error message that flashes very quickly in a termianal is 
[SR_ERROR_CANT_CREATE_FILE]

---

### Post by RichPicker on 2007-07-13
You wrote:
Replace [http://URL-TO-BE-RIPPED-HERE](http://URL-TO-BE-RIPPED-HERE) with the correct URL for the stream you wish to rip..

I say, what? I don't understand. All I did was choose a different application for recording. 

Is this the correct text for "Record a Stream"  ?

x-terminal-emulator -e streamripper %q -d /mnt/Shared_Disk/Music/Recorded -r -q


I uninstalled streamtuner and then reinstalled it hoping it would reset to that default, but it didn't. I have typed that text into the box.

---

### Post by RichPicker on 2007-07-13
Or, if using Exaile!,  what text do I enter to use it to record the streams.  I'm referring to the text after Record A Stream in the Preferences. I do appreciate your help.

---

### Post by jjgomera on 2008-04-12
Hello

I have this problem with streamripper too, i can hear the station with mplayer or other player, but streamripper don't connect, this is the message in terminal:

> jjgomera@ordenata:~/configuracion$ streamripper [http://a729.l830022151.c8300.e.lm.akamaistream.net/D/729/8300/v0001/reflector:22151](http://a729.l830022151.c8300.e.lm.akamaistream.net/D/729/8300/v0001/reflector:22151) -a programa.mp3
Connecting...

error -6 [SR_ERROR_CANT_RESOLVE_HOSTNAME]
bye..
shutting down

I think it's problem with ipv4-ipv6 because in mplayer there are some uncritical error, and finally conect:

> jjgomera@ordenata:~/configuracion$ mplayer [http://a729.l830022151.c8300.e.lm.akamaistream.net/D/729/8300/v0001/reflector:22151](http://a729.l830022151.c8300.e.lm.akamaistream.net/D/729/8300/v0001/reflector:22151)
...
Playing [http://a729.l830022151.c8300.e.lm.akamaistream.net/D/729/8300/v0001/reflector:22151](http://a729.l830022151.c8300.e.lm.akamaistream.net/D/729/8300/v0001/reflector:22151).
Resolving a729.l830022151.c8300.e.lm.akamaistream.net for AF_INET6...
Couldn't resolve name for AF_INET6: a729.l830022151.c8300.e.lm.akamaistream.net
Resolving a729.l830022151.c8300.e.lm.akamaistream.net for AF_INET...
Connecting to server a729.l830022151.c8300.e.lm.akamaistream.net[213.254.229.159]: 80...
STREAM_ASF, URL: [http://a729.l830022151.c8300.e.lm.akamaistream.net/D/729/8300/v0001/reflector:22151](http://a729.l830022151.c8300.e.lm.akamaistream.net/D/729/8300/v0001/reflector:22151)
Resolving a729.l830022151.c8300.e.lm.akamaistream.net for AF_INET6...
Connecting to server a729.l830022151.c8300.e.lm.akamaistream.net[213.254.229.159]: 80...
Cache size set to 64 KBytes
Cache fill: 12.50% (8192 bytes)   

but with option -prefer-ipv4 on this error go away.

> jjgomera@ordenata:~/configuracion$ mplayer -prefer-ipv4 [http://a729.l830022151.c8300.e.lm.akamaistream.net/D/729/8300/v0001/reflector:22151](http://a729.l830022151.c8300.e.lm.akamaistream.net/D/729/8300/v0001/reflector:22151)
...
Playing [http://a729.l830022151.c8300.e.lm.akamaistream.net/D/729/8300/v0001/reflector:22151](http://a729.l830022151.c8300.e.lm.akamaistream.net/D/729/8300/v0001/reflector:22151).
Resolving a729.l830022151.c8300.e.lm.akamaistream.net for AF_INET...
Connecting to server a729.l830022151.c8300.e.lm.akamaistream.net[213.254.229.159]: 80...
STREAM_ASF, URL: [http://a729.l830022151.c8300.e.lm.akamaistream.net/D/729/8300/v0001/reflector:22151](http://a729.l830022151.c8300.e.lm.akamaistream.net/D/729/8300/v0001/reflector:22151)
Resolving a729.l830022151.c8300.e.lm.akamaistream.net for AF_INET...
Connecting to server a729.l830022151.c8300.e.lm.akamaistream.net[213.254.229.172]: 80...
Cache size set to 64 KBytes
Cache fill: 12.50% (8192 bytes) 


But i dont find in man of streamripper any option of ipv4

This problem happen whit fairly stations, majority 

Thanks in advance

---

