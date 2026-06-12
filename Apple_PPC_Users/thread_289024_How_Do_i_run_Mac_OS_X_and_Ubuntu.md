---
title: "How Do i run Mac OS X and Ubuntu?"
date: 2006-10-30
forum: Apple PPC Users
---

### Post by compaq_xp on 2006-10-30
I want to run My Mac OS X 10.3.9 And the old verson of ubuntu on the same machine but not unitstall Mac os x in the prosess, Due to the fact i don't have restore cd's.

Does anyone know how i can do this?

---

### Post by compaq_xp on 2006-10-30
And how long does it take to get an ansewr?

---

### Post by angkor on 2006-10-30
> **compaq_xp said:**
> And how long does it take to get an ansewr?

It depends. People here are just users like you and volunteer to help when they know the answer to your question.

---

### Post by Sef on 2006-10-30
Does your Apple use PPC or intel chips?

---

### Post by compaq_xp on 2006-10-30
it' a 800MHZ G3 PPC

---

### Post by elcasey on 2006-10-30
I don't know myself because I run OS X and Ubuntu 6.06 on two different machines, but there are a lot of FAQs and stickied topics in the various subforums here that may help you - including one called "If Your Post Gets Zero Replies."

Look through the site and do some searching on your own. Vague problems and issues don't help too much when people try to help you out and I'm sure you're not the first to ask this question. It's probably on this very forum, stickied somewhere.

You have to do some legwork on your own in many cases, but that's how you learn.

---

### Post by gn2 on 2006-10-30
Can you access a boot device selection menu at boot on a Mac?

Can you add another hard drive?

If yes to both this may help: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

---

### Post by compaq_xp on 2006-10-30
I do have a boot slection. 

I can't add another hard drive]

---

### Post by Sef on 2006-10-30
I m moving this thread to the Apple PPC section.  There will be more support there than here.

---

### Post by linear on 2006-10-30
There is a way to do it, but I would strongly recommend you back up your OS X partition first.

0. Search this forum and read up on any model specific quirks.
1. Back up the OS X partition. ([Carbon Copy Cloner]("http://www.bombich.com/software/ccc.html") works well.)
2. Repartition the disk. Make two partitions, leave the first as free space (not formatted) and the second for OS X. You can use Disk Utility if you have a backup (it's destructive). Otherwise, there is a howto [here]("http://ubuntuforums.org/showthread.php?t=89960") on using **parted** to resize non-destructively.
3. Boot from the Ubuntu install disk. When you get to the partitioning step, tell the installer to use the largest free space. It will take care of the rest.

---

