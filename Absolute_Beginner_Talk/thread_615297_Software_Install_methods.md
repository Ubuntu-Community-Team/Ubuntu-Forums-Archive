---
title: "Software Install methods"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by jbguev on 2007-11-16
I know that there are at least five different methods to install software in Ubuntu: aptitude, apt-get, add/remove programs, synaptic, and compile from source/make.  What I really don't understand, however, are the advantages and disadvantages of each.  It seems like most posters here give examples using apt-get or aptitude.  Could someone please explain the benefits of each method or point me to a link?

When compiling from source, do the installed software packages then appear as installed under the synaptic package manager?  Also, for example, when installing PHP, are all the libraries/modules included in the source package?

Thanks for the knowledge.

Jerry

---

### Post by taurus on 2007-11-16
Maybe this link would help.

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by ramjet_1953 on 2007-11-16
OK, all methods work fine.

That is one of the really nice things about Linux, you can choose which method suits you best.

Most people familiar with the command line use the [COLOR="Blue"]apt-get install[/COLOR] command, just because it is faster and easier than using Synaptic or Add-Remove.

When I "roll my own" packages instead of using the following commands:

[COLOR="Blue"]./compile
make
sudo make install[/COLOR]

I use another package called [COLOR="Blue"]checkinstall[/COLOR]

[COLOR="Red"]sudo apt-get install checkinstall[/COLOR]

The advantage of using checkinstall is that it produces a standard debian package that you can then install and the installed package then appears in Synaptic, which makes it easier to un-install.

the command line for checkinstall is easy:

I then use these commands:

[COLOR="Blue"]./configure
make
sudo checkinstall -D --install=no[/COLOR]

These commands just produce the deb package, without installing it.

Hope this helps.

Regards,
Roger :cool:

---

### Post by jbguev on 2007-11-16
Thanks taurus.  I have read that particular link; I was just wondering if there was a "perfect" method for installation that never causes any problems and has all software work without issue.

ramjet_1953: that is great info, thanks a bunch!

Jerry

---

### Post by derby007 on 2007-11-17
There is a 6th method, go to : [http://packages.ubuntu.com/]("http://packages.ubuntu.com/") and pick/search for a package you want (and dependencies), download the package (.deb file) & 'right-click' on this file & install..... I have to do this method as I dont have broadband in my area yet!!!, ie. i download the packages from work, ahem, and then bring them home on my USB stick & install, its a nightmare though, ie. dependencies!!!!!!!

---

