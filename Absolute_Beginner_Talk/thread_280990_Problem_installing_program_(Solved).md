---
title: "Problem installing program (Solved)"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by Warthaug on 2006-10-20
I am trying to install cinerella, using these direcitons (dapper):

[http://www.kiberpipa.org/~gandalf/ubuntu/README](http://www.kiberpipa.org/~gandalf/ubuntu/README)

It is not working - adding the relevent sources to my sources.list works fine, both the command line installer, as well as the "Advanced" part of the GUI installer, detect the package fine.  When I try to install from the GUI installer  I get the following error:

"Could not mark all packaged for instillation or upgrade.  The following packages have unresolvable dependancies.  Make sure all required repositories are added and enabled in the preferences."

There is then a list:
"cinelerra:
 Depends: liblame0 (>=3.96.1-1) but it is not installable
 Depends: libquicktimehv but it is not going to be installed
 Depends: libquicktimehv but it is not going to be installed
"

If I use command line installer I get this error:

"Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package cinerella
root@bryan-laptop:/etc/apt# apt-get install cinelerra
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  cinelerra: Depends: liblame0 (>= 3.96.1-1) but it is not installable
             Depends: libquicktimehv (>= 1:2.0.0) but it is not going to be installed
             Depends: libquicktimehv (= 1:2.0.0-1svn20060611.1) but it is not going to be installed
E: Broken packages"

How do I get around this?

Thanx

Bryan

---

### Post by Bachstelze on 2006-10-20
You don't have multiverse enabled... Please paste your sources.list :)

---

### Post by deadgobby on 2006-10-20
Or you can get extra repostories. 
[http://psychocats.net/ubuntu/sources](http://psychocats.net/ubuntu/sources)
 Easy follow directions and try it after. But if you did, see above post.
Gobby

---

### Post by CatKiller on 2006-10-20
You need to enable the multiverse/universe repos, and add in the mjpegtools repository, and you might also need to do ```
sudo aptitude update && sudo aptitude install cinelerra liblame0 libquicktimehv
``` to force the dependencies to be installed along with cinelerra.

Good luck and welcome to the community.

---

### Post by Warthaug on 2006-10-20
Thanx everyone, I went through the steps you recommended and the intall went perfectly.

Once again, thanx

Bryan

---

