---
title: "A deb firefox package for Debian Etch PPC??"
date: 2008-02-04
forum: Apple PPC Users
---

### Post by khelben1979 on 2008-02-04
Hello all and greetings!

I'm a Debian Etch PPC user here and I need a little support.

I want to know if and where I can get a ppc deb package regarding Mozilla Firefox. Can anyone help? Deeply appreciated!

Friendly greetings from Sweden

---

### Post by hyperair on 2008-02-04
Surely there exists a deb for Debian Etch PPC in the Debian Etch repositories? If not, you could try adding the ubuntu repository.. 
```

deb http://archive.ubuntu.com/ubuntu dapper main

```
I'm not sure which one corresponds correctly to Debian Etch, so you should try replacing dapper with edgy, feisty, or gutsy.

Then:
```
sudo apt-get install firefox
```

---

### Post by khelben1979 on 2008-02-04
Can you give me a direct link to the package?

I don't want to mess upp my Debian distro with Ubuntu packages.. I also have very limited disk space, so.. I don't want to do it because of that too.

---

### Post by hyperair on 2008-02-04
[http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/](http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/)

---

### Post by khelben1979 on 2008-02-04
Thanks for the link and the fast reply.

I'm choosing to stick with Iceweasel(Firefox). It seems Iceweasel was using a pretty modern version of firefox, but... because of the rename to iceweasel, my bank here in Sweden can't recognise the browser as a qualified web browser, although, since it has all the features which Firefox has, it seems that there is no problem.

The Debian people chose to rename the firefox in their distribution to iceweasel, perhaps Ubuntu has done the same? Do you know? (I've never run Ubuntu and I've never seen it in action, yet, although it should look pretty much as Debian does, I think.)

---

### Post by hyperair on 2008-02-04
No that's not the case with Ubuntu. Ubuntu still has Firefox branded as Firefox. And honestly I must say I prefer it that way.

EDIT: You should try installing the User Agent Switcher add on. That one can make Firefox (or Iceweasel) pretend to be any other browser.

---

### Post by oswaldkelso on 2008-02-05
> **khelben1979 said:**
> Thanks for the link and the fast reply.

I'm choosing to stick with Iceweasel(Firefox). It seems Iceweasel was using a pretty modern version of firefox, but... because of the rename to iceweasel, my bank here in Sweden can't recognise the browser as a qualified web browser, although, since it has all the features which Firefox has, it seems that there is no problem.

The Debian people chose to rename the firefox in their distribution to iceweasel, perhaps Ubuntu has done the same? Do you know? (I've never run Ubuntu and I've never seen it in action, yet, although it should look pretty much as Debian does, I think.)

I run debian testing and both iceweasel and I'm sure firefox are in the repos. I run iceweasel you can change its identity if I remember correctly. I'm not at home at the moment so I cant check.  firefox is in the debian repos but it wont have all the debian security fixes (the reason for the name change) so I would stick with iceweasel and set it to appear as firefox or ie. Dont mix repos with ubuntu as its based on sid with ubuntu tweaks and it may break your system. stick with the debian repos and if you need to upgrade run lenny its very stable and the packages are a bit more modern. (though there is a bad bug in icedove 2 so dont add that package until you've check that its fixed.)

edit as Hyperair said User Agent Switcher lets you decide what browser you look like to the outside world.

---

