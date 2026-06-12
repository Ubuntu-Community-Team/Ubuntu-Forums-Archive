---
title: "[SOLVED] realplayer launching problem"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by James Fitzpatrick on 2007-09-02
I've downloaded realplayer from the wiki instructions regarding installation using debian:
sudo apt-get install libstdc++5
wget -c [http://www.debian-multimedia.org/pool/main/r/realplay/realplayer_10.0.8-0.1_i386.deb](http://www.debian-multimedia.org/pool/main/r/realplay/realplayer_10.0.8-0.1_i386.deb)
sudo dpkg -i realplayer_10.0.8-0.1_i386.deb

Everything seems to have worked fine, and I have it in my applications menu and on my panel, but I can't launch it.  I've tried reinstalling it, but the problem remains.

I'll be grateful for any help I may get, but I have little experience with computer jargon, so so please treat me as being "challenged".

---

### Post by benerivo on 2007-09-02
Do you get any error messages when you open a terminal and type realplay?

I have it installed, but just did it from Synaptic, as it's in the Ubuntu repositories. You may be better off installing it this way if you can't fix the debian package you downloaded. You might need to activate the commercial repository. The way i did it was to go in to 'Add / Remove' from the menu, and search for Opera. If you try to install it, you activate the commercial repository. Then go in to Synaptic, and search for realplay.

---

### Post by mali2297 on 2007-09-02
Try to run it in a terminal. Type *realplay* and see if you get any error messages.

---

### Post by James Fitzpatrick on 2007-09-03
This is what I get:
bash: realplay: command not found
I'll try the commercial repositories.

---

### Post by nowshining on 2007-09-03
totem will play realplayer files you just need to download the codecs..

---

### Post by James Fitzpatrick on 2007-09-03
My mistake - I was on the wrong coputer.  This is the message I got: Segmentation fault (core dumped)

---

### Post by James Fitzpatrick on 2007-09-03
I just downloaded it from the commercial applications, but it still doesn't launch.  I'm getting the same message in the terminal: Segmentation fault (core dumped)

---

### Post by nowshining on 2007-09-03
i had segmentation fault before - now how did I fix it.. :/

---

### Post by nowshining on 2007-09-03
to test something, do this

sudo gedit

hit enter

enter ur password if need be does it give you an error..

---

### Post by mali2297 on 2007-09-03
> **James Fitzpatrick said:**
> My mistake - I was on the wrong coputer.  This is the message I got: Segmentation fault (core dumped)

Strange. :-k

Do you have the 32bit version of ubuntu installed (and not 64bit)?

Can you use other media players?

You can try to install the *.bin* file from the official site. See here:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_RealPlayer_10_Multimedia_Player_.28RealPlayer.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_RealPlayer_10_Multimedia_Player_.28RealPlayer.29)

---

### Post by James Fitzpatrick on 2007-09-03
I just tried the sudo gedit, entered the password, and something about SCIM and an unsaved document came up.  I vaguely recall reading something about SCIM causing a problem for Realplayer.
I am using a 32 bit system on my laptop.  Realplayer won't install on my 64 bit desktop.  My other media players work fine - mplayer, rhythmbox, etc.

---

### Post by James Fitzpatrick on 2007-09-03
I'd try the bin file, but i'm not sure I understand what to do regarding "Add execute permissions to the installer and run it:"

---

### Post by nowshining on 2007-09-03
oh that's easy..

open up a terminal
gksudo nautilus

left side click file system
in the folders click home (do not click the top home button where next to computer it will take u to the root home which you do not want) then ur username and if the program is on your desktop the bin file - click the Desktop folder
after that right click the bin file
select properties
Permissions tab
Next to Execute there should be check box and the the words "Allow executing file as a program" check mark it click close now try it - if not log off and then back on for the changes to take effect..

---

### Post by oldos2er on 2007-09-03
>i'm not sure I understand what to do regarding "Add execute permissions to the installer >and run it:"

 Once you have it downloaded, right click on it, choose Properties, permissions, and check the box Allow executing file as program. Close properties, double-click the *.bin file, and choose Run in Terminal.

---

### Post by nowshining on 2007-09-03
#[**14**]("http://ubuntuforums.org/showpost.php?p=3305086&postcount=14")																					[oldos2er]("http://ubuntuforums.org/member.php?u=338320")
you helped learn a bit more myself. :)

