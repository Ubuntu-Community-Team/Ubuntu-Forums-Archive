---
title: "File Download"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by Aegis on 2007-05-02
In a neutron star level density move, I downloaded a file and didn't all all concern myself with where that file would download.   It gets better.  I didn't write down the filename.  (Please don't hurt me.)  Is there a "default" directory in ubuntu/linux to where files are downloaded?

I think it was a *.tar file.  I tried searching using the file manager, and using a terminal window.  I am an old UNIX user (emphasis on old) and I even changed to the root directory and tried 'cat' and 'grep'.  The problem is that my paleolithic brain cannot remember the command syntax to cause a search to check all the directories and files "under" a particular point on the "tree."  (Hence my attempt to search from root.)

I know I'm not worthy, but I pathetically beg for help!:oops: 

Thank you!

(I tried searching the forums, and couldn't find anything.  No, I did not look under 'stupid.':) :) )

p.s.  Is there a way to change the default download destination?

---

### Post by PartisanEntity on 2007-05-02
Did you download it with Firefox? Or using the terminal?

---

### Post by taurus on 2007-05-02
Probably in ~/Desktop.  Open a terminal and post the output of this command.

Applications -> Accessories -> Terminal
```
ls -la ~/Desktop
```

---

### Post by starcraft.man on 2007-05-02
If you downloaded it with firefox, the default is on your desktop. If you downloaded it with wget from terminal, it should be in your home folder. (Places > Home Folder). You should be able to spot the file thats out of place.

---

### Post by octoberdan on 2007-05-02
here's a neat trick. Open up a terminal and enter the following command/mini-script
```

find -type d | while read a; do ls -la "$a" | grep 2007-04-07; done

```

but replace 2007-03-07 with the date of when you downloaded the file.

---

### Post by Aegis on 2007-05-02
I only wish it was on the desktop.  I intend to make the desktop my default destination in the future.  I ran the list command in a terminal window, and I see only the parent directories and two folders which I have on the desktop, as follows

total 16
drwxr-xr-x  4 espo2 espo2 4096 2007-04-27 15:28 .
drwxr-xr-x 32 espo2 espo2 4096 2007-05-02 14:41 ..
drwxr-xr-x  2 espo2 espo2 4096 2007-04-27 15:28 Ex Libris
drwxr-xr-x  2 espo2 espo2 4096 2007-05-02 13:37 Resume & Job

I run feisty on a laptop "made" for WinXP.  Due to the keyboard shortcut manager, the Windows icon key on the keyboard (between 'ctrl' and 'alt') now serves the totally useful function of bringing up the terminal window!

I also tried ls -la *.tar from the root directory, with no results.  Perhaps I didn't properly download the file.

Thank you for your help!!!

---

### Post by taurus on 2007-05-02
Try this from a terminal.

```
sudo find / -name *.tar* -print
```

---

### Post by octoberdan on 2007-05-02
> **Aegis said:**
> I only wish it was on the desktop.  I intend to make the desktop my default destination in the future.  I ran the list command in a terminal window, and I see only the parent directories and two folders which I have on the desktop, as follows

total 16
drwxr-xr-x  4 espo2 espo2 4096 2007-04-27 15:28 .
drwxr-xr-x 32 espo2 espo2 4096 2007-05-02 14:41 ..
drwxr-xr-x  2 espo2 espo2 4096 2007-04-27 15:28 Ex Libris
drwxr-xr-x  2 espo2 espo2 4096 2007-05-02 13:37 Resume & Job

I run feisty on a laptop "made" for WinXP.  Due to the keyboard shortcut manager, the Windows icon key on the keyboard (between 'ctrl' and 'alt') now serves the totally useful function of bringing up the terminal window!

I also tried ls -la *.tar from the root directory, with no results.  Perhaps I didn't properly download the file.

Thank you for your help!!!

if you just ls -la *.tar from the root directory, it wont list files within the folders listed, that's the purpose of find.
Try 
```

cd /
sudo find -iname '*.tar' -mtime -1

```
"1" is within how many days the file was last modified. If it was a few days ago then try 2 or 3 or something.

Perhaps it was a .tar.gz file? Experiment! 

Suggested reading: [http://wooledge.org/mywiki/UsingFind](http://wooledge.org/mywiki/UsingFind)

---

### Post by octoberdan on 2007-05-02
Oh! And if you're on firefox, try Cntrl+Y and see if it is listed

---

### Post by sailor2001 on 2007-05-02
try this:  places/home  ctrl/h

---

### Post by Aegis on 2007-05-02
Scripts! Pipes!  

You fine people have shown me how rusty I am from my days of scripting in Unix System V !!!

Both were fine suggestions, and make me think that the file which I thought I downloaded, I uh, didn't.  No worries.

Is there a way to make the desktop the default download destination?  (I don't think even I could lose a file on the desktop, though the proverbial jury is still out on that one...)

Thank you for your help!!!

---

### Post by Aegis on 2007-05-02
J00 guys r0><><0r!  :guitar: 

Didn't even think of looking in Firefox!

I will indeed experiment, now that I know that which I seek!

---

