---
title: "Novatel Merlin U630 3G/UMTS/GPRS in Ubuntu...slow... help?"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by shriek on 2006-08-11
Hi, I just installed Ubuntu over my windows machine. for now I´m focusing on getting internet on my laptop and then move to other stuff (like wine for getting some apps to work on linux).

I use a 3G/GSM/UMTS/GPRS modem to access internet. Since Novatel Merlin U630 was detected right from the beginning I just had to install gnome-ppp to configure the access.

My problem now is that it is now a lot slower than in windows. It is supposed to get 384kpbs when connected to a 3G cell but I getting GPRS performance (56kpbs) even though the LED on the modem indicates it is connected to a 3G cell.

I know that probably most of you out there haven´t tried these kind of access but maybe you could still help me with diagnosing the problem.

---

### Post by xerife on 2006-08-12
Hello Shriek;
You´re not the only one. I have the same problems like you mentioned above. I've searched in a lot of ubuntu foruns, in google and almost everywhere, with no sucsess. It's kind of a problem. I guess it's a kernel bug. Anyway if you get the solution post it in here.

---

### Post by Carlos Santiago on 2007-05-28
I had the same problem. My report and solution is on [https://bugs.launchpad.net/ubuntu/+source/pcmciautils/+bug/99479](https://bugs.launchpad.net/ubuntu/+source/pcmciautils/+bug/99479)

As you will see on that post, I also had a problem when I update my Edgy to kernel 2.6.17-11-386.
Now I am using Feisty and everything works fine, but it also require manual configuration.

If you wish the modem to work out of the box, you are invited to had a comment to that post.
Together we may be success.

---

### Post by Carlos Santiago on 2007-07-10
My connection problems are all solved, and I also made a DEB package that I would like to share with you.

---

