---
title: "Using card media as RAM"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by kevindubrow on 2007-08-09
Hey, this may be a really silly question (and sorry if it is) but is it possible to use card media as RAM? I figure it may be a better substitute than using space on a HDD because that option is much slower than RAM itself. 

I am asking this mainly because I just got a laptop from eBay which I love in exception to its low RAM. It has a card reader built in, so I guess its worth asking. Thanks.

---

### Post by LaRoza on 2007-08-09
No, that would be impossible. (And slower than a harddrive)

---

### Post by xxdeusxx on 2007-08-09
card readers are in general even slower than hard disks...
you could possibly use a card for swapping purposes, but RAM is different...

i would recommend buying more RAM...

---

### Post by Inxsible on 2007-08-09
you can probably use that card as a swap memory, but you would have to always make certain the card is inserted before booting to Ubuntu or all bets are off !!

---

### Post by kevindubrow on 2007-08-09
Oh ok, I honestly believed card media was faster than a normal hard drive. Thanks for the answers and thanks for your time!

---

### Post by igknighted on 2007-08-09
As swap?  Sure.  The above poster is right... for the most part... in that it should be inserted before boot, but if you were to insert it later the swapon command could mount it as swap.  You could even write a script to activate it (perhaps a cron job that runs every so often and looks for the card, and if it finds it then it activates it?)...  lots of possibilities.

The only thing that you need to be aware of is that flash memory is limited in the number of writes before it dies.  A swap drive that gets accessed a lot could kill the memory fairly quickly.  If you have a spare card lying around it might be worth at least to try it out and see if it lasts, I really couldn't even begin to guess at how long that would be.

---

### Post by kozy6871 on 2007-08-09
Because flash memory (what you would find on an SD card) is so different from system RAM, it won't work like it.  It is slow - has to go through some sort of interface to get to the CPU(USB, or in your case, a card reader(my guess is PCI).  Where system RAM has a direct pipe to the CPU, and since it doesn't have to stay after you turn the computer off, it can be speed rated for access through that pipe(front side bus).

I really wish this were possible, too, because my MP3 player has more memeory than my desktop PC.

---

### Post by Hospadar on 2007-08-09
Well here's the deal, if you got some internal flash memory connected to your mobo by sata or a PCIe, it would be a lot better for a swap partition than a regular hard drive (the swap is where stuff goes when memory overflows).

But talking about a card hooked up to let's say a usb port is going to be much slower because while the memory itself has great random access speeds compared to a hard drive since it doesn't need to seek to tracks, the usb connection can't possibly compete with the 3Gb/s serial speed of a sata connection on a good hard drive.

That said, you can get internal (sata and pci) card readers that would allow you to use your card as a fast swap partition alternative to the swap on a hard drive.  But being as you are probably trying to save money by not buying things, that's probably a moot point

---

### Post by kevindubrow on 2007-08-09
Well I will have an internal card reader and I know Kingston makes very inexpensive cards (such as a 1gig for $10- $14) so if I can use the card as a swap, it may be worth a try.

---
By the way, here is a link about the card:
[http://news.com.com/8301-10784_3-9717155-7.html?tag=bl](http://news.com.com/8301-10784_3-9717155-7.html?tag=bl)

---

### Post by Steveway on 2007-08-09
The biggest problem is, as above mentioned, that those cards have a limited life-time.
If you use them as a swap-addition they will die very fast.
Very fast!

---

### Post by kevindubrow on 2007-08-09
Haha, true. I guess I should just stop trying to find a way around expensive RAM upgrades. I do wish there was a standard RAM type though...I would just take a gig out of my older computer.

---

