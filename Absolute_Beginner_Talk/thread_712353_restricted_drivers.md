---
title: "restricted drivers"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by RyanZec on 2008-03-01
I am trying to enable the restricted driver for my nvidia 8600 and when i goto the restricted driver window and enable for the nvidia one it brings up a window that says "the software source for the package nvidia-glx-new in not enabled. how do i enable my nvidia graphics restricted drivers?

---

### Post by Rocket2DMn on 2008-03-01
Go to System->Administration->Software Sources and enable the universe, multiverse, and restricted repositories.
I don't recall if that's available in Feisty, if not, post your sources.list file:
```
cat /etc/apt/sources.list
```
We'll add the repos manually if necessary.

---

### Post by Rolcol on 2008-03-01
You need to enable Source Code in the Software Sources.

System > Administration > Software Sources > Check "Source Code".

Then try again.

---

### Post by Rocket2DMn on 2008-03-01
> **Rolcol said:**
> You need to enable Source Code in the Software Sources.

System > Administration > Software Sources > Check "Source Code".

Then try again.

Actually it's in the Restricted repo: 
[http://packages.ubuntu.com/gutsy/misc/nvidia-glx-new](http://packages.ubuntu.com/gutsy/misc/nvidia-glx-new)
[http://packages.ubuntu.com/feisty/misc/nvidia-glx-new](http://packages.ubuntu.com/feisty/misc/nvidia-glx-new)

Source code is only needed if you are compiling yourself rather that just DLing the binaries. 95% of us don't need it :)

---

### Post by Rolcol on 2008-03-01
> **Rocket2DMn said:**
> Actually it's in the Restricted repo: 
[http://packages.ubuntu.com/gutsy/misc/nvidia-glx-new](http://packages.ubuntu.com/gutsy/misc/nvidia-glx-new)
[http://packages.ubuntu.com/feisty/misc/nvidia-glx-new](http://packages.ubuntu.com/feisty/misc/nvidia-glx-new)

Source code is only needed if you are compiling yourself rather that just DLing the binaries. 95% of us don't need it :)
My bad... I'm still learning

---

### Post by Rocket2DMn on 2008-03-01
> **Rolcol said:**
> My bad... I'm still learning

Quite alright, we are all still learning, it's a never ending process :)  We're glad you're here to help, don't stop!

---

### Post by sharris203 on 2008-03-01
> **Rocket2DMn said:**
> Actually it's in the Restricted repo: 
[http://packages.ubuntu.com/gutsy/misc/nvidia-glx-new](http://packages.ubuntu.com/gutsy/misc/nvidia-glx-new)
[http://packages.ubuntu.com/feisty/misc/nvidia-glx-new](http://packages.ubuntu.com/feisty/misc/nvidia-glx-new)

Source code is only needed if you are compiling yourself rather that just DLing the binaries. 95% of us don't need it :)

Actaully I had a friend who had this same problem, and it WAS the source code box he had to enable.
(However I myself have never needed it.)

---

### Post by Rocket2DMn on 2008-03-01
> **sharris203 said:**
> Actaully I had a friend who had this same problem, and it WAS the source code box he had to enable.
(However I myself have never needed it.)

Getting the source means it gets compiled on your machine.  There are times when this is useful, but it's a pain in the butt for most people.  I've never used it either, I don't know if it compiles automatically, but you do certainly have the option to do it manually.  However, if you're going to go through the hassle of installing the nvidia drivers not using the Restricted Drivers manager, I have a little guide on how to install the latest from NVIDIA's website.

---

