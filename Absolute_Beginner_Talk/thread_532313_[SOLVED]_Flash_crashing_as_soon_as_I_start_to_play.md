---
title: "[SOLVED] Flash crashing as soon as I start to play a video"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by jsully1 on 2007-08-22
Hi all,

I tried to install the latest flash beta, but all that resulted in was crashing the moment I tried to play any sort of flash video.  I tried to revert to a previous version I had hanging around, but now that's crashing too.  Can someone recommend a way to move forward, or what version they have luck with?

It *only* crashes playing video, such as youtube. Sites that use flash work fine.

Sully

---

### Post by jsully1 on 2007-08-23
Anyone have any ideas?  It's doing it in Firefox and Opera.  Here's an strace of firefox:
```
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb1e9a000
read(66, "#\n# \"raw\" modem - phoneline\n#\n\np"..., 4096) = 1284
read(66, "", 4096)                      = 0
close(66)                               = 0
munmap(0xb1e9a000, 4096)                = 0
read(65, "", 4096)                      = 0
read(65, "", 4096)                      = 0
close(65)                               = 0
munmap(0xb1e9b000, 4096)                = 0
open("/dev/snd/controlC1", O_RDONLY)    = -1 ENOENT (No such file or directory)
open("/dev/aloadC1", O_RDONLY)          = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC2", O_RDONLY)    = -1 ENOENT (No such file or directory)
open("/dev/aloadC2", O_RDONLY)          = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC3", O_RDONLY)    = -1 ENOENT (No such file or directory)
open("/dev/aloadC3", O_RDONLY)          = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC4", O_RDONLY)    = -1 ENOENT (No such file or directory)
open("/dev/aloadC4", O_RDONLY)          = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC5", O_RDONLY)    = -1 ENOENT (No such file or directory)
open("/dev/aloadC5", O_RDONLY)          = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC6", O_RDONLY)    = -1 ENOENT (No such file or directory)
open("/dev/aloadC6", O_RDONLY)          = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC7", O_RDONLY)    = -1 ENOENT (No such file or directory)
open("/dev/aloadC7", O_RDONLY)          = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC8", O_RDONLY)    = -1 ENOENT (No such file or directory)
open("/dev/aloadC8", O_RDONLY)          = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC9", O_RDONLY)    = -1 ENOENT (No such file or directory)
open("/dev/aloadC9", O_RDONLY)          = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC10", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC10", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC11", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC11", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC12", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC12", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC13", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC13", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC14", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC14", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC15", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC15", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC16", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC16", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC17", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC17", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC18", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC18", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC19", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC19", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC20", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC20", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC21", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC21", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC22", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC22", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC23", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC23", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC24", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC24", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC25", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC25", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC26", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC26", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC27", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC27", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC28", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC28", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC29", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC29", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC30", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC30", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC31", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC31", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC0", O_RDONLY)    = 65
close(65)                               = 0
stat64("/usr/share/alsa/alsa.conf", {st_mode=S_IFREG|0644, st_size=7701, ...}) = 0
open("/dev/snd/controlC0", O_RDONLY)    = 65
close(65)                               = 0
open("/dev/snd/controlC0", O_RDWR)      = 65
ioctl(65, USBDEVFS_CONTROL, 0xbfd58874) = 0
ioctl(65, UI_DEV_CREATE, 0xbfd58850)    = 0
close(65)                               = 0
open("/dev/snd/controlC0", O_RDONLY)    = 65
close(65)                               = 0
stat64("/usr/share/alsa/alsa.conf", {st_mode=S_IFREG|0644, st_size=7701, ...}) = 0
open("/dev/snd/controlC0", O_RDONLY)    = 65
close(65)                               = 0
open("/dev/snd/controlC0", O_RDWR)      = 65
ioctl(65, USBDEVFS_CONTROL, 0xbfd583c4) = 0
ioctl(65, UI_DEV_CREATE, 0xbfd583a0)    = 0
close(65)                               = 0
open("/dev/snd/controlC0", O_RDONLY)    = 65
close(65)                               = 0
stat64("/usr/share/alsa/alsa.conf", {st_mode=S_IFREG|0644, st_size=7701, ...}) = 0
open("/dev/snd/controlC0", O_RDONLY)    = 65
close(65)                               = 0
open("/dev/snd/controlC0", O_RDWR)      = 65
ioctl(65, USBDEVFS_CONTROL, 0xbfd583c4) = 0
ioctl(65, UI_DEV_CREATE, 0xbfd583a0)    = 0
close(65)                               = 0
open("/dev/snd/controlC0", O_RDONLY)    = 65
close(65)                               = 0
stat64("/usr/share/alsa/alsa.conf", {st_mode=S_IFREG|0644, st_size=7701, ...}) = 0
open("/dev/snd/controlC0", O_RDONLY)    = 65
close(65)                               = 0
open("/dev/snd/controlC0", O_RDWR)      = 65
ioctl(65, USBDEVFS_CONTROL, 0xbfd583c4) = 0
ioctl(65, UI_DEV_CREATE, 0xbfd583a0)    = 0
close(65)                               = 0
socket(PF_FILE, SOCK_STREAM, 0)         = 65
fcntl64(65, F_GETFL)                    = 0x2 (flags O_RDWR)
fcntl64(65, F_SETFL, O_RDWR|O_NONBLOCK) = 0
connect(65, {sa_family=AF_FILE, path="/var/run/nscd/socket"}, 110) = -1 ENOENT (No such file or directory)
close(65)                               = 0
socket(PF_FILE, SOCK_STREAM, 0)         = 65
fcntl64(65, F_GETFL)                    = 0x2 (flags O_RDWR)
fcntl64(65, F_SETFL, O_RDWR|O_NONBLOCK) = 0
connect(65, {sa_family=AF_FILE, path="/var/run/nscd/socket"}, 110) = -1 ENOENT (No such file or directory)
close(65)                               = 0
open("/etc/group", O_RDONLY)            = 65
fcntl64(65, F_GETFD)                    = 0
fcntl64(65, F_SETFD, FD_CLOEXEC)        = 0
_llseek(65, 0, [0], SEEK_CUR)           = 0
fstat64(65, {st_mode=S_IFREG|0644, st_size=870, ...}) = 0
mmap2(NULL, 870, PROT_READ, MAP_SHARED, 65, 0) = 0xb1e9b000
_llseek(65, 870, [870], SEEK_SET)       = 0
munmap(0xb1e9b000, 870)                 = 0
close(65)                               = 0
open("/dev/snd/controlC0", O_RDONLY)    = 65
close(65)                               = 0
semget(5678293, 1, IPC_CREAT|0660)      = 0
semctl(0, 0, IPC_64|IPC_STAT, 0xbfd588a8) = 0
semctl(0, 0, IPC_64|IPC_SET, 0xbfd588a8) = -1 EPERM (Operation not permitted)
semop(0, 0xbfd5897e, 2

```
It always hangs right there on that last bit, and it doesn't recover.

Opera displays the first frame of the video as it starts to play, hangs, then sits there for about 30 seconds, then it comes back to life and the area where the video used to be disappears like I don't have flash installed.

Anyone have any ideas?

---

### Post by jsully1 on 2007-08-23
Hi all,

It turned out to be a sound issue.  I followed the incredibly helpful sound trouble guide here
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
I had to reinstall ALSA - that was it, now everything works!

---

