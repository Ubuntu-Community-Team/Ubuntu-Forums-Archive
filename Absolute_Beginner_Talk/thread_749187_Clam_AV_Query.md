---
title: "Clam AV Query"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by ex-wirecutter on 2008-04-08
I have just downloaded Clam AV anti virus and got the message that it had been installed ,
but I cant find it . Other packages I have downloaded in package manager have put a 
shortcut in the applications drop down , but after a couple of restarts nothing, cant even find it with search. Any ideas please.

---

### Post by Belliinator on 2008-04-08
I think its run in the terminal
(application->accessories->terminal)

try
```
 clam av -help
```

or

```
man clam av
```

to find out more

But it didnt install properly on my system because I stuffed up my dependencies, but for you it should be there.

---

### Post by Paqman on 2008-04-08
If you want a GUI front end for ClamAV then install [ClamTK](apt:clamtk)

BUT, you do know that you don't really need antivirus at all on desktop Linux, right?

---

### Post by compmodder26 on 2008-04-08
Clam AV is used from the command line.  There are separate GUIs you can use with it though.  Try clamtk, you should be able to find it through synaptic.

---

### Post by compmodder26 on 2008-04-08
Please disregard everything below.  Apparently the virus definitions are automatically checked up to 24 times a day.  If that seems excessive to you, you can edit the configuration file under /etc/clamav/freshclam.conf.  Just change the configuration option that says "Checks 24".

Ignore below:

One thing to note, I couldn't find a way to update the virus definitions from clamtk.  So you'll probably still have to do that from the command line, just type "sudo freshclam".

If you want to check for new definitions daily add a new file under /etc/cron.daily with the following lines:

#!/bin/sh
freshclam

You'll also need to make it executable. 
 Type: sudo chmod +x filename_you_gave_the_new_file

Obviously change "filename_you_gave_the_new_file" to the real name of the file

---

### Post by Cadmus on 2008-04-08
> **Paqman said:**
> If you want a GUI front end for ClamAV then install [ClamTK](apt:clamtk)

BUT, you do know that you don't really need antivirus at all on desktop Linux, right?

This may come acorss as harsh, please don't take it personally, just as a voice of caution.

I'd add a qualifer of "you don't really need antivirus **YET**" if you're running it as a desktop machine.

If you host or distribute files on your system (file server, web host etc) then there's a duty to make sure you don't propagate virii to other OSs used by your clients.

---

### Post by ex-wirecutter on 2008-04-08
Thanks for the prompt replies .
Opinion seems to be divided on the anti virus , some people say yes some say no , as a beginner I dont know so better safe than sorry.
Thanks again

---

### Post by Kevbert on 2008-04-08
It's very unlikely you'll get a Linux virus, but if you're running a Windows emulator and/or dual boot system, you may download Windows viruses.  ClamAV will find these for you.
If you run ClamTK you can update the virus definitions by typing  sudo clamtk  in terrminal and when ClamTK opens go to Help and then select update.

---

### Post by Paqman on 2008-04-09
> **Cadmus said:**
> This may come acorss as harsh, please don't take it personally, just as a voice of caution.

I'd add a qualifer of "you don't really need antivirus **YET**" if you're running it as a desktop machine.


No, I agree completely. Desktop Linux is growing at a very fast rate, and if it continues to do so we'll eventually reach a point where we'll need additional protection.

For more reading about Linux security, try the ever-helpful [Psychocats](http://www.psychocats.net/ubuntu/security)

NB: This only applies to desktop machines. Servers need to be a lot more careful.

---

### Post by Kevbert on 2008-04-09
> **Paqman said:**
> No, I agree completely. Desktop Linux is growing at a very fast rate, and if it continues to do so we'll eventually reach a point where we'll need additional protection.

For more reading about Linux security, try the ever-helpful [Psychocats](http://www.psychocats.net/ubuntu/security)

NB: This only applies to desktop machines. Servers need to be a lot more careful.

Useful page, thanks Paqman.

Another page worth looking up is the Gibson Research webpage [http://www.grc.com]("http://www.grc.com")  They've been going for a few years.
Most of the items are for Windows, but a very useful utility is ShieldsUP! which will scan for all open ports and works fine with Ubuntu.

---

### Post by SOULRiDER on 2008-04-09
> **Kevbert said:**
> It's very unlikely you'll get a Linux virus, but if you're running a Windows emulator and/or dual boot system, you may download Windows viruses.  ClamAV will find these for you.
If you run ClamTK you can update the virus definitions by typing  sudo clamtk  in terrminal and when ClamTK opens go to Help and then select update.

Having an AV in Linux is useless for two reasons:

1) If you find a virus for Linux it means you have some very very very very very bad luck.
2) AV software for Linux doesnt even scan for Linux viruses....

---

### Post by Kevbert on 2008-04-09
I agree Soulrider.  However I have a dual boot system (WinXP/Ubuntu) and have downloaded some games which run under DosBox.  I also unknowingly downloaded four old Windows viruses which were found by ClamAV.  The point is that I use a shared data drive for both OS, so it's possible that XP could become infected.  The other possibility is that by having viruses on my machine, I could end up sharing viruses with anyone I email, especially if they run Windows.

---

### Post by Adbru on 2008-04-22
Hi Guys,

I was about to ask a similar question to the OP but found the answers here :)

many thanks.

Adbru

---

