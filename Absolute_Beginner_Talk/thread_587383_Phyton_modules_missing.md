---
title: "Phyton modules missing"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by lordpuppet on 2007-10-22
Hi, im using ubuntu gutsy, and i have installed Amarok. When i want to run a script that i downloaded for this software it gives me an error saiying:
"Some needed Python modules could not be found.
Python output: No module named kdecore"

And:

"Sorry, you need QtRuby, RubyGTK or TkRuby to execute this program"

I cant find where to download and install this modules.

---

### Post by molly_001 on 2007-10-23
Actually, it is not a Python module you are missing.  The script you are trying to run simply uses Python as it operation/programming base.

Before I forget:  I**f you can provide a link to whatever script you downloaded for use with Amorok, this would be very helpful.**

Do the following, for now:

Open Terminal, and type:```


sudo apt-get build-dep ruby-pkg-tools


```

Select [y]yes and install that.  Then, go to this web page and **very near the bottom of this page** download the tarball for qt4-qtruby_1.4.6.orig.tar.gz .  It is 1411.1 kB in size.

[http://packages.debian.org/stable/source/qt4-qtruby](http://packages.debian.org/stable/source/qt4-qtruby)

Be sure to save it to your desktop and let me know when you have done this.

Thanks.

---

### Post by cl_audio on 2007-11-13
I had a similar issue, by going into package manager and getting Ruby Gnome and RubyPkg something.

 it fixed it!


Give it a try!

---

