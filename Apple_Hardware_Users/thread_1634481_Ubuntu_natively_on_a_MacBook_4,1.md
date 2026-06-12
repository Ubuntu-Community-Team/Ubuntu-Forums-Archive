---
title: "Ubuntu natively on a MacBook 4,1"
date: 2010-11-30
forum: Apple Hardware Users
---

### Post by Chais_z3r0 on 2010-11-30
Since I'm increasingly pissed by OSX I thought I could install Linux once again.
First off: NO, I DON'T want to use Bootcamp. This computer is equipped with efi (although a messed up one) so I don't see why I should use an emulated BIOS.

So far I've found out that Apple took several steps to make that quest a bit harder.
- EFI comes with fat binaries (32bit and 64bit in a single file)
- They mixed EFI 1.10 and UEFI 2.0
- I'm quite sure there's more

So far I've tried running several distributions from bootable USB stick (dd works wonders) and stumbling around in the efi shell (rEFIt is installed of course), both without mentionable success.

I'm up to the challange, but I guess I'll need some support from more experienced users.
So thanks in advance.

Greetz

---

### Post by metatechbe on 2010-11-30
Hi Chais,

Have you tried the following procedure ?
[http://grub.enbug.org/TestingOnMacbook](http://grub.enbug.org/TestingOnMacbook)

If yes, which error do you encounter ?

metatech

---

### Post by Chais_z3r0 on 2010-12-01
Thanks for the quick answer. Nope didn't find that one while googling. I'll try and report.

---

### Post by Chais_z3r0 on 2010-12-02
I'm having trouble to compile the 64bit version of grub. Using Ubuntu 10.04 64bit and 'make' fails with:
```
Updating ./version.texi
restore=: && backupdir=".am$$" && \
    am__cwd=`pwd` && CDPATH="${ZSH_VERSION+.}:" && cd . && \
    rm -rf $backupdir && mkdir $backupdir && \
    if ( --version) >/dev/null 2>&1; then \
      for f in grub.info grub.info-[0-9] grub.info-[0-9][0-9] grub.i[0-9] grub.i[0-9][0-9]; do \
        if test -f $f; then mv $f $backupdir; restore=mv; else :; fi; \
      done; \
    else :; fi && \
    cd "$am__cwd"; \
    if    -I . \
     -o grub.info grub.texi; \
    then \
      rc=0; \
      CDPATH="${ZSH_VERSION+.}:" && cd .; \
    else \
      rc=$?; \
      CDPATH="${ZSH_VERSION+.}:" && cd . && \
      $restore $backupdir/* `echo "./grub.info" | sed 's|[^/]*$||'`; \
    fi; \
    rm -rf $backupdir; exit $rc
/bin/bash: Line 9: -I: Command not found.
make[2]: *** [grub.info] Error 127
make[2]: Leaving directory '/home/support/grub/docs'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory '/home/support/grub'
make: *** [all] Error 2
```
Probably it would work anyways, if the steps before aren't discarded. On the other hand documentation is always a good thing to have.

---

### Post by metatechbe on 2010-12-02
> **Chais_z3r0 said:**
> I'm having trouble to compile the 64bit version of grub. Using Ubuntu 10.04 64bit and 'make' fails with:
make[2]: Leaving directory '/home/support/grub/docs'

It's just the documentation part that fails I think.
I also have this error on my side.

metatech

---

### Post by Chais_z3r0 on 2010-12-03
Wooohooo. It's running. Linux Mint 10 natively on a MacBook. Thanks metatechbe. Take this, Steve :D

---

