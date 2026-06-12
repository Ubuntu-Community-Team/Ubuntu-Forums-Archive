---
title: "[SOLVED] bible desktop"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by Papa-san on 2008-03-15
I have downloaded Bible desktop as bibledesktop-1.0.7-bin.tar.gz

I extracted it to my /tmp using archive manager. It says I need to run: BibleDesktop.sh

When I double-click it, nothing happens. When I right-click on it I get 'Open with wine' , Open with 'text editor' , and open with 'other application' (this one doesn't give me any options in the GUI), or to open my scripts. 

A long time ago, I actually had a icon on my desktop to be able to double-click and the program opened.  Last re-install of Ubuntu, the best I could come up with was the .sh as a shortcut on my desktop. When I double-clicked that, It would give me a popup that asked if I wanted to open it as a text, cancel it or run it. I would have to do the 'run it' option, and it would finally open.

What I would like is to have it installed properly so that it's provided icon was the link to whatever it has to be linked to to open my program properly when I double-click that icon. (Just like all my other stuff)

Any help would be appreciated! 

Thanks!

Oh, I added a screenshot to show what I have in that folder, if it helps:

---

### Post by sumguy231 on 2008-03-15
Run it from a terminal to see what error output it gives. To run it, do this:
```
cd /tmp/jsword-1.0.7
./BibleDesktop.sh

```

All the .jar files hint that it might be a Java application. Do you have the Java runtime installed?

---

### Post by luke2760 on 2008-03-15
I haven't used bible desktop, but you might try right-clicking on the BibleDesktop.sh, hitting "properties," then browsing over to the "Permissions" tab, and then clicking "allow file to be run as executable."

So try that.

If that doesn't work, it sounds like someone has prettied up a wine interface so you don't need wine. But if that doesn't work, you could try installing wine, running winecfg, then trying the run as wine option (though you would want to run the .exe file, not the .sh)

---

### Post by Papa-san on 2008-03-15
Here's what I got:
```
john@ubuntu:~$ cd /tmp/jsword-1.0.7
john@ubuntu:/tmp/jsword-1.0.7$ ./BibleDesktop.sh
bash: ./BibleDesktop.sh: Permission denied
john@ubuntu:/tmp/jsword-1.0.7$ sudo ./BibleDesktop.sh
[sudo] password for john:
sudo: ./BibleDesktop.sh: command not found
john@ubuntu:/tmp/jsword-1.0.7$ cd /tmp/bibledesktop
bash: cd: /tmp/bibledesktop: No such file or directory
john@ubuntu:/tmp/jsword-1.0.7$ 
```
See, that's one of the things that bugs me... The file IS there, but for some reason it doesn't seem to find it... 
Are there more than one '/tmp' directory?

---

### Post by Papa-san on 2008-03-15
OK,
It runs after I changed the permissions, Thank you.

Do you know how I would make that a desktop shortcut (preferably using one of the .gif icons they supplied)  that doesn't ask me what I want it to do?

---

### Post by jordanmthomas on 2008-03-15
First off, don't keep it in /tmp or it will be deleted when you reboot.
Move it elsewhere.  Then, you can create a launcher for it.
The easiest way I know to do this is to right click on your panel and go to 'Add Item'
Then, create a custom launcher and fill out the info.  For the command line, select the BibleDesktop.sh

If you want this on your desktop, you can just drag it from your panel to your desktop.  Hope this helps.

---

### Post by JoshuaRL on 2008-03-15
You can also go into the terminal and run:
```

alacarte

```

That will open Alacarte.  You'll be able to put a new entry in the Applications menu through there, and assign an icon to it.

---

### Post by Papa-san on 2008-03-15
> **jordanmthomas said:**
> First off, don't keep it in /tmp or it will be deleted when you reboot.
Move it elsewhere.  Then, you can create a launcher for it.
The easiest way I know to do this is to right click on your panel and go to 'Add Item'
Then, create a custom launcher and fill out the info.  For the command line, select the BibleDesktop.sh

If you want this on your desktop, you can just drag it from your panel to your desktop.  Hope this helps.

OK. Where should I move it to? What is the proper way to move it? Cut and paste the jsword folder somewhere?

The 'add item' is that the same as 'create launcher'?
EDIT: I have the alacarte figured out, so I'll use that.

Thanks!

---

### Post by Papa-san on 2008-03-15
I know I'm a Linux idiot...
How do I establish permission to create a folder in /etc ?

---

### Post by crjackson on 2008-03-15
> **Papa-san said:**
> I know I'm a Linux idiot...
How do I establish permission to create a folder in /etc ?

It really doesn't belong there.  Why don't you just put it in a sub folder of your home folder?

---

### Post by Papa-san on 2008-03-15
LOL... like I said!

I just assumed that's where program files would go. I made a folder in /home and moved it. I'll try to set up a menu item now through alacarte

EDIT:
I re-booted, and looked in my /tmp directory, assuming it would be empty, but found these instead (attached screen-shot). Does anybody know what they are? 'Tracker' sounds like something I want to avoid...

RE-EDIT... OK, NOW there's a screen-shot! LOL

(any idea how to save a gif or jpg as a 'svg' so I can get it as a choice for my launcher?)

---

### Post by handydan918 on 2008-03-15
Are you sure you attached a screenie? I don't see one...

---

### Post by JoshuaRL on 2008-03-16
Tracker is an app that indexes everything you do for quick desktop searches.  So it might have something to do with that, but I'm not sure.

And what launcher are you talking about?

---

### Post by Papa-san on 2008-03-16
The launcher I made for Bible Desktop. It's under Applications > Bible Desktop now, but it has a default icon. I can change it to the one that comes with the program, but I need to figure out how to save it in a format that will be recognized by the alacarte launcher editor. It seems like it only wants to use .svg images from the /usr/share/icons/hicolor/scalable/apps folder... I tried copying the logo as a jpg and gif, then saving it as a .svg but gimp doesn't know what kind of file it is. (Funny, because I can navigate to an existing one and it opens it just fine...)

Here's a screen-shot: 
It shows the alacarte GUI and the properties GUI. in the background is the open directory where the icons are found by the properties GUI. What I want to change is the springy button looking thing on the upper right of the small properties GUI. An earlier shot shows the .gif icons that came with the program.

---

### Post by sumguy231 on 2008-03-16
Try making the icon a png or xpm, either of those should be recognized.

---

### Post by Papa-san on 2008-03-16
I cannot copy it to that directory in any format. I don't know how to get permission to do that. It keeps telling me I am not the owner, so I can't change settings... 

I have it saved as a .png, now I need to get it into the right place...

---

### Post by JoshuaRL on 2008-03-16
You can use a .png in Alacarte from wherever.  Just make sure it's somewhere you wont move or delete.  Then put the path to it or Browse for it, and you're set.

---

### Post by Papa-san on 2008-03-16
I have the image saved as a png in my jsword folder in  /home.
It doesn't give any options other than .svg files that are specifically in the './apps' folder. I do the 'Browse' thing, and once I get into the jsword folder, there is nothing listed. Not jpg's, gif's, or png's.

I will try to enter the path to it. That's one thing I haven't tried yet... Duh!

Edit:
I typed in the path and it says 'No icon'

---

### Post by jordanmthomas on 2008-03-16
```
sudo cp /path/to/theicon.png /usr/share/pixmaps
```
If you do this it should show up in the list of available icons.

Also, to convert the gif to a png in a way that definitely works (I don't know if you may have just renamed the gif to a png)
```
sudo apt-get install imagemagick
```
install imagemagick
```
convert icon.gif icon.png
```
This will turn your gif into a png that you can use.

---

### Post by Papa-san on 2008-03-16
I used Gimp to open the file and save as... .png.

I got it! 

I didn't know the path was /home/john/... I had tried with either one, but not both... 

nOOb mistake...

Thanks for all the help!

---

