---
title: "Feisty Kernel question"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by DCJoeDog on 2007-05-27
I have a Dell lattitude D600 laptop with a Pentium M chip. So here is my question, which kernel should I use to get the most out of my chip and how can I get it?

Thank you for all who reply.

---

### Post by throntax on 2007-05-27
Are you looking to compile a kernel yourself? If so, I don't imagine any but the most recent would be the best. However it can take a few weeks of a frustrating learning curve... 

I don't really know anything particular about that chip, but I imagine it would be close to a 'i686' chip, so perhaps that kernel would be best from the options in the repositories. 

Then you would want all the power management tools required to keep a laptop running well, APM  management software.. but thats another forum search away!

---

### Post by DCJoeDog on 2007-05-27
Thank you, I will look for an x86 kernel and see if I can find at least a 586 one if one is available.

---

### Post by hardyn on 2007-05-27
The generic kernel, while not optimised, will be within 95% of full efficiency... its probably not worth your time to do any more work.

if you are using a P-M based vaio notebook, you should probably be running the 386 kernel... while despite the naming is also a generic kernel but has SMP disabled.  some P-M based vaios will run hot and slow with the generic - generic kernel.

cheers.

---

### Post by DCJoeDog on 2007-05-29
yeah, I think I will keep my current (generic) kernel, I can and have compiled kernels in the past but I only wanted to do it for this laptop because I was getting MASSIVE slowdown on digg.com with Firefox, but it turns out it was the site itself, once I used ADblock to filter out the PNG images on the page it ran perfectly.

Thank you for all the help

---

