---
title: "Extremely basic bash wildcard questions"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by w00dchaz on 2007-02-14
I'm in the process of switching from Windows to Ubuntu and I'm determined to learn how to use the command line. I'm just getting started and I've got a long way to go. I got a Linux phrasebook and I'm having trouble figuring out just how the * wildcard works. 

The book has the following examples: 

rm libby1*.jpg would remove libby10.jpg through libby12.jpg as well as libby1.txt.

rm libby*.jpg would remove libby1.jpg through libby12.jpg, but NOT libby1.txt.

What I don't get is that last part. How does it delete the txt file in the first case, and why doesn't it in the second case?

Could somebody please explain that? Probably won't tax y'all's brain cells, but it's giving me a headache.

---

### Post by annda on 2007-02-14
the example is obviously wrong. you are right. (maybe there was no extension in the first example, or libby1*.* ?)

by the way, if you want to test things like that, create a test folder and you can quickly create empty files of any name with the command "touch some_file_name"

---

### Post by energiya on 2007-02-14
> **annda said:**
> the example is obviously wrong. you are right. (maybe there was no extension in the first example, or libby1*.* ?)

by the way, if you want to test things like that, create a test folder and you can quickly create empty files of any name with the command "touch some_file_name"

I second that. Just make a test folder in your home directory, and try (very nice way to learn). DON'T do anything as root, or beyond the test directory.. just to be on the safe side.

And... Wellcome to the forums!

---

### Post by w00dchaz on 2007-02-14
Thanks guys. I plan to do a lot of experimenting as soon as I get my new computer put together & get Ubuntu on it. I'm chompin' at the bit. 

Maybe I should have a separate user account just for playing around...

---

