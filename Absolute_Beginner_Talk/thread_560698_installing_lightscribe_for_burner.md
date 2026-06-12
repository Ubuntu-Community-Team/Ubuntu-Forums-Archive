---
title: "installing lightscribe for burner"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by chaddiesel on 2007-09-26
I'm trying to install lightscribe for my DVD burner. It is an added program that I can use to make labels.

I downloaded their linux version and it is an rpm file. How do I install this?

There instructions don't really work.
[http://www.lightscribe.com/downloadsection/linux/index.aspx?id=1374](http://www.lightscribe.com/downloadsection/linux/index.aspx?id=1374)

---

### Post by ddrichardson on 2007-09-26
You'd need to use alien to convert it to a deb file

Frankly I spent ages trying to get some light scribe disc and it was the biggest anti climax ever. They look blurry and take ages to label.

---

### Post by chaddiesel on 2007-09-26
Thanks for the help. I'll give it a try.

I'm hoping this won't be anti-climatic but I finally got the burner to work so its worth a try. :)

---

### Post by spur on 2007-09-26
I gave it a miss as it is only grey scale. Printing paper ones can be a hassle to get right but they are much more legible.

---

### Post by ddrichardson on 2007-09-26
Sorry I don't mean to sound negative, but its just so irritating - a little dust in thier or a fingerprint and the image is smudged. I thought it would solve the problem of never having an OHP marker to hand, but even just a little text is around 12 minutes to print.

---

### Post by ddrichardson on 2007-09-26
> **spur said:**
> I gave it a miss as it is only grey scale. Printing paper ones can be a hassle to get right but they are much more legible.
Yes, however the glue can degrade the CD and the the labels can jam the system, there's even a disclaimer in some software (Roxio for example) saying not to use labels.

---

### Post by por100pre1 on 2007-09-26
Try [this]("http://ubuntuforums.org/showthread.php?t=289922").

---

### Post by chaddiesel on 2007-09-26
I should have asked this earlier. Where do I get alien?

---

### Post by por100pre1 on 2007-09-26
```
sudo aptitude install alien
```

---

### Post by chaddiesel on 2007-09-26
and next.... how do I apply that application to convert rpm to deb?

---

### Post by chaddiesel on 2007-09-26
nevermind.....it works flawlessly. Just a little too easy.

---

### Post by Joe_Linux on 2007-09-26
joe@joe-desktop:~$ sudo alien lightscribe-1.8.15.1-linux-2.6-intel.rpm
Password:
Warning: Skipping conversion of scripts in package lightscribe: postinst prerm
Warning: Use the --scripts parameter to include the scripts.
mkdir: cannot create directory `lightscribe-1.8.15.1': File exists
mkdir: cannot create directory `lightscribe-1.8.15.1/debian': File exists
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
                xargs -0 -r -i cp -a {} debian/lightscribe
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: warning: could not find any packages for libstdc++.so.5
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libm.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libm (soname 6, path libm.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libc.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libc (soname 6, path libc.so.6, dependency field Depends)
dh_gencontrol
dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
find: lightscribe-1.8.15.1: No such file or directory
joe@joe-desktop:~$                                
I tried installing the file and got the above result any help would be appreciated.

---

### Post by flyingbrass on 2007-09-27
They have a pre-release deb available.  It might work better than aliening an RPM.  

[http://www.lightscribe.com/downloadsection/pse/](http://www.lightscribe.com/downloadsection/pse/)

---

### Post by lisati on 2007-09-27
It's good to see that you're making progress getting the lightscribe to work. Forget the "sticky labels" - I've found that they're more trouble than they're worth!

---

### Post by xjgnsdof on 2007-11-10
There's a deb right beneath the rpm in the list. Why not just download that?

---

