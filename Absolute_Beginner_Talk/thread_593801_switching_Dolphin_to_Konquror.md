---
title: "switching Dolphin to Konquror"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by baracuda68 on 2007-10-27
HI
In Kubuntru Gutsy I wish to go back to using konquror, instead of Dolphin, as my file browser.
I like the look of Dolphin, but sometimes as I browse through my files, the system automatically restarts. This is very annoying. I want to try Konquror as the default file manager and see if it still happens.

Any ideas how to do this?
Konquror is installed.

Thanks.:guitar:

---

### Post by kellemes on 2007-10-27
> **baracuda68 said:**
> HI
In Kubuntru Gutsy I wish to go back to using konquror, instead of Dolphin, as my file browser.
I like the look of Dolphin, but sometimes as I browse through my files, the system automatically restarts. This is very annoying. I want to try Konquror as the default file manager and see if it still happens.

Any ideas how to do this?
Konquror is installed.

Thanks.:guitar:

I'm surprised dolphin is default since it's part of a beta-released KDE4.. or so I thought.
Just wonder.. what do you mean with default? You can use Konqueror as you wish don't you?

---

### Post by baracuda68 on 2007-10-27
> **kellemes said:**
> I'm surprised dolphin is default since it's part of a beta-released KDE4.. or so I thought.
Just wonder.. what do you mean with default? You can use Konqueror as you wish don't you?

Yes, when I use Konquror stand alone, I can use it as the file browser, but I usually use my System Menu applet to access my files- and that opens Dolphin. How would I switch defaults?

---

### Post by kellemes on 2007-10-27
> **baracuda68 said:**
> Yes, when I use Konquror stand alone, I can use it as the file browser, but I usually use my System Menu applet to access my files- and that opens Dolphin. How would I switch defaults?

Right.. Well, I'm on another KDE-system, don't know how Kubuntu has done this..
Still, you might try to see if there is any option in Control-Center. Maybe at KDE-components -> Filemanager?

---

### Post by FFred on 2007-10-29
Run kontrol (alt-f2 kontrol)
In KDE components, 
File associations,
Inode,
Directory
Move Konqueror above Dolphin.

Done.

---

### Post by baracuda68 on 2007-10-29
> **FFred said:**
> Run kontrol (alt-f2 kontrol)
In KDE components, 
File associations,
Inode,
Directory
Move Konqueror above Dolphin.

Done.

Thanks, Ffred,
 That worked.

   Kcontrol:guitar:

---

### Post by LowSky on 2007-10-29
> **baracuda68 said:**
> HI
In Kubuntru Gutsy I wish to go back to using konquror, instead of Dolphin, as my file browser.
I like the look of Dolphin, but sometimes as I browse through my files, the system automatically restarts. This is very annoying. I want to try Konquror as the default file manager and see if it still happens.

Any ideas how to do this?
Konquror is installed.

Thanks.:guitar:

I think something is wrong if you system just reboots

---

### Post by FFred on 2007-10-29
> **LowSky said:**
> I think something is wrong if you system just reboots

Yes I have to concur, I don't think I've seen a system "just rebooting" in, what, 12 or 13 years of using Linux, unless there was a hardware fault, or possibly a gross system misconfiguration. 

At any rate I doubt Dolphin could cause this.

---

### Post by maestrobwh1 on 2007-11-07
I had to "sudo" kcontrol to get the change to stick.  No biggie, but if anyone is having issues, then you might need to do this.

---

### Post by FFred on 2007-11-08
Another (arguably more simple) method would be to check the properties of a directory, click the little "tools" icon next to "type" in the general tab and in application preference order move Konqueror up to the first (top) place.

It's pretty much the same thing as the Kontrol manipulation I outlined above except you don't need kontrol :)

Presumably this will only affect the current user.

---

### Post by the.ant on 2007-11-10
the best method to solve all those dolphin annoyances is imho
"sudo apt-get remove dolphin"

---

### Post by ffi on 2007-11-10
> **the.ant said:**
> the best method to solve all those dolphin annoyances is imho
"sudo apt-get remove dolphin"
I really don't get why the kde team made dolphin, they already have the best and easiest most intuitive file-browser, and much more, in the world -konqueror- and then they build dolphin, hard to use, counter intuitive and featureless, almost like nautilus....:confused:

---

### Post by the.ant on 2007-11-10
yep and nautilus was one of the main reasons I chose kde over gnome.
It's hard enough to convince experienced windows-users to give kubuntu a try and then to be stuck with something like dolphin is a major annoyance. 

I understand that it's easier for a programmer to write for a program which focuses on only one task, but in terms of usability dolphin is an immense regress.

---

### Post by FFred on 2007-11-10
While I don't really see Nautilus as under featured (although Konqueror does indeed have way more features) I too am puzzled by the sudden appearance of Dolphin.

I don't know if this is indeed the final choice for KDE 4 or if it's just a Ubuntu 7.10 packaging choice. Still very odd. Nobody seems to like that file browser.
If at least it was compatible with the Konqueror tools and extensions...

---

