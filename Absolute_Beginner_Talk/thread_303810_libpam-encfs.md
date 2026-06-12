---
title: "libpam-encfs"
date: 2006-11-20
forum: Absolute Beginner Talk
---

### Post by richardward101 on 2006-11-20
Anyone know of any good tutorials on this? its supposed to mount your home directory as an enfs file system when you log in, but its documentation is not very good. Got encfs working fine, its just libpam-encfs; I don't even know where to begin.
Thanks

---

### Post by richardward101 on 2006-11-26
bump

---

### Post by richardward101 on 2006-12-01
Anyone? I found a tutorial [here]("http://choffee.co.uk/ramble/2006/06/02/paranoia-at-home/")
but when I follow it I get the following when I log in:

```
richard@richard-desktop:~$,  su test
Password: 
encfs: invalid option -- t
encfs: invalid option -- e
encfs: invalid option -- t
encfs: invalid option -- t
encfs: invalid option -- e
encfs: invalid option -- t
encfs: invalid option -- 2
00:09:47 (main.cpp:636) Root directory: /enchome/test/
00:09:47 (main.cpp:637) Fuse arguments: (daemon) (UP) (timeout 1) (keyCheck) (useStdin) encfs /home/test -s -o use_ino -o default_permissions -o allow_root,allow_other,allow_root,nonempty 
00:09:47 (Interface.cpp:165) checking if ssl/aes(2:1:1) implements ssl/blowfish(2:1:1)
00:09:47 (Interface.cpp:165) checking if ssl/blowfish(2:1:1) implements ssl/blowfish(2:1:1)
00:09:47 (SSL_Cipher.cpp:322) allocated cipher ssl/blowfish, keySize 20, ivlength 8
00:09:47 (FileUtils.cpp:1296) useStdin: 1
00:09:47 (FileUtils.cpp:1307) configuration key size = 32
00:09:47 (FileUtils.cpp:1308) cipher key size = 32
00:09:47 (Interface.cpp:165) checking if nameio/block(3:0:1) implements nameio/block(3:0:1)
Note: requested single-threaded mode, but an idle
timeout was specified.  The filesystem will operate
single-threaded, but threads will still be used to
implement idle checking.
fuse: 'allow_other' and 'allow_root' options are mutually exclusive
fuse failed.  Common problems:
 - fuse kernel module not installed (modprobe fuse)
 - invalid options -- see usage message
test@richard-desktop:~$ 
```

fuse is definitely modprobed, and I can't figure out how to change the mount options it uses.

---

