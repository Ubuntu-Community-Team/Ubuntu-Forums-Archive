---
title: "Game Disappears"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by bmachia on 2008-01-19
Hello Folks, 
Please bear with me this is my first post on a Linux forum, I'm an absolute beginner.  I'll probably make a fool of myself before I'm done.

I've wanted to get into Linux for years but did not want to dual boot off my primary machine, just in case something happen and I loose everything.  Anyway, I just purchased a Thinkpad and have installed KUBUNTU.  

So, far I have worked my way through remote printing and setting up my PCMCIA Wireless card with ndiswrapper.  At one point, I was feeling rather comfortable with Linux!

Until, I decided to try a game.  AisleRiot Solitaire to be exact.   With the drag and drop of the first card, the program shuts down and disappears from the desktop.  I can go into K Menu, Games, Card Games and start it back up again only to have it shutdown with the first drag and drop.

I tried to removed and reinstall the game using add\remove programs, I even did an sudo apt-get autoclean and sudo apt-get autoremove before re-installing/adding the Solitaire game back in.  

All this only to experience the same problem.  Can anyone offer this newbie a suggestion?

Hoping to hear back
Bill

---

### Post by GavinZac on 2008-01-19
if you can run it from the terminal, it will give you an error message to help you figure out what is wrong.

I think in Kubuntu this is called Konsole. Then you can run it by typing its name (often the same as the apt-get package name) and see what comes out.

---

### Post by RomeReactor on 2008-01-19
Hi. Please open Konsole and run:
```
sol
```
if the program crashes, post any messages left there.

---

### Post by bmachia on 2008-01-19
Hi Folks,
Thanks for the quick reply.  I opened Konsole and typed 'sol', the program crashed and gave me the following;

bill@bill-laptop:~$ sol

(sol:19541): GStreamer-CRITICAL **: gst_element_get_bus: assertion `GST_IS_ELEMENT (element)' failed

(sol:19541): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed

(sol:19541): GStreamer-CRITICAL **: gst_element_set_state: assertion `GST_IS_ELEMENT (element)' failed

(sol:19541): GStreamer-CRITICAL **: gst_bus_timed_pop: assertion `GST_IS_BUS (bus)' failed
Segmentation fault (core dumped)

bill@bill-laptop:~$


Any ideas?  Did I install something worng or incorrectly?

Bill

---

### Post by RomeReactor on 2008-01-19
Try installing the following packages (NOTE: You need the 'Universe' and 'Multiverse' repositories enabled):
```
sudo aptitude install gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
```
Then run the game again.

---

### Post by bmachia on 2008-01-19
Well, I thought we had done something...  

In order to enable Universal / MulitUniversal, I needed to Kate Sources.list and remove 2 comments (#).  Just to be safe I rebooted and then ran your command string;

sudo aptitude install gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverseb

The machine installed code for (I bet) 40 seconds,  IT was really trucking, and I did not see any errors during the installs.

After everything settled, I typed; (and received the following)
bill@bill-laptop:~$ sol

(sol:6432): GStreamer-CRITICAL **: gst_element_get_bus: assertion `GST_IS_ELEMENT (element)' failed

(sol:6432): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed

(sol:6432): GStreamer-CRITICAL **: gst_element_set_state: assertion `GST_IS_ELEMENT (element)' failed

(sol:6432): GStreamer-CRITICAL **: gst_bus_timed_pop: assertion `GST_IS_BUS (bus)' failed
Segmentation fault (core dumped)
bill@bill-laptop:~$     
Looks like the same Crash error.  Any other ideas?  I'm game (no pun intended)
Bill

---

### Post by RomeReactor on 2008-01-19
Does 'Four In A Row' also crash?:
```
gnect
```
There are [many bugs]("https://bugs.launchpad.net/ubuntu/+source/gnome-games") for Gnome-Games; the one in Four In A Row is the [same one as yours]("https://bugs.launchpad.net/ubuntu/+source/gnome-games/+bug/179519").

---

### Post by bmachia on 2008-01-20
You guessed it,  Four in a row has the same error
bill@bill-laptop:~$ gnect

(gnect:17597): GStreamer-CRITICAL **: gst_element_get_bus: assertion `GST_IS_ELEMENT (element)' failed

(gnect:17597): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed

(gnect:17597): GStreamer-CRITICAL **: gst_element_set_state: assertion `GST_IS_ELEMENT (element)' failed

(gnect:17597): GStreamer-CRITICAL **: gst_bus_timed_pop: assertion `GST_IS_BUS (bus)' failed
Segmentation fault (core dumped)
bill@bill-laptop:~$

I guess this means there is nothing that can be done until a Crash fix is created.  Thanks, at least I realize there is nothing that I did.

I'll remove this series of games and look for something else.  Can you suggest a good download site?

Thanks again.
Bill

---

### Post by RomeReactor on 2008-01-20
You can try KDEgames:
```
sudo aptitude install kdegames
```

We have a section dedicated to games as well: [Gaming & Leisure]("http://ubuntuforums.org/forumdisplay.php?f=93"). You can find many lists of games, such as [this one]("http://ubuntuforums.org/showthread.php?t=427205"). This [documentation page]("https://help.ubuntu.com/community/Games") has a few games as well. A for linux gaming sites, there's [Ubuntu Gamers Arena]("http://gaming.gwos.org/doku.php"), [Linux Games]("http://www.linuxgames.com/"), [The Linux Game Tome]("http://happypenguin.org/"), and [Linux Gamers]("http://www.linux-gamers.net/"), among others.

---

