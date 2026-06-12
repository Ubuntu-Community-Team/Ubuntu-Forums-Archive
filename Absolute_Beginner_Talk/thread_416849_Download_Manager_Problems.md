---
title: "Download Manager Problems"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by dthatcher on 2007-04-21
Hi all! I have been fairly successful with the latest Ubuntu. However, I cannot get download managers to work. I have tried WXDFast and Retriever Download Manager and the same thing happens. I go to the application menu to open them and they come up for a fraction of a second then disappear. Same thing happens if I launch them from Firefox using FlashGot. I don't know what to do. Is anyone else successfully running a linux download manager on Feisty? Thanks

---

### Post by seshomaru samma on 2007-04-21
I'm running Dapper so I don't know about feisty 
however i usually use downloadthemall with firefox and k-get 
both work reasonably well

---

### Post by peter07 on 2007-04-21
Something wrong is with Firefox & Flashgot. When downloader (gwget, d4x or something else) is lunched before download everything is correct, but when I just click the download nothing happens :confused:

---

### Post by dthatcher on 2007-04-22
Fortunately, I am able to get KGet to work with FlashGot and Firefox nicely. But that is it so far.

---

### Post by peter07 on 2007-04-24
Download managers work only when they are launched first. I've tested Downloader for X and GwGet.

Somebody else have noticed that problem??

---

### Post by löwe on 2007-04-25
Hi,

I have the same problem with Feisty.

In Dapper it seems to work fine, and if d4x doesn't run when I download with flashgot, it's startet.

---

### Post by peter07 on 2007-04-25
After some research I think only GwGet has some real problems:

Why d4x doesn't work:
> Downloader 4 X users: you should upgrade to version 0.5.98.070331, due to a regression in current stable version which limits Downloader 4 X support to the older (nt) interface. Sorry for this inconvenience.
( [http://flashgot.net/](http://flashgot.net/) )

So switch to d4x (nt) in flashgot options or install new version.

---

### Post by vertigo1980 on 2007-04-27
> I have tried WXDFast and Retriever Download Manager and the same thing happens. I go to the application menu to open them and they come up for a fraction of a second then disappear. Same thing happens if I launch them from Firefox using FlashGot

wxDownload Fast disappears for me too, under feisty. anyone know a way around this?

---

### Post by vertigo1980 on 2007-04-28
anyone?...

---

### Post by Gavin77 on 2007-04-28
There's a Firefox extension called Downthemall that's worth checking out, I like it.
[http://www.downthemall.net/](http://www.downthemall.net/)

---

### Post by vertigo1980 on 2007-04-29
compiled it myself, all is well :)

---

### Post by PuppetMaster2070 on 2007-07-05
I'm having the same problems with wxd fast
I installed wxwidgits but still have error messages:in the make command :

[PHP]make[3]: *** [BoxFind.o] Error 1
make[3]: Leaving directory `/home/puppetmaster/Desktop/D/ubuntu/wxdfast-0.6.0/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/puppetmaster/Desktop/D/ubuntu/wxdfast-0.6.0/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/puppetmaster/Desktop/D/ubuntu/wxdfast-0.6.0'
make: *** [all] Error 2
[/PHP]
 
What should I do???

---

### Post by PuppetMaster2070 on 2007-07-05
Please anyone help me?
this problem is making me insane

---

### Post by war59312 on 2007-12-30
Same here, not only does Retriever Download Manager open and close real quick but it kills part of the GUI and have I to reboot to get it back. The top part, where you have the minimize, maximize, and close buttons. The title bar also vanishes. Really strange...

---

