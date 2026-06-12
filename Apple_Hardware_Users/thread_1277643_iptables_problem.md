---
title: "iptables problem"
date: 2009-09-28
forum: Apple Hardware Users
---

### Post by josephmcnelis on 2009-09-28
Hey all,

Im using my MAC mini to attempt to set up a Hardy Heron server via SSH.

Its the first time ive ever done this sort of thing so im pretty much clueless but anyway i was following a nice set of tutorials at slicehosts (detailed below)

[http://articles.slicehost.com/2008/4/25/ubuntu-hardy-setup-page-1](http://articles.slicehost.com/2008/4/25/ubuntu-hardy-setup-page-1)

but ive got to the iptables section but any command i attempt to run results in 

-bash: iptables: command not found

any ideas would be greatly appreciated??

-Cheers

---

### Post by DaithiF on 2009-09-28
iptables is located at /sbin/iptables
is /sbin in your path?if not then you need to provide the explicit path to it.

---

### Post by josephmcnelis on 2009-09-28
how could i find out my path?

---

### Post by DaithiF on 2009-09-28
echo $PATH

---

### Post by josephmcnelis on 2009-09-28
it returns the following

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

how would i go about adding iptables to it?

-Cheers

---

### Post by josephmcnelis on 2009-09-28
I thought iptables came as default but when i try whereis iptables it returns a blank.

Sorry if thats a terribly simple question :(

---

### Post by DaithiF on 2009-09-28
i guess i wasn't very clear.  iptables should be located in the directory /sbin.  Where the tutorial says to run iptables xyz..., use the full path instead: /sbin/iptables xyz...

The path you posted indicates that /sbin is already in your path, which means the command not found error is a little surprising.  Try /sbin/iptables as described above first, if you still get an error then post back.

---

