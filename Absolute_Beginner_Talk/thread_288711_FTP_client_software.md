---
title: "FTP client software"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by Tobywuk on 2006-10-30
Hey :)

simple question really, I need an FTP client for ubuntu so i can connect to my webserver. As im new to ubuntu and linux, i am unfamilier with all the program names :)

Thanks

---

### Post by Paul41 on 2006-10-30
I use gftp. Another option is the FireFTP extension for Firefox.

---

### Post by Tobywuk on 2006-10-30
tried 

```
sudo apt-get install gftp
```

said it couldent find package. can anyone help?

---

### Post by Paul41 on 2006-10-30
I don't remember the name of the package and I am at another computer right now. I originally found it by searching for "ftp" in synaptic. See if you can find it that way.

---

### Post by caravel on 2006-10-30
I used to use gftp a few years ago when administrating my old phpBB forums.  A good program.

I may be wrong but I think it's just a front end for the command line ftp client?

---

### Post by Tobywuk on 2006-10-30
well.. erm, found it in synaptic, downloaded it and all the files that were needed to run it, got the confirmation and so closed the dialog box... but i have no idea where it is or how to run it :/ 

lol please help :)

---

### Post by Paul41 on 2006-10-30
It is in Applications->Internet. I think that is right anyway, I have made a shortcut so I haven't gone to it that way in a while. If that doesn't work you can type gftp in the terminal and it will start.

If you need any help once you get it started let me know and I will see what I can do.

---

### Post by dmizer on 2006-10-30
? ...

you don't need to install squat.  just use nautilus.  kde's file manager will do the same.

places > connect to server > chose ftp with login > enter your settings > shezam instant ftp client.

---

### Post by Shay Stephens on 2006-10-30
I use nautilus and fireftp.  gftp irritates me too much.

What I like about nautilus is I can drag and drop files, use ctrl A, right click create folders, etc.  And my connection stays open too.

---

### Post by Tobywuk on 2006-10-30
oh yes, thankyou :) also i got Gftp to load in the terminal, but wasnt under applications>internet.

how do i create an icon on the desktop to launce gftp? and how do i put it on the applications menue?

thanks :)

---

### Post by dmizer on 2006-10-30
if you use nautilus as i described, it will create a folder on your desktop automatically.

---

### Post by Tobywuk on 2006-10-30
yeah it has.. 

but i just want to know, how to create launchers on the desktop or menue system for future refrence, incase in need to :)

---

### Post by caravel on 2006-10-30
You can right click the desktop and select new launcher.  Then just enter the path and select an icon.  If you don't know the path, then try 'whereis gftp' from the terminal.

@dmizer:  I never knew you could use konqueror or nautilus for ftp.  Useful to know thanks. :)

---

### Post by randyleepublic on 2006-10-31
> **dmizer said:**
> ? ...

you don't need to install squat.  just use nautilus.  kde's file manager will do the same.

places > connect to server > chose ftp with login > enter your settings > shezam instant ftp client.

I set this up just like I did filezilla on my old win install.  I was able to connect but read only.  Help!  I need to be able to upload too.  Not poss?

Thanks

---

### Post by Paul41 on 2006-10-31
> I set this up just like I did filezilla on my old win install. I was able to connect but read only. Help! I need to be able to upload too. Not poss?
I have not used Nautilus for ftp (but I am going to try now that I know you can) but it is probably just a permissions problem with the folder you are trying to move files to. Try opening nautilus from the terminal with sudo privileges.
```
gksudo nautilus
```

---

### Post by dannyboy79 on 2006-10-31
> **randyleepublic said:**
> I set this up just like I did filezilla on my old win install.  I was able to connect but read only.  Help!  I need to be able to upload too.  Not poss?

Thanks

well, are you using proftpd as your ftp server? if so, then you need to make sure that you have allowed the folder to be able to be written to as well as look at the permissions of the folder.

---

### Post by dmizer on 2006-10-31
> **Paul41 said:**
> Try opening nautilus from the terminal with sudo privileges.
```
gksudo nautilus
```
avoid doing that at all costs.  that'll expose your entire directory structure to root access over ftp.

nautilus does allow you upload and download to and from ftp, so if it's not working, it could be something like a port problem or pasv/active ... other things you might want to look into related to the ftp server connection style.

---

