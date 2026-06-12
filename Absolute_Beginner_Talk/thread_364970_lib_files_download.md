---
title: "lib files download"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by sauravbhaumik on 2007-02-18
I have been in great distress. I inadvertently deleted the files (not folders) from the /usr/lib directory and then restarted but Ubuntu was not starting. Then I booted from the Ubuntu CD and copied the files from /usr/lib of the CD to the /usr/lib of the ubuntu partition. Then Ubuntu booted.
But alas! While I tried to open the applications I installed using the add/remove, they did not open. I removed them from the add/remove and installed again, It did not work. I tried the same trick through the synaptic, but in vain again.  
Kindly tell me what to do. I can reinstall Ubuntu but you see, I have configured Ubuntu very conveniently and once I have to make it again as before, it would take time and it would be much troublesome. Kindly bother about this problem - I beg of you. It is very very urgent.
Regards,
Saurav

---

### Post by bulldog on 2007-02-18
Do you have at the bottom of your synaptic an error which tells you you have broken packages?

---

### Post by taurus on 2007-02-18
I would be nice to know the name of the package and why not try to install it with aptitude to see what's wrong with it.

Applications  -> Accessories  -> Terminal
```
sudo aptitude update
sudo aptitude install **package_name**
```

---

### Post by sauravbhaumik on 2007-02-18
> **bulldog said:**
> Do you have at the bottom of your synaptic an error which tells you you have broken packages?

No there is no such.

---

### Post by sauravbhaumik on 2007-02-18
> **taurus said:**
> I would be nice to know the name of the package and why not try to install it with aptitude to see what's wrong with it.

Applications  -> Accessories  -> Terminal
```
sudo aptitude update
sudo aptitude install **package_name**
```

It didn't work. I have lost my Texmaker .  It is a latex editor. When I run sudo aptitude install texmaker, it installs it. And when I try to open it, it gives ```
texmaker: error while loading shared libraries: libQtGui.so.4: cannot open shared object file: No such file or directory
```

---

### Post by bulldog on 2007-02-18
It seems you're been missing some lib's.
You can try ```
sudo aptitude dist-upgrade
```to see if it will solve things for you.

---

### Post by sauravbhaumik on 2007-02-18
Can anybody tell me how to download libQtGui.so.4?
I have inadvertently deleted the files from /usr/lib and then copied /usr/lib from Ubuntu CD. But it doesn't restore the lib files that were installed during the installation of TeXmaker and some other packages. Kindly help me.

---

### Post by po0f on 2007-02-18
sauravbhaumik,

You should be able to reinstall [libqt4-gui](http://packages.ubuntu.com/edgy/libs/libqt4-gui) and get it back.

---

### Post by aysiu on 2007-02-18
Try here:
[http://packages.ubuntu.com/edgy/libs/libqt4-gui](http://packages.ubuntu.com/edgy/libs/libqt4-gui)

Can't you just do something like this? ```
sudo apt-get install --reinstall texmaker
``` or ```
sudo apt-get install libqt4-gui
```

---

### Post by sauravbhaumik on 2007-02-18
> **aysiu said:**
> Try here:
[http://packages.ubuntu.com/edgy/libs/libqt4-gui](http://packages.ubuntu.com/edgy/libs/libqt4-gui)

Can't you just do something like this? ```
sudo apt-get install --reinstall texmaker
``` or ```
sudo apt-get install libqt4-gui
```

This turned out to fail to help me. However, I did aptitude remove libqt4-gui and it removed these and then I reinstalled them back; but when after doing these I run the command texmaker, it gives ```
root@saurav-desktop:/home/saurav# texmaker
texmaker: error while loading shared libraries: libQtCore.so.4: cannot open shared object file: No such file or directory
root@saurav-desktop:/home/saurav# 

```

---

### Post by po0f on 2007-02-18
sauravbhaumik,

Try removing both libqt4-gui and texmaker, then reinstalling both.

---

### Post by aysiu on 2007-02-18
Reinstall *texmaker* failed you?

In that case, you will have to reinstall all the original libraries: ```
sudo apt-get install libqt4-core
```

---

### Post by sauravbhaumik on 2007-02-19
I can't believe it! God seems to be gracious! I did the following:```
sudo aptitude purge libqt4-core

sudo aptitude purge libqt4-gui

sudo apt-get install libqt4-core libqt4-gui texmaker
```
And it worked!
Thank you very much:)

---

### Post by sauravbhaumik on 2007-02-19
But while doing the same for xfig, it doesn't work. command xfig gives that libxaw3d.so.6 is not available. Tell me what to do. I removed and installed back libxaw6; but it doesn't work.

---

### Post by sauravbhaumik on 2007-02-19
*Ref: previous post : download lib files*
But while doing the same for xfig, it doesn't work. command xfig gives that libxaw3d.so.6 is not available. Tell me what to do. I removed and installed back libxaw6; but it doesn't work.

---

### Post by aysiu on 2007-02-19
Maybe this? ```
sudo aptitude purge xaw3dg
sudo apt-get install xaw3dg xfig
```

---

### Post by po0f on 2007-02-19
sauravbhaumik,

Wow, triple post.  :P

Did you follow the same exact steps?

And that file is located in the [xaw3dg](http://packages.ubuntu.com/edgy/x11/xaw3dg) package.

---

### Post by sauravbhaumik on 2007-02-19
installing xaw3dg didn't fix it!](*,)

---

### Post by aysiu on 2007-02-19
I've merged your duplicate threads and moved the duplicate posts to the Jail. Please keep it all in one place so people can help you and also see what other suggestions people have made to you.

---

### Post by sauravbhaumik on 2007-02-19
> **aysiu said:**
> I've merged your duplicate threads and moved the duplicate posts to the Jail. Please keep it all in one place so people can help you and also see what other suggestions people have made to you.

Thanks, master roaster, for the defragmentation.
But with anjuta I am stuck again:confused: 
I give you what it does when I start ajunta
```
root@saurav-desktop:/home/saurav# anjuta

(anjuta:6758): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

(anjuta:6758): libgnomevfs-CRITICAL **: gnome_vfs_format_uri_for_display_internal: assertion `uri != NULL' failed
root@saurav-desktop:/home/saurav# anjuta

```

Can you find some hope in it?:(

---

### Post by po0f on 2007-02-19
sauravbhaumik,

> **sauravbhaumik said:**
> 
```
**[color="red"]root[/color]**@saurav-desktop:/home/saurav# anjuta

(anjuta:6758): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

(anjuta:6758): libgnomevfs-CRITICAL **: gnome_vfs_format_uri_for_display_internal: assertion `uri != NULL' failed
root@saurav-desktop:/home/saurav# anjuta

```

The bold, red part is your problem.  Don't run as root.  You wouldn't have deleted the lib file from earlier if you had taken simple precautions.  There's a reason why Ubuntu doesn't have a root account activated by default.

---

