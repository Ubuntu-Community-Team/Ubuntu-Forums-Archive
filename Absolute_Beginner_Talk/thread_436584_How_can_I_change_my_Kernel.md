---
title: "How can I change my Kernel?"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by ZeroWing on 2007-05-08
I want to swap my kernel on my laptop because, well, ubuntu seems slow on it, but I know that that computer has descent hardware on it.

 I've heard that updating your generic kernel to a processor-specific kernel will get you a speed boost varying from small to extreme, so I'd like to give it a shot.

 Lappy specs:

CPU: AMD Athlon XP 3200+
RAM: 1.0 GB; high latency :( 
Video card: 128MB ATI card. Forgot exact name

 So. How can I swap kernels?

---

### Post by Bachstelze on 2007-05-08
Which kernel do you currently have ?

```
uname -a
```

---

### Post by ZeroWing on 2007-05-08
> **HymnToLife said:**
> Which kernel do you currently have ?

```
uname -a
```

 I get this:

 ```
 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux
```

 By the way, what's up with GNU and Linux?

---

### Post by Bachstelze on 2007-05-08
You won't be able to get a better kernel if you stick with the official builds. If you really do want a faster system, you could try to build yourself a kernel from source.

To learn more about GNU and Linux, check out Wikipedia ;)

---

### Post by ZeroWing on 2007-05-08
> **HymnToLife said:**
> You won't be able to get a better kernel if you stick with the official builds. If you really do want a faster system, you could try to build yourself a kernel from source.

 That sounds hard...

 How difficult would it be to make a kernel...?

---

### Post by Bachstelze on 2007-05-08
Not difficult at all, I personnaly do it almost every week. Search on the forums, quite a few people have shared their experiences about this.

---

### Post by meman63 on 2007-05-08
There are some good tutorials for compiling your own kernel .It just takes time and patience.

This is what I've found here: [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

Try it,you might like it.

As always,
           Regards,
                     Red

---

### Post by ZeroWing on 2007-05-08
> **meman63 said:**
> There are some good tutorials for compiling your own kernel .It just takes time and patience.

This is what I've found here: [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

Try it,you might like it.

As always,
           Regards,
                     Red

 I tried. Just to hard to follow for me. I'm still a newb when it comes to linux.

---

### Post by Bachstelze on 2007-05-08
Then you'll have to stick with the default Ubuntu one. Or if you give me SSH access to your machine, I guess I could do it from here :)

---

