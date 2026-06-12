---
title: "Source List for dumb Paul"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by Paul_world10 on 2007-03-07
I've been reading 'Beginning Ubuntu Linux' by Keir Thomas. This has been a good book for me. I am on page 228 anyway :]  .

I've got some source list stuff going on with dapper 6.06 LTS    : heres my source list 

# Automatically generated sources.list
# [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages
# GPG key: 437D05B5
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted 
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe multiverse 
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

in my  /system/admin/update tab in Gnome ,im getting 8 out of 9 running from system updates.
it pauses after the 8th and when I click cancel 
I feel so dumb still which I am anyway
this is what I get:

[http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg)
Could not download all repository indexes

please help

thank you.

---

### Post by eljalill on 2007-03-07
Hello!

Basically the sources.list is deep magi to me, and I never understand why one or the other repository is not running anymore... 

However the problem usually gets clearer to me, when I use synaptic to update. Lese you could simply try another sources.list (I've done that a couple times)

Mine is:
```
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.

deb http://de.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse

deb http://de.archive.ubuntu.com/ubuntu/ edgy-proposed main restricted universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ edgy-proposed main restricted universe multiverse

##### MAJOR BUG FIX UPDATES#####
##(produced after the final release)
deb http://de.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse

##### UBUNTU SECURITY UPDATES #####
deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

##### BACKPORTS REPOSITORY #####
##(Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://de.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
                                                                                                                                                                          
##### CANONICAL COMMERCIAL REPOSITORY #####
##(Hosted on Canonical servers, not Ubuntu servers. RealPlayer10, Opera and more to come.) 
deb http://archive.canonical.com/ubuntu dapper-commercial main

##### BERYL REPOSITORY #####
deb http://ubuntu.beryl-project.org/ edgy main

##### New Network Manager #####
deb http://www.linux2go.dk/ubuntu edgy main

##### Opera repository #####
deb http://deb.opera.com/opera etch non-free

##### Wine repository #####
deb http://wine.budgetdedicated.com/apt edgy main
deb-src http://wine.budgetdedicated.com/apt edgy main

```

But as you can see I am not using US repositories. Theoretically you should be able to replace de through us? or else copy someone elses list... 

best,
eljalill

---

### Post by wpshooter on 2007-03-07
Paul:

My suggestion would be to go into software properties and ADD in the universe and multiuniverse repositories and then after that make sure ALL listings are checked and then come out of software properties, reboot the computer and then I believe you might have what you need.  My suggestion would be to stop trying to analyze these text listings of the repositories and use the GUI functions that are built into Ubuntu.

Good luck.

---

### Post by Perfect Storm on 2007-03-07
You might want to take a look at Ubuntu Source Generator: [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

---

