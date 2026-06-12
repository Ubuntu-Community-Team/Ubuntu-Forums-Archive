---
title: "Problem running iPodder in Kubuntu"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by SuperCool4678 on 2007-01-04
Hi, I'm a fairly new Ubuntu user (Kubuntu is the version I installed) who's making a transition from Windows.  The transition has been pretty smooth so far, but I still have to use Windows to get my podcasts.  I installed iPodder with the Adept Package Manager (Juice is the podcatcher I use in Windows), and it shows up in my "multimedia" menu, but when I try to start it, it disappears after the iPodder splash screen comes up.  What's causing this?  I tried installing PodNova, and it does the same thing.  I also tried installing Podracer with Adept, but I can't find it in any of my menus.  Can anyone help?  ](*,)

---

### Post by aidanr on 2007-01-04
run it in a terminal and see what error it prints out, podnova and ipodder use wxWidgets afaik, so make sure thats installed

---

### Post by SuperCool4678 on 2007-01-04
How do you install wxWidgets afaik?  I typed "wxWidgets afaik" into Adept's search box, and nothing came up.  Are any of the other wxWidgets packages in Adept the thing I need?  I tried installing a couple, but they didn't fix my problem.

To give you some idea of how generally clueless I am, I don't even know how to run iPodder or PodNova in a console!

---

### Post by aidanr on 2007-01-04
afaik stands for "as far as i know"

to run a program in a terminal, hit alt + F2 and type "konsole" without the quotes, hit enter and a new window will come up, type in "Podnova" and press enter (again without the quotes, and also check the spelling of that, i'm not 100% sure what it is, it's case sensitive aswell, it may be podnova or PodNova)

and then copy and paste the output here

---

### Post by SuperCool4678 on 2007-01-04
This is what it gave me when I tried to run Podnova in a console:

/usr/local/bin/PodNova-2.2/gui/tree.py:6: DeprecationWarning: The wxPython compatibility package is no longer automatically generated or activly maintained.  Please switch to the wx package as soon as possible.
  from wxPython.wx import *
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Traceback (most recent call last):
  File "iPodderGui.py", line 3522, in ?
    main()
  File "iPodderGui.py", line 3512, in main
    myApp = iPodderGui(ipodder,options)
  File "iPodderGui.py", line 738, in __init__
    wx.App.__init__(self, False, None)
  File "/usr/lib/python2.4/site-packages/wx-2.8-gtk2-unicode/wx/_core.py", line                                                                                                  7748, in __init__
    self._BootstrapApp()
  File "/usr/lib/python2.4/site-packages/wx-2.8-gtk2-unicode/wx/_core.py", line                                                                                                  7345, in _BootstrapApp
    return _core_.PyApp__BootstrapApp(*args, **kwargs)
  File "iPodderGui.py", line 1504, in OnInit
    self.InitHooks()
  File "iPodderGui.py", line 1852, in InitHooks
    for att, method in inspect.getmembers(self, inspect.ismethod):
  File "/usr/lib/python2.4/inspect.py", line 171, in getmembers
    value = getattr(object, key)
  File "/usr/lib/python2.4/site-packages/wx-2.8-gtk2-unicode/wx/_core.py", line                                                                                                  9302, in GetAcceleratorTable
    return _core_.Window_GetAcceleratorTable(*args, **kwargs)
TypeError: in method 'Window_GetAcceleratorTable', expected argument 1 of type '                                                                                                 wxWindow *'

---

### Post by Falcorian on 2007-01-05
Ok, so I'm going to dodge your question and suggest something you didn't ask for, and I hate it when people do that to my questions... But I'm going to do it anyway, maybe you'll find it useful. ;)


Amarok will both sync with your ipod (and other mp3 players) and will download podcasts from an RSS feed. And to boot, it's a great media player. Might want to give it a shot.


And sorry again for not helping with the question you asked. ;)

---

### Post by aidanr on 2007-01-05
yeah i've no clue either:-k 
as Falcorian said, amarok would be worth trying out

---

### Post by SuperCool4678 on 2007-01-05
I've played around with Amarok a little bit, but I haven't figured out how to do very much with it other than listen to music on my hard drive.  I'm looking for a podcasting client that lets you import feeds from an opml file.  I have a fairly long list of podcast subscriptions, and if I can avoid manually subscribing to all of them again, that would be nice.

