---
title: "Gnome Terminal and backup problem"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by fjr0122 on 2008-03-25
I've been running edgy on my main computer for over a year now, use it everyday and it has gathered a good bit of OS cruft, and picked up a few problems, one of them is with terminal emulation(?).

But, Maybe emulation isnt the right word. 

The gnome terminal application refuses to run, interestingly I had several other shells installed in the debian menu and those wont run either, I also installed the root terminal application which also wont work.  By wont work i mean I click the icon in the programs menu and it never launches, the computer acts like I didnt do anything at all.

This is only a problem because i was trying to backup my system using [this article]("www.arsgeek.com/?p=637"), and this command in particular 

>     sudo tar cvpzf arsgeek.backup.tgz –exclude=”/proc/*” \

    –exclude=”/lost+found/*” –exclude=”/dev/*” \

    –exclude=”/mnt/*” –exclude=”/media/*” –exclude=”/sys/*” \
    –exclude=”/tmp/*” –exclude “/var/cache/apt/*” /

Which I havent figured a way to copy from a browser to a command line (since the gnome terminal isnt working)

---

### Post by Samurai Penguin on 2008-03-25
I'm experiencing that with a game that was installed via Add-Remove
called gl-117

It used to run fine but as of last night it just will not launch. I checked
Add/Remove and it still shows as installed.

---

### Post by northern lights on 2008-03-25
I dunno quite yet why your shell doesn't work, but it most likely didn't get shot by "that command".

All you did was create a compressed file called arsgeek.backup.tgz. You can choose to delete that file again, especially if you've canceled the creation process before it was done. It was created wherever you ran it from (probably home folder).

One piece of advice: When I opened the article you followed one of the first things that struck me was it's date: Fall 2006! You realize the guy is running Dapper also? When it comes to backupping it should neither shoot your system nor change so quickly - nonetheless, a 2006 article might work if you wanna fix your car but usually it's outdated if it's about a comp - especially a comp with a linux system.

---

### Post by fjr0122 on 2008-03-25
I guess what I said wasn't 100% clear. 

I want to run that command, but havent been able to. 

I cant run it because my gnome terminal doesnt work, and I dont know how to paste it into a regular terminal session. 

So I need a fix for my terminal, or another good easy backup option.

I'm trying to get everything backed up because I am getting a new computer today (already recieved the hard drive).

---

### Post by northern lights on 2008-03-25
> **fjr0122 said:**
> I cant run it because my gnome terminal doesnt work, and I dont know how to paste it into a regular terminal session
Can or can you not access a shell? I'm sorry, but I don't quite understand what you mean by the gnome-terminal not working and you being able to have a "regular terminal session".

I doubt you simply mean the following, please don't feel offended by me providing this "solution":

A - if your browser is firefox, it needs to remain open after copying for the info to remain cached ("in the clipboard").

B - In the gnome-terminal pasting is "Shift+Ctrl+V"

--> If everything fails, how 'bout pen & paper copying and pasting via typing?!

---

### Post by fjr0122 on 2008-03-25
By gnome terminal not working I mean I click the icon and NOTHING happens AT ALL. No error, no window comes up, Nothing!

By normal terminal session I mean Ctrl-Alt-F2, as in outside of gnome and X. 

I could use pen and paper but that doesn't help the broken terminal. 

Additionally, back in the day I had Redhat and could paste into a "normal terminal session" from X or from any terminal program....

If that was working i could use Links. 

I think I got the backup more or less covered.  I used a program called file roller, I think. A graphical front end to tarball....

---

