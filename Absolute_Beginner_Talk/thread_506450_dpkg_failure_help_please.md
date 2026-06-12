---
title: "dpkg failure help please"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by LittleIrishDevil on 2007-07-21
I ran the sudo reconfig thing and then tried to download and install updates and got...

An unresolvable problem occurred while initialising the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package virtualbox needs to be reinstalled, but I can't find an archive for it.'

.... and so now ? Help

---

### Post by Majorix on 2007-07-21
What about this: Download the virtualbox.deb package from [www.getdeb.net](www.getdeb.net) and then try uninstalling using that.

---

### Post by pyros on 2007-07-21
> **LittleIrishDevil said:**
> I ran the sudo reconfig thing and then tried to download and install updates and got...

An unresolvable problem occurred while initialising the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package virtualbox needs to be reinstalled, but I can't find an archive for it.'

.... and so now ? Help

well, it's asking you to go here:
[https://bugs.launchpad.net/update-manager/](https://bugs.launchpad.net/update-manager/)
and file a bug with that error.

To fix it, try running 
```

dpkg --remove --force-remove-reinstreq virtualbox

```

---

### Post by LittleIrishDevil on 2007-07-21
mmh thanks but this didn't work because the system now oesn't seem to recognise me as a 'superuser' !

---

### Post by forestpixie on 2007-07-21
sudo dpkg --remove --force-remove-reinstreq virtualbox

and enter your password

---

### Post by LittleIrishDevil on 2007-07-21
Ok tried
sudo dpkg --remove --force-remove-reinstreq virtualbox
and got

dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 
dpkg: serious warning: files list file for package `virtualbox' missing, assuming package has no files currently installed.
105824 files and directories currently installed.)
Removing virtualbox ...

newbies like me break into a cold sweat with this sort of thing.... now what ?

---

### Post by forestpixie on 2007-07-21
you should now be back before you tried to install virtualbox - and I didn't like that message when i saw it couple of months ago :)

---

### Post by LittleIrishDevil on 2007-07-21
Thank you, that seems to have done it !!

---

### Post by pyros on 2007-07-21
> **LittleIrishDevil said:**
> Thank you, that seems to have done it !!

Sorry about that, can't believe I forgot sudo.

---

### Post by theduke0 on 2007-07-26
I have a similar problem for a broken package that I would like to remove.  

when I run sudo dpkg --remove --force-remove-reinstreq mypackage I get:

dpkg: you must specify packages by their own names, not by quoting the names of the files they come in

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].



  any ideas?

---

### Post by pyros on 2007-07-26
> **theduke0 said:**
> I have a similar problem for a broken package that I would like to remove.  

when I run sudo dpkg --remove --force-remove-reinstreq mypackage I get:

dpkg: you must specify packages by their own names, not by quoting the names of the files they come in

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].



  any ideas?

what package are you trying to remove? Can you find that package in "/var/cache/apt"?

---

### Post by theduke0 on 2007-07-26
the package is an brother rinter driver named hl517700dnlpr-1.1.2-1.i386.deb

I do not see this package in the directory you pointed me to above.  i have a folder in there names 'archives' and didn't see it.  there were also 2 bin files in that folder...nothing else.  

is there a revolution to this?

---

### Post by theduke0 on 2007-07-26
I have a solution!

So I needed to install 2 files so that the proper files were needed when installed the package I was talking about above.  I ended up digging through some other brother walkthoughs and realized that I needed to create a symbolic link to another file!  whew.  

I would like to know how to remove a package that does this in the future in case i have another faulty install, but for now -- i will just stick to fixing the install and then moving forward.

---

### Post by pseudo_nz on 2007-08-09
I'm having problems with a brother printer driver as well, and I'm not sure what to do next.  I've run the dpkg removal command posted earlier, but this is the output I get:

> dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 105023 files and directories currently installed.)
Removing dcp130ccupswrapper ...
/var/lib/dpkg/info/dcp130ccupswrapper.prerm: line 3: /usr/local/Brother/Printer/dcp130c/cupswrapper/cupswrapperdcp130c: No such file or directory
dpkg: error processing dcp130ccupswrapper (--remove):
 subprocess pre-removal script returned error exit status 127
/var/lib/dpkg/info/dcp130ccupswrapper.postinst: line 3: /usr/local/Brother/Printer/dcp130c/cupswrapper/cupswrapperdcp130c: No such file or directory
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 dcp130ccupswrapper


Am very much an end-user, so I'm totally lost.  Any help would be appreciated, thanks.

---

### Post by bwtranch on 2007-08-13
You might want to look at this thread: [http://ubuntuforums.org/showthread.php?t=515125&highlight=brother+dcp+1000](http://ubuntuforums.org/showthread.php?t=515125&highlight=brother+dcp+1000)

---

### Post by pseudo_nz on 2007-08-16
Thanks, it's good to know someone figured it out.  I admit, I gave up and reinstalled, and was lucky enough to find a walk-through [here]("http://ubuntuforums.org/showthread.php?t=71104&highlight=install+brother+scanner") that sidestepped whatever it is that broke dpkg.

---

