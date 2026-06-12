---
title: "Gnome title bar dsiapperead"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by Garavan on 2008-03-13
OS Gutsy. Display - Asus MW221U 1680 x 1050 resolution by 50 Hz VESA. The display type is WSXGA+. My MoBo came with a built-in graphic card, a nVIDIA®GeForce 6100/nForce 430. nVidia driver installed means that under Graphic Cards I selected nVIDIA with Geforce 6 series.

Result that the title bar (place, system, clock and others) is not displayed or not visible on the screen. As a newbie I've no idea how to fix it. Please baby-talk to me, so I could understand what to do to fix it.

I just started to read the Ubuntu Linux Bible book, which refers to "Assistive Technologies for using Gnome" but I can't find it under System ==> Preferences. Is that still supported?

---

### Post by Redenbacher on 2008-03-13
Well, I don't do baby-talk, I have a feeling that would get a bit annoying, but I'll keep it simple as I am in no way an advanced user...

The first thing I think you should try is open up a terminal. Now, since you have no panel you can't just click it off the bar, so we have to resort to other methods.

My first question to is, is there any panel visible? Your top bar is gone, but is your bottom panel still visible?

If yes, right click the panel, click Add new Panel, and one should appear on top. You then right click that panel and click Add to Panel and then double click the Menu Bar. This will restore your Applications/Places/System menu. You can then continue to add other things such as clock, notification menu (system panel), etc.

If no, can you right click the desktop and then click Open Terminal?

If yes, once terminal is opened, type "gnome-panel"

If no, Ctrl + Shift + T should be the default short cut to open a terminal, then enter "gnome-panel"

Hopefully this will restore your panels, follow the directions above to customize your panel to get the Menu bar back. If this works for you, you then want to go to System -> Preferences -> Sessions. Add a new program, and in "Command" enter "gnome-panel" and save. What you just did here is ensure that your panels start up when you login, so you don't have to run it from terminal every time.

If this doesn't work, ensure that gnome-panel is installed. Follow the instructions above to open up a terminal and type: 

```
sudo apt-get install gnome-panel
```

Then run it from the terminal you just opened with "gnome-panel", and follow the instructions above to add it to sessions.

If it is installed and none of the above steps helped, then it might be something else that I'm not familiar with, and someone else may have to help :/ but hopefully it doesn't come to that ( I like feeling as if I know what I'm doing every once in awhile :P)

I hope those instructions are easy to follow, if you need anything explained just say the word :)

---

### Post by Garavan on 2008-03-13
Sorry, for the delay, I had to run some errands. The thing is so, I can see the bottom of the panel, where I've my tasks minimized, the trash can and 2 Desktops. With the function keys I'm also able to get into applications, places and system. (Alt + F1). Right clicking the bottom + add new panel now displays an empty title bar. Add to panel + Menu Bar worked too. Now I've Applications Places and System. The rest I can add later.

Therefore, I thank you so much for your support. I was just kidding with baby-talk. Your answer was perfect, up to the point.

Now, my next step is install a e-GeForce 8600 GTS video card and my second monitor. Do you have any suggestion on the system side? I know how to install the HW and solved it several times under XP/Vista, but here so many easy things go wrong while other stuff, where I would think it will be a big problem, just run from the beginning. I still do not know how the title bar could disappear. Thanks again.

---

### Post by forrestcupp on 2008-03-13
When you install your 8600, it may mess up and not boot to the desktop because your system is set for your onboard chip and you will be switching to a PCI-e slot.  If it doesn't work, you may need to do this.

Boot to the recovery console.  The way you do this is start your computer and when you get to the GRUB boot menu, choose the one that shows the kernel name and says something like 'recovery mode.'  It's usually the 2nd choice.  This will boot to the command line, where you will type:
```
dpkg-reconfigure -phigh xserver-xorg
```
This will automatically configure xorg for your new video card.  Then type:
```
exit
```
to reboot your computer, and it should boot to the desktop correctly.  Then you can go to System->Administration->Restricted Drivers Manager to enable the proprietary drivers for your new nvidia card.

If those drivers don't work for your 8600, redo those commands and try using [Envy](http://www.albertomilone.com/nvidia_scripts1.html) to install the latest drivers.

You only need to do all of that if it doesn't work.

And by the way, the title bar you were talking about is called a 'panel.'  The title bar is the bar at the top of your windows that tell you the name of the app you are running.

---

### Post by Garavan on 2008-03-13
On the recovery consol I entered the suggested command, then choose nvidia. There were a lot of options, like nv, vesa, vga, via, and others. I'm not sure if nvidia was the right one or not?
However, the gnome could be viewed via the onboard video card. Now, I'm rebooting and changing BIOS to supress the onboard VGA and use the PEG (PCI express installed Grapchic card, which is the 8600 GTS) and boot the system to see if that solves the card issue.
I'll be back shortly. If you wish, you can send me a reply, since I can see it on the other PC.
Thanks so far.

---

### Post by Garavan on 2008-03-13
Shall I continue here? My problem with the Panel - "Title Bar" is already solved. The current problem is to install the graphic card and properly configure the 2 displays. I think it may be advantageous to start a new thread?

However, the system booted from the other screen at this time, from the one , which is directly on the 8600 GTS card, but after a few kernel line it went blank, -no signal,

Before I go further, I need your  reply as to what I may did wrong, or shall try it differently.

As always, thanks

---

### Post by Garavan on 2008-03-13
Super, I was sitting back and thinking of what the hell happened again while the screen went black. and after a while it suddenly both screen came on and both are connected to the new 8600 card. The only problem now that both screen show the same. I guess from now on it is just a setting issue. Isn't it?
It is now working like a copy-cat.
In the Screen and Graphics Preferences I only see Screen1 for both and it wont let me change anything.

What do I do next?

---

### Post by Therion on 2008-03-13
Deleted.

---

### Post by forrestcupp on 2008-03-13
in a terminal, type
```
nvidia-settings
```
It will bring up a GUI for your settings.  You can set your display options there.

---

### Post by Garavan on 2008-03-13
What a nightmare!

from the terminal window I entered the command as You advised nvidia-settings

I got a message 

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run "nvidia-xconfig" as root(, and restart the X server.

How many abuse this system provides? This is not an operating system! Windows at least let me do the basics, namely to properly interact with my devices. I'm very disappointed. It may be free but useless.

Coordinate your efforts to bring up a solid basic system and if that is free then many folks will jump on that. What a pitfall, wasting 2 weeks of my time to get nowhere.

---

### Post by Redenbacher on 2008-04-08
Well of course you would get this, you've installed the hardware but not the software. You need to install the nvidia drivers just as you would in windows. And if they are installed, they need to be enabled. the "nvidia-xconfig" command enables the driver in your xorg.conf file as far as I know. This is standard procedure, not a useless operating system. Restarting the x server is as simple as ctrl+Alt+backspace, then log back in.

I'll admit that Ubuntu takes a little extra effort to get *some* things working properly, mainly video cards, at least in my experience. But once they are working, you won't have a problem anymore. In my experience, this is much unlike windows, which creates problems that you haven't even touched!

---

