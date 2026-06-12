---
title: "Simple .bin problem (I think)"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by kaban13 on 2008-03-15
[SOLVED - see below]

So here's the quick back story: I'm using a fresh install of 64-bit Ubuntu Gutsy(7.10), the only thing I've done is enable the restricted nVidia graphics driver, and install the 190-some recommended updates.  This computers intended use is for a dedicated Counter Strike Source server.  I've been following the first step of the guides I find online.  Unfortunately, that's where I run into this problem, which I can't seem to find anywhere by searching (although I'm not a terribly good searcher).

I have to download a file called hldsupdatetool.bin.  So, I wget that from steampowered.com/download/hldsupdatetool.bin which all goes smoothly, then I chmod +x hldsupdatetool.bin to make sure it's executable, then I have the problem, which I'm assuming is very simple:

I type this:
```
./hldsupdatetool.bin
```
And get this:
```
bash: ./hldsupdatetool.bin: No such file or directory
```

So, I'm stumped.  I'm typing this command from the directory that hldsupdatetool.bin is in.  Maybe there's something that wasn't installed, or something that I need to add to the system, but, from what I've read about problems with .bin files, I've never seen anything about them not being there. (Also tried it with sudo, still not there.)

Thanks in advance for your help.  Sorry if the question has been asked before.

[Solution]
I randomly came upon another forum where this same question was asked.  The answer: you have to apt-get this:
```
apt-get install lib32gcc1
```

I'm not sure exactly how it works, but it allowed me to find and install the file sucessfully, so, I'll take it.

Thanks again to everyone who responded.

---

### Post by Rocket2DMn on 2008-03-15
You need to set executable permissions on it
```
chmod +x hldsupdatetool.bin
./hldsupdatetool.bin
```

---

### Post by joshrobinson on 2008-03-15
the only thing i can think of is your terminal isnt in the right directory, as it cant seem to find the file, are you 100% positive you are in the right directory

> **Rocket2DMn said:**
> You need to set executable permissions on it
```
chmod +x hldsupdatetool.bin
./hldsupdatetool.bin
```

the op stated in the thread that this was already done

---

### Post by handydan918 on 2008-03-15
From the directory where this file is suposed to reside, post the output of ls -l.

---

### Post by kaban13 on 2008-03-15
Yeah.  I'm in the right directory.  I'm also fairly confident that the file downloaded correctly:
```
steve@steve-serv:~/srcds_l$ ls -l
total 3436
-rwxr-xr-x 1 steve steve 3513408 2005-09-01 22:27 hldsupdatetool.bin
steve@steve-serv:~/srcds_l$ ./hldsupdatetool.bin
bash: ./hldsupdatetool.bin: No such file or directory
steve@steve-serv:~/srcds_l$ sudo ./hldsupdatetool.bin 
[sudo] password for steve:
sudo: unable to execute ./hldsupdatetool.bin: No such file or directory
steve@steve-serv:~/srcds_l$ 

```

What program or, ummm, thing, is it that executes this file when I type ./hldsupdatetool.bin?  Cause, if it's something I can find through synaptic or something, I might as well check to make sure it's installed.  

Thanks for your quick responses.

---

### Post by handydan918 on 2008-03-15
I'm really whistling in the dark here, but what about prepending <sh> before the <./>  ?

---

### Post by kaban13 on 2008-03-15
I tried a bunch of random commands to try and get something.  As for that one in particular:
```
steve@steve-serv:~/srcds_l$ sh ./hldsupdatetool.bin 
./hldsupdatetool.bin: 1: Syntax error: "(" unexpected

```

Another random question.  Is there any way to execute these kinds of files from the file-browser?  On a different system, I remember being able to execute shell script files from the file manager.  Then again, this this isn't a shell script.

---

### Post by kaban13 on 2008-03-15
So, I just tried doing the three basic commands on my Xubuntu 32 bit install on my laptop, and they worked flawlessly.  So, might this have something to do with the fact that it's a 64 bit install?  Maybe this file doesn't support 64 bit, or maybe it's a problem with Ubuntu.  Any ideas?

---

### Post by handydan918 on 2008-03-16
Yeah, I can see how 64bit might be a problem...I'd get with citrix to be sure they bon't have a 64 bit version before despairing, tho.

[rant]
This is a prime example of why 64 bit is nearly useless. Anything slightly proprietary, and you're scrod! 
All because Windows hasn't gotten 64 bit right for 5 years...
[/rant]

---

