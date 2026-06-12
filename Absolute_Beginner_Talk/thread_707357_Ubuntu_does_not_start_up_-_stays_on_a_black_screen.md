---
title: "Ubuntu does not start up - stays on a black screen"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by flamingsole on 2008-02-25
Hello,

So I run Gutsy and XP in a dual boot system. It has two gigs of memory, and a 64-bit AMD. Everything has been working fine for the most part, since upgrading.

The other day, when I went to turn on the system, after the Ubuntu startup screen where the bar loads, the system went black and the monitor turned itself off. The computer was still running, but nothing happened. 

For comparison, when I tried to boot into Windows, it seemed like it was going to boot normally, even getting all the way to the desktop a few times. Before it finished loading, though, it would simply restart the system.

If I choose recovery in the boot selector, I can get into the command prompt for Ubuntu. Are there terminal commands that would be wise for me to try, to figure out what is happening? Any other thoughts on what the issue might be?

Thanks for any help,
Jon

---

### Post by OffAxis on 2008-02-25
Have you messed with your hardware lately?

Like installing a new video card?

you can check out your syslog

```
less /var/log/syslog
```

for errors.

---

### Post by flamingsole on 2008-02-25
I went to try this out, but now I can't get into the recovery. It hangs on "Starting up..."

I tried booting in regular mode, and the following error displayed:
```

23.338861] Kernel panic - not syncing: Attempted to kill the idle task!

```

To answer your question, though, I haven't made any hardware changes. Thanks for the command. If I can get to the prompt, I will try it. Any thoughts on the error?

Thanks,
Jon

---

### Post by OffAxis on 2008-02-28
since both OSs are tanking it's probably a hardware problem.
A not syncing kernel panic makes me think it's a memory problem.

On the liveCD there's an option for memtest86. Run that.
This'll put your RAM through a series of read/write tests (12 in total, if I recall). It'll keep cycling them continuously, so just kill it if it comes up with errors or you're convinced that the RAM is good.

On to the hard disk.

Reboot to the LiveCD and run
```
sudo e2fsck /path/to/harddrive
```

This'll test your ext2 or ext3 formatted hard drive for errors.

If you've got another filesystem type or aren't sure about the path I think you can just run
```

sudo fsck
```

(I've never used fsck, so I'm not entirely certain about its options. You can check out the man page for more)
```
man fsck
```

---

### Post by flamingsole on 2008-02-28
Thanks so much for the suggestions. I ran memtest, and hit reboot when I thought it was recycling itself. The weird thing is that, apparently, the system is fixed now. Ubuntu boots, XP boots, and everything acts as though it was normal. Am I in the clear, or does this sound like a temporary lull in the trouble?

If I am in the clear, thanks again for the help.

Jon

---

