---
title: "problems intalling kqemu"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by orangedangila on 2007-01-04
i got this problem when i was installiing kqemu..

/root/qemu-src/qemu-0.7.2/linux-user/syscall.c:216: error: syntax error before "gettid"
/root/qemu-src/qemu-0.7.2/linux-user/syscall.c:222: error: syntax error before "sys_uname"
/root/qemu-src/qemu-0.7.2/linux-user/syscall.c:223: error: syntax error before "sys_getcwd1"
/root/qemu-src/qemu-0.7.2/linux-user/syscall.c:224: error: syntax error before "sys_getdents"
/root/qemu-src/qemu-0.7.2/linux-user/syscall.c:224: warning: type defaults to `int' in declaration of `_syscall3'
/root/qemu-src/qemu-0.7.2/linux-user/syscall.c:224: warning: data definition has no type or storage class
/root/qemu-src/qemu-0.7.2/linux-user/syscall.c:225: error: syntax error before "sys_getdents64"
/root/qemu-src/qemu-0.7.2/linux-user/syscall.c:225: warning: type defaults to `int' in declaration of `_syscall3'
/root/qemu-src/qemu-0.7.2/linux-user/syscall.c:225: warning: data definition has no type or storage class
/root/qemu-src/qemu-0.7.2/linux-user/syscall.c:226: error: syntax error before "_llseek"
/root/qemu-src/qemu-0.7.2/linux-user/syscall.c:227: warning: type defaults to `int' in declaration of `_syscall5'
/root/qemu-src/qemu-0.7.2/linux-user/syscall.c:227: warning: data definition has no type or storage class
/root/qemu-src/qemu-0.7.2/linux-user/syscall.c:228: error: syntax error before "sys_statfs"
/root/qemu-src/qemu-0.7.2/linux-user/syscall.c:229: error: syntax error before "sys_fstatfs"
/root/qemu-src/qemu-0.7.2/linux-user/syscall.c:230: error: syntax error before "sys_rt_sigqueueinfo"
/root/qemu-src/qemu-0.7.2/linux-user/syscall.c:232: error: syntax error before "exit_group"
/root/qemu-src/qemu-0.7.2/linux-user/syscall.c:235: warning: return type defaults to `int'
/root/qemu-src/qemu-0.7.2/linux-user/syscall.c: In function `_syscall1':
/root/qemu-src/qemu-0.7.2/linux-user/syscall.c:235: error: storage class specified for parameter `personality'
/root/qemu-src/qemu-0.7.2/linux-user/syscall.c:236: error: storage class specified for parameter `flock'
/root/qemu-src/qemu-0.7.2/linux-user/syscall.c:237: error: storage class specified for parameter `setfsuid'
/root/qemu-src/qemu-0.7.2/linux-user/syscall.c:238: error: storage class specified for parameter `setfsgid'
/root/qemu-src/qemu-0.7.2/linux-user/syscall.c:239: error: storage class specified for parameter `setresuid'
/root/qemu-src/qemu-0.7.2/linux-user/syscall.c:240: error: storage class specified for parameter `getresuid'
/root/qemu-src/qemu-0.7.2/linux-user/syscall.c:241: error: storage class specified for parameter `setresgid'
/root/qemu-src/qemu-0.7.2/linux-user/syscall.c:242: error: storage class specified for parameter `getresgid'
/root/qemu-src/qemu-0.7.2/linux-user/syscall.c:243: error: storage class specified for parameter `setgroups'
/root/qemu-src/qemu-0.7.2/linux-user/syscall.c:246: error: storage class specified for parameter `get_errno'
/root/qemu-src/qemu-0.7.2/linux-user/syscall.c:246: error: syntax error before '{' token
/root/qemu-src/qemu-0.7.2/linux-user/syscall.c:259: error: storage class specified for parameter `target_original_brk'
/root/qemu-src/qemu-0.7.2/linux-user/syscall.c:262: error: syntax error before '{' token
/root/qemu-src/qemu-0.7.2/linux-user/syscall.c:273: error: syntax error before "if"
/root/qemu-src/qemu-0.7.2/linux-user/syscall.c:407: error: syntax error before "rfds_ptr"
/root/qemu-src/qemu-0.7.2/linux-user/syscall.c:450: error: parameter `target_cmsg' is initialized
/root/qemu-src/qemu-0.7.2/linux-user/syscall.c:450: error: `target_msgh' undeclared (first use in this function)
/root/qemu-src/qemu-0.7.2/linux-user/syscall.c:450: error: (Each undeclared identifier is reported only once
/root/qemu-src/qemu-0.7.2/linux-user/syscall.c:450: error: for each function it appears in.)
/root/qemu-src/qemu-0.7.2/linux-user/syscall.c:450: confused by earlier errors, bailing out
make[1]: *** [syscall.o] Error 1
make[1]: Leaving directory `/root/qemu-src/qemu-0.7.2/i386-user'
make: *** [all] Error 1

PROBLEM IN MAKE: 2


any ideas how to resolve this problem???

---

### Post by tageiru on 2007-01-04
Why are you compiling an ancient version of qemu? Which version of gcc are you using. As far as I know qemu does not yet support gcc > 4.0.

---

### Post by orangedangila on 2007-01-04
> **tageiru said:**
> Why are you compiling an ancient version of qemu? Which version of gcc are you using. As far as I know qemu does not yet support gcc > 4.0.

btw.. what is gcc?? so if i cannot do that.. how can i make qemu runs faster??

---

