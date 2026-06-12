---
title: "What is 686?"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by siguy on 2006-06-27
I've been running Ubuntu for a little under a month and I'm really digging it. I'm a little confused though. I've read about 386 and 686 kernels.

I've also heard that 686 is better for intel processors (I've got an old dell laptop with a Pentium M in it). How can I tell which version I'm running and if I'm running 386, is it worth switching to 686?

Would I have to reinstall all my applications or anything like that?

Thanks in advance, this forum really makes learning linux a lot easier.

edit: here's what my terminal said 2.6.15-25-386 #1 PREEMPT Wed Jun 14 11:25:49 UTC 2006 i686 GNU/Linux

I see 386 in one part and i686 at the end. Not sure what that means.

---

### Post by bruenig on 2006-06-27
fairly certain ubuntu doesn't have a 686 install cd, but if they did you would have to redo everything

---

### Post by siguy on 2006-06-27
oh, okay, I'm just confusing myself probably.

---

### Post by jinx099 on 2006-06-27
You should look here [http://ubuntuforums.org/showthread.php?t=85917](http://ubuntuforums.org/showthread.php?t=85917)

all you have to do is:
```
sudo apt-get install linux-686

```
Then reboot and select the 686 kernel from grub and you are done.  Note that you MAY break some apps, like vmware, but most if not all can be fixed pretty easily.  From my understanding, you could just boot into your default 386 kernel if something failed anyway so give it a try.

---

### Post by professor_chaos on 2006-06-27
also 386 doesn't support over 1GB of Ram, 686 does.

---

### Post by tommcd on 2006-06-27
You can check what kernel you are using by typing 'uname -r' in terminal.
If you are using the nvidia driver, make sure you instal the linux-restricted-modules for 686 as well. Get them from synaptic before you reboot into the new kernel.

---

