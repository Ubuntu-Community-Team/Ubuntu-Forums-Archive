---
title: "What are openbox and fluxbox?"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by mongooseman1128 on 2006-09-25
What are openbox and fluxbox? What are their counterparts in windows OS?

---

### Post by Mr Frosti on 2006-09-25
Openbox and Fluxbox are examples of Windows managers. Other examples of Window Managers are "Metacity", and "Kwin". The last two examples are components of larger packages called desktop managers because they include a lot of extra software such as email, web browsers, text editors, etc.

Linux is built on many layers of software that may or may not have a comparable Windows counterpart. A typical desktop heiarchy might look something like this:

Linux[CENTER]Windows[/CENTER]
Video Card                              [CENTER]Video Card[/CENTER]
------------------------------------------------------------------------------------------------------------------
Video Driver                            [CENTER]Video Driver[/CENTER]
------------------------------------------------------------------------------------------------------------------
X server (XFree86 / Xorg)               [CENTER]Microsoft's own[/CENTER]
------------------------------------------------------------------------------------------------------------------
Rendering Engine (GTK)                  [CENTER]Windows Explorer[/CENTER]
------------------------------------------------------------------------------------------------------------------
Desktop Manager                        [CENTER] Windows Explorer[/CENTER]
------------------------------------------------------------------------------------------------------------------
Window Manager (Kwin, Metacity, Compiz) [CENTER]Windows Explorer[/CENTER]

If you experiment with Linux pieces, you can see that many of these layers are interchangable. If you choose Fluxbox, or Openbox, be aware that these are "minimalist enviroments", meaning they will render the window, and you might have a menu to choose actions from.

Sorry if the diagram doesn't scale well. I was never good at ASCII art

---

### Post by mongooseman1128 on 2006-09-25
what are some heavier window managers? What is the default with Ubuntu?

---

### Post by mongooseman1128 on 2006-09-25
Oh, and thanks for the reply it's really helpful to know that the boxes are comparable to windows explorer. Kind of gives me a sense of where stuff stands in the hierarchy

---

### Post by snakyjake on 2006-09-26
> **mongooseman1128 said:**
> what are some heavier window managers? What is the default with Ubuntu?

Defaults:
Ubuntu = Sawfish
Kubuntu = kwm

Heavier = dtwm, scwm.

You can experiment and try different Desktops:

```
sudo apt-get install ubuntu-desktop
sudo apt-get install kubuntu-desktop
sudo apt-get install xubuntu-desktop
```

Don't forget to consider the "Desktops" such as KDE, Gnome, and others.

Linux is VERY cool because it gives you so much flexibility and choice of what works best for you.  For me, I use Xfce/XFwm, Fluxbox, and KDE.  From what I've noticed, they all seem to have the same functionality.

I've been mostly searching for lighter.  I'm tired of applications consuming more resources that are unnecessary, and then forcing me to upgrade to new hardware.  Rather use the money for other cool toys.  

Jake

---

### Post by 23meg on 2006-09-26
> **snakyjake said:**
> Defaults:
Ubuntu = Sawfish

Should be Metacity. Sawfish is the window manager in older versions of GNOME.

Side note: X11 and the window managers mentioned aren't Linux specific, but can run on other kernels as well, such as BSD variants.

---

### Post by bodhi.zazen on 2006-09-26
[[color=blue]Window Managers 4 X[/color]](http://www.plig.net/xwinman/)

---

### Post by snakyjake on 2006-09-26
> Linux is built on many layers of software that may or may not have a comparable Windows counterpart.

One of the great features of Linux is how customizable it is.  Each "layer" gives you choices and options.  Microsoft just gives it to you their way.  And they only give it to you every 5+ years.

---

### Post by mongooseman1128 on 2006-09-26
okay so I decided I'm gonna give some of the other window managers a try, so how do I switch between different ones when I have multiples installed?

---

### Post by mongooseman1128 on 2006-09-26
nevermind, I found how to start them, but now my question is how do I make them more robust? With fluxbox all I get is a little toolbar and a blank screen and open box there's nothing until I right click. How do I customize them to be more useful?

---

### Post by bodhi.zazen on 2006-09-26
Depends on the window manager.

Start with rox. Icons + background with drag and drop. Very easy.

[[color=blue]Eyecandy[/color] [color=red]Here[/color]](http://ubuntuforums.org/showthread.php?t=77694)

Search the Ubuntu site. Search Debian. Google search.

See My signature for some starters on Icewm and fluxbox. Openbox is roll your own. If you want a panel in openbox try fbpanel, perlpanel, and pypanel.

---

### Post by snakyjake on 2006-09-26
> **mongooseman1128 said:**
> ...how do I make them more robust? With fluxbox all I get is a little toolbar and a blank screen and open box there's nothing until I right click. How do I customize them to be more useful?

mongooseman1128, you have excellent questions that will probably help others.  You may want to start new threads so the thread subjects can also assist others with similar questions.  Thread subject lines are very helpful when we're surfing the forum :-)

---

### Post by mongooseman1128 on 2006-09-26
thanks snakyjake

---

### Post by bodhi.zazen on 2006-09-27
> **snakyjake said:**
> mongooseman1128, you have excellent questions that will probably help others.  You may want to start new threads so the thread subjects can also assist others with similar questions.  Thread subject lines are very helpful when we're surfing the forum :-)

New threads are fine, PLEASE search first as there are already a number of threads on these subjects and repetitive threads creates confusion.

---

