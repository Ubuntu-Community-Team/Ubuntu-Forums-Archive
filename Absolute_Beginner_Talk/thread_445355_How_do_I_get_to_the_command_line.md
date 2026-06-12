---
title: "How do I get to the command line?"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by PhilKE3FL on 2007-05-15
Someone gave me a command line input but I have no idea how to get to the command line to enter it.

Thanks,

---

### Post by kpkeerthi on 2007-05-15
Applications -> Accessories -> terminal

Read the ubuntu desktop guide here [http://help.ubuntu.com](http://help.ubuntu.com)

---

### Post by wormser on 2007-05-15
Applications> Accessories> Terminal

You should right click it and add to panel to make a short cut.

---

### Post by Nythain on 2007-05-15
[SIZE=-1]Applications &#8594; Accessories &#8594; Terminal
or you could hit ctrl+alt+F2 through F6
[/SIZE]

---

### Post by Dr Small on 2007-05-15
Ctrl + Alt + F1
or, Applications > Accessories > Terminal
or Alt + F2 'gnome-terminal'

Dr Small

---

### Post by PhilKE3FL on 2007-05-17
Thanks to all for the help.

So far I've tried the Applications> Accessories> Terminal  and the Ctrl + Alt + F1

The first opens a small window, the other dumps yo u in terminal mode I guess.

So, how does one get out of terminal mode?

Also, thanks for the link to the desktop guide, I may find it in there.

Phil K

---

### Post by nvteighen on 2007-05-17
The "terminal mode" (not the "window") is actually called "Console". To exit from there, press Ctrl+Alt+F7.

There are six different "consoles" and you access them by Ctrl+Alt+(F1, F2, F3, F4, F5 or F6)

---

### Post by tompickles on 2007-05-17
wicked, cheers! was having the same problem of getting back to GNOME. wondered how i could get back!

so, when you first boot Ubuntu, GNOME is running in the 7th console? Consoles 1 through 6 are command line?!

---

### Post by nvteighen on 2007-05-17
> **tompickles said:**
> wicked, cheers! was having the same problem of getting back to GNOME. wondered how i could get back!

so, when you first boot Ubuntu, GNOME is running in the 7th console? Consoles 1 through 6 are command line?!
Well, I think it doesn't. I have always heard that there are just six consoles, but you could consider GNOME running over a "seventh" to remember how to return to it! (Is what I did... I had the same problem some time ago!)

---

### Post by tompickles on 2007-05-17
so, where does the GUI actually run?!?! bit of a linux noob tbh, but i have a few ideas! honest!

---

### Post by nvteighen on 2007-05-18
> **tompickles said:**
> so, where does the GUI actually run?!?! bit of a linux noob tbh, but i have a few ideas! honest!
After having done some research, I must conclude there must be a 7th console that automatically runs the "X Server".

Look this: [http://www-uxsup.csx.cam.ac.uk/pub/doc/suse/suse9.3/suselinux-adminguide_en/sec.suse.virt.konsolen.html](http://www-uxsup.csx.cam.ac.uk/pub/doc/suse/suse9.3/suselinux-adminguide_en/sec.suse.virt.konsolen.html)

It seems that you can change the amount of consoles and which you want to start X.

---

### Post by esoterica on 2007-05-18
You can also just type the word 

```

exit

```

in the terminal window to get out of it.

Other versions of Linux I've used have a box that works like the Windows RUN option in your list of applications like off your Windows START button. You just hit Applications and there it is, all ready for you to type all your shell commands directly into it.

I know it's available for Gnome because that's all I ever use, but I can't remember what it's called to look for it and install it. I was actually surprised to see Ubuntu didn't already include it by default, any other Linux distro I've ever tried I think included it by default, I haven't even been able to find it in the repos as an add on, though it would help if I could remember what it was named.

---

### Post by derred on 2007-05-18
The terminals 1-6 are set up to be independent text mode computers if you will (there called tty1-6/ tty being derived from the word teletype). You can be logged in to each of them with your 1 user or with any combination of users. the 7th is the first graphical interface and the one where the X server is started by default on most linux systems.
To log in to a terminal you just write your user name and password, to log out you enter the exit command(or hit CTRL+D).
To return to the graphical interface you can hit CTRL+ALT+F7.
If you want to open a terminal inside the GUI(as a window) I recommend the xterm as it uses less memory than gnome-terminal. 
You can quick launch xterm by pressing ALT+F2 and then entering xterm.
If you find yourself doing a lot of back and forth to the terminal there's a cool application called tilda that runs a terminal hidden all of the time and you can show it by pressing a button or combination. It looks like the quake console that you get when pressing `(that's where it gets the name)
Hope this helps, Cheers!

---

### Post by esoterica on 2007-05-18
Here's an example in RedHat of the "Run.." option being directly in your Applications list like in Windows...

[CENTER][IMG]http://www.redhat.com/docs/manuals/linux/RHL-7-Manual/getting-started-guide/figs/gnome60/mainmenu.gif[/IMG][/CENTER]

When clicked on this "Run..." it opens a small text box like window where you can type commands quickly and directly into it also like the Windows Run option does.

I thought I seen someone else a while back though using a newer option of this for Gnome, that actually gave you a mini terminal to type commands into directly in your Applications list, kind of like the Google Search box in the top of your Firefox web browser, but for running commands in and without having to open anything after you get your Application pop out list open.

---

