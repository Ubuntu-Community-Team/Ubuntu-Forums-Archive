---
title: "Installing Java 6 beta 2"
date: 2006-06-19
forum: Absolute Beginner Talk
---

### Post by neogia on 2006-06-19
Let me preface this by saying this is my first Linux O/S, just started yesterday, and am loving it... but nevertheless a ginormous noob at it. That said:

I'm trying to install the latest java 6 beta. I downloaded the self-extracting bin file, ran it and got "bash: rpm: command not found". After some digging, I found out that the rpm command was not installed. Went into synaptic, installed rpm, continued. Now I get the following:
```

ben@neogia:~/Desktop$ sudo bash jdk-6-beta2-linux-i586-rpm.bin
...
a bunch of License Agreement
...
Unpacking...
Checksumming...
Extracting...
UnZipSFX 5.50 of 17 February 2002, by Info-ZIP (Zip-Bugs@lists.wku.edu).
replace jdk-6-beta2-linux-i586.rpm? [y]es, [n]o, [A]ll, [N]one, [r]ename: y
  inflating: jdk-6-beta2-linux-i586.rpm
error: Failed dependencies:
        /bin/basename is needed by jdk-1.6.0-beta2.i586
        /bin/cat is needed by jdk-1.6.0-beta2.i586
        /bin/cp is needed by jdk-1.6.0-beta2.i586
        /bin/gawk is needed by jdk-1.6.0-beta2.i586
        /bin/grep is needed by jdk-1.6.0-beta2.i586
        /bin/ln is needed by jdk-1.6.0-beta2.i586
        /bin/ls is needed by jdk-1.6.0-beta2.i586
        /bin/mkdir is needed by jdk-1.6.0-beta2.i586
        /bin/mv is needed by jdk-1.6.0-beta2.i586
        /bin/pwd is needed by jdk-1.6.0-beta2.i586
        /bin/rm is needed by jdk-1.6.0-beta2.i586
        /bin/sed is needed by jdk-1.6.0-beta2.i586
        /bin/sort is needed by jdk-1.6.0-beta2.i586
        /bin/touch is needed by jdk-1.6.0-beta2.i586
        /usr/bin/cut is needed by jdk-1.6.0-beta2.i586
        /usr/bin/dirname is needed by jdk-1.6.0-beta2.i586
        /usr/bin/expr is needed by jdk-1.6.0-beta2.i586
        /usr/bin/find is needed by jdk-1.6.0-beta2.i586
        /usr/bin/tail is needed by jdk-1.6.0-beta2.i586
        /usr/bin/tr is needed by jdk-1.6.0-beta2.i586
        /usr/bin/wc is needed by jdk-1.6.0-beta2.i586
        /bin/sh is needed by jdk-1.6.0-beta2.i586

Done.

```
Then I tried "man rpm" and was swallowed whole.

I'm figuring maybe I'm just missing an "include dependencies" flag or something? At least that's all I can muster from the currently-foreign jumble laid before me. Any help?

---

### Post by Winblowz on 2006-06-19
Are you sure you're supposed to be using the rpm version? You probably should use the .bin version since rpm is for rpm distro's. I could be wrong though. Also, I think in order to install Sun Java directly from Sun you need to install fakeroot. I am not exactly sure how to do this, but there is an Ubuntu guide that shows how to install sun Java 5 directly from Sun (which says you need the fakeroot package). I'd think it would be similar with Java 6.

---

### Post by HereInOz on 2006-06-19
Essentially, you need to download the *.bin file from Sun.  Follow their instructions.  You need to move the *.bin file in to the directory in which you want to install java, then run the .bin file.

Once this runs, you will have java installed in that directory.  You then need to go to the firefox plug-ins directory and create a symbolic link to the .so file in the correct installed java directory.

There are instructions on the Firefox help page to assist with this:
[http://www.mozilla.org/support/firefox/faq#q2.2](http://www.mozilla.org/support/firefox/faq#q2.2)
They are a bit out of date, unfortunately, but the idea is there.  You will need to experiment with which .so file in which directory you chose.  There are a couple of directories each with a .so file in there, but if you pick the wrong one, Firefox will crash, or not load at all, so it is a matter of trial and error.

When it works, it is a wonderful thing!!

Good luck

---

### Post by neogia on 2006-06-19
[QUOTE=HereInOz]Essentially, you need to download the *.bin file from Sun.  Follow their instructions...[/QUOTE]
Yes, this is what I've done, to the letter. I downloaded the .bin file, ran it from an arbitrary location, in my case the Desktop, then I ran into the problems stated in my first post, which seem unrelated to where I ran the bin from. That seems to be the only difference between what you said and what I did.

---

### Post by ape on 2006-06-19
From your output above, you downloaded the .rpm.bin file, not the .bin file.  The file you should have downloaded is:

jdk-6-beta2-linux-i586.bin

with a filesize of 55721698

I've just downloaded this file and ran `sh jdk-6-beta2-linux-i586.bin` and ended up with a good installation.

---

### Post by neogia on 2006-06-19
[QUOTE=ape]From your output above, you downloaded the .rpm.bin file, not the .bin file.  The file you should have downloaded is:

jdk-6-beta2-linux-i586.bin

with a filesize of 55721698

I've just downloaded this file and ran `sh jdk-6-beta2-linux-i586.bin` and ended up with a good installation.[/QUOTE]
Ah, thanks ape, I'll have to try that when I get home.

---

