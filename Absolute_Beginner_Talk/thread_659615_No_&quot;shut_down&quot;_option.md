---
title: "No &quot;shut down&quot; option?"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by NHmomma on 2008-01-05
Hi,

Having a bit of a problem, there does not appear to be a shut down button anymore in the log off menu.  

If I log off, it does not bring me to the switch user screen (login screen) or anything, it kicks me out to black screen and prompt...

I attempted to run x config stuff, and I was able to get back in, but still not power off button...  Need help..

---

### Post by rodo-&gt;dave on 2008-01-05
Check this thread and see if it helps:

[http://ww.ubuntuforums.org/showthread.php?t=658453&highlight=shutdown+button](http://ww.ubuntuforums.org/showthread.php?t=658453&highlight=shutdown+button)

Edit:
specifically this post
> 
Some reported a similar problem in Feisty Fawn 7.04. If I remember correctly, the fix was to:

1. Go to the top menu bar and choose System
2. Select the Administration menu option
3. Then choose the Login Window menu option
4. Enter your password when prompted
5. Select the Local tab
6. Check the box next to Show Actions Menu
7. Make sure Include Host Name Chooser below it is checked as well

The Shutdown and Restart options should will magically reappear! Not sure if this fix also works in Gutsy 7.10. See if this helps!


---

### Post by NHmomma on 2008-01-05
Thanks for the reply, I checked out the thread and the part you posted here... Well, I do not have a login window menu option.  Nothing on that system... admin... list...

Posted the same reply after checking the right click on apps. and then trying to find it that way..  

Any suggestions?

Carrie

---

### Post by SpookComix on 2008-01-05
I wish I had time to investigate this to confirm it, but I wonder about something:  Are you running "kdm" or "gdm" on startup?  I only ask because, on my laptop that was running Kubuntu Gutsy, I installed the "ubuntu-desktop" package so I could give Gnome a fair run.  I'm using "kdm" on startup.  On this laptop, I do not have the option for "Shut down."  I have to "Log Out," then do the shutdown from the "kdm" login screen.

On my wife's laptop, where I recently did a fresh install of Ubuntu Gutsy, she's got the Shut Down option.  However, since it's a default Ubuntu install, it's using "gdm" instead of "kdm".

Dunno, it's worth a shot.  I'll be testing it out myself soon.

--SpookComix

---

### Post by SpookComix on 2008-01-05
Ok, well, that worked for me.

I followed the advice in another thread to run

```
sudo dpkg-reconfigure gdm
```

Running this will give you the option to pick which of the two - gdm or kdm - that you want to run.  Now, when I tried this, I'm not sure if it worked properly.  I tried it and restarted X, but that didn't work.  I suspect that it might have worked if I rebooted, but I didn't want to reboot and find out that it *hadn't* worked...so just to be safe, I removed the "kdm" package altogether before rebooting.  I'm just being lazy.

Anyway, after the reboot I was using "gdm," and after logging in, I now have the "Shut Down" option.  Maybe that'll work for you.

--SpookComix

---

### Post by hilltop_yodeler on 2008-01-06
> **rodo->dave said:**
> Check this thread and see if it helps:

1. Go to the top menu bar and choose System
2. Select the Administration menu option
3. Then choose the Login Window menu option
4. Enter your password when prompted
5. Select the Local tab
6. Check the box next to Show Actions Menu
7. Make sure Include Host Name Chooser below it is checked as well


Hey rodo->dave, thank you for your post. Last night, I installed a bunch of new GDM themes and had set them up so that a login theme would be randomly selected at login.  I also installed Java JDK and JRE as well as Eclipse, so when I lost my ability to shut down last night, I was not sure if it was related to the installation of Java, Eclipse, or if it was related to the themes that I had installed.  Your suggestion solved my problem.  Thanks so much for your help!  

BTW: It took less than one minute to find the solution here on the forum.  The Ubuntu community is just one more testament as to why I love Ubuntu.  Thanks!

---

### Post by newlinux on 2008-01-06
Just for clarification, If you run GDM with with kubuntu (KDE) or KDM with ubuntu (gnome) you will not get all the logout/shutdown options.

---

### Post by rodo-&gt;dave on 2008-01-06
Here is the command you can run from the command line if you want to try it this way:

$ gksu /usr/sbin/gdmsetup

And Hilltop_Yodeler, thanks for the thanks but I just copied and pasted from the other thread so NHmomma wouldn't have to to look for it ;)

---

### Post by kachline on 2008-06-20
Perfect!
Worked like a champ under 8.04 (Hardy) as well.

---

