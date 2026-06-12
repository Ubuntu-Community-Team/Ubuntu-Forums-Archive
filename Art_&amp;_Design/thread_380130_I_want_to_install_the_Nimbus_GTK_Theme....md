---
title: "I want to install the Nimbus GTK Theme..."
date: 2007-03-09
forum: Art &amp; Design
---

### Post by laxmanb on 2007-03-09
Nimbus is the new default GTK theme used in Solaris... I like it (colorful+shiny... looks cool to me!!)

[IMG]http://developers.sun.com/solaris/articles/java_gnome/images/java_gnome-figure5.gif[/IMG]

any idea where I can get it from? I googled it but didn't didn't anything...

---

### Post by Graduate on 2007-03-09
I'm running xubuntu with openbox, so I can't tell you if this is the file but it's something. [http://www.youmustbejoking.demon.co.uk/progs.sid.html#gtk2-engines-nimbus](http://www.youmustbejoking.demon.co.uk/progs.sid.html#gtk2-engines-nimbus) Also, they have a link to the Nimbus icons in the right corner.

---

### Post by ComplexNumber on 2007-03-09
> **Graduate said:**
> I'm running xubuntu with openbox, so I can't tell you if this is the file but it's something. [http://www.youmustbejoking.demon.co.uk/progs.sid.html#gtk2-engines-nimbus](http://www.youmustbejoking.demon.co.uk/progs.sid.html#gtk2-engines-nimbus) Also, they have a link to the Nimbus icons in the right corner.
the gtk and metacity theme is contained within the package labeled as 'nimbus icon theme'. however, the gtk themes needs the engine to be installed, and the engine requires certain  versions of  libfontconfig and pango to be installed. i got this:
```
 dpkg: dependency problems prevent configuration of gtk2-engines-nimbus:
 gtk2-engines-nimbus depends on libfontconfig1 (>= 2.4.0); however:
  Version of libfontconfig1 on system is 2.3.2-7ubuntu2.
 gtk2-engines-nimbus depends on libpango1.0-0 (>= 1.14.0); however:
  Version of libpango1.0-0 on system is 1.14.5-0ubuntu1.
dpkg: error processing gtk2-engines-nimbus (--install):
 dependency problems - leaving unconfigured
Setting up nimbus-icon-theme (0.0.4-1) ...
Errors were encountered while processing:
 gtk2-engines-nimbus
```

---

### Post by laxmanb on 2007-03-09
Thanks!! Got the dependencies from the ubuntu package site...theme installed!

---

### Post by fakie_flip on 2007-06-25
You can also get packages from here, but they don't have 64 bit versions :(

