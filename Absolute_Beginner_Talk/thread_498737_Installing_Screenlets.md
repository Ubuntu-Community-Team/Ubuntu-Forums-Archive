---
title: "Installing Screenlets"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by Sethalos on 2007-07-11
Hi,

I'm trying to install a theme (based on Aero) and I was following the instructions from this site:

[http://www.compiz.org/Desktop_Screenlets](http://www.compiz.org/Desktop_Screenlets) to install the screenlets.

So I downloaded the tar.gz package and installed it as per the instructions.

(Note: I tried using the Feisty instructions using apt but they didn't work)

Anyways, when I run the screenletsd start command it runs, however, I can't seem to bring up the control panel, the command in the Terminal is supposed to be: screenlets-tray to bring it up, but when I type that in I get : bash: screenlets-tray: command not found

I'm pretty much stuck there and can't seem to get it to work.

I would appreciate any help. Thanks

You can find the Theme installation instructions here: [http://gnomestyle.blogspot.com/2007/05/make-ubuntu-look-like-vista.html](http://gnomestyle.blogspot.com/2007/05/make-ubuntu-look-like-vista.html)

Note: I also am not sure which fonts to use where either if anyone has used this theme.

---

### Post by DSn0wMan on 2007-07-12
I forget exactly where it is since I removed my screenlets, but there should be a python script somewhere called "screenletsd.py" once it's installed. Once you run that script you should see a little button floating around your desktop somewhere that you can right click to add and configure screenlets. You should also now see a screenlets icon in your system tray.

---

### Post by Inxsible on 2007-07-12
See if you have a entry under Applications --> Accessories --> Screenlets. That will start up your screenlets-tray. You can right click on the icon and select Settings to start the control panel then.

---

### Post by Sethalos on 2007-07-14
Hi, 

No, I don't have the little icon on the desktop and it's not in my Accessories menu either.  However, the program does seem to be running, and when I installed it, I didn't receive an error either.

I do know where that file is, that is what I used to install it I believe.  Perhaps I installed it incorrectly. I'm not sure.  What would the command be?

make install <file name>  is what I used <filename> being the .py file listed above.

---

### Post by DSn0wMan on 2007-07-14
Here are some instructions on how to install screenlets from a repository

[http://ubuntuforums.org/showthread.php?t=444158&highlight=screenlets](http://ubuntuforums.org/showthread.php?t=444158&highlight=screenlets)

[http://www.compiz.org/Desktop_Screenlets](http://www.compiz.org/Desktop_Screenlets)

Once you have used apt-get or aptitude install, you have installed it. To start the screenlets try ```
screenletsd start
```

---

