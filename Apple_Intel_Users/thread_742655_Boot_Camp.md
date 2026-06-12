---
title: "Boot Camp"
date: 2008-04-01
forum: Apple Intel Users
---

### Post by money2themax on 2008-04-01
I'm getting a Mac mini in about 1 month and i want to duel boot gusty [or hardy if it's out] on a mac mini so i can do i linux LAN party because it would be great

---

### Post by mrsteveman1 on 2008-04-02
The mini is a great little machine for that stuff, it should work fine

---

### Post by money2themax on 2008-04-02
thx but i need to know if bbot camp will work with ubuntu

---

### Post by wthoang on 2008-04-02
but does the osx boot camp work with ubuntu...cos its supposedly only for windows and mac osx

---

### Post by mrsteveman1 on 2008-04-02
There isn't anything windows specific to boot camp.

Boot camp is simply Apples name for the compatibility support module in the firmware that emulates certain BIOS functions. The bios stuff is fairly standardized at this point and isn't OS specific, so yes Ubuntu works just fine on an Intel Mac just like Windows.

---

### Post by money2themax on 2008-04-02
but they had this windows program so you could switch back on the next start up doesn't that play into this? I'm sry if I'm sounding stupid i don't know much about macs

---

### Post by mrsteveman1 on 2008-04-02
Intel macs use EFI, and they use an NVRAM variable to tell the EFI firmware which volume/operating system to start with next time the system reboots. You are right, there is a startup disk panel for Windows that sets this NVRAM variable just like the one in OS X, and there is no such panel for Linux. 

However, it doesn't really matter, because you can just hold the option key when the system starts and it will ask you which OS you want to boot.

I recommend you leave OS X installed and leave OS X as the designated boot volume, then when you boot into ubuntu just hold option at startup and select the other entry. It might say windows because thats what Apple expects most people to be using, but it works just fine even with Linux.

---

### Post by money2themax on 2008-04-02
ok well thats fine I'll do that then

---

### Post by cyberdork33 on 2008-04-02
boot camp not needed. but you can use it to partition the hard drive if you like. Also, I would suggest rEFIt to replace the standard OS selector.

---

### Post by money2themax on 2008-04-02
> **cyberdork33 said:**
> boot camp not needed. but you can use it to partition the hard drive if you like. Also, I would suggest rEFIt to replace the standard OS selector.
how do i get that and "install" it

---

### Post by cyberdork33 on 2008-04-02
> **money2themax said:**
> how do i get that and "install" it[LIST=1]
[*]Google 'refit'
[*]go to the refit page
[*]download it
[*]install it.[/LIST]It is pretty straightforward.
[http://refit.sourceforge.net/](http://refit.sourceforge.net/)

---

### Post by money2themax on 2008-04-03
mucho thanks! just a question but have you ever used this program yourself?

---

### Post by Viro on 2008-04-03
Hi, read the [Wiki](https://help.ubuntu.com/community/MacBook#head-8ac4aa9e31998d0959f15485171f1dd03a266224). I know it's for the Macbook, but the installation instructions will be exactly the same for all Intel Macs.

Edit: Yes, I used rEFIt and it worked. However, I've completely wiped OS X now since I don't really need it and it was taking up space ;)

---

### Post by cyberdork33 on 2008-04-03
> **money2themax said:**
> mucho thanks! just a question but have you ever used this program yourself?
Yes. Pretty much everyone that multi-boots an Intel Mac uses rEFIt.

---

### Post by thenes on 2008-04-03
I just installed Ubuntu on my Intel Mac Mini a week ago. I went by it by first installing rEFIt, then using boot camp to partion the drive. Then I used a live CD to make the partion boot camp made, called "windows" by defult, into free space. Then I installed Ubuntu 7.10 on that free space. It workes great!

---

### Post by Chrisj303 on 2008-04-04
What sort of games are you hoping to play at the LAN party?

The Mac mini's lack of decent GPU will limit your choice much more so than Linux...

---

### Post by money2themax on 2008-04-05
> **Chrisj303 said:**
> What sort of games are you hoping to play at the LAN party?

The Mac mini's lack of decent GPU will limit your choice much more so than Linux...
oh a bunch of stuff mainly linux

---

