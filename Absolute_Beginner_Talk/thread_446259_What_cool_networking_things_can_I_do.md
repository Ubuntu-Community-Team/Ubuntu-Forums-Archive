---
title: "What cool networking things can I do"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by tomt on 2007-05-16
So i have two laptops running Ubuntu now (both rescued after Windows had fouled up). I want to know what the coolest things I can do around home networking. Id love to be able to share files, control one remotely etc etc etc.

So I have two laptops.

A belkin wireless router

An X-box 360 (is there anyway I can stream to it)

My girlfriend also has a lap top however it runs windows-provided her connection to the internet is not interrupted! she does not need to be included on the network-I think it should stay strictly ubuntu only (Im partly hoping shell want to convert through envy (gee how geeky is that).


Anyway I look forward to hearing your suggestions!

Best.

tomt

---

### Post by chamberlain2006 on 2007-05-16
That is a VERY broad question.  Personally, I share files, have a web server, connect remotely, and share my internet on my PC.  So it's not really a question of what you can do, but more what you want to do.

---

### Post by jms830 on 2007-05-17
softmod an original xbox, put xbox media center (xbmc) on it, and samba share files on your computer. Then you will be able to stream videos, music, photos, whatever to your original xbox & tv. I dunno how to stream to the 360, as I don't think it supports samba shares. Use google for more details.

---

### Post by brundles on 2007-05-19
You can stream some files to the 360 using something called [uShare](http://ushare.geexbox.com). The only catch is that the current version (0.9.10) doesn't work. A patch has been sent to the developer though (I can post it here if you need it) and it streams hi-def WMVs very nicely :).

XBMC is (damn) good but doesn't have the grunt to cope with hi-def content.

---

### Post by tomt on 2007-05-19
cheers. bearing in mind I am a moron...i can or cant use ushare to watch stuff on my 360. currently the 360 doesnt even seem to notice my ubuntu laptops.

---

### Post by brundles on 2007-05-20
It won't unfortunately. MS designed the 360 to only talk to XP MCE or Vista. Without them you need to setup a uPnP server with the relevant tweaks (you just know MS can't leave an open standard alone!!). This is where uShare comes in.

Once you have uShare up and running it will see the computer it's installed on and be able to stream from it.

---

### Post by tact on 2007-05-20
Yerrrr... (I know nothing about xbox's) but all the rest of the stuff you mention is easily done.

I have a similar home set up..  a router connected to broadband internet.

I have ubuntu, wife's laptop is winXP.   We share files.  I have streamed media to her (used VLC to stream, and she had the win version of VLC to receive - so very basic).   

Also if the winXP box is set to accept incoming remote connections (Control Panel>System>remote tab) I have used Applications>Internet>Terminal Server Client to take control of her desktop.

---

### Post by noname101 on 2007-05-26
I have made packages of the patched ushare for ubuntu. I also have a how to.
[Link]("http://linux.vanvalkinburgh.org/2007/05/25/stream-videos-to-xbox-360-with-patched-ushare/")

On that link above I also have instructions for converting video files to MPEG 4. Assuming you have the latest update that lets you play MPEG 4 videos.

---

