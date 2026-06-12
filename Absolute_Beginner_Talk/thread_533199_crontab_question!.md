---
title: "crontab question!"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by cAllison on 2007-08-23
Hi, quick question!

Crontab sorta confuses me. but heres what I need done.
I have a file server setup for my office using samba. I have about 8 departments running files off of it. Just recently I added the recycle vfs object to all the shares (for virtual recycle bins). I also made a script to empty the recycle bins. Now I just need to script to execute every week, on Sunday @ midnight.

The script is in a path folder (/bin)

So to get this to run as specified I would do:
```

# Use the hash sign to prefix a comment
# +---------------- minute (0 - 59)
# |  +------------- hour (0 - 23)
# |  |  +---------- day of month (1 - 31)
# |  |  |  +------- month (1 - 12)
# |  |  |  |  +---- day of week (0 - 7) (Sunday=0 or 7)
# |  |  |  |  |
# *  *  *  *  *  command to be executed
 59  23 *  *  7  scriptname


```

correct?

Now my last question, would I use sudo crontab to set it up as root so it can run even if I'm not logged in?

---

### Post by hyper_ch on 2007-08-23
you don't have to be logged in for running it... just the computer must be running :)

That looks fine to me :)

However I'd use:

```

0 0 * * 7 /bin/scriptname

```

---

