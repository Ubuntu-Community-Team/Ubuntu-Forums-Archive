---
title: "A program has lost its icon how can I give it a new icon?"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2007-07-27
A program has lost its icon how can I give it a new icon?
I deleted some temp files in an invisible folder for some program.  Even when I uninstall and re-install the program it can't assign a icon for itself in the menu nor on the desktop.
However when you resize it to minimal it has an icon when in use.

How do I give it a new icon?

---

### Post by Hobo Joe on 2007-07-27
I'm not quite sure what you're saying here.

BUT I'll try to help.

```

sudo aptitude purge <program name>

sudo aptitude install <program name>

```

---

### Post by dfreer on 2007-07-27
The above advice should help.
 
If it doesn't, you can try downloading the package manually from [http://packages.ubuntu.com](http://packages.ubuntu.com), save it to your desktop, and extract the contents of the package by either right-clicking on the package and choosing "Extract", or with the following commands:
```
mkdir ~/Desktop/temp
sudo dpkg -x ~/Desktop/*your_package_name_here.deb* ~/Desktop/temp/
```
Check in your ~/Desktop/temp/ folders, specifically in ~/Desktop/temp/usr/share/, the icon for the program can normally be found by digging around in there. Good luck!

EDIT: If you right-click and choose extract, you will also need to enter the resulting folder and extract the data.tar.gz file inside, which should have the /usr directory inside it.

---

### Post by jingo811 on 2007-07-27
I'm saying my icon is gone for this program no matter how many times I uninstall and reinstall it through Synaptic.
[IMG]http://i11.tinypic.com/5xy3hxs.png[/IMG]
Should I still use that purge aptitutde method you mentioned?

---

### Post by Lord Illidan on 2007-07-27
Try that, yes.

---

### Post by jingo811 on 2007-07-27
......soon

---

### Post by dfreer on 2007-07-27
> **jingo811 said:**
> I'm saying my icon is gone for this program no matter how many times I uninstall and reinstall it through Synaptic.
[IMG]http://i11.tinypic.com/5xy3hxs.png[/IMG]
Should I still use that purge aptitutde method you mentioned?

It may very well be that the path to the ktorrent icon on the desktop shortcut has been modified, which may also explain why you do not see the icon even upon reinstallation of the program. If you can see the icon for the program in your applications menu, I'd suggest creating a new shortcut. Still, try the above suggests first and report back on what worked/didn't work if you would :)

---

### Post by jingo811 on 2007-07-27
Hobo Joe's 2 line aptitude method worked like a charm.  Tnx for the help ppl :)

---

