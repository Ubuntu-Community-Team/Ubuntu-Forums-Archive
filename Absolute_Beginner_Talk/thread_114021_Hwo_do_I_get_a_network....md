---
title: "Hwo do I get a network..."
date: 2006-01-07
forum: Absolute Beginner Talk
---

### Post by JoeZ on 2006-01-07
How do I find some other computer that has Windows XP installed?
How do I transfer files etc.?

---

### Post by pbb on 2006-01-07
I'm a newbie myself also, but my understanding is that you need to have Samba installed to connect to Windows XP computers.

---

### Post by hbush on 2006-01-07
[QUOTE=JoeZ]How do I find some other computer that has Windows XP installed?
How do I transfer files etc.?[/QUOTE]

Hi, I am not really qualified, but I think you should see all the computers just like on windows network neighbourhod, workgroups and computers. 
I have ubuntu on my laptop and I can acces my desktop through Places --> Server Network --> and there you will see windows network. On your WINXP computer make a share folder read & write. 

hope this helps,
h

---

### Post by me3ohm on 2006-01-07
Hi,

I haven't got my Ubuntu computer in front of me (slowly upgrading from SuSE to Ubuntu at Home and Work) so I can't help with that side of things.  Just remember that if you have Service Pack 2 on your Windows computer, you will have to enable File Sharing as an exception in the Firewall properties - otherwise you will not see the computer at all!  

Hope this helps

Matthew

---

### Post by racecat on 2006-01-07
You also need smbfs. Note - I had to reboot after installing this to get it to work. You may also need smbclient. On the xp box, you need to share folders. Same on the Ubuntu box. You also need to set up smbpasswd. The Wiki will probably help with the specifics. I have kind of an odd setup - using 5.04 with Xfce and it's been awhile since I set it up.

Once it's set up, it all works pretty well, although I've found initiating things from the Windows box a little quicker.

Have fun!
Bill

---

