---
title: "moving folders to install program"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by myotis on 2008-04-02
I am trying to install LightZone, which "I think" seems to only require a folder of files to be copied into an appropriate place.

I have extracted the folder of files from the downloaded tar file called Lightzone onto the desktop.

Firstly I'm not sure where I should put this folder.  does it just get copied as a folder into  /usr/bin?

I know this is obvious to everyone but me, but I would appreciate the confirmation.

The other issue is that it doesn't appear that the GUI will let me move this folder anywhere. I am assuming I need to use the terminal and sudo to do the actual moving.

So would I open the terminal and type

sudo "my password" root

cd desktop

mv LightZone /usr/bin

sudo "my password" -1 root

Thanks ,

Graham

---

### Post by taavikko on 2008-04-02
extract the folder in desktop, inside you'll find README file or INSTALL read those!

---

### Post by Joeb454 on 2008-04-02
You cannot move folders :) and that is not how you become root in a terminal :)

And I agree with taavikko, there will most likely be an install or readme file in the extracted folder :)

---

### Post by lswest on 2008-04-02
well to move things you would need to do:
```
cd [place where files are such as Desktop/LightZone]
sudo mkdir [destination folder]/LightZone
sudo mv * [destination folder]/LightZone
``` which will move all the files from one folder to another of the same name (which is why i added LightZone on the end) but yes, read the How-To or readme file first, since this is not how you install programs.  Installing it would usually consist of ```
cd [folder]
./configure
make
sudo make install
``` but it may differ for the program you're trying to install.

---

### Post by myotis on 2008-04-02
Thanks to everyone, there is no readme or install file in the folders. I had already checked that, but there is a script file called "lightzone" that runs the program from the extracted folder on the desktop. Using the script file to run the program is all that is mentioned on the LightZone help forum.

So I assumed it didn't need installed as such, just moved somewhere sensible. 

I now see that I misread the bit in my Ubuntu book about getting into root so I assume I need to follow the instructions

cd Desktop/LightZone
sudo mkdir usr/bin/LightZone
sudo mv * usr/bin/LightZone

but I'm still not sure if this is the best place to move the folder to.

Graham

---

### Post by lswest on 2008-04-02
well, you could just move the folder to your home folder, then create a launcher to the script, or write a script to launch the script (sounds funny, i know, but i do it with Java apps)

---

### Post by myotis on 2008-04-02
>well, you could just move the folder to your home folder, then create a launcher to the script, or >write a script to launch the script (sounds funny, i know, but i do it with Java apps)

Yes, I have already done (part of this) but feel uncomfrotable with it being in my home directory which I think of as being data rather than programs.

Am I misunderstanding the usr/bin directory and is there no logic in it going there.

Thanks,

Graham

---

### Post by lswest on 2008-04-02
Well, if there is no install to put it in /usr/bin, i'd prefer to leave it wherever it is, because technically, from your description, the file is a **script** and not a **executable** (basically a binary file run like a .exe from windows).  So...if it helps, think of it as a coding example.  But yes, i would prefer it in a Home folder, just so a) you can find it again b) it doesn't get permissions it's not meant to have and c) so you don't run it with permissions it's not meant to have.  It's best to right-click your panel click "add to panel" then "custom launcher" and to browse to the script you want to have, or choose "run in terminal" and input the command you're using to run it.

---

### Post by myotis on 2008-04-02
>Well, if there is no install to put it in /usr/bin, i'd prefer to leave it wherever it is, because technically, from your description, the file is a script and not a executable (basically a binary file run like a .exe from windows).

OK as, you say it will be easy to find, but there are dozens of files in the LightZone folder, the script just launches the program, which seems to be written in Java.

But I can see the logic of it sitting in the Home directory.

Thanks for the advice.

Graham

---

### Post by lswest on 2008-04-02
No problem, it's just my personal opinion though.  However, if you stuck the script in /usr/bin, you'd run it with root permissions (since otherwise you would have no access) and that might end up causing it to do something else, and when running things with root permissions your ~ is /root (i believe) which can lead to more issues.

---

### Post by myotis on 2008-04-02
> **lswest said:**
> No problem, it's just my personal opinion though.  However, if you stuck the script in /usr/bin, you'd run it with root permissions (since otherwise you would have no access) and that might end up causing it to do something else, and when running things with root permissions your ~ is /root (i believe) which can lead to more issues.

Well, its now in my home directory and added to the graphics menu for launching it.  I assume that once it comes out of beta and becomes a paid for product as the Mac and Windows versions are, it will have a proper install, with support available.

Graham

---

