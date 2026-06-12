---
title: "[SOLVED] how to change my default OS"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by saurabh srivastava on 2008-01-10
my default is ubuntu when i start up my laptop there is six option 
first 4(two generic two recovery) are ubuntu and last two are windows(one recovery mode)
ubuntu is my default it automatically start in few seconds  how can i change my default to windows. 
please help me....:(

---

### Post by iris-n on 2008-01-10
You have to edit your grub menu.

Type: ```
sudo nano /boot/grub/menu.lst
```

In your terminal to open it. Right in the beginning, there's a line

default 0

That's your default startup. You have to change the 0 (first position) to the position of your windows system in the grub, seems to me it's 4.

---

### Post by saurabh srivastava on 2008-01-10
thnx sir ..u r gr8

---

### Post by esteckis on 2008-01-10
Or you can use the startup manager that lets you configure in Ubuntu which OS will be the default loader. It is in the Synaptics package manager.

---

### Post by changes on 2008-01-10
I'm not able to save after edit this from the terminal, no such option.
Tried to browse for the file /boot/grub/menu.lst
But when I try to save, i got an error saying I don't have permission.. 
Perhaps I have to log in as Root, but How do I do that?
I have tried to log in as root at the welcome screen, but then I get an error saying; You can not log in as your administrator from here.. 
Any Idèas?

Want to set windows as default boot option

---

### Post by taurus on 2008-01-10
> **changes said:**
> I'm not able to save after edit this from the terminal, no such option.
Tried to browse for the file /boot/grub/menu.lst
But when I try to save, i got an error saying I don't have permission.. 
Perhaps I have to log in as Root, but How do I do that?
I have tried to log in as root at the welcome screen, but then I get an error saying; You can not log in as your administrator from here.. 
Any Idèas?

Want to set windows as default boot option

Applications -> Accessories -> Terminal
```
**gksudo** gedit /boot/grub/menu.lst
```

---

### Post by jrharvey on 2008-01-10
I would use the startup manager in synaptic because messing around with text really makes things worrisome because you can always have a typo. The startup manager also allows you to configure other things such as grub images and does it in a nice little GUI.

---

### Post by changes on 2008-01-10
> **taurus said:**
> Applications -> Accessories -> Terminal
```
**gksudo** gedit /boot/grub/menu.lst
```

Thx, worked fine

---

### Post by changes on 2008-01-10
> **jrharvey said:**
> I would use the startup manager in synaptic because messing around with text really makes things worrisome because you can always have a typo. The startup manager also allows you to configure other things such as grub images and does it in a nice little GUI.

I have solved the problem, but since I am n00b in linux/ubuntu I have to ask how i enter the startup manager?

---

### Post by esteckis on 2008-01-11
You download the startup manager from the synaptics repo. Once it is installed, it should be under your administration menu I believe.   Here is a link for startup manager

[http://web.telia.com/~u88005282/sum/index.html]("http://web.telia.com/~u88005282/sum/index.html")

---

