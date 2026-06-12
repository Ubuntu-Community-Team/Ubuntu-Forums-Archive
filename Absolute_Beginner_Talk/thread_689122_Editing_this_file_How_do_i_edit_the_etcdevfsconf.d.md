---
title: "Editing this file How do i edit the /etc/devfs/conf.d/nvidia-kernel-nkc"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by ibizatunes on 2008-02-06
How do i edit the 
/etc/devfs/conf.d/nvidia-kernel-nkc

---

### Post by talsemgeest on 2008-02-06
Type ```
gksudo gedit /etc/devfs/conf.d/nvidia-kernel-nkc
``` and then enter you administrator password.

Hope I've helped :)

---

### Post by ibizatunes on 2008-02-06
Thanks, will give that a try when i get home from work

---

### Post by Kevbert on 2008-02-06
sudo gedit /etc/devfs/conf.d/nvidia-kernel-nkc

What do you want to do ?
[forum.compiz-fusion.org/archive/index.php/t-561.html]("forum.compiz-fusion.org/archive/index.php/t-561.html")
[http://ubuntuforums.org/archive/index.php/t-215551.html]("http://ubuntuforums.org/archive/index.php/t-215551.html")

---

### Post by ibizatunes on 2008-02-06
Re: Help with Picasa 

i have the error......
/dev/nvidia0 or /dev/nvidiact1 are not accessable. Picasa will crash if these files are not accessable. To fix this, as root, please run:

chmod 666 /dev/nvidia0 /dev/nvidiact1


--------------------------------------------------------------------------------


Tried running the below from a terminal:

sudo chmod 666 /dev/nvidia0
sudo chmod 666 /dev/nvidiactl 
 

Works untill FINE till i reboot the workstation, then the permission the screw up again

 so i found this fix on
[http://ubuntuforums.org/showthread.php?p=4278628#post4278628](http://ubuntuforums.org/showthread.php?p=4278628#post4278628)

----------------------------

"I edited 
Code:
/etc/devfs/conf.d/nvidia-kernel-nkcand changed the "0660" to "0666" on both lines.

Probably not the best solution but it works for me."

I need to try and get picasa working and i found that this MAY fix my issue, as there is a permission problem......

--------------------------------------------------------------------------------

---

### Post by ibizatunes on 2008-02-06
If not i will have to wipe the work station, something i really dont want 2 do!!
So any help would be usefull

---

### Post by talsemgeest on 2008-02-06
BTW my suggestion will only work if the file is a text file...

---

### Post by ibizatunes on 2008-02-06
Is it a text file, i dont no?!
Can i edit this file in GUI?

---

### Post by talsemgeest on 2008-02-06
Type my command in and it will open in a GUI.

Oh wait, I will just make an edit to that command...

---

### Post by talsemgeest on 2008-02-06
There, done. Well most files are text files, so it should work. If not, it won't do you any harm trying

---

