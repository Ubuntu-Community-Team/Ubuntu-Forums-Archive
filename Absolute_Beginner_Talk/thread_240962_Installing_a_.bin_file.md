---
title: "Installing a .bin file?"
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by Matt827 on 2006-08-21
Trying to get a P2P File sharing program installed. It's installed but currently not working. It says i need an updated version of sun java. So i downloaded the file and it's a .bin 

It's downloaded onto my desktop but when i double click it opens in Gedit and gives me some error. So i assume this isn't the program i want to execute the .bin file through.

So is there a terminal code i use to run it? I tried 

chmod a+x nameofbin.bin 

but it's telling me the file doesn't exist...(I copy /pasted the name of the file from my desktop so this isn't the case)

---

### Post by ironfistchamp on 2006-08-21
May sound stupid but have you changed directory to your Desktop. I have done it many times and thought "it does exist I can see it!"

when you have chmodded it successfully you just need to run ./nameofbin when in the directory it is in.

Hope this helps

Ironfistchamp

---

### Post by Matt827 on 2006-08-21
i dont think i have. Haha, i'm so new to this i wouldn't even know how to go about doing that!

---

### Post by TFX360 on 2006-08-21
> **ironfistchamp said:**
> May sound stupid but have you changed directory to your Desktop. I have done it many times and thought "it does exist I can see it!"

when you have chmodded it successfully you just need to run ./nameofbin when in the directory it is in.

Hope this helps

Ironfistchamp
Dear Matt,


Try this link:

[http://blog.agileware.net/index.php/archives/2005/09/30/how-to-install-java-on-ubuntu-linux/]("http://blog.agileware.net/index.php/archives/2005/09/30/how-to-install-java-on-ubuntu-linux/")


Kind regards,


TFX

---

### Post by Zerocool10482 on 2006-08-21
Right click the .bin file and then click the execute and write check box. Then click close. Click the .bin and say run in terminal.

It should work:p

---

### Post by win_zik on 2006-08-21
First off, I'm pretty sure you can get a relatively new version of Sun Java from the repositories, which would be better than installing an external file. Look around the forums or the wiki.

About installing the bin file, you'll first have to make the file executable. That's what you tried to do with chmod. I don't know why you didn't find the file, but I suspect it's in a different directory. You can use cd to navigate to an other directory.

Also, you can use the tab key for autocompletion, which makes using the terminal so much faster. For example type chmod +X nameoff tab and it will be autocompleted to name of file.

After the file is executable you can simply run it in the directory it is in with ./nameoffile.bin

Hope this helps! :-D

---

### Post by Matt827 on 2006-08-21
i have tried dragging and dropping the file into the terminal window so it gets the correct directory and when i do this it actually tells me my permission is denied. 

On a side note... i can't edit any file locations while logged on..It always tells me i do not have write permission. Which is odd considering i'm the only user and this computer. 

This stuff is too confusing. I'm starting to miss my unstable windows...

---

### Post by ironfistchamp on 2006-08-21
Don't turn back it won't be long till you are thinking how you ever lived without Linux. Anyway the write permissions is probably because you are not root. You won't be even if you are the only user. If you are trying to write somewhere outide of you home directory you will have probs. If working in a terminal type sudo before the command.

Or you coulde type 

```

gksu nautilus 

```

to get a gui with root permissions.

Ironfistchamp

---

### Post by Matt827 on 2006-08-21
tried that code iron...

i got this

"(nautilus:7676): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
"

---

### Post by bulldog on 2006-08-21
You can also run Automatix and you have the choice over several P2P apps.
You can install java in the same time and a lot more.

Take a look.

[http://ubuntuforums.org/showthread.php?t=80295](http://ubuntuforums.org/showthread.php?t=80295)

It's much more easyer.

Running gksu nautilus:

ALT-F2
gksu nautilus
password

And your done.

A little advice though,when you go and alter some files with nautilus,be sure to make a backup first.
Things can go badly wrong when you don't!

---

### Post by ironfistchamp on 2006-08-21
Bulldog good one with the backup. You can really mess things up as root.

Matt I get the same message as you but it doesn't seem to matter as nautilus opens up fine. Does it open when you do that. If it does ignore the message.

---

### Post by Matt827 on 2006-08-21
yep it opens up :-D

---

### Post by bulldog on 2006-08-21
The warning you get when you do gksu nautilus in konsole is nothing to be worried about.

There's a topic about using sudo and gksudo to open applications with a GUI.
When using sudo you could mess up your .ICEauthority and woodn't be able to log in your Ubuntu.

To prefent this to happen it's advised to use gksudo for graphical applications.

The warning you get is a little annoyance but is harmless and is considered a low priority bug.

---

### Post by TFX360 on 2006-08-21
Maybe read up on RootSudo :D

[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

Good luck


Kind regards,


TFX

---

