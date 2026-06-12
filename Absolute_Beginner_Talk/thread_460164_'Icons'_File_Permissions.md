---
title: "'Icons' File Permissions"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by Blowfly on 2007-05-31
Hey everybody,

I've spent the last 2 weeks installing Kubuntu and of course alternating between triumph and frustration as the learning curve levels out (hopefully).

Anyway, I was trying to install some mouse cursor/themes and the 'Icons' file would not let me write/copy to it, so I went into Konsole and changed the permissions.

Of course, at that point the damage was done and I'm sure I could find out how to fix it eventually, but it would probably take a few days to a few weeks (yikes).

Can anyone give me a quick fix on this?

Thanks in advance...:)

---

### Post by kernel tom on 2007-05-31
what exactly is ur problem? changing permissions shouldn't have damaged anything.  but here's how u would move cursor/themes without having to change anything.  

If you know the directory just do the following, after downloading the theme/cursor to ur desktop

sudo mv Desktop/filename /path_of_your_theme_cursor_or_icon_folder

that will cut and paste it into the correct folder

---

### Post by Blowfly on 2007-05-31
The icons are not showing up on the desktop.

My problem may possibly be the NTFS drive. I'm using a dual boot setup with WinXP on another partition.

I'm totally noob, so I'm gonna be in a state of confusion until I learn a little more...

---

### Post by kernel tom on 2007-05-31
what icons are not appearing on the desktop?

depending on how you have it set up there may be no icons on ur desktop, or are there "blank" icons, meaning they have what looks like a sheet of paper for an icon and it's not a text document... 

It is possible that when u changed the permissions Windows XP corrupted some of the information.

try changing the permissions back to whatever else is in that directory and rebooting

---

### Post by Blowfly on 2007-05-31
Hey Tom,

Well I'm in Kubuntu now w/ Firefox, and just tried enabling NTFS writing, but that wasn't it.

Here's the thing:

Path to file is /usr/share/icons

All files within /usr are fine *except* 'icons' which spits out [COLOR="Red"]Access Denied[/COLOR].

So I goofed and set the permissions to that because, hey, I don't know what I'm doing.

So I need some code to enter from the terminal to set the file permissions the way they should be and I'm pretty sure that will fix it.

I'm guessing something along the lines of:

sudo chmod *x-x-x-x* /usr/share/icons

It's the *x*'s I'm not sure about, and my UNIX (is that word allowed here? ;) ) command line book has been lost for years...

---

### Post by kernel tom on 2007-05-31
gotcha

here's the scoop on that

cd into your /usr/share folder
then type "ls -l"

this will bring up all of the folders and files in that directory and show you their permissions

then i believe what you would like to do is the following

sudo chmod -R 755 icons

this will recursively change the permissions of icons and every file and folder inside it to this...
drwxr-xr-x, which should be like all the other files in your directory

---

### Post by Blowfly on 2007-05-31
Thanks Tom.

[COLOR="Blue"]cd /usr/share[/COLOR]

then
[COLOR="Blue"]
sudo chmod a=rwx icons[/COLOR]

Did the trick. But dang these icons are oo-ge-lee....now I'll be able to do something about *that*...

Thanks very much for your quick replies. You guys are fast!

Anyway, I have link to an online command glossary, *LINUX For Total Idiots* which, I believe, was written especially for ME...so I don't have to keep botherin' y'all with basic s*%t... :D

---

### Post by kernel tom on 2007-05-31
yea not a bad idea... however

I would recomend doing the following instead of ur a=rwx to 
sudo chmod -R 755 icons

just to be on the safe side

then when u download a theme to your desktop use

sudo mv Desktop/filename /usr/share/icons/

this way only you can make changes to the directory

---

### Post by Blowfly on 2007-05-31
^^^^ Thanks, doing it now.

---

