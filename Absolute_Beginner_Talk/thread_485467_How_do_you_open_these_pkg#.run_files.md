---
title: "How do you open these pkg#.run files?"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by SquallLeonE on 2007-06-26
Alright, so I downloaded a file that ends in "pkg1.run", and whenever I try to open it, it says "gedit has not been able to detect the character coding.  Please check that you are not trying to open a binary file.  Select a character coding from the menu and try again."  Then it gives me two options to choose from, Current Locale and Western.

How do I open these files?

---

### Post by aktiwers on 2007-06-26
Will this open it?
```
./filename.pkg1.run
```
in Terminal..

or this:
```
sh /filename.pkg1.run
```
in Terminal..

??

---

### Post by Seisen on 2007-06-26
You have to run it in the terminal.

```
sudo ./nameoffile
```

---

### Post by yabbadabbadont on 2007-06-26
Edit: I give up.  I'm just too slow tonight.  :lol:

---

### Post by SquallLeonE on 2007-06-26
No.  For your first one, I got this once I entered it:  
bash: ./NVIDIA-Linux-x86-100.14.11-pkg1.run: No such file or directory

For your second one, I got:
sh: Can't open /NVIDIA-Linux-x86-100.14.11-pkg1.run

EDIT:  This be a response to aktiwers

---

### Post by yabbadabbadont on 2007-06-26
The nvidia drivers are already in the linux-restricted-modules packages.  Is there a reason why you aren't using them instead?

---

### Post by SquallLeonE on 2007-06-26
> **yabbadabbadont said:**
> The nvidia drivers are already in the linux-restricted-modules packages.  Is there a reason why you aren't using them instead?How do I get them?  Are they already installed?  Right now, I can't select a resolution higher than 800 x 600, but last time I had Ubuntu, I could.

---

### Post by aktiwers on 2007-06-26
> **SquallLeonE said:**
> No.  For your first one, I got this once I entered it:  
bash: ./NVIDIA-Linux-x86-100.14.11-pkg1.run: No such file or directory

For your second one, I got:
sh: Can't open /NVIDIA-Linux-x86-100.14.11-pkg1.run

EDIT:  This be a response to aktiwers

Did you "cd" yourself into the folder the file is in?

Also I forgot you need a sudo infront of this commands.

so its:

   ```
  sudo ./filename.pkg1.run 
```
or

```
      sudo sh /filename.pkg1.run 
```
 But yabbadabbadont is right..  if you go to System=>Restricted Driver Manager
And enable the nVidia drivers, wont that work for you?

---

### Post by yabbadabbadont on 2007-06-26
What is the output when you run, in a terminal window: ```
uname -a
```

---

### Post by SquallLeonE on 2007-06-26
Oh...  Thanks guys, I've been wondering for about an hour on how to get these nvidia drivers, then I came here.  I didn't know how easy it was.  :D

---

