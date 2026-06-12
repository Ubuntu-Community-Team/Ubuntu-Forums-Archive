---
title: "Gmail notifier startup"
date: 2006-03-26
forum: Absolute Beginner Talk
---

### Post by _simon_ on 2006-03-26
If I want to add the Gmail notifier to startup in session what is it called?

For future reference how do I find out names of programs like this? I tried searching the file system for gmail but only found the icon.

Edit: I found it by adding the launcher to the desktop and then looking in the properties. I assume there is another way to check rather than this way?

btw it's gmail-notify

---

### Post by Enter on 2006-03-26
why not start it and when your exiting just click save this sesion?

---

### Post by arnieboy on 2006-03-26
[QUOTE=_simon_]If I want to add the Gmail notifier to startup in session what is it called?

For future reference how do I find out names of programs like this? I tried searching the file system for gmail but only found the icon.[/QUOTE]
the app is "gmail-notify"
this is how I do it.
open **synaptic**--> search for the package by using a partial string (which I make a calculated guess on)
find the package, **right click** --> hit **properties**--> **installed files**.
There I look for executables installed in **/usr/bin** because thats where executables for all packages go by default.
The name of the executable in **/usr/bin** is the name that you need to use when running the app from terminal or anywhere (even when adding to startup programs)

if the executable is not in the user PATH (**/usr/bin** always is by default), then you might need to specify the whole path.

---

### Post by _simon_ on 2006-03-26
so really, adding a launcher to the desktop and copying the command from there may be quicker?

Thanks for the replies guys.

---

### Post by jrib on 2006-03-26
quickest way is probably ```
 dpkg -L packagename | grep bin 
``` which amounts to what arnieboy suggested in synaptic

Another way would be to open system tools > applications menu editor, and check the properties of the shortcut

---

### Post by arnieboy on 2006-03-26
[QUOTE=_jason]quickest way is probably ```
 dpkg -L packagename | grep bin 
``` which amounts to what arnieboy suggested in synaptic

Another way would be to open system tools > applications menu editor, and check the properties of the shortcut[/QUOTE]
the above command is indeed the quickest if you know what the package name is which is not always the case.

---

### Post by arnieboy on 2006-03-26
[QUOTE=_simon_]so really, adding a launcher to the desktop and copying the command from there may be quicker?

Thanks for the replies guys.[/QUOTE]
you can create a deskop launcher, a panel launcher or even a menu launcher by using smeg or even by doing it manually which I do.

---

### Post by MakubeX on 2006-03-27
Right now, I'm having problem with that Gmail notify applet.. I've been using it for months already but when I got home, it says "Connection failed" even though I can log-in to the web service. I rechecked by reinputting the username and password then it says that my log-in is invalid even though when I use it via a web browser, it works! 

I wonder what happened to my gmail-notify applet..

---

### Post by Perfect Storm on 2006-03-27
[QUOTE=MakubeX]Right now, I'm having problem with that Gmail notify applet.. I've been using it for months already but when I got home, it says "Connection failed" even though I can log-in to the web service. I rechecked by reinputting the username and password then it says that my log-in is invalid even though when I use it via a web browser, it works! 

I wonder what happened to my gmail-notify applet..[/QUOTE]

Same problem here, it worked nice yesterday, might be a gmail problem.

---

### Post by NoNo_231 on 2006-04-10
Try to login to your gmail account via web browser. Sometimes it asks for a verification (that strange aplhanumeric). I had three times this problem and all three times it asked me for this. I think it does it if you have logged in from different computers, never logged in before. Last time I had this problem I had visited gmail via mobile.

edit: sorry didn't see that you had already used web browser.

---

### Post by chammi on 2006-04-23
Another way to find the command (especially if you have an *idea* of what it might be but aren't sure exactly) is to open the System Monitor (Applications>System Tools> System Monitor) the next time your program is running and look for it there (first sorting the processes by name is helpful)

---

