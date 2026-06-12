---
title: "[SOLVED] How can I determine whether I installed 32bit or 64bit Ubuntu 7.10?"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2007-12-24
Hello!

How can I determine whether:

a. I have installed the 32bit Ubuntu 7.10 on my PC, or
b. I have installed the 64bit Ubuntu 7.10 on my PC?

Where can locate this info on my Desktop?
Can somebody provide the Path?

Thanks.

---

### Post by barbedsaber on 2007-12-24
not really sure, but I think if you have a 32 bit PC  and it is working, you have the 32 bit version, and if it dosn't work, you have 64 bit, not sure tho.

---

### Post by Existentialist on 2007-12-24
From the terminal run:

>uname -m

x86_64 is 64 bit.

---

### Post by dvarsam on 2007-12-24
> **barbedsaber said:**
> not really sure, but I think if you have a 32 bit PC  and it is working, you have the 32 bit version, and if it dosn't work, you have 64 bit, not sure tho.

This is a funny answer, you provided... :)

Conclusion:

1. If my Ubuntu is functional, I probably have installed the 32bit version.
2. If my Ubuntu is not functional, I probably have installed the 64bit version.
3. There is always a chance that my PC in functional & I have installed any of the above 1 or 2.
4. There is always a chance that my PC is non Functional & I have installed any of the above 1 or 2.

Great advice, but you have not provided an answer... :lolflag:

Thanks.

---

### Post by dvarsam on 2007-12-24
> **Existentialist said:**
> From the terminal run:

>uname -m

x86_64 is 64 bit.

This is what I got:

```
root@tony-desktop:/# uname -m
i686
root@tony-desktop:/#
```

Should I assume 32bit?

Thanks.

---

### Post by Josh1 on 2007-12-24
> **dvarsam said:**
> This is a funny answer, you provided... :)

Conclusion:

1. If my Ubuntu is functional, I probably have installed the 32bit version.
2. If my Ubuntu is not functional, I probably have installed the 64bit version.
3. There is always a chance that my PC in functional & I have installed any of the above 1 or 2.
4. There is always a chance that my PC is non Functional & I have installed any of the above 1 or 2.

Great advice, but you have not provided an answer... :lolflag:

Thanks.

Tried:
> **Existentialist said:**
> From the terminal run:

>uname -m

x86_64 is 64 bit.

?

---

### Post by dvarsam on 2007-12-24
Is the response "i686" considered 32bit?

Cause you only provided half the response ("x86_64")...

Thanks.

---

### Post by Existentialist on 2007-12-24
Yes i686 is a 32 bit architecture.

---

### Post by Josh1 on 2007-12-24
> **dvarsam said:**
> Is the response "i686" considered 32bit?

Cause you only provided half the response ("x86_64")...

Thanks.

i686 is 32bit.

---

### Post by dnvikram on 2007-12-24
Check with this:

uname -a

This should show you a long line something like this:

Linux mybox 2.6.9-55.ELsmp #1 SMP Wed Dec 24 14:04:42 EDT 2007 **x86_64** x86_64 x86_64 GNU/Linux

This output is of a Red Hat box on which I am working currently in office.That apart,the output should be in the same lines in ubuntu too.

---

### Post by dvarsam on 2007-12-24
> **dnvikram said:**
> Check with this:

uname -a


Thank you all for your quick replies!
Now I want to make this Thread "Closed" & can not find where the option is...
I visit the "Advanced Options" but can't find the "Thread Solved" checkbox...
Thanks.

---

### Post by barbedsaber on 2007-12-24
its not advanced options, its thread tools, and its down the bottem.

---

