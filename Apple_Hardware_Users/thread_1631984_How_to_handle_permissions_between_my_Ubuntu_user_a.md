---
title: "How to handle permissions between my Ubuntu user and OSX user?"
date: 2010-11-27
forum: Apple Hardware Users
---

### Post by skullmunky on 2010-11-27
I'd like to be able to access files in my OSX account while in Ubuntu.  For now read-only is ok, but the immediate problem is just permissions.  I have a user in OSX and one in Ubuntu both named skullmunky, but of course the id #'s are different (in OSX it's 501, in Ubuntu it's 1001).  I'd like to be able to log into Ubuntu and have access to everything in /media/Macintosh HD/Users/skullmunky.

I can't figure out a nice way to do this other than manually altering the uid of my Ubuntu user, which seems awkward.  But better than my other methods, which involve either sudo cp'ing stuff over to the Ubuntu partition (wasteful), or booting into OSX and chmod'ing everything a+r (seems like a bad idea).  

Or, is there a way to mount the hfs+ volume without permissions enabled?

---

### Post by srs5694 on 2010-11-28
Change the UID on one side or the other. It's not that hard. In Ubuntu:

```

sudo chown -R 501 /home/skullmonkey
sudo usermod -u 501 skullmonkey

```

You should then *immediately* log out and back in again.

Note that a UID of 501 is unusual in Ubuntu, since it's less than the officially-supported minimum UID value. It does work, though. (I've done this myself.) IIRC, there are some minor side effects, like a need to type your username rather than point and click on it when logging in. In theory, it's better to change the OS X UID to match the Ubuntu one, but I'm not sure offhand precisely what commands you'd use in OS X to do this.

---

### Post by ceratophyllum on 2010-11-28
Rather than risk goofing up the permissions on your working linux user account, why not create a new linux user with UID 501? Once you've tested that the new user can access the OS X partition, then migrate your linux files from skullmoney's (UID 1001) home directory to the new user's home. (It sounds like most of your stuff is on the OS X partition anyway.)


I don't know whether it's better to change the OS X UID. Considering how kludgy and broken a lot of OS X is--Remember it only has to support a very limited amount of Apple hardware and most Os X users don't even know what Terminal is for-- I think it is a very bad idea to do anything,um, funky with your OS X account.

---

