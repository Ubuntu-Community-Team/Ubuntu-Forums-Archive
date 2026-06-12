---
title: "New to Linux and trying to get a crash course"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by prmmel on 2007-06-15
Always been with windows and I downloaded Ubuntu for a stab.
Slick interface, instant connections, quicker than widows...Free software!!!

Ok, now I want to ultimately install Myth TV on a PC I just built.  Monitor is a 37" 1080P LCD.  Ubuntu defaults to a max of 1280x1024...he motherboard has onboard video (MSI, ATI 1250X), but will support 1080P.  So, i fugured there must be a driver issue.  Went to ATI and whala, there are downloads for the 1250X drivers for linux.  I think it was  50MB download.  Saved it to my desktop. The filename is ati-driver-istaller-8.37.6.run.  

Now i figured double click and it would install...wrong..wrong wrong.  I guess this is where people get frustrated.  When I double click, it said something about being a BIN file, so i got on google and found something about bash....Ok, now I'm lost and need someone with some experience to giv me a bit of guidance.  I think if someone can help give me the basics, i will be off to the races.

So...anyone willing to help out!

-Mel
:D:D:D:D

---

### Post by Sparkster185 on 2007-06-15
You should just have to type:
```

sudo ./ati-driver-istaller-8.37.6.run

```

---

### Post by bukwirm on 2007-06-15
You may also need to make the file executable - "chmod +x *filename*" is the command (with sudo if needed, of course).

A Google search for "bash basics" or something similar will probably give you lots of good links.

---

### Post by pete83 on 2007-06-15
Without typing anything, I think you can just right click the file and go to properties, and then on the "permissions" tab you can check off "allow executing file as program."

---

### Post by prmmel on 2007-06-15
Changed the property to "executable as program" and double click .....10s, it pops up and says must run as super user.

If i go to terminal window and enter sudo ./ati.run (changed name), then I got  a password request....entered the password then it says command not recogmzed...

????

---

### Post by bukwirm on 2007-06-16
What is the output of "ls -l *filename*"?

If the output doesn't begin with something like "-rwxr-xr-x" but instead looks like "-rw-r--r--" (in others works, has no 'x's), you need to use the chmod command I gave earlier.

---

### Post by raynard79 on 2007-06-16
hahaha, I have just had the same problem.

You need to execute what is called a "bash command", and that needs to be typed in your directory that the file is in...

ie.# /home/(insert your username here)/Desktop/

Read this wiki, it will help..

[http://www.sumardi.net/2006/12/25/how-to-install-fglrx-in-ubuntu-manually/](http://www.sumardi.net/2006/12/25/how-to-install-fglrx-in-ubuntu-manually/)

It sounds like your at step no. 4 (create a DEB Package). Scroll down to "Alex's" comments on asking what the frug to do here, and he explains it..

Good luck!

Also, another good reference to have is this one:

[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

---

### Post by raynard79 on 2007-06-16
Just to let you know, that the first link I sent you has commands for the old Ubuntu (Dapper), you need to switch the commands to Feisy, which you can find in the second link... 


ie.

$ cd /home/<your_username>/Desktop

$ sudo bash ati-driver-installer-8.37.6-x86.x86_64.run --buildpkg Ubuntu/feisty

---

