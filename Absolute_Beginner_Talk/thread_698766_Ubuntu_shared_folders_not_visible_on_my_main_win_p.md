---
title: "Ubuntu shared folders not visible on my main win pc."
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by DizMan on 2008-02-16
Hi there

I've used Ubuntu 7.10 for about two weeks - and I'm quite impressed!

I'm dual booting Ubuntu and Win XP prof. on and old IBM T23 laptop. So far so good.

I also have a desktop pc which is my main pc. It runs win XP prof. On this machine I've got some shared folders (the "documents" folder for example). This is visible on the Ubuntu laptop. Fine!

On the Ubuntu laptop I also selected the app "Shared folders" and made my home folder shared (folder \home\peter). I called the workgroup the same names as on my main win pc.

When i click on "Workgroup computers" on my win pc it shows both my win pc and the Ubuntu laptop. When I click on the Ubuntu laptop a dialogue box is opened where I have to enter username and password. But regardless of what I'm entering nothing happens. The dialogue box just stays open and prompt me for username and password again.

What can I do to be able to see the Ubuntu files on the win pc? Somebody told me to install the Samba server. I don't know if that is nescecary. I tried to install everything with "Samba" in the name or description through the synaptic app. But that didn't help.

Please give me a hint - and please write the help for "dummies" as I'm very new to the Ubuntu (and every non-windows) world!

Thanks in advance!

/diz.

.ps: The partitions where Ubuntu are located on the laptop are formatted with the ext2 filesystem by partition magic. Can that be the reason? The Ubuntu machine itsself runs smoothly

.pss: I earlier posted a thread with this question; but didn't get an answer that I could understand: [http://ubuntuforums.org/showthread.php?t=694600](http://ubuntuforums.org/showthread.php?t=694600). Sorry if I'm breaking the rules by posting again.

---

### Post by badmedic on 2008-02-16
Are you using different User Names and Passwords on the two systems? If so you could try creating a new User/pw on the Ubuntu Laptop that matches your Windows Desktop account.

I am pretty sure that with Ubuntu/Samba the user has to exist on the system to access shares on it.

---

### Post by DizMan on 2008-02-16
> **badmedic said:**
> Are you using different User Names and Passwords on the two systems? If so you could try creating a new User/pw on the Ubuntu Laptop that matches your Windows Desktop account.

I am pretty sure that with Ubuntu/Samba the user has to exist on the system to access shares on it.

Thanks for your reply!

Hmmm... Yes and no.

The user "peter" exists on both the win pc and the Ubuntu laptop. But is has a password on the Ubuntu machine - and none on the win machine. But i've thied using the Ubuntu password (in lower case, upper case and mixed case) - and also tried without any password. But I don't get passed this dialogue with username and password.

/Diz

---

### Post by markharding557 on 2008-02-16
i'm not any expert on networking however maybe this link will help[https://help.ubuntu.com/community/ComprehensiveSambaGuide?highlight=%28samba%29]("https://help.ubuntu.com/community/ComprehensiveSambaGuide?highlight=%28samba%29")

---

### Post by DizMan on 2008-02-16
> **markharding557 said:**
> i'm not any expert on networking however maybe this link will help[https://help.ubuntu.com/community/ComprehensiveSambaGuide?highlight=%28samba%29]("https://help.ubuntu.com/community/ComprehensiveSambaGuide?highlight=%28samba%29")

Thanks. 

I just read the document - but as far as I can tell the howto desribes how to read a Win share on Ubuntu. That already works here. I need the opposite - to read an Ubuntu share on the win machine. Is that possible (even for a complete newbee)+

/Diz

---

