---
title: "xorg.conf edit gone wrong"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by Prophion on 2007-02-06
So....
I plunged into the adventure called (K)Ubuntu and immediately dived head first into trouble. After installing the OS and some extra programs, I decided I was ready for something bigger. I wanted my logitech mx500 to run properly (read use all buttons)

So I searched the forums and found this very clear guide:
[http://www.ubuntuforums.org/showthread.php?t=65471&highlight=logitech+mx500](http://www.ubuntuforums.org/showthread.php?t=65471&highlight=logitech+mx500)

I followed the instructions spot on (at least i thought so) and get to the point where i have to restart X. But it doesnt restart... 
No worries: I wrote down the recovery part:

> Don't restart X yet! Just before we do I have to warn you if you made a mistake in the xorg file X will not restart. But don't worry that's why we only commented out the previous settings and didn't delete them. If X fails to restart then you will end up in a text console. Log in and type the following to edit the xorg file:
 
 
Code:
sudo nano /etc/X11/xorg.conf
 All you need to do is comment out the new section we just added by putting a "#" in front of each line and un-commenting the original section by deleting the "#" which is at the start of each line. Save the xorg file in nano by typing "CTRL + X" press "Y" to confirm the save and type "startx" to get back to your desktop and re-read section two carefully and correct your xorg file.

The only thing is: I dont see any text when I open the file. Its blank. Maybe there is an extra thing I have to do but I dont have a clue.

So please help out this newb...

---

### Post by meng on 2007-02-06
Are you sure you typed the command correctly? Remember Linux is case-sensitive. Also, I would recommend:
sudo nano -B /etc/X11/xorg.conf

(the -B creates a backup, just in case things go bad)

---

### Post by aysiu on 2007-02-06
You can also re-create the file by typing this command: ```
sudo dpkg-reconfigure xserver-xorg
```

---

