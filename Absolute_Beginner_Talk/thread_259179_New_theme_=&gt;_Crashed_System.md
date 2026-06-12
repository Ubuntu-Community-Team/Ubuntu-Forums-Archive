---
title: "New theme =&gt; Crashed System"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by RudolfMDLT on 2006-09-17
Hi there,

I installed a knew theme recently for Gnome, new Icons, window manager, cursers ect from gnome-looks.org. I've been trying to fix the problem for the past couble(8) days but I just can't get the job done.


After booting my machine up, gnome would start loading, I can see all the new icons and the theme that i loaded, gaim opens and starts logging in to ICQ, and then the screen goes black and I'm back at the log in screen. Every time I log in I get this. Using some of the other accounts on my computer I can log in though.

Right now I'm stuck useing windows! Please help me fix this! I spent the past 4 months getting used to and really enjoying Ubuntnu and only using Windows occasionally! I've been stuck in XP for over a week now! Honestly, it's annoying!

Thanks for any help I get!

---

### Post by sktx on 2006-09-17
You could try creating a new user in the console and using them to log into GNOME, then going through and trying all the themes and icons that you downloaded, to see which is killing your GNOME session... 

hit CTRL-ALT-F1 to swich to console mode, and log in with your regular user name and password...

at the shell prompt, type:
```

sudo adduser clevername admin

```

Replace **clevername** with whatever you want the user to be called. You'll be prompted for a little information, you don't have to fill it all in..  I usually just enter a password, enter the "Real Name" field, and skip the rest.

*Note:* The "admin" part adds the user to the admin group so he can use sudo.  You don't have to do this if you don't want.

---

### Post by RudolfMDLT on 2006-09-18
Thnx, But once I found out which theme crashes the system, how do I remove it. I have found a config file that has paths pionting to what looks like cursers and theme's and stuff. I tried renameing it in the hope that gnome won't be able to read the file and just load system defaults but to no avail, gnome still loads the theme and then crashes...

---

### Post by bulldog on 2006-09-18
If you know the name of the crash theme you can remove it in your console.

Go to the /.themes directory in your home folder and 

sudo rm -r -i 'name of the theme'

---

### Post by RudolfMDLT on 2006-09-20
OOOooooo! Thnx! Stupid me:tongue: ! I thought I had to take the theme out of a config file! 

Sorry I'm only replying now, Busy writing exams... Thanks for the help!

---

