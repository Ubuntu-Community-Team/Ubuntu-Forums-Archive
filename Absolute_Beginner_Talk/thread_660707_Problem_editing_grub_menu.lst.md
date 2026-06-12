---
title: "Problem editing grub menu.lst"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by Withadee on 2008-01-07
I have a dual boot system (Windows XP/ Ubuntu 7.04) and I'm trying to change the grub default to windows.  The Start up Manager does not appear in the  Administration drop down list.  I don't know how to begin to edit this file.  When I try to edit the file in the text editor, it won't let me save the changes because the file is a read only file.  How do I edit this file?

Withadee

---

### Post by erginemr on 2008-01-07
Hello,

You need to have root privileges to be able to edit this file. To get it, you need to write down:
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by mdewet on 2008-01-07
Me too, try opening a teminal and using 
```

sudo gedit /filename
 
```

---

### Post by erginemr on 2008-01-07
> **mdewet said:**
> Me too, try opening a teminal and using 
```

sudo gedit /filename
 
```

Avoid using sudo with graphical applications, use "gksudo" or "gksu" instead. Most of the time, you won't run into any trouble, but I have once run into a big trouble, unable to boot into Gnome after using "sudo" with a graphical application.

---

### Post by erginemr on 2008-01-07
> **Withadee said:**
> I have a dual boot system (Windows XP/ Ubuntu 7.04) and I'm trying to change 

the grub default to windows.  The Start up Manager does not appear in the  Administration drop down 

list.  I don't know how to begin to edit this file.  When I try to edit the file in the text editor, it 

won't let me save the changes because the file is a read only file.  How do I edit this file?

Withadee

Once you open the file with enough permissions, you need to find the line
```
Default   0
```

There are chunks of lines down the file, which are not commmented out with #'s, with each chunk 

corresponding to an operating system in your computer. You should count those chunks starting with 0, 

and change the above line accordingly. The final one should be for Windows.

Besides, the line
```
Timeout   0
```

corresponds to the waiting time in seconds, before the active selection in the Grub menu is processed. A waiting time of 5 seconds would be a reasonable value.

---

### Post by hyper_ch on 2008-01-07
You are normally only allowed to alter files/directories in your home folder. For everthing else you need additional powers:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Withadee on 2008-01-08
Thank you.  That command got me the privileges I needed.  The default line did not appear in the file so I added it at the beginning of the file and set it to the Windows OS.  It works just fine now. I am curious about the "gk" preceding the "sudo" command.  What does it stand for?  As the menu.lst appears on the screen as text only (no graphics) was the gk necessary?

Withadee

---

### Post by bodhi.zazen on 2008-01-08
gksudo : [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by erginemr on 2008-01-08
> **Withadee said:**
> Thank you.  That command got me the privileges I needed.  The default line did not appear in the file so I added it at the beginning of the file and set it to the Windows OS.  It works just fine now. I am curious about the "gk" preceding the "sudo" command.  What does it stand for?  As the menu.lst appears on the screen as text only (no graphics) was the gk necessary?

Withadee

You are welcome. In addition to the above link by bodhi.zazen, you need gksudo to run "gedit", Gnome Editor, which is a Gnome application. If you use a text-only editor instead, such as vim (which is my favorite by the way), you can do:
```
sudo vim /boot/grub/menu.lst
```

Have Fun!

---

### Post by erfahren on 2008-01-08
> 
There are chunks of lines down the file, which are not commmented out with #'s, with each chunk 

corresponding to an operating system in your computer. You should count those chunks starting with 0, 

and change the above line accordingly. The final one should be for Windows.

it's actually easier to count the non-commented "titles"

for an excellent guide on editing menu.lst see: [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

