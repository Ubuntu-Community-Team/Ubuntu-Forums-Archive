---
title: "Quick Customization (MacBook Pro) Questions For New User"
date: 2008-05-20
forum: Apple Hardware Users
---

### Post by boarder4021 on 2008-05-20
Hi and thank you for clicking on my thread (I know I actually appreciate it). I have a couple of questions that I hope could be answered or have been answered in the past and could be linked to me. [**This is all regarding a Live Install, but I suspect little will change with a actual hard install**.

First off, I would love to turn the Trackpad off when I have a mouse plugged in. OS X gives that option in system preferences, but I don't know how to do it in Ubuntu. I'm a new user but love to fiddle around with my computer and thought of trying out Ubuntu. 

Also, my brightness and keyboard function keys do not work. They do not dim the display or illuminate the keyboard when I press them, although the icon comes up there is no increase/decrease in either option.

That's all I have for now. Thank you for taking the time to read my requests!\\:D/

---

### Post by cyberdork33 on 2008-05-20
First one is not straightforward:
[http://linuxtidbits.wordpress.com/2007/10/27/switch-automatically-mouse-and-touchpad/](http://linuxtidbits.wordpress.com/2007/10/27/switch-automatically-mouse-and-touchpad/)

For your extra functions to work you have to install pommed.

---

### Post by russo.mic on 2008-05-21
You could just setup a script to do this.  the name of the program is synclient, and the parameter would be TouchpadOff=1.

So, from the command line, if you were to type 
synclient TouchpadOff=1, it would turn the touchpad off.  You could have the bluetooth daemon call on a script that just executed this command upon connection.  you could write another script and turn it off.  

I'm going to figure out what file should call this script, and repost after I do.  

Pommed works great for me!

Russo

---

