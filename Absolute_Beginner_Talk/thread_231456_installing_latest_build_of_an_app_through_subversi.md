---
title: "installing latest build of an app through subversion (svn)"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by hanzj on 2006-08-07
So I want to install the latest build of gpodder.  [http://perli.net/projekte/gpodder/downloads.html](http://perli.net/projekte/gpodder/downloads.html) says that I should do
```
svn co http://svn.berlios.de/svnroot/repos/gpodder/trunk gpodder
```

Could anyone tell me the next step?

---

### Post by paulyche on 2006-08-07
I've just been looking for the an answer to the same problem. The answer is to install the "subversion" pacakge, I was searching synaptic for "svn".

---

### Post by hanzj on 2006-08-07
I have already installed subversion. 
I ran that svn co ... command after installing subversion. 

Is the app now installed? Don't I have to do something else?

---

### Post by paulyche on 2006-08-07
Oops. I haven't answered your question have I?

I'm doing my 1st cvs/svn build install (amarok) right now so if no-one more experienced replies I'll share any wisdom I acquire.

---

### Post by paulyche on 2006-08-07
Try

```
sudo ./configure
``` in the downloaded source directory

then

```
sudo make
```
```
sudo make install
```

---

### Post by hanzj on 2006-08-07
paul, thanks. 
The readme file didn't have installation instructions, but the INSTALL file does. In the case for gpodder, all that's needed is 
sudo make install

---

### Post by hanzj on 2006-08-07
after running "sudo make install" may  i now delete the gpodder directory that "svn co ..." made?

---

### Post by mlind on 2006-08-07
> **hanzj said:**
> after running "sudo make install" may  i now delete the gpodder directory that "svn co ..." made?

You probably already had **build-essential** package installed (and other build dependencies too), otherwise running **make** would have produced an error.
You shouldn't remove local gpodder build tree just yet or uninstalling might get difficult. Ofter (not always..) Makefile(s) contain **uninstall** target which will contain instructions for uninstalling the target.

```

make uninstall

```

But you're totally missing benefits of debian build system if you install packages this way. I suggest you to study how to build packages 'the debian way' or find pre-built binary (.deb file) of gpodder svn version. One way to do this is to download current Ubuntu/Debian gpodder source package and apply old packaging information to downloaded svn module (sources).

---

### Post by hanzj on 2006-08-09
According to the [downloads page]("http://perli.net/projekte/gpodder/downloads.html"), I can get the latest development version of gpodder by doing: 
```
svn co http://svn.berlios.de/svnroot/repos/gpodder/trunk gpodder
```

According to the [ChangeLog]("http://svn.berlios.de/svnroot/repos/gpodder/trunk/ChangeLog"), the latest development version is  Monday, August 7.

When I now open gpodder, i get this screen:

> gPodder development version 0.8.0+svn20060730
Use at your own risk, but also enjoy new features :)


Should not the window instead say > gPodder development version 0.8.0+svn2006**[COLOR="DarkOrange"]0807[/COLOR]**
 ?

I don't think the problem is just having a typo. I don't think I have the 20060807 version.

How can I get the really latest version (20060807)? Am I doing something wrong?

[SIZE="6"]:confused: :confused: [/SIZE]

---

### Post by hanzj on 2006-08-09
Here is the answer I have received:

> This string isn't always updated when commiting changes. Anyway: In your checked out source, you should simply be able to run "svn up" and grab the latest changes.

---

### Post by hanzj on 2006-08-09
I went to ~/gpodder/gpodder and ran "svn up".
The printout said "At revision 153." I ran gpodder again but it still says "gPodder development version
0.8.0+svn20060730"