I have Rockbox installed on my iPod, which means that I can just put audio files on it like a little external hard drive instead of having to mess with iTunes to put music/podcasts/audiobooks on it.  When I get podcasts in Windows, I have Juice set up to put them directly on the iPod's hard disk.  I enqueue them in Winamp, and then save the playlist on the iPod.  This procedure gives me a playlist of the podcasts I listen to every day with a minimum of effort.  I'm trying to figure out how to do something similar in Linux, but so far, I've just had to give up and reboot in Windows to get my podcasts.  

Juice is the Windows podcast client that works best for me, so I would like to find a Linux program that's as close as possible.

---

### Post by SuperCool4678 on 2007-01-05
I came across this forum posting in which a Debian user describes having a similar problem with Podnova.  Unfortunately, nobody offered any solutions:

[http://sourceforge.net/forum/forum.php?thread_id=1546213&forum_id=467631](http://sourceforge.net/forum/forum.php?thread_id=1546213&forum_id=467631)

---

### Post by meng on 2007-01-05
What version of Kubuntu are you using?

---

### Post by SuperCool4678 on 2007-01-05
> **meng said:**
> What version of Kubuntu are you using?

6.10

---

### Post by SuperCool4678 on 2007-01-09
Could running the Windows version of Juice in WINE possibly work?  I haven't tried that yet.

---

### Post by vgrisham on 2007-01-18
> **SuperCool4678 said:**
> Hi, I'm a fairly new Ubuntu user (Kubuntu is the version I installed) who's making a transition from Windows.  The transition has been pretty smooth so far, but I still have to use Windows to get my podcasts.  I installed iPodder with the Adept Package Manager (Juice is the podcatcher I use in Windows), and it shows up in my "multimedia" menu, but when I try to start it, it disappears after the iPodder splash screen comes up.  What's causing this?  I tried installing PodNova, and it does the same thing.  I also tried installing Podracer with Adept, but I can't find it in any of my menus.  Can anyone help?  ](*,)

SOLVED!!! I just fixed this!!! Pardon my excitement, but I think I just graduated from complete noob to freshman geek. 

The way I happened upon this problem is that I convinced my wife (finally) to let me convert her laptop to Ubuntu. I installed dapper on it this week, and from the get go, PodNova would crash on startup. Meanwhile, I have dapper on my desktop, and have continued to run PodNova without fail. 

I noticed the mention of wxwidgets in this thread, so I searched both the laptop's and my desktop's synaptic packages. What I found was that all of the desktop's wxgtk files were version 2.6 and all of the laptop's were 2.8. After some trial and error, I found that PODNOVA WORKS if you: 

1. search wxwidgets in Synaptic (or Adept in your case) and uninstall everything that comes up.
2. Reinstall Python-wxgtk2.6 (this will install all dependencies).

Done. Launch PodNova. 8)

---

### Post by SuperCool4678 on 2007-01-20
I tried what you suggested, and that seems to have fixed it on my computer!

Many thanks!  ):P   This problem I was having with getting my podcasts was one of the few remaining obstacles to me switching over pretty much completely to Linux.

---

### Post by vgrisham on 2007-01-20
> **SuperCool4678 said:**
> I tried what you suggested, and that seems to have fixed it on my computer!

Many thanks!  ):P   This problem I was having with getting my podcasts was one of the few remaining obstacles to me switching over pretty much completely to Linux.

You're welcome. It's a good feeling to be free of Windows. Have fun.

---

### Post by drdf on 2007-02-08
I ran into this same problem on Gnome.  An alternative to the suggestion of uninstalling wx2.8 is to just install wx2.6 along side it and then tell iPodder to use verion 2.6 instead of 2.8.  This way you don't risk breaking another application that might needs a feature of wx2.8 that wx2.6 doesn't have.  I tried this at it works fine.   As I recall, these are the steps that I used on Ubuntu Dapper:

1.Use Synaptic Package Manager to install python-wxgtk2.6.  (I'm not sure if it will require other packages.  For me it didn't but I already had a few 2.6 things installed.)
2.Then edit the file iPodderGui.py, and right above the line “import wx” at the top of the file put the lines:
import wxversion
wxversion.select('2.6')
3.Here's the detail on how I do the above:

[INDENT][/INDENT]a.Open a terminal.

