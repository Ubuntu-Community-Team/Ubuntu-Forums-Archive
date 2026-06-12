---
title: "How do I open ports on an Ubuntu box used as a router?"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by teleios on 2006-10-31
The old systems admin who setup an Ubuntu box to act as a router for a colocation quit a few weeks ago, and I have been trying to make sure that everything stays working with him gone.  I'll be the first to admit I know tons about Windows, and very little about Ubuntu.  I'm trying to use Webmin setup on some of the servers behind the router, but it seems that the port isn't open to allow that traffic through.  I've looked through the minimal documentation that the old systems admin gave to me, but none of the .conf files and other directories that he has written contain anything to do with what ports are open.

What file would I be looking for, or how do I open up new ports on an Ubuntu router?  Any help would be greatly appreciated.

---

### Post by hw-tph on 2006-10-31
Don't.

Opening Webmin to the world is a very dangerous thing to do. Use SSH to log in to the servers if you need to access them from off site locations, and even when using SSH you shouldn't be using passwords if you can avoid it. Gentoo has a good guide on creating and using an [SSH key chain](http://www.gentoo.org/doc/en/keychain-guide.xml).


Håkan

---

### Post by teleios on 2006-11-02
Thanks for the info.  However, I still need to be able to open ports for different functions, ie mail servers, and don't know how to do that.

---

