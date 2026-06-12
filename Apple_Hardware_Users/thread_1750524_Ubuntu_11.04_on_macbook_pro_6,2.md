---
title: "Ubuntu 11.04 on macbook pro 6,2"
date: 2011-05-05
forum: Apple Hardware Users
---

### Post by manitta1 on 2011-05-05
hello guys,
 I have a mbp 6,2 with triple-boot: 

1. Mac OSX 10.6.7 
2. win7 (ultimate x64)
3. ubuntu 10.10 (x64)
 
when I installed ubuntu I followed this guide: 
[https://help.ubuntu.com/community/MacBookPro6-2/Maverick?highlight=%28\bCategoryMac\b%29](https://help.ubuntu.com/community/MacBookPro6-2/Maverick?highlight=%28\bCategoryMac\b%29)

 Now I want to upgrade to 11.04 but reading the ubuntu guide at 
[https://help.ubuntu.com/community/MacBookPro6-2/Natty?highlight=%28\bCategoryMac\b%29]("https://help.ubuntu.com/community/MacBookPro6-2/Natty?highlight=%28%5CbCategoryMac%5Cb%29")
I saw that it says **"Note That Some Bugs May cause hardware damage.".**

 Can I upgrade? which guide should I follow?
 thanks in advance.

---

### Post by manitta1 on 2011-05-08
up

---

### Post by pauljwells on 2011-05-08
Well, it is always a risk. It's your machine and not mine, but it looks like the 'bugs' are pretty minor. Just don't do anything CPU intensive until you're sure you've got the sensors working and don't use 'hibernate'...

As for a 'guide' I'm not sure there is one :-/ FWIW I found that the dist-upgrade worked perfectly on my 64 bit netbook - just make sure if it asks any questions you don't understand that you write down the question and your choices so you can research afterwards. If it doesn't work a clean install is always an option.

---

### Post by Silmathoron on 2011-05-08
I don't know what to answer to this kind of question. I don't even understand why they say it could cause hardware damage : if you know what you're doing, you can't damage your hardware, when it breaks, it's because it was old or of poor quality.
Of course, if you try to mess with your computer while you don't fully understand the consequences of the modifications you're doing, that could be a problem.
By the way, did they write anything more about those "hardware damage" ?

Anyway, could you please give us more details about your mbp ? I don't own a 6,2 so I'm not able to tell you much more.
```
sudo lspci -k
```

---

### Post by manitta1 on 2011-05-08
this is my mbp:

cpu: intel core i7 2,66 GhZ x64
ram: 4 gb ddr3 1066mhz
gpu: intel graphics HD and Nvidia GeForce 330M
hdd: 500 gb (10gb for ubuntu)

---

### Post by pauljwells on 2011-05-08
@manitta1

please run the code posted by Silmathoron in a terminal and copy/paste the output here

---

