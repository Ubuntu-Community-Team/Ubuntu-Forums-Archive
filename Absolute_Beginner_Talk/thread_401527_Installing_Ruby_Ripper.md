---
title: "Installing Ruby Ripper"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by Majin Zero on 2007-04-04
I'm trying to install ruby ripper

[http://rubyforge.org/projects/rubyripper](http://rubyforge.org/projects/rubyripper)

However, after unarchiving the tar ball, and running make install from the directory; nothing seems to have happened.

I can't find ruby ripper with app finder, and I don't know the command for it.

---

### Post by boredandblogging.com on 2007-04-04
Look under the unarchived source directory. The compiled binaries are probably in there somewhere. The make install just copies them somewhere. If you can identify it, try doing a 'sudo updatedb' and then use locate to find the binaries.

---

### Post by rabid9797 on 2007-04-04
why not use one of the provided audio rippers already in the repos, such as sound juicer?

---

### Post by Majin Zero on 2007-04-05
> **boredandblogging.com said:**
> Look under the unarchived source directory. The compiled binaries are probably in there somewhere. The make install just copies them somewhere. If you can identify it, try doing a 'sudo updatedb' and then use locate to find the binaries.

K, I found the binaries, now what?

---

### Post by Maestro23 on 2007-04-05
> **Majin Zero said:**
> K, I found the binaries, now what?

Take a look at the README doc in the extracted folder.  Tells you want dependencies are required and gives install instructions.

If you have never installed from source before on Ubuntu, take a look at Section 4: Installing from Source: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Major_Kong on 2008-05-09
> **rabid9797 said:**
> why not use one of the provided audio rippers already in the repos, such as sound juicer?

2 Reasons Mostly:

1. RubyRipper is the only one that offers Secure Ripping.

2. Better encoding support.


PS: There's .deb packages avaliable at getdeb.net for rubyripper. Although there for Ubuntu 7.10, they should work in the current version.

---

