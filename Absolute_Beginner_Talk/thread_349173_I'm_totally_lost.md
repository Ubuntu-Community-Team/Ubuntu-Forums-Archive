---
title: "I'm totally lost"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by blarney on 2007-01-29
I just installed server version 6.10 and I can log into it but at that point I am at a total lost.  I have downloaded files to a cd so that I can install a gui on it etc.  but not sure how to launch it.  I used to use linux/unix software back in the early 90's but haven't touched it since.  Now I don't know how to look at different drives, how to install software once I find it and pretty much feel like I have just turned on my very first computer for the very first time.  If anyone can give me some direction on at leasst getting a GUI installed it would be greatly appreciated.

---

### Post by taurus on 2007-01-29
Do you have a network connection on your server?  If you do, you can install a window manager from a console with

```
sudo aptitude update
sudo aptitude install ubuntu-desktop <-- if you want to use Gnome
sudo aptitude install kubuntu-desktop <-- if you want to use KDE
sudo aptitude install xubuntu-desktop <-- if you want to use XFce4
```

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by irish_flu on 2007-01-29
EDIT:  (deleted all the things that taurus posted just as I was typing that :)

You can also add your CD as a repository for apt-get and install things that way, but I'll let somebody more knowledgeable than me explain it.  :D

---

### Post by blarney on 2007-01-29
okay I know I am about to sound like a dumbass but what do you mean by a console?  Do I just type in whichever one I want to use by just typing in the command line like you showed?  I don't even know how to get my ip address and not even sure I need one.  

Can ya tell I am at a total loss here?  :)   I appreciate the help.

which is the best desktop to get, by the way?  :)

---

### Post by irish_flu on 2007-01-29
Yeah, by "console", folks mean "command-line interface".

---

### Post by taurus on 2007-01-29
Is your machine connected to the net at all?  What's the output of this command from a prompt?

```
/sbin/ifconfig
```

---

### Post by irish_flu on 2007-01-29
As for which desktop, it's all a matter or opinion but I can try to give you some basic ideas:

gnome: practical, simple to use, well-organized, mature (but can be made pretty)

KDE: flashier than gnome, preferred by many, also mature

Xfce: lightweight, might be best for older low-end machines, or just for folks who like to keep stuff small and lightweight    :)

---

### Post by IYY on 2007-01-29
The commands mentioned above would work provided that your system is already connected to the Internet, or that there is a CD with the components on it (such as the Ubuntu Desktop CD).

To check your current IP address, use the command

```
ifconfig
```

Of course, you could just try pinging some website

```
ping -c 5 http://www.google.com
```

If your machine is not connected, you could try a command like

```
sudo dhclient
```

to try and obtain an IP address via DHCP.

If you can't manage to configure it with the command line, you might want to install the Desktop edition. It comes with a LiveCD which allows you to see the OS running prior to installation, a GUI, and all the power that the server edition provides.

---

### Post by taurus on 2007-01-29
> **irish_flu said:**
> As for which desktop, it's all a matter or opinion but I can try to give you some basic ideas:

gnome: practical, simple to use, well-organized, mature (but can be made pretty)

KDE: flashier than gnome, preferred by many, also mature

Xfce: lightweight, might be best for older low-end machines, or just for folks who like to keep stuff small and lightweight    :)

And don't forget about this link.

