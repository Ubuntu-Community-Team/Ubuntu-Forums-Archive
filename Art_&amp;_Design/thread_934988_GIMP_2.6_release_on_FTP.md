---
title: "GIMP 2.6 release on FTP"
date: 2008-10-01
forum: Art &amp; Design
---

### Post by Half-Left on 2008-10-01
> GIMP approaches the next stable release and only a handful bugs are left to be fixed before GIMP 2.6 is ready.**2008-09-17**

[ftp://ftp.gimp.org/pub/gimp/v2.6/](ftp://ftp.gimp.org/pub/gimp/v2.6/)

2.6 here already, great news :)

If you want to compile manually I can show you how so just ask.

**Building GIMP from Source**

Firstly sudo apt-get install build-essential

Latest babl [ftp://ftp.gtk.org/pub/babl/](ftp://ftp.gtk.org/pub/babl/) <--Install first
Latest GEGL [ftp://ftp.gimp.org/pub/gegl/](ftp://ftp.gimp.org/pub/gegl/)

Both of these should be **./configure --prefix=/usr**

Then the following packages(some I have forgot, sorry but GIMP configure will tell you :p )

libgtk-dev
xserver-xorg-dev
python-2.5-dev
intltool
libgnomeui-dev

Remove your GIMP2.4 packages and run **./configure --prefix=/usr** then **make** then **sudo make install** in your GIMP-2.6.0 directory. Run **make clean** to clean your directory after. Good luck :)

---

### Post by exploder on 2008-10-01
Hopefully this will make it into getdeb.net along with it's dependencies.

---

### Post by Guruji on 2008-10-01
checking getdeb every 2min hehe.. can't wait to get it!

---

### Post by jeffegg2 on 2008-10-01
Yes please! How to do a manual install!!!

Ubuntu 8.04 amd64.

---

### Post by Kakurady on 2008-10-01
Ubuntu 8.04 i686. 

babl-0.0.22 compile successful.
Cannot compile GEGL: 
```
./clones.xml
/home/nekoyasha/Downloads/gegl-0.0.18/bin/.libs/lt-gegl: error while loading shared libraries: libbabl-0.0.so.0: cannot open shared object file: No such file or directory

```
BABL was installed to /usr/local/lib/.

---

### Post by plean on 2008-10-01
Well I have absolutely the same problem as Kakurady ...

---

### Post by binbash on 2008-10-01
.deb is online at getdeb

---

### Post by maruchan on 2008-10-01
Somebody post the main getdeb GIMP deb please? Getdeb is not serving up the file here...I got all the other files except that one. :confused:

---

### Post by binbash on 2008-10-01
main : 

[http://ftp1.srv.endpoint.nu/pub/software/getdeb/ubuntu/hardy/gi/gimp_2.6.0-1~getdeb1_i386.deb](http://ftp1.srv.endpoint.nu/pub/software/getdeb/ubuntu/hardy/gi/gimp_2.6.0-1~getdeb1_i386.deb)

---

### Post by scpatl4now on 2008-10-01
YEA!!!  I installed it and it works!!!

---

### Post by TrikeKid on 2008-10-01
> **Half-Left said:**
> 
If you want to compile manually I can show you how so just ask.

Please do! I downloaded all the files off of get deb and tried to install them with package manager and it's just causing all kinds of problems and giving me broken package messages and wanting me to do things like uninstall ubuntu desktop to fix it.

---

### Post by nulall on 2008-10-01
I also downloaded them all from getdeb but can't install. Likely a stupid question, but how do I got about doing this?

---

### Post by qwuery on 2008-10-01
> **nulall said:**
> I also downloaded them all from getdeb but can't install. Likely a stupid question, but how do I got about doing this?
See [http://meetthegimp.org/gimp-26-as-promised-released-on-september-31/]("http://meetthegimp.org/gimp-26-as-promised-released-on-september-31/")
(I haven't tried it myself however)

---

### Post by fujikofujio on 2008-10-01
> **scpatl4now said:**
> YEA!!!  I installed it and it works!!!

did you install the one posted by binbash?

[http://ftp1.srv.endpoint.nu/pub/software/getdeb/ubuntu/hardy/gi/gimp_2.6.0-1~getdeb1_i386.deb](http://ftp1.srv.endpoint.nu/pub/software/getdeb/ubuntu/hardy/gi/gimp_2.6.0-1~getdeb1_i386.deb)

or the one from getdeb?

---

### Post by Buster95 on 2008-10-01
> **binbash said:**
> main : 

[http://ftp1.srv.endpoint.nu/pub/software/getdeb/ubuntu/hardy/gi/gimp_2.6.0-1~getdeb1_i386.deb](http://ftp1.srv.endpoint.nu/pub/software/getdeb/ubuntu/hardy/gi/gimp_2.6.0-1~getdeb1_i386.deb)

This didn't work for me. Download seemed to run and files appeared in usr/bin and usr/lib so I assume it went OK. However, the package installer displayed an error message: "Dependency is not satisfiable: gimp-data"

Any ideas on what this means?

Thanks

---

### Post by pBeseda on 2008-10-02
Oh boy, "Dependency is not satisfiable: gimp-data"

Hmm.... thanks for the help with this problem guys.

---

### Post by binbash on 2008-10-02
Heyyy i only posted main file because a member said he cant download it!! 

Download everything to a new folder :

[http://www.getdeb.net/release/3233](http://www.getdeb.net/release/3233)

And do this :

sudo dpkg -i *.deb 

then remove the debs.

---

### Post by Half-Left on 2008-10-02
I was going to post how to build manually but being as getdebs has it now, you can make it easy on yourself. :)

---

### Post by TrikeKid on 2008-10-02
> **binbash said:**
> Heyyy i only posted main file because a member said he cant download it!! 

Download everything to a new folder :

[http://www.getdeb.net/release/3233](http://www.getdeb.net/release/3233)

And do this :

sudo dpkg -i *.deb 

then remove the debs.

Care to elaborate for the less literate? That command accomplishes nothing for me.

---

### Post by Death Dream on 2008-10-02
> **pBeseda said:**
> Oh boy, "Dependency is not satisfiable: gimp-data"

Yeah I got the same problem here. Make sure you download and install the .debs it says you are missing. Seems to be fixing my prob.

Edit: yeah, download all the .deb files and install each one it says you do not have before the other. Pretty strait forward after you figure that part out.

~Death Dream~

---

### Post by neoanderthal on 2008-10-02
> **Half-Left said:**
> I was going to post how to build manually but being as getdebs has it now, you can make it easy on yourself. :)

I'd be interested in seeing it, Half-Left. I installed from the DEBs, but the main reason is because I am having a terrible time finding the libs and such I need to build stuff. It took me 30 minutes of trial and error and google to finally uncover all of the dependencies I needed to build Gnomint. Is there a way that I can install like a 'developer's package' or something for Ubuntu?
You'll have to forgive me, I'm used to FreeBSD, where I could specify at install time if I wanted source code installed. I can't seem to figure it out for Ubuntu.

---

### Post by maruchan on 2008-10-02
I like 2.6 a lot but I ended up replacing the splash screen with my own. I've attached it to this post. If you like it, save it as "gimp-splash.png" in your /home/username/.gimp-2.6 folder.

---

### Post by binbash on 2008-10-02
> **TrikeKid said:**
> Care to elaborate for the less literate? That command accomplishes nothing for me.

dude you will download all the .debs to a folder.And you will go to that folder at terminal and you will install all debs with that command that is all

---

### Post by pBeseda on 2008-10-02
It works! All I needed was the libpoppler-glib2. I'm using Intrepid Ibex, so I added the security.ubuntu repo to my software source, tada, installed libpoppler-glib2, GIMP, all the rest. Thanks everyone.

---

### Post by dmn_clown on 2008-10-02
> **Kakurady said:**
> Ubuntu 8.04 i686. 

babl-0.0.22 compile successful.
Cannot compile GEGL: 
```
./clones.xml
/home/nekoyasha/Downloads/gegl-0.0.18/bin/.libs/lt-gegl: error while loading shared libraries: libbabl-0.0.so.0: cannot open shared object file: No such file or directory

```
BABL was installed to /usr/local/lib/.

you have to run ldconfig after you install babl (and gegl or any shared object, for that manner) manually.

```
sudo ldconfig
```

---

### Post by Buster95 on 2008-10-02
> **binbash said:**
> dude you will download all the .debs to a folder.And you will go to that folder at terminal and you will install all debs with that command that is all

Still no success.
I initially assumed that the dependency issue was related to the sequence of installation of the various components. If that was the case, a repeat of the depackaging command should have worked. Instead I got the message below.

I had unloaded the previous version (GIMP-2.4.5) via synaptic before I started this adventure with GIMP-2.6, but it appears that that wasn't enough.

Any advice? How do I find the "right" gimp-data file?

Cheers

Extracted from sudo dpkg on terminal

(Reading database ... 165344 files and directories currently installed.)
Preparing to replace gimp 2.6.0-1~getdeb1 (using gimp_2.6.0-1~getdeb1_i386.deb) ...
Unpacking replacement gimp ...
Preparing to replace gimp-python 2.6.0-1~getdeb1 (using gimp-python_2.6.0-1~getdeb1_i386.deb) ...
Unpacking replacement gimp-python ...
Preparing to replace libbabl-0.0-0 0.0.22-1~getdeb1 (using libbabl-0.0-0_0.0.22-1~getdeb1_i386.deb) ...
Unpacking replacement libbabl-0.0-0 ...
Preparing to replace libgegl-0.0-0 0.0.18-1~getdeb1 (using libgegl-0.0-0_0.0.18-1~getdeb1_i386.deb) ...
Unpacking replacement libgegl-0.0-0 ...
Preparing to replace libgimp2.0 2.6.0-1~getdeb1 (using libgimp2.0_2.6.0-1~getdeb1_i386.deb) ...
Unpacking replacement libgimp2.0 ...
[COLOR="Red"]dpkg: dependency problems prevent configuration of gimp:
 gimp depends on gimp-data (>= 2.6.0); however:
  Version of gimp-data on system is 2.4.5-1ubuntu2.[/COLOR]
dpkg: error processing gimp (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gimp-python:
 gimp-python depends on gimp (= 2.6.0-1~getdeb1); however:
  Package gimp is not configured yet.
dpkg: error processing gimp-python (--install):
 dependency problems - leaving unconfigured
Setting up libbabl-0.0-0 (0.0.22-1~getdeb1) ...

Setting up libgegl-0.0-0 (0.0.18-1~getdeb1) ...

Setting up libgimp2.0 (2.6.0-1~getdeb1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 gimp
 gimp-python

---

### Post by Buster95 on 2008-10-03
Following on from my last post.
Assuming that something didn't download sweetly (although I don't know enough to know what!), I removed it all and started again. The depackage generated no faults, but the GIMP splash screen initially stalled on "scanner plug-ins".

I removed all scanner-related plugins and the launch was able to complete. I haven't yet checked whether everything works, but so far so good.

Thanks everyone for the guidance.

Cheers

---

### Post by Half-Left on 2008-10-03
I've added some instructions on the front page about compiling GIMP, sorry I've forgot about some of the deps you need but Ubuntu has them, running ./configure will tell you.

---

### Post by TrikeKid on 2008-10-03
> **Buster95 said:**
> Still no success.
I initially assumed that the dependency issue was related to the sequence of installation of the various components. If that was the case, a repeat of the depackaging command should have worked. Instead I got the message below.

I had unloaded the previous version (GIMP-2.4.5) via synaptic before I started this adventure with GIMP-2.6, but it appears that that wasn't enough.

Any advice? How do I find the "right" gimp-data file?

Cheers

Extracted from sudo dpkg on terminal

(Reading database ... 165344 files and directories currently installed.)
Preparing to replace gimp 2.6.0-1~getdeb1 (using gimp_2.6.0-1~getdeb1_i386.deb) ...
Unpacking replacement gimp ...
Preparing to replace gimp-python 2.6.0-1~getdeb1 (using gimp-python_2.6.0-1~getdeb1_i386.deb) ...
Unpacking replacement gimp-python ...
Preparing to replace libbabl-0.0-0 0.0.22-1~getdeb1 (using libbabl-0.0-0_0.0.22-1~getdeb1_i386.deb) ...
Unpacking replacement libbabl-0.0-0 ...
Preparing to replace libgegl-0.0-0 0.0.18-1~getdeb1 (using libgegl-0.0-0_0.0.18-1~getdeb1_i386.deb) ...
Unpacking replacement libgegl-0.0-0 ...
Preparing to replace libgimp2.0 2.6.0-1~getdeb1 (using libgimp2.0_2.6.0-1~getdeb1_i386.deb) ...
Unpacking replacement libgimp2.0 ...
[COLOR="Red"]dpkg: dependency problems prevent configuration of gimp:
 gimp depends on gimp-data (>= 2.6.0); however:
  Version of gimp-data on system is 2.4.5-1ubuntu2.[/COLOR]
dpkg: error processing gimp (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gimp-python:
 gimp-python depends on gimp (= 2.6.0-1~getdeb1); however:
  Package gimp is not configured yet.
dpkg: error processing gimp-python (--install):
 dependency problems - leaving unconfigured
Setting up libbabl-0.0-0 (0.0.22-1~getdeb1) ...

Setting up libgegl-0.0-0 (0.0.18-1~getdeb1) ...

Setting up libgimp2.0 (2.6.0-1~getdeb1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 gimp
 gimp-python
The right gimp-data file is on the getdeb page.

I installed them with Gdebi instead of terminal, might have taken a bit longer but it worked. Double click on the main gimp package, and it will tell you which dependency you're missing, install that one then try it again and it tells you which to install next and so on.

---

### Post by dmn_clown on 2008-10-04
> **Half-Left said:**
> I've added some instructions on the front page about compiling GIMP, sorry I've forgot about some of the deps you need but Ubuntu has them, running ./configure will tell you.

Please do not manually install anything in /usr unless you want the hassle of conflicting versions of libs when babl and gegl enter main.  There is no guarantee that the packaged version of the libs will overwrite your manually installed versions.

/usr/local or /opt will both work equally well and make it easier on yourself as long as those paths are included in ld.so.conf and you remember to run ldconfig after your make install.

---

### Post by silkstone on 2008-10-04
It's a matter of choice, obviously, but I installed 2.6 using the six .deb files from getdeb, and after playing with it for a while I uninstalled it and went back to the older version.

I didn't find anything new in 2.6 that I really wanted, and there were a few bugs - on my machine, at least. For instance, F11 displayed full-screen but with the toolbox and other windows on top of the image, which isn't much use. I tried GEGL but it was very slow.

Your experience may be different, but I wouldn't rush to upgrade to 2.6 right now.

---

### Post by Half-Left on 2008-10-04
> **dmn_clown said:**
> Please do not manually install anything in /usr unless you want the hassle of conflicting versions of libs when babl and gegl enter main.  There is no guarantee that the packaged version of the libs will overwrite your manually installed versions.

/usr/local or /opt will both work equally well and make it easier on yourself as long as those paths are included in ld.so.conf and you remember to run ldconfig after your make install.

Well if your manually compiling it you shouldn't be using any packages, using /usr as the natural path. This is why I said remove your GIMP-2.4.

---

### Post by dmn_clown on 2008-10-04
> **Half-Left said:**
> Well if your manually compiling it you shouldn't be using any packages, using /usr as the natural path. This is why I said remove your GIMP-2.4.

You are misunderstanding me, let me rephrase it:

When you dist-upgrade your system to the next release that includes a packaged version of babl and gegl there is no guarantee that they will be overwritten when you install the packaged versions.

That is why /usr/local or /opt is a much better place to manually install software.

---

### Post by Half-Left on 2008-10-04
> **dmn_clown said:**
> You are misunderstanding me, let me rephrase it:

When you dist-upgrade your system to the next release that includes a packaged version of babl and gegl there is no guarantee that they will be overwritten when you install the packaged versions.

That is why /usr/local or /opt is a much better place to manually install software.

I dont undnerstand how you think they wont be overwritten, they are in the same prefix with the same files, just like a update overwrites files in the same place to the new version.

So unless Ubuntu decides to move prefixes, it's not a issue. If you leave GIMP package installed and compile to the same prefix and then remove the GIMP package, guess what happens?, yes it removes the one you compile just like it would do a package.

---

### Post by VeeDubb on 2008-10-05
> **Half-Left said:**
> I dont undnerstand how you think they wont be overwritten, they are in the same prefix with the same files, just like a update overwrites files in the same place to the new version.

So unless Ubuntu decides to move prefixes, it's not a issue. If you leave GIMP package installed and compile to the same prefix and then remove the GIMP package, guess what happens?, yes it removes the one you compile just like it would do a package.

On the other hand, you can do what I do, which is a good practice anyway.  Whenever I install anything from source, whether there are packaged versions available or not, I place the source code in /home/steve/src/ and I leave it there.  

Then, if ever I need to remove software I have installed manually, all it takes is to cd to /home/steve/src/program-name and "sudo make uninstall"

This works with just about anything.  While you're correct about packages overwriting, there are always the odd exceptions, and keeping the source, or at least the config files around will let you fully uninstall, and prevent any errors.

---

### Post by Half-Left on 2008-10-05
> **VeeDubb said:**
> On the other hand, you can do what I do, which is a good practice anyway.  Whenever I install anything from source, whether there are packaged versions available or not, I place the source code in /home/steve/src/ and I leave it there.  

Then, if ever I need to remove software I have installed manually, all it takes is to cd to /home/steve/src/program-name and "sudo make uninstall"

This works with just about anything.  While you're correct about packages overwriting, there are always the odd exceptions, and keeping the source, or at least the config files around will let you fully uninstall, and prevent any errors.

Well yes, I personally have a directory for my source tarballs, but in the end we are talking about just GIMP here, not loads of compiling. :)

---

### Post by VeeDubb on 2008-10-05
> **Half-Left said:**
> Well yes, I personally have a directory for my source tarballs, but in the end we are talking about just GIMP here, not loads of compiling. :)


Slippery slope........

Right now it's just gimp, but compiling from source to get the latest and greatest tends to become a habit, and good housekeeping habits now will mean an easier life later.

---

### Post by donom on 2008-10-05
Is updating to 2.6 from 2.4.5 using synaptic or apt-get going to be an option sometime in the future? I don't really want to try doing things I don't fully understand only to end up doing it wrong and having trouble later.

---

### Post by twodayslate on 2008-10-05
Very nice, but Gimp won't stay in [one window](http://img119.imageshack.us/img119/4083/screenshotow4.png) for me.


://
> **WindowsSucks said:**
> You're still going to have three windows because nothing really handles the windows perfectly as sub-windows, but if you're running Metacity (or Compiz from git as of this morning), the toolbox, etc. will float above the main window, and the main window will size the image to better fit this set up.
So I need compiz to make gimp one window? WTF!

---

### Post by racoq on 2008-10-05
The debs from getdeb have a bug, i have installed them in Xubuntu and all went ok, however i cannot open png, tiff  and other formats that i used to open. My guess is that the package gimp-data, was not correctly built with all options. 

Anyone with 2.6.0 can open Png's and Tiff's, or is just me?

---

### Post by exploder on 2008-10-05
The Gimp developer's did not actually make the new version to be in one window. (I wanted this too.) You can change the window management settings in the preferences to make it appear to be one window but it is actually windows placed on top of each other.

---

### Post by fabbaz on 2008-10-06
any idea on how to install on gutsy?
with the getdeb packages dpkg tells me that libcairo2 is too old...

---

### Post by Teamgeist on 2008-10-06
Gimp 2.6 just entered the Intrepid Ibex Repositories. Yay!

[https://lists.ubuntu.com/archives/intrepid-changes/2008-October/008013.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-October/008013.html)

---

### Post by Half-Left on 2008-10-06
The GEGL operation is awesome for enhancing images, check out the unsharp-mask and colour temperature option, gives great results.

---

### Post by Half-Left on 2008-10-10
2.6.1 already. :)


>  GNU Image Manipulation Program
                          2.6 Stable Branch
                   ------------------------------

This is the stable branch of GIMP. No new features are being added
here, just bug-fixes.


Overview of Changes from GIMP 2.6.0 to GIMP 2.6.1
=================================================

* Bugs fixed:

 555587 &#8211; PSD file crashes PSD plug-in
 555222 &#8211; PSD Load Plugin: unsupported compression mode
 555362 &#8211; gimp-remote is not working properly
 555280 &#8211; some gif files will not be open
 554890 &#8211; JPEG Save Options Dialog does not remember
 554966 &#8211; Gimp crashes creating a new image using a template
 554785 &#8211; Compile failure on uri-backend-libcurl
 554646 &#8211; Opening Help crashes GIMP with lqr-plugin installed
 553534 &#8211; centering issues after image scaling and setting zoom
 554898 &#8211; Compile failure on uri-backend-wget.c


By the way, any of you missing Save/Save As option in File menu?, I dont even have that option.

---

### Post by shelbyvision on 2008-11-21
> **binbash said:**
> main : 

[http://ftp1.srv.endpoint.nu/pub/software/getdeb/ubuntu/hardy/gi/gimp_2.6.0-1~getdeb1_i386.deb](http://ftp1.srv.endpoint.nu/pub/software/getdeb/ubuntu/hardy/gi/gimp_2.6.0-1~getdeb1_i386.deb)

I tried this and gdebi gave me this message:
**Error: Dependency is not satisfiable: gimp-data**
What does that mean?
I have Ubuntu 3.10 and currently have gimp2.4.0-rc3. I'd like to try upgrading GIMP to see if it improves my printing situation at all.

---

### Post by maruchan on 2008-11-21
Hi shelbyvision,

This means there's a package out there called "gimp-data" that needs to be installed on your system before you can install Gimp.

Also...you have Ubuntu 3.10???! I don't even think that's possible. Depending on which version you have, you can go to [www.getdeb.net](www.getdeb.net) and find packages (including gimp-data) for Gimp 2.6.

You might also look into using Scribus or OpenOffice for printing your images if Gimp doesn't fit the bill.

---

### Post by shelbyvision on 2008-11-21
OOPS, typo, that's Ubuntu 7.10 (Gutsy)!
I have a gimp-data already installed. When I tried installing the one at getdeb, I got another error message, saying something about being incompatible with gimp-python. When I went to synaptic and tried to update or remove gimp-python, it told me it was going to remove ubuntu-desktop! I'm pretty sure I don't want to do that! I got the same results using apt-get.
Steve

---

### Post by AJB2K3 on 2008-11-21
Im getting conflicts with gnome gfs. anyone else?

---

### Post by maruchan on 2008-11-21
OK, so you probably should go into Synaptic and remove all the Gimp stuff that's there. If it wants to remove Ubuntu Desktop, that's fine. UD is just a wrapper (a "metapackage") around a bunch of software, so it won't be removing the software itself, just the wrapper. No biggie.

After Gimp and gimp-python is completely removed, try again.

---

### Post by maruchan on 2008-11-21
AJB, did you install the corresponding .deb for your Ubuntu release version?

---

### Post by shelbyvision on 2008-11-21
> **maruchan said:**
> OK, so you probably should go into Synaptic and remove all the Gimp stuff that's there. If it wants to remove Ubuntu Desktop, that's fine. UD is just a wrapper (a "metapackage") around a bunch of software, so it won't be removing the software itself, just the wrapper. No biggie.

After Gimp and gimp-python is completely removed, try again.

I think I remember losing ubuntu-desktop once before, and nothing worked. I ended up having to re-install Ubuntu. I looked up ubuntu-desktop, and found this: [[COLOR="Blue"]http://packages.ubuntu.com/gutsy/ubuntu-desktop[/COLOR]]("http://packages.ubuntu.com/gutsy/ubuntu-desktop"). The list of things that depend on ubuntu-desktop is HUGE.
Steve

---

### Post by maruchan on 2008-11-21
Typically you would remove Ubuntu-desktop in cases like this. Then, when you do your next dist-upgrade, you'd reinstall it just prior, and remove any conflicting packages. Google "ok to remove ubuntu-desktop" if you don't believe me ;)

---

### Post by shelbyvision on 2008-11-22
> **maruchan said:**
> Typically you would remove Ubuntu-desktop in cases like this. Then, when you do your next dist-upgrade, you'd reinstall it just prior, and remove any conflicting packages. Google "ok to remove ubuntu-desktop" if you don't believe me ;)

OK, I think I understand now. I just have to *remember* to re install it (remembering is not my strong suit).
I removed ubuntu-desktop, and so was able to successfully install gimp-data from getdeb. Then I ran into problems. If I try to install gimp, it says "Error: Dependency is not satisfiable: libgimp2.0". When I try to install libgimp2.0 from getdeb, I get this: "Error: Dependency is not satisfiable: libglib2.0-0". A synaptic search shows that it is already installed, version 2.14.1-1ubuntu1. Could it be that I need a newer version?
Steve

---

### Post by maruchan on 2008-11-22
Yep, you'll need matching, newer versions of those libs, and there  is an order in which they need to be installed (which you are finding). Don't they have those libraries linked at getdeb?

---

### Post by shelbyvision on 2008-11-22
> **maruchan said:**
> Yep, you'll need matching, newer versions of those libs, and there  is an order in which they need to be installed (which you are finding). Don't they have those libraries linked at getdeb?

They don't have them at getdeb. I found them at the Debian website. I was able to install a newer version of libglib, but then when I tried to install libgimp2.0, it said there was something wrong with libgtk2.0-0. I tried installing that and it tells me there's a conflict with "metacity". I don't know if I need metacity or not. 
Steve

---

### Post by maruchan on 2008-11-22
Yeah, it sounds like these packages won't work for your version of Ubuntu...you need a 7.10 version of the various GIMP packages, or you'll need to compile them for yourself. Metacity is what is used to manage windows on your screen and is pretty necessary, IIRC.

The other option is to upgrade to Ubuntu 8.04, for which getdeb has all the packages.

Usually when you are told you need a new version of GTK or metacity, that means you'll have to dist-upgrade or compile the packages yourself.

---

### Post by shelbyvision on 2008-11-22
> **maruchan said:**
> 

The other option is to upgrade to Ubuntu 8.04, for which getdeb has all the packages.

The button is there, ready to press, on my update manager, to upgrade to 8.04. How painful is it to do that? Will it mess up any "unofficial" programs I have installed? Would I have to re-install ubuntu-desktop first? I really don't want to have to spend hours trying to get things back to normal.
Steve

---

### Post by maruchan on 2008-11-22
What do you mean by "unofficial" programs? You'd want to follow these instructions: [https://help.ubuntu.com/community/HardyUpgrades#Known%20Problems](https://help.ubuntu.com/community/HardyUpgrades#Known%20Problems)

And yes, definitely reinstall ubuntu-desktop before upgrading (although I've forgotten it before and didn't run into any problems).

---

### Post by AJB2K3 on 2008-11-22
> **maruchan said:**
> AJB, did you install the corresponding .deb for your Ubuntu release version?
I just ran the install via terminal and it removed the package but all is working now and I have to say.

Apart from the gimp head and gegl whats changed on the interface?

---

### Post by maruchan on 2008-11-22
If you don't notice what's changed, you could go read this:

[http://www.gimp.org/release-notes/gimp-2.6.html](http://www.gimp.org/release-notes/gimp-2.6.html)

---

### Post by shelbyvision on 2008-11-22
> **maruchan said:**
> What do you mean by "unofficial" programs? You'd want to follow these instructions: [https://help.ubuntu.com/community/HardyUpgrades#Known%20Problems](https://help.ubuntu.com/community/HardyUpgrades#Known%20Problems)

And yes, definitely reinstall ubuntu-desktop before upgrading (although I've forgotten it before and didn't run into any problems).

Thanks for the link.
By unofficial, I meant the ones that aren't part of the official Ubuntu repositories, that Ubuntu gives a warning about when you install it. I looked at my applications, and I'm not sure, but I think these may me some: Fontmatrix, KPov Modeler, Phatch, Simple backup restore.
Steve

---

### Post by maruchan on 2008-11-22
I think the bigger worry would be applications for which you've included custom repositories in your sources file. You'd want to disable the repos before upgrading. Other than that, I don't see why you'd be in any trouble.

---

### Post by Propwash on 2008-11-23
I have just tried the getdeb install, last night with the 2.6.2 release and today the 2.6.3 release.  I get the same error when I try to load libgimp2.0.  The package installer says "Error: Dependency is not satisfiable: libgtk2.0-0".  I've done a check and apt-get install -f and generally pounded away at apt thinking I had corrupt tree.  I've checked with dpkg and yep I do have libgtk2.0-0 installed and all is well.  I can reload the ubuntu Gimp 2.4.5 version and all works.  The newer gimp-data loads from the getdeb site but not the newer libgimp2.0.  Any ideas?

---

### Post by shelbyvision on 2008-11-23
I decided to wait, and not upgrade to hardy. It took me quite a while to get everything back the way it was, and when I tried to install Gimp again, It made me install newer versions of libpango1.0-0 and libpango1.0-common, which was kind of a hassle, but I'm very happy now because the GIMP it installed was a newer one than I had before, and it has a printing plugin that actually works the way it should, which was all I ever wanted to begin with! :)
Steve

---

