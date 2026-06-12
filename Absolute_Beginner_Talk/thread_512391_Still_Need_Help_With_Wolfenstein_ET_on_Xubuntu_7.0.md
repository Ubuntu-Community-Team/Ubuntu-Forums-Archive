---
title: "Still Need Help With Wolfenstein: ET on Xubuntu 7.04"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by Wolfraptor1 on 2007-07-29
These are the two commands I put in...

sudo chmod +x et-linux-2.55.x86.run
sudo ./et-linux-2.55.x86.run

this is the first response from the Terminal I got:

"Verifying archive integrity... All good.
Uncompressing Enemy Territory 2.55"

I did the commands as specified and then it gave me this message:

"/home/*******/.setup11022: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
The setup program seems to have failed on x86/glibc-2.1

See [http://zerowing.idsoftware.com/linux/](http://zerowing.idsoftware.com/linux/) for troubleshooting

What am I doing wrong?

---

### Post by Stephen Howard on 2007-07-29
maybe install the gtk library:

```
sudo apt-get install libgtk1.2
```

---

