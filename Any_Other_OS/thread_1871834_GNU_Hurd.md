---
title: "GNU Hurd"
date: 2011-10-29
forum: Any Other OS
---

### Post by abedayyad on 2011-10-29
Hello Ubuntuers, 

I was wondering if any of you had any idea about using the kernel which was released by GNU, called Hurd. It, apparently, can be used with a Debian distribution and has been for some months now ... I was wondering if anybody had any ideas about this or, preferably, experiences. 

Was just curious ...

---

### Post by kaldor on 2011-10-29
It's comparable to where Linux was in 1995-1999. It's nowhere near a stable or usable system by today's standards. With Linux in existence, I think the effort to make a GNU/Hurd OS is useless. The only actual benefit is the idea of a microkernel instead of a monolithic kernel.

Debian GNU/Hurd is probably the largest OS using the Hurd kernel. That said, go ahead and try it, but don't expect much. If Free (as in Richard Stallman) matters a huge lot to you, I heavily recommend using a distribution which uses the *linux-libre* kernel. The largest distribution for this is Debian GNU/Linux as of version 6. Due to some disagreements however, Debian is not considered entirely Free. Trisquel is the FSF's currently endorsed distro.

Debian GNU/Hurd can be found [_here_]("http://people.debian.org/~sthibault/hurd-i386/installer/cdimage/").

Enjoy :)

---

### Post by shobon on 2011-10-29
> **kaldor said:**
> If Free (as in Richard Stallman) matters a huge lot to you, I heavily recommend using a distribution which uses the *linux-libre* kernel. The largest distribution for this is Debian GNU/Linux as of version 6. Due to some disagreements however, Debian is not considered entirely Free. Trisquel is the FSF's currently endorsed distro.

I'd also suggest Parabola GNU/Linux-libre. It's a "free as in freedom" version of Arch Linux. I use it on my laptop and it's great :)

But as for the Hurd, I ran it in a VM a couple months ago, but it ran too sluggishly for me to use. Last I checked there weren't even USB drivers available, so I'm a bit hesitant about installing it on real hardware.

---

### Post by trinux_bc on 2011-10-29
> **kaldor said:**
> It's comparable to where Linux was in 1995-1999. It's nowhere near a stable or usable system by today's standards. With Linux in existence, I think the effort to make a GNU/Hurd OS is useless. The only actual benefit is the idea of a microkernel instead of a monolithic kernel.

Debian GNU/Hurd is probably the largest OS using the Hurd kernel. That said, go ahead and try it, but don't expect much. If Free (as in Richard Stallman) matters a huge lot to you, I heavily recommend using a distribution which uses the *linux-libre* kernel. The largest distribution for this is Debian GNU/Linux as of version 6. Due to some disagreements however, Debian is not considered entirely Free. Trisquel is the FSF's currently endorsed distro.

Debian GNU/Hurd can be found [_here_]("http://people.debian.org/%7Esthibault/hurd-i386/installer/cdimage/").

Enjoy :)

+1

Hurd seems like a great way to re-live problems that were solved years ago in the Linux kernel.

trinux_bc

---

### Post by abedayyad on 2011-11-10
trinux_bc, kaldon and shobon: Thanks so much for all your help. I think I might try using a GNU Hurd on a desktop I'm planning to buy in the coming weeks ... I'll probably post here if anything remarkable happens.

---

