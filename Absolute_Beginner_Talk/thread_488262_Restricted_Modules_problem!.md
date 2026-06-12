---
title: "Restricted Modules problem!"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by thunderloki on 2007-06-30
Hi, I'm new to Linux but so far the forums have been a great help.  I'm running Ubuntu Server 2.6.20.16 with GDE and a firewall and things have been working quite nicely.  I run GDE since it's my home PC when I'm around.

However I'm having some problems with drivers which seem linked to my ATI X800 graphics card.  I thought I got it all figured out when I got GDE running and fglrx set up, but I decided I wanted to try to enable desktop effects.  I think that the problem is that "direct rendering" does not work, so I followed the guide at [http://ubuntuforums.org/showthread.php?t=143283&highlight=mesa+dri+ati](http://ubuntuforums.org/showthread.php?t=143283&highlight=mesa+dri+ati).

When I try to **sudo apt-get remove linux-restricted-modules-$(uname -r)**, it says: "Couldn't find package linux-restricted-modules-2.6.20-16-server".  I tried to use the Restricted Drivers Manager and it simply crashes with the message "You need to install the package linux-restricted-modules-2.6.20-16-server".  I used Synaptic to try to get this package but couldn't find anything that matched it so I installed (or reinstalled) the following packages:
 - linux-restricted-modules-2.6.20-16-generic
 - linux-restricted-modules-common
 - linux-restricted-modules-generic

](*,) I couldn't find anything marked -server and the same problems are still coming up.  Any help would be appreciated.

---

### Post by thunderloki on 2007-06-30
I think I found the solution:

[http://ubuntuforums.org/showthread.php?t=441013&highlight=restricted+drivers+manager+problem](http://ubuntuforums.org/showthread.php?t=441013&highlight=restricted+drivers+manager+problem)

I'm trying this for the -server kernel version...still I really have no idea what I'm doing, just winging it.  So if anyone has suggestions they would really be welcome.

---

### Post by thunderloki on 2007-06-30
When I sudo apt-get install linux-restricted-modules-$(uname -r) it tells me:

Package linux-restricted-modules-2.6.20-16-server is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-restricted-modules-2.6.20-16-server has no installation candidate

but if I revert to the unedited package lists, it just goes back to the normal error.

If anyone knows about how to make the restricted modules work on Server...or a non-generic kernel...that would be great.  peace

---

### Post by thunderloki on 2007-06-30
Bump.  Problem solved when I boot in -16-generic.  But what's the difference between that and -16-server?  And why won't it work in -server?

---

