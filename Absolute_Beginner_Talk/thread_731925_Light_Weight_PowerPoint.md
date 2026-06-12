---
title: "Light Weight PowerPoint"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by hikujk123 on 2008-03-22
I am running xubuntu gutsy gibbon on an AMD64 machine.  OpenOffice,org from the package manager is a bit buggy on my system.  Despite, reading a howto, I don't *really*  know how to to install it from [www.OpenOffice.org](www.OpenOffice.org).  I am now successfully using light weight programs.  I installed AbiWord and Gnumeric spreadsheet.  Is there a light weight equivalent to MS PowerPoint.

---

### Post by hikujk123 on 2008-03-22
Bump

---

### Post by hikujk123 on 2008-03-22
Bump.  If there is none, can someone walk me through installing openoffice from its website.  Someone gave me a link in an earlier post, but as I am new to linux, it did not help much.

---

### Post by angryfirelord on 2008-03-22
You should concentrate on installing software within the Ubuntu repos rather than from external sites. You can do it in one of two ways:

-open Synaptic and search for openoffice.org-impress
-do a **sudo apt-get install openoffice.org-impress**

If you want the whole openoffice suite, install the openoffice.org meta-package instead. If you're new to installing software on Ubuntu, read the synaptic and apt how-tos: 
[https://help.ubuntu.com/community/SynapticHowto]("https://help.ubuntu.com/community/SynapticHowto")
[https://help.ubuntu.com/community/AptGetHowto?action=show&redirect=AptGetHowTo]("https://help.ubuntu.com/community/AptGetHowto?action=show&redirect=AptGetHowTo")

---

### Post by kerry_s on 2008-03-22
there are 2 options
sudo apt-get install pptview
or
use google apps

i use google for all the office stuff now.

---

### Post by hikujk123 on 2008-03-22
> **angryfirelord said:**
> You should concentrate on installing software within the Ubuntu repos rather than from external sites. You can do it in one of two ways:

-open Synaptic and search for openoffice.org-impress
-do a **sudo apt-get install openoffice.org-impress**

If you want the whole openoffice suite, install the openoffice.org meta-package instead. If you're new to installing software on Ubuntu, read the synaptic and apt how-tos: 
[https://help.ubuntu.com/community/SynapticHowto]("https://help.ubuntu.com/community/SynapticHowto")
[https://help.ubuntu.com/community/AptGetHowto?action=show&redirect=AptGetHowTo]("https://help.ubuntu.com/community/AptGetHowto?action=show&redirect=AptGetHowTo")

As I said, the openoffice meta package is buggy on my computer.

---

### Post by Oldsoldier2003 on 2008-03-22
> **hikujk123 said:**
> As I said, the openoffice meta package is buggy on my computer.
update your package lists. The meta package shouldn't be any buggier on your computer than any other computer :)
```
sudo apt-get update
```

---

### Post by hikujk123 on 2008-03-23
I know it shouldn't be, but it is.  I am up-to-date.  Maybe because I have a 64 bit computer?  **Can someone please help me install it via the website?**  I like openoffice the best, but weird black lines appear all over the window when I use it.  They go away sometimes when I keep on typing but come back when I want to save it.  AbiWord doesn't do this, but I need a full suite (at least a MS Office Compatible spreadsheet (which I can use Gnumeric), word processor, and power point program.  I could run MS Office 2000 under wine but would prefer not to because it'll open my computer up to MS viruses.  I like open source/freeware.   KOffice is not MS compatible.

---

### Post by Ub1476 on 2008-03-23
Keyjnote can add effects and make a powerpoint/keynote presentation out of a PDF document. I suggest keyjnote-gui for a graphical front end to it.

And, you wont get Windows viruses by running a windows program under WINE.

---

### Post by hikujk123 on 2008-03-23
I guess it all goes back to Microsoft Office :(.  I was looking forward to being independent from MS.  Oh well.

---

### Post by angry_johnnie on 2008-03-25
If you want the latest version of OOo.

Here's a howto.

[http://ubuntuforums.org/showthread.php?t=398074](http://ubuntuforums.org/showthread.php?t=398074)

It was meant for an older version of open office.  But, other than that, it should be the same.  Just download the package, copy it to your /home folder, and follow the rest of the instructions.

---

### Post by hikujk123 on 2008-03-25
Thanks.  Where would I make the changes in the commands for 2.3.1.  I mean I know for the .tar.gz file I have to, but after that?

---

### Post by angry_johnnie on 2008-03-26
Remove open office.  If you don't know your version number, just go to synaptic and mark OOo.base OOo.calc OOo. math and so on for removal.  It will ask you to remove ubuntu-desktop.

Ubuntu-desktop is a metapackage, and can be safely removed.  However, I think an upgrade will require that you have it.  So, if you're planning to upgrade to Hardy, I'd say wait.  If you like to tinker, continue  :-)

Install alien.

```
sudo apt-get install alien
```

Download the tar.gz from openoffice.org.

Extract the files in it.

Open the newly created folder.

Inside it, there should be another folder, called RPMS

Open it, and then right-click somewhere and choose "open in terminal"

Convert the rpms to .deb packages.

```
sudo alien --scripts --keep-version -d *.rpm
```

Install the packages

```
sudo dpkg -i *.deb
```

Desktop integration and symbolic links

```
cd desktop-integration/
sudo dpkg -i openoffice.org-debian-menus_<YOUR VERSION>_all.deb
sudo ln -s /opt/openoffice.orgVERSION/program/swriter /usr/bin/swriter
sudo ln -s /opt/openoffice.orgVERSION/program/sbase /usr/bin/sbase
sudo ln -s /opt/openoffice.orgVERSION/program/scalc /usr/bin/scalc
sudo ln -s /opt/openoffice.orgVERSION/program/smath /usr/bin/smath
sudo ln -s /opt/openoffice.orgVERSION/program/sdraw /usr/bin/sdraw
sudo ln -s /opt/openoffice.orgVERSION/program/simpress /usr/bin/simpress
sudo ln -s /opt/openoffice.orgVERSION/program/soffice /usr/bin/soffice
sudo ln -s /opt/openoffice.orgVERSION/program/spadmin /usr/bin/spadmin
```

Replace VERSION with... well... your version :-)
Add them to your menus.
The command for each would be

/usr/bin/program

where program is something like swriter, sbase, scalc, and so on.

---

### Post by hikujk123 on 2008-03-30
I got to the part where I want to convert the RPMs to debs and got this error.

```

Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
                xargs -0 -r -i cp -a {} debian/jre
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: warning: format of 'NEEDED libmlib_image.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libawt.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libjava.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libjvm.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libjvm.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libjava.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libjava.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libjvm.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libjvm.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libjava.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libjvm.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libjava.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libnet.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libjava.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libjvm.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libjava.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libjvm.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libjava.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libjvm.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libjvm.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libjava.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libjvm.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libjava.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libjvm.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libjava.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libjli.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libjvm.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libjvm.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libjava.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libjvm.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libjvm.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libjava.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libjvm.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libverify.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libjvm.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libjava.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libjvm.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libjava.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libjava.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libjvm.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libjvm.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libawt.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libjava.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libjvm.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libodbcinst.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libodbc.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libjava.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libjvm.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libmlib_image.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libjvm.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libawt.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libjava.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libmlib_image.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libjvm.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libjava.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libjvm.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libjava.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libawt.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libmawt.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libjava.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libjvm.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libjava.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libjvm.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libmlib_image.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libjvm.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libawt.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libjava.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libjli.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libjli.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libjli.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libjli.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libjli.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libjli.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libjli.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libjli.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libjli.so' not recognized
dh_gencontrol
dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
find: jre-1.6.0_03: No such file or directory

```

What should I do?

---

### Post by angry_johnnie on 2008-03-30
Someone in the aforementioned thread said Sun doesn't make 64 bit java, and suggested one should install blackdown java instead.  It should be available in your repositories.  Other than that, it just beats me.  I've searched for a similar problem, but haven't found any answers.  You could try blackdown and see if it works.

But, why don't you try gnome-office instead?  It does not require java, and is much lighter than OOo.

If all else fails, you could still go back to your original state by typing

```
sudo aptitude install xubuntu-desktop
```

That way, it will look for all the things you might have removed, and install them again.

If you manage to get your hands on an already built 32 bit .deb package of the latest version of OOo, you could install it by

```
sudo dpkg --force-architecture -i <package>.deb
```

Sorry I can't be of more help.  I've searched for this and found nothing.  I hope someone who knows more than I do, can figure it out.

---

