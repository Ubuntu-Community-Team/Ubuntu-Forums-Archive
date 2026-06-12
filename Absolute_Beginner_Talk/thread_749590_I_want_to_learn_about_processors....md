---
title: "I want to learn about processors..."
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by Pogeymanz on 2008-04-08
I just want to know how to compare processors! For example, I want to be able to tell which processor would be the fastest out of a group, because I know that clock speed doesn't mean everything.

So, what do I look for in a processor? What does the cache value mean?

Also, I've heard some stuff about processors that I'd like verified:

1. I heard that Pentium 4's are all pretty bad (even for their times). I also heard that when the P4 FIRST came out they were SLOWER than the latest P3's despite having a much higher clock speed. Why would this be?

2. I also heard that in the past (I don't know about now) AMD's were only worth even having because they were easy to overclock. Was this said by an Intel fanboy?

It's entirely possible that these are totally false, but I would like to be able to figure out what is bogus on my own!

---

### Post by Rocket2DMn on 2008-04-08
It used to be we could judge processors primarily on their clock speed, but because of how advanced they are these days, there is more to it.  The biggest thing is how much can the proessor do in a single clock cycle?  This is because hardware can multitask with different pieces of the hardware performing functions during a clock cycle.  In a pipelined CPU (which is what we use) multiple instructions can be in the processor at the same time and may take different amounts of time to complete, like maybe 3 clocks while others take 5 clocks.  The pipeline in different processors can vary as well - an instruction that takes 3 clocks in one processor may take 4 in another, but the second processor may have a higher clock speed, so it can perform comparably to the first.  Cache memory is important because the processor can hold more info without having to go to RAM for data (which can take a couple of clock cycles), whereas L1 cache can be accessed in 1 clock cycle, and so on and so forth.  Also, multiple cores means you can multitask with different processes or threads on different CPUs on the same chip.
To get a good comparison however, you really need to see benchmarks which show how a processor performs compared to other similar processors when performing the same task.  Sometimes processors perform better than others in some tasks, but worse in others.  This is still the best way to really see how a processor performs.  All the info about a processor's cache sizes, clock speeds, etc. are useful, but benchmarks actually compare performance.

---

### Post by Bölvaður on 2008-04-08
If you are buying computer and have no idea where to start it is good for you to look at this [webpage]("http://www.cpubenchmark.net/cpu_list.php") and then when you've narrowed down the "to buy" list, then you can look at the CPUs in more detail.

---

### Post by fela on 2008-04-08
AMD used to be way ahead of intel a few years ago, but with the release of Core and Core2, intel seem to be one step ahead of AMD nowadays.

---

### Post by Rocket2DMn on 2008-04-08
AMD was comparable to, if not better, than intel processors (esp. during the pentium 4 and early post-p4 era), and tended to be significantly cheaper.  Now Intel has really stepped up the quality of their processors in speed, power usage, and overall technology and have dropped prices which is really taking its toll on AMD.  That being said, both companies are still making good processors.
I opted to go for a Core 2 Duo against its AMD competitor when building my Dell desktop last November simply because it was priced the same as the AMD but was slightly better performing and used less power with a smaller architecture.  In all other respects, the AMD processor was on par with the intel.

---

### Post by stchman on 2008-04-08
> **EmosSuck777 said:**
> I just want to know how to compare processors! For example, I want to be able to tell which processor would be the fastest out of a group, because I know that clock speed doesn't mean everything.

So, what do I look for in a processor? What does the cache value mean?

Also, I've heard some stuff about processors that I'd like verified:

1. I heard that Pentium 4's are all pretty bad (even for their times). I also heard that when the P4 FIRST came out they were SLOWER than the latest P3's despite having a much higher clock speed. Why would this be?

2. I also heard that in the past (I don't know about now) AMD's were only worth even having because they were easy to overclock. Was this said by an Intel fanboy?

It's entirely possible that these are totally false, but I would like to be able to figure out what is bogus on my own!

The fastest processors out today clock for clock are the Intel Core 2 series.  They come in dual and quad.  Get the quad as they are not too much more than the dual.

---

