---
title: "I keep restarting X"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by zedmaster on 2007-02-05
OK here's my silly problem.  While I'm typing, I keep hitting the key combos to restart X, ie. ctrl, shift backspace, etc.  Luckily I'm running AMD64, and it restarts in a couple seconds, but I'm sick of having to log back in.  Can someone tell me how I can edit the key combos that restart X?  Ideally before I go clinically insan(er)?

Thanks!

PS: I managed to do it in the middle of this post!!!

PPS:  I'm runing Xubuntu if that makes and difference, which I doubt...

---

### Post by aktiwers on 2007-02-05
are you running Beryl? Normally its CTRL+ALT+Backspace..

---

### Post by aktiwers on 2007-02-05
If you use Beryl here is how to turn it off:
```
xmodmap -e &#8220;keycode 22 = BackSpace BackSpace Terminate_Server
```
Copy/Pastre that to terminal and hit Enter..[SIZE=1]
[/SIZE]

---

### Post by zedmaster on 2007-02-05
Yes I am running Beryl.  Sorry, should've added that to the post.  I'll try your code right away, thanks!

Matthew

---

### Post by zedmaster on 2007-02-05
No luck on that code... Thanks again though...   Here is the output 

```
xmodmap:  unknown command on line commandline:1
xmodmap:  unable to open file '22' for reading
xmodmap:  unable to open file '=' for reading
xmodmap:  unable to open file 'BackSpace' for reading
xmodmap:  unable to open file 'BackSpace' for reading
xmodmap:  unable to open file 'Terminate_Server' for reading
xmodmap:  6 errors encountered, aborting.

```

Any ideas?

---

### Post by aktiwers on 2007-02-05
Take a look here
[http://ubuntuforums.org/showthread.php?t=331770](http://ubuntuforums.org/showthread.php?t=331770)

Basicly I think you need to make text file named: something.sh

And then add this to it:
```
 #!/bin/bash
xmodmap -e "keycode 22 = BackSpace BackSpace Terminate_Server"
```

Then run it from Terminal (place in homefolder and run)
```
sudo sh something.sh
```

Does that work?

---

### Post by zedmaster on 2007-02-05
Well my friend, that did it!  The actual problem was I didn't noticed the " missing at the end!  Anyhow all fixed, and much appreciated.

Thanks

---

