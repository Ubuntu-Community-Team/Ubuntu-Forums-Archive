---
title: "Please Help me get started"
date: 2005-09-10
forum: Absolute Beginner Talk
---

### Post by gerrenj on 2005-09-10
I just installed UBUNTU. On the boot screen, I put in my id and password, but how do I get pass that point. It says that I have mail then it has my my user name @ UBUNTUhome:$  What command opens UBUNTU? Please help; I am ready to see what this OS is all about.

---

### Post by mlomker on 2005-09-10
Not good.  It sounds like the system has a problem with your video card.  Try typing this at the prompt and see what errors you get:

**startx**

---

### Post by aysiu on 2005-09-10
Did you do an expert install? If you did, you may not have installed X (which you need for a graphical user interface).

---

### Post by John.Michael.Kane on 2005-09-10
You installed the server/base version. you will have to re-install. do not type anything at the boot promt just press enter. 


And welcome to Ubuntu/gnu-linux

---

### Post by gerrenj on 2005-09-10
when I type startx, nothing happens.  I ordered the UBUNTU cd from a company online and it automatically installs, then asks me a couple of options to get started.  Well it doesn't look good for me right now.  Does anyone have any suggestions for another linux product besides UBUNTU?

---

### Post by Gary Powers on 2005-09-10
Don't quit so soon!

If you are able, download the Hoary release for Ubuntu (takes maybe half an hour on broadband), then burn it to CD and install.  I have been on Ubuntu for about nine months and while I have tried (and still use) other Linux distros, Ubuntu is by far and away the best.

And the forums here are excellent.  I've found nothing like it with other distros.

As someone said earlier, it sounds like you don't have X installed and that is needed for your GUI.  

Stick around the folks here will get you up and running  :).

Gary

---

### Post by poofyhairguy on 2005-09-10
[QUOTE=gerrenj]when I type startx, nothing happens.  I ordered the UBUNTU cd from a company online and it automatically installs, then asks me a couple of options to get started.  Well it doesn't look good for me right now.  Does anyone have any suggestions for another linux product besides UBUNTU?[/QUOTE]

Don't give up unless you don't have broadband. If you do, put in:

> sudo apt-get update

and then 

> sudo apt-get install ubuntu-desktop

tell it yes and let it do its thing.

If that doesn't work, I advise SUSE or Mepis Linuxs.

---

### Post by gerrenj on 2005-09-11
I did everything that poofyhair said, and after that here is what it said:
reading pachage lists...Done
building dependency tree...done
E: couldn't find package UBUNTU

I have DSL and it will take 2 hours to download the live cd.  Is that normal?
I hve spent the last 4 days just trying to get the desktop to come up.  Is that normal?

---

### Post by sneax on 2005-09-11
Is it normal? It depends what you define as 'normal' ;) I don't think you should go through so much trouble, so no it's not normal. This is what I would do:
- Download the distro from the net and burn to cd (don't download the live cd, go with the 'install' cd, make sure you get the right stuff - read the download page)
- Install it, I think the installer could be much better but just try to get through it!

Once you installed it should boot into a graphical prompt asking for your username and password which you entered during the install.

---

### Post by Kvark on 2005-09-11
[QUOTE=gerrenj]I did everything that poofyhair said, and after that here is what it said:
reading pachage lists...Done
building dependency tree...done
E: couldn't find package UBUNTU

I have DSL and it will take 2 hours to download the live cd.  Is that normal?
I hve spent the last 4 days just trying to get the desktop to come up.  Is that normal?[/QUOTE]
No, that is definately not normal, your install went wrong somewhere.

Try to install again from the CD already have. Maybe you picked the wrong option somewhere so it didn't install the graphical user interface stuff.

If reinstalling doesn't work then maybe the CD is borked. Download the *install CD* (not the live CD) from [www.ubuntu.com](www.ubuntu.com) . Go watch TV or something if it takes too long, or try another mirror or the BT download. Most of Ubuntu's mirrors are very fast, at least for me. When you burn the CD, make sure use the "burn image", "burn from image" or "whatever your CD burner program calls it" option.

---

### Post by gerrenj on 2005-09-16
Okay, not to sound too cheesy; I am finally up and running and I am so excited.  Okay, I went to my computer expert guy, (he runs KDE) and he hooked me up.  I wish I knew what his forum name was so I could give him props.  Anyway, the problem was that he had to install my NVIDIA card.  I'm sure some of you know that you can go on the web from the boot screen.  He then installed the driver manually, then reinstalled UBUNTU.  Then I logged on here and let him see what you all said that replied and 5 minutes later  :-P   SWEEEET.  Okay now I'm ready to discover what you all are talking about.  Thank you everyon that responded.

---