[http://www.psychocats.net/ubuntu/kdegnome](http://www.psychocats.net/ubuntu/kdegnome)

---

### Post by blarney on 2007-01-29
> **taurus said:**
> Is your machine connected to the net at all?  What's the output of this command from a prompt?

```
/sbin/ifconfig
```

okay I tried ifconfig and it comes back saying no dhcpoffers received.  It tried a few different ports.

when I tried sbin in front of it it said "sbin is a directory".

---

### Post by blarney on 2007-01-29
> **IYY said:**
> The commands mentioned above would work provided that your system is already connected to the Internet, or that there is a CD with the components on it (such as the Ubuntu Desktop CD).

To check your current IP address, use the command

```
ifconfig
```

Of course, you could just try pinging some website

```
ping -c 5 http://www.google.com
```

If your machine is not connected, you could try a command like

```
sudo dhclient
```

to try and obtain an IP address via DHCP.

If you can't manage to configure it with the command line, you might want to install the Desktop edition. It comes with a LiveCD which allows you to see the OS running prior to installation, a GUI, and all the power that the server edition provides.


Okay so I tried all three of those commands and pretty much got nothing.  when it went through the installation it setup the network card.   I have lights on the network card so I know I have a connection etc.

---

### Post by taurus on 2007-01-29
So you have a wireless card!  Even if the light is on, it doesn't mean that it's working.  Maybe you need to install a driver for it.  Can you post the spec of your machine and that name and model of that wireless card?

---

### Post by blarney on 2007-01-29
> **taurus said:**
> So you have a wireless card!  Even if the light is on, it doesn't mean that it's working.  Maybe you need to install a driver for it.  Can you post the spec of your machine and that name and model of that wireless card?


it's an ibm pII450 this is basically a test machine.  Once I have it up and going I will make my proliant server unix based.  It's a 6862-24u pII450.  I am not worried about very much overhead and such because it's only for testing and me gettiing comfortable with it.  Once I have it up and running and stable I will go ahead and set it up on the server.  It's not wireless either I have cat6 run throughout my house and my server rack in my basement which will control everything.

---

### Post by Stephen Howard on 2007-01-29
Given that setting up a wireless connection can sometimes be difficult, its best to revert to ethernet cable when initially configuring your machine.  Once everything is stable, then experiment with wireless configuration.

You probably shouldn't be running a server until you're a bit more familiar with linux - certainly don't do it if the server will be exposed to the internet.  Maybe its best to start from scratch with your installation disks and select a 'desktop install' (after first connecting to the router with a cable).   Once you have an desktop you can still set up servers afterward.

---

### Post by Stephen Howard on 2007-01-29
> It's not wireless either I have cat6 run throughout my house and my server rack in my basement which will control everything.

I dream of having something like that.  Congratulations!

---

### Post by blarney on 2007-01-29
> **Stephen Howard said:**
> I dream of having something like that.  Congratulations!

Well it's nice when it works.  but right now it's kind of ticking me off.  Changing cables and making a stiff drink.  Not sure which will help more but am hoping one or the other will.

---

### Post by blarney on 2007-01-29
okay I changed cables(yes I made them all and I have one or two that I need to redo) and when i did the "sudo dhclient" I got back a message that said "dhcp pack from 10.65.96.1".  

 I then tried the command "sudo aptitude install kubuntu-desktop" and it listed off some things and siad "done".  

It "couldn't find any package name or description matched "kubuntu-desktop" no packages will be installed, upgraded or removed.  0 packages upgraded, 0newly installed, 0 to remove and 0 not upgraded need to get ob of archives. After unpacking OB will be used."

so I got an ip it looks like but it wouldn't pull down these files or I am doing something wrong.

---

### Post by taurus on 2007-01-29
```
**sudo aptitude update**
sudo aptitude install kubuntu-desktop
```

---

### Post by blarney on 2007-01-29
> **taurus said:**
> ```
**sudo aptitude update**
sudo aptitude install kubuntu-desktop
```

I think you just became my hero.

---

### Post by blarney on 2007-01-29
Okay it's all done sitting at the prompt and does't say it needs to reboot or anything.  Is there a run command now to see my gui?

---

### Post by Maestro23 on 2007-01-29
> **blarney said:**
> Okay it's all done sitting at the prompt and does't say it needs to reboot or anything.  Is there a run command now to see my gui?

If you are at the console: startx

---

### Post by blarney on 2007-01-29
> **Maestro23 said:**
> If you are at the console: startx

cannot stat /etc/x11/x (no such file or directory), aborting. xinit:  Server error.

I'm tied looking this up and got nothing.  I found something about having to create a symlink.  Not sure what a symlink but I also found the command line.  I am not sure though if this is a generic command line and I could just use this or what.  I'm also not sure what it actually does so am a bit reluctant to try it.

"ln -s /usr/bin/X11/XFree86  /etc/X11/X"

Does this look correct?

---

### Post by Stephen Howard on 2007-01-29
Hmm, maybe:   apt-get install xserver-org

---

### Post by Stephen Howard on 2007-01-29
> **blarney said:**
> cannot stat /etc/x11/x (no such file or directory), aborting. xinit:  Server error.
...
"ln -s /usr/bin/X11/XFree86  /etc/X11/X"

Does this look correct?

Probably not.  On my system X is:

  File: `X' -> `/usr/bin/Xorg'

---

### Post by blarney on 2007-01-29
Mr. Howard I hate to say it did not work.  I just had the wife come down and yell at me so I am giving up till tomorrow.  I appreciate the help from all of  you.  I think once I get over this hump here I will be good I just have to figure out how to make this UI run.   If you guys have any good ideas please feel free to toss out anything you can.  This has been very educational and you guys would not believe how helpful and unusual it is to find people so willing to help.  I hope to return the favor as I learn more about this.  I for some reason after reading what others have said about this can see myself tossing out the microsoft software and just going with this.

---

### Post by Stephen Howard on 2007-01-30
you'll also need the xorg package:  [FONT="Fixedsys"]sudo apt-get install xorg[/FONT]

---

### Post by Maestro23 on 2007-01-30
> **blarney said:**
> Mr. Howard I hate to say it did not work.  I just had the wife come down and yell at me so I am giving up till tomorrow.  I appreciate the help from all of  you.  I think once I get over this hump here I will be good I just have to figure out how to make this UI run.   If you guys have any good ideas please feel free to toss out anything you can.  This has been very educational and you guys would not believe how helpful and unusual it is to find people so willing to help.  I hope to return the favor as I learn more about this.  I for some reason after reading what others have said about this can see myself tossing out the microsoft software and just going with this.

If you are trying to install KDE, this thread should help you:

[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

Don't give up yet man, this stuff is fun...:D

---

### Post by Stephen Howard on 2007-01-30
This guy has a to-the-point article about [installing X11 on his Ubuntu server]("http://www.dharwadkar.com/weblog/ubuntu02/view")

---

### Post by blarney on 2007-01-30
Okay guys much appreciated for all the help.  I spent a good part of my day reading all over this board here and there and finally got this thing installed.  Yes I tried pretty much every command line I could find and finally poof it worked. 

Now I have painted myself into a new corner.  I setup my resolution on it and I apparently set it too high since I can't make out a darn thing on my monitor now.  How do I change my resolution to 800x600 if I can't even see through the lines on the screen?  Is there a command line for this?

---

### Post by blarney on 2007-01-30
Okay guys much appreciated for all the help.  I spent a good part of my day reading all over this board here and there and finally got this thing installed.  Yes I tried pretty much every command line I could find and finally poof it worked. 

Now I have painted myself into a new corner.  I setup my resolution on it and I apparently set it too high since I can't make out a darn thing on my monitor now.  How do I change my resolution to 800x600 if I can't even see through the lines on the screen?  Is there a command line for this?

---

### Post by Stephen Howard on 2007-01-30
Try this thread:  [How to change resolution/refresh rates]("http://ubuntuforums.org/showthread.php?t=83973")

Once upon a time I recall that a user could use ctrl-alt-keypadplus and keypadminus to scroll through the various resolution settings in the xorg.conf configuration file, but that doesn't seem to be working anymore.

---

### Post by blarney on 2007-01-30
okay I tried to resetup my desktop but it wouldn't let me reset my display settings.  I tried a different monitor just to be sure I wasn't being a bonehead and still I just have this display with lines across it so I cannot make out anything.  I can see my mouse move around but it's basically just stirring up all the lines.  I am think ing because this is an older monitor I need to kick it down to 800x600 or even 640x480 but just don't know how at this point since I think any changes I would make would have to be done inside the desktop.

---

### Post by Stephen Howard on 2007-01-30
so you tried to edit /etc/X11/xorg.conf?

Can you be more specific when you say "but it wouldn't let me reset my display settings."  What error message did you get?

Can you also tell me the manf and model of the graphics card and monitor.

---

### Post by blarney on 2007-01-31
> **Stephen Howard said:**
> so you tried to edit /etc/X11/xorg.conf?

Can you be more specific when you say "but it wouldn't let me reset my display settings."  What error message did you get?

Can you also tell me the manf and model of the graphics card and monitor.

I didn't get an error message it just wouldn't let me do it again.  I went through the whole process of installing the desktop again and got nothing.  I didn't try that command though.

---

### Post by fasoulas on 2007-01-31
> **taurus said:**
> Do you have a network connection on your server?  If you do, you can install a window manager from a console with

```
sudo aptitude update
sudo aptitude install ubuntu-desktop <-- if you want to use Gnome
sudo aptitude install kubuntu-desktop <-- if you want to use KDE
sudo aptitude install xubuntu-desktop <-- if you want to use XFce4
```[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)


I know that my question may be of topic but if try one of the above
commants like:

```
 sudo aptitude install xubuntu-desktop <-- if you want to use
```

after installation will i be able to choose to log on to the xfce from the **sessions** menu on my log on screen?

---

### Post by WorldTripping on 2007-01-31
About to install my first Linux experience, so been doing a bit of reading up.

Found this that might help with the screen resoulution issues;
sudo dpkg-reconfigure xserver-xorg

Originally came from;
[http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)

Hope it helps.

---

### Post by Stephen Howard on 2007-01-31
> after installation will i be able to choose to log on to the xfce from the sessions menu on my log on screen?

Yes, I think so.

---

### Post by Stephen Howard on 2007-01-31
> **blarney said:**
> I didn't get an error message it just wouldn't let me do it again.  I went through the whole process of installing the desktop again and got nothing.  I didn't try that command though.

Blarney, I think you'll need to be clearer as to what's going wrong - 'got nothing' doesn't really help us diagnose anything.

---

