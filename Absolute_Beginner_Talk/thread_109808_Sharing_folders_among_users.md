---
title: "Sharing folders among users"
date: 2005-12-29
forum: Absolute Beginner Talk
---

### Post by wagdog on 2005-12-29
I've created several users on my Breezy system and now I want to create a common shared folder where everyone can have access to it.  I understand permissions but my problem is I don't know where to put it.  I don't want to put it in my /home folder, I'd like it to be in a 'neutral' (non-user specific) location but I get lost/confused once I leave /home.  (What are all those odd folders with the funny names?).  Is there a proper place for me to create this folder?  Thanks!

---

### Post by KingBahamut on 2005-12-29
You could create a folder 

mkdir /stuff 

chmod 755 /stuff -R

and then users could access it via the filesystem.

---

### Post by psusi on 2005-12-29
You can put it wherever you want really, but I don't see anything wrong with /home/share.

---

### Post by wagdog on 2005-12-29
Thanks for the replies!

Silly me, I didn't realize all users share a /home folder so I was going to make a /home/share as psusi said but now I get a permission denied message.  Evidently /home is owned by root and I can't change anything.  My profile has admin permissions but still I can't create the folder.  How do I get around this pickle?
Thanks again!

---

### Post by wsanders on 2005-12-29
In order to use admin (root) functions, use sudo. so, to make a new folder in home, type:
```
sudo mkdir /home/share
```
You'll need to type your password, and then you can execute root commands.

---

### Post by wagdog on 2005-12-29
Ok, I'm slowly catching on.  I put sudo in front of the commands and I was able to create the folder but now I can only view the folder, not add any objects (even though I did "chmod 755 /home/share -R").  I know how to modify permissions through Nautilus but not this command line stuff so please educate me!

---

### Post by Mustard on 2005-12-29
did you put sudo in front of the chmod command as well?

---

### Post by wagdog on 2005-12-29
Mustard: Yes I did and it seemed to run ok (no errors).

I have now managed to get the permissions sorted out by kind of cheating.  I did "sudo nautilus" which took me into nautilus as root at which point I went into  permissions and granted access.  Seems to have worked.

Now I need to figure out how to get a "shortcut" (sorry, don't know the Linux term) on everyone's desktop and then I'll be done.

---

### Post by Sutekh on 2005-12-30
[QUOTE=wagdog]Now I need to figure out how to get a "shortcut" (sorry, don't know the Linux term) on everyone's desktop and then I'll be done.[/QUOTE]

What you want is a 'symbolic link'.  You can create these using the terminal, from the Desktop folder.

The red text is the link command, with a '-s' to make it a symbolic (or soft) link meaning that you can delete the link without touching the files.  The blue text is the path of the folder that contains the files.  The green text is the desired name of the link.
```
[COLOR="Red"]ln -s[/COLOR] [COLOR="Navy"]/Target-Folder[/COLOR] [COLOR="SeaGreen"]Link-Name[/COLOR]
```

If you prefer not to use the terminal you can right-click on the desktop and 'Create Launcher'.    Choose the 'type' to be a 'Link" and then in 'URL' add the path to the files.  Fill out the other entries as you want.  Personally I find the terminal way easier.

---

### Post by wagdog on 2005-12-30
Thanks Sutekh, that worked perfectly!

---

### Post by daibak on 2006-01-01
[QUOTE=Sutekh]What you want is a 'symbolic link'.  You can create these using the terminal, from the Desktop folder.
...
If you prefer not to use the terminal you can right-click on the desktop and 'Create Launcher'.    Choose the 'type' to be a 'Link" and then in 'URL' add the path to the files.  Fill out the other entries as you want.  Personally I find the terminal way easier.[/QUOTE]

Please tell me how to delete a symbolic link.
Created this first one yesterday in terminal to see how it worked (seemed to more or less with a video neroLINUX image .nrg mounted on a virtual drive that I could watch in Totem/Mplayer), but then had to log-out in order to clear the hard drive cache of 4.3GB I needed in my tiny Linux notebook partition.
I built this symlink with this
```
username@ubuntu:~$ sudo ln -s /dev/loop0 /dev/cdrom0
```
The umount did not release the 4.3GB virtual drive space back to Breezy, only the log-out did. I've got a lot to learn; I'll try your 'Create Launcher' tip.

---

### Post by kaamos on 2006-01-01
Try
```
sudo rm -i /dev/cdrom0
```

---

### Post by daibak on 2006-01-01
Gee, kaamos, that was as quick as pressing a button.
Thanks, and a happy New Year to you!
(it's not yet midnight 20060101 here)

---

### Post by daibak on 2006-01-01
[QUOTE=kaamos]Try
```
sudo rm -i /dev/cdrom0
```[/QUOTE]
For my education, in which folder does Breezy save symlinks?

TIA.

---

