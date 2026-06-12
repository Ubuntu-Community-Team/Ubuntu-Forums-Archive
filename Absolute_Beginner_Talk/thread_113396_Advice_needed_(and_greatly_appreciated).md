---
title: "Advice needed (and greatly appreciated)"
date: 2006-01-06
forum: Absolute Beginner Talk
---

### Post by uneasyjd on 2006-01-06
Hello all.  I'm sick of being in thrall to Microsoft and would like to try Ubuntu, but I want to make sure I'm going about this the right way.  Here's my setup:

[INDENT]379 megahertz AMD K6-2 w/3DNow!
64 kilobyte primary memory cache
512 kilobyte secondary memory cache

Board: Compaq 04B0h
Bus Clock: 100 megahertz
BIOS: Compaq 686A1 11/11/98[/INDENT]

It's an antique Compaq Presario that was designed for Windows 98, but is now (uncomfortably) running XP.  I inherited it from a friend, so I haven't original Windows disks, etc.  It's got a 6GB hard drive (master) with XP on it, and another 6GB hard drive (slave) with 3.75GB of free space where I'd like to put Ubuntu to dual boot until i learn the ropes.

Q1. Will my old clunker be able to cope?

Q2. Am I correct in thinking that I need x86 as opposed to 64?  (The x86 live CD seems to work fine.)

Q3. Assuming an average amount of knowledge (and a willingness to learn) have I got a snowball's chance in hell of getting through the partitioning process without doing something catastrophic?

Also, I'm having keyboard trouble when i use the live CD.  I've got a Danish keyboard, but even when I choose that option it won't recognize anything that requires a 'ctrl-alt-    ' - i.e. splat, dollar sign, etc.  Is this fixable?

Many thanks in advance...

---

### Post by soops1966 on 2006-01-06
[QUOTE=uneasyjd]
Q1. Will my old clunker be able to cope?

>Yes

Q2. Am I correct in thinking that I need x86 as opposed to 64?  (The x86 live CD seems to work fine.)

>Yes

Q3. Assuming an average amount of knowledge (and a willingness to learn) have I got a snowball's chance in hell of getting through the partitioning process without doing something catastrophic?

>Yes

Also, I'm having keyboard trouble when i use the live CD.  I've got a Danish keyboard, but even when I choose that option it won't recognize anything that requires a 'ctrl-alt-    ' - i.e. splat, dollar sign, etc.  Is this fixable?

>Yes

Many thanks in advance...[/QUOTE]

Oh you wanted some information with that!

Right, start the install process. Nothing gets written to disk until you say so, so you can have some 'dry runs' until you are happy that your partitioning is just right. It is advisable that you make a full backup first though - accidents do happen.

You will be able to get gnome or kde running on an older machine but I'd advise looking at a lighter desktop such as XFCE (try Xubuntu) or a windowmanager such as IceWM and Windowmaker. I've used both of the last two very succesfully, they take a little more setting up but they are fast and responsive.

Your keyboard will need some post install configuration, there's a lot of info on the web, but I've never had keyboard problems so I can't help you there.

If you've got a willingnes to learn you'll get on just fine with Linux.

Good luck and come back if you need any further help.

Soops

---

### Post by Lord Illidan on 2006-01-06
[quote=soops1966]Oh you wanted some information with that!

Right, start the install process. Nothing gets written to disk until you say so, so you can have some 'dry runs' until you are happy that your partitioning is just right. It is advisable that you make a full backup first though - accidents do happen.

You will be able to get gnome or kde running on an older machine but I'd advise looking at a lighter desktop such as XFCE (try Xubuntu) or a windowmanager such as IceWM and Windowmaker. I've used both of the last two very succesfully, they take a little more setting up but they are fast and responsive.

Your keyboard will need some post install configuration, there's a lot of info on the web, but I've never had keyboard problems so I can't help you there.

If you've got a willingnes to learn you'll get on just fine with Linux.

Good luck and come back if you need any further help.

Soops[/quote]

You can choose your keyboard in the installation.
Willingness to learn = Excellent Linux user!

Goodluck and have fun!

Note, if you find it too slow, consider Damn Small Linux.. Also consider getting some more RAM..

---

### Post by uneasyjd on 2006-01-06
[QUOTE=Lord Illidan]You can choose your keyboard in the installation.[/QUOTE]

I have tried that several times now - choosing Danish out of the list, using keystroke recognition, etc. - no luck.

