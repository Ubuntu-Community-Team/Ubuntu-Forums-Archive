---
title: "How to move folder from desktop to /boot/grub directory"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by muggins on 2007-06-15
I have downloaded some splash images for grub to my desktop but don't know how to get them into my /boot/grub directory. When I try to drag it into the folder it falls back onto the desktop.

---

### Post by mikewhatever on 2007-06-15
You need admin permissions to copy things into /boot/grub. Try the following
> sudo cp /home/Desktop/the_folder_name /boot/grub

---

### Post by Bachstelze on 2007-06-15
```
sudo mv ~/Desktop/filename /boot/grub
```

---

### Post by jargoman on 2007-06-15
I've never bothered changing my boot slpash so I don't know how to do it. I do know that you can't copy to /boot/grub as a regular user. You need root privelages. Ubuntu has no root so you have to use sudo in terminal like this

$ sudo cp -r ~/Desktop/splash_folder /boot/grub

wow I was beat to the punch lol

If you want to copy a whole folder though use the -r after cp

---

### Post by candtalan on 2007-06-15
Basically you will need to do an action or two after giving yourself superuser permissions (admin level) because the admin level files are protected.

What you want to do can be done in a terminal (looks like a dos screen but it isnt) by typing in the command sudo (followed by commands for what you want to do)

hope that gives an idea about it.

example 
sudo cp /home/user/desktop/splashfile /boot/grub/newsplashfilename

have a look at linux copy command on a search engine google? to see a bit more background?

If you do not want to loose existing file by being over written, copy it to a newname first.

take it gently.

---

### Post by muggins on 2007-06-15
Thanks for the replies, folder is now in /boot/grub.

---

