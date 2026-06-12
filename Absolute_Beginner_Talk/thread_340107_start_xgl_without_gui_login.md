---
title: "start xgl without gui login"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by tocleora on 2007-01-16
Ok hope I explain this right... Originally I had the graphic login, when I wanted to start xgl I would select something in the bottom right corner and then log in... it would ask me if I wanted to make that the primary I'd say only for this session... Now I don't use the graphic login, I instead type in username and password and more or less run xstart.  The reason I don't run xgl all the time is because it's choppy on my computer.  So is there a way to run it from xstart just when I want to use it or do I have to use that graphic login?  Hope someone can help... although it's choppy I love to run it from time to time to remind me how much better ubuntu is than windows. :)  thanks!

---

### Post by amunimanghi on 2007-01-16
Try startxgl or something like that.

---

### Post by tocleora on 2007-01-17
Ok funny, story... I read your reply and I immediately thought "What?!" and started to write that if you don't have anything legitimate to reply with don't reply at all.  But fortunately I decided to listen to my momma ("if you don't have anything nice to say...") and just go research it myself... only to find out that the script I created is called... startxgl.sh... Oops.  So sorry for thinking the bad thoughts. :)

Now, I brought gdm back up so I could see officially what it's called... it's called "Sessions", I have a session for xgl, I select it, log in and it still works great.  So I turned gdm back off, logged in at the command prompt and I get an error when I try to run startxgl.sh immediately after logging in and before running xstart (something like can't start cause it can't find xwindows or gnome or something).  But when I run xstart and do it after gnome is up, it acts like it does something but windows disappear and running the second "startcompiz" script I have displays an error as well (some sort of font error).  So I'm guessing I'm suppose to somehow tell xstart to start using the session "startxgl.sh", is that what Xsession and possibly .Xsession is for?

---

### Post by amunimanghi on 2007-03-03
Maybe you mean startx? If it works with gdm, why disable it? Also, do this at a terminal and post it here: ```
 cat /etc/X11/sessions/xgl.desktop
```

---

### Post by tocleora on 2007-03-05
Yeah, I meant startx.  I don't start gdm because I created a menu that allows me to choose between monitor configurations for work and home.  I'm using AIGLX now so it's no longer an issue.  Thanks anyway.

---

