---
title: "cant install any program 7.10"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by Pabx on 2007-10-18
Hi when i try to install some kinda program , using the add/remove app i cant it just says 

"the list of applications is not available" 

and when i try to use sudo apt-get install it   cant find any pacage. could you please help?

---

### Post by bobplano on 2007-10-18
try pinging ubuntu.com and see what you come up with. your internet connection might not be working. if you are using wifi, can you post your card here?

---

### Post by mitchbones on 2007-10-18
If you are able to ping them, you might try going to System>Admin>Software Sources and then enabling some of the sources (universal etc)

Hope this helps.

---

### Post by tboutcher on 2007-10-19
Same problem and connection is fine, could the repos be down due to high traffic?

---

### Post by supersloth on 2007-10-19
I have the same problem. Enabling the sources doesn't fix the problem, and I am able to ping ubuntu.com successfully.

I am using Wi-Fi, I have a default Intel a/b/g card from dell on my 700m.

---

### Post by lazyart on 2007-10-19
Servers are being hammered by thousands of people downloading the latest release of one of the most popular linux distros.  You'll just have to wait it out a day or two till things ease up.

---

### Post by kshane on 2007-10-19
> **supersloth said:**
> I have the same problem. Enabling the sources doesn't fix the problem, and I am able to ping ubuntu.com successfully.

I am using Wi-Fi, I have a default Intel a/b/g card from dell on my 700m.

Enable a different server in System>>Administration>>Software Sources

I changed to Utah and it's going smooth

Kevin

---

### Post by lazyart on 2007-10-19
<<insert Utah joke here>>

---

### Post by supersloth on 2007-10-19
Changing to Utah worked perfectly, gracias Senors.

---

### Post by Room 34 on 2007-10-19
I had this problem and it was what mitchbones described: go to **System > Administration > Software Sources** and make sure the first four boxes are checked!

I kept seeing a message saying that the package was not available for my system (i386), which seemed highly unlikely.

I'm still new to Ubuntu, but I did not have to do this under 7.04, so I wasn't expecting this kind of problem when I upgraded. My problem had nothing to do with server loads or which server I selected, it was all about those checkboxes!

---

### Post by kshane on 2007-10-19
> **supersloth said:**
> Changing to Utah worked perfectly, gracias Senors.

Any time!  :)

Kevin

---

### Post by efcorpamer on 2007-10-21
> **mitchbones said:**
> If you are able to ping them, you might try going to System>Admin>Software Sources and then enabling some of the sources (universal etc)

Hope this helps.

Thanks mitchbones. Enabling everything in the System>Admin>Software Sources did the trick. I am also running an intel wifi internal card in a newer toshiba laptop. I am also having trouble gaining access to my external hard drive. It says that it is unable to mount it and I thought It would recognize that it is formatted for windows, but still be able to read and write from it. Do I need a special app in order to do this? Thanks again.

---

