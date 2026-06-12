---
title: "How do I get rid of this brown screen?"
date: 2006-02-19
forum: Absolute Beginner Talk
---

### Post by Clark Nova on 2006-02-19
I've petty much got my PC set up as I want it now, with the login screen I want, icon themes, window themes etc. The only thing that bothers me now is when I log in it changes  to a brown screen showing me things like Nautilus and Gnome loading up. 

How can I get rid of it and change it to something I like better?

Thanks :)

---

### Post by unbutuju on 2006-02-19
Hey dude, hope ur having as much fun as I am with Ubuntu for the las few days!

Here you can change a few things about that:
GO TO: "System > Administration>Login Screen Setup" you will be prompt for password, wich is your password then read carefull and change what ever you think you should change!

C Ya

---

### Post by Clark Nova on 2006-02-19
I've been having lots of fun with it :D

I tried what you said and I thought I had changed the setting so that it would display my wallpaper but it is still showing me the brown screen when I first login. 

Which setting should I be changing specifically?

---

### Post by cronholio on 2006-02-19
I think you have to change the color setting in the GTK greeter tab. I'd try it myself now but I would have to re-login and I have tons of apps running.

---

### Post by unbutuju on 2006-02-19
hey there agn!

Yep, cronholio is rigth... it will do the trick, but!!
here is another : left clic your dekstop, bottom line :-) ,more options!

have fun

---

### Post by majikstreet on 2006-02-19
[http://ubuntuforums.org/showthread.php?t=77694](http://ubuntuforums.org/showthread.php?t=77694)

look at Change Login Splash.

HTH,
majikstreet

---

### Post by unbutuju on 2006-02-19
> ...brown screen showing me things like Nautilus and Gnome loading up.
How can I get rid of it and change it to something I like better?

Hi there, just figured out another way , specialy when you mentioned "gnome loading..."

System > Administration>Sessions

have fun!

---

### Post by shannonss on 2006-02-19
;) :-k  Keep playing around with the butttons and readong the help section that is how I figured out that there are several screensavers that at random keep rotating and will continue to until you figure out how to stop it . Don't get discouraged that is the fun of learning something new.
Shannon

---

### Post by shannonss on 2006-02-19
[QUOTE=unbutuju]hey there agn!

Yep, cronholio is rigth... it will do the trick, but!!
here is another : left clic your dekstop, bottom line :-) ,more options!

have fun[/QUOTE]
You go to System then to prefrences then to desktop background.
Your on your own from there.
Shannon

---

### Post by Clark Nova on 2006-02-19
Thanks very much guys, I'm now free of the splash screen :)

I still need to work out how to get rid of that nasty brown background though that appears just before my desktop loads. I've really been digging around but I'm still not there yet.

Any more suggestions?

---

### Post by Jedeye on 2006-02-19
go to System>Administration>Login Window and change the background color. I have attached a screen shot as I saw the same instructions were given earlier... but I figured you may have just overlooked the color box below the images.

good luck!

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=6275&stc=1&d=1140394392[/IMG]

---

### Post by SickTwist on 2006-02-19
[QUOTE=SiBuntu]Thanks very much guys, I'm now free of the splash screen :)

I still need to work out how to get rid of that nasty brown background though that appears just before my desktop loads. I've really been digging around but I'm still not there yet.

Any more suggestions?[/QUOTE]

There are two places that need to be changed. The first is accessed from System-->Administration-->Login Screen Setup as seen in the previous post. The second place is System-->Preferences-->Desktop Background (which can be seen in my attachment).

The first place changes the background for gdm which is the graphical login screen that you see when Ubuntu starts. The background color usually isn't visible because the Ubuntu logo/theme covers it. However it appears sometimes for a brief moment during the log-in. Once you change that setting it will take effect for all users.

The second setting adjusts the background color for your desktop. Again, this color is usually not visible because it is covered with a background image, but you can see the color briefly during the log-in before the background image loads. The Desktop Background color setting is separate for each user.

I usually set both the gdm and desktop background colors to black so that I don't see anything bright during log-in.

---

### Post by cronholio on 2006-02-20
> I still need to work out how to get rid of that nasty brown background though that appears just before my desktop loads. I've really been digging around but I'm still not there yet.

As I mentioned in my previous post:

> I think you have to change the color setting in the GTK greeter tab.

I tried it and it works. Have a look at the attachment to see what I mean. Strangely, my Login Screen Setup dialog looks different from Jedeye's.

---

### Post by Clark Nova on 2006-02-20
Yay! Thanks so much everyone who helped me with this!\\:D/

---

### Post by ejw2076 on 2008-02-07
Here is a follow up for anyone looking to solve this:
You can change it in the menu, but it will still show up before your wallpaper loads.

to solve this you can modify /etc/gdm/gdm.conf
-there is a backgroundcolor option, change it as you wish.

if that doesn't work,
modify /etc/gdm/PreSession/Default
change the default color value to what you want.  I had to use this method because of my dual-head set up.  Worked just fine.

---

### Post by gonzmark on 2008-02-28
Thanks ejw2076!  This was a pest for me as well.  The backcolor default value in /etc/gdm/PreSession/Default was the culprit.  Changing that did the trick.  Thanks for the tip.

---

