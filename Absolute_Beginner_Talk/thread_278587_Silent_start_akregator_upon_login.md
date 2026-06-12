---
title: "Silent start akregator upon login?"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by UnknownVariable on 2006-10-16
I'd like akregator to automatically launch and keep itself in the corner of my screen upon logging into Ubuntu. By that, I mean that no main window comes up, the program simply launches and sticks itself in the tray and continues with it's minutely checks for new feed updates.

Is there any way I can do this? I've looked through the settings and tried setting it to start in my sessions manager window thing, but the result I want wasn't achieved.

Thanks guys, you've always been a great help. :)

---

### Post by dbd on 2006-10-19
No idea how to do this, but I also would like to know how, so bumping this threat back to the top :)

---

### Post by doobit on 2006-10-19
I'm not near an Ubuntu machine right now, but in other distros that I work with there is a hidden script called .xinitrc.sh that will start up any X based program when X starts.
You can view invisible files in a terminal with the ls -a command, or in Nautilus or other file browser by checking View Hidden in the context menu.

---

### Post by dbd on 2006-10-20
I don't think that's really what we want.

What I want (and what I think UnknownVariable wants) is for Akregator to start, but only be visible as it's icon in the system tray, so its hidden from main view. I have it starting automatically because a link to it is in ~/.kde/Autostart/, but then it's main window appears on the screen and I often don't want to see it when I first start my PC, but I want it going in the background. Not a big deal really, but I'd guess there is an easy way to do this that I don't know about, so just asking if anyone knows how?

Thanks

---

### Post by dbd on 2006-10-20
hehe, I've worked a way to do it myself now, you can do it with dcop (a way to send commands to applications).

What you need is for this command:
> dcop akregator akregator_mainwindow hide
to run after akregator has started, then it will hide the main window (it will be shown for a shot time until this command is run, but thats better than nothing).

The way I do this is I have a script in ~/.kde/Autostart/ that runs everything I want at start up, and then runs dcop commands, so you could have this script:

> akregator &
dcop akregator akregator_mainwindow hide &

then akregator would start, and then disappear :)

Remember to make this script able to execute, goto the ~/.kde/Autostart/ directory then use the command:
chmod +x [script]
(where [script] is the name of the script).

Of course if you are using Gnome rather than KDE then this script needs to go somewhere else, but I'm sure you can work find that out pretty easily.

---

### Post by OmahaVike on 2007-12-11
thanks for the dcop tip.  extremely helpful.  did run into a snag, but hoping someone else might be able to lend a hand.

using dapper 6.06 with gnome.

took your suggested script and ran it manually.  was finding that the dcop wasn't working (to minimize it), so i was thinking that it was not communicating with dcop while checking the feeds.  so, i inserted a sleep, just to let it rest a bit.  seems to have worked.

created an executable script in my home folder which looks like this:
```

akregator &
sleep 10
dcop akregator akregator_mainwindow hide &

```

as far as gnome is concerned, it's really easy:

System -> Preferences -> Sessions -> (tab) Startup Programs -> Add -> (Point it to your script)

---

### Post by pb70 on 2008-03-26
It works in a more easy way too. Just add akregator to the autostart and add "--hide-mainwindow" to the start command.

akregator %i %m -caption "%c" --hide-mainwindow

This is my command for starting akregator.

---

### Post by vbcr on 2008-06-19
cool... this is wat i was lookin for... 
thanks..

---

