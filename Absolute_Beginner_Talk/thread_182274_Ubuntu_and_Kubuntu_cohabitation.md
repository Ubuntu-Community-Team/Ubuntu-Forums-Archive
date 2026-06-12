---
title: "Ubuntu and Kubuntu cohabitation?"
date: 2006-05-25
forum: Absolute Beginner Talk
---

### Post by mitch2k2 on 2006-05-25
This may be a stupid question, but I'd imagine also have a simple answer. I'm Ubuntu-happy, but curious. If I go ahead and download the Kubuntu desktop package, will I be able to switch easily between the two? Or will I be foresaking one for the other?

Thanks in advance.

---

### Post by nalmeth on 2006-05-25
yep, they can co-exist

sudo apt-get install kubuntu-desktop

log out, in GDM click SESSION and switch to KDE

that's it

---

### Post by aysiu on 2006-05-25
Try not to use apt-get. Aptitude is better for this.

More details:
[http://www.psychocats.net/ubuntu/kde.html](http://www.psychocats.net/ubuntu/kde.html)

---

### Post by Sef on 2006-05-25
> This may be a stupid question, but I'd imagine also have a simple answer. I'm Ubuntu-happy, but curious. If I go ahead and download the Kubuntu desktop package, will I be able to switch easily between the two? Or will I be foresaking one for the other?


It is not a stupid question.

---

### Post by nalmeth on 2006-05-25
[QUOTE=nalmeth]sudo apt-get install kubuntu-desktop[/QUOTE]
Never failed or brought out problem's of anykind for me.
[QUOTE=asiyu]Try not to use apt-get. Aptitude is better for this.[/QUOTE]
Maybe. Just force-of-habit for me. I learned debian with apt-get.
Either way will work.

---

### Post by aysiu on 2006-05-25
[QUOTE=nalmeth]
Maybe. Just force-of-habit for me. I learned debian with apt-get.
Either way will work.[/QUOTE] Either way will work to *install* Kubuntu, but then if you want to *un*install Kubuntu later, ```
sudo apt-get remove kubuntu-desktop
``` will do essentially nothing. ```
sudo aptitude remove kubuntu-desktop
``` will remove all the Kubuntu packages.

---

### Post by mitch2k2 on 2006-05-25
Thanks to all of you for the help.

---

### Post by ihavenoname on 2006-05-25
[QUOTE=aysiu]Either way will work to *install* Kubuntu, but then if you want to *un*install Kubuntu later, ```
sudo apt-get remove kubuntu-desktop
``` will do essentially nothing. ```
sudo aptitude remove kubuntu-desktop
``` will remove all the Kubuntu packages.[/QUOTE]
Whoa, im new to debain so could someone clarify this for me, cause I thought aptitude and apt-get where essentially the samething...is aptitude more advanced? hm...

---

### Post by aysiu on 2006-05-25
[QUOTE=ihavenoname]Whoa, im new to debain so could someone clarify this for me, cause I thought aptitude and apt-get where essentially the samething...is aptitude more advanced? hm...[/QUOTE] Yes, *aptitude* is more advanced.

This is what happens.

When you install *kubuntu-desktop* with **apt-get**, apt-get finds all of *kubuntu-desktop*'s dependencies (Kubuntu artwork, the appropriate KDE packages, the appropriate KDE applications) and installs them all.

When you then uninstall *kubuntu-desktop* with apt-get, only the pointer itself gets uninstalled. All the dependencies (Kubuntu artwork, etc.) stay installed. You need to either figure out what you installed before or try a script to uninstall it.

When you install with **aptitude**, it not only finds the dependencies--it remembers them, so that when you uninstall with *aptitude*, it'll remove not only the pointer, but also the associated packages (if no other packages depend on them).

---

### Post by uzi09 on 2006-05-26
yeah, there was another thread created about the whole aptitude vs apt-get thing...check it out: [http://ubuntuforums.org/showthread.php?t=181918](http://ubuntuforums.org/showthread.php?t=181918)

---

### Post by ihavenoname on 2006-05-26
Ah! thank you, but is it smart enought to keep one of the dependincies if they are needed by another package? For example if Both Kdevelop and Eclipse-Cdt rely on gcc will removing kdevelop also remove gcc? (Bad example but you get the point don't you?)

---

### Post by aysiu on 2006-05-26
[QUOTE=ihavenoname]Ah! thank you, but is it smart enought to keep one of the dependincies if they are needed by another package? For example if Both Kdevelop and Eclipse-Cdt rely on gcc will removing kdevelop also remove gcc? (Bad example but you get the point don't you?)[/QUOTE] Aptitude will remove dependencies only if other packages do not depend on those dependencies.

Look [here for more details](http://www.ubuntuforums.org/showpost.php?p=945406&postcount=7).

---

### Post by uzi09 on 2006-05-26
see that's the thing, it'll only remove it if NOTHING else needs it.

and the next time you download a program that does in fact need the file, it'll just automatically download/install it for ya!

so personally, i don't think it's that big of a deal.

the only problem i think may be the fact that it doesn't have a gui with it, and any other gui's all use apt -- so i'm not sure about this, but this **may** lead to inconsistancy if you install stuff through aptitude then pull up synaptic, but i don't think that should really be an issue, personally i don't use the gui anymore...

EDIT: jesus aysiu! always hit enter few seconds before i do :P

---

### Post by ihavenoname on 2006-05-26
Thank you (both of you)  That clears up alot. Hm, aptitude has an ncurses like mode, not to bad! I dont mind CLI anyways good night all! Just about 5 Days to go!

---

