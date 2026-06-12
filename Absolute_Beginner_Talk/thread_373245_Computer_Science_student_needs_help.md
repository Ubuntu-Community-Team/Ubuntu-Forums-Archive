---
title: "Computer Science student needs help"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by nite owl on 2007-03-01
Hi everyone I am totally stumped on one of the questions on the worksheet they gave me in my first week of my computer science course, I cannot find the answer in my textbook or on the internet and am hoping someone could help me with this. Thanks guys :) The question is as follows:

Main memory in modern computer systems is organized in cells. For a 32-bit system, each cell’s address can be represented by 32 binary digits. Answer the questions in the table and show your working in the space under the table.

How many hexadecimal digits are needed to represent a cell’s address?	
What is the largest possible address (as a Hex number)?	
How many cells can be addressed (as a power of 2)?	
How many Giga cells can be addressed (as a power of 2)?	

Any help would be appreciated and if someone could direct me to some sort of tutorial that would be great to. :)

---

### Post by islander_810 on 2007-03-01
> **nite owl said:**
>  How many hexadecimal digits are needed to represent a cell’s address?	 

It's simple. As only 1 hex-digit is required to represent 4 binary digits, if 32 bits are required to represent an address, 8 hex-digits will do the job

> **nite owl said:**
>  What is the largest possible address (as a Hex number)?	 

With a n-bit no, u can represent unsigned nos from 0 to (2^n)-1. Hence, largest no in binary is (2^32)-1 viz 11111.....11111 (32 ones) and in hex it is 0xFFFFFFFF


I'm unsure what the last two ques mean

---

### Post by nite owl on 2007-03-01
Thanks islander_810 for your prompt reply. I'm not really sure how you got the 2nd one but I had it already(I just took a wild guess because you could only have 8 digits and F is the largest hexadecimal digit..lol)???. Is the 0x in front of it just a convention? could a small 16 at the end of it replace the 0x? Thanks

---

### Post by islander_810 on 2007-03-01
yes, that's a convention of representing hex nos. and yes, another way is by writing 16 as a subscript. It's like this. The largest  single digit no that u can make (in decimal) is 9, 2 digit 99 and so on. The largest digit in decimal is 9. Similarly, largest digit in hex is F, hence largest 8 digit no is 0xFFFFFFFF.

---

### Post by nite owl on 2007-03-01
Oh i get it now..Thanks again islander. Now I just have to somehow figure out what the 
3rd and 4th questions are on about.???? :S....Actually maybe you could help me with one more simple question, I'm not sure if I'm right? Its as follows:

A 10KB file is transfered via a network running at 160bps(bits per second). How many seconds will the tansfer take?

I worked it out like this... 10 KB = 10 x 1024
                   Therefore = 10,240 bytes
                   Therefore = 10,240 x 8 = 81,920 bits
                   Therefore    81,920 / 160
                                  = 512 seconds

---

### Post by zba78 on 2007-03-01
My, I wish I could've done this type of thing in my day. I used to have to walk to the library :confused:

---

### Post by nite owl on 2007-03-01
....anyone???? In regards to my last post

---

### Post by Bachstelze on 2007-03-01
It will actually take a bit longer because of the TCP overheads but you're basically right.

---

