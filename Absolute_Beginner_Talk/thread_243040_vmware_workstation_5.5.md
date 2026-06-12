---
title: "vmware workstation 5.5"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by deadspeak on 2006-08-24
hey guys i'm having some real problems getting  vmware up and running.
i get it installed okay but when i run the configue i get this.

Thank you.

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons?
[/usr/share/icons]

What directory contains your desktop menu entry files? These files have a
.desktop file extension. [/usr/share/applications]

In which directory do you want to install the application's icon?
[/usr/share/pixmaps]

Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Workstation is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes] yes

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is not an existing directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]


really beg:confused: inging to do my head in.

any help would really be appreciated
Paul

---

### Post by NetworkGuy on 2006-08-24
Using Synaptic download the linux-headers for the kernel you are currently running  ```
uname -r
``` to get the kernel version.

---

### Post by deadspeak on 2006-08-24
thank you my friend worked a treat

---

### Post by GeekSpeek'r on 2006-08-24
the actaul code (easies)

apt-get install linux-headers-`uname -r` build-essential

---

### Post by NetworkGuy on 2006-08-24
> **GeekSpeek'r said:**
> the actaul code (easies)

apt-get install linux-headers-`uname -r` build-essential

I've never been able to get that command to work for me as often as I tried..:)

---

### Post by gruffy-06 on 2006-08-25
---

---

### Post by gruffy-06 on 2006-08-25
> **NetworkGuy said:**
> I've never been able to get that command to work for me as often as I tried..:)

You need to use sudo, because apt-get requires administrative rights.

Run the following in a terminal:

*sudo* apt-get install [whatever packages you want]

You will be asked for *your* password, not root's.

It should work now.

---

### Post by Spookster on 2006-08-25
> **NetworkGuy said:**
> I've never been able to get that command to work for me as often as I tried..:)

You did enter ` as a backtick, (top left of your keyboard) not a normal apostrophe...?

---

