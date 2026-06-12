---
title: "[SOLVED] Mouse problems - invisible, then destructive"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by klocked_in on 2008-03-04
[SIZE="2"]Hello All,
I've looked at just about every post (I think) and I haven't found my problem yet, so here goes:
When I boot from the 7.10 live CD, everything works great.  So, I installed it on my system.
     Athlon 64 3200+
     1 GB RAM
     ATi RV410 [Radeon X700 Pro (PCIE)]
     Logitech Cordless Keyboard and Optical mouse
Then the fun began.  The next time I rebooted, the login screen came up, I logged in, and got to the desktop, only to (not) find my mouse.  I've determined that the mouse *is* there, but I can't see it.

So, after much research, I finally came across a post here ([http://ubuntuforums.org/showthread.php?t=524466](http://ubuntuforums.org/showthread.php?t=524466)) that I used.  I put the SWCursor option in only, and now I can see my mouse.  However... now the cursor leaves a big trail of "video snow" wherever it goes.  It still functions normally, it's just that I can't see everything well.

If I use the CD, everything works fine.  I don't know if it's a mouse problem, or a video card problem.  I tried to use a MS Intellimouse PS/2, but it does the same thing.  I found out how to navigate Ubuntu with Alt-F1, and I did the update manager (150+ updates), but the same thing.  Any suggestions/help would be *most* appreciated.

Thanks again,
klocked_in
[/SIZE]

---

### Post by neurostu on 2008-03-05
Under Administration have you looked at the restricted drivers managers to see if there are any "special" (not OS) drivers you can install. If it is a issue with your video card I would recommend installing whatever drivers it is telling you are available.

---

### Post by klocked_in on 2008-03-05
I have not tried that - I will however.

Today the screen is much worse.  Now when I move around using just the keyboard, the drop down menus don't fill in unless I arrow key or tab over them.  The more I read, the more I'm leaning to a video card issue as opposed to the mouse.

I looked at the restricted drivers manager and there is something there for the ATi card.  I'll attempt to apply it and see what happens.

---

### Post by neurostu on 2008-03-05
Good luck...

also you might want to check this out:
[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

It appears to have some good installation instructions for your video card in ubuntu

---

### Post by klocked_in on 2008-03-05
Well, I applied the driver, and rebooted, and now all I get is a black screen. So I rebooted using the live CD, and I edited the xorg.conf file to change the driver from 'fglrx' to 'ati'.  I also commented out the last two sections, as I think they were added. I rebooted and I was back to almost the start - mouse is invisible, no background, and I can navigate with the keyboard.

I will try your post and see if that does anything different.

Thanks very much for you time!

---

### Post by klocked_in on 2008-03-05
I'm holding my breath right now - I'm on the installed version, and everything is working ok.  I decided that before I was to do the fix from the path you gave me, I should start from a clean install.  So, I reinstalled, rebooted, and got to the desktop.  I did the update manager and the restricted drivers, and rebooted.  That got me the black screen.

Just to be different, I rebooted from the CD, but this time I used the safe graphics option.  Boy, everything looks crisp and clean.  I reinstalled, rebooted, and -presto- I'm here.  I'm afraid to do any updates now for fear of upsetting something.

I think I will skip the restricted driver update, and try to install all the security updates.

---

### Post by klocked_in on 2008-03-10
I wrongly blamed my mouse for the trouble I had, but it was in fact my video card (ATI).  So, I've got the machine running fine, and I've applied most updates except OpenOffice, which is over 70Mb in size, so I'm saving it for some free time.

Thanks again neurostu for your suggestions.

I'm done with this thread.

---

### Post by neurostu on 2008-03-10
Congrats on getting your problem fixed. 

btw if you publicly want to thank somebody you can click the little star on the bottom right of a post.

---