[http://gnome-look.org/content/show.php/Nimbus+%28Ubuntu+and+Debian%29?content=54755](http://gnome-look.org/content/show.php/Nimbus+%28Ubuntu+and+Debian%29?content=54755)

---

### Post by fakie_flip on 2007-06-26
> **laxmanb said:**
> Thanks!! Got the dependencies from the ubuntu package site...theme installed!

Are you able to compile it with checkinstall? I havent been able to.

---

### Post by fakie_flip on 2007-06-26
I am getting lots of errors about intltool even though I have it installed.

```
config.status: executing intltool commands
./config.status: line 1191: ./intltool-extract.in: No such file or directory
mv: cannot stat `intltool-extract.out': No such file or directory
chmod: cannot access `intltool-extract': No such file or directory
chmod: cannot access `intltool-extract': No such file or directory
./config.status: line 1191: ./intltool-merge.in: No such file or directory
mv: cannot stat `intltool-merge.out': No such file or directory
chmod: cannot access `intltool-merge': No such file or directory
chmod: cannot access `intltool-merge': No such file or directory
./config.status: line 1191: ./intltool-update.in: No such file or directory
mv: cannot stat `intltool-update.out': No such file or directory
chmod: cannot access `intltool-update': No such file or directory
chmod: cannot access `intltool-update': No such file or directory
config.status: executing default-1 commands
config.status: executing po/stamp-it commands
```

```
[email]chris@ubuntu:~/Desktop/nimbus-0.0.6.orig[/email]$ dpkg -l | grep intltool
ii  intltool                               0.35.5-0ubuntu2                        Utility scripts for internationalizing XML
ii  intltool-debian                        0.35.0+20060710.1                      Help i18n of RFC822 compliant config files
[email]chris@ubuntu:~/Desktop/nimbus-0.0.6.orig[/email]$ which intltool-update 
/usr/bin/intltool-update
[email]chris@ubuntu:~/Desktop/nimbus-0.0.6.orig[/email]$ which intltool-merge  
/usr/bin/intltool-merge
[email]chris@ubuntu:~/Desktop/nimbus-0.0.6.orig[/email]$
```

---

### Post by madmax_haskovo on 2007-11-23
> **fakie_flip said:**
> I am getting lots of errors about intltool even though I have it installed.

```
config.status: executing intltool commands
./config.status: line 1191: ./intltool-extract.in: No such file or directory
mv: cannot stat `intltool-extract.out': No such file or directory
chmod: cannot access `intltool-extract': No such file or directory
chmod: cannot access `intltool-extract': No such file or directory
./config.status: line 1191: ./intltool-merge.in: No such file or directory
mv: cannot stat `intltool-merge.out': No such file or directory
chmod: cannot access `intltool-merge': No such file or directory
chmod: cannot access `intltool-merge': No such file or directory
./config.status: line 1191: ./intltool-update.in: No such file or directory
mv: cannot stat `intltool-update.out': No such file or directory
chmod: cannot access `intltool-update': No such file or directory
chmod: cannot access `intltool-update': No such file or directory
config.status: executing default-1 commands
config.status: executing po/stamp-it commands
```

```
[email]chris@ubuntu:~/Desktop/nimbus-0.0.6.orig[/email]$ dpkg -l | grep intltool
ii  intltool                               0.35.5-0ubuntu2                        Utility scripts for internationalizing XML
ii  intltool-debian                        0.35.0+20060710.1                      Help i18n of RFC822 compliant config files
[email]chris@ubuntu:~/Desktop/nimbus-0.0.6.orig[/email]$ which intltool-update 
/usr/bin/intltool-update
[email]chris@ubuntu:~/Desktop/nimbus-0.0.6.orig[/email]$ which intltool-merge  
/usr/bin/intltool-merge
[email]chris@ubuntu:~/Desktop/nimbus-0.0.6.orig[/email]$
```

Use [this]("http://www.vinodlive.com/2007/08/20/make-your-ubuntu-desktop-more-beautiful") tuttorial, get the original source from [here]("http://dlc.sun.com/osol/jds/downloads/extras/") and build the packages all by yourself. It's not so difficult. But this tuttorial work with all versions prior to 0.0.10. I'm working now on compiling 0.0.10, unsuccessfull so far :(

---

### Post by Anovadea on 2008-02-11
> **madmax_haskovo said:**
> Use [this]("http://www.vinodlive.com/2007/08/20/make-your-ubuntu-desktop-more-beautiful") tuttorial, get the original source from [here]("http://dlc.sun.com/osol/jds/downloads/extras/") and build the packages all by yourself. It's not so difficult. But this tuttorial work with all versions prior to 0.0.10. I'm working now on compiling 0.0.10, unsuccessfull so far :(

I got it to work with 0.0.11 with just a tiny bit of tweaking of intltool-merge.in

**BIG AND IMPORTANT NOTE**: I got this result by just hacking around. It turns out that this was the only change I needed to make, but I am not guaranteeing that this will work for everyone.

Now, if you've read the above and still want to try it...

0/ Start a terminal and change to the directory where you have the source tree.

1/ Open up *intltool-merge.in* with your preferred text editor.

Example: *nano intltool-merge.in* or open it with gedit

2/ Go to line 94. It should look like:
*my $iconv = $ENV{"ICONV"} || $ENV{"INTLTOOL_ICONV"} || "@INTLTOOL_ICONV@";*

3/ Copy and paste that line to the line just below it.

4/ Put a '#' in front of the first copy of that line.

By now it should look like:
*#my $iconv = $ENV{"ICONV"} || $ENV{"INTLTOOL_ICONV"} || "@INTLTOOL_ICONV@";*
*my $iconv = $ENV{"ICONV"} || $ENV{"INTLTOOL_ICONV"} || "@INTLTOOL_ICONV@";*

5/ Remove * || "@INTLTOOL_ICONV@"* from the second line.

Lines 94 and 95 should now look like:
*#my $iconv = $ENV{"ICONV"} || $ENV{"INTLTOOL_ICONV"} || "@INTLTOOL_ICONV@";*
*my $iconv = $ENV{"ICONV"} || $ENV{"INTLTOOL_ICONV"};*

6/ Follow the rest of the guide.

As I said, this worked for me, but I can't guarantee that it works (mainly because I looked at the warnings from the compilation and editted the files to fix them without fully understanding what I was doing) so, like all other unproven workarounds, **use it with caution**.

Let me know if that helps.
Aoife

---

### Post by acankat on 2008-02-11
Whatever I do the empty-trash icon is alwasy the default tango icon. (the full one is nimbus) is there a trick to overcome this?

---

### Post by Anovadea on 2008-02-11
Strangely, it works for me.

Check to see if you're using a custom theme. 

Even if it's not the case have a quick check to see what icon theme you're using. 

0/ Go to System->Preferences->Appearance

1/ Click "Customize..." button

2/ Click on the "Icons" tab. Click on another theme name and back to nimbus.

I hope this helps.

Aoife

---

### Post by acankat on 2008-02-12
can anyone upload the latest deb files somewhere?

---

### Post by pmagill on 2008-03-04
[http://www.gnome-look.org/content/show.php/ubuntu+AMD64+debs+for+Nimbus+themes?content=75816](http://www.gnome-look.org/content/show.php/ubuntu+AMD64+debs+for+Nimbus+themes?content=75816)

Above link Nimbus 64 bit debs :)

---

### Post by g474h4d on 2008-04-02
Let me summarize the thread and tell which procedure works perfectly for me so far for nimbus version 0.0.6 to 0.0.12:

Download sources from [http://dlc.sun.com/osol/jds/downloads/extras/]("http://dlc.sun.com/osol/jds/downloads/extras/")

the change into the extraced directory and type this:
```
sudo aptitude install intltool libgtk2.0-dev icon-naming-utils checkinstall
ln -s /usr/share/intltool/intltool-extract.in intltool-extract.in
ln -s /usr/share/intltool/intltool-merge.in intltool-merge.in
ln -s /usr/share/intltool/intltool-update.in intltool-update.in
./configure --prefix=/usr
make
sudo checkinstall -D make install
```

---

### Post by g474h4d on 2008-05-09
The above procedure works only up to Ubuntu 7.10 Gutsy Gibbon, but fails in 8.04 Hardy Heron. Below are the last lines of output:
```
make[3]: Entering directory `/home/andy/Desktop/nimbus-0.0.12/gtk-engine'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/lib/gtk-2.0/2.10.0/engines" || /bin/mkdir -p "/usr/lib/gtk-2.0/2.10.0/engines"
 /bin/bash ../libtool --mode=install /usr/bin/install -c  'libnimbus.la' '/usr/lib/gtk-2.0/2.10.0/engines/libnimbus.la'
/usr/bin/install -c .libs/libnimbus.so /usr/lib/gtk-2.0/2.10.0/engines/libnimbus.so
/usr/bin/install -c .libs/libnimbus.lai /usr/lib/gtk-2.0/2.10.0/engines/libnimbus.la
/usr/bin/install -c .libs/libnimbus.a /usr/lib/gtk-2.0/2.10.0/engines/libnimbus.a
chmod 644 /usr/lib/gtk-2.0/2.10.0/engines/libnimbus.a
chmod: changing permissions of `/usr/lib/gtk-2.0/2.10.0/engines/libnimbus.a': No such file or directory
make[3]: *** [install-engineLTLIBRARIES] Error 1
make[3]: Leaving directory `/home/andy/Desktop/nimbus-0.0.12/gtk-engine'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/andy/Desktop/nimbus-0.0.12/gtk-engine'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/andy/Desktop/nimbus-0.0.12/gtk-engine'
make: *** [install-recursive] Error 1
```
I don't know why it doesn't work in Hardy :confused:

---

### Post by ShodanjoDM on 2008-05-09
> **g474h4d said:**
> 
I don't know why it doesn't work in Hardy :confused:

Try this after extracting the tar archive:

```
./autogen.sh --prefix=/usr
./configure --prefix=/usr
```

^^I think the ./configure part is unecessary, but still...

```
make
sudo checkinstall --fstrans=no --install=no
```

This will create deb package in the directory (supposedly) without installing it. I wrote "supposedly" because when I ran:

```
sudo make uninstall
```

There were a bunch of cleaning happened. Good thing, I guess, since I want to do it the dpkg way:

```
sudo dpkg -i *.deb
```

---

### Post by diamondsw on 2008-05-12
I've [posted a script]("http://ubuntuforums.org/showthread.php?p=4939907") that will install all dependencies, make some patches here and there, and generally create the debs for you automagically. :)

Enjoy!

---

