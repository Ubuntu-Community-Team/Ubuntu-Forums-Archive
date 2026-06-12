---
title: "Not at Maximum brightness after installing Macbook-Backlight-control"
date: 2007-03-16
forum: Apple Intel Users
---

### Post by AnthonyJK@gmail.com on 2007-03-16
[http://desrt.mcmaster.ca/dapper.xhtml](http://desrt.mcmaster.ca/dapper.xhtml)

After installing the backlight control from this site I can now controll my brightness levels using f2 and f1 but now my maximum brightness isn't that bright. I know this because when I suspend my computer and it wakes up. The screen is at maxium brightness but onces i get prompted for my password and log back in the screen dims. I hit f2 to brighten the screen more but it is a maximum brightness according to  my computer. Can anyone help? Thanks!

---

### Post by david_edmundson on 2007-03-17
I can possibly shed some light on this. I used the same backlight script. The brightness on the mac using the CLI tool ranges from 0-120 (ish). I'm a KDE user so I don't know what the backend is doing but I imagine it probably uses a normal 0-100. When the computer resumes from sleep, it defaults to maximum until the computer script takes over.

If I'm right, and it will need a gnome user to tell me, you'll need to see if you can adjust the gnome backlight manager to scale differently.

For any KDE users out there I've got a bodged version of the power manager to control the mac-backlight. PM me if you want a copy of it.

---

