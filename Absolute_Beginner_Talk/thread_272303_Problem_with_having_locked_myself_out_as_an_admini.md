---
title: "Problem with having locked myself out as an administrator"
date: 2006-10-06
forum: Absolute Beginner Talk
---

### Post by rusimons on 2006-10-06
Hello everyone. I think I have really messed up this time. 

I used the alternate CD and had an oem install, After having done a lot of installing, I added several users without adminstrator priveliges, but forgot to add myself as an administrator. Then I removed the oem user by typing sudo oem-config-prepare in the terminal, and never got the opportunity to add myself as a priveliged user after reboot. Now I have only users without administrator priveliges on my machine. This is truly frustrating. Do I have to reinstall everything, or is threre something I can do in order to add myself as a user with adminstrator priveliges?

Thanks in advance for any reply, either positive or negative.

---

### Post by guysmiley25 on 2006-10-06
I remeber reading somewhere that there was a file you could edit to give yourself sudo access. Can't remeber what is was though.

But you could boot to live CD then mount the partition then edit the file.

Just a guess but should work

Sorry I can't tell you what file it was.

---

### Post by Iarwain ben-adar on 2006-10-06
Hi,
just boot up in rescue mode :D

That way you're root (be careful!) so you can add a admin.


Iarwain

---

### Post by rusimons on 2006-10-08
Thanks a lot for your help. Because Ubuntu is the only system on my computer, I was not able to automatically make choises from Grub. But all I needed to do was to press the escape button during bootup. Then I was able to boot up in rescue mode.

Again: Thanks a lot. :-)

---

