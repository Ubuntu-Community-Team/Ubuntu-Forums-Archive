---
title: "i don't understand how to do this?..."
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by crunchystrike on 2006-09-05
1- download this script to your hard drive : [http://ting.homeunix.org/cvs_wine/GetCVSWineX](http://ting.homeunix.org/cvs_wine/GetCVSWineX)
2- as root type chmod 777 GetCVSWineX ..
3- and execute it ./getCvsWinex
follow the instructions ...
If the CVS checkout is not responding (it failed) you must get it sources manually.. get the file here: HEREthen untar it as usual : tar -zxvf cvswinex.tar.gz and then compile it in the source directory by doing a:
- ./configure --enable-opengl
- make
and finally : make install (as root)

like how do i download the script, when i put it into the browser, it was just a bunch of codes, what do i do with them? can i download it via terminal? help will be appreciated.

---

### Post by divgradcurl on 2006-09-05
Right click on the link and save it.
Its actually a shell script, not a text file.
When you have saved it you may want to change the file extension to .sh to remind you of what it is.

---

### Post by croak77 on 2006-09-05
Open a terminal and type```

wget http://ting.homeunix.org/cvs_wine/GetCVSWineX 
```

---

### Post by LadyDoor on 2006-09-05
> can i download it via terminal?

Yes, you sure can. Please install wget, first.

```
$ sudo aptitude install wget
```

Then do this:

```
$ wget http://ting.homeunix.org/cvs_wine/GetCVSWineX
```

Then, continue to follow the provided directions. Good luck!

--Door

---

### Post by crunchystrike on 2006-09-05
another example of how friendly, nice, and helpful the ubuntu/linux community is, thanks a bunch guys!

---

