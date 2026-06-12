---
title: "dpkg problems, can't update or download"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by BrianAT on 2006-09-22
I started talking about this in my dual boot thread, but since all the boot issues are fixed (thank you everyone who helped for the help), I figured I would move this into a thread of it's own.
I have Ubuntu 6.06 LTS Drapper Drake installed on an AMD 64 system having an nVidia chipset, 1GB Ram, and I believe an nVidia 6600GT graphics card. (I am not sure where the sytem details are at in Linux off hand).
Here is the problem. I can't update. The icon in the corner says there are 8 updates avaialable. However, it complains that another package manager is open, even though none seem to be.
I used terminal to "sudo apt-get update" and it goes along fine until it hits that a "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem." So I try running "sudo dpkg --configure -a" and it as soon as it hits "Generating Locals en_AU.UTF-8...." it will either freeze or reboots. This is the same thing even under recovery mode. I saw something about a strace somewhere, and here are the results of "strace apt-get update >& /tmp/apt-get.txt":
```
execve("/usr/bin/apt-get", ["apt-get", "update"], [/* 31 vars */]) = 0
uname({sys="Linux", node="brian-desktop", ...}) = 0
brk(0)                                  = 0x522000
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2aaaaaac1000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2aaaaaac2000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=33886, ...}) = 0
mmap(NULL, 33886, PROT_READ, MAP_PRIVATE, 3, 0) = 0x2aaaaaac4000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libapt-pkg-libc6.3-6.so.3.11", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0000\374\1"..., 640) = 640
fstat(3, {st_mode=S_IFREG|0644, st_size=658912, ...}) = 0
mmap(NULL, 1706736, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x2aaaaabc2000
mprotect(0x2aaaaac5f000, 1063664, PROT_NONE) = 0
mmap(0x2aaaaad5f000, 16384, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x9d000) = 0x2aaaaad5f000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libstdc++.so.6", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0000\345\4"..., 640) = 640
fstat(3, {st_mode=S_IFREG|0644, st_size=959808, ...}) = 0
mmap(NULL, 2083288, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x2aaaaad63000
mprotect(0x2aaaaae45000, 1157592, PROT_NONE) = 0
mmap(0x2aaaaaf45000, 32768, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xe2000) = 0x2aaaaaf45000
mmap(0x2aaaaaf4d000, 76248, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x2aaaaaf4d000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libm.so.6", O_RDONLY)        = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0000>\0\0"..., 640) = 640
fstat(3, {st_mode=S_IFREG|0644, st_size=546000, ...}) = 0
mmap(NULL, 1591784, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x2aaaaaf60000
mprotect(0x2aaaaafe5000, 1047016, PROT_NONE) = 0
mmap(0x2aaaab0e4000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x84000) = 0x2aaaab0e4000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libgcc_s.so.1", O_RDONLY)    = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\300\37\0"..., 640) = 640
fstat(3, {st_mode=S_IFREG|0644, st_size=54256, ...}) = 0
mmap(NULL, 1101488, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x2aaaab0e5000
mprotect(0x2aaaab0f2000, 1048240, PROT_NONE) = 0
mmap(0x2aaaab1f1000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xc000) = 0x2aaaab1f1000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libc.so.6", O_RDONLY)        = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0@\305\1\0"..., 640) = 640
fstat(3, {st_mode=S_IFREG|0755, st_size=1267512, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2aaaab1f2000
mmap(NULL, 2327016, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x2aaaab1f3000
mprotect(0x2aaaab310000, 1159656, PROT_NONE) = 0
mmap(0x2aaaab410000, 94208, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x11d000) = 0x2aaaab410000
mmap(0x2aaaab427000, 16872, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x2aaaab427000
close(3)                                = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2aaaab42c000
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2aaaab42d000
arch_prctl(ARCH_SET_FS, 0x2aaaab42cae0) = 0
munmap(0x2aaaaaac4000, 33886)           = 0
brk(0)                                  = 0x522000
brk(0x543000)                           = 0x543000
open("/dev/null", O_WRONLY|O_CREAT|O_TRUNC, 0666) = 3
open("/usr/lib/locale/locale-archive", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/locale.alias", O_RDONLY) = 4
fstat(4, {st_mode=S_IFREG|0644, st_size=2586, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2aaaaaac4000
read(4, "# Locale name alias data base.\n#"..., 4096) = 2586
read(4, "", 4096)                       = 0
close(4)                                = 0
munmap(0x2aaaaaac4000, 4096)            = 0
open("/usr/lib/locale/en_US.UTF-8/LC_IDENTIFICATION", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_IDENTIFICATION", O_RDONLY) = 4
fstat(4, {st_mode=S_IFREG|0644, st_size=373, ...}) = 0
mmap(NULL, 373, PROT_READ, MAP_PRIVATE, 4, 0) = 0x2aaaaaac4000
close(4)                                = 0
open("/usr/lib/gconv/gconv-modules.cache", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/gconv/gconv-modules", O_RDONLY) = 4
fstat(4, {st_mode=S_IFREG|0644, st_size=45568, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2aaaaaac5000
read(4, "# GNU libc iconv configuration.\n"..., 4096) = 4096
read(4, "lias\tJS//\t\t\tJUS_I.B1.002//\nalias"..., 4096) = 4096
read(4, "ule\tINTERNAL\t\tISO-8859-3//\t\tISO8"..., 4096) = 4096
read(4, "lias\tISO-IR-199//\t\tISO-8859-14//"..., 4096) = 4096
read(4, "\t\tto\t\t\tmodule\t\tcost\nalias\tCSEBCD"..., 4096) = 4096
read(4, "ule\t\tcost\nalias\tCP284//\t\t\tIBM284"..., 4096) = 4096
read(4, "lias\tCP864//\t\t\tIBM864//\nalias\t86"..., 4096) = 4096
read(4, "module\tIBM937//\t\tINTERNAL\t\tIBM93"..., 4096) = 4096
read(4, "\tEUC-JP//\nalias\tUJIS//\t\t\tEUC-JP/"..., 4096) = 4096
read(4, "module\t\tcost\nalias\tISO-IR-143//\t"..., 4096) = 4096
read(4, "-BOX//\nmodule\tISO_10367-BOX//\t\tI"..., 4096) = 4096
brk(0x564000)                           = 0x564000
read(4, "module\tINTERNAL\t\tEUC-JISX0213//\t"..., 4096) = 512
read(4, "", 4096)                       = 0
close(4)                                = 0
munmap(0x2aaaaaac5000, 4096)            = 0
open("/usr/lib/locale/en_US.UTF-8/LC_MEASUREMENT", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_MEASUREMENT", O_RDONLY) = 4
fstat(4, {st_mode=S_IFREG|0644, st_size=23, ...}) = 0
mmap(NULL, 23, PROT_READ, MAP_PRIVATE, 4, 0) = 0x2aaaaaac5000
close(4)                                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_TELEPHONE", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_TELEPHONE", O_RDONLY) = 4
fstat(4, {st_mode=S_IFREG|0644, st_size=59, ...}) = 0
mmap(NULL, 59, PROT_READ, MAP_PRIVATE, 4, 0) = 0x2aaaaaac6000
close(4)                                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_ADDRESS", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_ADDRESS", O_RDONLY) = 4
fstat(4, {st_mode=S_IFREG|0644, st_size=155, ...}) = 0
mmap(NULL, 155, PROT_READ, MAP_PRIVATE, 4, 0) = 0x2aaaaaac7000
close(4)                                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_NAME", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_NAME", O_RDONLY) = 4
fstat(4, {st_mode=S_IFREG|0644, st_size=77, ...}) = 0
mmap(NULL, 77, PROT_READ, MAP_PRIVATE, 4, 0) = 0x2aaaaaac8000
close(4)                                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_PAPER", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_PAPER", O_RDONLY) = 4
fstat(4, {st_mode=S_IFREG|0644, st_size=34, ...}) = 0
mmap(NULL, 34, PROT_READ, MAP_PRIVATE, 4, 0) = 0x2aaaaaac9000
close(4)                                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_MESSAGES", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_MESSAGES", O_RDONLY) = 4
fstat(4, {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
close(4)                                = 0
open("/usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES", O_RDONLY) = 4
fstat(4, {st_mode=S_IFREG|0644, st_size=52, ...}) = 0
mmap(NULL, 52, PROT_READ, MAP_PRIVATE, 4, 0) = 0x2aaaaaaca000
close(4)                                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_MONETARY", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_MONETARY", O_RDONLY) = 4
fstat(4, {st_mode=S_IFREG|0644, st_size=286, ...}) = 0
mmap(NULL, 286, PROT_READ, MAP_PRIVATE, 4, 0) = 0x2aaaaaacb000
close(4)                                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_COLLATE", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_COLLATE", O_RDONLY) = 4
fstat(4, {st_mode=S_IFREG|0644, st_size=880086, ...}) = 0
mmap(NULL, 880086, PROT_READ, MAP_PRIVATE, 4, 0) = 0x2aaaaaacc000
close(4)                                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_TIME", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_TIME", O_RDONLY) = 4
fstat(4, {st_mode=S_IFREG|0644, st_size=2451, ...}) = 0
mmap(NULL, 2451, PROT_READ, MAP_PRIVATE, 4, 0) = 0x2aaaaaba3000
close(4)                                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_NUMERIC", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_NUMERIC", O_RDONLY) = 4
fstat(4, {st_mode=S_IFREG|0644, st_size=54, ...}) = 0
mmap(NULL, 54, PROT_READ, MAP_PRIVATE, 4, 0) = 0x2aaaaaba4000
close(4)                                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_CTYPE", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_CTYPE", O_RDONLY) = 4
fstat(4, {st_mode=S_IFREG|0644, st_size=208464, ...}) = 0
mmap(NULL, 208464, PROT_READ, MAP_PRIVATE, 4, 0) = 0x2aaaab42e000
close(4)                                = 0
stat("/var/lib/apt/.", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
stat("/etc/apt/apt.conf.d/", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/etc/apt/apt.conf.d/", O_RDONLY|O_NONBLOCK|O_DIRECTORY) = 4
fstat(4, {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
fcntl(4, F_SETFD, FD_CLOEXEC)           = 0
getdents64(4, /* 8 entries */, 4096)    = 264
stat("/etc/apt/apt.conf.d/05aptitude", {st_mode=S_IFREG|0644, st_size=80, ...}) = 0
stat("/etc/apt/apt.conf.d/10periodic", {st_mode=S_IFREG|0644, st_size=129, ...}) = 0
stat("/etc/apt/apt.conf.d/20archive", {st_mode=S_IFREG|0644, st_size=85, ...}) = 0
stat("/etc/apt/apt.conf.d/50unattended-upgrades", {st_mode=S_IFREG|0644, st_size=227, ...}) = 0
stat("/etc/apt/apt.conf.d/70debconf", {st_mode=S_IFREG|0644, st_size=182, ...}) = 0
stat("/etc/apt/apt.conf.d/99update-notifier", {st_mode=S_IFREG|0644, st_size=116, ...}) = 0
getdents64(4, /* 0 entries */, 4096)    = 0
close(4)                                = 0
open("/etc/apt/apt.conf.d/05aptitude", O_RDONLY) = 4
read(4, "aptitude::Keep-Unused-Pattern \"^"..., 8191) = 80
read(4, "", 8191)                       = 0
close(4)                                = 0
open("/etc/apt/apt.conf.d/10periodic", O_RDONLY) = 4
read(4, "APT::Periodic::Update-Package-Li"..., 8191) = 129
read(4, "", 8191)                       = 0
close(4)                                = 0
open("/etc/apt/apt.conf.d/20archive", O_RDONLY) = 4
read(4, "APT::Archives::MaxAge \"30\";\nAPT:"..., 8191) = 85
read(4, "", 8191)                       = 0
close(4)                                = 0
open("/etc/apt/apt.conf.d/50unattended-upgrades", O_RDONLY) = 4
read(4, "// allowed (origin, archive) pai"..., 8191) = 227
read(4, "", 8191)                       = 0
close(4)                                = 0
open("/etc/apt/apt.conf.d/70debconf", O_RDONLY) = 4
read(4, "// Pre-configure all packages wi"..., 8191) = 182
read(4, "", 8191)                       = 0
close(4)                                = 0
open("/etc/apt/apt.conf.d/99update-notifier", O_RDONLY) = 4
read(4, "DPkg::Post-Invoke {\"if [ -d /var"..., 8191) = 116
read(4, "", 8191)                       = 0
close(4)                                = 0
stat("/etc/apt/apt.conf", {st_mode=S_IFREG|0644, st_size=30, ...}) = 0
open("/etc/apt/apt.conf", O_RDONLY)     = 4
read(4, "Acquire::http::Proxy \"false\";\n", 8191) = 30
read(4, "", 8191)                       = 0
close(4)                                = 0
stat("/var/lib/dpkg/status", {st_mode=S_IFREG|0644, st_size=971145, ...}) = 0
stat("/usr/bin/dpkg", {st_mode=S_IFREG|0755, st_size=336216, ...}) = 0
stat("/etc/debian_version", {st_mode=S_IFREG|0644, st_size=17, ...}) = 0
ioctl(1, SNDCTL_TMR_TIMEBASE or TCGETS, 0x7fffffd45040) = -1 ENOTTY (Inappropriate ioctl for device)
rt_sigaction(SIGPIPE, {SIG_IGN}, {SIG_DFL}, 8) = 0
rt_sigaction(SIGWINCH, {0x406080, [WINCH], SA_RESTORER|SA_RESTART, 0x2aaaab2221b0}, {SIG_DFL}, 8) = 0
ioctl(1, TIOCGWINSZ, 0x7fffffd450b0)    = -1 ENOTTY (Inappropriate ioctl for device)
stat("/etc/apt/sources.list", {st_mode=S_IFREG|0644, st_size=1784, ...}) = 0
open("/etc/apt/sources.list", O_RDONLY) = 4
read(4, "\ndeb http://us.archive.ubuntu.co"..., 8191) = 1784
read(4, "", 8191)                       = 0
close(4)                                = 0
stat("/etc/apt/sources.list.d/", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/etc/apt/sources.list.d/", O_RDONLY|O_NONBLOCK|O_DIRECTORY) = 4
fstat(4, {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
fcntl(4, F_SETFD, FD_CLOEXEC)           = 0
getdents64(4, /* 2 entries */, 4096)    = 48
getdents64(4, /* 0 entries */, 4096)    = 0
close(4)                                = 0
open("/var/lib/apt/lists/lock", O_RDWR|O_CREAT|O_TRUNC, 0640) = -1 EACCES (Permission denied)
open("/usr/share/locale/en/LC_MESSAGES/libapt-pkg3.11.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en/LC_MESSAGES/libapt-pkg3.11.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en/LC_MESSAGES/apt.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en/LC_MESSAGES/apt.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
write(2, "E: ", 3E: )                      = 3
write(2, "Could not open lock file /var/li"..., 78Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)) = 78
write(2, "\n", 1
)                       = 1
write(2, "E: ", 3E: )                      = 3
write(2, "Unable to lock the list director"..., 33Unable to lock the list directory) = 33
write(2, "\n", 1
)                       = 1
close(3)                                = 0
exit_group(100)                         = ?
```

