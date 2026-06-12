---
title: "What is going on....."
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by wasteoftime on 2007-02-01
Hi all, 

I've just installed ubuntu, and i have to say i'm impressed. Firstly its the first linux apart from Puppylinux that i've managed to get working and i've tried a few. Secondly i'm from M$ windows and am currently dual booting it on my laptop which has impressed me even more!

As a new user or noob i've a few questions and am hoping that i can find the answers here as at the moment i'm considering just giving up on linux. I'm a big fan of free software and don't agree with M$ philosophy but... on the other hand if i didn't have this dual booting id have nothing done!!

I'm not trying to antagonise anyone but what is going on?


Here are my questions:

I've installed WINE apparently where is it? its not in the Applications menu. I've searched for it and all i get is a description page. I've also installed other software but can't find it either; is there some secret place this stuff is installed that only the initiated know of?

Is there an application that shows the filesystem in tree form? as i would find this helpful.

How do you run applications that you have installed but can't find? (i've installed them from the add and remove program app)


I might be taking things for granted coming from windows and i know windows is full of holes but at least its more intuitive, i can't get my head around linux. I expected some difficulties like drive issues, compatibility problems, and not being widely supported, but what chance do noobs have if the basics such as installing software are soooo hard. 

I've got a full time job and can't study to be a programmer that linux expects you to be... help

---

### Post by taurus on 2007-02-01
1.  You can use nautilus to navigate around in your system.  It should be in Places -> Home Folder.

2.  If you know the name of the program, you can run it directly from a terminal by typing in the name of it.

Applications -> Accessories -> Terminal
```
**program_name**
-or-
firefox
```

3.  You don't have to be a programmer to use Ubuntu or Linux because I am not a programmer and I have been using Linux for years.  ;) 

Here's a guide showing you how to install something on Ubuntu.
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Happy_Man on 2007-02-01
Well now, let's get your questions answered:

Wine is not going to be found in your Applications menu, because it's very simple to use. Just go find some .exe and double-click. No, I'm not kidding. Wine will automatically boot itself up and run your app! 

I'm not sure about the filesystem tree, as I've never needed one, but you might want to search google and these forums. There must be one out there somewhere! :)

If you can't find the application, simply go to the terminal (Applications-->Accessories-->Terminal) and type in its name. If you're lucky, it should start. If it doesn't, go into Synaptic and check exactly what its name is, and then go type that in. 

And, linux doesn't expect yout to be a programmer. I haven't touched the terminal in about half a year now, and the world is running fine for me. ;) And besides, these forums are an incredible resource. Almost every question you may have can be answered here. It's a great place; use it! Hope this helps!

EDIT: Darn, I got beat to it. Ah well; taurus's advice is good. Me, I'm just here for kicks. ;)

---

### Post by annda on 2007-02-01
you don't have to be a programmer to copy and paste or click something.

if you like linux, get to know the terminal/command line (Applications->Accessories->Terminal). it's actually very nice because it talks to you - type a command or a program name and it will just launch it or give you error messages telling you what is wrong. for example, if you install avidemux and can't find it in your menus or it is acting strangely, you can always type avidemux and see if the program runs and if not, what are the errors (and post the error message here).

then again, linux is not for everyone. and neither is windows or any other OS.

---

### Post by wasteoftime on 2007-02-01
I'm just frustrated i really want linux but i keep hitting brick walls i need an idiots guide to understand the idiots guide.

This is the secong time i've installed ubuntu as the first time i managed to lock myself out of it setting up me, the only user, with minor privileges then found out that you can't login a root from gui login screen and couldn't figure out how to start desktop from that cli. 

It would have been nice to know this before hand it would have saved time. Having said that it installs 100% faster than xp which was nice!:D

also i'm a paranoid windows user (and that paranoia is well founded) do i need security and if i do what?

---

### Post by Extrapolation on 2007-02-01
[quote=wasteoftime]Is there an application that shows the filesystem in tree form? as i would find this helpful.[/quote]In a Nautilus (file browser) window, get the drop-down menu for "View" and switch the check box at the very bottom from "Icons" to "List."  Close and re-open the window.

[quote=wasteoftime]How do you run applications that you have installed but can't find? (i've installed them from the add and remove program[/quote]
Just [Install the Debian Menu]("http://cutlersoftware.com/ubuntuinstall/#where_did_it_go").

---

### Post by wasteoftime on 2007-02-01
Thanks for the help!!!

To be honest i didn't think that it would be as simple as just typing the program i thought it would have to be some arcane language that made no sense like windows cli. 

Oh.. one more thing the fan on my laptop is on continuously in ubuntu but not in windows is there something i could do?

Ill definitely be getting the debian menu!

---

### Post by Brunellus on 2007-02-01
> **wasteoftime said:**
> Thanks for the help!!!

To be honest i didn't think that it would be as simple as just typing the program i thought it would have to be some arcane language that made no sense like windows cli. 

Oh.. one more thing the fan on my laptop is on continuously in ubuntu but not in windows is there something i could do?

Ill definitely be getting the debian menu!
post a separate thread about the hardware issue, preferrably in the laptop forum.  I suspect it's something very peculiar to your processor/motherboard and how it works with acpi.  

For menu editing in GNOME, use the Alacarte menu editor--accessible in the gnome programs menu (can't remember where, exactly)

---

