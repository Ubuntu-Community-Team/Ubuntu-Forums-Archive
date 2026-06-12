---
title: "Xubuntu :&quot; system font problem &quot;"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by kurian on 2006-12-09
hi

me installed xubuntu in my system and after slight modifications i found my system font to be too small

through googling i understood that its a bug in the xfce ....

i need to correct this is there any method by which i will be able to increase my system font ........

will be thankfull for a quick reply...

Along with that i need to ask you one doubt whether i could upgrade the xfce desktop environment in the xubuntu alone ???so that i will be able to correct any other bugs in the xfce

---

### Post by john.nicholls on 2006-12-09
Settings Manager | User Interface | Fonts

John

---

### Post by kurian on 2006-12-10
NO man that doesnt works ........................


its a bug in the xubuntu .....

is there any other method to overcome the problem


any new solution to this problem????

---

### Post by Gausus on 2008-01-22
> **john.nicholls said:**
> Settings Manager | User Interface | Fonts

John

I am having this problem and would like to try to navigate the menus to change the settings, but the font is SERIOUSLY small (like 2pt) could someone please post a screen shot of the menus so I can try to navigate by placement? I have been unable to find an image that will suit.

Thanks

---

### Post by Nadim on 2008-02-02
I just dropped a clean Gutsy Xubuntu install on an old machine I'm repurposing and had the same problem.  I had a bit of trouble finding help myself, as the standard solutions no longer seem to work correctly in the latest release.  

In my case, the root problem was caused by the fact that I'm hooked up to a large TV (1080p 61" Samsung DLP), which is helpfully reporting back information that convinces Xubuntu that the DPI is around 38.  I guess it's "helpfully" trying to ensure that a 9 pt font really is a physical 9 points, which is, of course, NOT what you want on a huge TV, since you don't actually sit 18 inches from it, and it is only 1080p, not 4320p.  if you want to check if this is your issue, try "xdpyinfo | grep resolution" from the command line once you get it workable (see below).  Mine was 38... But I digress...

The first thing you're going to need to do is get your terminal window up, so you can work the command line.  In the Applications menu (most top left icon on the screen), select Accessories (2nd one down from the top), then Terminal (2nd one up from the bottom).  In the terminal window, select Edit (2nd menu item over), Preferences (bottom item).  Then click the Appearance tab (2nd one down, left side).  The top item in that pane should be your font...Click it, and play with the right vertical slider to get a bigger font size...lower selections larger.  Then click Ok (bottom right).

Now, you should be good to work the command line.

Many solution posts on this topic focused on getting  "Xft.dpi: 96" into your X resource database.  And, that makes sense if the problem is your DPI.  But, when I tried the standard solutions (e.g. ~/.config/xfce4/Xft.xrdb, etc.), I couldn't get them to work.  I could do it manually (echo "Xft.dpi:96 | xrdb -merge"),  but couldn't get it to "stick".  When I looked at what was in my xrdb (xrdb -q), I found practically nothing, just one line about "*customization: color".  So I tracked down where that was, and added the line there, and presto, now it's working for me.  I'm not sure if this is the best / only solution, which is why I'm jotting down how I arrived at it, rather than just a mystical incantation.  :)  (anyone more knowledgeable, feel free to point out how I did it the hard way...)

Anyway, what worked for me was to add the following line to the end of /etc/X11/Xresources/x11-common:

Xft:dpi: 96

Then restart the xorg server (hit ctrl-alt-backspace), and presto.  Now you'll have to dial down your terminal font settings to make them sane again.

   -Nadim

---

### Post by whoscheesemine on 2008-03-09
> 

Anyway, what worked for me was to add the following line to the end of /etc/X11/Xresources/x11-common:

Xft:dpi: 96

Then restart the xorg server (hit ctrl-alt-backspace), and presto.  Now you'll have to dial down your terminal font settings to make them sane again.

   -Nadim

