---
title: "IBM ThinkCentre Volume only 'loud' - lspci result"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by Andavane on 2008-03-30
All sound on IBM Thinkcentre is set on loud.
Master volume slider is on 51% - using the slider makes no difference.
Have read round various threads on subject.
Here is result of typing lspci into terminal:

> 
andavane@andavane-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
03:02.0 Communication controller: Conexant Unknown device 2702 (rev 01)
03:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)
andavane@andavane-desktop:~$

Hope this gives a clue.
Have burrowed into all the sound and volume adjusters I can find in the menus -- to no effect.

Regards

John

---

### Post by c-ron on 2008-03-30
Try using alsamixer to adjust playback levels and see if maybe one of the switches is/isn't activated. 

From the terminal:
```
alsamixer
```

Use the left and right arrow keys to select the control you want to change.
(Note that if your soundcard has lots of controls, alsamixer doesn't show them all on one screen, just arrow over to see more)
Up and down arrow keys to change levels.
'M' key toggle switches on or off.

Is something like 'external amplifier' enabled?

---

### Post by Andavane on 2008-03-30
> **c-ron said:**
> Try using alsamixer to adjust playback levels and see if maybe one of the switches is/isn't activated. 

From the terminal:
```
alsamixer
```

Use the left and right arrow keys to select the control you want to change.
(Note that if your soundcard has lots of controls, alsamixer doesn't show them all on one screen, just arrow over to see more)
Up and down arrow keys to change levels.
'M' key toggle switches on or off.

Is something like 'external amplifier' enabled?

c-ron:
almost daily I'm amazed at the amount of things this system can do.
Yes I can see the alsamixer in the terminal.
When I hear of something new, I type it into the synaptic package manager that there's an "alsamixergui" which I presume is just the basic thing with more pictures (not installed), but also not installed is: "gnome-alsamixer". I think I'll install that as it looks useful. 
Before I do anything, I do need to synchronize this sort of test with other things going on in the house, you know meals and such. Also I get up earlier sometimes and don't want to blast people sleeping ;)

By the way, before I fiddle about one thing:
In the morning we do some chants using mp3 files via the "Rhythmbox" programme, and the volume slider works perfectly in that, i.e. I can quieten or enlouden the sounds according to wish.

looking forward to trying out alsamixer!

Regards

John

---

### Post by Andavane on 2008-03-30
> **c-ron said:**
> Try using alsamixer to adjust playback levels and see if maybe one of the switches is/isn't activated. 

From the terminal:
```
alsamixer
```
...
Up and down arrow keys to change levels.
'M' key toggle switches on or off.

Is something like 'external amplifier' enabled?
OK i can see all the levels, and move left and right with the left--right arrow keys and alter volumes with up and down. Am not sure whether some bars are enabled or disabled. There is only one small bart labelled "external" and the figures are set to "00" in green, and the up--down arrows have no effect.
Does that tell you something?
Regards
John

---

### Post by c-ron on 2008-03-30
Arrow over to 'External' and press the M key on your keyboard to toggle it off.

---

### Post by Andavane on 2008-03-30
Yes I have the hang of the toggling now.
I felt a bit daft when my carer pointed out to me that youtube has its own volume control.
duh!
That helped a lot.
We live and learn...
Regards
John

---

### Post by Andavane on 2008-03-31
> **Andavane said:**
> Yes I have the hang of the toggling now.
I felt a bit daft when my carer pointed out to me that youtube has its own volume control.
duh!
That helped a lot.
We live and learn...
Regards
John
However since the last post, I've had a chance to open alsamixer and go through all the bars, toggling on and off and adjusting volumes up and down. Nothing seems to make any difference.
Although I can adjust volume in the youtube slider and in the Rhythmbox volume control, the master controls  have no effect.
Regards
John

---

