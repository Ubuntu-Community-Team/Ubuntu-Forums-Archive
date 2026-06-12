---
title: "deleting stuff."
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by devilsadvocate1987 on 2006-11-12
hi all, 
In continuation of a wierd problem i've been having (i havent been able to sign in from gdm. It accepts user name and passwords, starts loading X and the comes back to the gdm), i've more or less isolated it to not having enough free space. the partion is showing 0b free when i try df from one of the virtual consoles. 

Now, since the problem started, I've deleted a LOT of stuff, in tens and maybe even hundreds of megabytes. It still shows 0b. Is it moving the files to some temporary place? I've checked .Trash and its empty. Just to be safe rm -r .Trash . I could really use some help on this one.

Why do we even need this recycle bin like business, I will never understand. Personally, I find it _very_ annoying and even insulting. I always shift+delete whenever possible.

---

### Post by bodhi.zazen on 2006-11-13
> **devilsadvocate1987 said:**
> hi all, 
In continuation of a wierd problem i've been having (i havent been able to sign in from gdm. It accepts user name and passwords, starts loading X and the comes back to the gdm), i've more or less isolated it to not having enough free space. the partion is showing 0b free when i try df from one of the virtual consoles. 

Now, since the problem started, I've deleted a LOT of stuff, in tens and maybe even hundreds of megabytes. It still shows 0b. Is it moving the files to some temporary place? I've checked .Trash and its empty. Just to be safe rm -r .Trash . I could really use some help on this one.

Why do we even need this recycle bin like business, I will never understand. Personally, I find it _very_ annoying and even insulting. I always shift+delete whenever possible.

try ```
Locate .Trash
```And other variations.

---

