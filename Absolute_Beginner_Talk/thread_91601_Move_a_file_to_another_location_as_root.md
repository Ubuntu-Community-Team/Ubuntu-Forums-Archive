---
title: "Move a file to another location as root?"
date: 2005-11-17
forum: Absolute Beginner Talk
---

### Post by Darrin on 2005-11-17
Example: 
I have a file in my home directory and I wish to move it from the home directory to another folder in a different location. This folder requires root ownership to move it there.  Whats the command line for enabling me to doing this?
Im sure its something simple but I cant find it.

---

### Post by Chayak on 2005-11-17
[QUOTE=Darrin]Example: 
I have a file in my home directory and I wish to move it from the home directory to another folder in a different location. This folder requires root ownership to move it there.  Whats the command line for enabling me to doing this?
Im sure its something simple but I cant find it.[/QUOTE]

```
sudo mv /home/USER/FILE /<the path to where you want to move it>

ex.
sudo mv /home/me/file1 /media/usbdisk/archive/file1 
```

You can also rename a file with the mv command by just changing the destination file name.

---

### Post by canadianwriterman on 2005-11-17
If you have a lot of files that you need to work with that require root privileges, what I like to do is use the "Run as a different user" tool, open Nautilus as root and do my copying. Saves typing into the Terminal if you have a bunch to do. "Run as a different user" is under Applications>System Tools (I think... not at my Ubuntu box).

---

### Post by Darrin on 2005-11-17
[QUOTE=Chayak]```
sudo mv /home/USER/FILE /<the path to where you want to move it>

ex.
sudo mv /home/me/file1 /media/usbdisk/archive/file1 
```

You can also rename a file with the mv command by just changing the destination file name.[/QUOTE]
Thanks. Ill write that one down in my notes. I didnt realize you could change the file name that way either. Thats cool. :D

---

### Post by thomas.mcmahon on 2005-11-20
[QUOTE=canadianwriterman]If you have a lot of files that you need to work with that require root privileges, what I like to do is use the "Run as a different user" tool, open Nautilus as root and do my copying. Saves typing into the Terminal if you have a bunch to do. "Run as a different user" is under Applications>System Tools (I think... not at my Ubuntu box).[/QUOTE]

Alternatively, you can just open a terminal up normally and type "sudo -s" to get a root shell :)

---

### Post by Kyral on 2005-11-20
*points to Terminal For Beginners in his sig for almost all your Terminal related needs*

---

### Post by earobinson on 2005-11-20
[QUOTE=canadianwriterman]If you have a lot of files that you need to work with that require root privileges, what I like to do is use the "Run as a different user" tool, open Nautilus as root and do my copying. Saves typing into the Terminal if you have a bunch to do. "Run as a different user" is under Applications>System Tools (I think... not at my Ubuntu box).[/QUOTE]
This is a very good idea, you could also open up a terminal and type sudo nautilus and that will launch (after a password of cource) Nautilus with root privileges.

NOTE: as soon as you are done I would always close the window because you can break things with root and you dont want to forget that you have an open Nautilus with root privileges. It can be very easy to break things like this.

---

### Post by Darrin on 2005-11-20
[QUOTE=canadianwriterman]If you have a lot of files that you need to work with that require root privileges, what I like to do is use the "Run as a different user" tool, open Nautilus as root and do my copying. Saves typing into the Terminal if you have a bunch to do. "Run as a different user" is under Applications>System Tools (I think... not at my Ubuntu box).[/QUOTE]
What would I type in the Run box? Im not sure what the next step would be here.

---

### Post by thomas.mcmahon on 2005-11-20
I personally don't recommend this, as having a graphical root file browser means you could very easily break your system. 

However what you would do is type "nautilus" in Applications>System Tools>"Run as different user".

Be careful!

---

