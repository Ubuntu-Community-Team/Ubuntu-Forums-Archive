---
title: "Low vision: Cursor"
date: 2014-05-10
forum: Assistive Technology &amp; Accessibility
---

### Post by Kurt_Alan on 2014-05-10
**[SIZE=5][COLOR="#000000"][/COLOR][/SIZE]**

I am low vision.  The mouse cursor is a critical and precise input device.  The most obvious thing you could imagine doing with it for low vision people would be to make it bigger.  This is such a no-brainer.  I can't imagine a good argument against this solution.

Windows, which I no longer use, handles this exceedingly well.  Not only can you choose a large or an extra large cursor but you can also change the color, shape and add a tail.  For me, with one eye, it really helps my one eye to track the cursor when it has an adjustable tail.

Yet, in Ubuntu, since Dapper Drake, I have never seen a setting to change the cursor size.  I just ran a program which I downloaded from linux.softpedia.org called "whitelarge" which involved used gconf-editor.  All the procedures ran smoothly but no change.  I also tried "big-cursor" which I loaded from Synaptic.  That failed.  I also tried two editings from gconf-editor and dconf-editor.  They failed.

 :-(

---

### Post by sudodus on 2014-05-11
I don't know how to change cursor, but I'm sure there are people at the Ubuntu Forums who know. Let us hope one of them will find your thread, chip in and help.

I know a help gadget. You can use ***xeyes*** that 'look at' the cursor. Start one or more instances, for example in two or four corners. Try xeyes, they may help you locate the cursor :-)

You can use a shellscript similar to this to start xeyes in the four corners of the screen.

```

xeyes -geometry +0+0 &
xeyes -geometry +0-0 &
xeyes -geometry -0+0 &
xeyes -geometry -0-0 &

```

or if you want smaller eyes

```

xeyes -geometry 80x50+0+0 &
xeyes -geometry 80x50+0-0 &
xeyes -geometry 80x50-0+0 &
xeyes -geometry 80x50-0-0 &

```

Beware,  Xeyes watches what you do and reports to the Boss, according to the manual ;-) 
```
man xeyes
```

---

### Post by sudodus on 2014-05-11
I found this link that might help you change the cursor size

