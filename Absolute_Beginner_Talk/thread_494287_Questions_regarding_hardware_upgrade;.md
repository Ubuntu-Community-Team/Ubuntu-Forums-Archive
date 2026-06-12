---
title: "Questions regarding hardware upgrade;"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by _sAm_ on 2007-07-06
Today I changed the motherboard(msi to gigabyte), cpu(from AMD single core to Intel dual core), vga and ram. After I had done that I just booted from my Ubuntu disk as normal(without doing any thing). Ubuntu told me that something was wrong and did a forced check, and after that everything works as before(I guess): I am so impressed!! 

Question 1; since I have my home on its own partition I could easily do a fresh install. Are there any point in doing that?  (I would with windows). 

Question 2: Do I have to do anything about the dual core, or will Ubuntu know that by itself?

Question 3: How can I check witch nVidia driver I am using, and how can I see if that is the latest? 

Thanks for any help:D

---

### Post by pyros on 2007-07-06
> **_sAm_ said:**
> Today I changed the motherboard(msi to gigabyte), cpu(from AMD single core to Intel dual core), vga and ram. After I had done that I just booted from my Ubuntu disk as normal(without doing any thing). Ubuntu told me that something was wrong and did a forced check, and after that everything works as before(I guess): I am so impressed!! 

Question 1; since I have my home on its own partition I could easily do a fresh install. Are there any point in doing that?  (I would with windows). 

Question 2: Do I have to do anything about the dual core, or will Ubuntu know that by itself?

Question 3: How can I check witch nVidia driver I am using, and how can I see if that is the latest? 

Thanks for any help:D

That's rather cool : ) 

#1 If everything is working without malfunction, I see no reason to reinstall.

#2 my turion;s cores were both recognized without any configuration. If you want to be sure, go to System>Administration>System Monitor (or run gnome-system-monitor, same thing) and go to the resources tab. you should have a cpu history graph that shows two processors.

#3 If you are installing updates when the notice appears in the system tray, you should have the most current nvidia driver that's been packaged and reviewed.

---

### Post by _sAm_ on 2007-07-06
> That's rather cool : )  Yeah, you could try that with other OS :-) I just have to say it again; I am impressed! 

> #1 If everything is working without malfunction, I see no reason to reinstall. Ok, I need to try the it more before I know for sure – but so far everything works like it should(but faster then before cus the upgrade). Hmm, some buttons in "hardinfo" made it crash, I just have to see. 
> 
#2 my turion;s cores were both recognized without any configuration. If you want to be sure, go to System>Administration>System Monitor (or run gnome-system-monitor, same thing) and go to the resources tab. you should have a cpu history graph that shows two processors. Thanks, didnt think about that one. But that brings me to a new question; if you take a look at the picture, should it look like that?(mark, I am not doing any heavy lifting).
> 
#3 If you are installing updates when the notice appears in the system tray, you should have the most current nvidia driver that's been packaged and reviewed. I didn't know, so even closed drivers from nVidia gets updated from Synaptic? 

Thanks again

---

### Post by pyros on 2007-07-06
> **_sAm_ said:**
> Yeah, you could try that with other OS :-) I just have to say it again; I am impressed! 

 Ok, I need to try the it more before I know for sure &#8211; but so far everything works like it should(but faster then before cus the upgrade). Hmm, some buttons in "hardinfo" made it crash, I just have to see. 
 Thanks, didnt think about that one. But that brings me to a new question; if you take a look at the picture, should it look like that?(mark, I am not doing any heavy lifting).
 I didn't know, so even closed drivers from nVidia gets updated from Synaptic? 

Thanks again

hmm, yeah that looks a bit active,  You know, if you don't care about reinstalling, it might not be a bad idea.
*wonders what kernel package you have installed...

I belive the closed drivers will be updated with the rest of the system, assuming you installed through the restricted-drivers-manager. Mind you, that's just "official" (or official-unofficial) driver releases. mine has updated at least once, unless I was hallucinating. But with the poor quality of our city's water supply, that's not out of the question.

---

