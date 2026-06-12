---
title: "yaboot problem"
date: 2007-01-09
forum: Apple PPC Users
---

### Post by ekimseekem on 2007-01-09
hey everyone,

i'm relatively new to ubuntu, however i've installed it before without too much problems, however this is different.

I've been successful starting up from the CD, however yaboot seems to not be installed correctly, from the last time i tried.  removing it and reinstalling it have been problematic as well.  this is the error that its generating in my terminal when trying a 'make install':

gcc -Os  -nostdinc -Wall -isystem `gcc -print-file-name=include` -fsigned-char -DVERSION=\"1.3.13\"      -DTEXTADDR=0x200000 -DDEBUG=0 -DMALLOCADDR=0x300000 -DMALLOCSIZE=0x100000 -DKERNELADDR=0x01400000 -I ./include -DCONFIG_COLOR_TEXT -DCONFIG_SET_COLORMAP -DUSE_MD5_PASSWORDS -DCONFIG_FS_XFS -DCONFIG_FS_REISERFS -D__ASSEMBLY__  -c -o second/crt0.o second/crt0.S
second/crt0.S:8:Parameter syntax error (parameter 1)
second/crt0.S:8:Invalid mnemonic 'h'
second/crt0.S:9:Parameter syntax error
second/crt0.S:9:Invalid mnemonic 'l'
second/crt0.S:10:Parameter syntax error (parameter 1)
second/crt0.S:10:Invalid mnemonic 'h'
second/crt0.S:11:Parameter syntax error
second/crt0.S:11:Invalid mnemonic 'l'
second/crt0.S:12:Parameter syntax error (parameter 1)
second/crt0.S:13:Parameter syntax error (parameter 1)
second/crt0.S:14:Parameter syntax error (parameter 1)
second/crt0.S:15:Parameter syntax error (parameter 1)
second/crt0.S:16:Parameter syntax error
second/crt0.S:25:Parameter syntax error (parameter 1)
second/crt0.S:27:Parameter syntax error (parameter 1)
second/crt0.S:28:Parameter syntax error (parameter 1)
second/crt0.S:28:Invalid mnemonic 'ha'
second/crt0.S:29:Parameter syntax error (parameter 1)
second/crt0.S:29:Invalid mnemonic 'l'
second/crt0.S:30:Parameter syntax error (parameter 1)
second/crt0.S:31:Parameter syntax error (parameter 2)
make: *** [second/crt0.o] Error 1

now i'm not an application programmer by any stretch of the imagination, i'm a network guy, so i haven't the faintest clue of how to solve the problem, i have installed hfsutils without a problem.  This also stops the install of ubuntu as it generates an error that yaboot hasn't been properly configured... maybe, but the install won't complete anyways :( 

i should also mention i'm running a version of Mac OS X server, 10.4.x, i have a G5 and 2 hard drives installed.  an 80GB storage drive and a 160 split 4 ways, 20GB allocated towards ubuntu's partitions

thanks in advance, post if ya need more info :???:

---

### Post by 3rdalbum on 2007-01-09
It looks like you're trying to compile Yaboot... why exactly?

Have you tried running:

```
sudo ybin
```?

---

### Post by ekimseekem on 2007-01-09
nothing...

i'm compiling as per the instructions in the install manual:

> 
The fastest way to install ybin and yaboot is to run `make install'.

This will install the man pages in /usr/local/man by default and
ybin/mkofboot in /usr/local/sbin.  yaboot and ofboot will be
installed in /usr/local/lib/yaboot/.

you may change the install paths by setting variables ROOT, PREFIX and
MANDIR to make.  ie make ROOT=/ PREFIX=/usr MANDIR=/share/man (this is only
intended for package maintainers.)

yaboot can be installed where you like but
/usr/local/lib/yaboot/yaboot is the first default location ybin will
look, followed by /usr/lib/yaboot/yaboot.

ybin needs hfsutils version 3.2.6 or later.

The man pages should be installed in /usr/local/man/man?/.  The *.8.gz
pages should be in /usr/local/man/man8/ and the *.5.gz page should be
in /usr/local/man/man5/.

If you need to remove ybin (say if your installing a debian package or
.rpm) you can do so by issuing the command `make deinstall'.


---

### Post by linear on 2007-01-10
OK, but why are you trying to compile rather than just use apt-get or Synaptic to re-install (yaboot _is_ in the repositories, after all).

---

### Post by ekimseekem on 2007-01-10
well i was trying to install it in Mac OS X the way it wanted me to... again mostly new to ubuntu. now i can't boot into ubuntu, other then the live CD, can i use that and install yaboot from there using the repositories... and what are the commands?

or could you use the apt-get commands from within Mac OS X...?

---

### Post by linear on 2007-01-10
Let's back up a bit. Looking at your first post, it sounds as though you never actually completed the Ubuntu install, is that correct? If that's the case, the easiest solution would be to wipe the Ubuntu partition and start the install over. Yaboot gets installed as part of the normal process.

If you're having trouble with install from the LiveCD, you may want to try the alternate install CD.

Although it's possible to fix an install gone bad, it may not be worth the time/trouble. (There is a "rescue" option on the alternate install CD - if I remember correctly, it's a menu option on the Dapper CD, and a boot option on the Edgy CD.)

---

