---
title: "Veteran Windows user - Just installed Ubuntu, confused!"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by NeptuneUK on 2007-08-18
I've managed to sucessfully install and boot Ubuntu! Then access the internet - epic win! 

Uber noob ftw!
\o/

Being such an experienced windows user has left me feeling rather uncomfortable in this envoironment as I have very little understanding of how things work. There's masses of information and downloads on the net but I don't know where to begin!

I have downloaded a couple of .bin files that I wish to install, from what I can make out from the documentation I am supposed to use the 'terminal' in applications and type : sudo aptitude install FILENAME

A load of funny stuff happens, then stops - I guess this means the file has installed correctly? :D

MAIN QUESTION : Why can I not set the resolution to the industry standard 1280x1024??!?
Everything is all pixelated and horrid! I assume there is a load of complicated codes and things to type in to change it from 1024 res, but that begs the question as to why it is missing from the menu in the first place?

---

### Post by taurus on 2007-08-18
1.  How to install stuff in Ubuntu, [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/).

2.  You just need to either install a driver for your graphic card so you can go higher resolution or reconfigure it again.  What graphic card do you have on your machine anyway?

---

### Post by NeptuneUK on 2007-08-18
I have an ATI x1950 series, that's the first thing I assumed! I have already downloaded the drivers from the site and typed the magic codes in the box to initiate the funky install. I guess I should reboot now?

edit: No change. Nothing appears to have installed. Why is it not possible to initialise installation of .bin files with a double click? I don't understand the logic behind the nature of typing things into the terminal thingy.

---

### Post by LowSky on 2007-08-18
> **NeptuneUK said:**
>  I don't understand the logic behind the nature of typing things into the terminal thingy.
 
You know you can install a lot of things with the add/remove option under Applications

---

### Post by NeptuneUK on 2007-08-18
How do I run something as a 'super user' when the sudo thing doesnt work?
This is needlessly complicated.
I will try and stick to the add/remove in future.

But I need to install drivers before adding programs and things.

---

### Post by NeptuneUK on 2007-08-18
Ive read and re-read the installing guide ([http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)) again and again, tried loads of different commands. Why can I not install some drivers?

I need to run it as a 'super user' .... I thought windows vista was bad when restricting your own privileges! (Ok so the vista comparison was a little harsh)

---

### Post by LowSky on 2007-08-18
in terminal type 
```
sudo -i
```

---

### Post by NeptuneUK on 2007-08-18
It asked me for the password finally! But it still wanted me to be a super user.

grr

---

### Post by taurus on 2007-08-18
> **NeptuneUK said:**
> Ive read and re-read the installing guide ([http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)) again and again, tried loads of different commands. Why can I not install some drivers?

I need to run it as a 'super user' .... I thought windows vista was bad when restricting your own privileges! (Ok so the vista comparison was a little harsh)

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by taurus on 2007-08-18
> **NeptuneUK said:**
> It asked me for the password finally! But it still wanted me to be a super user.

grr

And did you type in the same password that you are logging in with?  Remember, it won't echo on the screen what you type so make sure you type the right one and hit Return.

Otherwise, post the output of this command here to see if you are allowed to use sudo.

```
id
```

---

### Post by LowSky on 2007-08-18
> **NeptuneUK said:**
> Ive read and re-read the installing guide ([http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)) again and again, tried loads of different commands. Why can I not install some drivers?

I need to run it as a 'super user' .... I thought windows vista was bad when restricting your own privileges! (Ok so the vista comparison was a little harsh)

Type 
```
Sudo -i
```

type you regular password

the insatal what you need to do

---

### Post by NeptuneUK on 2007-08-18
It saays:


```
dan@DansPC:~$ id
uid=1000(dan) gid=1000(dan) groups=4(adm),20(dialout),24(cdrom),25(floppy),
29(audio),30(dip),44(video),46(plugdev),104(scanner),
113(netdev),114(lpadmin),116(powerdev),118(admin),1000(dan)

```

---

### Post by CSMatt on 2007-08-18
GNU/Linux (of which Ubuntu is a flavor of) was never deisigned to replace Windows.  It was designed to replace UNIX, which was the most popular OS in the early 1980s when the GNU project began.  This of course doesn't mean that you can't leave Windows for Ubuntu, but it does mean that you can't always rely on simplistic Windows-like methods, as most of them violate the UNIX philosophy (programs do one thing, but do it well).  Fifteen years of existence has brought about a lot of innovation to to GNU/Linux, which is why we have Add/Remove, a GUI, and other user-friendly programs, but a number of shortcomings that are out of the developers' hands prevent it from being a Windows replacement in the sense that Mac OS X is a Windows replacement.

One of these shortcomings is that ATI refuses to release the source code to their drivers, meaning that one who wants to get the full features of a recent card must rely on ATI's proprietary drivers, and are at the mercy of the original developers to fix bugs and release new drivers.  For this reason, people are reverse-engineering the cards and writing free drivers for them, however it takes at least a few months for hardware to be supported this way.  Ubuntu's philosophy is to not include proprietary drivers with the operating system unless they are absolutely necessary.  Because free drivers exist that at least allow you to use the display, it isn't necessary to include the drivers.  However these drivers are included on the Ubuntu servers for anyone who wants to use them.  You can install them by following the steps in the wiki page [here](https://help.ubuntu.com/community/BinaryDriverHowto/ATI).

In short: you've been looking in the wrong place for drivers.  95% of all Ubuntu-compatible software is provided by the Ubuntu servers, the rest is distributed in either binary form (which is what your BIN file is) or source form (which usually is in the form of tar.gz) from the provider.  When in doubt, always check to see if the program is supplied by Add/Remove first.

---

### Post by NeptuneUK on 2007-08-18
Thank you for the post, the drivers are set up properly and the display is no longer painful to view :D

I'll now continue my exploration of Ubunu, if I like it I will leave it on my Hard drive and use my other HDD for Vista.

I can already see that the OS runs smoother, I just need to get used to the huge differences!

---

### Post by steveneddy on 2007-08-18
To see the loads of software available to you in Ubuntu, go to the top tool bar, select System --> Administration --> Synaptic Package Manager.

There should be very little need for you to go out onto the internet to find software that you need.

Search the forums, for this is their purpose. Someone has asked your question before. Use the search feature.

Don't be scared to ask questions, but don't be rude. Everyone here is a volunteer, so needless ranting will not get you anywhere.

You need to learn the cpoy/paste feature in Linux. 

Highlight the word or phrase you want to copy. After it is highlighted, open up your terminal, then click the MIDDLE mouse button. This will paste any highlighted text here. Or anywhere else for that matter, not just in the terminal.

Try this:

Highlight this phrase

```
uname -a
```

open your terminal and try to paste it, then hit Enter.

When someone gives you code for the terminal, or you read in a forum about CP code, use this technique.

Please remember that you need to follow directions very carefully. Each step complete, then move on to the next step. Very important.

Good luck, we're all counting on you.

:popcorn:

---

