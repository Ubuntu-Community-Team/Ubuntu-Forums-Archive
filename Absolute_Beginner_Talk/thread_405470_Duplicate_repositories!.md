---
title: "Duplicate repositories?!"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by rufousfelix on 2007-04-09
I am not sure when it happened, but I have been getting the following warning for months.  It states I have duplicate source lists for Dapper main packages, multiverse and so on.  I am not sure how these lists are created, so I have resisted the impulse to delete all named files in hopes if I reload the repositories all would be fine.  Probably it would not.

The only side effect, as far as I can determine, is the update notifications are problematic as to when they occur.

The question is, What if anything can I do to eliminate this warning?

==============================================================

Warning

The following problems were found on your system:

W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper_multiverse_binary-i386_Packages)

---

### Post by francisco_athens on 2007-04-09
first make sure you are not running synaptic or aptitude.

then do

```
 sudo gedit /etc/apt/sources.list 
```

you can then remove or comment out duplicate entries.

you can comment out an entry by using a #  at the beginning of a line.

after you save it out and close gedit do:

```
 sudo apt-get update 
``` 

to update your database.

you can then run synaptic again and check.

---

### Post by slimdog360 on 2007-04-09
yes there is

aysiu has a good site for that sort of thing.
[http://www.psychocats.net/ubuntu/sources]("http://www.psychocats.net/ubuntu/sources")
and just replace your list with the dapper list on the site.

---

