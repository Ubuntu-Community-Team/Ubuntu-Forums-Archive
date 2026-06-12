---
title: "Launchers and Apps"
date: 2006-01-27
forum: Absolute Beginner Talk
---

### Post by qwazert on 2006-01-27
OK, so I finally have Aegis installed!

I can find it by searching the harddrive....living in usr/share/gnome-appsinstall/
and if I click the icon, it runs as it should!

If I try to create a LAUNCHER on the desktop, it tells me that I don't have permission to use this app. Indeed, when I check the properties of this application, it would appear that only ROOT can access! What was the root password again? I have a "regular" install, btw.
What's worse is that it "should" appear in my drop-down menu of Apps, and it does; in the Application Menu Editor, but does _NOT_ appear in the menu.

I finally got my Canon IP1500 working, but this whole UBUNTU/LINUX experiment is really starting to test my patience....even the smallest task seems to require so much effort and input!

---

### Post by frodon on 2006-01-27
[QUOTE=qwazert]What was the root password again? I have a "regular" install, btw.[/QUOTE]After a fresh install your root password should be your user password, you should read that : 
[https://wiki.ubuntu.com/RootSudo?action=show&redirect=UsingSudo](https://wiki.ubuntu.com/RootSudo?action=show&redirect=UsingSudo)

---

### Post by qwazert on 2006-01-27
Allright, I read it and I think I understand.

The question remains, what good is an app if I can't use it? I can see it sitting there in the directory and it allows me to run it by double-clicking on it, but I cannot make any sort of link/shortcut or launcher that works.

---

### Post by Jimmey on 2006-01-27
Change the file permissions of the binary. There's a shorter way to do this, but the long way works just as well.

Open the terminal, and type 
> whereis aegis-virus-scanner
Then, find the path where the binary file is located, and type
> sudo nautilus /path/where/binary/is
Then, find the binary file, and right click on it, selecting the tab labelled "permissions." Then, change the owner to yourself, and change the read, write and execute permissions.

Edit: 
I didn't read your post properly :P
If the above doesn't work, right click on the launcher, and not the binary, and do the same thing.
Hope that helps.

---

### Post by frodon on 2006-01-27
[QUOTE=qwazert]Allright, I read it and I think I understand.

The question remains, what good is an app if I can't use it? I can see it sitting there in the directory and it allows me to run it by double-clicking on it, but I cannot make any sort of link/shortcut or launcher that works.[/QUOTE]Generally you use root things in  terminal but if you really want a launcher it's possible. Right click on the desktop and select "create launcher", there is a field where you can specify a command to run with this launcher put in this field "gksudo path_of_the_apps" and select the icon you want for the launcher.
So when you will use it a window will ask you your password and then you will be able to use your apps as root.

---

### Post by qwazert on 2006-01-27
I'll try these suggestions and get back to you!  \\:D/

---

### Post by qwazert on 2006-01-27
Using the **WHEREIS** command, I was able to find 3 other locations where Aegis resided. I merely picked the appropriate executable and created a Launcher for THAT executable.

Works now, THANKS!

---

### Post by ras on 2006-01-28
I had the same initial problem.  What worked for me was "gksudo aegis-virus-scanner" in the launcher command line.  It then asked for password and worked fine.

---

### Post by Madpilot on 2006-01-28
[QUOTE=qwazert]Using the **WHEREIS** command, I was able to find 3 other locations where Aegis resided. I merely picked the appropriate executable and created a Launcher for THAT executable.

Works now, THANKS![/QUOTE]

Actually, you probably only found one executable, and two symlinks to it. But that's a technicality, if it works that's the main thing.

---

### Post by MakubeX on 2006-02-17
[[img]http://img6.picsplace.to/img6/14/thumbs/launcherprob.png[/img]](http://img6.picsplace.to/img.php?file=img6/14/launcherprob.png)

How about this one? I can only use the icon (.PNG file) when I copy it into /usr/share/pixmaps but not from its source directory. User has all necessary permissions on the folder but it is not select-able. How come?

I was supposed to create a launcher for netbeans.

---

