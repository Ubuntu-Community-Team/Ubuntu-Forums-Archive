---
title: "Scorched 3D won't run"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by olejorgen on 2007-05-23
```

fish: Job 1, “scorched3d” terminated by signal SIGSEGV (Address boundary error)

```
Any idea? (I'm running feisty, and using the scorched 3d package from the repos)

I tried to search, but nothing useful came up :(

---

### Post by Terl on 2007-05-23
Do you have your graphics drivers installed?

Here's another spot to check:  [Scorched3D Forums]("http://www.scorched3d.co.uk/phpBB2/viewforum.php?f=6&sid=899ac7d7ad07be0f20def03c26a13976")

---

### Post by olejorgen on 2007-05-24
Yeah, (should probably hava mentioned that) I got the nvidia (binary drivers) from the repos. Installed by using restricted driver manager.

Here is the last lines from strace:
```

munmap(0xb61c3000, 55951)               = 0
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=55951, ...}) = 0
mmap2(NULL, 55951, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb61c3000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libnss_nis.so.2", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\20\31\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=34352, ...}) = 0
mmap2(NULL, 37436, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb61a2000
mmap2(0xb61aa000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x7) = 0xb61aa000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libnss_files.so.2", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\0\31\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=38416, ...}) = 0
mmap2(NULL, 41624, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb6197000
mmap2(0xb61a0000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x8) = 0xb61a0000
close(3)                                = 0
brk(0x8387000)                          = 0x8387000
munmap(0xb61c3000, 55951)               = 0
open("/etc/passwd", O_RDONLY)           = 3
fcntl64(3, F_GETFD)                     = 0
fcntl64(3, F_SETFD, FD_CLOEXEC)         = 0
_llseek(3, 0, [0], SEEK_CUR)            = 0
fstat64(3, {st_mode=S_IFREG|0644, st_size=1462, ...}) = 0
mmap2(NULL, 1462, PROT_READ, MAP_SHARED, 3, 0) = 0xb7f20000
_llseek(3, 1462, [1462], SEEK_SET)      = 0
munmap(0xb7f20000, 1462)                = 0
close(3)                                = 0
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
+++ killed by SIGSEGV (core dumped) +++
Process 1262 detached

```

This is where it's crashing:
```
0xb7414ef0 in wcsncpy () from /lib/tls/i686/cmov/libc.so.6
```
(according to gdb)


BTW: What's the difference between glx. glx-new, glx-legacy?

---

