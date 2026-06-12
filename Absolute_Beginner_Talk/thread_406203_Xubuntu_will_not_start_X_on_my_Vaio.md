---
title: "Xubuntu will not start X on my Vaio"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by AlanClone on 2007-04-10
Hello, I installed Xubuntu on my Sony Vaio PCG-F630 laptop.

The Specs:
AMD k6-III+ processor
188MB of RAM 
12 Gig hard drive

I need some help with getting the graphical interface to work.  When I start it up it goes straight into text mode.  If I enter the "startx" command the screen goes black and stays that way. Can anyone help me, please?

---

### Post by caffienefree on 2007-04-10
What if you type xinit?

---

### Post by x1a4 on 2007-04-10
> **caffienefree said:**
> What if you type xinit?

Don't do that.  Instead try *startxfce4*.  

Is the problem Xfce or GDM?  

Try this:  

See if GDM is running: 
*ps -A |grep gdm*

If yes: 
*sudo /etc/init.d/gdm restart*
else:
*sudo /etc/init.d/gdm &*


Post error messages.

---

### Post by AlanClone on 2007-04-10
> **x1a4 said:**
> Don't do that.  Instead try *startxfce4*.  

Is the problem Xfce or GDM?  

Try this:  

See if GDM is running: 
*ps -A |grep gdm*

If yes: 
*sudo /etc/init.d/gdm restart*
else:
*sudo /etc/init.d/gdm &*


Post error messages.

I tried the *xinit* and then the *startxfce4* commands. 
The same black screen is the result.

When I entered *ps -A /grep gdm* I see the message,
*ERROR: Unsupported SysV option.*

Upon Entering *sudo /etc/init.d/gdm restart* I get nothing

And *sudo /etc/init.d/gdm &* I see, 
*[1] 4432*

Even more interesting when I press Ctrl + Alt + F1 at boot I see a line which says, 
*FATAL: Error inserting sonypi (/lib/modules/2.6.15-26-386/kernel/drivers/char/sonypi.ko): No such device*

---

### Post by caffienefree on 2007-04-12
Type sudo /etc/init.d/gdm again, and take that 4 digit number (i.e. 4432) and prefix it with ps.

For example:

ps 4432

and please post the result.

---

### Post by x1a4 on 2007-04-12
> **AlanClone said:**
> I tried the *xinit* and then the *startxfce4* commands. 
The same black screen is the result.

When I entered *ps -A /grep gdm* I see the message,
*ERROR: Unsupported SysV option.*

It's supposed to be: ps -A **|**grep gdm
You entered the Forwardslash (**/**), instead of the Pipe **|**.  Press Shift when hitting the Backslash to generate the Pipe (**|**).

> Upon Entering *sudo /etc/init.d/gdm restart* I get nothing

And *sudo /etc/init.d/gdm &* I see, 
*[1] 4432*

Do you get the GDM login screen when this happens?  4432 is the process ID of GDM.  It means that GDM has started.  

> Even more interesting when I press Ctrl + Alt + F1 at boot I see a line which says, 
*FATAL: Error inserting sonypi (/lib/modules/2.6.15-26-386/kernel/drivers/char/sonypi.ko): No such device*

A kernel module is missing.  Try removing it.  Don't worry it's nothing vital.  As a matter of fact this is probably the cause of the problem as it's a character module.  

As the super user run 

modprobe -r sonypi

Then restart.

---

### Post by AlanClone on 2007-05-26
> **caffienefree said:**
> Type sudo /etc/init.d/gdm again, and take that 4 digit number (i.e. 4432) and prefix it with ps.

For example:

ps 4432

and please post the result.

No result...

I can see an error message about the BIOS briefly when I start X.
It says something about the BIOS so I am going to try updating it and then reinstalling xubuntu.

BTW do either of you know whether its worth updating Phoenix BIOS version4.0 re. 6?

Thanks.

---

