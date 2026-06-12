---
title: "Can't log in after download updates..."
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by ajard on 2008-02-08
Hey everyone, I'm happy to say I made the switch to Linux (Ubuntu 7.10) and through the help of this forum I've got everything working right. I'm still new though, and I have no idea what to do about this problem:

Last night I downloaded all of my security updates and recommended updates, about 180 of them total. I fell asleep while they were downloading and when I woke up my computer had shut down (forgot that i set  it to shut down after 2 hours). The problem is, I can boot up and get to the login screen, it takes my name and password and then it just stalls. I am fairly sure all the updates were downloaded, I don't know if they are set to automatically install or what though.. I'm currently logged in through failsafe gnome. Can anybody help??

---

### Post by ajard on 2008-02-08
Also - it just occured to me, it's probably worth mentioning that my graphics card can't handle Compiz so I had it turned off. Maybe something in the updates turned it on?

---

### Post by nynoah on 2008-02-08
I am thinking that you have the wrong graphics type enabled.  Try doing this and see if it helps.

>  Boot in Recovery Mode (select it from the GRUB menu)

type:
Code:

dpkg-reconfigure xserver-xorg

select the "vesa" driver and press ENTER whenever you don't know the answer to a question.

then type:
Code:

reboot

and boot as usual

On next reboot the Xserver should work fine


NOTE: if the problem is not solved try using "vga" instead of "vesa" and try again.


---

### Post by ajard on 2008-02-08
Thanks for the fast reply.. however, I tried both and it made it even worse. I couldn't even boot because the screen would just say "running local boot scripts" and then flash, over and over and repeat itself. I set my driver back to ATI, and it is working in failsafe mode again. Any other ideas?

---

