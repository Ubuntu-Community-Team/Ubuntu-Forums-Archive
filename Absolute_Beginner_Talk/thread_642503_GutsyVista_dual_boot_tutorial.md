---
title: "Gutsy/Vista dual boot tutorial"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by Aqualung on 2007-12-16
Can someone point me to a comprehensive tutorial on how to dual boot Vista (Ultimate 64) witn Gutsy? I tried installing Gutsy just after it came out and it wreaked havoc on my Vista PC ("No operating system" error). All tutorials I've seen deal with Feisty, which is quite different.

The situation is like this: I have Vista 64 ultimate, and I made room on my boot drive for Gutsy (partitioned my boot disk). I'm thinking I may need some advanced Grub tweaking during Gutsy's installation. (The default Gutsy install settings screwed up my PC.)

Many thanks.

---

### Post by logos34 on 2007-12-16
> **Aqualung said:**
> Can someone point me to a comprehensive tutorial on how to dual boot Vista (Ultimate 64) witn Gutsy? I tried installing Gutsy just after it came out and it wreaked havoc on my Vista PC ("No operating system" error). All tutorials I've seen deal with Feisty, which is quite different.

The situation is like this: I have Vista 64 ultimate, and I made room on my boot drive for Gutsy (partitioned my boot disk). I'm thinking I may need some advanced Grub tweaking during Gutsy's installation. (The default Gutsy install settings screwed up my PC.)

Many thanks.

I haven't seen EXACTLY what you;re looking for, but there's this guide for vista ultimate (32-bit) and ubuntu 7.04.  Gutsy install is hardly any different, so it should work.  It's a popular guide, a lot of people use it.

---

### Post by Aqualung on 2007-12-17
> **logos34 said:**
> I haven't seen EXACTLY what you;re looking for, but there's this guide for vista ultimate (32-bit) and ubuntu 7.04.  Gutsy install is hardly any different, so it should work.  It's a popular guide, a lot of people use it.Thanks, I suppose you are referring to the same tutorial I used the first time (you forgot to give the link). I think the steps described in there differ essentially in some minute, but very important, details--details that happen to make quite a difference to me. You may want to repost the link though...

Cheers

---

### Post by Yellowdog428 on 2007-12-17
is this it?

[http://apcmag.com/dualboot](http://apcmag.com/dualboot)

Cheers

---

### Post by Sef on 2007-12-17
When shrinking Vista's partition, use Vista's partitioner.  Otherwise there is no difference in the install.   [Psychocat's tutorials]("http://www.psychocats.net/ubuntu/index.php")

---

### Post by logos34 on 2007-12-17
> **Aqualung said:**
> Thanks, I suppose you are referring to the same tutorial I used the first time (you forgot to give the link). I think the steps described in there differ essentially in some minute, but very important, details--details that happen to make quite a difference to me. You may want to repost the link though...

Cheers

oops!...sorry

[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

If you could be more specific about the details, I'd like to know out of curiosity and for future reference.

---

### Post by Aqualung on 2008-01-03
Here's a post I made elsewhere, I'll just reproduce it here w/o modifications, just to save some time:

"Hello, I am at my wit's end attempting to install Gutsy on my Vista computer. I like Gutsy, but so far all attempts to install it killed my Vista MBR, so it was imposible to boot into Vista (actually, it was impossible to boot into Ubuntu also!). It looks like I have no control over where Grub gets installed, and what it points to, so it ends up wreaking havoc on my PC. Presumably I have to configure some advanced options during Gutsy's installation, but so far I haven't come across anybody that knows how to do that. I have 4 IDE HDDs on a Promise card, and 3 SATA HDDs, all in a Xeon Woodcrest system (S2696). One of the SATA Raptors hosts my Vista, and the other SATA Raptor was supposed to be devoted exclusively to Gutsy. The main problem seems to be that I don't know how to tell Grub to (a) install itself on the Ubuntu HDD and (b) point to the Ubuntu HDD (i.e. to itself).

At some point I was toying with the idea of using EasyBDC; nevertheless, it looks like I still have to install Grub, and configure it properly--which I am, frankly, not very eager to do manually/from scratch. Also, I keep hearing through the grapevine that setting up a Vista/Gutsy dual boot in a multi-controller, mixed IDE-SATA environment, is a forlorn cause...

(Needless to say that I am complete Linux noobie, and don't really feel like learning Grub and the like.)"

---

