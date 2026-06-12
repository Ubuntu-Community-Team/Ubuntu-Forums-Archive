---
title: "X Error: BadDevice"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by MotorCityMadMan on 2006-10-16
I used kate to open a file from a shell.

What is this problem ?

How is this fixed ?


Password:
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Link points to "/tmp/ksocket-root"
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Link points to "/tmp/kde-root"
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0.0
DCOP aborting call from 'anonymous-5163' to 'kded'
kded: ERROR: Communication problem with kded, it probably crashed.
ScimInputContextPlugin()
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kio_uiserver: cannot connect to X server :0.0
DCOP aborting call from 'kate-5154' to 'kio_uiserver'
DCOP aborting call from 'anonymous-5172' to 'kio_uiserver'
ERROR: Communication problem with kio_uiserver, it probably crashed.
QObject::disconnect: Unexpected null parameter
~ScimInputContextPlugin()

---

### Post by jordanmthomas on 2006-10-16
a)  did you try to open with sudo?
If so, use kdesu instead...I believe that's the only way it will work with KDE programs.
i.e.
```
kdesu kate
```

b)  did it still open?  I get at least some of those errors every time I run a KDE program, but it still opens.

---

### Post by MotorCityMadMan on 2006-10-16
At first kate would not open. 

I did a sudo apt-get install build-essential and after that little deal kate opened using sudo and kdesu but x error: badDevice showed again.

It's just something one doesn't like to see is badDevice message.

---

### Post by jordanmthomas on 2006-10-16
build-essential should *not* have solved your problem.

I don't think the bad device is anything to worry about as I have always seen them and everything has always worked fine.

I use kate every day to take notes for class and every day I get this error:
```
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kdecore (KAction): WARNING: KActionCollection::KActionCollection( QObject *parent, const char *name, KInstance *instance )

```

Never had a problem, but a person at this site seems to have found a solution:
[http://www.linuxfordummies.org/index.php?PHPSESSID=94a045f7057cbba9b48514dbf396d626&topic=581;prev_next=next](http://www.linuxfordummies.org/index.php?PHPSESSID=94a045f7057cbba9b48514dbf396d626&topic=581;prev_next=next)
or here
[http://kubuntuforums.net/forums/index.php?topic=7964.0;topicseen](http://kubuntuforums.net/forums/index.php?topic=7964.0;topicseen)

Maybe these can help, but unless you want to possibly have some "fun" fixing your xorg.conf, I'd just deal with the errors.

Of course, I am one who likes to antagonize myself so I'm going to go and try the solutions out.

Good luck!

---

