---
title: "problem with copy &amp; paste functions"
date: 2006-06-26
forum: Absolute Beginner Talk
---

### Post by wpshooter on 2006-06-26
When I am attemting to make a desktop shortcut/launcher for a web address link and I am wanting to use the copy and paste function to bring the web address into the launcher setup diagonal link field, the paste function is **NOT** available to me unless I leave the web site from which I am doing the copy function from either **open** or **minimized**, i.e. if I close the website/browser after doing the copy function and then attempt to paste the link, the paste function is **NOT** available.

Am I missing something here ?  I just tried this in M/S windows and it works fine.  Yes, I know this is not M/S but should this not work the same or similar in Ubuntu/Linux ?

Thanks.

---

### Post by scxtt on 2006-06-26
i can highlight the address of this thread from a firefox address bar, right click, copy -- go to my desktop, click "create launcher", right click and paste it where ever i want ...

seems normal to me ...

---

### Post by wpshooter on 2006-06-26
[QUOTE=scxtt]i can highlight the address of this thread from a firefox address bar, right click, copy -- go to my desktop, click "create launcher", right click and paste it where ever i want ...

seems normal to me ...[/QUOTE]

When you are doing that, are you leaving the website/browser OPEN that you did the copy from or are you closing it first.  The problem does not occur as long as I leave the website/browers open, the problem only occurs if I copy and then close the website/browers before trying to paste.  

Is this what you tried ?

Thanks.

---

### Post by mcduck on 2006-06-26
That's just the way it works in Linux. There is no 'clipboard' to store the stuff you copy&paste, it's copied directly. So you need to keep the source where you're copying open.

If you want, you could install the Gnome Clipboard Daemon to make copy&paste work even if you close the program you're copying from.

By the way, if you're using Gnome and Firefox, you can create those shortcuts simply by draggin&dropping the tab from Firefox to your desktop ;)

And have you tried unix-style copy&paste? Just 'paint' to select the text you want to copy, and paste it with a middle click.. This also often works in apps that don't give you any visible copy&paste option..

---

### Post by richbarna on 2006-06-26
You can also copy Ctrl+C and then Paste Ctrl+V

KDE has a clipboard (Klipper) that will save any amount of "copies" that you specify.

---

### Post by wpshooter on 2006-06-26
[QUOTE=mcduck]That's just the way it works in Linux. There is no 'clipboard' to store the stuff you copy&paste, it's copied directly. So you need to keep the source where you're copying open.

[/QUOTE]

That's sort of the conclusion I had come to.

YAAHO, I learned something new today !!!

Thanks for your reply.

P. S. - Is Gnome Clipboard Daemon in Synaptic or Add/Remove programs, I would look but I am at work right now and as you can guess, there are no Ubuntu machines here.

---

### Post by mcduck on 2006-06-27
[QUOTE=wpshooter]Is Gnome Clipboard Daemon in Synaptic or Add/Remove programs, I would look but I am at work right now and as you can guess, there are no Ubuntu machines here.[/QUOTE]For some reason I can't understand it's not in the repositories.

But it has'n got any dependencies you wouldn't have if you are running Gnome, and if you get the binary you don't actually need to 'install' it anywhere, just put it in your home (or where ever you want) and run it with './gnome-clipboard-daemon', or add it to your session to make it autostart when you log in to Gnome.

---

