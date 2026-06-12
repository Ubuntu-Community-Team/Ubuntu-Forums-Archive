---
title: "Problem removing package: bug or feature?"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by Muun on 2006-07-04
I have the latest Ubuntu installed and am running Gnome. Experimenting with other GUIs, I installed XFce from the Synaptic Package Manager. I didn't like it, so I removed it -- again, using the package manager. It's not gone! "Removing" it freed up no noticable amount of disk space; at least some XFce executables are still in /usr/bin; and XFce is still available as a session choice from the login screen. What's up with that? I am wondering if this is the norm for installing & removing packages. Do they never really go away?

---

### Post by Dr. Nick on 2006-07-04
If you uninstalled xubuntu-desktop then xfce will still be thier, xubuntu-desktop is a metapackage that makes it easy to install all the needed parts of xfce, but removing it doesnt remove xfce. Their are only a few packages like that, most end in -desktop. 

For all other programs it will remove the executables and free the space.

If you just search in synaptic for xfce you may be able to find most of the parts and remove them

---

### Post by Jagot on 2006-07-04
[http://psychocats.net/ubuntu/puregnome.php](http://psychocats.net/ubuntu/puregnome.php)

---

### Post by Muun on 2006-07-04
[QUOTE=Dr. Nick]If you uninstalled xubuntu-desktop then xfce will still be thier, xubuntu-desktop is a metapackage that makes it easy to install all the needed parts of xfce, but removing it doesnt remove xfce. Their are only a few packages like that, most end in -desktop. 

For all other programs it will remove the executables and free the space.

If you just search in synaptic for xfce you may be able to find most of the parts and remove them[/QUOTE]

Thanks. I did not uninstall xubuntu-desktop. I installed, and later "removed", xfce4. I expected to go back to what I had before the install/remove -- but I didn't. 

Is there a convenient way to track exactly what changes an installation does, in order to remove it manually?

---

### Post by Muun on 2006-07-04
[QUOTE=Jagot][http://psychocats.net/ubuntu/puregnome.php](http://psychocats.net/ubuntu/puregnome.php)[/QUOTE]

Thanks. Doesn't apply to my case; but it does serve to point out that I shouldn't be using Synaptic.

---

### Post by Jagot on 2006-07-04
[QUOTE=Muun]Thanks. Doesn't apply to my case; but it does serve to point out that I shouldn't be using Synaptic.[/QUOTE]

It tells you all the packages you need to remove Xubuntu/XFCE - isn't that what you wanted?

---

### Post by Dr. Nick on 2006-07-04
ok..

Apparently thier is a xfce4 metapackage that isnt xubuntu-desktop. That is what you installed. Its the same principle as above.

I told it to install it on mine just to see what packages it installs, here are the results
```

drnick@Springfield:~$ sudo apt-get install xfce4
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  gtk2-engines-xfce libexo-0.3-0 libthunar-vfs-1 libxfce4mcs-client3
  libxfce4mcs-manager3 libxfce4util4 libxfcegui4-4 xfce4-icon-theme
  xfce4-mcs-manager xfce4-mcs-plugins xfce4-panel xfce4-session xfce4-utils
  xfdesktop4 xfwm4 xfwm4-themes
Recommended packages:
  xfce4-mixer xfprint4 orage xubuntu-default-settings
The following NEW packages will be installed:
  gtk2-engines-xfce libexo-0.3-0 libthunar-vfs-1 libxfce4mcs-client3
  libxfce4mcs-manager3 libxfce4util4 libxfcegui4-4 xfce4 xfce4-icon-theme
  xfce4-mcs-manager xfce4-mcs-plugins xfce4-panel xfce4-session xfce4-utils
  xfdesktop4 xfwm4 xfwm4-themes
0 upgraded, 17 newly installed, 0 to remove and 0 not upgraded.
Need to get 9815kB of archives.
After unpacking 51.5MB of additional disk space will be used.
Do you want to continue [Y/n]?
``` 

You may just be able to remove them in a similar manner as mentioned in the link above, many of them are probably the same package. The link above may try to remove some which are not installed which isnt a big deal

---

### Post by Muun on 2006-07-04
[QUOTE=Dr. Nick]ok..

Apparently thier is a xfce4 metapackage that isnt xubuntu-desktop. That is what you installed. Its the same principle as above.

I told it to install it on mine just to see what packages it installs, here are the results
```

drnick@Springfield:~$ sudo apt-get install xfce4
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  gtk2-engines-xfce libexo-0.3-0 libthunar-vfs-1 libxfce4mcs-client3
  libxfce4mcs-manager3 libxfce4util4 libxfcegui4-4 xfce4-icon-theme
  xfce4-mcs-manager xfce4-mcs-plugins xfce4-panel xfce4-session xfce4-utils
  xfdesktop4 xfwm4 xfwm4-themes
Recommended packages:
  xfce4-mixer xfprint4 orage xubuntu-default-settings
The following NEW packages will be installed:
  gtk2-engines-xfce libexo-0.3-0 libthunar-vfs-1 libxfce4mcs-client3
  libxfce4mcs-manager3 libxfce4util4 libxfcegui4-4 xfce4 xfce4-icon-theme
  xfce4-mcs-manager xfce4-mcs-plugins xfce4-panel xfce4-session xfce4-utils
  xfdesktop4 xfwm4 xfwm4-themes
0 upgraded, 17 newly installed, 0 to remove and 0 not upgraded.
Need to get 9815kB of archives.
After unpacking 51.5MB of additional disk space will be used.
Do you want to continue [Y/n]?
``` 

You may just be able to remove them in a similar manner as mentioned in the link above, many of them are probably the same package. The link above may try to remove some which are not installed which isnt a big deal[/QUOTE]

Great, thanks.

---

### Post by Dr. Nick on 2006-07-04
You can still use synaptic for some things, but if you read the description and see something like this
> 
This package depends on all of the packages in the Xubuntu desktop system
> 
This package is a pseudo meta package:

then stop and use aptitude instead to make removal easier

---

### Post by Muun on 2006-07-04
[QUOTE=Dr. Nick]You can still use synaptic for some things, but if you read the description and see something like this



then stop and use aptitude instead to make removal easier[/QUOTE]
Yes, I realize that now. Thanks. I was able to use your package list from the previous post to delete them individually. There's still no noticable blip in HD usage (though Synaptic has told me around 130 Mb total), but the offending executables and the XFce login option are gone. Well, that's my first Linux lesson -- I'm sure there will be many more.

---

