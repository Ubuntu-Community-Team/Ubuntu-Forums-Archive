---
title: "Display properties+boot+wireless"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by fuligin on 2007-02-02
Hi everyone, 
I am a fairly new use to Ubuntu, and have recently installed 6.10 and am trying to get the hang of it. 

I do have a few questions that i would like to ask, however i will slowly ask them inorder to avoid hatemail :), just kidding this fourm is really helpful and the ppl so far are really fast at giving their assistance. 

Well my first question is that i have a Thinkpad R51e, which has 

ATI Radeon Xpress 200M 

Now im not sure if i need to install a driver for this or not, as i was told as long as u can get ur reslolution theres no need for it, however on xp my screen is alot brighter and crisper, and things seem a bit smaller at 1024 x768.
I have attempted to install the driver with no luck :(.  If i install it will i get the nicer screen that i have on my xp side?


My second question for this post is that I have gotten my artheros wireless to work and managed to connect to a secuired netowrk afer reading from a few postings, however my signal is very low, my network manager shows that my signal is 86-90% and my wirelss shows that im 30%. This is even common in areas that in xp i would get 100% signal, ie at the same desk as my wireless router. is there any other way to connect to wireless that i could have a better signal or is this a bug as ive read in some places. 

My third question is how do i get to the boot manager becuase i want my xp to be my deault boot if i dont put anything on my keyboard, i assum its from my system, but i cant find boot :( the manual directs me to something thats i cant see. 

wow ive already asked too much for one post, im just really exited to get these things running so i can move on to more tinkering.

Thank you all in advance :)

---

### Post by jd65pl on 2007-02-02
To change your default boot option do the following:

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bkup
gksudo gedit /boot/grub/menu.lst
```

Then alter the 'default' line to your windows option i.e. change the number from 0 to what ever windows is.

---

### Post by fuligin on 2007-02-02
Thank you am attempting it now, and will save all the codes on textpad. Do you guys actually know these codes by heart?
----

Worked like a charm, 
Is it posible to have like a auto login, and disable password?

---

