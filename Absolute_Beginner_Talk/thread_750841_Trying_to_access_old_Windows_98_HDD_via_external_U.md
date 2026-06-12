---
title: "Trying to access old Windows 98 HDD via external USB hard drive."
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by reubs on 2008-04-09
I'm trying to gain access to an old Windows 98 HDD that might have some files on it that my wife needs in order to apply for grad school.  I have the enhanced IDE HDD hooked up to my tower running Ubuntu 7.10 via a USB port, but nothing is showing up anywhere.

I've tried booting it from another computer, and it hangs on the 98 screen, and I can't gain access to it via Windows or OS X using the external enclosures, so Ubuntu is my last chance before taking it to a shop and having them fleece me for it.

Thanks for any info anyone can offer!

---

### Post by simonn on 2008-04-10
Open a terminal and run the following on a command line just before plugging the drive in to a USB port (do not type the $ that represents the prompt):

```

$ dmesg

```

Now, plug in the drive and continualy run the command above (say, once a second) and note any messages that appear. Post them here.

---

