---
title: "Installed apps, where do they go?"
date: 2006-01-18
forum: Absolute Beginner Talk
---

### Post by Quinch on 2006-01-18
By now I think I know how to install packages via Synaptic, except... I have no idea where the files go, what to run or where the help files are, let alone choose the installation location myself....

---

### Post by 23meg on 2006-01-18
To see where files from an installed package go, go into its properties in Synaptic and check out the "Installed files" tab.

---

### Post by Quinch on 2006-01-18
But there's dozens of them! {specific case in point, Wine}

And it's all Geek to me...

---

### Post by 23meg on 2006-01-18
Then maybe if I know why you want to know where installed files go, I can help you better. What exactly are you trying to do?

If you want to run an app you've installed, see if it's put an icon in your menu. If you feel it should and it doesn't seem to have, refresh your Gnome panel with ```
killall gnome-panel
```and see if it appears. If it doesn't, hit alt+f2 and type the name of the app (sometimes package names don't exactly match executable names but auto completion will help you; just start typing).

If you want to get help, type "man" followed by the name of the app. For example ```
man wine
```

---

### Post by Quinch on 2006-01-18
[QUOTE=23meg]Then maybe if I know why you want to know where installed files go, I can help you better. What exactly are you trying to do?[/QUOTE]

Mostly trying to glean some insight into what happens after I click the install button, as well as trying to find out if there's a way to install software into non-default folders for ease of access and organization.

On the other hand, thanks for the MAN hint; by the way, is there a list of "essential commands" one should get familiar with before attempting anything else?

---

### Post by lha on 2006-01-18
[QUOTE=Quinch]Mostly trying to glean some insight into what happens after I click the install button, as well as trying to find out if there's a way to install software into non-default folders for ease of access and organization.

On the other hand, thanks for the MAN hint; by the way, is there a list of "essential commands" one should get familiar with before attempting anything else?[/QUOTE]

Ok, try
```
dpkg-query --listfiles wine
```. This tells you what files belong to package wine. You can also find this information in Synaptic. First, select a package and then click Properties. Under Installed Files-tab is a list of files that are installed on your system. IMHO, there's no need to reorganize files that are installed from packages. It would makes things more complicated. If you want to ease access to some files, you can make symlinks (powerful shortcuts) to your home folder or its subdirectories using ln with -s option. (Of course, you can make symlinks wherever you want to, but I like to keep my filesystem organized.)

Don't know what you mean with essential commands, but there a thread called [Terminal for Beginners]("http://ubuntuforums.org/showthread.php?t=73885") that might interest you.

---

### Post by 23meg on 2006-01-18
[QUOTE=Quinch] 
On the other hand, thanks for the MAN hint; by the way, is there a list of "essential commands" one should get familiar with before attempting anything else?[/QUOTE]
[https://wiki.ubuntu.com/BasicCommands](https://wiki.ubuntu.com/BasicCommands)
[http://www.ss64.com/bash/index.html](http://www.ss64.com/bash/index.html)
[http:///www.linuxcommand.org](http:///www.linuxcommand.org)

---