It looks like the problem relates to lock files, at least this time arround, although I'll leave it to you experts to know for sure.
I get the dpkg error if I try to start Synaptic as well. I tried apt-getting other stuff as well, and keep getting the dpkg error, which as I noted, if I follow, reboots or freezes the system.

Any ideas?

---

### Post by BrianAT on 2006-09-23
Wow, did I stump everyone?
Could I remove all lock files (something I guess I'll have to do from Windows since it won't let me do it in Ubuntu's UI) and will that fix it, or will that make matters worse? Since it seems to be a lock file issue. At least for the updates, as for the dpkg rebooting after the generating locals...

EDIT: Seems the dpkg problems are related to language files. I did get into Synaptic, after clicking ok to the dpkg error and clicking refresh, it loaded stuff up. I made two attempts to install stuff, but failed. The first froze during the language pack and the other I didn't see where it was when it rebooted the system. Since it freezes or reboots during generating locals when I run dpkg --configure -a, I suspect a language problem on the system.

---

### Post by BrianAT on 2006-09-23
Things get odder.
I managed to use Synaptic to dowload and install the updates after all. However dpkg is still giving problems with en_AU.UTF-8. Where is this and how do I get rid of it?
I tried 
```
dpkg-reconfigure --force locales
```

But it reboots after it displays en_AU.UTF-8... which is the first one. And for some reason I can't get into Lanuage Support as it says another software management tool is running. I'll disable the update manager in starteup programs and see if I can't get it to it there.

---

