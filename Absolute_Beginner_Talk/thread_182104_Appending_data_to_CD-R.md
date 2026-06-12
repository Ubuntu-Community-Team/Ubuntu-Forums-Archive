---
title: "Appending data to CD-R"
date: 2006-05-25
forum: Absolute Beginner Talk
---

### Post by jimbob on 2006-05-25
Does anyone know if k3b will append data to a partially filled CD-R disc?

I have used the Nero demo software to do this successfully but was reluctant to purchase the package since I would not use it enough to justify the price.
________________________________       
  If I can't be Mr. Root I won't play ...

___________________________________
AMD 64 Sempron 3400+ 512MB 60GB
Gigabyte GA-K8NS socket 754 nForce3 250 chipset
nVidia GeForce2 MX/MX400 64 MB

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by meng on 2006-05-25
K3B should support multisession writing, which is what you're requesting.

---

### Post by wpshooter on 2006-05-25
It took me a while to figure it out, but yes it does.

I would recommend trying it on the Dapper Drake beta version of Ubuntu and make sure you install of the updates to K3b after you do the initial installation of the program.

P. S. - I use CD-RW media instead of CD-R.  I can't understand while people waste their money on all of those CD-Rs.

Good luck

---

### Post by Clay85 on 2006-05-25
I think I just noticed that Breezy doesn't do multisession CD-Rs. How do you get the K3B program? 

I use a combo of CD-R and CD-RW. If I'm burning MST3K episodes to a CD/DVD there's no reason to put it on a CD/DVD-RW, I'll only need to write to the disk once (so this is cheaper). I back up files on CD-RWs (or DVD-RWs) because I often make last minute changes to files while I do backups, and if I used CD-Rs for this it would be costly. I don't think completely excluding either R or RW is a good idea, I like to use both for different tasks.

---

### Post by jimbob on 2006-05-25
Wpshooter:

  Could you be so kind as to tell me how you did it?

Clay85:  

  I actually went to the k3b website and got the source and did a compile/make on my system since I needed version 12.15 due to SCSI problems with 12.14.  The instructions are there on how to build the module and they worked well.

Thanks guys ...
________________________________       
  If I can't be Mr. Root I won't play ...

___________________________________
AMD 64 Sempron 3400+ 512MB 60GB
Gigabyte GA-K8NS socket 754 nForce3 250 chipset
nVidia GeForce2 MX/MX400 64 MB

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

