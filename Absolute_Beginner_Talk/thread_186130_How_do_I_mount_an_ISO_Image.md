---
title: "How do I mount an ISO Image?"
date: 2006-06-01
forum: Absolute Beginner Talk
---

### Post by michaeljb2005 on 2006-06-01
Is there a program that lets me mount an iso image without having to type "mount -o loop -t iso9660 filename.iso /mnt/iso" everytime?

---

### Post by richbarna on 2006-06-01
This link has a mount/ unmount right click script :-
[http://ubuntu.wordpress.com/2005/10/24/nautilus-script-to-mount-iso-files/]("http://ubuntu.wordpress.com/2005/10/24/nautilus-script-to-mount-iso-files/")

---

### Post by michaeljb2005 on 2006-06-01
[QUOTE=richbarna]This link has a mount/ unmount right click script :-
[http://ubuntu.wordpress.com/2005/10/24/nautilus-script-to-mount-iso-files/]("http://ubuntu.wordpress.com/2005/10/24/nautilus-script-to-mount-iso-files/")[/QUOTE]

Thanks I'll try it when I get home.

---

### Post by linuchsan on 2006-06-01
try kiso

---

### Post by michaeljb2005 on 2006-06-01
[QUOTE=linuchsan]try kiso[/QUOTE]

Sweetness!  Is that available in the repositories or will I have to build it?  Can't see it right now, I'm at work (using XP).

---

### Post by linuchsan on 2006-06-01
apt-cache search kiso
kiso - program to create manipulate and extract CD Image

---

### Post by michaeljb2005 on 2006-06-04
[QUOTE=linuchsan]apt-cache search kiso
kiso - program to create manipulate and extract CD Image[/QUOTE]

kiso does not mount images it only lets you burn and convert them basically.  The scripts I was referred to did nothing when I ran them from the Scripts menu.  I made the scripts executable and everything.

---

### Post by joshrobinson on 2006-06-04
```
sudo mkdir /media/iso
sudo modprobe loop
sudo mount file.iso /media/iso/ -t iso9660 -o loop
```

to unmount

```
sudo umount /media/iso/
```

---

### Post by joshrobinson on 2006-06-04
did you try the script in the comments of the page posted above? its a longer one, looks like its more usefull

sorry about the above post i didnt read your post good enough

---

### Post by michaeljb2005 on 2006-06-04
[QUOTE=joshrobinson]did you try the script in the comments of the page posted above? its a longer one, looks like its more usefull

sorry about the above post i didnt read your post good enough[/QUOTE]

I tried that one as well.  None of those seem to work for me for some reason.  I don't think I'm doing it wrong so I'm not sure what the issue is because I don't know what the code means.  I just copy paste make executable and use the script within nautilus.

---

### Post by linuchsan on 2006-06-05
[QUOTE=michaeljb2005]kiso does not mount images it only lets you burn and convert them basically.  The scripts I was referred to did nothing when I ran them from the Scripts menu.  I made the scripts executable and everything.[/QUOTE]

Yes it does mount an iso. Right klik on the file, KIso/Mount as virtual drive.

---

### Post by michaeljb2005 on 2006-06-05
[QUOTE=linuchsan]Yes it does mount an iso. Right klik on the file, KIso/Mount as virtual drive.[/QUOTE]

Does it only show that in KDE?

---

### Post by linuchsan on 2006-06-05
can't tell if you can use it with gnome ?
try from a terminal, kiso --help-all (see options --virtualdrive)

---

### Post by MetalMusicAddict on 2006-06-05
Look into a app called **nautilus-actions**. Then look at [THIS]("http://www.grumz.net/index.php?q=configlist&PHPSESSID=e0515b3b9994cad4a4d32182bfc347a0") page. There are some mount .iso plug-ins halfway down.

---

### Post by ryan76 on 2006-06-11
I used this to mount an ISO and play it:

sudo mount -o loop -t iso9660 kraftwerk1.iso  /mnt/ISO/

How do I unmount it and play a different one?

---

### Post by taurus on 2006-06-11
[QUOTE=ryan76]I used this to mount an ISO and play it:

sudo mount -o loop -t iso9660 kraftwerk1.iso  /mnt/ISO/

How do I unmount it and play a different one?[/QUOTE]
Umount it with
```

sudo umount /mnt/ISO

```

---

