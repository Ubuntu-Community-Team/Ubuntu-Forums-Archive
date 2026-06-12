---
title: "can anyone give me a complete summary on how to use wine?"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by sayuki288 on 2007-11-01
need help using wine it's my first time using it

---

### Post by KhaaL on 2007-11-01
it's easy, you start a console in the directory of the .exe file you want to run, and type 

wine nameoffile.exe

you can also run winecfg to make some advanced configurations to it. You should also check [http://appdb.winehq.org/](http://appdb.winehq.org/) for what programs/games are supported and what settings they require.

---

### Post by sayuki288 on 2007-11-01
is there also a tutorial there on how to use it?

---

### Post by sayuki288 on 2007-11-01
i don't even know how to install in wine

---

### Post by KhaaL on 2007-11-01
not that i know of (except the man pages: man wine. they're not newbie friendly though!). If a program dosen't run properly, you should consult the appdb or these forums for help :)

---

### Post by KhaaL on 2007-11-01
And regarding installing - do it just as you would have done it on your windows machine: 
Enter the folder where the install.exe or setup.exe is, and run it with wine. Are you familiar with how DOS commands work (cd, dir etc.)? because if you do, then navigating within the console would be familiar to you.

---

### Post by sayuki288 on 2007-11-01
> **KhaaL said:**
> not that i know of (except the man pages: man wine. they're not newbie friendly though!). If a program dosen't run properly, you should consult the appdb or these forums for help :)

hey dude what can i use to mount .daa images cant seem to open it with gmount iso

---

### Post by KhaaL on 2007-11-01
For a solution with graphical interface, try [Acetone]("http://www.acetoneteam.org/download.html"). The new version isn't in a deb format yet, so you may have to get the old version instead.

There is another way of doing it [here]("http://www.cyberciti.biz/faq/how-do-i-open-daa-direct-access-archive-files-under-linux-or-unix-oses/"), but it's not a graphical solution and requires you to use the console.

Good luck!

---

### Post by linuxlizard on 2007-11-01
[http://frankscorner.org/](http://frankscorner.org/)

is a good site for basics of wine.

Easiest way to get wine is simply to click on applications in the upper right hand coner of your screen, then add/remove programs in the menu that appears. When the window opens, choose office in the left hand column and then scroll the right hand column all the way down- the last app under office is wine. click the box next to it, then click apply changes and there you go.

---

### Post by Scotty562 on 2007-11-01
What would make things really nice would be if you could go to wines website and download the .deb and have that automatically add the entry into the sources file. THEN, be able to browse to whatever .exe you want through the gui rather than the command line and then just double click on the .exe to run it. However, this isn't the case quite yet.

You have to do what the others mentioned. Pop open a terminal and navigate to the directory the .exe is in and then run wine myexe.exe. What I do after I get an app working is add it to my Applications menu, but that isn't straightforward either...

Good luck.

---

### Post by linuxlizard on 2007-11-01
> *You have to do what the others mentioned. Pop open a terminal and navigate to the directory the .exe is in and then run wine myexe.exe.*

No you don't- just browse with the filebrowser to the directory the exe is in, right click on it and select "open with Wine Windows Emulator".

> " What I do after I get an app working is add it to my Applications menu, but that isn't straightforward either.."

What I do which is a little more straightforward is to just make a shortcut icon on the desktop to run the app.

> wines website and download the .deb and have that automatically add the entry into the sources file

Maybe you can't do that, but you can click on the deb and ubuntu will ask you if you want to install it. Once installed, it will show up in synaptic and can be removed there as well. It's pretty easy to just follow the instructions on site though for how to add them to your sources file. If that's too complicated, there is a fairly recent version in synaptic already that you can just click on and install out of the box.

Oh, by the way, look into wine-doors as well. It automatically installs some windows apps for you and adds them to your applications menu.

---

