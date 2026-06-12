---
title: "Live CD vs. Installation of 6.06"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by bob415 on 2006-09-26
I want to use Ubuntu 6.06 to surf the internet. I want to know which is the safest. I was told using live CD, the hard drive is disabled making it safe from intrusion from the internet. I don't know what safety features are there, when I use the installed Ubuntu in my computer? 

     Thank you,

---

### Post by benuski on 2006-09-26
Well, it really depends on how safe you want to be.  Really, for all intents and purposes, you're perfectly safe surfing the internet with Ubuntu installed on your hard drive.  There are very very few viruses for linux, like under 10, and they can get patched within hours, not days or months.  Also, spyware can't be packaged in Ubuntu software because the source code is right there, anyone could see what it was doing.  Also, with the livecd, you get the disadvantage of having to reconfigure everything every time you want to use the internet.  So, in conclusion, I say install Ubuntu over using the livecd every time.

---

### Post by reacocard on 2006-09-26
The liveCD is somewhat safer, since it impossible for any intruder to access your hard drive. Even a full install is still very safe though. Ubuntu's default setup is hard to break into, and you can make it even more secure by installing a firewall such as guarddog or firestarter.

---

### Post by whizbaby on 2006-09-26
As long as you don't provide any services you don't need any precautions, ubuntu is safe by default. Using software that requires opening ports to the outside (e.g. bittorrent, aim(ICQ), webserver) makes it worth thinking about a firewall.

---

### Post by aysiu on 2006-09-26
My opinion?

1. They both have the same security defaults and are pretty safe.

2. Security primarily rests with the user. It's nice to have good software security, but if the user is stupid, it doesn't matter how good the software is.

3. The live CD is probably the less secure of the two, as it has a standard username (*ubuntu*) with *sudo* privileges and no password needed to execute root commands. The live CD doesn't automatically mount your partition, but it *could* mount your partition and write to it.

---

### Post by og-emmet on 2006-09-26
> **bob415 said:**
> I want to use Ubuntu 6.06 to surf the internet. I want to know which is the safest. I was told using live CD, the hard drive is disabled making it safe from intrusion from the internet. I don't know what safety features are there, when I use the installed Ubuntu in my computer? 

     Thank you,

Generally speaking "live" distros, those that run entirely off a cd, are "safer" than installed versions since the cd can't easily be altered*. With that said a properly patched ubuntu box is extremely safe.

If you go with a standard installation and pay attention to the "Update Manager" you'll be very, very safe from things like worms and viruses.

Hoped that helped,
emmet


* You could do a unionfs hack but it's unlikely.

---

### Post by metaltailz on 2006-09-26
They both have pretty much the same security, but the liveCD you have to reconfigure to your likings. Last time I checked there where 40 known viruses for linux, but the majority of them where made and used in a lab, and never released into the wild world web.

If you are really cautious about security I think the best and easiest thing to do would be to install 6.06, and anti-virus and a firewall. That way you would be safe.

---

### Post by bob415 on 2006-09-26
I can't figure out how to respond to all the messages of help, so thank you, to all

What I am conserned with on the internet is typing in passwords and credit card numbers. I don't plan on doing any configuring of Ubunto, that is beyond my knowledge. I just boot from the cd and it takes about 10 minutes for this to complete. I was looking for a way I could feel safe when I do these things.

---

### Post by aysiu on 2006-09-26
If you're typing your credit card number into the wrong site, it won't matter live/installed or Ubuntu/Windows/Mac...

---

