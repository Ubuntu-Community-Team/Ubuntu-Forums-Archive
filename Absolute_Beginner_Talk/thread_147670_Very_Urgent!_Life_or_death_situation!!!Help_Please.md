---
title: "Very Urgent! Life or death situation!!!Help Please!!!!!!"
date: 2006-03-20
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-03-20
I'm sorta new to ubuntu just so you know.
Anyway I was happily using firefox until last night when it simply won't start.  It was working fine before.  It just opens the minimized box that says "starting firefox" but after a while it simply closes.  I need the internet urgently for my business and I am on a deadline so if anyone can help please do so asap.
Thank you in advance.

---

### Post by timas on 2006-03-20
Open a console window and type 'firefox' see what it says.. copy that info here so that other people might get an idea of whats going wrong

---

### Post by user1397 on 2006-03-20
Thanks for the reply.
It just goes:
myusername@mycomputer'sname:~$
so basically nothing happens!

---

### Post by user1397 on 2006-03-20
As a side note yesterday I found a virus that had something to do with the win32 codecs, but I quarantined and removed it with aegis virus scanner.

---

### Post by neoflight on 2006-03-20
[QUOTE=erik1397]As a side note yesterday I found a virus that had something to do with the win32 codecs, but I quarantined and removed it with aegis virus scanner.[/QUOTE]

try reinstalling FF using synaptic... ??? did u try that?

---

### Post by WelterPelter on 2006-03-20
Well, I'm sure you've already done this, but I would try re-installing Firefox post haste.

---

### Post by KansasJoe on 2006-03-20
don't know what the problem is but you can dl and use opera instead until you figure out the problem if it's that urgent

---

### Post by rattking on 2006-03-20
a local setting or plugin could be hoseing firefox up
you can try over from the defaults.. just move your settings dir out of the way
mv .mozilla .mozilla.bak
then try to run firefox agian
if that does not work you can restore your settings by moveing .mozilla.bak to .mozilla agian and your no worse off

---

### Post by rfruth on 2006-03-20
Quite possibly your Firefox profile folder got corrupted [http://kb.mozillazine.org/Profile_folder]("http://kb.mozillazine.org/Profile_folder")
while you try to straighten that out use the package manager to download a completely different browser such as mozilla-browser, you won't have your bookmarks etc but you'll be back on the web ;)

---

### Post by timas on 2006-03-20
I'm not this deep into the workings of it all yet.. so I'm really cracking my head on what you can do in order to get some debug info..  perhaps the scanner also found a few firefox files unclean and put them in quarantee.. I'd check to see if the virus scanner shows any files in a log or somesuch..
A few other options are:
- Re-install firefox (either by a re-install, or by a remove and install)
- Temporarily use a different browser while you work on solving this issue.. it might take more time than you can afford it to take.. 
- try running firefox with a log file hooked to it.. something like "firefox > ~/firefox-log" .. I however doubt this is going to give you any output at all if the command line doesn't give any.. its worth a try, though.

Sorry I can't be of more assistance, one of the gurus should probably be able to

Edit: Sorry bout the double post.. ya'll posted in the time it took me to write this post out :P

---

### Post by user1397 on 2006-03-20
Thank you all.
I just installed the epiphany, galeon, and mozilla browsers for my urgency but I will come back and read this when I can because I still want my firefox to work!

---

### Post by Luke on 2006-03-20
use the machine you're posting from ?

---

### Post by user1397 on 2006-03-20
Ummm how can you make pictures in ubuntu open up in windows.
I sent a pic with my email to a windows computer and when I try to open it there it can't.  It can't open it with windows picture viewer, nor paint, nor explorer, nor any program possible.  In ubuntu, its a jpeg file.  Shoudn't it work on windows???

---

### Post by ncappel1 on 2006-03-21
I've had similar problems, where the browsers just don't work. if you really need to just use the internet, there is a VERY minimalist application that comes preinstalled. just go into a terminal and type: w3m [internet site]

to pull up google, it would be 
```
 w3m www.google.com
```

the mouse won't do much and pictures won't show, but you can move around with the keyboard. to select something, use the "enter" key.

good luck with your deadline!

edit: I was wrong about not being able to use the mouse!

---

### Post by tuxinvader on 2006-03-21
did firefox crash last time you ran it?

open a console and run 

  $ ls -l .mozilla/firefox/*.default/lock

If you see a file there, delete it and then re-launch firefox

---

### Post by user1397 on 2006-04-15
Just if you guys wanted to know I did fix my firefox simply by reinstalling it with automatix
Sorry about the uber-late reply and thanks for all the replies

---

