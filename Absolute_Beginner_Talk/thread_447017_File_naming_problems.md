---
title: "File naming problems"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by sequimbob on 2007-05-17
When I am trying to access files on my windows partition, it does not seem to recognize files which have a space in their name. For example, it can't find the folder "Program Files" in the Windows XP partition.  I can't rename the folder because Windows would not operate properly.  Is there a way around this problem.  I am new to Linux but can't switch over completely until I can get some of my Windows software to run under Linus using WINE.

---

### Post by tgm4883 on 2007-05-17
Do you mean that you cannot see those folders or you cannot access them?

---

### Post by taurus on 2007-05-17
```
cd "Program Files"
```
or
```
cd Program\ Files
```

---

### Post by kebes on 2007-05-17
> **sequimbob said:**
> When I am trying to access files on my windows partition, it does not seem to recognize files which have a space in their name.

Can you be more specific? What kind of access isn't working? I have lots of files and directories with spaces in the name. If you use the file browser, you can click on them, and they should open normally.

In the terminal, it's a bit more complicated. You have to either put things in quotes if they have spaces, or use "\ " instead of just " " to denote a space. However in the terminal you can also use tab to auto-complete the names of things, so if you start typing "Progr" then press tab, it will finish it as "Program\ Files" which is very convenient.


So Linux handles spaces no problem. Maybe if you describe the details of what's going wrong, we can suggest what to do...

---

### Post by Happy_Man on 2007-05-17
You can't actually run existing installed windows programs using WINE; you have to get the installer and install it again in Linux. Open up a terminal: System --> Accessories --> Terminal. then, type:
```
winecfg
```

That opens up WINE's settings manager. Make sure all your settings are OK, and then close the manager. Go download the installer you want, and put it on the Desktop. Then, type this into a terminal:
```
wine /home/<username>/Desktop/<filename of .exe>
```

That will install the program to the directory /home/<username>/.wine/drive_c. Hope this helps!

---

### Post by sequimbob on 2007-05-17
Hi Kebes
to be more specific, I was in terminal and when I tried the following commands this is what I got

bob@hp-laptop:/$ cd /media/sda1
bob@hp-laptop:/media/sda1$ cd Program Files
bash: cd: Program: No such file or directory
bob@hp-laptop:/media/sda1$ 

I then tried to put them in Quotes and it worked. Thanks for your help and to all the others who answered my post, thanks to you also.

---

### Post by heimo on 2007-05-17
> **sequimbob said:**
> I then tried to put them in Quotes and it worked. Thanks for your help and to all the others who answered my post, thanks to you also.

To speed up using command line, try using tab completion. For example, write "cd Prog" and hit tabulator. If there are no other directories which begin with Prog, it'll autocomplete the rest of the name "Program Files".

---

