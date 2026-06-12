---
title: "Is my XP partition safe?"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by mit on 2006-07-07
One of things i like about linux is you can use the machine for what you need all of the time, and not have have to worry about Spyware and Virus :KS 

Is there any chance that i could contract a Virus (that is harmless to Ubuntu) and transfer itself to the Windows NTFS partition?

Mit

---

### Post by Stealth on 2006-07-07
Nope. Mainly because Ubuntu doesn't even have write support to your NTFS partitions, so how would a virus put itself on there? :D

---

### Post by mit on 2006-07-07
Great, news, thanks!

mit

---

### Post by FredB on 2006-07-07
NTFS writing is very very very experimental. So, there is - and there won't be - a problem related to this before a long long time ;)

---

### Post by mit on 2006-07-07
music to my ears!

---

### Post by PriceChild on 2006-07-07
Correct me if i'm wrong... but i can't see any problem even with fat partitions...

no windows viruses can run in linux and infect files, and so can't get onto fat drives to infect windows.

However of course, you can always download infected files to a fat drive in linux, and read it from a windows install.

---

### Post by Stealth on 2006-07-07
That's correct PriceChild. Unless you get Wine to have access to your Windows partition, and deliberately get it to install there somehow, I really doubt there's any problem (as Wine creates a fake Windows directory in your home anyway, so it's not gonna get any root access without your consent). 
I didn't bother adding anything about FAT though as he specified his NTFS partition. ;)

---

### Post by mit on 2006-07-07
Thanks guys. Did i misread or did you say Install Linux on FAT? I thought Linux could only go on its own (superior) file system EXT?

mit

---

### Post by aysiu on 2006-07-07
You misread.

---

### Post by mit on 2006-07-07
as i thought :KS 

mit

---

