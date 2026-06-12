---
title: "Adding fonts to OOo"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by hikujk123 on 2008-04-13
OOo 2.3.1 refused to work properly on my Gutsy machine, so I turned to OOo 2.4.  Ah..but of course, I have an amd64 computer, so I can't install from the OOo website.  My solution: I installed the windows version of OOo with wine, and everything seems to work pefectly and much faster than it ever did before.  Now I notice that neither Times New Roman nor any other MS Word fonts/fonts that I have in Windows when running OOo appear on my list.  I get the standard Ubuntu fonts that frankly do not work for me.  How do I add additional fonts to the OOo wine arrangement?  I would at least like to get Times New Roman.  I am not sure whether these fonts were native to windows or msword, but want them badly.

---

### Post by hikujk123 on 2008-04-13
I am not sure whether or not running OOo under wine will affect the solution of this problem or not.

---

### Post by forrestcupp on 2008-04-13
If you have access of windows, just copy all of your fonts from C:\Windows\Fonts to /home/*username*/.wine/drive_c/windows/fonts

Substitute your own username of course.

---

### Post by hikujk123 on 2008-04-13
I am not dual booting.  This machine only has ubuntu with gnome on it.  When I was talking about windows, I was talking about my other machine/before I erased windows on this computer.

---

### Post by hikujk123 on 2008-04-13
Found a way by googling it.  For future reference here are the codes:

```
 sudo apt-get install msttcorefonts 
```
```
 $sudo fc-cache -fv 
```


You should definitely try OOo with wine, it starts-up much faster than the OOo metapackage (which doesn't even work on this machine).  Also, it makes updating a whole lot easier.

---

### Post by forrestcupp on 2008-04-14
I didn't realize that msttcorefonts would work with wine apps.  I thought they were only for native apps.  

But if there are any other fonts you need, you can usually find a download of the font file and copy it to the folder I mentioned.  Or if you need other fonts for native apps, you can create a directory called **/.fonts** in your /home folder and put the files there.

---

### Post by hikujk123 on 2008-04-14
It did work, but guess what?  Now I get black lines when running OOo in wine too!  I don't know what is wrong!!!!!

---

### Post by stchman on 2008-04-14
> **hikujk123 said:**
> It did work, but guess what?  Now I get black lines when running OOo in wine too!  I don't know what is wrong!!!!!

There is no guarantee that WINE will run OO2.4 well.

If you want OO2.4 and you have 64bit OS you will need to build OO2.4 from source.  You can get the source here.

[http://download.openoffice.org/2.4.0/source.html](http://download.openoffice.org/2.4.0/source.html)

Maybe OO will start making 64bit debs soon.

---

### Post by calc on 2008-04-20
> **hikujk123 said:**
> Found a way by googling it.  For future reference here are the codes:

```
 sudo apt-get install msttcorefonts 
```
```
 $sudo fc-cache -fv 
```


You should definitely try OOo with wine, it starts-up much faster than the OOo metapackage (which doesn't even work on this machine).  Also, it makes updating a whole lot easier.

OOo takes between 1-2 seconds to start for me, perhaps you are just seeing the general speedup from 2.4 which from what I hear from other users is much faster on Ubuntu than older releases.

---

### Post by calc on 2008-04-20
> **hikujk123 said:**
> It did work, but guess what?  Now I get black lines when running OOo in wine too!  I don't know what is wrong!!!!!

As I mentioned in the other thread this is almost certainly due to your SiS video chip. SiS has extremely small market share in general and are Linux hostile on top of that (from what I read on the net anyway) which in turn leads to them having buggy drivers for their video chips.

---

