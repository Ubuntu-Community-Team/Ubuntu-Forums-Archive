---
title: "Removed perl from /usr/local/lib"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by princeza on 2007-12-11
How do I get it back?

---

### Post by spai on 2007-12-11
Actually I tried
```
srikanth@ubuntu:/usr/local/lib$ ls
ocaml  python2.5  site_ruby
```
Are you sure that is the default directory?For me it looks like it is in /usr/bin/perl
Try "whereis" to check where perl actually is,
```
srikanth@ubuntu:/usr/local/lib$ whereis perl 
perl: /usr/bin/perl /etc/perl /usr/lib/perl /usr/share/perl /usr/share/man/man1/perl.1.gz
```
If all things fail you can always re-install

---

### Post by princeza on 2007-12-11
yes, it's in  /usr/bin/perl but what did I actually do then by typing
sudo rm -r /usr/local/lib/perl?

it was in there before, along with python!

---

### Post by spai on 2007-12-13
Really? Then I must have deleted mine too.
Then you had better re-install

---

