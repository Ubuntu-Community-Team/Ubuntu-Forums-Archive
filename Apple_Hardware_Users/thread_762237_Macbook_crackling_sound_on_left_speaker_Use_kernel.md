---
title: "Macbook crackling sound on left speaker? Use kernel 2.6.25!"
date: 2008-04-21
forum: Apple Hardware Users
---

### Post by volanin on 2008-04-21
I am using the newly realeased kernel 2.6.25 for some time now,
with a Gutsy install. And one thing I noted is that it
completely fixes the crackling sound problem some
people with intel macbooks have.

There were some workarounds for old kernels, but this one is
really making me very happy. If somebody tries this, please
post your experience here.

Thank you!
:)

---

### Post by volanin on 2008-04-21
Kubuntu?
How the hell it went there before the thread title?
Well, I think I might have mis-selected something.

Anyway, this is a kernel thing.
It applies to all ubuntu derivatives!

---

### Post by cyberdork33 on 2008-04-21
> **volanin said:**
> Kubuntu?
How the hell it went there before the thread title?
Well, I think I might have mis-selected something.

Anyway, this is a kernel thing.
It applies to all ubuntu derivatives!
Yea, it is a new "feature". Can you post the kernel config you are using and your Macbook Version? Some people were having trouble with the new kernel version.

---

### Post by Rog-Mahal on 2008-04-21
I second cyberdork. So far 2.6.24 has brought me nothing but trouble. I have a 3rd gen. Macbook, do suspend and resume still work with 2.6.25?

---

### Post by volanin on 2008-04-22
Suspend and hibernate works flawlessly for me in every kernel since 2.6.23.
Here goes the kernel 2.6.25 config for the Macbook 3rd gen. (see SIG)
I hope you have luck with it.

It supports every hardware except for iSight.
And it lacks support for iptables.
:)

---

### Post by volanin on 2008-04-22
I lied.
This new kernel breaks suspend.

---

### Post by cyberdork33 on 2008-04-22
> **volanin said:**
> I lied.
This new kernel breaks suspend.
Then your sig lies too ;)

---

### Post by mikeym on 2008-04-22
I'm using 0.2.65 having run into a sound issue on hardy that I traced back to a kernel issue. (Something to do with the soundcard reporting as DEAD) The sound only worked as far as playing the drums on login. 

Anyway there is a patch on [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/87652](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/87652) which I found had been included in 2.6.25. I compiled it using the method on the [PPC FAQ]("https://wiki.ubuntu.com/PowerPCFAQ#head-faa36f4765cc2dec98f5d029183807b8ccd9a954") with a few changes.

The only changes I made in the menuconfig were:

```

 Kernel Options>Timer Frequency>1000 Hz
 Kernel Options>Preemption Model>(X) Preemptible Kernel (Low-Latency Desktop)

```

But I found an error once I compiled and I had to include *CONFIG_INPUT_UINPUT=y* in the file *.config*. I did this between the steps *fakeroot make-kpkg clean* and *fakeroot make-kpkg --initrd --revision=ppc32 kernel_image kernel_headers modules_image*.

I hope this helps anyone with the same issue.

As a result I have working sound. Sound with games (such as openarena which runs superfast at 800x600). Suspend and wake-up. Also the problem I had found that most games crashed on exit seems to have been fixed. :)

I have also compiled [OpenAl Soft]("http://ubuntuforums.org/showthread.php?t=725727&highlight=openal+soft") which is working well.

---

### Post by cyberdork33 on 2008-04-22
> **mikeym said:**
> I'm using 0.2.65 having run into a sound issue on hardy that I traced back to a kernel issue. (Something to do with the soundcard reporting as DEAD) The sound only worked as far as playing the drums on login. 

Anyway there is a patch on [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/87652](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/87652) which I found had been included in 2.6.25. I compiled it using the method on the [PPC FAQ]("https://wiki.ubuntu.com/PowerPCFAQ#head-faa36f4765cc2dec98f5d029183807b8ccd9a954") with a few changes.

The only changes I made in the menuconfig were:

```

 Kernel Options>Timer Frequency>1000 Hz
 Kernel Options>Preemption Model>(X) Preemptible Kernel (Low-Latency Desktop)

```But I found an error once I compiled and I had to include *CONFIG_INPUT_UINPUT=y* in the file *.config*. I did this between the steps *fakeroot make-kpkg clean* and *fakeroot make-kpkg --initrd --revision=ppc32 kernel_image kernel_headers modules_image*.

I hope this helps anyone with the same issue.Please note he has a Macbook (i.e. Intel-based).

---

### Post by mikeym on 2008-04-22
Oh OK. Sorry yes mine is a PPC.

---

