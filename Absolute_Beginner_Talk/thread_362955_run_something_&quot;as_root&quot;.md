---
title: "run something &quot;as root&quot;"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by aalr1986 on 2007-02-16
What does it mean when I want to install a package, I have to run it "as root"...?
What do I do there?

---

### Post by rabid emu on 2007-02-16
Means you need Super User privilages, think Admin for windows.  This means you need to run the command that you're trying to do with "sudo" in front of it, like "sudo apt-get install <package name>".  It will ask you for your user password.

Running as Root generally isn't a good thing unless you have to, like in this case where it tells you to.  Most of the time try not to use sudo unless you know you need to.

---

### Post by aalr1986 on 2007-02-16
well, I tried to install my packages that way, and it said "it didn't find a package", even though i'm in the same directory....
can I use "sudo install <package name>"....???

---

### Post by bodhi.zazen on 2007-02-16
LOL aalr1986, what are you truing to install ??

See this post :

[http://www.ubuntuforums.org/showpost.php?&p=2165017&postcount=4](http://www.ubuntuforums.org/showpost.php?&p=2165017&postcount=4)

---

### Post by Maestro23 on 2007-02-16
> **aalr1986 said:**
> well, I tried to install my packages that way, and it said "it didn't find a package", even though i'm in the same directory....
can I use "sudo install <package name>"....???

> sudo apt-get install pkg

or 

sudo aptitude install pkg

Installing in Ubuntu: [http://www.cutlersoftware.com/ubuntuinstall/](http://www.cutlersoftware.com/ubuntuinstall/)
                                      [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

*To the OP:  By using the .tar files, you are installing form "source", not from a package.

---

### Post by aalr1986 on 2007-02-16
> **bodhi.zazen said:**
> LOL aalr1986, what are you truing to install ??


i'm trying to install the last firefox.. the 2.0.0.1, and some divx codecs for Linux.... they're both in .tar.gz packages.. I checked the document you gave me already
the thing is that:
I'm using KUBUNTU.... so that makes a little difference

any ideas?

---

### Post by bodhi.zazen on 2007-02-16
Well, for firefox take a look at this : [https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

for restricted formats see here :

Restricted formats:

	[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

	[http://www.ubuntuforums.org/showthread.php?&t=182902](http://www.ubuntuforums.org/showthread.php?&t=182902)

I do not think KDE makes much difference ...
[indent]Is there a specific step or question you have ?[/indent]

Also Maestro23 gave you some nice links on su powers.

To change to root, in a terminal type:

```
sudo -i
```

Enter you log-in password

Type exit to return to your user status.

---

