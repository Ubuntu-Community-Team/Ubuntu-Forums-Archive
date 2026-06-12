---
title: "[SOLVED] Sloooooooow Boot?"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by Webby_s on 2007-06-29
Ok so I went and installed Ubuntu on a dell 2350 with 1gig ram. .... when I boot from the hard drive it is sooooo sloooooow. I mean it takes for ever to get to the ubuntu start up. So to me it must be something with the bios or something with the setup of the desktop. 

Also i have followed the instructions from this site [https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html#internet-basic-procedure]("https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html#internet-basic-procedure")
I've done it all. I have a wired connection with the correct IP address and so on and the connection properties recognize the 'DNS' search domains but in firefox I don't get anything... nothing](*,) I go to the most simple websites too?

And I have a question about resolution but I have done searches so I will learn from those.

---

### Post by avik on 2007-06-29
When the computer says something about grub, press escape to go to the grub menu.  Choose the first one and press "e".  Choose the second one and once again press "e."  Get rid of the "quiet" and the "splash" options, press escape and press "b."  Now look at where it slows down and report back here.

---

### Post by Nyxess on 2007-06-29
are you using the live cd to instal it? if you are, its using the cd drive speed and it takes longer than normal. just a thought, maybe the right one(but probably not)

---

### Post by Webby_s on 2007-06-29
Thanks all for the reply .... I will try the edit of the grub because **Nyxess** I am not booting from the live CD. I thought of that too. Thanks again

Any thoughts on the internet thing going on. That is my next project.

---

### Post by Webby_s on 2007-06-29
Ok just edited the Grub  and it is still slow. If I had a timer I would say that between the time I push the power button to the time that the logon screen for Ubuntu comes on would be somewhere around 45 to 65 seconds. During this time neither the 2 CD rom drives or the HDD are turning or thinking.

---

### Post by avik on 2007-06-29
What I meant was that editing that line would show you (only on that boot up) what Ubuntu was doing as it booted up.  If you could tell us on what commands it's slowing down especially, that might help us understand where the problem lies.  Make sure you edit that command again, because it only holds for that particular boot up.

---

### Post by Webby_s on 2007-06-29
Ok thanks for the patients and the explination. I may, though, just make it a little harder for us all. I did as you said but the screen says.... Starting up...       then the screen flickers to nothing. Then after about 45 seconds the HDD starts spining and the light flickers then the screen flickers again and I see the Ubuntu log on screen and all is well.

Now I told you that story to tell you this one;  Is the flicker somthing to have to do with the desktop hooked up the my big screen and the TV doesn't recognize that resolution?

---

### Post by kspn on 2007-06-29
> **Webby_s said:**
>  Is the flicker somthing to have to do with the desktop hooked up the my big screen and the TV doesn't recognize that resolution?

Chances are tpretty good that this is why you aren't seeing anything during bootup. If you can plug your Desktop into a standard monitor then you should be able to see the info that you need to work out why the system is booting so sloooooooowly.

---

### Post by Webby_s on 2007-06-29
Will work on that tomorrow ... need sleep

Any internet ideas of why it isn't working.

---

### Post by avik on 2007-06-29
> **Webby_s said:**
> If I had a timer I would say that between the time I push the power button to the time that the logon screen for Ubuntu comes on would be somewhere around 45 to 65 seconds. During this time neither the 2 CD rom drives or the HDD are turning or thinking.

And I just realized this; 45 to 65 seconds from power on to logon screen isn't *that* long.  My boot up takes roughly that much time.

---

### Post by alienexplorers on 2007-06-29
My average boot time is 3 minutes.  I know my problem is obsolete equipment.  With a newer system I would figure boot times would be drastically improved.

---

### Post by Webby_s on 2007-06-29
Well I think it is something powernowd. I will do a search but if you all are willing to also help please do.  Because now I am unable to log on at all from the HDD. Only from the Live CD. So I am reinstalling. Could that have to do with me trying to hook it up to my 1366×768 big screen in some way?  Why am I having so much trouble?

---

