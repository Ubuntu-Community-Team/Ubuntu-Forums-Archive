---
title: "Streaming MMS + weird hibernation"
date: 2005-06-29
forum: Absolute Beginner Talk
---

### Post by Nanaki on 2005-06-29
Hi,

First of all, after playing around with Ubuntu a couple of days, it rules! :) The only real problem I have some trouble ejecting some CD's, but I can live with that.

Now, my questions.
1. Is it possible to stream MMS? I installed all codecs, but when I try to stream MMS, Totem opens up and gives an "URI missing" (or such) error.

2. When I choose "Hibernate this computer", it gives me a login window and then a screensaver. Is this normal behaviour? I prefer the Windows behaviour of writing all RAM contents to HDD and then shut down the computer. Can this be achieved with Ubuntu?

Thanks in advance,

---

### Post by Mr. Electric Wizard on 2005-06-29
Do you mean stream content from a remote machine _**to**_ XMMS?

---

### Post by Nanaki on 2005-06-29
Yeah, just view streams from a server on my monitor. :)

---

### Post by Mr. Electric Wizard on 2005-06-29
The only real way I've seen that you can stream remote files to XMMS, or any other music player for that matter is by doing an SMBMOUNT, and mounting to a location....
This is different than browsing to your shared folder through nautilus.
Lookup mount to location.
This is a good thread that should get you up to speed on that:
[http://www.ubuntuforums.org/showthread.php?t=26438&highlight=smb+security](http://www.ubuntuforums.org/showthread.php?t=26438&highlight=smb+security) 

After you have a remote share mounted on your linux box, XMMS willl essentially see thse files as residing on the linux box.
You will be able to stream music then...
I did this for all my music shares, picture shares, and video shares. :razz: 

That's the trick though, to actually mount the remote folders...

---

### Post by Nanaki on 2005-06-29
[QUOTE=Mr. Electric Wizard]The only real way I've seen that you can stream remote files to XMMS, or any other music player for that matter is by doing an SMBMOUNT, and mounting to a location....
This is different than browsing to your shared folder through nautilus.
Lookup mount to location.
This is a good thread that should get you up to speed on that:
[http://www.ubuntuforums.org/showthread.php?t=26438&highlight=smb+security](http://www.ubuntuforums.org/showthread.php?t=26438&highlight=smb+security) 

After you have a remote share mounted on your linux box, XMMS willl essentially see thse files as residing on the linux box.
You will be able to stream music then...
I did this for all my music shares, picture shares, and video shares. :razz: 

That's the trick though, to actually mount the remote folders...[/QUOTE]
 Thanks for the help. :) Altho that answers one of my future questions, it wasn't what I meant now. I prob explained it wrong, but I just mean online MSS streams. Stuff that you click on in Firefox and (in Windows) that Windows Media Player starts streaming. Looking for a way to do that in Linux too. :D

---

### Post by Mr. Electric Wizard on 2005-06-29
Oops, there I go jumping the gun again...
Good question, I'll try tonight...

---

### Post by Mr. Electric Wizard on 2005-06-29
I just streamed tonight from [www.shoutcast.com](www.shoutcast.com) and from [www.somafm.com](www.somafm.com)
If you have xmms installed, then when the dialog box comes up and asks you what program you want to open the file with, just select xmms.
It works really well! :)

---

### Post by loon on 2005-07-06
What if you didn't mean to check "remember my selection" or something, so now all it does is bring Totem??  

;/

---

### Post by Bl0wn2b1ts on 2005-07-06
thats a good question!

where would we find the equivalent of the file extension app associations from windows in ubuntu?

thanks in advance!  :-P

---

### Post by Mr. Electric Wizard on 2005-07-06
If you save the target of the streamed radio station, ".pls" I believe, then save it to disk.
Then right click the file and associate the file extension to XMMS under properties, I believe, and you should be good to go... :grin:

---

### Post by Nanaki on 2005-07-06
Maybe try to go to Edit -> Preferences -> Downloads -> File Types.

Anyway, thanks for the help Mr. Electric Wizard, I forgot to say that. :)

---

