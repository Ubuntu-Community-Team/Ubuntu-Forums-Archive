---
title: "How to &quot;to natively boot EFI&quot; (very long booting time)"
date: 2008-05-27
forum: Apple Hardware Users
---

### Post by tomtom999 on 2008-05-27
[FONT="Arial"]Hi there,

when I boot up Ubuntu 8.04 on a MacBook (Pro 4.1, in my case), I get a white screen for about 30 seconds before Ubuntu loads.

I heard that to prevent this from happening, one must "natively boot EFI".

But what does that mean exactly?

Would I have to install rEfit before installing Ubuntu?

-> If yes, does that mean, it only makes sense to do this when I want a dual or triple boot? Or can one have rEfit for just 1 OS on the computer? (And does it make sense?)

-> If no, what else can I do to "natively boot EFI" (in order to prevent the long booting time)?

Thanks in advance for your complete answer(s)! (I'm still a n00b)
Tom[/FONT]

---

### Post by cyberdork33 on 2008-05-27
> **tomtom999 said:**
> [FONT=Arial]Hi there,

when I boot up Ubuntu 8.04 on a MacBook (Pro 4.1, in my case), I get a white screen for about 30 seconds before Ubuntu loads.

I heard that to prevent this from happening, one must "natively boot EFI".

But what does that mean exactly?

Would I have to install rEfit before installing Ubuntu?

-> If yes, does that mean, it only makes sense to do this when I want a dual or triple boot? Or can one have rEfit for just 1 OS on the computer? (And does it make sense?)

-> If no, what else can I do to "natively boot EFI" (in order to prevent the long booting time)?

Thanks in advance for your complete answer(s)! (I'm still a n00b)
Tom[/FONT]
Booting "native EFI" is a little different than what you mean, but, yes, the issue is that booting you do not have an EFI executable, so the machine searches for 30 seconds for a EFI executable before resorting to booting a "legacy" OS. Installing rEFIt would prevent this, but you have to use OSX to install (well really "bless" the execuatable).

---

### Post by tomtom999 on 2008-05-29
> **cyberdork33 said:**
> Booting "native EFI" is a little different than what you mean, but, yes, the issue is that booting you do not have an EFI executable, so the machine searches for 30 seconds for a EFI executable before resorting to booting a "legacy" OS. Installing rEFIt would prevent this, but you have to use OSX to install (well really "bless" the execuatable).

Thanks for your answer!

2 questions back:

1. So there is no way to tell the MacBook NOT to search for an EFI executable (like you would try to configure that in the BIOS in the case of a PC)?

2. If I want to solve the issue of the long booting time by installing rEFIt, would I definitely have to set up a DUAL boot (OS X + Ubuntu) or could I just use the OS X install CDs to get rEFIt and then somehow get rid of the installed OS X, so that I can use the entire hard drive for Linux?

---

### Post by cyberdork33 on 2008-05-29
> **tomtom999 said:**
> 1. So there is no way to tell the MacBook NOT to search for an EFI executable (like you would try to configure that in the BIOS in the case of a PC)? No. The issue is more the fact there are not really any PCs with EFI. Answering your first question though, not that anyone knows of. There may be a way to edit the EFI variables, but Apple certainly hasn't documented it, and nobody has found it.

> **tomtom999 said:**
> If I want to solve the issue of the long booting time by installing rEFIt, would I definitely have to set up a DUAL boot (OS X + Ubuntu) or could I just use the OS X install CDs to get rEFIt and then somehow get rid of the installed OS X, so that I can use the entire hard drive for Linux?
No you can definitely remove OSX from the equation, but if something happens to your rEFIt then you need OSX again to rebless the executable. You should be able to put refit and its supporting files in the EFI partition. [http://refit.sourceforge.net/doc/c1s1_install.html](http://refit.sourceforge.net/doc/c1s1_install.html)

EDIT: You might want to see if the bless command is available after booting the OSX DVD...

---

### Post by tomtom999 on 2008-05-29
Thanks a lot!

---

### Post by kosumi68 on 2008-06-01
It seems there are tools in "another operating system" that can write to the EFI NVRAM (see [http://msdn.microsoft.com/en-us/library/ms791521.aspx](http://msdn.microsoft.com/en-us/library/ms791521.aspx) for an overwiew). Perhaps it would be enough to be able to modify the boot-default timeout. The ubuntu efibootmgr package is supposed to do the same thing, but I have not been able to make it work.

---

### Post by cyberdork33 on 2008-06-01
> **kosumi68 said:**
> It seems there are tools in "another operating system" that can write to the EFI NVRAM (see [http://msdn.microsoft.com/en-us/library/ms791521.aspx](http://msdn.microsoft.com/en-us/library/ms791521.aspx) for an overwiew). Perhaps it would be enough to be able to modify the boot-default timeout. The ubuntu efibootmgr package is supposed to do the same thing, but I have not been able to make it work. Only Windows Server 2008 can work with EFI, and Apple has, of course, customized things a little, thus their implementation is nonstandard. If you sompile a kernel with all the EFI support in it, you can theoretically edit the EFI vars, but from my understanding it is  buggy, and doesn't seem to work for most people. EFI support in linux was designed for certain server machines not Apple machines.

---

