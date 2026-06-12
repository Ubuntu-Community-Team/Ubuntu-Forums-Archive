---
title: "Software for XP to See Ubuntu OS"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by Mac70 on 2006-12-18
Is there a download I can use so I can make XP see the ubuntu OS? I need to make it the default OS for the wife but dont want to mess around with boot.ini.:-k

---

### Post by Ecthelion on 2006-12-18
How do you mean?

Do you mean accessing the ubuntu harddisks on xp?

Do you mean changing the default startup option?
(So that grub chooses to start xp instead of ubuntu)

...

---

### Post by Mac70 on 2006-12-18
The latter. Ill be the only one using Ubuntu so it should be the last choice and booting into XP automatic.

---

### Post by groggyboy on 2006-12-18
Provided Ubuntu is already installed, you wanna edit the GRUB boot menu.  I just posted to another thread about the same issue.  [Check it out]("http://www.ubuntuforums.org/showthread.php?p=1902864#post1902864").

---

### Post by Mac70 on 2006-12-18
Ill give that a try and let you know.

---

### Post by slibuntu on 2006-12-18
There is a script called GrubEd which evenn gives you a GUI for changing settings like this, heres the [link]("http://ubuntuforums.org/showthread.php?t=228104")

---

### Post by Mac70 on 2006-12-18
As I still have no Net connection Ill have to download that into Windows and burn onto CD wont I?(Thats another issue for later)
I tried typing that "ghsu gedit" etc but all I got was command not found, a common thing when I had this on the virtual machine.Have I got a bad installation or something?

---

### Post by ciscosurfer on 2006-12-18
> **Mac70 said:**
> As I still have no Net connection Ill have to download that into Windows and burn onto CD wont I?(Thats another issue for later)
I tried typing that "ghsu gedit" etc but all I got was command not found, a common thing when I had this on the virtual machine.Have I got a bad installation or something?The correct command is```
gksu gedit /boot/grub/menu.lst
```You can do this from a Terminal command line, or you can hit ALT-F2 and enter it in there.  Then modify the default kernel to boot to.

GrubEd is a Linux app not a Windows app.  It's run natively in Ubuntu (and will not run in Windows) -- it allow you to graphically change your default boot OS graphically via a GUI.

---

### Post by reiatzu on 2006-12-18
[http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm](http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm)

You can mount your ubuntu partition and any ext partition in windows, with rw ability. Check it out

---

### Post by Mac70 on 2006-12-18
Thats the command I put in. I put it exactly like that but am I supposed to put sudo in front of everything?:confused: 
And this would be easier if I could connect to the Net but thats not happening either from Ubuntu.

---

### Post by Mac70 on 2006-12-18
Success.:D 
I went into the home folder and then File System and there is a grub folder in there with a menu list.Can I edit it in there?

---

### Post by Ecthelion on 2006-12-18
You can't edit it just like that...
You have to be root.

Easiest is to do

```
sudo gedit /boot/grub/menu.lst
```

and adapt it...

---

### Post by Mac70 on 2006-12-18
That worked!\\:D/ 
I changed the default to 3 which puts me on "other operating systems" so assuming each number corresponds to each line the number I want is 4?
Now I have to figure out how to get the internet working.Ill search around first.But one last question, is there a guide on all the mostly used command lines?

---

