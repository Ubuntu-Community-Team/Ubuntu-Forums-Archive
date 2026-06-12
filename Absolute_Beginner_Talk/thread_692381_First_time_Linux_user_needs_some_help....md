---
title: "First time Linux user needs some help..."
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by patrick0605 on 2008-02-09
Hey everyone, I've finally decided to swap over to the Linux world, because frankly Vista is annoying.  

Last night I installed Ubuntu 7.10 on my Lenovo laptop.  It worked fine the first time I logged in, but now I'm sitting here with nothing.  I rebooted back into Vista to upload a picture, then I wanted to swap back into Ubuntu.  I get past the initial loading screen, but once the bar fills completely up my system hangs on:  Running local boot scripts (/etc/rc.local)

It says [OK] like it passed the test, but it goes no further, I'm left with a blinking cursor though I can type since I've never used any form of Linux before I have ZERO clue what to do to alleviate my issue.

I read on another thread something about pressing: CTRL + ALT + F1 which I did and it will prompt for a log on, but after that I'm stuck.  Hmm, I'm using my desktop to type this with my lappy in front of me...I'm thinking it doesn't know what resolution to set my screen at, because it tried two different resoultions, and both failed then it resorts to 1024x768 when it should be 1280x800.

After that, I can log in but then I'm left with a command prompt:

patrick@patrick-laptop:~$

And this is the point where I haven't got a clue what I should do.

I guess I should mentioned that I changed my display adapter in the preferences to what I thought it was, apparently I was wrong, so how would I go about reversing this so I can use Ubuntu again.

Thanks in advance :)

---

### Post by timbounceback on 2008-02-09
try running ```
startx
``` at the command prompt

---

### Post by patrick0605 on 2008-02-09
> **timbounceback said:**
> try running ```
startx
``` at the command prompt

Just tried that, and I get a page full of crap that means nothing to me, but it ends with

XIO:  Fatal IO error 104 (connection reset by peer) on X server ":0.0"
         after - request (0 known precessed) with 0 events remaining.

which brings me back to the command line.

---

### Post by timbounceback on 2008-02-09
ok, it could be something with your xorg.conf... maybe something with your resolution like you mentioned earlier.

---

### Post by patrick0605 on 2008-02-09
> **timbounceback said:**
> ok, it could be something with your xorg.conf... maybe something with your resolution like you mentioned earlier.

ok, and how would I go about fixing that?

I grew up in a Windows world, Linux to me is like trying to learn Russian at this point.

---

### Post by amingv on 2008-02-09
If it's a xorg configuration mistep, that's easy to discard. Maybe try:

```
sudo dpkg-reconfigure xserver-xorg
```

Fill in the information about your card and report back if it still doesn't work.

---

### Post by benerivo on 2008-02-09
You could try sudo```
sudo dpkg-reconfigure xserver-xorg
```This should lead you through several questions, for which you should try and answer with the default or simplest option (unless you know otherwise), when given a choice. Use the arrow keys to move, the space bar to toggle and return to select. If it doesn't work, try agian at least once, with other settings.

---

### Post by timbounceback on 2008-02-09
try reconfiguring it via
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by denham2010 on 2008-02-09
Hi Patrick,

I know, first time installing Linux can be very frustrating and off putting. I think I had about 3 or 4 false starts until I finally ridded myself of that windows beast. But then, I like to tinker as well, so after going through about 10-11 different distros, I have found Ubuntu to be the most tolerant to my tinkering.

What I would suggest, is just let Ubuntu install with all the defaults. Don't change the video card settings. It appears from what you have described that the whole boot process is working, and it is just crashing when trying to boot the X Server. The X Server controls the graphic management of your system. If you have selected the wrong video card, it will have problems and just not start.

Install with just the defaults, and once you are into a working desktop, you will be able to change all the video card settings if necessary (Ubuntu is very good at getting this right in the first place).

