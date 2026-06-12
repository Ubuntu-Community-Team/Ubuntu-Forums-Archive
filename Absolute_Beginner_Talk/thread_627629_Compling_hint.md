---
title: "Compling hint"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by And1945 on 2007-11-30
I just found out that my Audacious was out of date, and the auto updater doesnt see it. So I decided to download the binaries. Then I had to figure out how to compile it.

It gave me an error:
```
configure: error: C compiler cannot create executables
```

Then I found this delightful little command:
```
sudo apt-get install build-essential
```

Now it tells me I dont have something called pango. Honestly, I ran the synaptic, and installed everything I thought was relevant to this.

This havent really worked. I somehow found out that panga, has something to do with glib2.
Am I doing this the wrong way? Because i keep getting errors.

EDIT:

It tells me i need the following:

  Glib 2.6
  GTK+ 2.6
  libglade >= 2.4
  mcs >= 0.1

---

### Post by Paul820 on 2007-11-30
Go to synaptic and install the following
> libglib2.0-dev
libgtk2.0-dev
libglade2-dev
libmcs-dev
Unless you have **all** the dependencies you are not going to get past ./configure.

---

### Post by And1945 on 2007-11-30
sorry for double post.

---

### Post by And1945 on 2007-11-30
Now it is starting to whine about missing libmowgli? omg...

I found a .deb file at [http://packages.ubuntu.com](http://packages.ubuntu.com) ... no no worries there

---

### Post by Vixis on 2007-11-30
enable source packages in the sources.list
```
sudo apt-get build-dep audacious
```
 build-dep causes apt-get to install/remove packages in an attempt to satisfy the build dependencies for a source package.

then you can disable source packages in the sources.list.

---

### Post by And1945 on 2007-11-30
> **Vixis said:**
> enable source packages in the sources.list
```
sudo apt-get build-dep audacious
```
 build-dep causes apt-get to install/remove packages in an attempt to satisfy the build dependencies for a source package.

then you can disable source packages in the sources.list.

How do I enable that? i tried reading though the /etc/apt/sources.list ... cant find anything about sources.

---

### Post by And1945 on 2007-11-30
Nevermind. I did it the wrong way, trying to install that mowgli library. It is running the Audacious install now.

Thanks! Think it is fixed, with my computer you will never know.

EDIT: Okay, When I click on Audacious nothing happens. *sigh* :)

EDIT: I wrote "rm -rf .config/audacious" in my terminal, now its version 1.3 instead of version 1.4 ...

---

### Post by Vixis on 2007-11-30
> **And1945 said:**
> How do I enable that? i tried reading though the /etc/apt/sources.list ... cant find anything about sources.

System -> Administration -> Software Sources
Enable Source code

In /etc/apt/sources.list lines for source code are started with deb-src

---

### Post by And1945 on 2007-11-30
> **Vixis said:**
> System -> Administration -> Software Sources
Enable Source code

In /etc/apt/sources.list lines for source code are started with deb-src

Sorry, I figured that out... but it still only version 1.3.2 instead of 1.4.1

---

### Post by And1945 on 2007-11-30
Is it so difficult to compile a piece of software? :(

---

### Post by And1945 on 2007-12-01
*bump*

---

### Post by And1945 on 2007-12-01
I added a Debian software source, and it updated to Audacious 1.4.0 right away. Way only for Debian? I dont understand.

---

