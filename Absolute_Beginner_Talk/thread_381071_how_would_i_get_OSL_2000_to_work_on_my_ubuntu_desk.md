---
title: "how would i get OSL 2000 to work on my ubuntu desktop?"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by spyder850 on 2007-03-10
hey guys, this is my first post into the ubuntu forums (woot). anyway, im booting 3 os's on two hdd's.

1st hdd. Windows Media Center 160GB (gaming and such)

2nd hdd. Windows Media Center(beta testing software and such)/Ubuntu 6.06...

now, usually when i would navigate between hard drives, i installed OSL 2000 on each of them and it would ask me which one i would like to boot from and i was able to get to each os without hassle...

but since ive started to use ubuntu, it recognises that Linux is there, but it hangs up when i press enter to use the linux partition...and i feel its because i dont have OSL 2000 installed on my ubuntu machine!

so my question is, is how do i get my osl2000.exe to run in ubuntu?

convert to .deb? if so how?
get wine? if so, how do i configure? and run?

lol. many, many questions. ive always wanted to utilize a good linux distro and when i found ubuntu, all my other linux distros just seemed too difficult to configure. but i will stick with ubuntu and i want to learn as much as i can about the distro that i can!

thanks.

---

### Post by louieb on 2007-03-10
Never heard of osl2000 but I looked at the website. Its a boot manager like GAG, not a boot loader. My wild as guess of the day is  you  will need to install the Linux boot loader (GRUB or LILO) in the MBR of you Linux partition. (See the reinstall grub link in my signature), and the point osl2000 to it.
What does you osl2000 doc say about booting Linux.

---

