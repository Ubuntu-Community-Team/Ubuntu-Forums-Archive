---
title: "how to start clamav"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by nikef on 2007-08-14
looked in applications and its nowhere to be seen :(

---

### Post by arijarot on 2007-08-14
I think it's ```
clamd
``` which starts the clamav deamon...

---

### Post by arijarot on 2007-08-14
if not, here is the user guide [http://www.clamav.net/doc/latest/html/](http://www.clamav.net/doc/latest/html/)

---

### Post by Arwen on 2007-08-14
You can also type clamscan in terminal,it starts a scan in /home/user/

---

### Post by RomeReactor on 2007-08-14
Hi. ClamAV is a command line application; you can install a graphical interface for it, like **ClamTK** or **KlamAV**. Look for them in Synaptic (System->Administration->Synaptic Package Manager), or to install from the terminal (Applications->Accessories->Terminal):
```
sudo apt-get install clamtk
```
or
```
sudo apt-get install klamav
```
I've heard ClamTK is a little buggy, so you should probably go with KlamAV.
To learn how to use ClamAV from the terminal, enter:
```
man clamscan
```

---

### Post by nikef on 2007-08-14
> **arijarot said:**
> I think it's ```
clamd
``` which starts the clamav deamon...

thanks i typed this in an i got an error 

trish@trish-desktop:~$ clamd
ERROR: Can't open /var/log/clamav/clamav.log in append mode (check permissions!).
ERROR: Problem with internal logger. Please check the permissions on the /var/log/clamav/clamav.log file.
trish@trish-desktop:~$

---

### Post by arijarot on 2007-08-14
> **nikef said:**
> thanks i typed this in an i got an error 

trish@trish-desktop:~$ clamd
ERROR: Can't open /var/log/clamav/clamav.log in append mode (check permissions!).
ERROR: Problem with internal logger. Please check the permissions on the /var/log/clamav/clamav.log file.
trish@trish-desktop:~$

sorry, type ```
sudo clamd
```

fyi, any time you get a message about permissions, it's usually because you need root permissions...

---

### Post by nikef on 2007-08-14
> **RomeReactor said:**
> Hi. ClamAV is a command line application; you can install a graphical interface for it, like **ClamTK** or **KlamAV**. Look for them in Synaptic (System->Administration->Synaptic Package Manager), or to install from the terminal (Applications->Accessories->Terminal):
```
sudo apt-get install clamtk
```
or
```
sudo apt-get install klamav
```
I've heard ClamTK is a little buggy, so you should probably go with KlamAV.
To learn how to use ClamAV from the terminal, enter:
```
man clamscan
```

thanks i have just open up clamtk,tried to scan a file but it says you do not apear to have virus definitions running freshclam-v as root may fix problem

---

### Post by nikef on 2007-08-14
> **arijarot said:**
> sorry, type ```
sudo clamd
```

fyi, any time you get a message about permissions, it's usually because you need root permissions...

thanks typed it in this is what it says 

trish@trish-desktop:~$ sudo clamd
Running as user clamav (UID 110, GID 120)

but i still can not find the scanner

---

### Post by nikef on 2007-08-14
tried to update clamtk
it says i must be root to run updates
but i am root,i am the only person that uses this pc :(

---

### Post by arijarot on 2007-08-14
> **nikef said:**
> thanks typed it in this is what it says 

trish@trish-desktop:~$ sudo clamd
Running as user clamav (UID 110, GID 120)

but i still can not find the scanner

well, as RomeReactor said, it's a command line program, so you won't see the scanner per se. you can type ```
 ps -aux | grep clam
``` in the terminal to see the process or look at the process in the system monitor (system>admin). other than that, you'll have to install the graphic user interface (gui) as [RomeReactor ]("http://ubuntuforums.org/showpost.php?p=3187378&postcount=5")suggested in order to "see" the scanner. 

hope that helps.

---

### Post by arijarot on 2007-08-14
> **nikef said:**
> tried to update clamtk
it says i must be root to run updates
but i am root,i am the only person that uses this pc :(

you need to use sudo in order to make yourself "root," as you normally just run under "user" (your name usually).

---

### Post by nikef on 2007-08-14
> **arijarot said:**
> well, as RomeReactor said, it's a command line program, so you won't see the scanner per se. you can type ```
 ps -aux | grep clam
``` in the terminal to see the process or look at the process in the system monitor (system>admin). other than that, you'll have to install the graphic user interface (gui) as RomeReactor suggested in order to "see" the scanner. 

hope that helps.

thanks very much,sorry it took a while for me to understand it properly  :)

---

### Post by nikef on 2007-08-14
> **arijarot said:**
> you need to use sudo in order to make yourself root, as you normally just run under "user" (your name usually).

thanks
so i want 2 run and update clamtk

do i type in terminal 

sudo update clamtk  ?

what do i type to tell it to scan ?

sorry for all the questions

---

### Post by RomeReactor on 2007-08-14
I don't have Clam installed at the moment, but I think you run:
```
sudo freshclam
```
to update the database.

I found one of my old posts describing how to [perform basic operations with Clam]("http://ubuntuforums.org/showpost.php?p=2039075&postcount=8") from the terminal. Also I suggest you uninstall ClamTK and use KlamAV instead.

---

### Post by nikef on 2007-08-14
> **RomeReactor said:**
> I don't have Clam installed at the moment, but I think you run:
```
sudo freshclam
```
to update the database.

I found one of my old posts describing how to [perform basic operations with Clam]("http://ubuntuforums.org/showpost.php?p=2039075&postcount=8") from the terminal. Also I suggest you uninstall ClamTK and use KlamAV instead.

thank you very much  i will read your post,how do i unistall clamtk  please

---

### Post by RomeReactor on 2007-08-14
Almost the same ay you installed it:

From Synaptic, search for **clamtk**, when it shows up right click on it and select "Mark for Removal".

Or to uninstall it from the terminal:
```
sudo apt-get remove clamtk
```

Just a note: Installing KlamAV will need additional libraries to run KDE applications in Gnome. Gnome is the desktop environment you have now; KDE is what comes by default in Kubuntu ([click this link]("http://www.linuxcdstore.it/kubuntu/01.gif") to see what KDE looks like). In any case, there's no problem running KDE applications in Gnome; I only want to let you know that downloading KlamAV and those additional libraries will result in a download of about 35 MB. So you might want to keep ClamTK after all. It's your choice.

---

### Post by nikef on 2007-08-14
> **RomeReactor said:**
> Almost the same ay you installed it:

From Synaptic, search for **clamtk**, when it shows up right click on it and select "Mark for Removal".

Or to uninstall it from the terminal:
```
sudo apt-get remove clamtk
```

Just a note: Installing KlamAV will need additional libraries to run KDE applications in Gnome. Gnome is the desktop environment you have now; KDE is what comes by default in Kubuntu ([click this link]("http://www.linuxcdstore.it/kubuntu/01.gif") to see what KDE looks like). In any case, there's no problem running KDE applications in Gnome; I only want to let you know that downloading KlamAV and those additional libraries will result in a download of about 35 MB. So you might want to keep ClamTK after all. It's your choice.

thanks
i have uninstalled  clamtk and installed klamav
i can not see it in my applications  :confused:
i have looked at kde and it looks nice
i have 32.6gb space left

---

### Post by RomeReactor on 2007-08-14
Sometimes programs don't make entries in the menus--it's a rare occurrence, but it does happen. And sometimes the panels just need a little time for the icon to show up. You can try restarting them to see if it shows up then: go to "System->Administration->System Monitor", look for **gnome-panel**, right-click on it and select **kill process**. Don't worry if it sounds too harsh; it will just restart the panels. When they show up again, look for KlamAV (it should show up in "Applications->Internet", I think). If it still doesn't show up, we'll make a menu entry ourselves.

---

### Post by arijarot on 2007-08-14
> **nikef said:**
> thanks
i have uninstalled  clamtk and installed klamav
i can not see it in my applications  :confused:
i have looked at kde and it looks nice
i have 32.6gb space left

you can type in ```
klamav
``` in the terminal to run it if you can't find it otherwise... use sudo if need be...

---

### Post by nikef on 2007-08-14
Wow that was scary lol
ok,its being a little devil and its still not showing

---

### Post by RomeReactor on 2007-08-14
Just installed it here and didn't show up either...

Well, we'll make an entry in the menus: right-click on your **Applications** menu and select "Edit Menus". Then highlight "Internet" on the left, and on the right press "New Item". A window titled **Create Launcher** will pop up, and we'll fill it out like this:

Type: Application

Name: KlamAV (or whatever you like)

Command: klamav

Comment:  (Leave blank if you like)

Now press the **No Icon** button, and paste this in the search bar:
```
/usr/share/apps/klamav/icons/hicolor/32x32/apps/
```
Four icons will show up; choose the one you want, clcik OK, again OK in the previous window, and you're done.

---

### Post by nikef on 2007-08-14
> **RomeReactor said:**
> Just installed it here and didn't show up either...

Well, we'll make an entry in the menus: right-click on your **Applications** menu and select "Edit Menus". Then highlight "Internet" on the left, and on the right press "New Item". A window titled **Create Launcher** will pop up, and we'll fill it out like this:

Type: Application

Name: KlamAV (or whatever you like)

Command: klamav

Comment:  (Leave blank if you like)

Now press the **No Icon** button, and paste this in the search bar:
```
/usr/share/apps/klamav/icons/hicolor/32x32/apps/
```
Four icons will show up; choose the one you want, clcik OK, again OK in the previous window, and you're done.

thank you very much for sticking with me on this 

i now have klamav 0.41 installed :)

---

