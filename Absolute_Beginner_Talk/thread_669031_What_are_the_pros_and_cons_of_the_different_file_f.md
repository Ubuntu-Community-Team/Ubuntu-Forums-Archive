---
title: "What are the pros and cons of the different file formats?"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by GopherGirl on 2008-01-16
What are the pros and cons of the different file formats?  Like ext3, ext4 etc...

---

### Post by jeffus_il on 2008-01-16
To start,
File systems are compared by the following:
1. Speed (Can differ for large and small files)
2. CPU usage 
3. Stabilty (journaled systems recover better from crashes)
4. Accessibility, by different OS's
5. Efficiency (Use more or less disk space for the same file sizes)

Use google to find comparisons, there are lots out there. In practice I find the differences small amongst the popular file systems.
ext3 is standard on many distros. I use reiserfs and like it (even though the creator- Mr Reiser is apparently in jail), I read that XFS may be the best all round system (reasonable cpu usage and fast), and I am trying it on a partition.

(Posters please add or correct)

---

### Post by kpkeerthi on 2008-01-16
[http://en.wikipedia.org/wiki/Comparison_of_file_systems#Features](http://en.wikipedia.org/wiki/Comparison_of_file_systems#Features)

---

### Post by mikewhatever on 2008-01-16
> **GopherGirl said:**
> What are the pros and cons of the different file formats?  Like ext3, ext4 etc...

One is better for some, the other for others. ([search for ext3 vs ext4]("http://www.google.co.il/search?q=ext3+vs+ext4&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a")). Oh, and those are file systems.

---

### Post by jerrykenny on 2008-01-16
I like ext3 for /   and ext2 for /home

I reckon you NEED a journaling fs for the root partition, however since i'm using a laptop, and have multimedia files, I use ext2 for performance.

---

### Post by cheahk on 2008-01-16
I'm not sure what you're getting at, but to the average user, the filesystem is transparent, and the only difference is probably speed.  From some of the benchmarks that I have seen, reiser4 seems to be really quick, especially for reading large files.  But the difference isn't that great, like 53 MB/s vs 52 MB/s for reiser4 vs ext4.

It all depends on the application.  If you're building a server and expecting high disk I/O, then pick reiser4.  If it's for a desktop/laptop install for casual web browsing and work, then ext3 is good enough.  Then again, you can always tune the fs, but it all depends how far you want to go to get the most out of each fs.  Again, to the casual user, the difference is negligible. 

-K

---

