---
title: "Editing a shell script"
date: 2005-11-23
forum: Absolute Beginner Talk
---

### Post by Steve00 on 2005-11-23
I have succesfully installed Ubuntu on an HPtc1100 tablet and am now in full linux learning mode. I tried installing mondorescue. After nosing around on the forums here, I found that there is a typo in the mindi shell script file that needs to be corrected. However, when I try to open mindi using the text editor it will only open as read only.  The file is a shell script -- the fix appears to be simple, but I cannot figure out how to open the file in order to make the correction and then save the changes.

How do I properly edit this file?

Thanks for any help!

---

### Post by 23meg on 2005-11-23
Append "sudo" as a prefix to the command you use to open it.

[http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo)

---

### Post by ctcecil on 2005-11-23
[QUOTE=Steve00]I have succesfully installed Ubuntu on an HPtc1100 tablet and am now in full linux learning mode. I tried installing mondorescue. After nosing around on the forums here, I found that there is a typo in the mindi shell script file that needs to be corrected. However, when I try to open mindi using the text editor it will only open as read only.  The file is a shell script -- the fix appears to be simple, but I cannot figure out how to open the file in order to make the correction and then save the changes.

How do I properly edit this file?

Thanks for any help![/QUOTE]

Open up your Terminal. (Application > System Tools > Terminal)
lets say the file is /home/<your username>/file.ext

in your terminal type
sudo gedit /home/<your username>/file.ext

it will ask for your password, then open the file.

---

### Post by Steve00 on 2005-11-23
Thanks! That did it!

Now, if I can just get Mondo and Mindi to cooperate.....

---

