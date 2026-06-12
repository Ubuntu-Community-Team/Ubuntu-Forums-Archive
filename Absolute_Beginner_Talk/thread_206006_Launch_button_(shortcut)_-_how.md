---
title: "Launch button (shortcut) - how"
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by Optiker on 2006-06-29
Im' running Kubuntu Dapper 6.06. I have learned how to add a new aplet or application to the panel, but, how do I add a launch button (shortcut in Windows) to the panel, and/or to the KMenu, and/or to the desktop, when to launch it from teh command line I run a run script  in the app folder?

More specifically, from the command line, I navigate to the app folder and type ./run. The app is a jaqva app, and the run script looks like this:
-------------------------
***./jre/bin/java -mx1024m -cp ij.jar ij.ImageJ***
-------------------------
A pointer to help would be great, or even better, simple instructions for a beginner.

Thanks!
Optiker

---

### Post by christhemonkey on 2006-06-29
```
/path/to/java/program/thing/jre/bin/java -mx1024m -cp ij.jar ij.ImageJ 
```

Something like that, obivously replacing /path/to/java/program/thing/ with the actual path.

---

### Post by Optiker on 2006-06-29
[QUOTE=christhemonkey]```
/path/to/java/program/thing/jre/bin/java -mx1024m -cp ij.jar ij.ImageJ 
```

Something like that, obivously replacing /path/to/java/program/thing/ with the actual path.[/QUOTE]
Hmmm...guess I'm too inexperienced to follow! Where do I do this - command line? What is the result - an icon on the desktop, item in the KMenu, other?

Thanks!
Optiker

---

### Post by christhemonkey on 2006-06-29
Very sorry i wasnt clearer, have never used kde, so dont know the specifics.

But likely you can right click on the panel and select "add launcher" or something.
Then select custom launcher (again not sure if this is right) and 
> /path/to/java/program/thing/jre/bin/java -mx1024m -cp ij.jar ij.ImageJ 
is what you want it to do as you click it.


This is apparently how to add launchers to panel:
> Main Menu => Configure Panel =>  Add => Button

---

### Post by Optiker on 2006-06-29
Chris...finally got there on my own...right-click on the K-icon and select "Edit K Menu". Can add shortcuts into the K-Menu form there. However...

I appear to have a problem anyhow that will need some help - probably in a different venue.

My ImageJ installation included a java runtime environment, so by giving the path to the java executable as /usr/local/bin/ImageJ/jre/java, it isn't working. When I searched for the jre folder, it turned up a couple of locations and I suspect that's the problem - redundant jre locations.

If you have a solution, I'd be happy to try it, but in the meantime will ask elsewhere.

Thanks!
Optiker

---

### Post by venik212 on 2007-02-06
I realize this is a very old thread, but I have the exact same problem, so if someone could tell me how to run ImageJ from Kubuntu (it ran fine under Gnome, Ubuntu 6.10), it will be greatly appreciated.

---

### Post by Deichgraf on 2007-06-14
Hi, 
I have found the solution for starting ImageJ from desktop icon shortcut. Suppose the ImageJ file system is in your local user path in Downloads/ImageJ then the correct shortcut would be:

Downloads/ImageJ/jre/bin/java -mx1024m -cp Downloads/ImageJ/ij.jar ij.ImageJ

I have a problem with ImageJ because the print dialog of ImageJ is always telling that there are no print jobs available. However printing from other applications like OpenOffice, Evolution etc. is no problem. My printers are not locally connected but part of the LAN and are connected to the Ubuntu PC via cups.

Does anybody know a work-around?

Regards

Christian

---

