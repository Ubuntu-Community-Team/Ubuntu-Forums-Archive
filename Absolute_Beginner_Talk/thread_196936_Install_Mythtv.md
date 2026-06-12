---
title: "Install Mythtv"
date: 2006-06-15
forum: Absolute Beginner Talk
---

### Post by Russty of Oz on 2006-06-15
Hi,

I am trying to install Mythtv, I got it in synaptic but what is the eaisest way to install it?  I have looked at some of the threads but many I don't understand, however, there was one that I found a few days ago but I can't find it now.

I noticed that some are talking about version 1.9 from the mythtv.org site, but it is in tar.bz2 and I can't find how to install that type of file anywhere.  

Is there an easy way to install mythtv?

Russty.

---

### Post by Titus A Duxass on 2006-06-15
Search the forum there is a good how-to or go directly with this link:

[http://hyams.webhop.net/mythtv/myth_ubuntu.html](http://hyams.webhop.net/mythtv/myth_ubuntu.html)

---

### Post by Russty of Oz on 2006-06-15
That may as well be in chinese!  I just can't even get those commands to work.

Oh well, it looks as though I will have to keep windows for my Fusion TV card.

Russty.

---

### Post by Russty of Oz on 2006-06-15
Could someone explain what I am suppose to do with this, what is the X session?

[B]You must run mythtv-setup as the 'mythtv' user in order to complete mythtv configuration.  Note that this program requires an X display, so you must either login to an X session as the 'mythtv' user, or otherwise arrange for that user to have access to your X display.

You must complete all four steps presented in the program.

Once you have done this, you may start the backend by executing the following command as root:

/etc/init.d/mythtv-backend start[/B]

Russty

---

### Post by vigleik on 2006-06-15
[QUOTE=Russty of Oz]Could someone explain what I am suppose to do with this, what is the X session?

[B]You must run mythtv-setup as the 'mythtv' user in order to complete mythtv configuration.  Note that this program requires an X display, so you must either login to an X session as the 'mythtv' user, or otherwise arrange for that user to have access to your X display.

You must complete all four steps presented in the program.

Once you have done this, you may start the backend by executing the following command as root:

/etc/init.d/mythtv-backend start[/B]

Russty[/QUOTE]

I agree that installing mythtv is nontrivial. I did it, and I learned a lot on the way. You can ignore the parts about the mythtv user, running mythtv as yourself is fine. And you start the backend by typing "mythbackend" in a terminal window, then you start the frontend by typing "mythfrontend". First you have to run "mythtv-setup" though.

If you managed to install it from synaptic that's great. Ignore version 0.19 for now, the improvement from 0.18 isn't worth the extra trouble.

However, before you start, does your capture card work? Does something like "cat /dev/video0 > test.mpg" (and then ctrl-C after a few seconds) create a big video file? Or can you watch tv with any other program? Try mplayer. In my experience making the capture card work is the hardest part, and mythtv is not going to help you with that. If it doesn't work (and it likely won't until you load the correct driver) then that's something you have to fix first. Google for the driver and post again if you get stuck.

Vigleik

---

### Post by Christmas on 2006-06-15
Why don't you try TVtime? It is very simple and works well for me.
```
sudo apt-get install tvtime
```
But I don't know if it has features like video capturing etc.

---

### Post by Russty of Oz on 2006-06-15
Thanks guys, that is the sort of information I needed.  

Vigleik, I haven't got the Fusion DVB-T drivers installed yet, so I will get onto that first.  

Christmas, I just did what you suggested and IT WORKS!!  Well, at least the program works, I just have to insall the DVB-T drivers now. That was much eaiser than mythtv.   Thanks for that!!

Russty

---

### Post by Titus A Duxass on 2006-06-16
"That may as well be in chinese! I just can't even get those commands to work." - It seems that you are not ready for mythtv, it requires a little linux experience to install.  But you learn a lot during the process. First install breezy and get it working then your x-session problems will go away.

---

