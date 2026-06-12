---
title: "Saving personal desktop configuration?"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by irishgoth8822 on 2008-02-20
My system hangs all the time, usually requiring me to reinstall the entire OS. Because I have to do this so often, I have begun saving all of my files once a week to my flash drive to ensure that I can easily get back all my information. However, it's still a pain to have to always reset my desktop and all of the keyboard shortcuts etc everytime I reinstall.

Is there any way to save the current desktop configuration (including icons used, shortcuts, menus etc) as a theme file or something like that that would allow me to just reload it from my flash drive when I have reinstalled? I know that I would still have to reinstall all the packages and programs that I use regularly, but I wonder if at least I could save myself the trouble of having to reconfigure all of my basic settings.

---

### Post by Zill on 2008-02-20
> **irishgoth8822 said:**
> My system hangs all the time, usually requiring me to reinstall the entire OS...
Not quite the answer you wanted but it seems to me that you may be better off fixing your system first :-)
Your info shows you are using Dapper which is a rock-solid version of Ubuntu - this should never (?) hang.  Sounds to me like you either have dodgy hardware or some serious configuration error(s).
It may be worth recording exactly what you were doing when the system crashed and then posting the info - someone may then be able to help with diagnosing the real fault(s).

---

### Post by irishgoth8822 on 2008-02-20
well, the first sign i usually get is that all of a sudden my internet will cut out. ive also noticed that it seems to happen most when im online, but that could just be because i'm online alot.

next, programs start loading very very slowly or not at all--i.e, i'll click on, say, openoffice, or firefox, and 'starting *insert program here*' will pop up on my sidebar, but then it will disappear and the program window still hasnt opened. sometimes it will open after a few minutes, sometimes not at all. everything will do that, even if i click the power symbol to choose to shut down or restart.

sometimes after this has happened, it will fix itself after a couple restarts. other times, it will start being slow even as early as when its booting the system log, when it will switch to the black terminal-looking screen and take considerably longer to complete booting. then, when i've logged in my username and password, when it pops up that orange bar that says 'starting window manager...starting nautilus, etc', that too will take a good couple of minutes between each load, if it completes at all. its when it gets like that that i reinstall.

---

### Post by cdtech on 2008-02-20
Wow! where to start?
When it starts to bog down like that the first place I would start is:
```
free
```
to see how much memory is used and how much is used by buffers and cache.

As you can see when I run the command free the memory I have left is just over 900M but 1.3G is in buffers and immediately available to any program that wants it.
```
             total       used       free     shared    buffers     cached
Mem:       1933708    1016692     917016          0      22584     418692
-/+ buffers/cache:     575416    1358292
Swap:      5373700          0    5373700

```
If you see your swap space being used, this is not bad. Other programs that haven't been used for awhile have probably been switched to use the swap by the system so that other programs could use the memory.

Using the vmstat with an interval (maybe 15 sec) and watching the "so" column, if that goes above "0" often, then your system is using swap pretty regularly; which is an indication that you are lacking memory (RAM).

For those that opt to run no swap, I think that is a bad choice. If a program can't get enough memory you know the outcome (crash).

---

### Post by Zill on 2008-02-20
I don't know if this will help in this case but it is often worth disabling ipv6.  See [this thread]("http://ubuntuforums.org/showthread.php?t=87798") for further details.

---