That's the beauty of Linux. Everything can be changed to your liking. You don't need to have it exactly right from the beginning. Just get to a working state and then change as much or as little as you need.

Best of luck, and don't give up.....I remember the tantrums I had at the start and the bin ended up full of Linux distro disks. But each time taught me something new, and now I am at a point that no matter what my tinkering may do to crash my system, I am always able to recover somehow....something I would have never learned using windows.

Ok, back to tinkering for me now...let's see what I can break next!

---

### Post by timbounceback on 2008-02-09
> **denham2010 said:**
> Hi Patrick,

I know, first time installing Linux can be very frustrating and off putting. I think I had about 3 or 4 false starts until I finally ridded myself of that windows beast. But then, I like to tinker as well, so after going through about 10-11 different distros, I have found Ubuntu to be the most tolerant to my tinkering.

What I would suggest, is just let Ubuntu install with all the defaults. Don't change the video card settings. It appears from what you have described that the whole boot process is working, and it is just crashing when trying to boot the X Server. The X Server controls the graphic management of your system. If you have selected the wrong video card, it will have problems and just not start.

Install with just the defaults, and once you are into a working desktop, you will be able to change all the video card settings if necessary (Ubuntu is very good at getting this right in the first place).

That's the beauty of Linux. Everything can be changed to your liking. You don't need to have it exactly right from the beginning. Just get to a working state and then change as much or as little as you need.

Best of luck, and don't give up.....I remember the tantrums I had at the start and the bin ended up full of Linux distro disks. But each time taught me something new, and now I am at a point that no matter what my tinkering may do to crash my system, I am always able to recover somehow....something I would have never learned using windows.

Ok, back to tinkering for me now...let's see what I can break next!

couldn't have said it better myself!

---

### Post by patrick0605 on 2008-02-09
Hey thanks guys!!

After going through the reconfiguration, I got it working again, well for now anyway :)

I'm gonna play around a bit more and see what else happens.

Thanks again.

---

### Post by patrick0605 on 2008-02-09
Ok, now that I can finally boot back into Ubuntu, my log on screen doesn't show up it's just a command prompt, and I have to type in startx to log in, and I don't want that.

How do I swap it back to the way it used to be?

---

### Post by benerivo on 2008-02-09
Try```
sudo /etc/init.d/gdm start
```

---

### Post by patrick0605 on 2008-02-10
Yep got it to work.

Aftering figuring out where the hell to type in these commands (the terminal) I'm lovin this OS very much...really I'm that dumb with linux I was confused as hell for a while.

---

### Post by barbedsaber on 2008-02-10
> **patrick0605 said:**
> Yep got it to work.

Aftering figuring out where the hell to type in these commands (the terminal) I'm lovin this OS very much...really I'm that dumb with linux I was confused as hell for a while.


Welcome to ubuntu (nice, in'it?) If you have any more questions feel free to ask, may I recomend that you add google linux (in my sig) to your bookmarks, and once again, welcome to ubuntu.

<shakes hand>

---

### Post by tyggna1 on 2008-02-10
yeah, the terminal really threw me through a loop the first time I used it.  I was kinda scared I'd screw something up.  Once I realized that the terminal *is* linux (or the vast majority of it), I started learning things.  If you want to learn the terminal better, here's a few tips:
1:  man
typing man before any command will give you the manual page.  This can help you avoid [unpleasant situations ]("http://xkcd.com/293/")
2: /bin, and /usr/(s)bin
this is where Linux keeps a list of all the commands/programs available from the command line.  These will be very long.
3:  log files
helps you see what's going on and find where problems are, they're in the /var/log directory.
4:  /etc
stands for etc.  kinda dumb.  Anyway, this is where linux puts almost all of your configuration files (which you may have to edit sometimes)
5:  Navigation commands
you probably already know these, but I like covering all my bases.  ls lists a directory, cd /dir changes to an absolute directory, cd dirname/ changes to a directory from where you are, and cd .. goes up a directory.

hope that helps.

---

