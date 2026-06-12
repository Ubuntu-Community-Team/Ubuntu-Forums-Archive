---
title: "Best Linux for a 266?"
date: 2006-05-28
forum: Absolute Beginner Talk
---

### Post by halftoke on 2006-05-28
Okay, I know the obvious question is going to be "why are you still using a 266?". This is an older (intentional understatement) Compaq Presario 1625 laptop. It has a 266MHz processor, a 3GB HD and 128MB RAM.

I *was* running XP Pro on it until I installed Ubuntu (breezy) on it. Ubuntu runs *much* better than XP or w98 did, altho it is rather slow. Is there a flavor of Linux better suited to older machines?

~halftoke

---

### Post by ed_agamemnon on 2006-05-28
try Puppy or Damn Small Linux

---

### Post by user1397 on 2006-05-28
did you try the XFCE desktop environment yet? aka xubuntu?  it is a small and lightweight desktop environment (de) that is best for low-end machines.  to install it, follow this guide: [http://www.psychocats.net/ubuntu/xubuntu.php]("http://www.psychocats.net/ubuntu/xubuntu.php"), and pay attention to the **"Adding XFCE to an existing Ubuntu/Kubuntu" **, because you just want to install it as an alternate desktop environment, you wouldn't want to reinstall ubuntu, unless of course you don't mind backing up important data and reinstalling ubuntu. if you don't mind, then you would use the **"Installing XFCE"** part of the article.

---

### Post by Belathor on 2006-05-28
If you have high speed internet and a cd burner you could also download Xubuntu Dapper Final when it comes out in like 4 days.

---

### Post by user1397 on 2006-05-28
[quote=Belathor]If you have high speed internet and a cd burner you could also download Xubuntu Dapper Final when it comes out in like 4 days.[/quote]
ah yes, i would recommend this, so forget about what i said ;)

---

### Post by %hMa@?b&lt;C on 2006-05-28
iceWM shoudl run ok on that.  i highly suggest using DamnSmallLinux, it is best suited for that tyope of machine

---

### Post by Engnome on 2006-05-28
[QUOTE=erik1397]did you try the XFCE desktop environment yet? aka xubuntu?  it is a small and lightweight desktop environment (de) that is best for low-end machines. .[/QUOTE]

fluxbox is even more lightweight. Its in the repo's

sudo apt-get install fluxbox

then choose it in the session menu at login.

---

### Post by clarkth on 2006-05-28
I put ZenWalk on an old PII 300 MHz with 128 MB RAM.  Works well enough for my mother-in-law for web surfing, email, etc.

---

### Post by Sutekh on 2006-05-28
Maybe Openbox?  By itself, its very light.

```

sudo apt-get install x-window-system-core xterm gdm openbox obconf menu firefox synaptic
sudo /etc/init.d/gdm start
``` 
These are some helpful links for installing/configuring

[Openbox Web Page]("http://www.icculus.org/openbox/")

[Ubuntu Wiki - Openbox]("https://wiki.ubuntu.com/Openbox")

 This link is for Breezy, but works fine for Dapper.

[Ubuntu Forums - How to use Openbox in GNOME and by itself.]("http://www.ubuntuforums.org/showthread.php?t=75471")

This last link is for the Openbox menu editor, which is very useful.

[Openbox Menu Editor]("http://sourceforge.net/projects/obmenu")

---

### Post by confused57 on 2006-05-28
Ubuntu Lite maybe:

[http://www.ubuntulite.org/dokuwiki/doku.php?id=repositories](http://www.ubuntulite.org/dokuwiki/doku.php?id=repositories)

[http://ubuntuforums.org/showthread.php?t=98233](http://ubuntuforums.org/showthread.php?t=98233)

I think you'd need to do a server install of Ubuntu before installing UbuntuLite and I think also for Sutekh's instructions.  You may want to read through the 2nd link I listed  to get an idea what UbuntuLite can do.

---

### Post by halftoke on 2006-05-28
***Zounds!*** 9 replies is less than an hour? I *love* this forum...

The amount of information here is amazing. I use this machine primarily at work. Tasks include:
[LIST=1]
[*]wireless networking (I use this box to detect bugs in the WiFi in an 86 room hotel).
[*]rdc to my server so I can work anywhere in the hotel
[*]monitor security cameras via http
[*]surf the web (of course)
[*]email
[*]some basic office functions; word processor, text editor, spread sheets and db queries.
[/LIST]

obviously, I am not doing any multitasking with this box, nor do I expect to be able to do much. Is it possible to do all of the above with any of the aforementioned flavors of Linux?

(As a side note, I have a 566MHZ, 128MB RAM box running W2K as a guest use computer in the hotel lobby [email, websurfing, printer], and intended to replace the OS with breezy. Any sugestions?)

---

### Post by IYY on 2006-05-29
I believe all the distros mentioned in this thread are Debian based, so you'll be able to add whichever components may be missing via apt-get. Personally, I'd suggest either Damn Small Linux (DSL), or Ubuntu with Fluxbox or IceWM as the display manager. 

You should install Dapper on the 566 MHz machine (after you check with a LiveCD to see if your printer is supported).

---

### Post by halftoke on 2006-05-29
Reconfiguring the 566 box is going to be down the road a bit, at least until I get this 266 laptop the way I want it. I installed FluxBox (using it as we speak) and am happy with the improvement. I'm looking at DamnSmallLinux and wondering if that will be even more of an improvement...

I'd always heard that Linux (besides its obvious other advantages) was the OS to use when trying to bring life back to old pc's. Now I believe it. My General Manager was dead set *against* any kind of install other than windoze on *any* of our machinges here. That is until I said the magic word, "free". Now he's all over the idea.

---

