---
title: "No .wine folder"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by jack3 on 2007-04-13
I was doing the how to get Photoshop CS2 working with Wine. It tells me to go to the .wine folder under the home/name//what ever. I have tried to install wine via terminal and sudo or even the automatix. 

But I can't find wine any where under applications or anything.

Any Idea?

Jack

---

### Post by taurus on 2007-04-13
Applications -> Accessories -> Terminal
```
cd ~/.wine
ls -la
```

---

### Post by jack3 on 2007-04-14
> **taurus said:**
> Applications -> Accessories -> Terminal
```
cd ~/.wine
ls -la
```

Hmm... I ran the first one and it said no such file or directory and the second one just shows a list of directories.

Whats it supposed to do?

Jack

---

### Post by ajmorris on 2007-04-14
> **jack3 said:**
> Hmm... I ran the first one and it said no such file or directory and the second one just shows a list of directories.

Whats it supposed to do?

Jack

Since Taurus is now offline i'll answer for him :)

if you have installed wine.... in your home directory (~ is short hand for the current users home directory)

and hence cd ~/.wine should go into that directory. (.wine is created automatically when wine is installed so check it is actually installed through Synaptic ( System >> Administration >> Synaptic Package manager))

as for ls -la....
ls is the shell command to display the folders contents. ls -l shows the permission of the directories contents and ls -a shows hidden folders and hence ls -la shows both.

(also directories with a '.' infront of their name are hidden folders) if you are using a GUI based file manager (such as nautilus) to display folders, ctrl+h shows hidden files and folders

Hope that helps.

---

### Post by david_kt on 2007-04-14
> **jack3 said:**
> 
But I can't find wine any where under applications or anything.

Any Idea?

Jack

It is because it is not yet created. To create it, just run whatever program with wine, or you could run wine configuration:

```
winecfg
```

After that, just exit winecfg, your .wine has already created.

DK

---

### Post by jack3 on 2007-04-15
Thanks David! That got that part taken care of... But I did the tutorial at:

[http://blog.publicidadpixelada.com/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps/](http://blog.publicidadpixelada.com/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps/)

And at the end it tells you to type:

> sudo wine –winver winxp “[path to Photoshop]/photoshop.exe” 

I get this out come:

```
jack3@Jack:~$ sudo wine –winver winxp /home/jack3/.wine/drive_c/Program Files/Adobe Photoshop CS2/photoshop.exe
wine: could not load L"c:\\windows\\system32\\\2013winver.exe": Module not found

```

Any idea?

Thanks,

Jack

---

### Post by david_kt on 2007-04-15
I have checked the tutorial, I think you should not follow it.

First, never run "sudo wine".
Second, what I know, you could not use "-winver" now. Instead, run 

```
winecfg
```

click add application, and navigate to photoshops.exe.
After that, while photoshops.exe still highlighted, change the

What you could do instead
wine –winver winxp “[path to Photoshop]/photoshop.exe” change the windows version from "Use global settings" to "windows XP". After that click apply and apply and then ok (you are back in terminal), and type this:

```
wine “[path to Photoshop]/photoshop.exe”
```

DK

---

