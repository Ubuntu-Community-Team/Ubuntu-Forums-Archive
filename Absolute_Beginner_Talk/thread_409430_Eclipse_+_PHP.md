---
title: "Eclipse + PHP"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by mech7 on 2007-04-14
I am trying to install php on the eclipse ide.. i think i need to unpack the plugin in the dir from eclipse? but where does it install:confused: I can't find it anywhere?

---

### Post by LaurelLynn on 2007-04-14
Dear mech7,

That would depend on the type of file downloaded.  Look at the extension at the end of the filename.

If you can´t find where it was downloaded to, go to the top bar on your Desktop and select  ¨Places->Home Folder¨.  Hit the search button and enter the filename.

If the extension is ¨.deb¨ then:

dpkg   -i  the-filename.deb

if the extension is ¨.tar¨ or ¨.tar.gz¨, find the file on your Desktop or through ¨Places->Home Folder¨ as above.  Double-click on it and hit the Extract button.  That should give you a folder with the same name (without the extension)  in the same location. 

If there is a README file, follow it´s instructions to install.  If not there will probably be a file named configure and a makefile.   The following commands usually install it (make will figure out where to put it):

./configure
make
make install

If the file extension is ¨.eclipseextension¨ you have to install it from within eclipse.  Help->Software Updates->Find and Install...

Select   ¨Search for new features¨ Hit the Next button, then the ¨New Archived Site..¨ button. This should open the home folder then browse and select the folder with the installation file.

If you have something unusual like a ¨.rpm¨ file, know first that doubtful it will work on Ubuntu, but we can tell you how to use alien to import it, if you want to try.

---

### Post by annda on 2007-04-14
as LaurenLynn says, you can install the phpeclipse plugin from within eclipse. you just need to add the url that is listed on phpeclipse's website. however, it WILL NOT WORK with eclipse over 3.1 and the one in repositories is 3.2. so you need to get older eclipse first.

---

### Post by mech7 on 2007-04-14
> **annda said:**
> as LaurenLynn says, you can install the phpeclipse plugin from within eclipse. you just need to add the url that is listed on phpeclipse's website. however, it WILL NOT WORK with eclipse over 3.1 and the one in repositories is 3.2. so you need to get older eclipse first.

Hmm why is this? when i download the all in one package i do get 3.2 with PHP :confused:

Also when i extract the tar.gz file and do make it does not work :(

bash: mAKE: command not found
chris@chris-laptop:~/Desktop/eclipse$ make
make: *** No targets specified and no makefile found.  Stop.
chris@chris-laptop:~/Desktop/eclipse$ make install
make: *** No rule to make target `install'.  Stop.
chris@chris-laptop:~/Desktop/eclipse$

edit* 
Ok i just installed it through add/remove programs and then downloaded all in one, and pasted all files in user/bin/eclipse seems to work :p probably not the right way though :p

---

### Post by LaurelLynn on 2007-04-14
Any way it works is the right way...up util it doesn´t.  Just be prepared to re-install from scratch if something goes wrong.

---

