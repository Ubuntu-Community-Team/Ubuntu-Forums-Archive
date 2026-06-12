---
title: "Restore windows xp, grub error 22 question"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by toastonrye on 2006-10-10
Hi, I was looking for a linux distro a couple of days ago to install on my seperate hd. I have Windows XP on the first one. Anyways after Ubuntu said it was installed, I restarted the computer. On reboot it came up with "grub loader error 22".

I have browsed around google, seems grub wrote over my "MBR", so XP wouldn't boot. Anyways nothing in the tutorials jumped out to say how to fix this. I have since then formatted the second hd, so ubuntu is gone. I still have the live cd for it. (which I used to install it)

So to sum it up, ubuntu to the best of my knowledge is gone, except that the MBR is still trying to load error 22.

Thanks.

---

### Post by PPAAUULL on 2006-10-10
OK you can either restore the MBR with the windows CD or if you want Ubuntu you can try to install it again but be sure to sheck the CD for defects. Sometimes they can play a part in it.

---

### Post by jd65pl on 2006-10-10
These guys had a similar problem [see here!]("http://www.neowin.net/forum/lofiversion/index.php/t405091.html")

---

### Post by PPAAUULL on 2006-10-10
lol says about the same thing as I said. lol

---

### Post by jd65pl on 2006-10-10
hehe tittle tittle but whilst fixing the issue...

---

### Post by PPAAUULL on 2006-10-10
lol Ya well...

---

### Post by jd65pl on 2006-10-10
I have always found it best to give someone a direct solution to an issue in my experience of IT support for a fortune 100 company but i suppose any further explaination helps!!

---

### Post by toastonrye on 2006-10-10
Ya thanks for the quick replies. I used my Xp install disk and repaired the MBR. Works like before, as far as how well windows works.

---

### Post by jd65pl on 2006-10-10
I've heard [microsoft are helpful when removing linux]("http://support.microsoft.com/kb/314458") also!!

---

### Post by Aikon- on 2006-10-10
> **toastonrye said:**
> Hi, I was looking for a linux distro a couple of days ago to install on my seperate hd. I have Windows XP on the first one. Anyways after Ubuntu said it was installed, I restarted the computer. On reboot it came up with "grub loader error 22".

I have browsed around google, seems grub wrote over my "MBR", so XP wouldn't boot. Anyways nothing in the tutorials jumped out to say how to fix this. I have since then formatted the second hd, so ubuntu is gone. I still have the live cd for it. (which I used to install it)

So to sum it up, ubuntu to the best of my knowledge is gone, except that the MBR is still trying to load error 22.

Thanks.

I had a similar problem with my Ubuntu installation; in fact, I still do whenever I update my kernel. Seems that the GRUB installers (and other scripts that auto-generate my menu.lst file) think that my main drive's Linux partition is on hd(1,1) when it is in fact located at hd(0,1).

I wrote a slightly more detailed post about it [here]("http://ophelianet.blogspot.com/2006/08/diving-in-vs-falling-in.html"); try re-installing Ubuntu so that it re-installs GRUB, then manually edit the boot command until you get it to boot either Windows or Linux; then you should have an idea of where its getting confused and you can fix all the bad instances of hd(x,y) in /boot/grub/menu.lst.

Hope that helps! (And I hope that's your problem, and not something much more serious :-# )

-Aikon

---

### Post by PPAAUULL on 2006-10-10
screw windows go linux all the way!!!!

---

### Post by jd65pl on 2006-10-10
Thats what I feel I have never been so liberated in terms of computing capabilities!!

---

### Post by PPAAUULL on 2006-10-10
So true!!! I got into it 2 years ago and I have never looked back!!! I switched to Ubuntu from Suse but other then that I have been using Ubuntu for the majority of it!! and I love it!!!!!

---