[QUOTE=Lord Illidan]Also consider getting some more RAM..[/QUOTE]

I have 320MB of RAM installed.  (Probably should have mentioned that...)

---

### Post by uneasyjd on 2006-01-07
Many thanks!  Fingers crossed...

---

### Post by newuser111 on 2006-01-07
i think you can run ubuntu fine, 256mb ram would be a comfortable minimum i say

you also have the the option of trying Xfce (xubuntu) or fluxbox after you have installed ubuntu, if you think its running slowly

and yes use the 386/686/ not the 64bit kernel

---

### Post by uneasyjd on 2006-01-08
It worked!  (Although partitioning was a bit hellish - I ended up having to give Ubuntu a whole HD to itself.)

Thanks again for the help!

---

### Post by Mustard on 2006-01-08
Is it running well on your system?

---

### Post by uneasyjd on 2006-01-08
Well, I wouldn't say that it's lightning-quick, but I'm still running GNOME...

Also, last night it had a tendency to freeze if I left it alone for more than 15 minutes or so.  Today, however - no problems. (Knock wood.)

---

### Post by Mustard on 2006-01-08
[QUOTE=uneasyjd]Well, I wouldn't say that it's lightning-quick, but I'm still running GNOME...

Also, last night it had a tendency to freeze if I left it alone for more than 15 minutes or so.  Today, however - no problems. (Knock wood.)[/QUOTE]

Sounds like it might be a problem with the power management when it goes into screensaver mode.  You could go into System>>Preferences>>Screensaver, then click on 'Advanced' tab and turn off power management and see if that helps.

In terms of the speed problem, the suggestion given earlier of installing xubuntu-desktop might be an idea you could explore.  You can have both gnome and xubuntu-desktop installed, assuming you have enough disk space.  At the login screen you can choose which one you want to use in the Sessions option, after you've installed xubuntu.

---

### Post by poofyhairguy on 2006-01-08
[QUOTE=uneasyjd]It worked!  (Although partitioning was a bit hellish - I ended up having to give Ubuntu a whole HD to itself.)
[/QUOTE]

Yeah...Ubuntu likes to have its own hard drive. I give it two.

And with that much RAM and some determination, you can't fail!

---

### Post by uneasyjd on 2006-01-08
[QUOTE=Mustard] ...assuming you have enough disk space... [/QUOTE]

Which brings me to my next question - where can I check that?  (I'm still finding my way around...)

---

### Post by Mustard on 2006-01-08
[QUOTE=uneasyjd]Which brings me to my next question - where can I check that?  (I'm still finding my way around...)[/QUOTE]

Applications>>System Tools>>System Monitor  in the 'Devices' tab. :)

Also if you go to the Applications>>Accessories menu and open a terminal, you can type in this command...

```
df   

#the df command will report filesystem disk space usage
#or this one below for human readable format

df -h


#to read the manual for the df command type this command...

man df

#hit the 'q' key to exit the manual

```

---

### Post by uneasyjd on 2006-01-08
[QUOTE=poofyhairguy]And with that much RAM and some determination, you can't fail![/QUOTE]

That much RAM, some determination, and these forums!  Thanks again to everyone who took the time to answer my questions.  The level of helpfulness and sense of community here is really remarkable (and one of the things that convinced me to try Ubuntu).

---

### Post by johnraff on 2006-01-08
(Is it OK to butt in on someone else's question like this? If not I won't do it any more, but I'm also looking for something lighter than Gnome for an old machine.)
[QUOTE=soops1966]You will be able to get gnome or kde running on an older machine but I'd advise looking at a lighter desktop such as XFCE (try Xubuntu) or a windowmanager such as IceWM and Windowmaker.[/QUOTE]
Sorry, but what's the difference between a desktop and a windowmanager?

---

### Post by super on 2006-01-08
[QUOTE=johnraff]Sorry, but what's the difference between a desktop and a windowmanager?[/QUOTE]

ha! ha! thats the fifth time in a week i've heard that question. :razz: 

basically a window manager is the thing that draws the borders and the _  []  X (minimize, maximize, close buttons on your windows) a desktop environment includes a window manager and a heck of a lot more.

[here is a more informative post]("http://www.ubuntuforums.org/showthread.php?t=87276").

---

### Post by johnraff on 2006-01-08
Many thanks, that's just what I was looking for!  :)

---

