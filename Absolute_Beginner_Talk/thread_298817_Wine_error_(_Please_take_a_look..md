---
title: "Wine error :( Please take a look."
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by RiGLEY on 2006-11-13
Hi I'm trying to run a program (little opengl based 3d modeler) with wine.
 I can't start it. This is the output from the terminal:

```
X Error of failed request:  BadDevice, invalid or uninitialized input device
  Major opcode of failed request:  147 (XInputExtension)
  Minor opcode of failed request:  3 (X_OpenDevice)
  Serial number of failed request:  66
  Current serial number in output stream:  66
```

Can I try something to make it work?
Thanks!

Daniel

---

### Post by bodhi.zazen on 2006-11-13
> **RiGLEY said:**
> Hi I'm trying to run a program (little opengl based 3d modeler) with wine.
 I can't start it. This is the output from the terminal:

```
X Error of failed request:  BadDevice, invalid or uninitialized input device
  Major opcode of failed request:  147 (XInputExtension)
  Minor opcode of failed request:  3 (X_OpenDevice)
  Serial number of failed request:  66
  Current serial number in output stream:  66
```

Can I try something to make it work?
Thanks!

Daniel

wine is a large, complex program.

You will likely get a better response from [WineHQ](http://appdb.winehq.org/) Search the application database for your application (See the search box on the Left).

You can also try [downgrading wine](http://doc.gwos.org/index.php/HowToWine#Downgrade_wine).

---

### Post by RiGLEY on 2006-11-13
OK, Thanks!

---

### Post by RiGLEY on 2006-11-13
Thanks to the helpful guys at the #WineHQ chatroom, I've managed to resolve this problem. In case somebody has a similar problem - the only thing I had to do is to remove ALL the "wacom tablet" entries in the xorg.conf file. (I don't have a tablet)

Daniel

---

