---
title: "Uninstaller with a GUI interface?"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by u.b.u.n.t.u on 2006-06-12
Hi,

Some programs cannot be found in the Add/Remove or Synaptic. For situations such as this, is there any kind of GUI uninstaller?

Thanks.

---

### Post by aysiu on 2006-06-12
Can you give an example of one of these programs? Did you, by chance, compile it from source?

---

### Post by brentroos on 2006-06-12
.

---

### Post by u.b.u.n.t.u on 2006-06-12
Sorry, I downloaded a program and it installed itself but it doesn't have an uninstall. The program didn't work, it never completed the install. I tried twice.

It is residing in Applications > System tools as a link.

It is in my home directory as an empty folder.

It is in my usr/bin as a shell script.

Also in usr/local and usr/share.

Those are just the files I found searching with the name.

I guess it isn't safe to install programs outside of synaptic. I'll know better from now on lol.

---

### Post by elemental666 on 2006-06-12
aptitude may be your answer...

It does a better job of tracking dependancies and the like..

so instead of using apt-get or synaptic, make you main installer aptitude.

```

sudo aptitude install <package>

```

when it comes time to uninstall, aptitude will remove dependacies that are not being used by other packages (keeping your system much cleaner).

```

sudo aptitude remove <package name>

```

for more info see:
```
man aptitude
```
or search google for aptitude package manager

btw, if you want a pseudo gui for aptitude, type: ```
 sudo aptitude
``` and you'll get a curses based gui.

---

### Post by brentroos on 2006-06-12
.

---

### Post by u.b.u.n.t.u on 2006-06-12
Thanks elemental666, I will look up what "aptitude" is.

Thanks brentroos, I installed "Easy aMSN". It didn't work, it never completed the install and now  it is stuck at several places on my HDD.
[http://www.ubuntuforums.org/showthread.php?t=102299&page=6](http://www.ubuntuforums.org/showthread.php?t=102299&page=6)


I won't make the same mistake twice on this box, as it is my main computer.

---

### Post by elemental666 on 2006-06-12
How did you install aMSN?

---

### Post by brentroos on 2006-06-12
/

---

### Post by u.b.u.n.t.u on 2006-06-12
I installed aMSN with synaptic but aMSN isn't the problem.

The problem is the "Easy aMSN" I installed from here:

[http://wael.nasreddine.com/Articles/Articles/Easy_aMSN.html](http://wael.nasreddine.com/Articles/Articles/Easy_aMSN.html)

Which at the bottom of the page links back to here:

[http://www.ubuntuforums.org/showthread.php?t=102299](http://www.ubuntuforums.org/showthread.php?t=102299)

The program just didn't work for me. It doesn't seem to have an uninstall with it.

I can manually delete all the "Easy aMSN" I find on my HDD but I don't know how to delete their icon from Applications > System Tools.

I have no idea how to get rid of the other things it did. I won't be installing software like that again. I will check to see if there is an uninstall next time... lesson learned.

Thanks.

---

### Post by Perfect Storm on 2006-06-12
ah, it's an installer script. Try check its folder for an uninstaller script, or rerun the installer-script it might have an uninstaller mechanism.
If not you might want to manually remove the file it install by yourself.

---

### Post by Harleen on 2006-06-12
You can also just reinstall the application using checkinstall. This will do just the same as the install before, but also register the files to the packaging system.
So afterwards you will be able to uninstall all files with synaptic.

Instead of "sudo ./install.sh" do the following:
```
sudo checkinstall ./install.sh
```
And then remove the package with synaptic.

---

### Post by u.b.u.n.t.u on 2006-06-12
[QUOTE=Artificial Intelligence]ah, it's an installer script. Try check its folder for an uninstaller script, or rerun the installer-script it might have an uninstaller mechanism.
If not you might want to manually remove the file it install by yourself.[/QUOTE]

I doesn't seem to have any notes on uninstalling it.

The icon in the Applications > Systems Tools is what I really want to get rid off.

---

### Post by u.b.u.n.t.u on 2006-06-12
[QUOTE=Harleen]You can also just reinstall the application using checkinstall. This will do just the same as the install before, but also register the files to the packaging system.
So afterwards you will be able to uninstall all files with synaptic.

Instead of "sudo ./install.sh" do the following:
```
sudo checkinstall ./install.sh
```
And then remove the package with synaptic.[/QUOTE]

The application fails to install properly. I will try what you suggested - Danke.

---

### Post by Perfect Storm on 2006-06-12
Tried with alacarte menu editor?

Also if you have trouble with alarate menu editor try thte newest one here: [http://ubuntuforums.org/showthread.php?t=163272](http://ubuntuforums.org/showthread.php?t=163272)

---

### Post by elemental666 on 2006-06-12
[QUOTE=u.b.u.n.t.u]The icon in the Applications > Systems Tools is what I really want to get rid off.[/QUOTE]

1st try to delete: /usr/share/applications/easyamsn.desktop
if that doesn't work then open Accessories -> Alacarte Menu Editor, go to the system tools section and "uncheck" aMSN option.  This won't remove it from the system but will remove it from your menu.

---

### Post by brentroos on 2006-06-12
/

---

### Post by u.b.u.n.t.u on 2006-06-12
Thank you for all of your helpful replies. I will look into it today.

:D

---

