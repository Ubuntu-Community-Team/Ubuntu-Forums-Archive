---
title: "libgpod 0,6,0"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by disappearedng on 2008-02-22
Hi guys
after trying to install libgpod 0.6.0, 
i get this error message

./configure
make

"make  all-recursive
make[1]: Entering directory `/home/disappearedng/Documents/Software/ipod/libgpod-0.6.0'
Making all in src
make[2]: Entering directory `/home/disappearedng/Documents/Software/ipod/libgpod-0.6.0/src'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/disappearedng/Documents/Software/ipod/libgpod-0.6.0/src'
Making all in tools
make[2]: Entering directory `/home/disappearedng/Documents/Software/ipod/libgpod-0.6.0/tools'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/disappearedng/Documents/Software/ipod/libgpod-0.6.0/tools'
Making all in tests
make[2]: Entering directory `/home/disappearedng/Documents/Software/ipod/libgpod-0.6.0/tests'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/disappearedng/Documents/Software/ipod/libgpod-0.6.0/tests'
Making all in po
make[2]: Entering directory `/home/disappearedng/Documents/Software/ipod/libgpod-0.6.0/po'
file=`echo de | sed 's,.*/,,'`.gmo \
          && rm -f $file &&  -o $file de.po
/bin/sh: -o: not found
make[2]: *** [de.gmo] Error 127
make[2]: Leaving directory `/home/disappearedng/Documents/Software/ipod/libgpod-0.6.0/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/disappearedng/Documents/Software/ipod/libgpod-0.6.0'
make: *** [all] Error 2
"

What does this  mean?

---

### Post by disappearedng on 2008-02-22
bump any help

---

