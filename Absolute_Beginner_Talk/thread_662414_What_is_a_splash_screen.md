---
title: "What is a splash screen?"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by moebob24 on 2008-01-08
What is it and how can I change it? On gnome look I can choose one but I don't what it is, when I see it, or how to change it.

---

### Post by overdrank on 2008-01-08
> **moebob24 said:**
> What is it and how can I change it? On gnome look I can choose one but I don't what it is, when I see it, or how to change it.

Hi and this may help good luck
[https://help.ubuntu.com/community/USplash](https://help.ubuntu.com/community/USplash)

---

### Post by moebob24 on 2008-01-08
> **overdrank said:**
> Hi and this may help good luck
[https://help.ubuntu.com/community/USplash](https://help.ubuntu.com/community/USplash)

Cool thanks.

---

### Post by ryanVickers on 2008-01-08
to turn on the default one just run this and it will be on next login
```

gconftool-2 --type boolean --set /apps/gnome-session/options/show_splash_screen 1
```
to turn it off change the 1 to a zero

---

### Post by moebob24 on 2008-01-11
How do I use already made custom ones...they won't show when I do the search. Is there a special directory to put them in?

---

### Post by ryanVickers on 2008-01-11
Yes, put them in "/usr/share/pixmaps/splash" and then to change your pic, go
```

gconftool-2 --type string --set /apps/gnome-session/options/splash_image /splash/<name of your pic>
```
I would recommend not having any spaces in the name ;)

P.S. obviously the path/name of the image includes the file extension (if there is one) - so if it was splashpic.png, you would obviously need to include the ".png" part ;)

---

### Post by antisocialist on 2008-01-11
if you prefer to use a GUI so you can see which splash screen you are choosing, go to sys>admin>login window and you can set it from there

im assuming the first reply told you what a splash screen is

---

### Post by moebob24 on 2008-01-11
> **antisocialist said:**
> if you prefer to use a GUI so you can see which splash screen you are choosing, go to sys>admin>login window and you can set it from there

im assuming the first reply told you what a splash screen is

The login window menu deals with the login window not the splash screen...
Yes i know what a splash screen is. I have been changing them alot but cant get a custom one up

---

