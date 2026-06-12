---
title: "compling a custum kernel"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by fullback43 on 2007-12-27
i have been using this web site to help me with the kernel [http://www.errorforum.com/linux-unix-error/3203-how-customize-your-ubuntu-kernel.html]("http://www.errorforum.com/linux-unix-error/3203-how-customize-your-ubuntu-kernel.html")  but i get to the command fakeroot make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers and nothing happends or i get some kind of error 2. i dont know what i am doing wroung any idea?

---

### Post by nick_h on 2007-12-27
What error messages did you get?  Did all the other previous steps work?

You might like to read the [Master Kernel Thread](http://ubuntuforums.org/showthread.php?t=311158), but it suggests a very similar approach to the one in the link you are using.

---

### Post by fullback43 on 2007-12-27
make[2]: *** No rule to make target `arch/i386/kernel/asm-offsets.c', needed by `arch/i386/kernel/asm-offsets.s'.  Stop.
make[1]: *** [prepare0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-386'
make: *** [debian/stamp-kernel-conf] Error 2


and all of the other steps worked but the complie part

---

### Post by terminal on 2007-12-27
Follow this thread [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

Are you applying any custom patch to kernel ?

---

### Post by fullback43 on 2007-12-27
i dont think i am i dont even know how to do that yet

---

### Post by fullback43 on 2007-12-27
i now need help with choice my options b/c appently im not very good at it. i turned on smp support i have a core 2 duo but when it was done being compilied it just showed one processor and my sound does work. what info do i need to give that will help you guys help me?

---

### Post by dicecca112 on 2008-01-24
for the sound you need to enable intel HD audio, even if you don't use it.

---

