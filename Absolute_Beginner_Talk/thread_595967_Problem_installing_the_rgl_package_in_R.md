---
title: "Problem installing the rgl package in R"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by metaxab on 2007-10-29
Hello I have the following problem:

I am trying to install the 'rgl' package in R by:

sudo R
install.packages('rgl',dependencies=TRUE)


I get the following message

checking for X... no
configure: error: X11 not found but required, configure aborted.
ERROR: configuration failed for package 'rgl'
** Removing '/usr/local/lib/R/site-library/rgl'



How can I resolve this issue?

I run Ubuntu 7.10


Thank you in advance:)

---

### Post by johnnyg on 2007-10-29
Just a guess, but it looks like the sudo process is checking to see if X is running as a test for whether you have X or not.  Since the sudo is running as root and doesn't know about your X session this is failing.

Try using gksudo instead of sudo.

John

---

### Post by timbosity on 2008-02-13
HI,

been having same problem. Running gksudo didnt seem to work for me. Metaxab, did you figure out how to install rgl?

---

### Post by GorArn on 2008-02-25
You need to install some headers etc. See the following link:

[http://help.nceas.ucsb.edu/index.php/Installing_R_on_Ubuntu](http://help.nceas.ucsb.edu/index.php/Installing_R_on_Ubuntu)

/ GorArn

---

### Post by SOULRiDER on 2008-02-25
Im guessing youre trying to compile something?  If so install the **libx11-dev** package and try again.

---

