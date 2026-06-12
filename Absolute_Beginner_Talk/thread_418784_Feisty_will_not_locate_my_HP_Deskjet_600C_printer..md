---
title: "Feisty will not locate my HP Deskjet 600C printer."
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by kittyhawk63 on 2007-04-22
I had my HP Deskjet 600C working in both Dapper and Edgy without doing one thing. Dapper and Edgy found my printer and the default drivers worked fine. However, I cannot get it to find my printer in Feisty. I ran ***hplip-1.7.4.run*** and got to the point of the program trying to locate my printer. It could not locate it. I have done nothing. It works in Windows/Dapper/Edgy. Why won't it locate it in Feisty? 

Any suggestions to get this printer working will be greatly appreciated.  

kh

Why can't Linux have a plug and play feature? Or does it?

[COLOR=Red][COLOR=Black] Edit: [/COLOR]I chose System -> Administration -> Printing and clicked the icon Add Printer -> I chose HP600 instead of HP600C and went with the default settings. Everything worked out okay.[/COLOR]

---

### Post by bloodniece on 2007-04-22
HAve you tried just manually adding the printer and choosing LPT1 as the port and whatever the CUPS driver is supposed to be.  I had to do that for my HP Laserjet 1018 after going to Feisty on my desktop install.

---

### Post by kittyhawk63 on 2007-04-22
> **bloodniece said:**
> HAve you tried just manually adding the printer and choosing LPT1 as the port and whatever the CUPS driver is supposed to be.  I had to do that for my HP Laserjet 1018 after going to Feisty on my desktop install.

Not sure what you mean by manually. I did go the System-> Admin-> Printing route. It didn't work. Is that what you meant by manually?
kh

---

### Post by 11hjpphty76lkjj on 2007-04-25
if you are using a parallel printer check this doc:

[http://hplip.sourceforge.net/troubleshooting/parallel.html](http://hplip.sourceforge.net/troubleshooting/parallel.html)

A

---

### Post by oilchangeguy on 2007-04-25
Kittyhawk, in another thread you mentioned that you were going to re-install 6.06. what happened?

---

### Post by kittyhawk63 on 2007-04-25
> **oilchangeguy said:**
> Kittyhawk, in another thread you mentioned that you were going to re-install 6.06. what happened?

olichangeguy,
I will have to try and find that thread. I have decided to forgo that for now. I have everything working again, except for the video. I am always getting a screen freeze after undesignated amount of time. I will keep working at it until I get it fixed.
Thanks for the inquiry.
kh

---

### Post by kittyhawk63 on 2007-04-25
> **kalosaurusrex said:**
> if you are using a parallel printer check this doc:

[http://hplip.sourceforge.net/troubleshooting/parallel.html](http://hplip.sourceforge.net/troubleshooting/parallel.html)

A

I'll check this out. Thanks.
kh

---

