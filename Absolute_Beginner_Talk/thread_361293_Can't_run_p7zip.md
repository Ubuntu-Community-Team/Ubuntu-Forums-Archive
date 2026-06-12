---
title: "Can't run p7zip"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by wannabehero on 2007-02-14
I installed p7zip using the synaptic package manager, but now I can't run it. It doesn't show up as one of my applications.  A friend of mine told me I have to use a command line to run it, but I honestly have no idea how to do that. I mean, I can open a terminal and all, but it's all greek to me.

I just switched from Windows, I'm not a programmer, somebody help!!:confused:

---

### Post by taurus on 2007-02-14
Applications -> Accessories -> Terminal
```
p7zip
```

---

### Post by wannabehero on 2007-02-14
this was the response I got.

/usr/bin/p7zip: compressed data not written to a terminal.
For help, type: /usr/bin/p7zip -h

Maybe I'm approaching this the wrong way. Before switching to Ubuntu, I backed up all my essential files onto another computer in my house. After switching, I compressed all my files into a cd and have copied the file to my desktop. Basically I want to open that.  

do I have to open p7zip on its own, or is there a command line I can use that would open up at the desktop file all at once.

Thanks for your help.

---

### Post by taurus on 2007-02-14
p7zip is working.  However, to use it,  you need to supply a filename so it can uncompress it.

```
p7zip **filename**
```

---

### Post by wannabehero on 2007-02-14
Here's what I tried:

[I]wannabehero@DCUnited:~$ p7zip joes

7-Zip (A) 4.42  Copyright (c) 1999-2006 Igor Pavlov  2006-05-14
p7zip Version 4.42 (locale=en_US.UTF-8,Utf16=on,HugeFiles=on,1 CPU)
Scanning


joes:  WARNING: No more files                


Creating archive joes.7z



WARNINGS for files:

joes : No more files                
----------------
WARNING: Cannot find 1 file
wannabehero@DCUnited:~$ p7zip joes.7z

7-Zip (A) 4.42  Copyright (c) 1999-2006 Igor Pavlov  2006-05-14
p7zip Version 4.42 (locale=en_US.UTF-8,Utf16=on,HugeFiles=on,1 CPU)

Scanning

Updating archive joes.7z.7z

Compressing  joes.7z                                                      

Everything is Ok
wannabehero@DCUnited:~$ p7zip joes.7z -d

7-Zip (A) 4.42  Copyright (c) 1999-2006 Igor Pavlov  2006-05-14
p7zip Version 4.42 (locale=en_US.UTF-8,Utf16=on,HugeFiles=on,1 CPU)


Error:
there is no such archive[/I]

The last line kinda bothers me. I can see the file on my desktop. I tried to use these same commands, i.e. p7zip filename,  with filename replaced by the extension listed in the file properties, but that didn't work either.

thanks, i really appreciate the help.  i'm a total noob.:)

---

### Post by taurus on 2007-02-14
So, you are trying to compress joe and then uncompress it with p7zip!  What's the output of this command then?

```
ls -la
```

---

### Post by wannabehero on 2007-02-14
well, no.... I really have no idea what I'm doing. 

typing in ls -la got me this:

