---
title: "newb needs help plz (screwed up something...)"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by Kawasaki12 on 2007-07-31
hi, I'm new to this forum and to ubuntu.  I've had this OS for about 2 days so far...  I've searched around this forum for something that can help me with my screen resolution so i can get 1024x1240.  So I did find a thread with my exact question, and it had a code that I've tried to change the screen res

thread - [http://ubuntuforums.org/showthread.php?t=306663]("http://ubuntuforums.org/showthread.php?t=306663")
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

when I've inserted that in the terminal, i selected NVIDIA, then I finally had the option to change the res to 1024x1240.   After I did that, the thread said that i had to click <ctrl><alt><backspace>.  I did that.  I've signed back in, and I've realized that it was still 1024x768....but when i went to terminal, there is no text!  Or at least its white...I think...and whenever I open up a window (i.e. foxfire) i don't see the close, min/max buttons and theres no thing on the bottom panel that shows that a window is indeed open....plz help

thanks,
Kawasaki12

---

### Post by splintercellguy on 2007-07-31
Did you make a backup of /etc/X11/xorg.conf? If not, re-run and fall back to the VESA driver. Have you tried installing the Restricted Driver?

---

### Post by Kawasaki12 on 2007-07-31
> **splintercellguy said:**
> Did you make a backup of /etc/X11/xorg.conf? If not, re-run and fall back to the VESA driver. Have you tried installing the Restricted Driver?

i believe after i've changed the res it said something like backed-up something something....but how do I re-run and fall back to the VESA driver?  Through Synaptic Package Manager?  Thanks

---

### Post by shagster_ on 2007-07-31
try referencing this to get the drivers up to date and enabled for your NVIDIA card...

[https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia]("https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia")

otherwise, what video card do you have? and there should be a backup of /etc/X11/xorg.conf made automatically when you run dpkg-reconfigure

---

### Post by Kawasaki12 on 2007-07-31
> **shagster_ said:**
> try referencing this to get the drivers up to date and enabled for your NVIDIA card...

[https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia]("https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia")

otherwise, what video card do you have? and there should be a backup of /etc/X11/xorg.conf made automatically when you run dpkg-reconfigure

i have a Nvidia GeForce 7900 GT.  So there should be a backup of it?  Sweet!....but how am i sopost to put in that code when my terminal is blank?

---

### Post by Kawasaki12 on 2007-07-31
I've found a link to a website that has a VERY similar problem of mine with the solution!...but could it work even though my terminal is blank???
[http://linuxfud.wordpress.com/tag/terminal/]("http://linuxfud.wordpress.com/tag/terminal/")

---

### Post by Kawasaki12 on 2007-07-31
> **Kawasaki12 said:**
> I've found a link to a website that has a VERY similar problem of mine with the solution!...but could it work even though my terminal is blank???
[http://linuxfud.wordpress.com/tag/terminal/]("http://linuxfud.wordpress.com/tag/terminal/")

confirmed, and works!  Thanks for your help guys

Kawasaki12

---

### Post by shagster_ on 2007-07-31
> **Kawasaki12 said:**
> I've found a link to a website that has a VERY similar problem of mine with the solution!...but could it work even though my terminal is blank???
[http://linuxfud.wordpress.com/tag/terminal/]("http://linuxfud.wordpress.com/tag/terminal/")

Are you saying you want to set your GUI all to defaults with
```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```
?

I'm not 100% sure that would work, but you could try searching for that backup of /etc/X11/xorg.conf first....try CTRL+ALT+F1 to get to a text-only terminal and 
```
ls -l | grep xorg.conf*
```
look for any sort of backup...if its there, do
```
sudo cp /etc/X11/<backupfilename> /etc/X11/xorg.conf 
```
restart X and i think it should be fixed

---

