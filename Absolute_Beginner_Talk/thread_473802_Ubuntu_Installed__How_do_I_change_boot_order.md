---
title: "Ubuntu Installed | How do I change boot order?"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by ts51 on 2007-06-14
K. 

1st question:

Got Ubuntu installed. Now, how do I change the boot order so that XP Home is default? If someone could give me detailed instructions that'd be great. I will probably be using XP alot more, so it's annoying when linux loads and I want XP. 

2nd question: 

Also, I have downloaded the bcm43xx drivers... I was directed to them in another thread. Now the wifi card powers on and all that. Can someone please point me to a .deb package that will easily allow me to connect to me network? 


-TS51

---

### Post by ts51 on 2007-06-14
Going to try wifi radar

just need to know how to make xp at the top of the GRUB loader...

---

### Post by Rui Pais on 2007-06-14
```
gksudo gedit /boot/grub/menu.lst
```
now change line:
> default     0 
for the position of XP entry on grub menu.
(or count the lines 'title', first being 0)

As an example, if you have only one Ubuntu kernel, with 2 entries, Normal and Recovery mode, your XP should be then then 3rd on the list, so would be:
default 2

---

### Post by Mazza558 on 2007-06-14
> **ts51 said:**
> K. 

1st question:

Got Ubuntu installed. Now, how do I change the boot order so that XP Home is default? If someone could give me detailed instructions that'd be great. I will probably be using XP alot more, so it's annoying when linux loads and I want XP. 

2nd question: 

Also, I have downloaded the bcm43xx drivers... I was directed to them in another thread. Now the wifi card powers on and all that. Can someone please point me to a .deb package that will easily allow me to connect to me network? 


-TS51

If you've installed the drivers, you should be able to see an icon in the top right. Click on it and you should see a list of wireless networks available.

---

### Post by SDL on 2007-06-17
Hi. I'm also keen to boot into XP by default but when I use:
> ```
gksudo edit /boot/grub/menu.lst
```

I get the following error message:

> (gksudo:4366): Gtk-WARNING **: cannot open display:

What can I do?

Thanks for any help.

Stephen.

---

### Post by Rui Pais on 2007-06-17
](*,)](*,)](*,)
me type uid de elbows. (My fingers are dyslexic not me... )

Sorry, is **gedit** not edit. I'll change my post.

---

### Post by SDL on 2007-06-17
Thanks for your reply. Unfortunately, I now get a different error message:
> (gksudo:4199): Gtk-WARNING **: cannot open display:

I'd quite like to fix this as I'm having an unrelated problem where my PC completely crashes when Ubuntu opens as I've described here:
[http://ubuntuforums.org/showthread.php?p=2860569#post2860569]("http://ubuntuforums.org/showthread.php?p=2860569#post2860569")

Thanks for any help.

Stephen.

---

### Post by Rui Pais on 2007-06-17
> **SDL said:**
> Thanks for your reply. Unfortunately, I now get a different error message:


I'd quite like to fix this as I'm having an unrelated problem where my PC completely crashes when Ubuntu opens as I've described here:
[http://ubuntuforums.org/showthread.php?p=2860569#post2860569]("http://ubuntuforums.org/showthread.php?p=2860569#post2860569")

Thanks for any help.

Stephen.

Uhmmm... do you mind to post the output of:
```
ls -l .ICEauthority 
```

---

### Post by meborc on 2007-06-17
if your computer crashes when using ubuntu, you could boot into the recovery mode (second line in the grub menu)

when a lot of text has passed you by and you see cli (command line interface) then enter the following command:
```
nano /boot/grub/menu.lst
```
you will see your grub menu file... move cursor to the "default     0" line and change the number (if you have 2 ubuntu entries - one normal and one recovery) to 4

ctrl+o for save (click enter)
ctrl+x to close... reboot and see if xp is now the first choise

---

### Post by Rui Pais on 2007-06-17
Seems that SDL can boot to Linux, his computer frooze when logged on an X session (gnome i presume according to LiveCd used).

He/she can always go for a console Ctrl+Alt+F1. 
And he/she can simply choose Recovery Mode from boot menu.

Changing default to Recovery mode is a little too radical...

---

### Post by meborc on 2007-06-17
> **Rui Pais said:**
> Changing default to Recovery mode is a little too radical...
i think he wants XP to be the default... as the ubuntu install is not working right... at least this is what i understood from the first post ;)

---

### Post by Rui Pais on 2007-06-17
> **meborc said:**
> i think he wants XP to be the default... as the ubuntu install is not working right... at least this is what i understood from the first post ;)

