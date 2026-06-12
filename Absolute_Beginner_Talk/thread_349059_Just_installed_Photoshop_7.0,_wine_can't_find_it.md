---
title: "Just installed Photoshop 7.0, wine can't find it"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by kliljedahl on 2007-01-29
Trying to run from the terminal, so it's probably my command line. Got the same result with Dreamweaver MX. Here's what I put in for Photoshop: 

wine home/kliljedahl/.wine/drive_c/Program Files/Adobe/Photoshop 7.0/Photoshop.exe

Here's the result:

wine: cannot find 'home/kliljedahl/.wine/drive_c/Program'
kliljedahl@kliljedahl-desktop:~$ 

What did I do wrong?

---

### Post by Zzl1xndd on 2007-01-29
Im no Wine expert by any stretch but when I use the programs I have installed with wine I just use the command "wine programname"

---

### Post by punx45 on 2007-01-29
you have spaces in your path.  escape the space with \

e.g. ```
home/kliljedahl/.wine/drive_c/Program\ Files/Adobe/Photoshop\ 7.0/Photoshop.exe
```

i think quotes will work also

```
home/kliljedahl/.wine/drive_c/'Program Files'/Adobe/'Photoshop 7.0'/Photoshop.exe
```

and as suggested above, you could also cd to the directory that contains the program, and execute with wine <program-name>.

however, if you are creating a custom menu item etc. you would need the full path so the former example would be what you use.

---

### Post by kliljedahl on 2007-01-29
> **punx45 said:**
> you have spaces in your path.  escape the space with \

e.g. ```
home/kliljedahl/.wine/drive_c/Program\ Files/Adobe/Photoshop\ 7.0/Photoshop.exe
```

i think quotes will work also

```
home/kliljedahl/.wine/drive_c/'Program Files'/Adobe/'Photoshop 7.0'/Photoshop.exe
```

and as suggested above, you could also cd to the directory that contains the program, and execute with wine <program-name>.

however, if you are creating a custom menu item etc. you would need the full path so the former example would be what you use.


Got this with both:
home/kliljedahl/.wine/drive_c/Program\ Files/Adobe/Photoshop\ 7.0/Photoshop.exe
bash: home/kliljedahl/.wine/drive_c/Program Files/Adobe/Photoshop 7.0/Photoshop.exe: No such file or directory
kliljedahl@kliljedahl-desktop:~$

---

### Post by %hMa@?b&lt;C on 2007-01-29
> **kliljedahl said:**
> Got this with both:
home/kliljedahl/.wine/drive_c/Program\ Files/Adobe/Photoshop\ 7.0/Photoshop.exe
bash: home/kliljedahl/.wine/drive_c/Program Files/Adobe/Photoshop 7.0/Photoshop.exe: No such file or directory
kliljedahl@kliljedahl-desktop:~$
try
wine 'home/kliljedahl/.wine/drive_c/Program Files/Adobe/Photoshop 7.0/Photoshop.exe'
that is how it sould do to work

---

### Post by kliljedahl on 2007-01-29
> **jeffc313 said:**
> try
wine 'home/kliljedahl/.wine/drive_c/Program Files/Adobe/Photoshop 7.0/Photoshop.exe'
that is how it sould do to work

And I got:
wine 'home/kliljedahl/.wine/drive_c/Program Files/Adobe/Photoshop 7.0/Photoshop.exe'
wine: cannot find 'home/kliljedahl/.wine/drive_c/Program Files/Adobe/Photoshop 7.0/Photoshop.exe'

Maybe it needs full quotes instead of half quotes?

No that didn't work either

Maybe it doesn't support 7.0 yet.

---

### Post by Aythun on 2007-01-29
```
wine "/home/kliljedahl/.wine/drive_c/Program Files/Adobe/Photoshop 7.0/Photoshop.exe"
```

Prefix the path with a slash, otherwise it'll be looking within the current directory.

---

### Post by kliljedahl on 2007-01-29
> **Aythun said:**
> ```
wine "/home/kliljedahl/.wine/drive_c/Program Files/Adobe/Photoshop 7.0/Photoshop.exe"
```

Prefix the path with a slash, otherwise it'll be looking within the current directory.

And the I got this, so I guess there are other (driver) problems:
 wine "/home/kliljedahl/.wine/drive_c/Program Files/Adobe/Photoshop 7.0/Photoshop.exe"
libGL warning: 3D driver claims to not support visual 0x4b
fixme:actctx:QueryActCtxW 80000010 0x116283c (nil) 1 0x33fdc4 8 (nil)
libGL warning: 3D driver claims to not support visual 0x4b
X Error of failed request:  BadDevice, invalid or uninitialized input device
  Major opcode of failed request:  145 (XInputExtension)
  Minor opcode of failed request:  3 (X_OpenDevice)
  Serial number of failed request:  35
  Current serial number in output stream:  35

---

### Post by embeemb on 2007-03-29
I'm running dapper with Wine 0.9.12 and I got the same result when I tried to load Photoshop 7

> fixme:actctx:QueryActCtxW stub!
X Error of failed request:  BadDevice, invalid or uninitialized input device
  Major opcode of failed request:  145 (XInputExtension)
  Minor opcode of failed request:  3 (X_OpenDevice)
  Serial number of failed request:  37
  Current serial number in output stream:  37

Help.. Please?

---

### Post by pognonec on 2007-03-30
Hm,
that may not answer your question directly, but...
did you ever try "The Gimp"?
I am not using Photoshop anymore now. And if you hate changing habits, there even is an extension to get the same exact menus as Photoshop, available somewhere on line....
My 2 cts

---

