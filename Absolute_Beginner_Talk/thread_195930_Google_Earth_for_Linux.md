---
title: "Google Earth for Linux"
date: 2006-06-13
forum: Absolute Beginner Talk
---

### Post by MarkSheely on 2006-06-13
Has anyone tried out Google Earth for Linux?  

[http://earth.google.com/download-earth.html](http://earth.google.com/download-earth.html)

Being the newbie that I am, I'm confused about what to do with the GoogleEarthLinux.bin file I downloaded from their site above.

Any help would be appreciated.  I'm excited to try this out, it looks improved substantially.

Thanks,
Mark
[email]marksheely@gmail.com[/email]

---

### Post by xfile087 on 2006-06-13
I think kwaanens showed a better way.

---

### Post by kwaanens on 2006-06-13
$ chmod +x GoogleEarthLinux.bin
$ ./GoogleEarthLinux.bin

Works like a charm!

- Ketil

---

### Post by MarkSheely on 2006-06-13
[QUOTE=kwaanens]$ chmod +x GoogleEarthLinux.bin
$ ./GoogleEarthLinux.bin

Works like a charm!

- Ketil[/QUOTE]

It certainly did work like a charm - thanks for the advice!  Its an impressive application, I'd recommend checking it out if you are interested in that sort of thing.

What does "chmod +x" mean?

Thanks again,
Mark 
[email]marksheely@gmail.com[/email]

---

### Post by LanceM on 2006-06-13
"chmod +x" makes the file executable.

---

### Post by msv240586 on 2006-06-13
Mmmm pretty cool, i was just thinking today "Wonder when they going to amke a google earth for good ol linux"

---

### Post by henkk78 on 2006-06-13
Thanks for the help! I needed the exact same answer! 

btw, how do I now go about getting my bookmarks from GE for Windows from my mounted Windows partition?

./henk

---

### Post by kwaanens on 2006-06-13
Just locate myspaces.kml in your windows partition. Should be in your user files somewhere. (/Documents and settings/[Username]/Program files/Google/GoogleEarth on my computer)
Copy it to ~/.googleearth
...and you're done :)

- Ketil

---

### Post by cyborg939 on 2006-06-13
How do you do that and where? Also, how do you install downloaded zipped files that end it .tar.gz?

---

### Post by gommle on 2006-06-13
Doubleclick it, click "extract", choose desktop or home.

---

### Post by u.b.u.n.t.u on 2006-06-13
The commands in the terminal are literally:

```
chmod +x GoogleEarthLinux.bin
```

and then

```
./GoogleEarthLinux.bin
```

The "./" idicates that you are in the same directory as the file you wish to access, eg "GoogleEarthLinux.bin" in this case. Putting the file in your home directory is probably easiest, rather than typing out a path.

```
XYZ@XYZ-desktop:~$ chmod +x GoogleEarthLinux.bin
XYZ@XYZ-desktop:~$ ./GoogleEarthLinux.bin
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 4.0.1563..................................................................
Installing mimetypes...
Running /usr/bin/update-mime-database /home/XYZ/.local/share/mime
***
* Updating MIME database in /home/XYZ/.local/share/mime...
Wrote 3 strings at 20 - 88
Wrote aliases at 88 - 8c
Wrote parents at 8c - 90
Wrote literal globs at 90 - 94
Wrote suffix globs at 94 - 11c
Wrote full globs at 11c - 120
Wrote magic at 120 - 12c
Wrote namespace list at 12c - 130
***
Installing desktop menu entries...
XYZ@XYZ-desktop:~$
```

---

### Post by kystorms on 2007-04-23
Hi

I downloaded google earth to my desktop, now I am not sure how to proceed. where can we go to get the info on how to download and open the different files we download ( ie yahoo mess, or what ever files) I have seen that we must point to our files in our terminal, but I do not know how that is done.

---

### Post by Tulx on 2007-04-23
I used Automatix2 to install Google Earth. Very simple, as I am noob i didnt have to search for codes or anything.

---

### Post by Perfect Storm on 2007-04-23
no need for that. Just add medieubuntu (from add/remove application), then googleearth is there. Can't be more easier.

---

### Post by kittyhawk63 on 2007-04-23
I have an ATI Radeon 9200 SE video card. I don't know, but is that keeping Google Earth from loading? It opens up to the initial splash screen and then freezes. It will not go beyond that. I've not been able to get it to load in Dapper, Edgy and now Feisty.
kh

---

### Post by yock on 2007-04-29
> **kittyhawk63 said:**
> I have an ATI Radeon 9200 SE video card. I don't know, but is that keeping Google Earth from loading? It opens up to the initial splash screen and then freezes. It will not go beyond that. I've not been able to get it to load in Dapper, Edgy and now Feisty.
khI have this same problem. When running it for the first time from the installer, it freezes at "Installing desktop menu entries..."

---

