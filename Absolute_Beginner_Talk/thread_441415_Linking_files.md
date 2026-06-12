---
title: "Linking files?"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by bobtherocket on 2007-05-12
Ok, I have something that is asking for /usr/bin/perl to install, but I know everything it needs is probably in /usr/local/bin/perl.

Any suggestions for a fix?

---

### Post by taurus on 2007-05-12
You can either add /usr/local/bin to your path in ~/.bashrc or you can link it with

```
sudo ln -s /usr/local/bin/perl /usr/bin/perl
```

---

### Post by bobtherocket on 2007-05-12
ln: creating symbolic link `/usr/bin/perl' to `/usr/local/bin/perl': File exists

:(

---

### Post by taurus on 2007-05-12
```
ls -la /usr/bin/perl
```

---

### Post by bobtherocket on 2007-05-12
:P So what should I do to change the permissions?

---

### Post by taurus on 2007-05-12
What permissions are you talking about?  Is there a perl compiler in /usr/bin?  You need to be real careful with changing permissions because if you do it wrong, you would crash your whole system.

---

### Post by bobtherocket on 2007-05-12
ls -la /usr/bin/perl
-rwxr-xr-x 1 root root 1077808 2007-03-05 21:05 /usr/bin/perl

Was just wondering if changing perms would work or not? Dunno, what would you suggest here?

---

### Post by taurus on 2007-05-12
What's wrong with the current permissions for /usr/bin/perl?  

```
perl -version
```

---

### Post by bobtherocket on 2007-05-12
This is perl, v5.8.8 built for i486-linux-gnu-thread-multi

Well, it won't let me install my program because: 

```

/usr/bin/perl, libX11.so.6, libXext.so.6, libc.so.6, libc.so.6(GLIBC_2.0), libc.so.6(GLIBC_2.1), libc.so.6(GLIBC_2.1.3), etc.

```

When I could search for it myself, and find the files.

---

### Post by taurus on 2007-05-12
What program are you trying to install and how do you try to install it?

---

### Post by bobtherocket on 2007-05-12
Uh....Xpertmud with KPackage? Comes as an .rpm. I tried converting to .deb, and it installs just fine, and I can connect to a game, though it crashes out when I enter my password. :/

---

