---
title: "[SOLVED] lib/ x11/fonts?"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by acowboydave on 2007-07-25
Hello getting this warning on a upgrade install../usr/lib/x11/fonts/misc- does not exist. Anyone know how to fix?

---

### Post by Pragmatist on 2007-07-26
> **acowboydave said:**
> Hello getting this warning on a upgrade install../usr/lib/x11/fonts/misc- does not exist. Anyone know how to fix?

When do you see the message?  Does the upgrade complete?

---

### Post by acowboydave on 2007-07-26
Hello thanks for the reply, no I get a unable to install and maybe run apt-get update or a install missing line. In the dpkg log file I see a lot of half installed or none files after a unpack.

---

### Post by Pragmatist on 2007-07-26
please post your **/etc/apt/sources.list**

---

### Post by Anicka on 2007-07-26
What does you xorg.conf-file contain? ```
grep fonts /etc/X11/xorg.conf
```
And do you have any files in /etc/lib/X11/fonts?
If you go to synaptic you can do Edit -> Fix broken packages or in the terminal ```
sudo apt-get install -f
``` that should force the system to fix problems.

Edit: Of course I meant that you should check your /usr/lib/X11/fonts, not /etc/

---

### Post by acowboydave on 2007-07-26
hope I am doing this right

---

### Post by Anicka on 2007-07-26
The source-file looks ok. Have you tried to do "fix broken packages" in synaptic yet?

---

### Post by acowboydave on 2007-07-26
Hello yes and this is what it looked like

---

### Post by Anicka on 2007-07-26
Do you still have problems trying to upgrade? You can try to trick the program (apt-get, aptitude, synaptic, dpkg) if you create the files that it's looking for. Sometimes different packages have files with the same name and play tricks on each other. When you are upgrading something, it's (as I understand it) a uninstall old, install new version procedure. And that gives an error message if the file that should be there, isn't.

---

### Post by acowboydave on 2007-07-26
Thanks to everyone,  don't know if it's fixed also edited synaptic and clicked fix broken pkgs came back with a message all dependencies fixed.

---

### Post by Pragmatist on 2007-07-26
What happens if you comment out the last line in /etc/apt/sources.list  The one that reads:
> deb [http://repoubuntusoftware.info](http://repoubuntusoftware.info) feisty all

This is probably not the solution, but it easy enough to check.

---

### Post by acowboydave on 2007-07-26
Hello, not really understanding "comment out" but went back to the dpkg log and picked out a failure and tried apt-get to install, it went ok. I believe the problem is fixed, when I try a few more hopefully I can mark this one solved.

---

### Post by Pragmatist on 2007-07-26
> **acowboydave said:**
> ...not really understanding "comment out"...

To comment out a line, you just put a hash mark (#) in front of it.  

This:
>                               
deb [http://repoubuntusoftware.info]("http://repoubuntusoftware.info/") feisty all
Becomes this:
>                               
# deb [http://repoubuntusoftware.info]("http://repoubuntusoftware.info/") feisty all
 The hash mark designates the line as a comment so it is ignored (comments are used extensively by programmers to make notes to themselves and others.  They want them just to be read by humans but ignored by the computer).  If you decide you want the computer to read the line again, you just remove the #

---

### Post by acowboydave on 2007-07-27
Hello this is what I am getting now with apt-get update

---

### Post by acowboydave on 2007-07-27
Problem solved with everones help had  to use gedit to get sources list again, had dupes in my sources  list. and the ran update' Thanks again to all that helped.

---

