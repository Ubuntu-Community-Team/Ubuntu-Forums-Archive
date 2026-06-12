---
title: "[SOLVED] Posted before, still an issue. Scroll up or down in the body of a window doe"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by Hopworks on 2007-12-19
I love Ubuntu Feisty Server, and will continue to try to make my transition over to it from Windows, but there is this nagging issue I can't seem to fix.

In Ubuntu, I can't scroll up or down in windows unless I have my mouse pointer over the scroll bar. I'd like to scroll up or down when pointed over the body of the window. Has anyone else had this problem?? 

I have no idea how to fix it. In Windows, you can use the mouse scroll wheel to scroll up or down if you have the pointer anywhere over the body of the window. For some reason, in Ubuntu, I HAVE to have that pointer over the scroll bar in order to scroll up or down.

Also, can't seem to get my forward and back buttons on my intellimouse to take me forward or backward in the web page hierarchy, etc.

Can someone please help?

Thanks for your time!

Hop

---

### Post by Hopworks on 2007-12-19
I've googled this, and didn't get any hits. Must be isolated to my install. God I wish I could fix this. Hasn't ANYONE had this problem here? =(

---

### Post by Hopworks on 2007-12-21
I still can't find a solution, and no one has replied. Maybe I'll try the hardware forums. There HAS to be a solution out there.

---

### Post by LaRoza on 2007-12-21
Odd, I, in Ubuntu, can scroll up and down when the Window isn't in focus (handy for when I am using Pidgin, and reading something in a browser)

Are you using GNOME?

---

### Post by Hopworks on 2007-12-21
> **LaRoza said:**
> Odd, I, in Ubuntu, can scroll up and down when the Window isn't in focus (handy for when I am using Pidgin, and reading something in a browser)

Are you using GNOME?

Yes, and I'm thinking seriously about using what-is-it-called... KDE? Kubuntu?

Just seems like there is more apps geared towards KDE, and less hassle. Not sure why I picked Gnome. I was new to Linux and Ubuntu, and picked a GUI.

The only two things that have been persistently annoying me is the mouse scroll wheel thing, and the buttons being backwards on almost everything in relation to the windows I'm trying to move away from. Buttons being backwards meaning, like when you get the popup window when running FireFox after closing it with multiple tabs open, the button to restore them is opposite from what you see in windows. Most other confirmation dialogs are that way too. Makes it hard when you are using two different OS's.

Oh, when I use the scroll wheel in a window, it scrolls side-to-side instead of up and down. It HAS to be a configuration setting somewhere. I can't for the life of me figure out why I can't find an answer. I've googled for months. It's probably something obvious, making me look like an idiot. I'm use to that role so no biggy. lol

---

### Post by LaRoza on 2007-12-21
> **Hopworks said:**
> Yes, and I'm thinking seriously about using what-is-it-called... KDE? Kubuntu?

The only two things that have been persistently annoying me is the mouse scroll wheel thing, and the buttons being backwards on almost everything in relation to the windows I'm trying to move away from. Buttons being backwards meaning, like when you get the popup window when running FireFox after closing it with multiple tabs open, the button to restore them is opposite from what you see in windows. Most other confirmation dialogs are that way too. Makes it hard when you are using two different OS's.

I don't know why you have that mouse trouble, sorry. You can use KDE apps in GNOME.

To install KDE:

```

sudo aptitude install kde-core

```

