---
title: "gdesklets: gnome starter bar"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by shadowboxer_k on 2007-02-25
hello,

i have a a couple of silly newb questions, hope anyone can help.

i installed gdesklets and i want to use the gnome starter bar. my problem is, i don't know how to add a new starter to the bar. i click "new starter" and when the applet pops up, it tells me i need to type in a command. i have no idea what to type. can anyone please help?

also, i read that most gdesklet weather widgets don't work because yahoo changed something. is there a fixed weather widget that works with yahoo's new settings?

thanks for the patience.

---

### Post by Ferri on 2007-02-25
If the application you want to launch is in your path, it should work just entering the executable's name (firefox, oowriter...).
If it's not there (usually something you have installed on your own) you'll hve to enter the full path (/home/yourname/foldername/appname, for example).
I don't know about a fix for the weather desklets.

---

### Post by shadowboxer_k on 2007-02-25
thanks, Ferri.

my problem is that i still don't know what folder my applications are in, so i get stuck after typing /home/myname/...

---

### Post by Ferri on 2007-02-25
Most executables are in /usr/bin usr/local/bin or /bin, or at least have a shortcut in this folders.
If they are there, the name of the executable, which most likely is the name of the program should be enough.
The applications you have installed using the default install process (apt or aptitude) should be in these locations.

---

### Post by shadowboxer_k on 2007-02-25
thank you! this seems to work.

---

### Post by gloscherrybomb on 2007-03-07
What about if you want to open a folder, i.e. photos?

---

### Post by mgmiller on 2007-03-07
> What about if you want to open a folder, i.e. photos?

Just browse to the folder using the regular old nautilus file browser.  Once the folder you want is open, at the top of the window click on Bookmarks and then add bookmark.  A shortcut has been created and is now in your Places drop down in the top panel.  I actually have one in mine to my pictures folder, by the way.

---

### Post by gloscherrybomb on 2007-03-07
I've done this but I'm still unable to launch a folder from the starterbar. I think you have got a bit confused.... I need to know the command to launch a folder from the gdesklets dock.

---

### Post by Naikei on 2007-03-11
gloscherrybomb -

Assuming you are running the default Ubuntu install with the Nautilus file manager:

In the launcher properties use the command "nautilus /home/yourname/pictures" (or whatever the folder you want to navigate to is) without the speech marks. This works for me.

Naikei
x

---

### Post by lhardyl on 2008-02-04
Sorry to bring this post back from the dead but has anyone had any luck adding folders to the launcher?

when i do the "/home/lhardyl/Documents" in the command line.... nothing happens

It creates an icon of a springy thing and when i click it, no folder opens

*pulls out hair*

---

### Post by gloscherrybomb on 2008-02-04
Its: 'nautilus' followed by the destination e.g.

nautilus /home/jimmy/desktop/

---

