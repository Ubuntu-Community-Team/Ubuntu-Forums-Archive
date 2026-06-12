---
title: "newbie has an error"
date: 2006-01-14
forum: Absolute Beginner Talk
---

### Post by Solhan on 2006-01-14
When booting up normally, after I input my username and password, it goes to a brown screen with the following error message:

An error occurred while loading or saving configuration information for gnome_segv.  Some of your configuration settings may not work properly.

there is a Details button and a Ok button underneath that but in the same window, but I can't click on the Ok button at all.  Mouse seems to be working fine but it doesn't click in that window.  there is a window behind it and i can only see one and a part of another word of the message:

lp them

and the one button that I could see is:
velopers

I'm assuming the second window says that you can contact the developers to help them fix the problem or whatever, but thats the only button I can click on and it doesn't seem to do anything when I click the button.

the tops of these windows are not visible, otherwise I would move them around to be able to read the 2nd one better.  I have booted up numerous ways and can get to a recovery mode rather easily, I just don't know what to do once I'm there.

The last time it was working I had installed a media player that worked for the files that I wanted, so I removed all the players that it didn't say were neccessary besides that one.  I wish i could remember the name, but it was in a repository and I only removed ones that were also in the repositories.

---

### Post by bscbrit on 2006-01-14
Try to reboot the computer and enter recovery mode.  That should get you as far as the command line.  The command 'dmesg' might give a clue as to what is going wrong.

Have you ever managed to log in successfully, or have you had this problem since you installed from the CD?

If you have logged in previously, what were you doing or what happened immediately prior to this fault appearing?

If this is a new install, it looks like it didn't do everything correctly.  From the command line you could try

apt-get dist-upgrade

to see if that manages to correct the problem.

---

