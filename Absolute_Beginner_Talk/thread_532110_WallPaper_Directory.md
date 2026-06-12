---
title: "WallPaper Directory"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-08-22
I'd like to add some Wallpaper files to my Ubuntu installation.
What is the directory path they are in?

Tkanks

---

### Post by deadgobby on 2007-08-22
Where did or what default file you saved your DL images too? Check your firefox preferences>main> and check where you have your default settings to. You can click on any image and have it set to wall paper. 
 Here is some link to help get around your desk top.
[http://screencasts.ubuntu.com/Customising_Ubuntu_Desktop](http://screencasts.ubuntu.com/Customising_Ubuntu_Desktop)

---

### Post by em007a on 2007-08-22
I created a folder named "Wallpaper" in my home folder. Each time I save an image I might want to use as a wallpaper I save it to that folder.

When you want to switch backgrounds, just right click on the desktop and select "Change Desktop Background". If your image is not in the list, select "Add  Wallpaper" and browse to the folder you have them stored in.

---

### Post by Orbital75 on 2007-08-22
Thanks guys but I was wanting to make the Wall Paper System wide for all
users. I'm new to linux but If i'm correct if I do as you all said no one
else will be able to choose these wallpapers correct?

---

### Post by Dr Small on 2007-08-22
Make a folder called Wallpapers somewhere on your system. Put all of your wallpapers in it. Make a symbolic link to it, and place that in every user's home folder...

(That's the way I did it).
By the way, make sure the Wallpapers folder has read permission for everyone.

Dr Small

---

### Post by brommage on 2008-05-15
> **Orbital75 said:**
> What is the directory path they are in?

Putting it in /usr/share/backgrounds will make it accessible to all users on the system.

---

