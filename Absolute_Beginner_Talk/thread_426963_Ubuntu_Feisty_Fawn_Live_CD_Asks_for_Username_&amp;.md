---
title: "Ubuntu Feisty Fawn Live CD Asks for Username &amp; Password"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by petzoldpet on 2007-04-29
Hi guys i am new to this community:) , planning to switch from Windows.

Straight away i have had few issues with the Live CD of Ubuntu Feisty Fawn (32 bit version)

- I downloaded the ISO from the ubuntu site burnt it onto a CD

- Booted with the live CD, which gives me few options of which i selected to Start  Ubuntu from the Live CD 

- After few minutes it Shows me the login screen and asks me for the user name and password.

- Every thing ends here whatever user name & password combination i try it does not proceed ahead.

- I have tried googling about this issue but i have not come across any thing like this also i searched in this forum but no result.

- Guys it will be of great help if some body can give me solution to this or direct me to any other resource which can solve this problem.

My System Config:

Opteron 165,
2 gb RAM,
7900 gt,
nForce 4 motherboard

---

### Post by Sef on 2007-04-29
Did you md5sum the download?

---

### Post by petzoldpet on 2007-04-29
> **Sef said:**
> Did you md5sum the download?

No, how do i check for the MD5 checksum

---

### Post by petzoldpet on 2007-04-29
Hey thanks pal the MD5 checksum is wrong :(, the download is corrupted i have to download it again.

But still surprised to see that the live CD ran.

---

### Post by Sef on 2007-04-29
> Hey thanks pal the MD5 checksum is wrong , the download is corrupted i have to download it again.

But still surprised to see that the live CD ran.


Me 2.  Glad I could help you with your problem.

---

### Post by uberground on 2007-06-02
This also happened with me, with the same solution (download a new iso, check the md5sum, burn it again). Thanks for the heads up, I was confused - looking in the docs to try to find how to login on a live cd

---

### Post by aysiu on 2007-07-27
I've never seen this happen with a live CD that I've tried in person, but I have occasionally (about twice or three times a year) seen a thread where someone happens to get a live CD that asks for a username and password.

Well, I popped in a live CD (Kubuntu 7.04 Desktop CD, to be precise). I logged out and tried a username and password, and it worked. The username is **ubuntu**, and there is no password--the password is blank. So if you type in *ubuntu* and hit *Enter* for the password, you should be able to log in.

I'm not sure why it shows up this way, but the relevant line in the /etc/shadow file of the live CD is this: ```
ubuntu:U6aMy0wojraho:13721:0:99999:7:::
``` and root's line (even though there isn't really a root user you can log in as) looks like this: ```
root:*:13721:0:99999:7:::
``` That doesn't help, does it? Since it's all encrypted anyway?

---

