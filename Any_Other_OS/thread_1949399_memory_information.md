---
title: "memory information"
date: 2012-03-30
forum: Any Other OS
---

### Post by ramakanta on 2012-03-30
please learn me the detail of **Virtual memory** And **Page file** in windows. also what is the different between page file and virtual memory. what is the purpose of these memory.
thank you.
 
:confused:

---

### Post by Paddy Landau on 2012-03-30
Your computer uses a **hard disk** (or, these days, often an **SSD** instead) to  hold data and programs. It is like your own brain's normal long-term memory.

Your computer uses **RAM** (Random Access Memory) to do its work. It is like your own brain's working memory -- the things you happen to be doing right at the moment.

RAM is much faster than a hard disk or an SSD. However, being expensive, there is much less RAM than hard disk. Also, RAM is wiped clean when your computer turns off or reboots, so you have to have a hard disk or SDD as well.

Sometimes, the computer runs out of RAM. Then it saves some of its work to hard disk (just as you might make notes on paper). This slows it down, but at least it can carry on working. This is known as **swapping**.

You can turn off swapping, but that is not advised because your computer will crash when it runs out of RAM.

Ubuntu (and most modern distributions of Linux) use a separate dedicated region on the hard disk, known as a **swap partition**, to swap.

Windows (and some distributions of Linux) use a special file called a **page file** instead of a swap partition.

I do not know what OSX (Apple's operating system), Unix and other operating systems use.

For more information, use [Google]("http://www.google.com/").

---

