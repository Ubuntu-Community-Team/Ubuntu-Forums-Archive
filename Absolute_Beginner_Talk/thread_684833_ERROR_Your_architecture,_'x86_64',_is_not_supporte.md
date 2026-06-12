---
title: "ERROR: Your architecture, \'x86_64\', is not supported"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by Nazty_Nayt on 2008-02-01
ERROR: Your architecture, \'x86_64\', is not supported by  the Adobe Flash Player installer is I keep runnning into trying to get this whole flash thing straitened out.

I've looked around and seen people with the same problem, seems to be common lately.  So basically I'm at the first step right now, when I type in 
-------------------
wget [http://fpdownload.macromedia.com/get/flashplayer/c](http://fpdownload.macromedia.com/get/flashplayer/c) urrent/install_flash_player_9_linux.tar.gz
-----
I get this
----
Resolving fpdownload.macromedia.com... 96.6.130.70
Connecting to fpdownload.macromedia.com|96.6.130.70|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
13:57:28 ERROR 404: Not Found.

--13:57:28--  [http://urrent/install_flash_player_9_linux.tar.gz](http://urrent/install_flash_player_9_linux.tar.gz)
           => `install_flash_player_9_linux.tar.gz'
Resolving urrent... failed: Name or service not known.

FINISHED --13:57:28--
Downloaded: 0 bytes in 0 files
--------------------------------------

So Naturally I have no idea what to do now, and yes I am on AMD64.  Can anyone help me out here?

---

### Post by jan quark on 2008-02-01
read this perhaps it helps
[http://ubuntuforums.org/showthread.php?t=669038&page=2](http://ubuntuforums.org/showthread.php?t=669038&page=2)

---

### Post by Thelasko on 2008-02-01
If you look on the 64 bit section of the forums there is all kinds of information.  Ubuntu 7.10 should resolve this issue automatically, if you are on Ubuntu 7.04 you need to run [Kilz's script.]("http://ubuntuforums.org/showthread.php?p=1174435")  Read on there is plenty of information on this subject here on the forums.

Yes, Flash works on 64-bit, don't let anyone tell you otherwise!

---

### Post by Nazty_Nayt on 2008-02-01
I didn't know 7.10 was out already, I think I'll probably just upgrade to that instead.  Ok, I went to the update manager, and there's no new version there.  I also ran the update for the update manger in the command line, followed by the sudo apt get install update manger and still nothing.

**UPDATE** NVM, I'm retarded I'm already on 7.10, I though you were referring to Heron, I didn't think it was out yet.  So then if 7.10 is supposed to auto fix this problem, why am I having it?

---

### Post by Thelasko on 2008-02-01
Ok, since I know you are running 7.10, all I had to do was go to a site that contains flash, like youtube, using firefox and the little puzzle piece appears at the top of the browser notifying you to install the plugin.  Click that install missing plugin button and it should give you two options:
1. install Flash
2  install Gnash
Click the Flash option and ok and wait a few minutes and your done.  That's it.  If that didn't work let us know.

---

### Post by jan quark on 2008-02-01
I would not install both gnash and flash

there were compatibility issues when they were installed both

---

### Post by Nazty_Nayt on 2008-02-01
Ok, well I should of specified earlier, I got flash somewhat working already, basically sometimes it works sometimes it doesn't.  For some flash players, it's lines and messed up, some on youtube play fine, but some on youtube don't play at all.  I don't know if this helps or makes my problem worse.

---

### Post by Thelasko on 2008-02-01
Your sure you installed Flash and not Gnash?  In my experience Gnash is very buggy.  I've noticed some quirks in Flash, but not like you are describing.  It's very minor.

---

### Post by Nazty_Nayt on 2008-02-01
Nope, I don't have either of the gnash programs installed in Add/Remove

---

### Post by Thelasko on 2008-02-01
This I don't know how to fix.  You can try uninstalling flash and reinstalling.  If that doesn't work I recommend posting a new thread on the X86 64-bit group.  Make the title something about Flash being glitchy.  Don't say anything about flash not being supported on 64-bit because it will tick people off.  There are some people who are very knowledgeable in that group particularly Kilz.  I'm sure you will get plenty of replies.

Be as specific as possible about what your computer is doing.  It helps!

Sorry I can't help:(

---

### Post by Kilz on 2008-02-01
[Try this sticky post.]("http://ubuntuforums.org/showthread.php?t=476924") :D

---

### Post by Nazty_Nayt on 2008-02-01
Ok, well I ran that with no problems everything completed, and it didn't change anything.  I've been dealing with this all day, and it's not even worth it anymore, it's only on a few sites so I'll live.  I'll just wait for the new Ubuntu to come out and see if that chanes anything.  I really appreciate everyones help though, thanks alot.  :)

---

