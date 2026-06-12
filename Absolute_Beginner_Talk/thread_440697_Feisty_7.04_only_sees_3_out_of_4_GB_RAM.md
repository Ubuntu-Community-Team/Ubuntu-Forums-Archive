---
title: "Feisty 7.04 only sees 3 out of 4 GB RAM ?"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by ahuesjp on 2007-05-11
Hello,

I am farily new to Linux, and completely new to Ubuntu. This is my first ubuntu install onto a new box I just put together. I have a MSI P6N SLI Board based on the NVIDIA nForce 650i SLI chipset with 4x1GB DDR2 DIMMs.

My CPU is the Core2 Duo E4300, which I believe supports x86-64. So I tried AMD64 CD, but it takes for ever (1+ hours) to load, GNOME has issues, and the installer never goes anywhere. So, given that the i386 was so much faster and seemed to recognize everything, I decided to go with it.

The BIOS sees the 4 GB of RAM, but Feistly i386 only sees 3 GB of RAM. How do I get it to see all 4 GB of RAM?

Thanks,

Juan

---

### Post by Rescue9 on 2007-05-11
If i understand correctly, it has to do with the 32-bit OS. 

Take a look at the following page: [URL="http://www.codinghorror.com/blog/archives/000811.html"]http://www.codinghorror.com/blog/archives/000811.html
[/URL]
I understand that the information is about Vista, but unless you're running 64-bit linux, you're going to have the same problems. Besides, the descriptions are good.

---

### Post by knightnet on 2007-05-15
You should be seeing slightly more than 3GB at a guess but Rescue9 is correct, you can never access all 4GB of RAM on a 32bit OS as some of the memory map has to be used for other purposes.
For example, if you have a video card with 512MB there's 1/2 a gig gone already.

---

### Post by ikonia on 2007-05-15
video card ram is managed different than system ram and shouldn't count against the 3 gig ceiling.

But yup - limitations of 32 bit.

---

