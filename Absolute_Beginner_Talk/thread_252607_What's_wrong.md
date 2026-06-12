---
title: "What's wrong???"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by Russty of Oz on 2006-09-07
I still haven't been able to install a .tar.gz file yet.  I have tried quite a few but there is alway something wrong.  

The only one I have got anywhere with is kmediafactory, at least with that one I have got through the **./configure** stage!  But when I do **make**,  I get the folling output which seems to say that I don't have a version of ImageMagick >= 6.0  but I have checked an I do have version 6.2.4 installed.  So what is wrong??

Configure summary
----------------------------------------------------------------------
Mandatory
- FontConfig ..................... Yes
- msgfmt ......................... Yes
- zip ............................ Yes
- ImageMagick >= 6.0 ............. No
- dvdauthor ...................... Yes
- mjpegtools ..................... Yes
----------------------------------------------------------------------
Optional
- DV import plugin (libdv) ....... Yes
- DVD info dialog (libdvdread) ... Yes
- Own DVD player (libxine) ....... Yes
- Support theora files (libtheora) Yes
- Slideshow (dvd-slideshow) ...... Yes
- office macro install (unopkg) .. Yes
----------------------------------------------------------------------
Needed dependencies for building missing!!
----------------------------------------------------------------------
configure: error:


Can anyone help?

Russty.

---

### Post by croak77 on 2006-09-07
Try installing libmagick++9-dev

---

### Post by Russty of Oz on 2006-09-07
Thanks, that got me past that error!

**BUT**

Now when I do **make install** I get this!

russty@russty-desktop:~/Software/kmediafactory-0.5.2$ make install
Making install in doc
make[1]: Entering directory `/home/russty/Software/kmediafactory-0.5.2/doc'
Making install in .
make[2]: Entering directory `/home/russty/Software/kmediafactory-0.5.2/doc'
make[3]: Entering directory `/home/russty/Software/kmediafactory-0.5.2/doc'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/russty/Software/kmediafactory-0.5.2/doc'
make[2]: Leaving directory `/home/russty/Software/kmediafactory-0.5.2/doc'
Making install in en
make[2]: Entering directory `/home/russty/Software/kmediafactory-0.5.2/doc/en'
make[3]: Entering directory `/home/russty/Software/kmediafactory-0.5.2/doc/en'
make[3]: Nothing to be done for `install-exec-am'.
/bin/sh ../../admin/mkinstalldirs /usr/share/doc/HTML/en/kmediafactory
mkdir -p -- /usr/share/doc/HTML/en/kmediafactory
mkdir: cannot create directory `/usr/share/doc/HTML': Permission denied
make[3]: *** [install-nls] Error 1
make[3]: Leaving directory `/home/russty/Software/kmediafactory-0.5.2/doc/en'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/russty/Software/kmediafactory-0.5.2/doc/en'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/russty/Software/kmediafactory-0.5.2/doc'
make: *** [install-recursive] Error 1
russty@russty-desktop:~/Software/kmediafactory-0.5.2$         

WHY ME!?!? :(

---

### Post by croak77 on 2006-09-07
You need to run 'sudo make install' cause it will install in /usr. So you need to be root.

---

### Post by Russty of Oz on 2006-09-07
What is mean by you need to be root?  

Russty.

---

### Post by croak77 on 2006-09-07
You are running make install as a user. It is giving you an error 'mkdir: cannot create directory `/usr/share/doc/HTML': Permission denied'. You need to run it as root (sudo) cause a user does not have write permissions on /usr. Just like you install .debs with sudo, you need to install src programs as sudo too. 

```
sudo make install
```

---

### Post by Russty of Oz on 2006-09-07
Oh, is that all it means!  Well it did the trick.

Thanks for all the help.

Russty :)

---

### Post by deadgobby on 2006-09-07
Becareful from installing from source packs. Some times the program is all ready in Synaptic and can cause broken packages. Yet, installing from source is the only thing to install a program or drivers. It can be a little fustrating to install from source pack. Like tar or bin. Please book mark some help ways to install from source from
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
 It takes practice and it is not like at all a one click install. Some time soon as Linux is getting big and bad. You can take a tar or bin file and click on it like automantic like a wash machine. It is going to be soon and I can't wait. 
Gobby:-D

---

