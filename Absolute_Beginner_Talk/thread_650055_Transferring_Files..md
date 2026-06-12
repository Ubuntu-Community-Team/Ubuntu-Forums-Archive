---
title: "Transferring Files."
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by CapitanYochua on 2007-12-25
I am trying to transfer a 700 MB file on a 500 MB flash drive from one computer to another (both running ubuntu). How can I do this? I was thinking about somehow splitting the file and then joining it on the other computer with the parts. Thank you for any advice.

---

### Post by SOULRiDER on 2007-12-25
Check this out, ive never sued it but it mihgt be a good option. Ill keep on searching.
[http://peazip.sourceforge.net/file-split-utility.html](http://peazip.sourceforge.net/file-split-utility.html)

---

### Post by frup on 2007-12-25
have you tried compressing it yet?

[http://www.computerhope.com/unix/usplit.htm](http://www.computerhope.com/unix/usplit.htm)

that page has information on the split command and 

[http://www.computerhope.com/unix/ujoin.htm](http://www.computerhope.com/unix/ujoin.htm)

join.... I have never done this before so you better wait till some one else confirms what I said... I'm away from home at the moment :(

---

### Post by foxmulder881 on 2007-12-25
> **CapitanYochua said:**
> I am trying to transfer a 700 MB file on a 500 MB flash drive from one computer to another (both running ubuntu). How can I do this? I was thinking about somehow splitting the file and then joining it on the other computer with the parts. Thank you for any advice.

Wouldn't it just be quicker and easier to burn it onto a CD-R?

If it's no bigger than 700MB of course.

---

### Post by SOULRiDER on 2007-12-25
> **foxmulder881 said:**
> Wouldn't it just be quicker and easier to burn it onto a CD-R?

If it's no bigger than 700MB of course.

+1

---

### Post by CapitanYochua on 2007-12-25
> **foxmulder881 said:**
> Wouldn't it just be quicker and easier to burn it onto a CD-R?

If it's no bigger than 700MB of course.

 Wouldn't work. I had to use a DVD-R to burn it as a data CD or whatever, and my laptop that I am trying to transfer the files to is old-school (running xubuntu) and can't read DVDs for some bad reason.

---

### Post by foxmulder881 on 2007-12-25
> **CapitanYochua said:**
> Wouldn't work. I had to use a DVD-R to burn it as a data CD or whatever, and my laptop that I am trying to transfer the files to is old-school (running xubuntu) and can't read DVDs for some bad reason.

This post didn't make sense?!?

It your drive doesn't read DVDs it doesn't matter, it should still read CD-Rs.

---

### Post by CapitanYochua on 2007-12-25
I am not able to burn it on a CD. And the laptop can't read DVDs. So I can't do it through CD.

---

### Post by frup on 2007-12-25
type in terminal:
cd /where/your/file/is
split -b 500 m file.txt new

add first file to the stick... copy over
add second file to the stick... copy over

then
cat file1 file2 > file

that should work from what I understand. It can't hurt to try :)

---

### Post by foxmulder881 on 2007-12-25
> **CapitanYochua said:**
> I am not able to burn it on a CD. And the laptop can't read DVDs. So I can't do it through CD.

Ok, right.

If you have a crossover network cable laying around, you could always transfer it via network.

---

### Post by CapitanYochua on 2007-12-25
I found a 1 GB flash drive to do it with. Thanks though.

---

### Post by foxmulder881 on 2007-12-25
> **CapitanYochua said:**
> I found a 1 GB flash drive to do it with. Thanks though.
All hail the 1GB stick! :popcorn:

---

