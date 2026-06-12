---
title: "Deleting a folder: Access Denied"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by Fizzzy on 2008-02-01
I'm trying to delete a folder, but I keep getting a accessed denied error, i'm assuming I have to get root access in a folder.
I tried and tried, and I don't think I can get the Terminal to open a window as root, i'm hoping someone can post a command that can do something like that.
Thanks in advance! :)

---

### Post by wolfen69 on 2008-02-01
```
sudo nautilus
```
then navigate to the folder and delete

---

### Post by jpeddicord on 2008-02-01
The easiest way: Hit Alt+F2. Type in "gksu nautilus" and type in your password if prompted. You now have a root window. Be sure to close it when you are done to avoid nuking the wrong file.

And I see I have been beaten to the punch. I guess that is what happens when I'm yakking away in IRC!

---

### Post by jaytek13 on 2008-02-01
The terminal command to delete a folder with privilege would be

```

sudo rm -rf folder

```

---

### Post by conehead77 on 2008-02-01
this will delete a directory:
```
sudo rm -Rf <path to directory>
```

be very careful with the command, the deleted files cannot be restored and many people messed up their system when accidentally misspelled the path.

---

### Post by bodhi.zazen on 2008-02-01
> **Fizzzy said:**
> I'm trying to delete a folder, but I keep getting a accessed denied error, i'm assuming I have to get root access in a folder.
I tried and tried, and I don't think I can get the Terminal to open a window as root, i'm hoping someone can post a command that can do something like that.
Thanks in advance! :)

Ubuntu uses sudo for root access. Use

sudo <command>

to run a single command as root.

Use :```
sudo -i
``` for a root shell.

Use gksu for graphical apps, like, 

```
gksu nautilus
```

If you run kde, kde uses kdesu rather then gksu for graphical apps.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
	gksudo : [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by mc4man on 2008-02-01
If you use nautilus (sudo, gksudo, ect.) to delete files, folders, whatever highlight and use shift/delete on your keyboard. Otherwise you'll have to go to a hidden .trash in your root folder to actually remove from computer

---

### Post by Fizzzy on 2008-02-01
Thanks for the help, the problem is solved now :).

---

### Post by jpeddicord on 2008-02-01
> **jaytek13 said:**
> The terminal command to delete a folder with privilege would be

```

sudo rm -rf folder

```
Just a word of advice: be very careful of the rm command, even if you are sure of what you are doing. One false key and your home directory is wiped.

...because I was the idiot who did that trying to remove *.log and hit Enter too early.

---

### Post by jaytek13 on 2008-02-01
> **jacobmp92 said:**
> Just a word of advice: be very careful of the rm command, even if you are sure of what you are doing. One false key and your home directory is wiped.

...because I was the idiot who did that trying to remove *.log and hit Enter too early.

Yeah, that's true. There isn't a "are you sure?" prompt with the rm command, and the command doesn't send it to a trash bin, it just deletes it basically for good. Might be a good idea to stick with the GUI.

---

### Post by PeterJS on 2008-02-02
> **jaytek13 said:**
> Yeah, that's true. There isn't a "are you sure?" prompt with the rm command, and the command doesn't send it to a trash bin, it just deletes it basically for good. Might be a good idea to stick with the GUI.

you can use:
```

rm -ri somedir

```

The f in rm -rf stands for force and tells rm not to ask about anything. The other option is i for interactive, but with that it asks for each and every file. There's not really any middle ground that I know of.

---

