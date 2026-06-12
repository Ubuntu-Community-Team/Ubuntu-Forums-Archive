---
title: "How do I make changes to GRUB permanent?/yelp:5521"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by GregoryMA on 2007-05-20
Upon boot-up I had the error "...MP-BIOS bug: 8254 timer not connected to IO-APIC" which I found out how to fix from two other posts.  

[http://ubuntuforums.org/showthread.php?t=191355](http://ubuntuforums.org/showthread.php?t=191355)
[http://ubuntuforums.org/showthread.php?t=166212&highlight=MP-BIOS+bug](http://ubuntuforums.org/showthread.php?t=166212&highlight=MP-BIOS+bug)

However, I followed the directions in these posts to make the changes to GRUB permanent ("...make it permanent by adding "noapic" to the "# defoptions=" line in /boot/grub/menu.lst and then running update-grub.") but I think I am doing it wrong or something is not working correctly (maybe both).  When I put the command in the terminal I do not get the a line that reads '# defoptions=' I get:

(yelp:5521) yelp-warning**: cannot find dbus bus
**(yelp:5521): warning**:AT_SPI_REGISTRY was not started at session startup.
**(yelp:5521): warning**:IOR not set.
**(yelp:5521): warning**:Could not locate registry
unmatched element: citerefentry
unmatched element: retentrytitle
unmatched element: citerefentry
unmatched element: retentrylittle

I guess I have two questions:
How do I make the change I made in GRUB permanent?
What is all this stuff about yelp:5521?

Thanks, Greg.

---

### Post by Pragmatist on 2007-05-21
Please post the contents of your /boot/grub/menu.lst

---

### Post by GregoryMA on 2007-05-21
Here is the output of /boot/grub/menu.1st from the terminal:

bash: /boot/grub/menu.1st: No such file or directory.

I also inputed gedit /boot/grub/menu.1st  (note that this is the command I used earlier to get the output laden with yelps).  However, when I did this again I got:

(gedit:5379): GnomeUI-warning**: while connecting to session manager: Authentication rejected, reason: None of the authentication protocols specified are supported and host-based authentication failed.

---

### Post by RedSquirrel on 2007-05-21
The file is /boot/grub/menu.lst NOT menu.1st

The character after the dot is an "l", as in "larry", not a "1".

To open it for editing, do:

```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by GregoryMA on 2007-05-23
Using menu.lst worked and I altered the commands but when I ran update-grub the reply was:

cp: cannot remove `/boot/grub/menu.lst~': Permission denied

Why is permission denied? and what do I have to do to be allowed to execute this command?

---

### Post by Pragmatist on 2007-05-23
you need to use **sudo** 
```
sudo update-grub
```

When prompted for a password, give your user password.

---

### Post by GregoryMA on 2007-05-24
SUCCESS!!!  Thank you everyone for your help.

---

