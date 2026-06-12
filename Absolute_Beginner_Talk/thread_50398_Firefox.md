---
title: "Firefox"
date: 2005-07-20
forum: Absolute Beginner Talk
---

### Post by Typhoid Mary on 2005-07-20
[FONT=Times New Roman][SIZE=3]*I have version 1.0.2 of Firefox. How do I upgrade to the latest version? After downloading it from their web site and installing it, Firefox refused to work.*[/SIZE][/FONT]

---

### Post by wellery on 2005-07-20
this explains how to install the latest verison:

[http://www.ubuntuforums.org/showpost.php?p=261096&postcount=3](http://www.ubuntuforums.org/showpost.php?p=261096&postcount=3)

---

### Post by darkmatter on 2005-07-20
[QUOTE=Typhoid Mary][FONT=Times New Roman][SIZE=3]*I have version 1.0.2 of Firefox. How do I upgrade to the latest version? After downloading it from their web site and installing it, Firefox refused to work.*[/SIZE][/FONT][/QUOTE]

You actually don't need to upgrade. The Firefox 1.0.2 actually is 1.0.4 (oversight when packaging), and the newest build should be in backports shortly.

Till then, just reinstall Firefox using Synaptic, type 
```
about:config
```
in the location bar, and find the entry
```
general.useragent.vendorSub
```
right click on it and select modify. change the value from 1.0 to 1.0.4 (this will allow you accesss to Mozilla Update)

---

### Post by Nequeo on 2005-07-20
Hey Wellery,

When a previously answered question gets posted again, it's considered polite to link to the original post:  [URL=http://www.ubuntuforums.org/showpost.php?p=261096&postcount=3]
Like so[/URL],  rather than pasting the whole thing in vertabim  :smile: 

Cheers,

---

### Post by wellery on 2005-07-20
yeah sorry. I didn't really know how to link to a single posting or didn't really bother to find out.

---

### Post by Strangerdave on 2005-07-20
I can't seem to mkdir ~/apps/firefox1.06 for some reason
Can anyone help?

SD

Would I have to be in root?

---

### Post by ozzie123 on 2005-07-20
[QUOTE=Strangerdave]I can't seem to mkdir ~/apps/firefox1.06 for some reason
Can anyone help?

SD

Would I have to be in root?[/QUOTE]
 If you wanted to delete your past firefox installation, then yes, you have to be the root.

---

### Post by poofyhairguy on 2005-07-20
[QUOTE=Strangerdave]I can't seem to mkdir ~/apps/firefox1.06 for some reason
Can anyone help?

SD

Would I have to be in root?[/QUOTE]

Yep. You can't do anything in folders other than your home folder as a regular user. 

Use this command:

> gksudo nautilus

---

### Post by ozzie123 on 2005-07-20
Plus: I think firefox installation on backport repo is damaged. I always gets an error when I tried to install it via synaptic.

Probably better to install it manually from the files directly from Mozilla, I mean, you'll learn more with that :)

---

### Post by poofyhairguy on 2005-07-20
[QUOTE=ozzie123]Plus: I think firefox installation on backport repo is damaged. I always gets an error when I tried to install it via synaptic.

Probably better to install it manually from the files directly from Mozilla, I mean, you'll learn more with that :)[/QUOTE]


Or just wait till Jdong backports 1.0.6.

---

### Post by Strangerdave on 2005-07-20
Humm, I can't seem to create the directory no matter what type of user I am.  I get this:

```
mkdir: cannot create directory `/root/apps/firefox1.06': No such file or directory
```

I thought that I had followed the directions, could I be missing something.  I can upack the tar okay, just can't create the directory.

SD 

PS: sorry for highjacking the thread

---

### Post by Kyral on 2005-07-20
it seems stupid, but you have to mkdir root from / then cd into that and mkdir apps then cd into that then mkdir firefox

---

### Post by poofyhairguy on 2005-07-21
[QUOTE=Kyral]it seems stupid, but you have to mkdir root from / then cd into that and mkdir apps then cd into that then mkdir firefox[/QUOTE]

just do it in nautilus.

> gksudo nautilus

---

### Post by Strangerdave on 2005-07-21
Alright guys, thanks for the info.  I didn't realize that one had to create the apps folder to begin with.  I will try it out in nautilus.  But is it normal to recieve error messages in the terminal window when using 

```
gksudo nauilus
``` ?  

I can't remember exactly what the messages were, but I did notice them when I first tried the command.

SD

---

### Post by Wolki on 2005-07-21
[QUOTE=poofyhairguy> ]I can't seem to mkdir ~/apps/firefox1.06 for some reason
Can anyone help?

SD

Would I have to be in root?
Yep. You can't do anything in folders other than your home folder as a regular user. 
[/QUOTE]

Why does he have to be root? ~/apps/firefox1.06 is in the home directory.

In the linked thread, there's an explanation on how to install the newest firefox into the home directory so you won't have to remove/add files in the system directories. This means the new firefox will only work for that user.

If he installs it as root, it might end up in root's homedir, and then a normal user will have to sudo everytime to start firefox.

For the installation process as described in that thread, no sudo is needed. If you want to install it system-wide for all userssudo is required, but be careful with that so it won't conflict with ubuntu's version.

---

