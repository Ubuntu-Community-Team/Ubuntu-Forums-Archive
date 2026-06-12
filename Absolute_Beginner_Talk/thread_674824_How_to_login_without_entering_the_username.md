---
title: "How to login without entering the username?"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by Zdravko on 2008-01-22
I'd like to have my user name already written, when trying to login. Just like Windows. So that I only have to choose the user and then type its password to login. How do I achieve that?

---

### Post by quandary on 2008-01-22
go to System->Administration->Login Window

if you don't have permission, go to the command line:
run: gksudo gdmsetup

Go to tab local
in the field "Style" select Themed with face browser"

If you want to be automatically logged in, go to the tab "security"

click enable autologin, and write your username next to the field who says "User*

If you want to login as root, click "Allow local system administrator login"

---

### Post by ibizatunes on 2008-01-22
I dont no if that is a security setting but if u go 2 [www.gnome-look.org/](www.gnome-look.org/) the click Splash Screens
download a login screen, some of them have the usernames already populated....
Download and install 
system > admin > login window > local > add > select the theme > then make sure ubuntu has that as it default
That is how i got round it

---

### Post by Zdravko on 2008-01-22
> **quandary said:**
> go to System->Administration->Login Window

if you don't have permission, go to the command line:
run: gksudo gdmsetup

Go to tab local
in the field "Style" select Themed with face browser"

If you want to be automatically logged in, go to the tab "security"

click enable autologin, and write your username next to the field who says "User*

If you want to login as root, click "Allow local system administrator login"
This is not working. I don't want to be automatically logged in, but to have to choose my username and then write the password. Just like Windows.

---

### Post by quandary on 2008-01-22
> **Zdravko said:**
> This is not working. I don't want to be automatically logged in, but to have to choose my username and then write the password. Just like Windows.

You don't have to enable the autologin, you CAN.

Selecting the username should work with 
Go to tab local
in the field "Style" select Themed with face browser"

If it doesn't, are you using kubuntu?

---

### Post by ugm6hr on 2008-01-22
These are the kind of GDM theme you need:
[http://www.gnome-look.org/content/show.php/Green+Glass+GDM?content=57855](http://www.gnome-look.org/content/show.php/Green+Glass+GDM?content=57855)
[http://www.gnome-look.org/content/show.php/Avio-GDM?content=37395](http://www.gnome-look.org/content/show.php/Avio-GDM?content=37395)
[http://www.gnome-look.org/content/show.php/Relaxing+Water?content=48213](http://www.gnome-look.org/content/show.php/Relaxing+Water?content=48213)

There are lots more on that website, even XP-like ones:
[http://www.gnome-look.org/content/show.php/TwilightXP?content=71805](http://www.gnome-look.org/content/show.php/TwilightXP?content=71805)

EDIT:

There appear to be 2 default themes with a face browser - as per quandary's advice:
Happy GNOME with browser
Human List

Select one of these, and it should do what you ask (or use one of the gnome-look alternatives)

---

### Post by Zdravko on 2008-01-22
> **quandary said:**
> You don't have to enable the autologin, you CAN.

Selecting the username should work with 
Go to tab local
in the field "Style" select Themed with face browser"

If it doesn't, are you using kubuntu?
It is selected. But then I have to type my user name again.

> **ugm6hr said:**
> These are the kind of GDM theme you need:
[http://www.gnome-look.org/content/show.php/Green+Glass+GDM?content=57855](http://www.gnome-look.org/content/show.php/Green+Glass+GDM?content=57855)
[http://www.gnome-look.org/content/show.php/Avio-GDM?content=37395](http://www.gnome-look.org/content/show.php/Avio-GDM?content=37395)
[http://www.gnome-look.org/content/show.php/Relaxing+Water?content=48213](http://www.gnome-look.org/content/show.php/Relaxing+Water?content=48213)

There are lots more on that website, even XP-like ones:
[http://www.gnome-look.org/content/show.php/TwilightXP?content=71805](http://www.gnome-look.org/content/show.php/TwilightXP?content=71805)

EDIT:

There appear to be 2 default themes with a face browser - as per quandary's advice:
Happy GNOME with browser
Human List

Select one of these, and it should do what you ask (or use one of the gnome-look alternatives)
I didn't understand this. There is no Ubuntu login theme that supports Windows-like username chooser?

---

### Post by ugm6hr on 2008-01-22
> **Zdravko said:**
> I didn't understand this. There is no Ubuntu login theme that supports Windows-like username chooser?

There are. Lots.

2 are included (System->Administration->Login Window: Local tab):
Happy GNOME with browser
Human List

Follow the links for different customized versions.

---

### Post by Zdravko on 2008-01-22
Thanks. I had to choose the last one. It offered a user list.

---

