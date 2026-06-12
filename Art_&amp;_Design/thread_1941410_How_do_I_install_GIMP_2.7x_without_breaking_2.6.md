---
title: "How do I install GIMP 2.7x without breaking 2.6"
date: 2012-03-15
forum: Art &amp; Design
---

### Post by BcRich on 2012-03-15
H
'd like to install the latest GIMP 2.7.5 without breaking my current working installation 2.6.10. there are instructions on the gimp website >  
You install the new version into a separate prefix, say /opt/gimp-2.7 by passing --prefix=/opt/gimp-2.7tothe configure script. Then, in order to run the binary installed there, you change your environment to look for executables in /opt/gimp-2.7/bin by setting PATH=/opt/gimp-2.7/bin and you tell your linker to pick up libraries from /opt/gimp-2.7/lib by setting LD_LIBRARY_PATH=/opt/gimp-2.7/lib. Do not forget to export both variables.  
so does that mean i do this
```
./configure prefix=/opt/gimp2-7
``` 
when running the configure script? then after make install,
```
PATH= /opt/gimp-2.7/bin
``` then
```
LD_LIBRARY_PATH=/opt/gimp-2.7/lib
```
then ```
export PATH
```
```
export LD_LIBRARY_PATH
```
or is it just a simple case of running configure with the above prefix then placing this script in /usr/local/bin
```
 #!/bin/sh

PATH=/opt/gimp-2.7/bin:$PATH 
export PATH 
LD_LIBRARY_PATH=/opt/gimp-2.7/lib 
export LD_LIBRARY_PATH

/opt/gimp-2.7/bin/gimp-2.7 "$@" 
```
does the above script need to have a specific name and extension?
thanks to you if u can help me :)

---

