---
title: "Auto startup after power outage disrupts system"
date: 2024-02-12
forum: Apple Hardware Users
---

### Post by amitbloomberg7 on 2024-02-12
I have recently installed ubuntu 22.04 on my late 2012 mac mini (not dual boot).
recently there was a power outage while the computer was turned off (completly turned off - not in sleep mode) and it started up automatically when the power came back.
But, for some reason ubuntu didn't boot up properly and I have reached some sort of command line interface (not grub).
I have tried looking for some information about it but couldn't find much.
I was wondering what went wrong, and how can I prevent it in the future. additionaly, is there a way to turn off auto startup after power outage?
thanks you!

---

### Post by TheFu on 2024-02-13
This sounds like something Apple hardware specific.

---

### Post by amitbloomberg7 on 2024-02-13
I thought so, but I couldn't change the BIOS settings on the mac. The strange thing though, is that when mac os was installed it would only automatically boot up if the computer was turned on before the power outage. I don't know much about it as I'm new to the linux world, but maybe the computer doesn't shutdown completly with ubuntu?
Thanks for the help.

---

### Post by TheFu on 2024-02-14
Again, this sounds like something Apple hardware specific. 

Ubuntu shutdowns aren't like MSFT. They shouldn't leave things "open", at least on normal x86 hardware.  

Are you sure you are doing a full shutdown and not hibernating or going into standby?  There have been bugs where the shutdown doesn't actually complete.  

I've never seen that myself, but lots of other people have posted here they have shutdown issues.  Since there are millions of possible hardware combinations, I suppose that could happen and perhaps I've just be lucky never to see it.  

OTOH, I pick my hardware carefully and avoid hardware that isn't actually supported by the HW maker for Linux.  There are a few MS-Win PC parts vendors who are hostile towards Linux. We Linux people learn about them and stop giving them our money, even if their stuff has worked previously.

Anyway, perhaps this question is better asked in an Apple forum or in the Mac Hardware sub-forum here? I'm actually a little surprised a moderator hasn't moved this thread there already.

---

### Post by MAFoElffen on 2024-02-14
What happens if you press the Apple keyboard's <Option> key, right after the <PowerOn> key, then select the OS?

---

### Post by amitbloomberg7 on 2024-02-14
Well I'm pretty sure i did a full shutdown and the mac seemed to be off. It's an old mac no longer eligible for mac updates so i thought I would bring it back to life with Linux. I'm sorry for posting it here I didn't know that there was an apple sub forum and I've tried to look through the Apple forums but they aren't so keen on helping issues with linux there. I'll try to read more on the shutdown issues, thank you!

---

### Post by amitbloomberg7 on 2024-02-14
I only see the drive with Ubuntu, but there are not any settings I can change.

---

### Post by TheFu on 2024-02-14
> **amitbloomberg7 said:**
> Well I'm pretty sure i did a full shutdown and the mac seemed to be off. It's an old mac no longer eligible for mac updates so i thought I would bring it back to life with Linux. I'm sorry for posting it here I didn't know that there was an apple sub forum and I've tried to look through the Apple forums but they aren't so keen on helping issues with linux there. I'll try to read more on the shutdown issues, thank you!

No worries. Moving this thread to the Apple HW sub-forum isn't something you can do.

Now that MAFoElffen is in this thread, you'll get better help.  I suspect there are many Mac experts, but as I never read the Apple subforum here, I don't recognize any names.

---

### Post by him610 on 2024-02-14
@amitbloomberg7
Not to worry. You came to the right place. There are real experts that dwell in Ubuntu forums. They are patient, friendly, and very helpful. I have learned a great deal by just reading the issues and responses in these forums. 
Welcome to the forums.

---

### Post by ajgreeny on 2024-02-14
I have now moved the thread to **Apple Hardware Users** which as suggested is much more appropriate and a better fit for this query.

---

### Post by amitbloomberg7 on 2024-02-17
> **ajgreeny said:**
> I have now moved the thread to **Apple Hardware Users** which as suggested is much more appropriate and a better fit for this query.

> **him610 said:**
> @amitbloomberg7
Not to worry. You came to the right place. There are real experts that dwell in Ubuntu forums. They are patient, friendly, and very helpful. I have learned a great deal by just reading the issues and responses in these forums. 
Welcome to the forums.

> **TheFu said:**
> No worries. Moving this thread to the Apple HW sub-forum isn't something you can do.

Now that MAFoElffen is in this thread, you'll get better help.  I suspect there are many Mac experts, but as I never read the Apple subforum here, I don't recognize any names.


Thank you very much guys! 
Someone reffered me to this great article, and it solved the problem (or at least enabled me to turn off auto restart): [https://williamlam.com/2013/02/enable-auto-startup-after-power-failure.html](https://williamlam.com/2013/02/enable-auto-startup-after-power-failure.html)
There are 2 options:
1. Boot into recovery (cmd + R) then open terminal and type: pmset autorestart 0 (1 is on).
2. Inside Ubuntu, open terminal and sign into root (sudo su -) then type: setpci  -s 0:1f.0 0xa4.b=1 (there's another link in there for more information on this one).
It is still interesting why it autorestarted when the computer was initially turned off so I'll keep reading about it.

---