oops, i misreading your post... and take your reference to use recover mode to set default to xp as instructions to default to that mode :)


anyway maybe SDL has only an incorrect permitions  on .ICEauthority and we can simply fix his Ubuntu :)

---

### Post by SDL on 2007-06-17
Hi. Thank you both for your replies, using meborc's suggestion my PC now boots into XP by default. :D

I probably should have mentioned earlier that I abandoned the LiveCD and installed the alternated CD 32-bit Ubuntu 7.04 onto a partitioned drive. Sorry!

Rui Pais, would it still be useful for me to:
> Uhmmm... do you mind to post the output of:
```
ls -l .ICEauthority
```

or was that for helping with the boot options? If it would help me solve the other problem I'd be very happy to post but unfortunately, I'm a very inexperienced Ubuntu user. When I typed it in I got an error message saying it doesn't exist - I think I must have typed it in the wrong place or something?

One more thing, unfortunately I can't use Ctrl-Alt-F1 when the PC crashes, even Alt-Sys-Rq+O doesn't work.

Thanks again for all the help.

Stephen.

---

### Post by meborc on 2007-06-17
does you computer crash in the recovery mode also? if not you could work on the problem from there...

---

### Post by Rui Pais on 2007-06-17
> **SDL said:**
> ...
Rui Pais, would it still be useful for me to:
ls -l .ICEauthority
or was that for helping with the boot options? If it would help me solve the other problem I'd be very happy to post but unfortunately, I'm a very inexperienced Ubuntu user. When I typed it in I got an error message saying it doesn't exist - I think I must have typed it in the wrong place or something?

One more thing, unfortunately I can't use Ctrl-Alt-F1 when the PC crashes, even Alt-Sys-Rq+O doesn't work.

Thanks again for all the help.

Stephen.

The instructions is to try to track what prevents your gedit and gksu to start. 
Usually thats an incorrect permission on that file... that by the way can make Gnome behave weird. Just to be sure,
do that on a command line on a terminal or on recovery mode (note this command is slightly different from the one i gave previously):
```
ls -l ~/.ICEauthority
```
if it says it don't exist you need to make a new one, if exist check if it says something like:
> -rw------- 1 your_username your_username 163 2007-06-12 21:17 /home/rui/.ICEauthority

---

### Post by SDL on 2007-06-17
The PC doesn't crash in recovery mode thankfully - as you say this is probably a good place to start fixing the problem.

I'm going to try the .ICEauthority thing and I'll post the results in a minute.

Thanks.

Stephen.

---

### Post by SDL on 2007-06-17
Turns out my .ICEauthority does exist, I just have to login first! It appeared exactly how you described it. I presume that means that it is as it should be.

Hmmm... back to square 1 on the crashing problem. Thank you both for sorting out my boot sequence.

Stephen.

---

### Post by Rui Pais on 2007-06-17
> **SDL said:**
> Turns out my .ICEauthority does exist, I just have to login first! It appeared exactly how you described it. I presume that means that it is as it should be.

Hmmm... back to square 1 on the crashing problem. Thank you both for sorting out my boot sequence.

Stephen.

Ok. Since your .ICEautorithy is correct you need to search for other causes.
Since your specific question on this thread is solved i will answer on your other thread and try to give some help.

See you.

---

### Post by Henrywantstobeapenguin on 2008-02-28
Thanks for this - worked a treat for me! 

I was trying to type Default 5 into the cmd prompt that could be accessed at the memory screen! :confused:

I'd looked over the Grub Documentation before coming here, I later found this how to

[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

Henry

---

