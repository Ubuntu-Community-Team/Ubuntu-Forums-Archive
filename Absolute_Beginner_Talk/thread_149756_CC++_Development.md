---
title: "C/C++ Development"
date: 2006-03-24
forum: Absolute Beginner Talk
---

### Post by aquatone282 on 2006-03-24
Hi,

I'd like to set up my 5.10 install up for C/C++ development.

What do I need to install, where can I get it, and how do I install it?

TIA,

Jim

---

### Post by taurus on 2006-03-24
Probably build-essential as
```

sudo apt-get install build-essential

```

---

### Post by aquatone282 on 2006-03-24
Thanks!

Will build-essential install gcc or do I need to do that seperately?

---

### Post by gerbman on 2006-03-24
It should take care of gcc. Also, I would recommend a good editor like emacs. It might take a little time getting used to, but I absolutely cannot live without it now that I have.

---

### Post by aquatone282 on 2006-03-24
Yes, build-essential does include gcc.

I found the info at: [http://packages.ubuntulinux.org/breezy/devel/build-essential](http://packages.ubuntulinux.org/breezy/devel/build-essential)

Thanks for your help!

---

### Post by skirkpatrick on 2006-03-24
I've been using Eclipse for all my development in C/C++.

---

### Post by Joshuwa on 2006-03-24
I've never used Eclipse, but have heard good things about it.

Personally I've been using Anjuta, and absolutely love it.

```
sudo apt-get install anjuta
```

will install it for you. (replace anjuta with eclipse to install that). Might have to add the universe/multiverse to your source list though, not sure.

---

### Post by TylerH on 2006-03-26
how do you use eclipse for c++?
i thought it was just for java?
do i have to install some extra functionality?

---

### Post by skirkpatrick on 2006-03-28
Go to [http://www.eclipse.org/cdt/](http://www.eclipse.org/cdt/) and it will tell you how to install the C/C++ plugin.  There's also one around for subversion, if you want to use instead of CVS for version control.

---

