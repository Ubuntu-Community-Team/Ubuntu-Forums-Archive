---
title: "Question about using custom kernel"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by CounterStrike on 2007-03-07
I have a question that I hope someone could help with. I have seen the thread on the dev boards that discussed the decision to go with a generic kernel supporting multiple features (386,686,smp,etc...) in lieu of continuing the dapper custom kernels, but had a question with regard to what the implications are of using a custom compiled kernel instead of the generic kernel. If someone were to compile a specific kernel for 64 bit and high memory support, what would that mean as far as updates go? Does having a custom kernel negate you from using apt-get to install updates for the ubuntu kernel because it is custom? If that is the case, how does a custom kernel get updated with secrity updates? Do you have to recompile the kernel each time you want to apply a security update?

   I am trying to ascertain the implications and understand any limitations having a custom kernel would impose as opposed to running the generic kernel.

Thanks,

Brian

---

### Post by Bachstelze on 2007-03-07
Of course, the kernel you compiled yourself will not be updated with apt-get. All the kernel-related stuff - headers, restricted-modules - will also not apply for your kernel. Apart from that, your updates will behave normally.

---

### Post by CounterStrike on 2007-03-07
Thanks HymnTo LIfe for addressing this. I thought that was the case, but couldn't find anything stating as such.

Thanks,

Brian

---

