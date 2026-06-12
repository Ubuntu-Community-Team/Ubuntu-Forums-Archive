---
title: "binary operation"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by krisfrajer on 2007-11-14
Hi guys
This is nto ubuntu related

if I have two integers i, j which stores one byte value each,

what would the result of the following operation

( i<<8 ) + j = ?? 

willl the first operation yield 0x00 and te result would be 0x00XX  where XX is the hexadecimal value of j i.e. Hex(j) ?

---

### Post by jw5801 on 2007-11-14
EDIT: Whoops, my bad. << is a shift left logical. So the actual operation is:
?? = i + j
Since i is 8 bit, shifting it 8 bit in either direction returns the same result.

Apologies, haven't coded in C for a while!

---

### Post by krisfrajer on 2007-11-14
wouldnt that "+" sign act as a concatenator so to yield a 2 byte ?

---

### Post by krisfrajer on 2007-11-14
Great thxs. I found the answer I was looking for. 

[http://en.wikipedia.org/wiki/Bitwise_operation](http://en.wikipedia.org/wiki/Bitwise_operation)

---

### Post by jw5801 on 2007-11-14
> **krisfrajer said:**
> wouldnt that "+" sign act as a concatenator so to yield a 2 byte ?

Depends on the language I guess. And on what size you've specified ?? to be. Most high-level languages would probably yield a 2 byte result, but something like C wouldn't unless you defined ?? as being 2 bytes (long int, as opposed to int). My post above was wrong also, I've adjusted it to be accurate now, apologies!

---

