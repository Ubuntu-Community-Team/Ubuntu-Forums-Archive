---
title: "ktorrent crashes and acts all wierd"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by mangurt on 2007-10-31
Greeting all,
I started using ktorrent, and I really like the interface, but it's now acting weird.  A brief description;  if I click anywhere on the program, it's jumps around from a small screen to a large screen.  I can not click anywhere in the program to select stuff.  It crash, and I got a kde code error?  Any ideas?
Thanks
Ed

---

### Post by amingv on 2007-11-02
Hello

Maybe try opening it from the terminal and see the execution pattern, and where it ends. If possible, post that in formation.

Also reinstalling ktorrent may fix the problem, so you should try that too.

---

### Post by zip_000 on 2007-11-03
I've been getting the same error - it seemed to happen after I downloaded a .torrent file from the browser and clicked, "Open with Ktorrent" - previously to that I had always just downloaded from rss feeds.

Here is the result of running ktorrent from the terminal:

X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  149
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  149
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
Qt: Warning: X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  149
  Minor opcode:  3
  Resource id:  0x0
Qt: Warning: Failed to open device
Qt: Warning: X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  149
  Minor opcode:  3
  Resource id:  0x0
Qt: Warning: Failed to open device
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  149
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  149
  Minor opcode:  3
  Resource id:  0x0
Failed to open device


It opens, and it seems to be actually downloading the files that I have sent to it, but I can't click on anything on the ktorrent console. If I hover over a button, it looks like I can click it, but when I click - the whole console jumps (up or down) and nothing else happens.

Any help?

Thanks.

---

### Post by amingv on 2007-11-03
I had never interested myself in opening ktorrent from the console, following this thread I did. I noticed something weird; even when it "works fine" there's some errors, some look like  the one you got, but at the end I got another, a bit more interesting to my taste:

```
ubuntu@ubuntu:~$ ktorrent
Qt: Warning: X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Qt: Warning: Failed to open device
Qt: Warning: X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Qt: Warning: Failed to open device
Qt: Warning: QObject::disconnect: Unexpected null parameter
Qt: Warning: QObject::disconnect: Unexpected null parameter
ubuntu@ubuntu:~$ Qt: Warning: QWidget (unnamed): deleted while being painted
Qt: Warning: QPaintDevice: Cannot destroy paint device that is being painted
```

Notice the two lines after the second ubuntu@ubuntu:~$, maybe these aren't the exact source of the problem, but there's something going on down there. I get those when I close the program (because to the naked eye the program works fine), if you try to close the program would you get it as well? what was this torrent you were downloading? I want to try and mimic your error.

Just to make my interest more clear, this line makes reference to a runtime error related to a QWidget and QPaintDevice. This two buckos have a deal in drawing the GUI (created under [QT](http://en.wikipedia.org/wiki/Qt_(toolkit))). Since your problems are related to "the screen crashes, jumps, won't do anything when I click..." I fancy there may be a GUI error somewhere that we have not yet seen, triggered by some action; maybe with another function call.

---

