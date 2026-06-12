---
title: "Delete &amp; NumLock"
date: 2006-05-13
forum: Absolute Beginner Talk
---

### Post by JNowka on 2006-05-13
1st) How do you delete a folder that has stuff in it without having to delete the stuff first.

2nd) How do you make it so that NumLock is automatically on after bootup.

---

### Post by nanotube on 2006-05-13
to delete a folder that has stuff in it, use command "rm -rf foldername" from a terminal

to play with numlock status on startup, install package "numlockx" with synaptic or apt-get.

it's nice to see easy questions once in a while. :)

---

### Post by JNowka on 2006-05-13
Thank you and I will try to keep em coming ;)

---

### Post by Sef on 2006-05-13
to get numlock to start up at boot.

```
NumLock
Enabling NumLock during startup

    *

      Install numlockx using Synaptic or apt-get
    *

      Edit /etc/X11/gdm/Init/Default
          o

            Find the line

            exit 0

          o

            Add the following code above that line

            if [ -x /usr/bin/numlockx ]; then
              /usr/bin/numlockx on
            fi


```

> [https://wiki.ubuntu.com/NumLock?highlight=%28numlock%29](https://wiki.ubuntu.com/NumLock?highlight=%28numlock%29)

---

