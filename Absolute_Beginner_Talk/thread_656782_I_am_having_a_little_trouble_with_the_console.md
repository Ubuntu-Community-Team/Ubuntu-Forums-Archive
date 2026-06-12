---
title: "I am having a little trouble with the console:"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by C. Stringer on 2008-01-02
I am attempting to install my webcam on my Ubuntu desktop using instructions from this site:
I am using 7.10
[http://www.linuxlove.org/2007/11/12/linux-webcam-microsoft-lifecam-nx-6000-on-ubuntu-and-fedora/](http://www.linuxlove.org/2007/11/12/linux-webcam-microsoft-lifecam-nx-6000-on-ubuntu-and-fedora/)

As soon as I type  "sudo apt-get install subversion build-essential linux-headers libsdl1.2 libsdl1.2-dev" I am asked for my password.  When I try to enter the password, the console doesn't accept any input.  What would cause this/ why is this happening?

Thanks,

---

### Post by PeterJS on 2008-01-02
It's supposed to do that. It is accepting keyboard input it's just not giving you any visual feedback, this is a security feature to make it harder for people to read your password over your shoulder as you're typing.

---

### Post by C. Stringer on 2008-01-02
Oh.  Thanks.  I probably should have checked for that.

---

### Post by ~LoKe on 2008-01-02
Yeah, I was kind of surprised the first time I saw it.  I'm used to seeing asterisks, but I guess that would give away the password length.

---

