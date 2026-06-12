---
title: "tileracer"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by dylondadank on 2007-11-07
i tried installing the game and a window appeared, it reads

Could not open the file /tmp/TileRacer0.6_Setup.sh using the Unicode (UTF-8) character coding.
gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

is there an easier way to install it?

---

### Post by Maestro23 on 2007-11-07
> **dylondadank said:**
> i tried installing the game and a window appeared, it reads

Could not open the file /tmp/TileRacer0.6_Setup.sh using the Unicode (UTF-8) character coding.

is there an easier way to install it?

What commands did you use to try and install? Got a link to the download?

---

### Post by dylondadank on 2007-11-07
> **Maestro23 said:**
> What commands did you use to try and install? Got a link to the download?

[http://tileracer.model-view.com/tl/index.php/downloads.html](http://tileracer.model-view.com/tl/index.php/downloads.html)

---

### Post by Maestro23 on 2007-11-07
> **dylondadank said:**
> [http://tileracer.model-view.com/tl/index.php/downloads.html](http://tileracer.model-view.com/tl/index.php/downloads.html)

If the file is a .sh file then:  Copy the file to your /home/username directory as the download page suggesed.

Then, in a terminal:

> sudo chmod + x filename.sh (makes it executable)

./filename.sh **or** sh filename.sh

*If the file is on your Desktop and you want to copy it to your /home directory:
> 
cd ~/Desktop
ls (should see the file)

cp filename.sh /home/username

Hope that sheds some light.:)

---

