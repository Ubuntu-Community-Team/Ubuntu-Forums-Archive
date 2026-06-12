---
title: "Not getting menus on Toshiba A30 laptop"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by xxxmjgxxx on 2007-07-25
Help needed by a total newbie to Ubuntu & Linux.

A new install of 7.04, dual booted with WinXP Pro SP2 on a Toshiba Satellite A30 laptop (with ATI Mobility Radeon 9000 graphics). Have imported a couple of user accounts from WinXP during the install.

Login prompt comes up Ok. When I enter an account & password, the login goes thru to a screen with just wallpaper and a pointer, pointer moves OK with mouse, BUT no menu bars, icons or anything else on the desktop.

What can I do to get some menus etc. to come up on desktop?

[INDENT](_Note_: 

I thought I had this nailed when I came across a posting and reply called "**Feisty Fawn not working on Toshiba laptop**" - [COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=480280[/COLOR] . 

I implemented the suggested solution  - "* ...ctrl,alt,F1 ...to the terminal ... then use this command sudo dpkg-reconfigure -phigh xserver-xorg...*" - but it didn't fix it for me)[/INDENT]

Thanks

---

### Post by shearn89 on 2007-07-25
It could be that you need to enable restricted drivers for your graphics card. Not sure how to do this from the command line though. I'll do some searching...

---

### Post by shearn89 on 2007-07-28
You could try running "restricted-manager" from the command line, although not sure whether it will work if you haven't started a graphical desktop. Can you use alt-f1 to run a command?

---

### Post by xxxmjgxxx on 2007-07-30
Alt-F1 didn't do anything, so I assumed ctrl-alt-f1 is what I needed to do to go to a command line. 

Tried the "restricted-manager" command from there, but got a screenful of warnings - first of which included "...GtkWarning: could not open display". It looks like this is expecting a GUI to work.

---

### Post by jaded83 on 2007-08-20
ok i am a newb.

I have the same laptop ( Toshiba A30 ), and the same problem.

But before i formatted and installed ubuntu, i booted it off liveCD and it worked with the GUI working.  But it had a warning when it booted up in the top corner about 'restricted drivers'.

As i have about 2 hours linux experience i hope i have been helpful to someone out there and not just muttered BS.

If it was helpful, how can i fix it on mine. lol

---

### Post by Jem00 on 2007-10-24
Hey guys,

The same thing happened to me.
As an experiment I went in through recovery mode and created a new user...to see if it would work. In my case it was a fresh install and I had no documents to import.

So essentially go into recovery mode, delete your previous user, create a new user, and add it to the admin group.

```

deluser <user>                # <user> being whatever your username was
adduser <user>              #<user> being what you would like to name your user
adduser <user> admin

```

---

