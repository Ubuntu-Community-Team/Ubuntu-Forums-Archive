---
title: "part two of install *bin* using terminal"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by dubs on 2007-09-18
Thank you to Justleen and Lexyboy



Ok I'm able to get the file from it location. But come a choice that I'm not able to get. This are
the question after reading the License agreement.

Do you agree to the above license terms? [yes or no]
yes
Unpacking...
Checksumming...
Extracting...
UnZipSFX 5.50 of 17 February 2002, by Info-ZIP (Zip-Bugs@lists.wku.edu).
replace jre-6u2-linux-i586.rpm? [y]es, [n]o, [A]ll, [N]one, [r]ename: N
/home/dis622/Java/jre-6u2-linux-i586-rpm.bin: 400: rpm: not found


I answer yes- no- All- None- and it come up the same 
/home/dis622/Java/jre-6u2-linux-i586-rpm.bin: 400: rpm: not found


What to do


Steven

---

### Post by RomeReactor on 2007-09-18
Hi. RPM packages are for Red Hat and other Linux distros; Ubuntu uses DEB packages. Are you trying to install Java? all you need is install these packages: **sun-java6-bin, sun-java6-fonts, sun-java6-jre**, and **sun-java6-plugin**; search for **sun-java6** in Synaptic (System->Administration->Synaptic Package Manager), or to install from the terminal (Applications->Accessories->Terminal):
```
sudo apt-get install sun-java6-bin sun-java6-fonts sun-java6-jre sun-java6-plugin
```

---

### Post by Lord Illidan on 2007-09-18
What are you trying to install?

---

### Post by dubs on 2007-09-18
Yes your wright it work good.



Thank you

---

### Post by dubs on 2007-09-18
ok I was able to install the Java but I'm still not able to get any JVM when I go to this web site 


[http://java.com/en/download/help/testvm.xml](http://java.com/en/download/help/testvm.xml)


What I'm missing?


Thank 


Steven

---

### Post by FuturePilot on 2007-09-18
Make sure you restart Firefox

---

### Post by dubs on 2007-09-18
I did but still wont work

---

### Post by RomeReactor on 2007-09-18
Type **ABOUT:PLUGINS** in Firefox and see if it lists Java. Also, go into "Edit->Preferences->Content" and make sure the "Enable Java" box is checked.

Try running this:
```
sudo update-alternatives --config java
```
and select **/usr/lib/jvm/java-6-sun/jre/bin/java** (should be the second option), and restart Firefox.

Or it could be that this problem is related to [this bug]("https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/112994").

---

### Post by dubs on 2007-09-18
Thank you all


The Java runtime was not install correctly the first time around.  Now it work very good.


It's enough for today, will come back to try to install a theme. will let you all know my progress.


Thank you to all again.

Steven

---

