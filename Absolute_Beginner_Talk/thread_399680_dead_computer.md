---
title: "dead computer"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by rshel on 2007-04-02
Hi,

Thank you in advance to anyone who can give me advice.

I awoke this morning to find that my Gateway desktop computer will not start.  Push the little power button, and the power button lights up. But nothing else.  Fan doesn't come on.  Nothing.  Just sits there.  I open the case and push the on button and see the fan spin once or twice and then stop.  Almost as if insufficient power is going to the computer.

So I chat online with a gateway tech, who tells me I should send it in to them since it is under warranty.  My concern is that since I dual-boot with Ubuntu and Windows XP pro, they will void my warranty, as HP does.  I would remove ubuntu before sending it in, but I can't get the thing even to the bios flash screen.   Does anyone know if Gateway (which does sell machines with Linux I think) will honor warranties with linux as the os?   Any suggestions for accessing the harddrive of a machine seemingly without power?  Would it be possible/worthwhile to go buy an external hd case, remove the harddrive from the computer and mount it in the case to access it from a different machine?

Any help/advice/answers appreciated greatly!


rshel

---

### Post by Parasitesss on 2007-04-02
according to experience, and I maybe awfully wrong, there is no way to access the HD of a machine the way you want it without the power.

Youre going to have to ask someone experienced, sorry.

---

### Post by taurus on 2007-04-02
If you have another computer, unplug the harddrive from the first computer, reset the jumper on the back to slave, connect it to the second computer, use gparted to delete the Linux partitions (from the LiveCD if you don't have Ubuntu running on the second computer), unplug it, reset the jumper back to master, reconnect it to the first computer (Gateway), and send it back for repair.

---

### Post by sad_iq on 2007-04-02
Does the (built in)speaker makes any sound when you start it up? If it does...count the times it does...that will tell us something...also..if you have an extra power supply try to replace it and see if it you can make it boot(I had a similar problem!!!)..if it still won't boot...remove every pci card, memory card and the like in your system (keep only the cpu and the video  card)and try to boot again...the speaker should beep...that's a good sign(again...count it if it beeps)!!!
 Hope we can get it up and running without any "specialized tech support"!!!

---

### Post by land0 on 2007-04-02
I Called Gateway and talked to a customer service rep. I asked her if I purchased a Gateway would it void the warranty if I installed Linux on my hard drive and she said no.

---

### Post by rshel on 2007-04-04
Thanks to everyone for the advice.  I also called Gateway and asked about linux voiding the warranty and they said the same thing:  the warranty was good for parts and service regardless of what operating system I had installed.  So I went ahead and sent it back with the hard drive as is.  If they don't fix it and blame Ubuntu, I will certainly post that information, and then we can properly vilify them for selling out to microsoft.   

But I will certainly keep in mind the advice from Taurus about removing the hd as well as suggestions from others.  They all sound like things that could easily come in handy one day.

Thanks again,

rshel

---

