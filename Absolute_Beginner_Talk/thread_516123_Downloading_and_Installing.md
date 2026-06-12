---
title: "Downloading and Installing"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by philip793 on 2007-08-02
Hello Ubuntu People,

I'm Ubuntu newbie. I just installed Ubuntu yesterday with Wubi. I downloaded something and  I don't know what to. When I double clicked it it didn't show the installer. Please help with downloading and installing. BTW I am liking Ubuntu really great OS.

:confused::confused:

---

### Post by Tux Aubrey on 2007-08-02
hi Philip

what exactly did you download?  Was it a .deb file or tar.gz?

Far and way the best way to get and install new software is the Add/Remove gui from the main menu.  If its something a bit more obscure, use Synaptic (System>Administration menu).

---

### Post by Bachstelze on 2007-08-02
[http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)

THis link has everything you need to know about installing software in Ubuntu.

---

### Post by Paul133 on 2007-08-02
The link Hymn gave is great. In Ubuntu (and other Linux distros), most programs are not installed by downloading them from a web site, like in Windows, but from downloading them from servers called repositories. If you go to System -> Administration -> Repositories, you can find thousnds of programs that can be marked for installation with one click. That's all you have to do. It's possible that you'll occasionally need to download a .deb online or install from source, but not usually. Good luck with Ubuntu.

---

### Post by philip793 on 2007-08-02
It's a .tar Aubrey. Thanks for the help again. :)

---

### Post by Paul133 on 2007-08-02
Did you find the program you needed?

---

### Post by philip793 on 2007-08-02
I want to download firefox and reinstall it.:(

---

### Post by Tux Aubrey on 2007-08-02
I'd really recommend using Add/Remove or Synaptic for Firefox - the repositories have the latest version that has been optimised for Ubuntu.

Synaptic is probably the way to go here because, I suspect, you should do a complete remove before reinstalling.  If you were having any problems, a complete remove is the best way to ensure that you get the right packages replaced.

I'm not on an Ubuntu machine at the mement, so I can't do a full "walkthrough" for you but you should open Synaptic (System>Administration>Synaptic Package Manager), search for firefox - find the main program file (it should be obvious) and it will have a green box next to it (if you haven't already uninstalled it) Right click on the box and select "completely remove".  You will be asked to confirm that Firefox and its unique dependencies (files that come with it) should be removed.  Agree and then "Apply".  Let it finish and then go back and right click the same box (now cleared) and select to install it.  Apply again and all should be right.

BTW, the tar.gz package should open with "File Roller".  It should already be associated with that program but, if not, you use the right mouse button and opt to select the program to open it with.  Choose "File Roller".  I'm not familiar with the Firefox tar.gz package, but my hunch would be that there is either a deb file inside it (that will run the install script when double clicked) or it will unarchive the executable/s to the necessary folders and you would have to create a launcher or menu item for it.  Synaptic much better.

---

### Post by Frak on 2007-08-02
Goto Applications > Accessories > Terminal
And copy and paste this into it
```
sudo aptitude reinstall firefox
```
Sudo grants you the ability to install things
Aptitude is a package manager
reinstall tells Aptitude to do
firefox tell aptitude what to reinstall.

---

