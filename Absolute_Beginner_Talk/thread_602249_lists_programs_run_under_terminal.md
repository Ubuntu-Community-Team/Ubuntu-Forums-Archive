---
title: "lists programs run under terminal"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by Purplecatty on 2007-11-04
How do list all program that can be ran under terminal.  I did found one of the command on other blog (not ubuntu) that I tried it on Terminal and it did list all programs that I can run using terminal.  I saved it  in Firefox Bookmark.  Later, I backed up files and reformatted hard drive and installed Gusty Gibbon 7.10.  I realized that bookmarks that I saved wasn't available.  I goofed and now that I lost the information of command that I can list a programs that I can run under terminal. ](*,)

If I am not clear to you,  like If I want to run "kopete" under terminal, type "kopete" and hit return, It'll pop up on dekstop.or "k3b", CDburning software will pop up on desktop.  I wanted to list a program that can be ran thru Terminal rather than using mouse to click "Applications--Internet--Kopete".  

So Can you tell me what is it???:wink:8)  This time.. I will write it down so I won't forget or lose it!!!
Thanks!
Catty

---

### Post by jordanmthomas on 2007-11-04
This won't get ALL of them, but a lot (and mostly anything you'll want to run):
```
ls /bin > ~/Desktop/list
ls /usr/bin >> ~/Desktop/list
uniq ~/Desktop/list | sort > ~/Desktop/list2 && mv ~/Desktop/list2 ~/Desktop/list

```
It's probably an inefficient way of doing it, but after this you'll have a semi-complete list of commands available.  (A less lazy way would be to parse out what's in your $PATH and get things from there)

Also, rather than a list, I'd just use tab-completion.

---

### Post by nick_h on 2007-11-04
There are also commands in /sbin and /usr/sbin that you may want to add to the list.

---

### Post by jordanmthomas on 2007-11-04
I thought about that, but those aren't really commands a *user* runs.  Anyway, feel free to add them if you want Purplecatty.

---

### Post by Purplecatty on 2007-11-04
> **jordanmthomas said:**
> This won't get ALL of them, but a lot (and mostly anything you'll want to run):
```
ls /bin > ~/Desktop/list
ls /usr/bin >> ~/Desktop/list
uniq ~/Desktop/list | sort > ~/Desktop/list2 && mv ~/Desktop/list2 ~/Desktop/list

```
It's probably an inefficient way of doing it, but after this you'll have a semi-complete list of commands available.  (A less lazy way would be to parse out what's in your $PATH and get things from there)

Also, rather than a list, I'd just use tab-completion.

Ummh!  It is just couple of simple commands that listed programs that can be ran under Terminal.  What you did was different than what I recalled.  I think I remmy "ls" something.  when I typed couple of command,  terminal listed all the programs either hidden or not in alphabetcal order.  I think it was about 50 something program listed and I scrolled down.  I regretted that I should have written it down so I won't be asking anybody in this blog!  I am familiar with what's on the list that can be ran on Terminal.  

Actually,  I was on Kubuntu and was looking for screen resolution adjustment that was missing and I google searched and found out to be KDE- guidance.  I came across one of the blog related to KDE and the guy did mentioned something else about Terminal command and I tried it for fun of it.  I found it so cool.  So that's why I was asking anyone if they know a simple couple of code that lists programs hidden or not hidden in alphabetcally order.  I tried to remember what I did wording on google search that narrowed down to what I found,  It's been a while and I forgotten it and I reformatted that same hard drive few weeks ago and thought I backed up the bookmark but didn't!!!

Thanks
Catty

---

### Post by jordanmthomas on 2007-11-04
Well, I don't know what you're after if this was unsatisfactory.
Hitting tab twice in a row will list everything you can run (but you can't read it later)

Anyway, sorry I can't help any more.  Maybe someone else will understand exactly what you're looking for and help you out.

Good luck.

---

### Post by Purplecatty on 2007-11-06
Sure no problem.  THanks for TRYING to help me.  If I found something. I'll post it.
Thanks
Catty):P

---

### Post by nick_h on 2007-11-06
Perhaps you were looking for something like:
```
dpkg -l
```
but this will list packages rather than programs.

---

### Post by nickbooker on 2007-11-06
Was it tab completion you were after?

Double-press the Tab key at a clean prompt, e.g.

```
nick@merlin:~$ <TAB><TAB>
Display all 3498 possibilities? (y or n)  <Y>
:
!
./
[
[[
]]
{
}
2038.pl
411toppm
7zr
822-date
a2p
a2ping
a2ps
a2ps-lpr-wrapper
aalib-config
abiword
AbiWord-2.4
abw2html
accept
accessdb
ace_canfield
```

This will show the list in More so you can just press enter to scroll down one word at a time, or space to move a whole screen at a time.  Press q to quit the listing.

If you know the first or more letters, type that first to reduce the size of the list.  If there is only one possibility, it will autocomplete it on the first tab press.

Read the man page for Bash to find out more about completion, or search for Bash Completion on Google.  For the man page:--

```
user@host:~$ man bash
```

Hope this helps...

Nick

EDIT: Sorry jordanmthomas - didn't spot your reference to the tab completion ;)

---

