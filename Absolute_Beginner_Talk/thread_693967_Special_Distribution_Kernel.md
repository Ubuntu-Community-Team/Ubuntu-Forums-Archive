---
title: "Special Distribution Kernel"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by vafanculo702 on 2008-02-11
Hello everybody. I just joined and decided to ask my first question already. I know I should google before asking dumb stuff, but I did, I did google. Nothing helpful.

Now, I know that the latest Linux Kernel Version is 2.6.24.2. I've heard about some special distribution kernels that are modified to suit the OS. Now, on my Ubuntu 7.10 x86 Intel processor running laptop, if I want to compile anew kernel do I have to compile a special one or a normal kernel when it comes out? So if I have to compile a normal kernel, will it be transformed in a special Distribution version?


Could somebody please tell me as I am really confused?

---

### Post by dstew on 2008-02-11
If you are a regular Ubuntu user, you never have to compile any kernels. You just install the distribution, and the kernel is included in it. Then, from time to time, you get kernel updates. The only reason to compile your own kernel is if you have some very special application in mind, or some tiny embedded system and you want a very tiny kernel image.

---

### Post by vafanculo702 on 2008-02-11
Well, yes. But that doesn't answer my question. Number one reason for which I asked is that I heard about this exploit and I don't want to be exposed to it so I want to update my kernel. I hear people using Ubuntu with  2.6.24.1 and  2.6.24.2 while I am still at 2.6.22-14-generic. And the update manager never prompted me to update to a new kernel.

---

### Post by dstew on 2008-02-11
> I heard about this exploit and I don't want to be exposed to itWhat exploit?

---

### Post by vafanculo702 on 2008-02-11
Well, there is this exploit where it takes advantage of a security hole via vmsplice. I have't tried it but I want ot be sure I am safe from it. Can you please answer my question?

---

### Post by dstew on 2008-02-11
That exploit at worst allows a local user to gain root access. If you are the only one using your computer, you don't have to worry about it. The kernel is not vulnerable to attacks over the net.

---

### Post by Joeb454 on 2008-02-11
I agree with **dstew** and would also like to add, that there will be a fix for it pretty soon I'd imagine, definitely quicker than the 12-18 months Microsoft takes to fix security holes worse than that ;)

---

### Post by vafanculo702 on 2008-02-12
Well, ok. How is it not vulnerable over the net. if someone uploads the file via ftp and then via ssh it compiles and runs it, it gains root access. Still, thank you. And about microsoft, it has many many more security problems. and it is also exposed to viruses like crazy. The good thing about Linux is that is Open Source and it is community based. So everybody can work on it and fix it fast. Microsoft...you have to wait until a new SP is out because they are the only ones working on it.

---

### Post by jordanmthomas on 2008-02-12
If you do want to compile your own kernel, here's the way to do it easily in Ubuntu:
[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

Obviously, version numbers have changed but the process is still the same.  

<geekalert>It can be pretty fun to compile your own kernel and know that it's suited just for your own computer.</geekalert>

The exploit worked well on my computer yesterday, but the Arch devs had the new kernel in the repositories within a few hours, so I'm safe now without having to recompile myself :)

---

### Post by Bachstelze on 2008-02-12
[QUOTE=jordanmthomas;4315314]<geekalert>It can be pretty fun to compile your own kernel and know that it's suited just for your own computer.</geekalert>/QUOTE]

Very educational, too.

By the way, I've posted [a temporary fix](http://ubuntuforums.org/showpost.php?p=4312743&postcount=15) that doesn't require recompiling the whole kernel.

---

### Post by dstew on 2008-02-12
> Well, ok. How is it not vulnerable over the netThe exploit is only available to users who have an account on your system. So, if you give a user the ability to upload files and execute them, then yes, you can be hacked over the net.

---

### Post by gupta_sumesh63 on 2008-02-12
I tried the temporary fix suggested by Hymntolife. However, the last step ie sudo modprobe novmsplice gives the following error:
FATAL: module novmsplice not found.
Am I doing anything wrong?
I use the 20.6.24.4 kernel
Any suggestions?
Thanks in advance.

---

### Post by Bachstelze on 2008-02-12
> **gupta_sumesh63 said:**
> I tried the temporary fix suggested by Hymntolife. However, the last step ie sudo modprobe novmsplice gives the following error:
FATAL: module novmsplice not found.
Am I doing anything wrong?
I use the 20.6.24.4 kernel
Any suggestions?
Thanks in advance.

You most likely missed a step. Tell us exactly what you did.

---

### Post by gupta_sumesh63 on 2008-02-13
Well!!These are the steps I followed:

sudo apt-get install build-essential linux-headers-`uname -r`(Were already the newest versions)
wget [http://www.linux.it/~md/software/novmsplice.tgz](http://www.linux.it/~md/software/novmsplice.tgz)
tar xzvf novmsplice.tgz
cd novmsplice
make
sudo cp novmsplice.ko /lib/modules/`uname -r`/kernel/security
sudo depmod -a
sudo modprobe novmsplice

Thats it :-
Any suggestions?
Thanks

---

### Post by Joeb454 on 2008-02-13
I got a kernel update today. I'm guessing this issue has been fixed :)

---