I am in love with you right now, look what I've been going through trying to figure that out:

[http://ubuntuforums.org/showthread.php?p=4480112](http://ubuntuforums.org/showthread.php?p=4480112)

thank you 40,987,498,763,978,639,876 times

... I take it back... no love for you! all that did was change the font of my desktop icons to 15, as soon as I checked the "use system font" box it all went back to tiny, and for some god forsaken reason (probably because I was up till 4AM trying to fix it) I didn't even notice that everything else was back to small again (font in prorams, font in the applications menu, font of my minimized items, font of my terminal) everything is tiny! what do I do? I'm assuming its my system font due to the little thing I checked int he desktop settings, but how do I change my system font?

---

### Post by jojopumpkin on 2008-03-26
> **Nadim said:**
> I just dropped a clean Gutsy Xubuntu install on an old machine I'm repurposing and had the same problem.  I had a bit of trouble finding help myself, as the standard solutions no longer seem to work correctly in the latest release.  

In my case, the root problem was caused by the fact that I'm hooked up to a large TV (1080p 61" Samsung DLP), which is helpfully reporting back information that convinces Xubuntu that the DPI is around 38.  I guess it's "helpfully" trying to ensure that a 9 pt font really is a physical 9 points, which is, of course, NOT what you want on a huge TV, since you don't actually sit 18 inches from it, and it is only 1080p, not 4320p.  if you want to check if this is your issue, try "xdpyinfo | grep resolution" from the command line once you get it workable (see below).  Mine was 38... But I digress...

The first thing you're going to need to do is get your terminal window up, so you can work the command line.  In the Applications menu (most top left icon on the screen), select Accessories (2nd one down from the top), then Terminal (2nd one up from the bottom).  In the terminal window, select Edit (2nd menu item over), Preferences (bottom item).  Then click the Appearance tab (2nd one down, left side).  The top item in that pane should be your font...Click it, and play with the right vertical slider to get a bigger font size...lower selections larger.  Then click Ok (bottom right).

Now, you should be good to work the command line.

Many solution posts on this topic focused on getting  "Xft.dpi: 96" into your X resource database.  And, that makes sense if the problem is your DPI.  But, when I tried the standard solutions (e.g. ~/.config/xfce4/Xft.xrdb, etc.), I couldn't get them to work.  I could do it manually (echo "Xft.dpi:96 | xrdb -merge"),  but couldn't get it to "stick".  When I looked at what was in my xrdb (xrdb -q), I found practically nothing, just one line about "*customization: color".  So I tracked down where that was, and added the line there, and presto, now it's working for me.  I'm not sure if this is the best / only solution, which is why I'm jotting down how I arrived at it, rather than just a mystical incantation.  :)  (anyone more knowledgeable, feel free to point out how I did it the hard way...)

Anyway, what worked for me was to add the following line to the end of /etc/X11/Xresources/x11-common:

Xft:dpi: 96

Then restart the xorg server (hit ctrl-alt-backspace), and presto.  Now you'll have to dial down your terminal font settings to make them sane again.

   -Nadim

I am having the same issue as you had. I am also trying to get the fonts to a legible size on a 40" Sony. I am having issues getting the terminal to work. When I start up I'm getting an error as soon as I log into XUBUNTU but I cant read it. When I select the Terminal I get kicked out to the login screen.

I resorted to "ctrl + alt + F1" to attempt your potential fix but I keep getting "permission denied" as a result. GRRRR! Pain in my butt!



I should mention that I was having the same font problem with Ubuntu 7.10 but it didn't happen all the time and I would just log out and back to remedy it.

Edit: I figured it out!

---

### Post by RobJohnston on 2008-04-15
Hi all, just correcting a typo, the edit to /etc/X11/Xresources/x11-common should be:

Xft.dpi: 96
not
Xft:dpi: 96

Worked for me once I did that.

Thanks Nadim for your work.

Rob.

---

