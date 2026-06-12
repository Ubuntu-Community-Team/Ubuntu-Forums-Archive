---
title: "ubuntu 10.10 ppc got me mad of asking changing passwrd"
date: 2012-11-23
forum: Apple Hardware Users
---

### Post by Stendhalmed on 2012-11-23
hello every body,

i have intalled ubuntu 10.10 ppc on my ibookg4 
and it comes to loging i type my pass word and it ask me to change it this the sentence i get any time 

(current) unix password 

how cani delete the password at all how cani log without password plz

if there not a way to delete at les there will be away not to change it every time

thank you

---

### Post by Stendhalmed on 2012-11-23
is there any body

tell me how to rest this hell passwod

i dont want any pass plz help

---

### Post by snowpine on 2012-11-23
Here are easy instructions to reset your password in Ubuntu:

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

10.10 is **unsupported** since April, so it may be time to come up with an upgrade plan.

---

### Post by Stendhalmed on 2012-11-23
well i dont know how to run the recovery mode , im using an ibookg4 and its very slow is there an other way beacuse i keept hloding the shift key but its dosnet go on that mode.

---

### Post by snowpine on 2012-11-23
Have you read this page yet? (first Google result for "ubuntu recovery mode")

[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

---

### Post by Stendhalmed on 2012-11-23
i have and i have used both kyes shift or escape but 
i coudnet get the rocovry mode.is there an other way to remove the passwd plz

---

### Post by snowpine on 2012-11-23
Apologies but I cannot Support you with an Unsupported release, except to give you links to the official documentation, which I hope is accurate. Most Ubuntu users on these forums have moved on to newer, supported releases.

---

### Post by kingthatcher on 2012-11-25
He has yaboot, because that is the only efi/bootloader that runs on ppc macs, and it is installed by default in a ubuntu ppc installation.

Have you tried, on the second prompt(not the prompt with the options "l" and "c", the next one) when it boots up, typing:
```
Linux single
```That will bring you into single-user mode. That is the closest thing I can get you to if you have yaboot. Once it lets you in through single-user mode, then you can reset the password by typing
```
passwd yourusernamehere
```

@snowpine Also, isn't that a bit cold, saying that, because he has an old unsupported release, you can't help him? I know that it isn't a LTS release, but you could at least try to help him. I don't think that ANY ppc versions are supported, so therefore you will ditch anyone using a mac older than 2006? That's just mean. Sorry, but higher sys reqs come with newer releases, making it impossible for ppc macs to run newer releases well. It's only logical for ppc users to not use newer releases.

Sorry about my rant... Stendhalmed just try the single-user thing... it may help you.

---

### Post by snowpine on 2012-11-25
> **kingthatcher said:**
> @snowpine Also, isn't that a bit cold, saying that, because he has an old unsupported release, you can't help him? I know that it isn't a LTS release, but you could at least try to help him.

How can you possibly accuse I did not try to help him? I gave him instructions to reset his password within 1 hour of posting the question. It turns out my advice was inaccurate, because I am not a Mac user so I didn't know about the difference between Yaboot and GRUB, but it was an innocent mistake, certainly not my intention to be mean. Thankfully you came along with the correct information. :)

My comment "10.10 is unsupported since April, so it may be time to come up with an upgrade plan" is based on 4+ years and over 7,000 posts on these forums. It is good advice.

---

