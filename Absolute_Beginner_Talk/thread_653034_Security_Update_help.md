---
title: "Security Update help"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by rorsino on 2007-12-29
Hello everyone,

I too am getting the following message while installing Ubuntu 7.10 server.

"while installing Ubuntu 7.10 clean install, from the cd i got from the website (i386 desktop) i got this error message:

"""The security update on security.Ubuntu.com could not be accessed, so those updates will not be made available to you at this time. You should investigate this later.
comments entries for security.Ubuntu.com have been added to /etc/apt/sources.list file """

Because of this error everyting in my /etc/apt/sources.list has been commented out.  I edited the file and uncommented all the repository links except for the source.

Now when I run apt-get update or apt-get install ubuntu-desktop,  I get, "Failed to fetch [http://us.archive.ubuntu.com/etc](http://us.archive.ubuntu.com/etc)......   Could not resolve 'us.archive.ubuntu.com'

I am hooked up to my network and can ping my router and wireless router.  I am not sure where to go from here.  Ant help would be greatly appreciated !!

---

### Post by p_quarles on 2007-12-29
Can you ping an outside URL?:
```
ping -c 5 www.google.com
```

---

### Post by eternicode on 2007-12-29
Another post like this popped up yesterday.  Is this using Adept or Synaptic or some other GUI updater?

When you run "sudo aptitude update", it should start "Get"ing a bunch of files.  Does it do this, or does it give you a bunch of "Err" lines (or something similar)?  You also might post the output here.

It's probably just an update that the repo maintainers haven't set the proper permissons on yet; it happens every once in a while.  It should be fixed sometime soon, though I don't understand why the update program would comment out the entire sources.list.

---

