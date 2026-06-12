---
title: "Installing with apt-get.... now what?"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by reado on 2006-12-07
Hi Everyone,

I'm really trying hard here to give Ubuntu a fair shot but I'm having a problem trying to understand some concepts.

The big one I have right now is that I've followed a few tutorials for installing programs using things like apt-get, add/remove programs and a ton of other application managers and I've been able to get all methods working properly but i'm having troubles trying to find the program once its installed.

For example... I tried to install Eclipse to do some Java/C developing and I read some tutorials indicating that the program can be installed with apt-get (assuming you also get jdk, etc..).  I used this method and the install went fine but I'm not sure how to even start the program... Where the hell did the 'executable' program go?

Not to sound dumb but i'm used to be able to select a location ("C:\Program Files\...") and worst case scenario then be able to access the files in there...

I understand that unlike windows, applications don't always "invade" your desktop without your permission but to be honest, i'm not even sure where to begin!  Why isn't the program listed in my app list?  where's the desktop icon??  (haha, i know this might sound EXTREMELY Microsoft influenced but whatever 8) )

This also isn't limited to just Eclipse, earlier I wanted to install checkgmail which is great but yeah, i had to track it down within /usr/bin (found it by fluke) and I had to setup the application in my desktop manually.  (I have since added it to my login start and app list).. but do i have to do this every time???

Anyone have some suggestions for me?  

Thanks, please note, I really did try to figure this out on my own but i've realized that I have to get this figured out if i ever plan to seriously use a linux system.

Thanks so much!

---

### Post by lemonsCC on 2006-12-07
As far as I know most apps install in the /usr/bin directory.  If it doesn't show up in you applications menu try typing ```
killall gnome-panel
```

---

### Post by lemonsCC on 2006-12-07
Also linux maintains a clean desktop, any icons you want must be added manually.

---

### Post by reado on 2006-12-07
Thanks

Under normal circumstances, do most programs install in the app list or was this just the case for these particular programs?

As well, how do you guys typically find the applications you install?

And yeah, I have found my Eclipse install folder (at least I think i did..) but I don't really see any executable program... 

Obviously i'm missing something... any ideas?

Thanks again lemonsCC

---

### Post by ciscosurfer on 2006-12-07
You can use the **find** or **locate** (or others like **whereis**) commands to find the app.  To use locate, you must first update the database```
sudo updatedb
```If you can't find the app in your menus, you can manually create a menu location by going to System > Adminstration > Menu Layout and create one there.

You can find help on the "find" commands by entering in a terminal```
man find
man locate
man whereis
```You can also go to Sytem > Help > System Documention and type in man find (for example) into the keyword search if you want yelp (graphical front-end to the help system) to do it for you.

If you do find the app in your menus, you can right-click and choose Add this launcher to panel or Add this launcher to desktop.

---

### Post by ciscosurfer on 2006-12-07
I believe Eclipse should/will be located under Applications > Programming menu.

---

### Post by gentlemanmasher on 2006-12-07
Any program can be started by typeing in the name of the program in the terminal.  Also have you used synaptic to intall any programs?    
Very easy for me when I started.

Read [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php) for some help on beginner tutorials.  this saved my life when I first started.

---

### Post by lemonsCC on 2006-12-07
You could do yourself a favor and install debian menus.  This lists ABSOLUTELY EVERY program installed on your system.

I am not sure of the packages but automatix can install it for you.

---