So I thought that perhaps I needed to do
svn co [http://svn.berlios.de/svnroot/repos/gpodder/trunk](http://svn.berlios.de/svnroot/repos/gpodder/trunk) gpodder again, so I did. The last line of the printout says "Checked out revision 153."

I opened gpodder again, yet it still has the 20070730 version.

As you can probably tell, I'm just guessing my way through. Did I do "svn up" in the right folder? Is there anything else I should do after running "svn up"?

---

### Post by mlind on 2006-08-09
> **hanzj said:**
> I went to ~/gpodder/gpodder and ran "svn up".
The printout said "At revision 153." I ran gpodder again but it still says "gPodder development version
0.8.0+svn20060730"

So I thought that perhaps I needed to do
svn co [http://svn.berlios.de/svnroot/repos/gpodder/trunk](http://svn.berlios.de/svnroot/repos/gpodder/trunk) gpodder again, so I did. The last line of the printout says "Checked out revision 153."

I opened gpodder again, yet it still has the 20070730 version.

As you can probably tell, I'm just guessing my way through. Did I do "svn up" in the right folder? Is there anything else I should do after running "svn up"?

You did it right, it looks like upstream haven't updated the version info.

---

### Post by hanzj on 2006-08-09
>  it looks like upstream haven't updated the version info.

I contacted the developer directly and it was him who said that the latest version is 20060807. Can we confirm that the problem is in fact based on the upstream not being updated yet?

---

### Post by mlind on 2006-08-09
> **hanzj said:**
> I contacted the developer directly and it was him who said that the latest version is 20060807. Can we confirm that the problem is in fact based on the upstream not being updated yet?

After you've checke'd out the module, did you compile and install it?
I executed dist target and gpodder version seems to be 0.8.0+svn20060808.

---

### Post by hanzj on 2006-08-09
please tell me exactly what commands you ran.

---

### Post by mlind on 2006-08-09
> **hanzj said:**
> please tell me exactly what commands you ran.

There's two file on gpodder directory, README and INSTALL which you should read. Those contain the install instructions.

---

### Post by hanzj on 2006-08-10
I re-read README and INSTALL. All INSTALL says is "make install". Neither mentions the "dist target" command you ran. 

Please advise.

---

### Post by hanzj on 2006-08-10
> **mlind said:**
> After you've checked out the module, did you compile and install it?
I executed dist target and gpodder version seems to be 0.8.0+svn20060808.

you have 2006080**[COLOR="Red"]8[/COLOR]**? 8-[ I thought the latest version was 2006080**[COLOR="#ff0000"]7[/COLOR]**?

---

### Post by paulyche on 2006-08-10
These are daily builds.

20060807 means 07 August 2006.

---

### Post by hanzj on 2006-08-10
Well, the builds may be daily, but the builds are not put out daily.

---

### Post by mlind on 2006-08-10
> **hanzj said:**
> you have 2006080**[COLOR="Red"]8[/COLOR]**? 8-[ I thought the latest version was 2006080**[COLOR="#ff0000"]7[/COLOR]**?

Type **make** in gpodder folder to see all the targets. You'll just have to follow the README install instructions.

---

### Post by hanzj on 2006-08-10
> **mlind said:**
> Type **make** in gpodder folder to see all the targets. You'll just have to follow the README install instructions.

[PHP]~/gpodder/gpodder$ make

make test            run gpodder in local directory
make cl              make new changelog entry (1)
make release         create source tarball in "dist/"
make install         install gpodder into "/usr/"
make uninstall       uninstall gpodder from "/usr/"
make generators      re-generate manpage and run tepache
make messages        rebuild messages.pot from new source
make clean           remove generated+temp+*.pyc files
make distclean       do a "make clean" + remove "dist/"
[/PHP]



> **mlind said:**
>  You'll just have to follow the README install instructions.

Here's the README text on install:

```
 3) How to run/install
 =====================

 Extract the tar archive somewhere into your home directory and cd into 
 the directory where you extracted it, for example:

   tar xzvf gpodder-0.8.0.tar.gz
   cd gpodder-0.8.0/
 
 After that you can start gPodder by starting it with the following 
 command:

   make test
 
 If this works out, close gPodder again and install it system-wide:

   sudo make install

 This will install gPodder in standard locations. After the installation 
 routine (hopefully) finished successfully, you might run gPodder from 
 any path on your machine by simply typing:

   gpodder
```




> **mlind said:**
> I executed dist target and gpodder version seems to be 0.8.0+svn20060808.

I did **make test** and it opened up gpodder with a  screen that said that I was using version svn20060808. :D  But what about your reference to **dist target**? I don't see that command in README nor in **make**.

---

### Post by mlind on 2006-08-10
> **hanzj said:**
> [PHP]~/gpodder/gpodder$ make

make test            run gpodder in local directory
make cl              make new changelog entry (1)
make release         create source tarball in "dist/"
make install         install gpodder into "/usr/"
make uninstall       uninstall gpodder from "/usr/"
make generators      re-generate manpage and run tepache
make messages        rebuild messages.pot from new source
make clean           remove generated+temp+*.pyc files
make distclean       do a "make clean" + remove "dist/"
[/PHP]



Here's the README text on install:

```
 3) How to run/install
 =====================

 Extract the tar archive somewhere into your home directory and cd into 
 the directory where you extracted it, for example:

   tar xzvf gpodder-0.8.0.tar.gz
   cd gpodder-0.8.0/
 
 After that you can start gPodder by starting it with the following 
 command:

   make test
 
 If this works out, close gPodder again and install it system-wide:

   sudo make install

 This will install gPodder in standard locations. After the installation 
 routine (hopefully) finished successfully, you might run gPodder from 
 any path on your machine by simply typing:

   gpodder
```






I did **make test** and it opened up gpodder with a  screen that said that I was using version svn20060808. :D  But what about your reference to **dist target**? I don't see that command in README nor in **make**.

I meant **release** target :-\" , but that's not necessary for install anyway.

---

