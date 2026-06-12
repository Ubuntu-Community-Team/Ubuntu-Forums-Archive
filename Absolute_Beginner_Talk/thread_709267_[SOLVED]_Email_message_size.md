---
title: "[SOLVED] Email message size"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by yanewby on 2008-02-27
I am writing a small Perl script that emails images to my online storage space.

I would like to be able to calculate the size of the potential email before sending it to the email send queue.  How do I do this?

For instance I have an image that is 8Mb in size.  This equates to 8420142 bytes.  The email I want to send (including a minimal amount of text) registers as 11602073 bytes.

How do I go about calculating the 11602073 bytes size?  What are the email overheads that increase the email size?

---

### Post by LuisGMarine on 2008-02-27
I'm asking a mod to move this to the Development & programming section.

I think posting this about scripting in the beginners area is probably a bad idea since no one starting out with ubuntu knows programming.  At least the regular uses, I know we have exceptional users around but on the majority no one knows.

---

### Post by dcstar on 2008-02-28
> **yanewby said:**
> I am writing a small Perl script that emails images to my online storage space.

I would like to be able to calculate the size of the potential email before sending it to the email send queue.  How do I do this?

For instance I have an image that is 8Mb in size.  This equates to 8420142 bytes.  The email I want to send (including a minimal amount of text) registers as 11602073 bytes.

How do I go about calculating the 11602073 bytes size?  What are the email overheads that increase the email size?

All binary attachments have to be converted from 8 bit to 7 bit (the e-mail transport system was only ever intended to handle 7 bit data - like ACSII text).

Your 8,420,142 8 bit bytes equals 67,361,136 bits, which will encode into 9,623,020 7 bit characters (which still take up 8 bits in transmission) , and then you have to add in the various formatting characters/headers etc. etc. (CR/LF pairs for each encoded line and so on).

So the "simple" estimation formula is to multiply by 1.37, then you should have a number close to the size of what your encoded attachment will be.

---

### Post by yanewby on 2008-02-28
Thanks dcstar!  Great explanation.

---