---

### Post by James Fitzpatrick on 2007-09-04
I downloaded it, selected the permissions box, then double clicked on it, but nothing happened.

---

### Post by James Fitzpatrick on 2007-09-04
I tried moving the file to my home folder, double clicked on it, and an icon the was labeled xxextract.tmp momentarily appeared, then disappeared.

---

### Post by mali2297 on 2007-09-04
> **James Fitzpatrick said:**
> I'd try the bin file, but i'm not sure I understand what to do regarding "Add execute permissions to the installer and run it:"

That's what the commands do, run them in a terminal. 

First *cd* to the directory where you have downloaded the *.bin* file (if not the home directory), then type
```

chmod +x RealPlayer10GOLD.bin
sudo ./RealPlayer10GOLD.bin

```
You will then get a few questions, just choose the defaults (capital letter), and you're done.

---

### Post by James Fitzpatrick on 2007-09-04
Okay, I've done that, and now the terminal is saying: "Enter the complete path to the directory where you want
RealPlayer to be installed.  You must specify the full
pathname of the directory and have write privileges to
the chosen directory."

What do I type in next?  The bin file is currently in my home folder.

---

### Post by James Fitzpatrick on 2007-09-04
I think I'm starting to understand.  I've reached the point where the terminal is saying, "Copying RealPlayer files...configure system-wide symbolic links? [Y/n]: ....Y.
enter the prefix for symbolic links [/usr]: .........................."

What's next?

---

### Post by James Fitzpatrick on 2007-09-04
I see, I just type in what it prompts.  It seems to have installed, but it still doesn't launch.  Obviously, there's something in the system which prevents launching.  Any ideas from that angle?

---

### Post by mali2297 on 2007-09-04
> **James Fitzpatrick said:**
> I just tried the sudo gedit, entered the password, and something about SCIM and an unsaved document came up.  I vaguely recall reading something about SCIM causing a problem for Realplayer.

Perhaps this post holds the key:
[http://ubuntuforums.org/showthread.php?t=450110](http://ubuntuforums.org/showthread.php?t=450110)

Some additional help: 

You can find the *realplay* file with
```

whereis realplay

```
To open the file in gedit, type
```

gksudo gedit PATH/realplay

```
where PATH is taken from the output of *whereis*.

---

### Post by James Fitzpatrick on 2007-09-04
It doesn't seem to help. When I opened the file, there was nothing in it. When I typed in the command,  "export GTK_IM_MODULE=xim", I came up with this message in the terminal:"** (gedit:15174): WARNING **: Hit unhandled case 1 (File not found) in gedit_unrecoverable_saving_error_message_area_new.  I couldn't save.

This seems hopeless.

---

### Post by mali2297 on 2007-09-04
> **James Fitzpatrick said:**
> It doesn't seem to help. When I opened the file, there was nothing in it. When I typed in the command,  "export GTK_IM_MODULE=xim", I came up with this message in the terminal:"** (gedit:15174): WARNING **: Hit unhandled case 1 (File not found) in gedit_unrecoverable_saving_error_message_area_new.  I couldn't save.

This seems hopeless.

It probably means that you didn't open the correct file, instead you created a new one.  Show the output of
```

whereis realplay

```

---

### Post by James Fitzpatrick on 2007-09-04
realplay: /usr/bin/realplay /usr/lib/realplay /usr/X11R6/bin/realplay /usr/bin/X11/realplay /usr/share/realplay

---

### Post by mali2297 on 2007-09-04
Type
```

gksudo gedit /usr/bin/realplay

```
and you should be able view a content that starts similar to this:
> 
#!/bin/sh

# If you don't have readlink, fill in the path to hxplay.bin here.
HELIX_LIBS=/opt/RealPlayer ; export HELIX_LIBS

# To install this script, create a symlink to it from somewhere in your
# path.  Do *not* move the script out of the HelixPlayer directory, since
# it relies on the true location of hxplay to derive the location of the
# HelixPlayer directory


Add *export GTK_IM_MODULE=xim* somewhere below *#!/bin/sh*. Then save and quit.

---

### Post by James Fitzpatrick on 2007-09-04
Thank you !  It's launching now.  May the Vanir be with you!

---

