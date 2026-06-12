---
title: "[SOLVED] THEORY: Ubuntu slow=No SWAP"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by karlo on 2008-02-22
I think probably my laptop is unstable becuase, let's say I resized my swap file from 2GB to 1GB, and now it's not working.

It's ok to resize it right, since I only have a 512MB of ram, but Ubuntu only reads 495MB, still, a swap file only needs to be the twice as the memory, plus, before, my swap file didn't even reached 500MB even If I am running high memory consumption applications.

Now, it's 1GB, I am running every memory-eating applications, still it does not work. Here are the screenshots...

---

### Post by bumanie on 2008-02-22
If swap isn't being used, it means that your ram is dealing with the necessary processes. Increasing the swap size won't make any difference, unless ram is unable to cope, which in your case is not occurring (at least by that screenshot). I wonder whether your laptop is unstable due to the small amount of hard drive space you have left, especially the windows partition. I don't know whether this would effect the ubuntu partitions or not, but may be you need a larger or secondary hard drive.

---

### Post by PaulFr on 2008-02-22
Can you try running **top** command in a terminal (shell) and checking the Swap: line at the top ?

Also, you could check for lines containing the word **swap** in your /etc/fstab to verify that you are indeed mounting the swap partition :-)

---

### Post by karlo on 2008-02-22
> **PaulFr said:**
> Can you try running **top** command in a terminal (shell) and checking the Swap: line at the top ?

Also, you could check for lines containing the word **swap** in your /etc/fstab to verify that you are indeed mounting the swap partition :-)

Can you feel confirm this, If I did the right thing? check out the screenshots...switched swapoff>swapON

The only problem is, I have to do it everytime I run ubuntu. For sure there must be a way to make things [b]automatic[b].:lolflag:

Now, also, is there a way to improve swapping? I mean improve it's performance aside from making it larger?

---

### Post by hyper_ch on 2008-02-22
post the output of

```

cat /etc/fstab

```

---

### Post by mcduck on 2008-02-22
Since you resized the swap partition, it's not probably even mounting now.. Resizing and other editing of partitions will change their UUID's. (UUID is a specific piece of code that is used to identify different partitons)

To verify this, run 'free -m' and check if any swap is reported. Based on your screenshots "free" will probably report that you have 0 bytes of available swap..

Then use the 'blkid'-command to get the correct UUID for the partition, and edit the /etc/fstab-file to use this UUID. After that run "sudo mkswap /dev/sda6" and "sudo mount -a" to start using the partition.

When you have done this the swap partition should work automatically.

Anyway, increasing swapping will not increase your performance, quite the opposite. Reading and writing to a hard disk is roughly 1000 times slower than reading and writing to RAM. The less you have to use swap the better.

---

### Post by dougleduck on 2008-02-22
To say swapping wont increase performance is not true. Swap is much slower than actual memory but when you only have 512MB as RAM, as I also do, running out of memory completely is the issue. 

This is probably what causes the slow down you're experiencing.

---

### Post by SunnyRabbiera on 2008-02-22
This is why having swap is a good idea, even with newer computers its a lifesaver.

---

### Post by karlo on 2008-02-22
> **bumanie said:**
> If swap isn't being used, it means that your ram is dealing with the necessary processes. Increasing the swap size won't make any difference, unless ram is unable to cope, which in your case is not occurring (at least by that screenshot). I wonder whether your laptop is unstable due to the small amount of hard drive space you have left, especially the windows partition. I don't know whether this would effect the ubuntu partitions or not, but may be you need a larger or secondary hard drive.

Well, I resized my main parition from 2 GB, it's now 6-7 GB.

---

### Post by karlo on 2008-02-22
> **PaulFr said:**
> Can you try running **top** command in a terminal (shell) and checking the Swap: line at the top ?

Also, you could check for lines containing the word **swap** in your /etc/fstab to verify that you are indeed mounting the swap partition :-)

Wow, I saw that guide here [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by karlo on 2008-02-22
> **mcduck said:**
> Since you resized the swap partition, it's not probably even mounting now.. Resizing and other editing of partitions will change their UUID's. (UUID is a specific piece of code that is used to identify different partitons)

To verify this, run 'free -m' and check if any swap is reported. Based on your screenshots "free" will probably report that you have 0 bytes of available swap..

Then use the 'blkid'-command to get the correct UUID for the partition, and edit the /etc/fstab-file to use this UUID. After that run "sudo mkswap /dev/sda6" and "sudo mount -a" to start using the partition.

When you have done this the swap partition should work automatically.

Anyway, increasing swapping will not increase your performance, quite the opposite. Reading and writing to a hard disk is roughly 1000 times slower than reading and writing to RAM. The less you have to use swap the better.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq) ... same as that right? I read everything, now everything is OK, thanks by the way... I don't know if I should post this on launchpad specially with the laptop turned off automatically issue.

I hope in the future versions of Ubuntu, automatic mounting specially automatic mounting of the swap file if detected that it is changed or the UID changed, it should mount automatically, for user friendliness.

A really complete newbie will probably have difficulties in doing those steps that you suggested above, as well as the ubuntu documentation site suggested.

---

### Post by karlo on 2008-02-22
> **dougleduck said:**
> To say swapping wont increase performance is not true. Swap is much slower than actual memory but when you only have 512MB as RAM, as I also do, running out of memory completely is the issue. 

This is probably what causes the slow down you're experiencing.

I see, that's my theory too..

---

### Post by dougleduck on 2008-02-22
I'd imagine you did this with gparted.

It's probably been reported, I've changed my swap size several times (until I discovered swap files), and I've had to go through those steps everytime (at least since Gutsy).

You'd imagine it would be a relatively simple process to make gparted alter the fstab to include the correct UUID. So it's worth checking.

---

### Post by Vadi on 2008-02-22
This is a good theory... Ubuntu completely dies (read - abuses HD to max and locks up) when you run out of ram and have no swap.

---

### Post by karlo on 2008-02-22
> **dougleduck said:**
> I'd imagine you did this with gparted.

It's probably been reported, I've changed my swap size several times (until I discovered swap files), and I've had to go through those steps everytime (at least since Gutsy).

You'd imagine it would be a relatively simple process to make gparted alter the fstab to include the correct UUID. So it's worth checking.

Can you please explain the second paragraph?

---

