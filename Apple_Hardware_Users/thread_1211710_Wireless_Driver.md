---
title: "Wireless Driver"
date: 2009-07-12
forum: Apple Hardware Users
---

### Post by urkrnboy90 on 2009-07-12
I've recently installed the latest ubuntu on my (White) Macbook [intel].
Last time I did this the wireless card was recognized and I was able to connect via wireless. But now, I don't even see a wireless driver installed! How can i fix this? 

I've searched everywhere and am getting desperate...

---

### Post by pcrussell50 on 2009-07-13
i just asked the same question, and had the same circumstances.  i'm worried that you have no answer yet, because i'm afraid that means i won't get an answer either.

guessing this question is so old and remedial, most folks are tired of answering it... in which case, it should be a sticky... but it's not. :(

-peter

---

### Post by j.stam.84 on 2009-07-14
Personally I think that you guys don't get a reply because of the (lack of) information you're giving. For instance, what type of Macbook is it ? I'm no MAC-user but I could imagine there are different versions. What type of wireless card are we talking about ? (The MAC-mini from my parents has one with a Broadcom chipset fe). And not unimportant, what Ubuntu version are you using (I'm assuming Jaunty?).

Also, is the card being detected and what does Ubuntu do with it ? (execute 'lspci -v' and 'dmesg' and attach the output to your reply). I don't know both your experiences with Linux but if these commands look strange to you, I would *strongly* recommend to read a beginners guide, at least. That way, when (fe) another device fails on you, you could start debugging yourself! :)

Post a reply and let's get that wireless up-n-running :)

---

### Post by pcrussell50 on 2009-07-14
jstam,

thanks for showing some life to this question.  for the longest time, this thread we are in right now, was right next to [this thread]("http://ubuntuforums.org/showthread.php?t=1211922"), which is almost the same, except it DOES contain the information you are looking for.  It has been completely ignored.  It also happens to have been started by me.  the text from it is here:

> i have a perfectly functioning dual boot of leopard and ubu9.04 using refit. love it. 

but...

i know this has got to be buried somewhere in this mac users forum, [and i am inferring without knowing for sure that] i will need to do some sort of ndiswrapper solution, but i have no idea now to do it. is there a step-by-step walkthrough someone could link me to?

core2 duo 2.2Ghz, 1Gb ram, fully up-to-date leopard, 10.5.7, plain white macbook

thanks and regards,
peter 

i now happen to know that the wireless adapter is a broadcom bcm43xx, which i gather is the same family that's giving everyone else with current mactel laptops the same problem.  only at the time of my posting, i did not know how to find it.  now i do.

what else do we need to know to figure this out?

-peter

---

### Post by j.stam.84 on 2009-07-14
Peter,

If you have a Broadcom chipset, you have to extract the firmware from the windows driver. The firmware is uploaded onto the broadcomchip (instead of embedded) every time the module is loaded by the kernel. I think that's where things go wrong. It's illegal to distribute the firmware alongside Ubuntu so out-of-the-box, it isn't supported.

I say again: I THINK that's the problem.... you have to check /var/log/messages to confirm this.

But, as always, the OSS-community comes with an answer :). To enable this, you have to use a program called b43-fwcutter. It's available in the repositories, so you can just search for it using synaptic (GUI) or aptitude (shell). On install, it will automatically download the driver and extract/copy the nessecary .fw files.

Check your /var/log/messages and if it a firmware issue, try this. If it's something else, we'll look further. (btw. could you attach /var/log/messages to you next message please?)

Greets,

Jan-Jaap

p.s. One sidenote... With the PPC version, the bcm43xx module in combination with newer firmware don't play well with the stock kernel so I've got a /var/log/messages full of error messages. Compiling a custom kernel will resolve this (or so I've read...). I don't know if this bug exists on Intel.... If you have this bug, wifi will work a bit quirky until you compile your own kernel (if you don't know how, I'll help)

---

### Post by j.stam.84 on 2009-07-14
There's another thing I'd like to add... Normally on forums, people are very helpful. I think some people, and then I mean those who use "RTFM" a lot, don't see that some users don't know how and where to start.. Some don't even know how to really use a forum (believe me, I've seen this). 

That's the only explanation I can think of that your other post (and this one, for the most part) was ignored. I see this all the time...

Ubuntu is, in my opinion, at a place where it's accessible to utmost beginners (no offence Peter, I don't now your level of knowledge regarding Linux/Ubuntu) and we as a community, should react accordingly....

---

### Post by pcrussell50 on 2009-07-14
> **j.stam.84 said:**
> 
Ubuntu is, in my opinion, at a place where it's accessible to utmost beginners (no offence Peter, I don't now your level of knowledge regarding Linux/Ubuntu) and we as a community, should react accordingly....

no offence taken here :)

i can tell you exactly my level of knowledge.  that is the level where i can follow instructions exactly as they are given.  most of the problems i've encountered in my two and a half years with ubuntu and xubuntu, where the forums were of help, came from me cutting and pasting commands i find in the forums.  the example i like to give is the set of instructions for enabling multimedia [found here]("http://ubuntuforums.org/showthread.php?t=766683").  at any given time, i have both ubuntu and xubuntu on my desktop pc, and ubuntu and xubuntu on my mother's desktop pc, and i do a new, clean install of each shortly after each new version comes out... so, twice per year.  because all the parts of both my pc and my mother's are compatible with ubuntu/xubuntu linux, i have not had to face this problem.

i look forward to pasting up the results of my > /var/log/messages when i get home in a few days so i can get back on a cat5/lan cable so i can do this from ubuntu.  what is the exact syntax for the var/log/messages command, so i may paste it into my terminal?

regards,
peter

---

