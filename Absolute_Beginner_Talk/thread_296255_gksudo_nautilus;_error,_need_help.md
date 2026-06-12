---
title: "gksudo nautilus; error, need help"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by Oki on 2006-11-09
What am I doing wrong?

I want to move some files from the Desktop to usr/share/pixmaps with Nautilus and type gksudo nautilus in the terminal, and get;

(nautilus:16196): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
thomas@thomas-desktop:~$ /home/thomas/Desktop/Ikoner/nvidia.png.tar.gz
bash: /home/thomas/Desktop/Ikoner/nvidia.png.tar.gz: Permission denied
thomas@thomas-desktop:~$

Then the Desktop is empty in Nautilus witch starts...?

Thanks for your help

---

### Post by taurus on 2006-11-09
You first need to unpack your "nvidia.png.tar.gz" before you move to /usr/share/pixmaps!  Open a terminal, Applications -> Accessories -> Terminal, and type

```

cd ~/Desktop/Ikoner/
tar xvzf nvidia.png.tar.gz

```
I assume you now have nvidia.png and want to move that to /usr/share/pixmaps...

```
sudo cp nvidia.png /usr/share/pixmaps
```

---

### Post by hotbrainz on 2006-11-09
Hi Oki...

Well, after u see all these error messages did you see that a window pops up with the filesystem. That is your files for you to manipulate as a root user. Happens in my system all the time. ;)

---

### Post by Oki on 2006-11-09
Hi -thank you for the quick respons! 

I am very new to all this but;
I typed gksudo nautilus cus I want to move som png files to the usr/share/pixmaos(the good way for an Windows user). The png files are on my Desktop, both packed and unpacked(as a png file). But when Nautilus opens there are nothing on the Desktop, not my files, folders, icons and so on. The error message don't say anything to me. Yes, I have a shortcut/icon on the Desktop for the command nvidia-settings, but I am not going to use that now. 

Edit; 
I used my brain for a second – off course, the Desktop that I see belongs to the “super user”, not to me(as just a user), so I need to go to the home directory to find “my” Desktop – where all the thing where as they should... So now the files are moved as I wanted. 

Ok, sorry for the posting – I should have understood this form the beginning! So the error is nothing to worried about, great. Thanks again, and sorry for my poor English.

---

