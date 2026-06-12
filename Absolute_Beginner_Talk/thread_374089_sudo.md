---
title: "sudo"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by omrsafetyo on 2007-03-02
I'm used to running SCO UNIX (non-adminstratively - basic computer operator tasks, and proprietary binaries), in which I have the liberty of logging in as root/su.

It seems in Ubuntu, this feature is missing, and everything needs to be done with sudo.

I have no problem with this for the most part - but I have tried setting the date/time on my computer, as it is an hour off... and **sudo date 03010122** didn't seem to cut it.

I was trying to get this to work, and so I did set the password for root, to try and make it so that I could log in - but of course, this was to no avail.

So is there a way to make it possible to log in as su?

And if no, I'm thinking it will probably be best for me to get rid of my password for su, so that when I do use 'sudo', I am not prompted - how do I go about doing that?

Also, if no - how do I set my time??

It feels weird going back to square one..  but I do like to learn new things.  Thanks guys.

---

### Post by deadgobby on 2007-03-02
Here is the guide to answer your questions. 
[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

---

### Post by 23meg on 2007-03-02
> and sudo date 03010122 didn't seem to cut it.


You need to use the -s option to set the date; maybe that's why it didn't work.

---

### Post by omrsafetyo on 2007-03-02
> **23meg said:**
> You need to use the -s option to set the date; maybe that's why it didn't work.

I'm looking at the man page (albeit on a SCO system), and am not seeing -s option for date.  Care to elaborate?

---

### Post by scxtt on 2007-03-02
also, it should be in the format:

date MMDDhhmmYYYY

---

### Post by 23meg on 2007-03-02
> **omrsafetyo said:**
> I'm looking at the man page (albeit on a SCO system), and am not seeing -s option for date.  Care to elaborate?

From the man page of "date" on Ubuntu:

>        -s, --set=STRING
              set time described by STRING


If you don't use -s, it merely displays the date. Most of the standard UNIX tools have cloned GNU equivalents in Ubuntu, and their usage may sometimes differ.

---

### Post by omrsafetyo on 2007-03-02
> **scxtt said:**
> also, it should be in the format:

date MMDDhhmmYYYY

unless its different in Ubuntu, the year is not required.  We have a script at work that makes us just use the hour and minute (which also restricts us from changing the time by more than 2 minutes) - and I believe you can actually just use **date hhmm** - unless of course there are differences in Ubuntu over the UNIX systems I am more familiar with.

> **23meg said:**
> 
If you don't use -s, it merely displays the date. Most of the standard UNIX tools have cloned GNU equivalents in Ubuntu, and their usage may sometimes differ.
Thanks!  I'll try that when i get home.

---

### Post by scxtt on 2007-03-02
```
[font=courier]scxtt@kubuntu [~]
:> date 030203452007
date: cannot set date: Operation not permitted
Fri Mar  2 03:45:00 EST 2007

scxtt@kubuntu [~]
:> sudo date 030203452007
Fri Mar  2 03:45:00 EST 2007

scxtt@kubuntu [~]
:> date
Fri Mar  2 03:45:05 EST 2007[/font]
```

---