Kubuntu is Ubuntu with KDE and KDE apps, but you can install KDE on Ubuntu (choose it when you log in under "sessions". I don't know if that will fix the problem, I doubt it, but you might like it.

Blame Firefox for that, the DE or Linux doesn't have control over that.

---

### Post by maybeway36 on 2007-12-21
And also install kubuntu-default-settings if you don't like the KDE defaults.

---

### Post by Hopworks on 2007-12-21
> **LaRoza said:**
> I don't know why you have that mouse trouble, sorry. You can use KDE apps in GNOME.

To install KDE:

```

sudo aptitude install kde-core

```

Kubuntu is Ubuntu with KDE and KDE apps, but you can install KDE on Ubuntu (choose it when you log in under "sessions". I don't know if that will fix the problem, I doubt it, but you might like it.

Blame Firefox for that, the DE or Linux doesn't have control over that.

I like your sig by the way. Especially "Learn to Program in Python". I want to. I want to write apps that run in Linux to automate things for me. Would be a nice diversion from my embedded systems work. =)

---

### Post by Hopworks on 2007-12-21
> **maybeway36 said:**
> And also install kubuntu-default-settings if you don't like the KDE defaults.

Well, in about 20 minutes, I plan to use some help I got from tech9 for backing up my LAMP server for migration to new hardware. I wonder how much of that backup will affect my need to go KDE. Seems like it is easy from a working Feisty Server, but being still a newbie, not fully knowing the inner workings of Ubuntu Linux, I'll have to learn about all the parallel issues that come up.

---

### Post by LaRoza on 2007-12-21
> **Hopworks said:**
> I like your sig by the way. Especially "Learn to Program in Python". I want to. I want to write apps that run in Linux to automate things for me. Would be a nice diversion from my embedded systems work. =)

The first link is better. (The first one is my wiki, the second is another forum member that needs no naming)

My wiki, the first one, links to that wiki, but [http://laroza.pbwiki.com/Python](http://laroza.pbwiki.com/Python) has pretty good resources.

---

### Post by Hopworks on 2007-12-21
> **LaRoza said:**
> The first link is better. (The first one is my wiki, the second is another forum member that needs no naming)

My wiki, the first one, links to that wiki, but [http://laroza.pbwiki.com/Python](http://laroza.pbwiki.com/Python) has pretty good resources.

I always wondered about how to do things in Linux to automate things, or just write an app with a simple UI. Scripts are cool, but would love an app I can write that will give me feedback. I need to study up big time, but there are so many tools out there.

Ideally, I'd LOVE something like what I have in Windows, in Excel, in VBA, where you write the code, and can set up watch points, and output to the immediate window some sort of output. If the output isn't right, you can just stop and change the code, and run again. Can you link anything that is along those lines? I haven't checked your links yet, so it all may be there.

They call that an IDE I guess. For example, for PHP, in Windows, I edit my code in SciTE, save it, up it via an FTP app, access it on my remote server, then see the results. I'd like something more local. Any recommendations?

Thanks again for all your time, advice, and help!

---

### Post by LaRoza on 2007-12-21
>Ideally, I'd LOVE something like what I have in Windows, in Excel, in VBA, where you write the code, and can set up watch points, and output to the immediate window some sort of output. If the output isn't right, you can just stop and change the code, and run again. Can you link anything that is along those lines? I haven't checked your links yet, so it all may be there.

That is called a debugger, and Linux has them.

>They call that an IDE I guess. For example, for PHP, in Windows, I edit my code in SciTE, save it, up it via an FTP app, access it on my remote server, then see the results. I'd like something more local. Any recommendations?

You can use SciTE in Linux. As for what editor you want, that is a highly opinionated topic (you will never see recommend Emacs). For the programming forum, [http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39), the stickies address the IDE question.

You can set up an IDE for any language you want, although I neve use them. Geany looks good, in my opinion. I use Gedit, Kate, Kwrite and Vim.

---

### Post by Hopworks on 2007-12-30
After successfully (I think) moving over my Feisty install to newer hardware, I decided to tackle a couple of nagging problems, like this one. It turned out to be an entry in xorg.conf. I guess I should research harder, or better because it was a thread from 2005 that clued me in.

I'm not sure which did it, because I changed a number of things. Now I wish I had done one at a time so I could relay better solution info in this thread.

I changed two things in my mouse setup
```
Section "InputDevice"
    Identifier     "Configured Mouse"
```
removed
```
Option "Protocol" "ExplorerPS/2"
Option "Buttons" "7"
```
and added
```
Option "Protocol" "ImPS/2"
Option "Emulate3Buttons" "true"
```

but then I also removed tablet PC support, not sure why it was in there.
removed from Section "ServerLayout"
```
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
```

removed sections;
```
Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection
```

Now my mouse wheel works like I want it to, and now one step closer to linux and away from windows.

Still can't figure out how to get my left side button on my mouse to navigate back a page in Firefox, or anywhere for that matter, but that's another thread. =)

---

