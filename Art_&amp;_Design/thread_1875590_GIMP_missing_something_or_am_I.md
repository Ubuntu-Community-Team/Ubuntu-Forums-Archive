---
title: "GIMP missing something or am I?"
date: 2011-11-05
forum: Art &amp; Design
---

### Post by Satanta on 2011-11-05
I have been trying to figure out how to install scripts/add-on fliters to Gimp 2.6.  I have read the web until my eyes are bleeding.  A couple of more sites tell me to go into Gimp/edit/preffs/folders and it will show me Python-fu and donkey Kong-fu [[or whatever]]  however MINE shows a .tmp folder and a swap folder [[IIRC]], soething of that natyure in drop-down box type menu ala Windows,  I have tried a number of different ways of installing the tarballs and the single .scm files-the tarbals have not installed or even moved from their current location [[my desktop]].  I can unzip them and read thru the files but I see nothing usefull and nothing on the web has helped.  I moved the .scm from my desktop using Sudo in this path: file system/usr/lib/gimp/2.0[?] then plugins [[there is no 'scripts' folder anywhere that I have found.  I had been using WINE to run PS7 but getting my best filters in has also been a serious PITA.  I need to get one or both of them running as I am a artist/photographer and this is killing my workflow.  Any help for one or both would be appreciated.

---

### Post by SteveDee on 2011-11-05
> **Satanta said:**
> ...I moved the .scm from my desktop using Sudo in this path: file system/usr/lib/gimp/2.0[?] then plugins [[there is no 'scripts' folder anywhere that I have found....

The path to your scripts file should be: /home/satanta/.gimp-2.6/scripts

So put .scm files in there, then start Gimp and go to: menu Filters > Script-Fu > Refresh Scripts

Now when you go to the Script-Fu menu your scripts should be listed.

---

### Post by ofnuts on 2011-11-05
To make it short:

- you can install additional things (modules, plugins, scripts, fonts, brushes....) either for all ids in the system (in /usr) or only for yourself (under ~/gimp-2.6). To install for all ids under Unix use the "gimptool-2.0" utility (usually "sudo gimptools-2.0 install ...", but on the whole it's better to install most of this stuff for yourself under /home.

- tarballs are usually C code that should be compiled into an executable: de-tar ("tar -cvf...."), and in the root directory issue "./configure" then "make". The resulting executable should then be moved to ~/gimp-2.6/plugins.

- script-fu (.scm) go directly in ~/gimp-2.6/scripts.

- python-fu (.py) go into ~/gimp-2.6/plugins after making them executable ("chmod +x foobar.py")

- other stuff goes into the appropriate subdirectory of ~/.gimp-2.6: brushes, gradients, fonts, palettes...

"Edit/preference/folders" lets you manage which folders Gimp looks at for all this additional stuff (you will find that each category usually has two entries, one under /usr, and one "writable" under ~/gimp-2.6) but unless you are a big user you don't need to play with that.

---

### Post by Satanta on 2011-11-05
Hmmm....well, Under "Home" either on the System Settings or Home button on the sidebar neither of them show Satanta [[That is my name used too]]  "Home" on the sidebar takes me to the next tree or whatever with 12 icons and none are me.  Also GIMP does not have a scripts folde when I go thru system and follow the branches in to it.  Late last night but one route I took that I would have to figure out going into the Gimp files had 'Zero' folders in it-that was confusing as I thought perhaps I had somehow deleted the Add-ons folder by accident.  I like Ubuntu for the most part-seems a bit slow and my mouse, even with the settings adjusted, seems to not 'catch' on things to move them and highlighting text for a C&P is almost impossible but I can live with that.  Not being able to enhance and run my photography software is a problem tho.  Anyone know if screenshots in Ubuntu are done similart to Windoze?  Win I hit PrntScrn and paste it into a new doc in PS&, compress, resize and post.  Not sure for Ubuntu but am wondering if screenshots might help.

---

### Post by ofnuts on 2011-11-05
> **Satanta said:**
> Hmmm....well, Under "Home" either on the System Settings or Home button on the sidebar neither of them show Satanta [[That is my name used too]]  "Home" on the sidebar takes me to the next tree or whatever with 12 icons and none are me.  Also GIMP does not have a scripts folde when I go thru system and follow the branches in to it.  Late last night but one route I took that I would have to figure out going into the Gimp files had 'Zero' folders in it-that was confusing as I thought perhaps I had somehow deleted the Add-ons folder by accident.  I like Ubuntu for the most part-seems a bit slow and my mouse, even with the settings adjusted, seems to not 'catch' on things to move them and highlighting text for a C&P is almost impossible but I can live with that.  Not being able to enhance and run my photography software is a problem tho.  Anyone know if screenshots in Ubuntu are done similart to Windoze?  Win I hit PrntScrn and paste it into a new doc in PS&, compress, resize and post.  Not sure for Ubuntu but am wondering if screenshots might help.
1) which version of Ubuntu are you using? With which desktop (Unity, Grnome, KDE)?
2) "Home" in your file manager is likely "/home/satanta/" on the file system 
3) your Gimp profile (.gimp-2.6) has a name starting with a dot, so by default it's not displayed. If you want to access it with your file manager, you have to explicitly ask it to show hidden files/directories. By doing so you'll discover you have already quite a few beside .gimp-2.6.
4) as said above, Gimp has two places to keep scripts: those available to everybody in /usr/share/gimp/2.0/scripts/ (but your better stay out of that for the tile being), and those that are only yours in /home/satanta/.gimp-2.6/scripts
5) There is no reason that Ubuntu to be any slower than Windows on the same hardware. I find it a lot faster in many cases, especially when there is a lot of disk I/O. But these are question for the general help section.

---

### Post by bluexrider on 2011-11-05
All of the sub-folders used by Gimp are in /home/USER/.gimp2-XX folder

Make sure you access the correct one.

---

### Post by Satanta on 2011-11-05
Got it.  THe answers helped me search on the right questions [[plus I learned a little more about the OS' workings.]]  CTRL-H showed me the .gimp folder.  Otherwise a was branching much further into the system.  Much appreciate the help.

---

### Post by bluexrider on 2011-11-27
done

(SOLVED)

---