[http://askubuntu.com/questions/126491/how-do-i-change-the-cursor-and-its-size](http://askubuntu.com/questions/126491/how-do-i-change-the-cursor-and-its-size)

---

### Post by Kurt_Alan on 2014-05-11
**[COLOR="#000000"][/COLOR]**[SIZE=5][/SIZE]



"xeyes" gave me a good laugh!  So my one eye is watching two virtual eyes which are looking at my cursor, so if I can't find my cursor, I look at the machine eyes for the location . . . 

This is definitely an indirect method.  If I can get a big mouse cursor I'll be happy, so proceeding to your next reply.

Notes:

Hmm. Who is the Boss? I'm sure the Boss has more important stuff to think about. Sudo apt-get install xeyes revealed that this program is probably obsoleted--it goes back to 1988--and is now incorporated into x-11 apps. When I checked, this was already installed.  I could not find or initiate it.

I've never entered a script before. I see I do not need sudo and also that the script terminates when I close the terminal . . .

---

### Post by sudodus on 2014-05-11
> **Kurt_Alan said:**
> 



"xeyes" gave me a good laugh!  So my one eye is watching two virtual eyes which are looking at my cursor, so if I can't find my cursor, I look at the machine eyes for the location . . . 

This is definitely an indirect method.  If I can get a big mouse cursor I'll be happy, so proceeding to your next reply.

Notes:

Hmm. Who is the Boss? I'm sure the Boss has more important stuff to think about.

:-D
> 
Sudo apt-get install xeyes revealed that this program is probably obsoleted--it goes back to 1988--and is now incorporated into x-11 apps. When I checked, this was already installed.  I could not find or initiate it.

You type ***xeyes ***and finish with the Enter key in a terminal window (or use the command lines in my previous post).
> 
I've never entered a script before. I see I do not need sudo and also that the script terminates when I close the terminal . . .

Put the command lines in a file, give the file execute permissions, type its name in a terminal window, finish with the Enter key, and it will run. What script do you want to run, about xeyes or about a bigger cursor?

Did you try to make the cursor bigger according to this link?

[http://askubuntu.com/questions/126491/how-do-i-change-the-cursor-and-its-size](http://askubuntu.com/questions/126491/how-do-i-change-the-cursor-and-its-size)

---

### Post by Kurt_Alan on 2014-05-11
[SIZE=5]****[/SIZE]

Thanks for that link.  Re: ```
 sudo update-alternatives --config x-cursor-theme 
``` this is a powerful tool.  In an instant you get a list of six different cursors, besides the default.  You only have to input the number, enter, reboot to see the effect.

I found one cursor, #5, which is an improvement over the default: it is not bigger but it is black with a white border.  With this, it is easier to see when I am on a white web page, e.g. google.com  And the two-color contrast helps me to resolve it rather than it being plain white . . . So this is an improvement: if only I could make this one bigger, that would be the sweetspot . . .

Re: some of the other solutions here: I used the gnome-tweak tool but the GUI for this tool rendered impartially: uninstall.  It seems that with the end of Gnome as a DE for Ubuntu and its replacement by Unity, that some gnome tools, even though they may still be in the repositories may create problems.

I changed cursor size and themes both with dconf and gconf.  In both cases, all my settings seemed to "take" --they were still there after a reboot.  But the cursor never changed. So these solutions failed.  Any idea why? --and what is the difference between dconf and gconf? Should I use one and not the other or both?

Continuing to read your replies and following up . . .

---

### Post by sudodus on 2014-05-12
I'm glad you found a better cursor, but it is too bad that the tip about increasing the size does not work.

I'm sorry, but I don't know the gnome tools very well, because I use the light-weight flavours Lubuntu with LXDE and Xubuntu with XFCE most of the time. I hope someone who uses gnome and or Unity can chip in and help you.

What about the solution to simply have lower resolution than the default one (which is the highest)? Then everything will be bigger. You can easily change the resolution with the terminal command xrandr. In my case:

```
[COLOR=#0000ff]xrandr[/COLOR]
Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 16384 x 16384
DVI-I-0 disconnected (normal left inverted right x axis y axis)
VGA-0 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 530mm x 300mm
   1920x1080      60.0*+
   1680x1050      60.0  
   1600x1200      60.0  
   1440x900       59.9  
   1280x1024      60.0  
   1280x960       60.0  
   1280x800       59.8  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)
```

I can 'downgrade' the resolution from 1920x1080 to 1440x900 or 1280x800 (and keep the wide-screen) with the following commands

```
xrandr -s 1440x900
xrandr -s 1280x800
```
and reset it with
```
xrandr -s 1920x1080
```

You can make one-letter aliases for a couple of resolutions and easily switch depending on the application program you run, for example

```
alias c='xrandr -s 1280x800'   # custom resolution
alias h='xrandr -s 1920x1080'  # high resolution
```
Use the relevant resolutions for your screen and enter those lines into your **~/.cshrc** file (near the other aliases) if you like it.

---

### Post by Kurt_Alan on 2014-05-13
**[SIZE=5][COLOR="#s000000"][/COLOR][/SIZE]**

```
 xrandr 
``` and the -s flag really demonstrate the power of the CLI.  In an instant you can see multiple monitors (I have my netbook outputted to a large display via VGA), the default resolution, as well as available resolutions.  And in an instant you can change them.

I think that a sticky for CLI in the "Absolute Beginners" section could be useful--not just a list of help sources but frequently used commands.  They could be sub-divided.  For example, the above could come under "hardware."
Maybe someone could post a request in the General Help section to start assembling examples.  Then someone else could categorize them.  The work could be divided. 

Anyway, it turns out that my default resolution is *800x600.  When I drop down to 640x480 this does, in fact, solve my cursor problem but creates other display issues: "The cure is worse than the disease."

I'm going to try contacting the dev at linux.softpedia who ported the Windows' cursors to Linux and try to troubleshoot why this didn't work; also play more with gconf, dconf, and the tweak tools.

When I find out how to get a large cursor, I'll post the result here and mark this thread as solved.  It will be a good project. Thanks for helping.  You are teaching me a lot.

---

### Post by sudodus on 2014-05-13
If you search the internet for ***bash tutorials*** you will find many links. Try some until you find a tutorial that suits your way of thinking :-)

---

### Post by sudodus on 2014-05-13
Search the internet for ***ubuntu cursor size*** and you will find several links, for example this one

[http://handytutorial.com/change-cursor-theme-in-ubuntu-12-04-12-10/](http://handytutorial.com/change-cursor-theme-in-ubuntu-12-04-12-10/)

and chances are that one of them will work for you.

I don't which version, 12.04 LTS, 13.10 or 14.04 LTS, and which flavour, standard Ubuntu, Kubuntu, Lubuntu, Ubuntu Gnome or Xubuntu you are running. It might be easier to find a tweak that works in 12.04 LTS, which is well debugged and polished after two years, and standard Ubuntu has three more years of support, while the community flavours have one more year of support.

Furthermore, what graphics chip/card are you using, and what graphics driver?

---

### Post by Kurt_Alan on 2014-05-15
**[COLOR="#000000"][COLOR="#000000"][SIZE=5][/SIZE][/COLOR][/COLOR]**

Response to your last question:

I have on-board graphics.  I would assume, then, no driver?  I finally added specs to my Profile!

See the last item re: graphics.  Did I get that right? Could my rudimentary hardware be limiting my software graphics tweaking possibilities?

---

### Post by Kurt_Alan on 2014-05-15
**[COLOR="#000000"][SIZE=5][/SIZE][/COLOR]**

I have cursorily (Ha! Ha!) followed up your link.  I think you are right.  The problem is with the evolution of Unity from 12.XX to 14.XX.  A problem that was once solved no longer succeeds.  I have tried dconf-tools and dconf-editor.  This standard method no longer works in 14.04.  And the GUI for gnome-control-center (from terminal) crashed before I could edit anything.

I think grumblebum2 states the problem. Scroll down to the last reply.  I have yet to follow this up: 

[http://http://ubuntuforums.org/showthread.php?t=2048046&page=7&p=12994288#post12994288]("http://ubuntuforums.org/showthread.php?t=2048046&page=7&p=12994288#post12994288")

---

### Post by sudodus on 2014-05-16
Good luck with *grumblebum2*'s tweak :-)

---

### Post by Kurt_Alan on 2014-05-17
**[COLOR="#000000"][/COLOR]**

Thanks to you and grumblebum2, I now have a choice of 14.04 Unity cursors AND I can make any of those cursors very large:

First select cursor type: ```
  sudo update-alternatives --config x-cursor-theme 
```

Log off, log on.

Then make that cursor large: ```
  echo "Xcursor.size:48" > ~/.Xresources && gsettings set com.canonical.Unity.Interface cursor-scale-factor 2 
```

Log off, log on.

---

