---
title: "do i copy using cp"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by arbogast on 2006-08-11
I want to copy the contents of a directory placed on my desktop (/home/arbogast/Desktop/Python-Guide-2.4.3/) to a specific directory (/usr/share/doc/python/html/)

i've been looking at the man page and different web-places.

I've tried cd'ing my way to the destination dir and typing: 'cp -rv home/arbogast/Desktop/Python-Docs-2.4.3/ Python-Docs-2.4.3'

and I've tried cd'ing my way to the source dir and typing 'cd -rv Python-Docs-2.4.3 //usr/share/doc/python/html/

I know this is very basic stuff and feel stupid asking but for me the man/info pages are hard to grasp.

How should i do it? And how should i understand the info-/manpages on cp in regard to what directory im currently in when i want to copy something?

---

### Post by taurus on 2006-08-11
```

cd ~/Desktop/Python-Guide-2.4.3
sudo cp -R * /usr/share/doc/python/html/

```
The reason you have to use "sudo" because you are planning to write to /usr which requires root administration...

---

### Post by arbogast on 2006-08-11
thanks a lot!

I knew about sudo, but im not sure i understand whay this'll work.

At least im having fun learning :)

---

