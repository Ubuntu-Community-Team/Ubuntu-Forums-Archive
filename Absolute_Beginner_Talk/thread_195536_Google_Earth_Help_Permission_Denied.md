---
title: "Google Earth Help Permission Denied"
date: 2006-06-13
forum: Absolute Beginner Talk
---

### Post by vierranet on 2006-06-13
Installed google earth, receiving permission denied when I type googleearth in the command line:confused: 

vierranet@vierranet1:~$ googleearth
symlink: Permission denied

vierranet@vierranet1:~$ cd ~/Desktop
vierranet@vierranet1:~/Desktop$ chmod +x GoogleEarthLinux.bin
vierranet@vierranet1:~/Desktop$ ./GoogleEarthLinux.bin
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 

4.0.1563..................................................................
Installing mimetypes...
mkdir: `/home/vierranet/.local/share/mime/packages/': Permission denied
cp: accessing `/home/vierranet/.local/share/mime/packages//googleearth-mimetypes.xml': Permission denied
Running /usr/bin/update-mime-database /home/vierranet/.local/share/mime
/usr/bin/update-mime-database: I don't have write permission on /home/vierranet/.local/share/mime.
Try rerunning me as root.
Installing desktop menu entries...
cp: cannot create regular file `/home/vierranet/.local/share/applications/googleearth.desktop': Permission denied
mkdir: `/home/vierranet/.kde/share/applnk': Permission denied
cp: accessing `/home/vierranet/.kde/share/applnk/googleearth.desktop': Permission denied
cp: accessing `/home/vierranet/.gnome/apps/googleearth.desktop': Permission denied

---

### Post by loell on 2006-06-13
there are directories in your home directory that are owned by your root account
as the package suggest.. try running it as root

sudo ./GoogleEarthLinux.bin

---

### Post by u.b.u.n.t.u on 2006-06-13
I looked at Google Earth the other day and thought it wasn't available for linux.

Edit:

Only Windows and Mac are officially supported. Therefore whatever is on Linux isn't ideal in terms of stability.

[http://earth.google.com/faq.html](http://earth.google.com/faq.html)

"Minimum configuration:

    * Operating System: Windows 2000, Windows XP"

"Minimum Configuration:

    * Operating System: Mac OS X 10.3.9"

---

### Post by vierranet on 2006-06-13
[QUOTE=loell]there are directories in your home directory that are owned by your root account
as the package suggest.. try running it as root

sudo ./GoogleEarthLinux.bin[/QUOTE]

New to Linux, gave up MS for Lent, been at it ever since, still learning. To be honest I'm still having a bit of a learning curve. How do I run it (this) as Root?:confused:

---

### Post by dmizer on 2006-06-13
[QUOTE=vierranet]How do I run it (this) as Root?[/QUOTE]
[QUOTE=loell]sudo ./GoogleEarthLinux.bin[/QUOTE]
but keep in mind that as u.b.u.n.t.u noted, this will probably not work either.  as currently google earth is not supported in linux (ie. not supported in ubuntu)

---

### Post by _simon_ on 2006-06-13
[QUOTE=u.b.u.n.t.u]I looked at Google Earth the other day and thought it wasn't available for linux.

Edit:

Only Windows and Mac are officially supported. Therefore whatever is on Linux isn't ideal in terms of stability.

[http://earth.google.com/faq.html](http://earth.google.com/faq.html)

"Minimum configuration:

    * Operating System: Windows 2000, Windows XP"

"Minimum Configuration:

    * Operating System: Mac OS X 10.3.9"[/QUOTE]

Beta 4

[http://earth.google.com/download-earth.html](http://earth.google.com/download-earth.html)

Works fine for me.

To install it you just do ```
sh GoogleEarthLinux.bin
``` and it will by default install into the home directory.

To run it, there's a link in Applications -> Internet

---

### Post by vierranet on 2006-06-13
Thank You Guy's... Got it running, it's slow but that's ok...

---

### Post by u.b.u.n.t.u on 2006-06-13
Thanks for the link _simon_.

Is that run natively on Linux or through wine within their software?

---

### Post by superm1 on 2006-06-13
This permission denied problem is because you let it launch with sudo permissions immediately after installing.  When it finishes installing, don't let it run, but launch it yourself instead. 

If you already did let it run as root, change the permissions of the entire .googleearth directory in your home directory.  Also 
change permissions on anything within .local that the installer made.

---

### Post by superm1 on 2006-06-13
[quote=u.b.u.n.t.u]Thanks for the link _simon_.

Is that run natively on Linux or through wine within their software?[/quote]
It is native, and linked with QT.

---

### Post by _simon_ on 2006-06-13
I believe it's native, if you run it and check system monitor you won't see any instances of WINE like you do with picaso2

---

### Post by vierranet on 2006-06-13
[QUOTE=superm1]This permission denied problem is because you let it launch with sudo permissions immediately after installing.  When it finishes installing, don't let it run, but launch it yourself instead. 

If you already did let it run as root, change the permissions of the entire .googleearth directory in your home directory.  Also 
change permissions on anything within .local that the installer made.[/QUOTE]


How do I change the permissions in .googleearth and .local (I'm new, learning, and have brain cramps). :confused:

---

### Post by superm1 on 2006-06-13
Easiest way is

sudo chown $USER:users ~/.googleearth -R
sudo chown $USER:users ~/.local -R

Where $USER is your username

---

### Post by vierranet on 2006-06-13
superm1

Thank You...
I Got it..

vierranet

---

### Post by adam.tropics on 2006-06-13
Go Google! They seem to be getting a bit linux friendly at the moment! (Makes you want to ask what they want! )

Edit: except the exceptionally slow download!!

---

### Post by u.b.u.n.t.u on 2006-06-13
[QUOTE=superm1]It is native, and linked with QT.[/QUOTE]

Thanks. I think I read that Google's image viewer Picasa runs on Linux, emulated with wine so I was wondering if they may have done this again.

I'll download Google Earth too later. Looks promising. I'll get Beta 4 as well.

---

