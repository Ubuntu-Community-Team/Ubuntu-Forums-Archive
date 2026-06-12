---
title: "automatix2 cannot recieve keys"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by ukbob on 2006-11-17
I am using dapper 6.06 on ibm t20 with wireless i am trying to run automatix 2 but every time i try and start it i get this error bob@ubuntuhome:~$ automatix2
Starting
could not create keys directory
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
bob@ubuntuhome:~$

thanks for any help in advance.if i try and start it via applications i get a box telling me some keys cannot be downloaded and to try later.

---

### Post by goldenatom on 2006-11-17
How did you install automatix2? Did you download the PGP keys in the first place?

---

### Post by ukbob on 2006-11-17
no it wouldnt let me so i found another thread which let me import the key which then lets automatix run.

---

### Post by ukbob on 2006-11-17
i wondering if theres any way i can import the key or keys its meant to find on start up so as to bypass this problem.

---

### Post by goldenatom on 2006-11-17
Im sorry, I meant how did you install automatix2 in the first place? Did you use apt-get...or did you use an install script?

---

### Post by ukbob on 2006-11-17
thanks for help i have sorted it.all to do with setting up my proxy server.

---

### Post by clantoncs on 2006-12-11
Actually, this is my exact problem-- I can't receive the keys because I cannot connect to the getautomatix.com site (which is where, I assume, it's trying to get the keys from).  I live in China, and my connection is a bit screwy-- it randomly won't connect to various sites, sometimes for no reason what so ever.  

I was able to download the install script from the website by using anonymouse, but now when the program runs it can't get the keys.  Is there some way I can tell Automatix2 to connect to all of this through a proxy?  

By the way, I'm using edgy on an i386-- right now I'm using the point-and-click install program, but will do anything to just get this program to run!

---

