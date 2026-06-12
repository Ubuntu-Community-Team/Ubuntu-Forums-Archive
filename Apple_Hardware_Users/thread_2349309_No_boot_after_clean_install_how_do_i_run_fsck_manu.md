---
title: "No boot after clean install how do i run fsck manually?"
date: 2017-01-13
forum: Apple Hardware Users
---

### Post by alive1dub on 2017-01-13
After a clean install of studio 16.04.1 on my old macbook the system was running Perfectly bar WiFi problem. Sorted that but now the system will not reboot. Error is an unexpected inco sistency and asks that i run fsck manually without -a or -p options. Fsck exited with status code 4.  The root file system on /dev/sda2 requires manual fsck.
How do i do this?
The same ma book was running 14.04 with no problems.
Cheers. Al

---

### Post by howefield on 2017-01-13
Moved to the "*Apple Hardware Users*" forum.

---

### Post by alive1dub on 2017-01-13
Thanks, i will try to find that now &#128512;

---

### Post by Bashing-om on 2017-01-13
alive1dub; Hello;

From a liveDVD(USB) run terminal command(s):
so everything is unmounted,swap off if necessary, change example shown with partition sda1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
```

sudo e2fsck -C0 -p -f -v /dev/sda1

```
#if errors: -y auto answers yes for fixes needing response see: man e2fsck
```

sudo e2fsck -f -y -v /dev/sda1

```
fsck: [http://www.thegeekstuff.com/2012/08/fsck-command-examples/](http://www.thegeekstuff.com/2012/08/fsck-command-examples/)

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by alive1dub on 2017-01-13
Ok will give it a go &#128512;

---

### Post by alive1dub on 2017-01-14
Sorted, thank you &#128526;

---

### Post by Bashing-om on 2017-01-14
alive1dub; Hey great !

what did you do to get " Sorted, thank you " ? Was it a file system problem ?

With the advisement, and if this matter is concluded to your satisfaction ->
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]up up and away
[/INDENT][/INDENT]

---

### Post by alive1dub on 2017-01-14
Hi, I ran the terminal commands as indicated for /sda2 then shutdown and rebooted, now all is well and system running fine. &#128512;

---

