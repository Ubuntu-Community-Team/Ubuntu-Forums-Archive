---
title: "Compiling"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by pmptg on 2007-05-03
I downloaded a program that I need for my HD tuner a .tgz file. I extracted it and got a folder with "Stuff" in it. I was told it needed to be compiled. How do I go about that ( it has a makefile in it - if that helps and the file is on my desktop). HELP!!!

---

### Post by aysiu on 2007-05-03
Take a look at method #4 here:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Cypher on 2007-05-03
Most modern programs usually follow these steps
```

./configure

```
followed by
```

make

```
and finally
```

sudo make install

```

So attempt that and see how you fare..

---

### Post by pmptg on 2007-05-04
./configure didn't work. I did a 'make' command and then it put a file in the folder with a lock by it. Tried make install but no luck

---

### Post by Billy McCann on 2007-05-04
Within every tar.gz is a README.  But absolutely sure to read it.

---

### Post by pmptg on 2007-05-04
/*

 * libhdhomerun

 *

 * Copyright © 2005-2006 Silicondust Engineering Ltd. <www.silicondust.com>.

 *

 * This library is free software; you can redistribute it and/or

 * modify it under the terms of the GNU Lesser General Public

 * License as published by the Free Software Foundation; either

 * version 2.1 of the License, or (at your option) any later version.

 *

 * This library is distributed in the hope that it will be useful,

 * but WITHOUT ANY WARRANTY; without even the implied warranty of

 * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU

 * Lesser General Public License for more details.

 *

 * You should have received a copy of the GNU Lesser General Public

 * License along with this library; if not, write to the Free Software

 * Foundation, Inc., 51 Franklin St, Fifth Floor, Boston, MA  02110-1301  USA

 */



Top level include file: hdhomerun.h



Top level API: hdhomerun_device. See hdhomerun_device.h for documentation.



The hdhomerun_device API should be used rather than the low level control and video APIs required with previous versions.



Additional libraries required:

- pthread

- iphlpapi (windows only)

---

### Post by Sef on 2007-05-04
Did you install build-essential?  If not, then this is how to do it:

Applications > Accessories > Terminal

```
sudo aptitude update
```

```
sudo aptitude install build-essential
```

If you have then just do this one, which will need to be added

```
sudo aptitude install pthread
```

You could also install them from Synaptic.  (If it is the repositories.)

---

