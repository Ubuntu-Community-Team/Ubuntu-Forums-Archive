---
title: "!? Help with amsn installation..."
date: 2006-05-03
forum: Absolute Beginner Talk
---

### Post by gummylindz on 2006-05-03
Hi, I'm installing amsn and im compiling it at the mo (don't think that by saying that I know what I'm saying, it's just what the readme says, i'm a newbie and a noob in these matters......:-? ). Anyway, it just told me this:

> You must have the tcl-dev and tk-dev packages installed on your system, please refer to your system package management software or website in order to find these packages and to install them prior to running the ./configure script.

So yeah, I needa get those **tcl-dev** and **tk-dev** packages from somewhere, can anybody help??? :confused: 

thanks....

---

### Post by gummylindz on 2006-05-03
okay, i've got the files.

but i've also got two very weird readme installation things that i haven't a clue what they mean......... can't i just install the two packages by doing a sudo -R thingy??? *shrug*....

as you can see im quite inexperienced in the ubuntu way of installing new things.

help!!

---

### Post by gummylindz on 2006-05-03
ok......... i've done the **tcl-dev** package. yay! i managed it :D but now there's that other one........ it isnt as easy, the readme isn't as clear. i'll carry on investigating if nobody comes up with any help, but it would be much appreciated!!!

---

### Post by NetMatrix on 2006-05-03
try 

```
sudo apt-get install tk-dev
```

if that doesn't help (or doesn't work) try

```
sudo apt-get install build-essential
```

This should install most, if not all things needed to compile programs.

Good Luck. :D

---

### Post by aysiu on 2006-05-03
When advanced users compile from source, I think they usually have a reason for doing so.

When people in the Absolute Beginner section compile from source, I think they usually don't realize there's an easier way to do it.

Read this if you want to know how to install software easily:
[http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html)

If you absolutely must have the latest version (0.95), follow [these instructions](http://www.ubuntuforums.org/showpost.php?p=978766&postcount=47). It's easier than compiling from source--believe me.

---

### Post by gummylindz on 2006-05-03
thanks a bunch guys :) 

aysiu, that first page is funny, even if its for simpleminds like me..... :$ ..... thanku tho hehehe

---

### Post by mattm591 on 2006-05-03
[QUOTE=aysiu]When advanced users compile from source, I think they usually have a reason for doing so.

When people in the Absolute Beginner section compile from source, I think they usually don't realize there's an easier way to do it.

Read this if you want to know how to install software easily:
[http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html)

If you absolutely must have the latest version (0.95), follow [these instructions](http://www.ubuntuforums.org/showpost.php?p=978766&postcount=47). It's easier than compiling from source--believe me.[/QUOTE]
The latest version is 0.96. 0.95 is now avaliable through Synaptic. To get to it jhust make sure you have all the different repositories ticked (look in one of the menus to change this). Then you can search for and find amsn. If you want to get 0.96 (which does have many improvements) you should just be able to download the cvs and then use this command:

sudo cp -R amsn /usr/share/


This presumes you have extracted the cvs and renamed the folder to amsn (which you must do) and that you are currently in that folder location in terminal.

---

### Post by aysiu on 2006-05-03
[QUOTE=mattm591]The latest version is 0.96.[/quote] When you go to the download page on the aMSN website, the version you download is 0.95. The latest announcement on the front page of their website is the release of 0.95. Isn't CVS the latest test build--not one they've officially released? >  0.95 is now avaliable through Synaptic. [It is in Dapper](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=amsn&searchon=name&subword=1&version=all&release=all), but I was assuming an Absolute Beginner would be using Breezy. 

**Edit**: Now that I look again, though, you're right--gummylindz is using Dapper, not Breezy. So,yes, 0.95 is in the repositories.

---

