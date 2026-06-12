---
title: "can't stop Thunderbird-running but not reponding"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by Haus Neuerburg on 2007-06-06
Hi there,
I'm as new with ubuntu/xubuntu/Linux as one can only be, so I have a real freshman's question: after I had installed one Thunderbird extension (options toolbar button) Thunderbird did not start anymore if it wasn't the first programme to be started. The problem is still occurring even after I had deinstalled that extension. The error message I get is: *Mozilla-Thunderbird is already running, but not responding. To open a new window you must first close the existing Mozilla-Thunderbird process, or restart your computer.*
Is there any equivalent in xubuntu to the windows ALT+CTRL+DEL shortcut to be able to remotely close a programme? I can't close down a window I can't see on any desktop.
Thanks in advance
Haus Neuerburg

---

### Post by charles.g.moore on 2007-06-06
> **Haus Neuerburg said:**
> Hi there,
I'm as new with ubuntu/xubuntu/Linux as one can only be, so I have a real freshman's question: after I had installed one Thunderbird extension (options toolbar button) Thunderbird did not start anymore if it wasn't the first programme to be started. The problem is still occurring even after I had deinstalled that extension. The error message I get is: *Mozilla-Thunderbird is already running, but not responding. To open a new window you must first close the existing Mozilla-Thunderbird process, or restart your computer.*
Is there any equivalent in xubuntu to the windows ALT+CTRL+DEL shortcut to be able to remotely close a programme? I can't close down a window I can't see on any desktop.
Thanks in advance
Haus Neuerburg

you can fire up a terminal type 

top

find the PID that corresponds to thunderbird then

sudo kill <*PID NUMBER*>

---

### Post by charles.g.moore on 2007-06-06
I have had that problem before with firefox and if that does not work you could always restart,

before you restart the system you could try doing a ctrl-alt-backspace to restart the x server that should kill the process too...

---

### Post by Haus Neuerburg on 2007-06-06
yup, but what is a PID? I'm a bit uneasy about terminal entries as I tend to use them w/o having an idea what they do and they've let me doing three more xubuntu installations before (my fault I know ;-)

---

### Post by Haus Neuerburg on 2007-06-06
is ctrl-alt-backspace the equivalent to the windows alt-ctrl-del? I know about restarting but really I'd like to open the programmes in the order I need/want them and not have to think about the right order when using the computer....

---

### Post by charles.g.moore on 2007-06-06
> **Haus Neuerburg said:**
> yup, but what is a PID? I'm a bit uneasy about terminal entries as I tend to use them w/o having an idea what they do and they've let me doing three more xubuntu installations before (my fault I know ;-)

A PID is the process ID it should be the first column when you type top

dont worry you wont hurt anything

all you are doing is finding the number associated with the process through top and then killing it manually...

try looking at top and you will see it looks like the processes tab when you ctrl alt del on a winblows box

---

### Post by charles.g.moore on 2007-06-06
> **Haus Neuerburg said:**
> is ctrl-alt-backspace the equivalent to the windows alt-ctrl-del? I know about restarting but really I'd like to open the programmes in the order I need/want them and not have to think about the right order when using the computer....

ctrl alt backspace is a way to manually kill your X server, or the GUI engine if you will...

I guess you could equate it to a "soft reset"

---

### Post by Haus Neuerburg on 2007-06-06
ok, so I tried ctrl-alt-backspace but the problem still exists: after the "soft reset" I started FF again, tried to start Thunderbird and got the same error message: gues I should try the PID entry?

---

### Post by teddybairs1 on 2007-06-06
Have you tried reinstalling thunderbird? Also, do you need thunderbird, would evolution or one of the other mail clients work? Have you tried using Thunderbird 2.0 from Mozilla's website?
Killing the program only solves the symptoms. Try doing a complete removal, and then reinstall it.
Try using 2.0 from Mozilla.com. You just unpack it to your home directory and run the executable within the folder. Works perfectly, you just have to set up all the shortcuts by hand.
Is there a system monitor in Xubuntu like there is with the Gnome desktop? It should be under System->Administration. You should be able to kill an open app there.

---

### Post by Haus Neuerburg on 2007-06-06
> **charles.g.moore said:**
> A PID is the process ID it should be the first column when you type top

dont worry you wont hurt anything

all you are doing is finding the number associated with the process through top and then killing it manually...

try looking at top and you will see it looks like the processes tab when you ctrl alt del on a winblows box

sorry, but I need more help because top doesn't show any process relating to Thunderbird ( as far as I can identify it) so what should I do now? Is there any other way?

---

### Post by Haus Neuerburg on 2007-06-06
@teddybears1: isn't there any other way of solving the problem? I'm not too keen on deleting Thunderbird neither on installing TB2 (nothing against it but manipulating all shortcuts manually is not at all attractive to a newie who still hasn't the slightest idea of where everything comes from and goes to); I've done it with FF as xubuntu came with FF1.5 and I had wanted FF2 as I had used and loved it before and I haven't figured out all shortcuts yet: if for example I'm starting a system help it always opens in FF1.5 if it has to open the browser and I have no idea how to eliminate this........:confused:

---

### Post by Haus Neuerburg on 2007-06-06
> **charles.g.moore said:**
> you can fire up a terminal type 

top

find the PID that corresponds to thunderbird then

sudo kill <*PID NUMBER*>

managed to find the PID eventually ;-) (in the xfce 4 Task Manager) and killed it with your entry....started TB again and it popped-up: THNX
just 1 more question: will I have to do it this way everytime I don't open it as the first programme?

---

### Post by teddybairs1 on 2007-06-06
Honesly, I don't know yet. In troubleshooting anything we have to go through a process of elimination. If you were to either install 2.0, or do a complete removal and reinstallation of TB from the repos and the problem still occurs then we know it's not the program itself.

---

### Post by teddybairs1 on 2007-06-06
Just had an idea. Is Thunderbird set to start upon bootup? Don't know if this is an option with Thunderbird but it's worth a look. If it is, set it to not start on bootup.

---

### Post by p_quarles on 2007-06-06
FYI, in Windows, uninstalling Thunderbird will not get rid of any e-mail or personal settings, including plugin data.  I'm assuming this is true of Linux as well, so reinstalling it might not get rid of the problem. For the same reason, though, it's worth a try, since it won't touch your archives. 

Someone should confirm that this is true for Linux, though, since I've never had to do a reinstallation.

---

### Post by dondad on 2007-06-06
go to admin/system monitor. There is a tab that lists processes. highlight the thunderbird entry and there is a button to end it. I have had the Firefox problem mentioned, usually when it crashes if I try to close a tab with video running. Thsi method closes the invisible session of it and then I can open normally.

---

### Post by Haus Neuerburg on 2007-06-06
@dondad: this is how I stopped the non-responding process in the end, or rather finding the PID vai the monitor and then using charles.g.mores kill-entry. Have to admit that I haven't tried again whether the problem persists or not: actually it only turned up after I had installed an extension and persisted even though I had deinstalled the extension. I'll wait until tomorrow to see whether it will occur again.

---

