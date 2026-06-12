---
title: "the proper kernel for my cpu"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by karellen on 2006-12-14
I have a four years old P4 and I want to install the proper kernel version for it ( I think it's i586 or i686), not the actual i386 generic version. I believe the speed improvement will be substanstial. I searched with synaptic but there were old kernel images...What can I do? I don't wanna screw my system anyway and I don't wanna compile a kernel from scratch.

---

### Post by macogw on 2006-12-14
Install the i386, then recompile for the kernel you want.  [http://doc.gwos.org/index.php/Kernel_Compilation_Dapper](http://doc.gwos.org/index.php/Kernel_Compilation_Dapper) Follow those directions.  Yeah, it says Dapper.  If you're using Edgy, it should be similar.  I haven't bothered recompiling Edgy for 686 since it has SMP by default, so I can't say for sure that it's identical, but the general idea will be the same (the command line stuff will 99% sure be the same...the interface later may look a tad different).

---

### Post by karellen on 2006-12-14
thanks, I'll try that and see what happens :)

---

### Post by mcduck on 2006-12-14
I wouldn't bother compiling the kernel myself unless the latest kernel would bring support for some of my hardware that wasn't supported in Ubuntu's kernels.

You'll just make things harder for yourself for no reason.

Just run 'sudo apt-get install linux-686', or if your CPU supports HyperThreading 'sudo apt-get install linux-686-smp'. Then reboot and now you are running kernel optimized for your CPU :)

---

### Post by thornomad on 2006-12-14
Along these lines, are there any guides for processors regarding optimizing the kernal?  For older models, and well as for new chips (e.g., Intel's Core 2 Duo) ?

I had no idea there was an **optimized** kernal!  Sheesh.

The things I am learning.

---

### Post by karellen on 2006-12-14
:d...I'd rather take the simple way with sudo...;)

---

