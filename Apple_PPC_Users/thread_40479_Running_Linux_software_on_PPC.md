---
title: "Running Linux software on PPC"
date: 2005-06-09
forum: Apple PPC Users
---

### Post by geeky on 2005-06-09
I tried to run a .bin file and i got the following message:
"cannot execute binary file"

i'm using ubuntu 5.04 on a Mac mini.
does anybody know why?

just in case you want to know what the file is, it's java J2SE 5.0 bundled with NetBeans 4.1

any help would be appreciated,
Thanks,

EDIT: I changed the permissions using "chmod 755 <filename>".. so this is not the problem.

---

### Post by slux on 2005-06-09
Is it a i386 binary? probably included in the name (or x86) and you should also be able to find out by doing 'file <filename>'.

I ask because there is no Java 1.5.0 yet for PPC Linux as far as I know. You might be able to compile it yourself (accept 200kbytes worth of license by Sun) or if you're happy with 1.4.2, IBM has that available. [More info](http://www-128.ibm.com/developerworks/eserver/library-html/l-pow-LoPJDKFinal.html).

---

### Post by geeky on 2005-06-09
yeah i guess it's because of the system structure.
i even tried to run skype and other programs but none seemed to work.
i guess running Linux on PPC is not a good idea for me. although i love using linux.
i guess i'm gonna sell my mac and get an intel/AMD-based laptop instead.

---

### Post by slux on 2005-06-10
It's the processor architecture. Non-free programs that are only available in binary form as compiled for x86 won't work just like the current Mac OS X won't work on a x86 computer.

Most of the apps you run on a GNU/Linux-based computer are fortunately [free](http://www.fsf.org/licensing/essays/free-sw.html), but Java and Skype aren't. (although as I said, Java can still be ran). I'll have to comment that you'll be better off running just free software while using GNU/Linux in the long run even though some non-free packages are a convenience initially. For example, nothing guarantees that Skype is going to be available in the future even for x86 Linux.

I'd at least keep track of the proprietary solutions you're currently forced to use and check for free alternatives occasionally.

---

