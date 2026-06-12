---
title: "Fatal system error when booting windows"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by -WiM- on 2007-10-16
Every time I try to boot my windows, it gives me this error message, after I see the loading bar of windows for about a minute. 

STOP: c000021a {Fatal system error}
Systemprocess Session Manager Initialization is aborted unexpected with status:
0x000003a (0x00000000 0x00000000).
System is shut down.

I tried changing my menu.lst, but it didn't solve the problem. 
Is it possible that Ubuntu messed up my  Windows? 
I also tried to repair windows using the original cd, but it just won't repair...
Maybe I can format the windows partition and install it again, but I'm afraid that doing this will affect Grub. 

Any help please :( 
I study informatics and I really need windows for running some programs...

Thanks

---

### Post by Drakkor on 2007-10-16
Did you try the  ```
fix boot
``` and ```
fix mbr
``` commands ?
If so, you can just reinstall windows,and fix the grub later, it's not hard at all ! :)

---

### Post by Joeb454 on 2007-10-16
well if your wanting to install Windows after Ubuntu then you need to know that Windows will overwrite grub with the MBR. But you can then boot from the Live CD to reinstall grub, so it's not hard, but I just thought I ought to mention that so you don't get scared that Windows has erased 'Buntu

---

### Post by -WiM- on 2007-10-17
Have tried the' fix boot' and 'fix mbr' commands.
It made things worse, pc didnt accept any cd no more, 
I had to change stuff in my bios so that I could reinstall grub, 
cause it simply won't accept any windows cd ... 

So reinstalling windows isn't an option cause it doesn't accept the cd no more,
it is the official one, so that isn't the problem. 

Any other options I can try?

---

