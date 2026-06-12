---
title: "Ethernet bug.. (works, with hard workaround)"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by Althares on 2007-10-20
Hi...

I'm connected to the internet through a wired ethernet connection. When I try to connect on windows, everything works. On Ubuntu though; it doesn't...  

I found a solution, but its really annoying;
When I'm logged into windows, I have to hard shut it off (hold the power switch), and then internet will work in ubuntu. If I just shut down normally, the internet doesn't work! 

Another thing I've noticed, is when I shut down windows normally, the ethernet light on my router goes off. When I use my workaround, the ethernet light stays blinking. I think the problem is that Ubuntu doesn't start up the ethernet, but I'm not sure.

Can anyone help me please?

Thanks...

---

### Post by Althares on 2007-10-20
Or.. is there any way (if my analysis is correct) to not shut off the ethernet as windows shuts off?

I've had this problem on 7.04 and 7.10..

---

### Post by Mr.Beast on 2007-10-20
> **Althares said:**
> Hi...

Another thing I've noticed, is when I shut down windows normally, the ethernet light on my router goes off. When I use my workaround, the ethernet light stays blinking. I think the problem is that Ubuntu doesn't start up the ethernet, but I'm not sure.

Can anyone help me please?

Thanks...

Hi, I'm not sure if this will be much help, but with most motherboards they now have a "wake-on-lan feaure embedded.  This allows the computer to be started over the network. The thing is that is's o/s independent.  you could try disabling this feature in your bios, or, alternatively perhaps it's to do with the power managment features of the motherboard.?

just some thoughts.

---

### Post by Althares on 2007-10-22
Thanks a lot; that worked!

---