[INDENT][/INDENT]b.Find where iPodderGui.py is (“locate iPodderGui.py” should do it, and if it doesn't run “sudo updatedb” first).

[INDENT][/INDENT]c.Navigate to this directory in the terminal, and type “sudo gedit iPodderGui.py”.

[INDENT][/INDENT]d.Insert the lines from step 2.
4.Save the file and try to run PodNova.

I'm quite new to Ubuntu and Linux, as I've been using Windows exclusively until a few days ago.  But I have done some Python and wxWidgets programming.  It seems to me that modifying the code of the program isn't the best approach, but it's a pretty small modification.

---

### Post by orengolan on 2007-03-30
> **vgrisham said:**
> 
1. search wxwidgets in Synaptic (or Adept in your case) and uninstall everything that comes up.
2. Reinstall Python-wxgtk2.6 (this will install all dependencies).

Done. Launch PodNova. 8)

worked for me too, thanks!

btw, i am using Ipod so I also need an application that transfers the files from my computer into my Ipod.

on my windows I Used Vpod, small and fast app that did just that.
does anyone know if it exist in Linux or any other way of moving files into Ipod?

thanks

I just saw that even though it works i get this in the Terminal:

oren@oren-desktop:~$ /usr/local/bin/PodNova
Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed

(python:11538): Gtk-CRITICAL **: gtk_container_remove: assertion `GTK_IS_TOOLBAR (container) || widget->parent == GTK_WIDGET (container)' failed

---

### Post by xe1ufo on 2007-03-31
For the Ipod (I have a fifth generation 30-Gigger, which I love!!) I found the easiest program to be gtkpod.  Now: many people have trouble because they fail to FIRST import the Ipod's database to gtkpod.  Once you plug in your Ipod and it appears as an icon on your desktop, just start gtkpod.  On the left menu go down to Import Database from Ipod. Once you do that, you can add files and even folders full of audio files to gtkpod to your heart's content. When you are done, (wait for the importation to finish!), then export the database back to your Ipod and you are done.  

And, no, it does NOT insist on formatting your Ipod like the Mickey Mouse Itunes on a different Windows machine! You can connect your Ipod to as many Linux machines as you wish, and lose no files. I connect the same Ipod to my WindowsXP laptop and desktop Ubuntu 6.10 box with no problems.

Hope this helps!

Dr. Steve, central old Mexico

---

### Post by ivago on 2007-04-02
hi all,

today I subscribed to the brand new podnova site, wich also released new client software (2.3).

This relies on the following 
```
System Requirements
PodNova requires Python 2.4 and the Python library wxPython 2.6.
Also the mxDateTime library is required.
```

I have all the above installed but when I start  the  program I get the following error:

```
gb@TACO:~$ /usr/local/bin/PodNova
RuntimeError: Bad magic number in .pyc file

```

As far as I can tell Feisty uses standard python 2.5, so now I have both installed but I suspect the above error occurs because ubuntu uses python 2.5

So how  can I launch Podnova using python 2.4  instead of 2.5?

Thx in advance!!

ivago

---

### Post by orengolan on 2007-04-21
I get this error when running Podnova 2.3 :

```

oren@oren-desktop:~/Desktop/PodNova-2.3-linux-py25$ sudo sh ./PodNova.sh
Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed
oren@oren-desktop:~/Desktop/PodNova-2.3-linux-py25$ cd
oren@oren-desktop:~$ PodNova
/usr/local/bin/PodNova-2.2/gui/tree.py:6: DeprecationWarning: The wxPython compatibility package is no longer automatically generated or actively maintained.  Please switch to the wx package as soon as possible.
  from wxPython.wx import *
Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed
Traceback (most recent call last):
  File "iPodderGui.py", line 3522, in <module>
    main()
  File "iPodderGui.py", line 3512, in main
    myApp = iPodderGui(ipodder,options)
  File "iPodderGui.py", line 738, in __init__
    wx.App.__init__(self, False, None)
  File "/usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode/wx/_core.py", line 7757, in __init__
    self._BootstrapApp()
  File "/usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode/wx/_core.py", line 7354, in _BootstrapApp
    return _core_.PyApp__BootstrapApp(*args, **kwargs)
  File "iPodderGui.py", line 1504, in OnInit
    self.InitHooks()
  File "iPodderGui.py", line 1852, in InitHooks
    for att, method in inspect.getmembers(self, inspect.ismethod): 
  File "/usr/lib/python2.5/inspect.py", line 206, in getmembers
    value = getattr(object, key)
  File "/usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode/wx/_core.py", line 9319, in GetAcceleratorTable
    return _core_.Window_GetAcceleratorTable(*args, **kwargs)
TypeError: in method 'Window_GetAcceleratorTable', expected argument 1 of type 'wxWindow *'


```

---

