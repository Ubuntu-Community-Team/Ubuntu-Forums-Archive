---
title: "[SOLVED] start x apps from shell"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by klas_katt on 2008-02-13
I'd like to start an X app without this happening, it's ugly.

```
klas_katt@whatever:~$ kate &
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
```

(I can't search the forum for "X", word's too short. :confused: )

---

### Post by kellemes on 2008-02-13
Shouldn't kate get a filename?  I guess it would..
So.. try "kate /path/to/filename &"

---

### Post by Crooksey on 2008-02-13
I think he dosent want to view application feedback within the shell, not so much a program error, amrite?

---

### Post by Joeb454 on 2008-02-13
You're typing kate &

Try typing ```
(kate &)
``` instead :) That might be what you're looking for

---

### Post by Trail on 2008-02-13
This is actually an X confiuguration issue. (sudo) Kate the file /etc/X11/xorg.conf. Look for some lines like this:

```

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

```

And comment those lines out, by addind a "#" in front. Then reload X (logout-login). See if it works.

---

### Post by erginemr on 2008-02-13
As a backup to the above post by **Trail**:

[http://netmirror.org/mirror/linuxgazette.net/135/misc/lg/x_error_on_kubuntu.html](http://netmirror.org/mirror/linuxgazette.net/135/misc/lg/x_error_on_kubuntu.html)

---

### Post by klas_katt on 2008-02-15
(I was writing this post online only to find that I had been logged out when I tried to submit it => post gone. Note to self: write posts offline.)

Thank you Trail!
This started to bother me last year :)
I see now that my question could be more specific. It happens whenever I start ANY X application from any shell, kate was the example. I want the app feedback, just not the wacom opcodes. 

So, I sloppily erased (# comment is safer) without doing a backup (warning) the portion suggested by Trail in /etc/X11/xorg.conf and restarted X only to find that I had no X (suspence). I read /var/log/Xorg.0.log to find that
```
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
```
in the "ServerLayout" section was referring to the now missing part, so I erased those lines aswell. Thank you erginemr, I should have read your link more thoroughly. Restart of X and ta-da! It worked!

The wacom stanzas was in my xorg.conf by DEFAULT, so this problem would be very common. Do you think this nuisance could recieve or has bug status? Maybe I could have solved it by bying a wacom :)

This is so SOLVED! How can I mark it as such? How do I give thanks?

---

### Post by Trail on 2008-02-15
I think it's on by default so that the laptops' touch-mousepad thingy works by default. Safer bet for beginners.

---

### Post by erginemr on 2008-02-15
Great! We are glad that your problem has been resolved.

On a final note. In my xorg.conf file, I have all those chunks of wacom that you have posted at the start of the thread, but also have 
```

#	Inputdevice	"stylus"	"SendCoreEvents"
#	Inputdevice	"cursor"	"SendCoreEvents"
#	Inputdevice	"eraser"	"SendCoreEvents"

```
as commented out at the bottom in the "ServerLayout" section. So, I believe, leaving those chunks intact and commenting these out disables them. Just FYI...

**To close a thread **-> Select **"mark this thread as solved"** from the thread tools menu. 
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

**To thank someone **-> Click on the blue ribbon/badge on the bottom right part of the post(s), whose author(s), you believe, has helped you fix your problem.

Take Care,

Emrah

---

### Post by klas_katt on 2008-02-15
Done! Commenting the three lines would be the best solution. Trail seem unthankable (is that a word?) at the moment :)

---

### Post by erginemr on 2008-02-15
I will thank **Trail** on your behalf. Take care.

**"I am what I am because of who we all are."**

---

