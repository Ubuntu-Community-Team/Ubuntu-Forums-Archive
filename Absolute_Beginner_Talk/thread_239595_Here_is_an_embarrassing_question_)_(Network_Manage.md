---
title: "Here is an embarrassing question :) (Network Manager)"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by jsully1 on 2006-08-19
I accidentally right clicked and selected remove from Panel on the network manager.  How do I get it back??

---

### Post by bulldog on 2006-08-19
Just right click your panel and choose add to panel.
Make your choice and close the candy-box.

It's as easy as that :grin:

---

### Post by jsully1 on 2006-08-19
Right, I had figured *that* part out :)
Where do I find network manager though?

---

### Post by GeekSpeek'r on 2006-08-19
under:
 --Applications
     -- Internet

---

### Post by jsully1 on 2006-08-19
It's not there.  If I go to add/remove however it shows up under Internet there.

---

### Post by bulldog on 2006-08-19
Under Applications --> Administration I think.

---

### Post by jsully1 on 2006-08-19
No love there either, sorry.  Should I just uninstall, reinstall?

---

### Post by GeekSpeek'r on 2006-08-19
yeah, might be the easiest / quickest method -- re-installing that is

---

### Post by bulldog on 2006-08-19
If you can't find it,that's the best thing to do.
But removing it from your panel isn't uninstalling anything though.

If you had it before it should be there,try your console and type in the name  off the app and see if it comes up.

---

### Post by jsully1 on 2006-08-19
Reinstalling didn't bring it back :(

---

### Post by bulldog on 2006-08-19
I'm sorry but I just installed it and can't find it either.

How did you get it the first time on your panel?

What does it do,cause I didn't need it so far.

---

### Post by jsully1 on 2006-08-19
[http://www.ces.clemson.edu/linux/nm.shtml#nm-apps](http://www.ces.clemson.edu/linux/nm.shtml#nm-apps)
It's pretty sweet...

I can't even figure out how to bring up the manager - forget the little app.

---

### Post by orb9220 on 2006-08-19
Goto system>prefs>sessions
startup tab add 
nm-applet --sm-disable
logoff and logon

---

### Post by jsully1 on 2006-08-19
It's already there, and running.  I just can't figure out how to access it.

---

### Post by bulldog on 2006-08-19
I have the icon in my panel.
Not configured but it's there!

You can try in console:

sudo aptitude install network-manager

That's the way I did it.
Then log out and again in and the icon appears in your panel, not in your applications menu.

---

### Post by jsully1 on 2006-08-19
Didn't change anything unfortunately.
Why is this so insanely difficult... nm-applet is listed under the Current Session.

---

### Post by bulldog on 2006-08-19
You can make a starter by right click on your desktop.
Only you have to know how to start it,you could try
nm -applet --sm-disable
to see if your starter takes of.

Did you log out and log in already?

---

### Post by jsully1 on 2006-08-22
Hi all,

I figured I would followup with some more info - I reinstalled, and it turns out I didn't nuke the network manager - I closed the Notification Area, which houses the network manager :)
Still, it would be nice if network manager showed up in Applications like it should

Thanks for all of the help!

---

