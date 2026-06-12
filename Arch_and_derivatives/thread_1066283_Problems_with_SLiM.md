---
title: "Problems with SLiM"
date: 2009-02-10
forum: Arch and derivatives
---

### Post by ghindo on 2009-02-10
Hey all,
I recently decided to switch from GDM to SLiM, but haven't had much success.  I've removed GDM entirely, but haven't gotten SLiM to work.  I've tried both daemon and inittab method, but neither have worked.  When I try to launch SLiM manually, I get the error message:```
slim: Could not create lock file: /var/lock/slim.lock
```Anybody have any suggestions?  I've tried Googling the error message to no avail, and I've already checked the Arch Wiki and SLiM site.  Thanks! :popcorn:

---

### Post by cardinals_fan on 2009-02-10
Adding slim to the daemons in rc.conf should have worked...

A silly question, but you ARE trying to start it as root, right?

---

### Post by ghindo on 2009-02-10
Yeah, I've tried to manually start it as root and it didn't work.

---

### Post by kerry_s on 2009-02-10
it would help to see how you put it in inittab, do your settings than post it here and will look at it to make sure it's right.

in the rc.conf it's pretty hard to mess that up:

```
DAEMONS=(!syslog-ng @network @netfs !crond @alsa **slim**)
```

---

### Post by mpsii on 2009-02-10
Does the /var/lock directory exist? What are its permissions? (ls -al /var/|grep lock)

As root, try:```
# mkdir -p /var/lock
# touch /var/lock/slim.lock
```

---

### Post by ghindo on 2009-02-10
> **mpsii said:**
> Does the /var/lock directory exist? What are its permissions? (ls -al /var/|grep lock)

As root, try:```
# mkdir -p /var/lock
# touch /var/lock/slim.lock
```This solved it, thank you so much! :KS  I just wonder why I couldn't find that in any of the documentation?

---

### Post by Grant A. on 2009-02-10
```
DAEMONS=(!syslog-ng @network @netfs !crond @alsa **xinit** **slim**)
```

X has to be started before slim can run. Place "xinit" before slim in the rc.conf file in the section "DAEMONS"

---

### Post by mpsii on 2009-02-10
> **ghindo said:**
> This solved it, thank you so much! :KS  I just wonder why I couldn't find that in any of the documentation?

It is not really what would be considered a documentation-worthy item. I think the problem is that, during installation, the slim package does not create the directory. You may wish to use Synaptic to look up the package maintainer. Then you can drop an email to him/her and notify them of the problem with the default installation.

---

### Post by crimesaucer on 2009-02-10
Most people in the Arch forum use the inittab method for SLIM and not the daemons way.

---

### Post by Grant A. on 2009-02-10
> **crimesaucer said:**
> Most people in the Arch forum use the inittab method for SLIM and not the daemons way.

All the 1337 people use daemons. ;)

---

### Post by crimesaucer on 2009-02-11
> **Grant A. said:**
> All the 1337 people use daemons. ;)

I thought all the 1337 people don't even use a login manager.....


But every post that I've seen in Arch that discussed Slim said to run it with inittab and not daemons. Would there be a reason to use the daemons line instead? Would it load faster? Could it be backgrounded?

---

