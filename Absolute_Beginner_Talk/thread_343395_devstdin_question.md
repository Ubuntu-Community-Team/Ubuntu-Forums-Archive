---
title: "/dev/stdin question"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by mathsjunky on 2007-01-21
Many years ago I used to be a unix developer, and would happily write

dd if=/dev/stdin of=test

to create a file from the stdin stream, this doesn't seem to work in linux - neither ubuntu or suse, they both seem to have /dev/stdin as a link to a link to a character file /dev/pts/0.

Running dd if=/dev/pts/0 has the expected result, but why won't /dev/stdin work?

I'm trying to install a package for amsn and I'm getting a couldn't open  /dev/stdin error with sed, and debugging this has prompted the question.

any pointers (sorry :) gratefully received.

Cheers
Paul.

---

### Post by harrisony on 2007-01-21
so your trying to install an amsn plugin and it cant open /dev/stdin?

---

### Post by mathsjunky on 2007-01-21
During the package install I get errors to the effect that sed couldn't open /dev/stdin. That got me looking at the char device stdin, and I'm surprised that its a link to a link and won't work when I use
dd if=/dev/stdin

I'm expecting the two problems are linked, but I'm most interested in the basic dd problem

---

### Post by hal10000 on 2007-01-21
DELETE THIS MESSAGE

sorry.

---

### Post by Bachstelze on 2007-01-21
*cat > foobar.txt* should work too.

---

### Post by mathsjunky on 2007-01-22
Indeed is does. But why should dd if=/dev/stdin not work, simply because its a symbolic link?

---

