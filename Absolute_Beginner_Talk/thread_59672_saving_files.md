---
title: "saving files"
date: 2005-08-24
forum: Absolute Beginner Talk
---

### Post by jasonpeinko on 2005-08-24
how do i save a file in a locked folder? 
and how do i edit a locked file?

---

### Post by Nequeo on 2005-08-24
[QUOTE=jasonpeinko]how do i save a file in a locked folder? 
and how do i edit a locked file?[/QUOTE]
 The lock basically means there is no write access on that folder/file. Changing it is simple if you happen to 'own' the file, and slightly harder if you don't.

First, try right clicking on the file/folder and selecting 'Properties--->Permissions'. 
If you are the owner of the file, just click the 'Write' box under 'owner' and voila! The lock will vanish and you can save files into the folder, or edit the file.

If the files are in your home directory somewhere, you are almost certainly the owner. If you are not the owner of the file, (i.e. the security options are greyed out), we're going to need to use the command line to take ownership. There are instructions here:

[http://www.ubuntuguide.org/#changefilesfolderspermissions](http://www.ubuntuguide.org/#changefilesfolderspermissions)

They're a bit terse, however, so feel free to ask if you still have problems. Just be aware that there are some circumstances where you cannot, or at least should not, be messing around with read-only files and folders. For example, if you habe mounted a windows partition formatted as NTFS, you cannot (currently) save files onto it, even though you can read files off it. 

Cheers,

---

### Post by jasonpeinko on 2005-08-25
i need to write the xorg,conf 
file for my ati graphics card. But where is says system_username 
is that my user name?

---

### Post by Nequeo on 2005-08-25
In that case, you don't want to change the file permissions... Just edit the file with admin privaleges...

Easiest way to do it is to type the following at the terminal

```

sudo gedit /etc/X11/xorg.conf

```

When it asks for a password, enter your own. 

However, reguarding the question about system_username, yeah, that's your login name. However, in the case of xorg.conf, it should stay as it is. 

You might want to look at [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo) It explains better than I could about the security model in Ubuntu.

Cheers,

---

