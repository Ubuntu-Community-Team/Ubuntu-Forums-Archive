---
title: "Getting and Installing gFTP"
date: 2005-07-25
forum: Absolute Beginner Talk
---

### Post by KrisDwyer on 2005-07-25
ok, i kinda downloaded some of the gftp stuff but im really confused... what stuff do i need to download to use gFTP (the GUI version) and how do i install it (i.e what order)

Thanks in Advance,
Kris

---

### Post by KrisDwyer on 2005-07-25
[QUOTE=KrisDwyer]ok, i kinda downloaded some of the gftp stuff but im really confused... what stuff do i need to download to use gFTP (the GUI version) and how do i install it (i.e what order)

Thanks in Advance,
Kris[/QUOTE]
 this thread is related to this one also:
[http://www.ubuntuforums.org/showthread.php?t=51711](http://www.ubuntuforums.org/showthread.php?t=51711)

---

### Post by SYD2005 on 2005-07-25
Kris -- it depends what way you want to go about instaling gFTP. I will give you 2 ways to do this.

-- Use Synaptic located in your menu under System --> Administration --> Synaptic Package Manager. You will need to type password when asked for it. Search for gFTP then tick the box. Once you do that then click the tick at the top and it will install it for you. Once finished go to your Applications menu --> Internet and then you should see it located in there.

-- Or via a command line type "sudo apt-get install gftp"  (without the quotes) 

Have a look at [www.ubuntuguide.org](www.ubuntuguide.org) to see more info.

Hope this helps.

---

### Post by darkmatter on 2005-07-25
Kris, I agree with SYD...grabbing the Synaptic/apt-get version is a much better option than a manual install, as the packages are built for Ubuntu and apt will handle dependency resolution for you, potentially saving you a lot of extra work.

---

### Post by KrisDwyer on 2005-07-25
[QUOTE=darkmatter]Kris, I agree with SYD...grabbing the Synaptic/apt-get version is a much better option than a manual install, as the packages are built for Ubuntu and apt will handle dependency resolution for you, potentially saving you a lot of extra work.[/QUOTE]
 Eep! It didnt work! Please Help!
[IMG]http://www.geocities.com/kristiand45/eek.png[/IMG]

---

### Post by Kimm on 2005-07-25
strange, have you enabled extra repositories? I have no idea if thats it or not but might solve it...

---

### Post by KrisDwyer on 2005-07-25
[QUOTE=Kimm]strange, have you enabled extra repositories? I have no idea if thats it or not but might solve it...[/QUOTE]
 how do i do this?

---

### Post by darkmatter on 2005-07-25
[QUOTE=KrisDwyer]how do i do this?[/QUOTE]
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

---

### Post by rmjokers on 2005-07-25
Actually, when you want to install a software package, it is often best to do a search first so that you can get the name right.  In your case, if you do:

apt-cache search gftp, you get:

gftp - X/GTK+ FTP client
gftp-text - colored FTP client using GLib
gftp-common - shared files for other gFTP packages
gftp-gtk - X/GTK+ FTP client

To install the gtk version, which is better, you need to do:

sudo apt-get install gftp-gtk

I think all of the necessary packages are in the ubuntu repository, but if not, you can enable the universe and multiverse packages by adding them in

Settings->Repositories in the Synaptic menu

---

### Post by UbuWu on 2005-07-25
Install gftp-gtk instead of gftp, no need to enable extra repositories.

---

