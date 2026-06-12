---
title: "need help installing program"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by crunchystrike on 2006-09-05
ok, i have downloaded this file:

[http://ting.homeunix.org/cvs_wine/GetCVSWineX](http://ting.homeunix.org/cvs_wine/GetCVSWineX) by doing     
'wget http://ting.homeunix.org/cvs_wine/GetCVSWineX'

now it tells me in the instructions to as root type chmod 777 GetCVSWineX ..

ok, i type in chmod 777 GetCVSWineX .., tells me chmod: changing permissions of `..': Operation not permitted

then i type in sudo chmod 777 GetCVSWineX .. and it justs gives me the next line without doing anything

Here are instructions:

1- download this script to your hard drive : [http://ting.homeunix.org/cvs_wine/GetCVSWineX](http://ting.homeunix.org/cvs_wine/GetCVSWineX)
2- as root type chmod 777 GetCVSWineX ..
3- and execute it ./getCvsWinex
follow the instructions ...
If the CVS checkout is not responding (it failed) you must get it sources manually.. get the file here: HEREthen untar it as usual : tar -zxvf cvswinex.tar.gz and then compile it in the source directory by doing a:
- ./configure --enable-opengl
- make
and finally : make install (as root)


I might belive that im not doing this right because he tells me as root do it, i don't know what he means by that. Appreciate all the help i can get.

---

### Post by slibuntu on 2006-09-05
As root just means using sudo, if that helps

---

### Post by crunchystrike on 2006-09-05
ok, i have done that, don't work, i have 2 questions:

does anyone know what I am doing wrong here

where does the file save once u get it via wget?

---

### Post by Metacarpal on 2006-09-05
> **crunchystrike said:**
> then i type in sudo chmod 777 GetCVSWineX .. and it justs gives me the next line without doing anything

That means the operation was completed successfully.  Basically, you just made that file available to read, write, and execute to all users.  If you want to double-check to see if that worked, you can go to the folder where you saved the script, right-click, and choose Properties.  Click on the Permissions tab, and look to see that the Execute permission is checked.  If it is not, you should be able to check that box now.

Then, you can continue to the next step.  (And as previously mentioned, when it says "as root", just add sudo to the start of the command.

---

### Post by crunchystrike on 2006-09-05
I am newb, sorry, but where does the file save to if you get it by typing wget link link?

---

### Post by ruppmeister on 2006-09-06
crunchystrike,

It looks like you have done what the instructions have said up to line 2. Now you just have to type in the command line

```
./getCvsWinex
```

That should take you to the setup of Wine.

---

### Post by steve.horsley on 2006-09-06
If all you are trying to di is to install a nice recent version of wine, there is an easier way. winehq maintain their own repository that you can install wine from. It's updated every month or so. If that's what you want, then use the command:
**gksudo gedit /etc/apt/sources.lst**
and add these lines to the end of the file:
> # WINE
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
Now you can use synaptic, hit the reload button to learn about the new repository, and install the latest version of wine. You get the usual notofication when they release a later version.

---

### Post by carverj on 2006-09-06
Woohoo, Automatix is available for dapper

For easy install script for Wine and 700 other great things you'll need
follow link and run quick script

[http://www.ubuntuforums.org/showthread.php?t=177646](http://www.ubuntuforums.org/showthread.php?t=177646)

Couldn't be easier
Good Luck

---