total 188
drwxr-xr-x 28 wannabehero wannabehero  4096 2007-02-14 09:42 .
drwxr-xr-x  3 root        root         4096 2007-02-10 17:39 ..
-rw-------  1 wannabehero wannabehero   564 2007-02-14 09:20 .bash_history
-rw-r--r--  1 wannabehero wannabehero   220 2007-02-10 17:39 .bash_logout
-rw-r--r--  1 wannabehero wannabehero   414 2007-02-10 17:39 .bash_profile
-rw-r--r--  1 wannabehero wannabehero  2227 2007-02-10 17:39 .bashrc
drwx------  3 wannabehero wannabehero  4096 2007-02-11 09:40 .config
drwxr-xr-x  6 wannabehero wannabehero  4096 2007-02-14 09:37 Desktop
-rw-------  1 wannabehero wannabehero    26 2007-02-10 17:50 .dmrc
-rw-------  1 wannabehero wannabehero    16 2007-02-10 17:50 .esd_auth
drwxr-xr-x  8 wannabehero wannabehero  4096 2007-02-13 22:08 .evolution
lrwxrwxrwx  1 wannabehero wannabehero    26 2007-02-10 17:39 Examples -> /usr/share/example-content
-rw-r--r--  1 wannabehero wannabehero     0 2007-02-10 18:38 .fonts.cache-1
drwx------  4 wannabehero wannabehero  4096 2007-02-14 09:55 .gaim
drwx------  4 wannabehero wannabehero  4096 2007-02-14 07:46 .gconf
drwx------  2 wannabehero wannabehero  4096 2007-02-14 09:56 .gconfd
drwxr-xr-x 21 wannabehero wannabehero  4096 2007-02-11 21:26 .gimp-2.2
-rw-r-----  1 wannabehero wannabehero     0 2007-02-13 20:51 .gksu.lock
drwxr-xr-x  3 wannabehero wannabehero  4096 2007-02-10 17:51 .gnome
drwx------ 10 wannabehero wannabehero  4096 2007-02-13 22:08 .gnome2
drwx------  2 wannabehero wannabehero  4096 2007-02-10 18:53 .gnome2_private
drwxr-xr-x  2 wannabehero wannabehero  4096 2007-02-10 17:50 .gstreamer-0.10
-rw-r--r--  1 wannabehero wannabehero    93 2007-02-10 17:50 .gtkrc-1.2-gnome2
-rw-------  1 wannabehero wannabehero   326 2007-02-14 07:46 .ICEauthority
-rw-r--r--  1 wannabehero wannabehero    32 2007-02-14 09:33 joe.7z.7z
-rw-r--r--  1 wannabehero wannabehero   131 2007-02-14 09:42 joes.7z.7z
drwx------  3 wannabehero wannabehero  4096 2007-02-11 09:46 .kde
drwx------  3 wannabehero wannabehero  4096 2007-02-12 18:34 .local
drwx------  3 wannabehero wannabehero  4096 2007-02-10 18:56 .macromedia
drwxr-xr-x  3 wannabehero wannabehero  4096 2007-02-11 09:48 .mcop
-rw-------  1 wannabehero wannabehero    31 2007-02-11 09:48 .mcoprc
drwx------  3 wannabehero wannabehero  4096 2007-02-10 17:51 .metacity
drwx------  4 wannabehero wannabehero  4096 2007-02-10 18:56 .mozilla
drwxr-xr-x  3 wannabehero wannabehero  4096 2007-02-13 22:08 .nautilus
drwx------  3 wannabehero wannabehero  4096 2007-02-11 08:34 .openoffice.org2
drwxr-xr-x  2 wannabehero wannabehero  4096 2007-02-11 09:47 .qt
-rw-------  1 wannabehero wannabehero  1321 2007-02-13 20:09 .recently-used
-rw-r--r--  1 wannabehero wannabehero 10642 2007-02-14 09:07 .recently-used.xbel
-rw-r--r--  1 wannabehero wannabehero     0 2007-02-10 17:52 .sudo_as_admin_successful
drwx------  4 wannabehero wannabehero  4096 2007-02-11 11:08 .thumbnails
drwx------  2 wannabehero wannabehero  4096 2007-02-14 09:34 .Trash
drwxr-xr-x  2 wannabehero wannabehero  4096 2007-02-10 17:51 .update-manager
drwx------  2 wannabehero wannabehero  4096 2007-02-10 17:51 .update-notifier
drwxr-xr-x  3 wannabehero wannabehero  4096 2007-02-12 18:40 .vlc
drwxr-x---  3 wannabehero wannabehero  4096 2007-02-13 20:26 .xarchive
-rw-------  1 wannabehero wannabehero   119 2007-02-14 07:46 .Xauthority
-rw-r--r--  1 wannabehero wannabehero 10961 2007-02-14 09:34 .xsession-errors

I don't know what to do with that.....:confused:

---

### Post by taurus on 2007-02-14
```
p7zip -d joes.7z.7z
p7zip -d joes.7z
```

---

