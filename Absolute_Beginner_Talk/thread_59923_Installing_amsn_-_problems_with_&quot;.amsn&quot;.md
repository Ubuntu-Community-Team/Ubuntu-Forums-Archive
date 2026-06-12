---
title: "Installing amsn - problems with &quot;./amsn&quot;"
date: 2005-08-25
forum: Absolute Beginner Talk
---

### Post by LinuxLove on 2005-08-25
Sorry if this might be posted already, but I searched the forums and found nothing.

```

root@COMPUTER-01:/home/jeremy # gzip -d amsn.orig.tar.gz
root@COMPUTER-01:/home/jeremy # tar xvf amsn.orig.tar


------------ displays the files that were extracted ------------


root@COMPUTER-01:/home/jeremy # cd amsn-0.94.orig
[email]root@COMPUTER-01:/home/jeremy/amsn-0.94.orig[/email] # ./amsn
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Application initialization failed: this isn't a Tk applicationcouldn't connect to display ":0.0"
Error in startup script: invalid command name "wm"
    while executing
"wm state . withdraw"
    (file "./amsn" line 43)


``` 

Help is appreciated.

---

### Post by jasmuz on 2005-08-25
I cant say much about your issue, but did you know the aMSN 0.94 is in the repositories, unless you are trying to use the CVS version of the 0.95 with integrated webcam support there is no need to go nuts over compiling your own.

---

### Post by LinuxLove on 2005-08-25
[QUOTE=jasmuz]I cant say much about your issue, but did you know the aMSN 0.94 is in the repositories, unless you are trying to use the CVS version of the 0.95 with integrated webcam support there is no need to go nuts over compiling your own.[/QUOTE]


Sorry, but I'm quite new to Kubuntu and Linux in general. I take it that compiling is using the Terminal to install? Correct me if I'm wrong, but are you suggesting that I use a package manager? Maybe its that my eyes are bad, but I can't find "amsn" anywhere in the Kubuntu Package Manager. From tutorials I was told this is how I could install amsn; any method of installing is fine by me.

Thanks.

---

### Post by poopdedoop on 2005-08-25
are you trying to install it thru the termanal? there is an installer for that.

[amsn-0.94-3-linux-installer.bin](http://prdownloads.sourceforge.net/amsn/amsn-0.94-3-linux-installer.bin?download) 

get it there ^^

if you can't open it you have to go into it's properties, then under permissions (or whatever it is) you have to check execute beside "owner"

---

### Post by LinuxLove on 2005-08-25
[QUOTE=poopdedoop]are you trying to install it thru the termanal? there is an installer for that.

[amsn-0.94-3-linux-installer.bin](http://prdownloads.sourceforge.net/amsn/amsn-0.94-3-linux-installer.bin?download) 

get it there ^^

if you can't open it you have to go into it's properties, then under permissions (or whatever it is) you have to check execute beside "owner"[/QUOTE]

I did this, but it only created another folder just like the terminal did with the same files. I went back to the terminal and did a "./amsn" inside the new directory but I get the same error.

Also, if "./amsn" isn't required, and you can actually boot the file from the folder it installed too "amsn.desktop" didn't work when clicked. Told me "Could not launch 'amsn'. Could not find 'amsn' executable". I right-clicked, went to properties, then to permissions, and checked the box next to "is executable" (just like the .bin file) -- still didn't work.

--------------
EDIT: Oh! I just noticed the "aMSN" icon on my desktop. Thanks a lot for your help. (:

---

### Post by El Viejo Lobo on 2007-11-22
Why not going to System/Administration/Synaptc Package manager ? 
Search for aMSN and mark it for installation  then apply it and have it clean&easy working.
:guitar:

---

