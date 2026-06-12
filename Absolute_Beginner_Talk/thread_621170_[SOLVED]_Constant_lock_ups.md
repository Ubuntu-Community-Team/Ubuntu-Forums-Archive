---
title: "[SOLVED] Constant lock ups"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by POWERVICE on 2007-11-23
Hello,      
Please can some one tell me the definitive answer as to why my pc. keeps randomly locking every 20-30 mins when I try to use UBUNTU with the internet connected. It seems to be ok if I am not connected to the internet. I cannot clear the lock up (ie no mouse or keyboard) with alt+pri screen RSEIUB (other threads indicate this should clear a lock up). Sometimes the lock up eventually clears otherwise I simply switch off. I have previously posted a thread and after trying various recommendations people advised me to use an ethernet modem which I now have - Thomson 110 V6. This was ok for 3 hours and now the lock ups have returned. THE ACTUAL POINT OF LOCK UP SEEMS TO BE WHEN A NEW WEB PAGE IS BEING LOADED AND THE PROGRESS BAR IN BOTTOM RIGHT HAND CORNER SHOWS THE PAGE LOAD HAS NOT COMPLETED - does UBUNTU need some sort of delay for a split second to be added ????????
   I have tried 7.1 but that locked up and would only operate at limited screen resolution. I have now done a fresh install of 7.04 which still locks up. I have added all updates and it still locks up and also loaded the latest ATI driver using to no effect

My pc is 6 months old and has a win xp installation on one hard drive which has NEVER EVER  locked up
even though I use Firefox.


The only extra insoftware installed is  'ENVY' which automatically collects and installs updated drivers for my Radeon Xpress 200 graphics card. Lock ups occurred before ENVY was installed.

My basic pc spec is: Pentium 4 3.2ghz with 1 gb ram. with UBUNTU loaded on a brand new Seagate 160GB drive. I have ran memtest - no errors

 I am an ABSOLUTE BEGINNER  and am going to have to return to XP unless I can fix the problem. 

Thank you in anticipation    -------------- SIMPLY GO STRAIGHT TO THE END FOR THE ANSWER ------------

---

### Post by frank002 on 2007-11-23
Are you using Gutsy?

---

### Post by frank002 on 2007-11-23
Never mind. I see you went back to Feisty. Have you tried another browser like Galeon or Epiphany?

---

### Post by frank002 on 2007-11-23
I am assuming you use Firefox.

---

### Post by asmiller-ke6seh on 2007-11-23
This is a wild guess:

I am guessing that your system is not locking up, but that something in the web page is soaking up cycle time on your CPU.

You might want to open the system monitor and watch what is happening as you browse, and see if your memory usage shoots sky high when you experience the symptom you are describing.

---

### Post by POWERVICE on 2007-11-23
Thanks for your advice. I am using Firefox simply because UBUNTU came with it. Is there a fix for my problem do you think? or which of the other browsers do you recommend?

---

### Post by frank002 on 2007-11-23
Epiphany is a good browser. You can install it from Synaptic or go to 
Applications>Add/Remove Software and search for it. I was having problems with Firefox in Gutsy until someone suggested I disable IPv6. I did it and that solved the problem. However, in Feisty, Firefox did not have that problem. I hope this helps. Good Luck.

---

### Post by POWERVICE on 2007-11-23
Epiphany installed and locked up after 20mins with 10.9% cpu usage. Have had to switch off to clear.
Have set networkdns.disablepv6 to true and also to false in 'about:config' but lock ups occur with both.
After further investigation lock ups now appear to occur even when not accessing the internet. Ie they appear to be totally random.
Please can someone advise me what I should do to stop them

---

### Post by frank002 on 2007-11-23
I look at system monitor while browsing with Firefox and my cpu usage flucttuates from 9% to 11%..
 My RAM usage is 227Mb out of 1Gb. Have you seen how much of your RAM is being used? If I think of something else I'll post right away but now I'm out of ideas.  I am a newbie so I am not real knowledgeable.

---

### Post by POWERVICE on 2007-11-27
Ah well I have tried for 8 weeks. Fitted a new hard drive and new modem, installed Ubuntu 7.04 and 7.1 approx 10x and still cannot fix the lock ups. No one seems to know the answer so back to windows xp for me. If it is like this for everyone I really do not know how you can possibly continue!

---

### Post by stchman on 2007-11-27
> **POWERVICE said:**
> Hello,
Please can some one tell me the definitive answer as to why my pc. keeps randomly locking every 20-30 mins when I try to use UBUNTU with the internet connected. It seems to be ok if I am not connected to the internet. I cannot clear the lock up (ie no mouse or keyboard) with alt+pri screen RSEIUB (other threads indicate this should clear a lock up). Sometimes the lock up eventually clears otherwise I simply switch off. I have previously posted a thread and after trying various recommendations people advised me to use an ethernet modem which I now have - Thomson 110 V6. This was ok for 3 hours and now the lock ups have returned. THE ACTUAL POINT OF LOCK UP SEEMS TO BE WHEN A NEW WEB PAGE IS BEING LOADED AND THE PROGRESS BAR IN BOTTOM RIGHT HAND CORNER SHOWS THE PAGE LOAD HAS NOT COMPLETED - does UBUNTU need some sort of delay for a split second to be added ????????
   I have tried 7.1 but that locked up and would only operate at limited screen resolution. I have now done a fresh install of 7.04 which still locks up. I have added all updates and it still locks up and also loaded the latest ATI driver using to no effect

My pc is 6 months old and has a win xp installation on one hard drive which has NEVER EVER  locked up
even though I use Firefox.


The only extra insoftware installed is  'ENVY' which automatically collects and installs updated drivers for my Radeon Xpress 200 graphics card. Lock ups occurred before ENVY was installed.

My basic pc spec is: Pentium 4 3.2ghz with 1 gb ram. with UBUNTU loaded on a brand new Seagate 160GB drive. I have ran memtest - no errors

 I am an ABSOLUTE BEGINNER  and am going to have to return to XP unless I can fix the problem. 

Thank you in anticipation

You might have had a corrupt CD when installing.  I usually burn the .iso at 8X on my CD-RW.

My laptop has a Radeon Xpress 200M and all I did was enable the Restricted Driver.

I find Ubuntu far more stable than XP ever was.  In the 10 months I have been running Ubuntu (on 3 different machines) I have had only two lockups.

As far as Firefox locking up I get that as that is a Flash 9 bug.  Adobe knows about it but won't fix it.

---

### Post by Daveski on 2007-11-27
> **POWERVICE said:**
> If it is like this for everyone I really do not know how you can possibly continue!

Well clearly it is not like this for everyone. I am sorry this is happening though. Are you able to post the full spec of your machine, motherboard and BIOS so that if this is a bug, others can try to figure out what the cause is.

---

### Post by POWERVICE on 2007-11-28
Thanks for your replies. I made both disks (7.1 and 7.04 slowly - 4X). As far as I can now tell the lock ups are random and not internet related. My spec is Pentium 4 640 processor.
                                                            3.2 GHz 800 MHz FSB. 2mb cache
                                                             1GB DDR RAM
                                                             128MB ATi Radeon X200 graphics (restricted driver installed makes    
                                                                                                                                             no difference to lock ups)
                                                             phoenix award bios V6.00PG
                                                             rc410 series 594D3P11 090506
I have a Foxcon motherboard with on board graphics. I don't know whether the sound is on board as well
but the sound does not work and reading the forums it looks like sound is a very, very, very difficult subject. (is there an ABUNTU prog that will automatically sort sound like 'ENVY' does with graphics?).
 I hope all the numbers mean something and please let me know if the answer is doable for a complete beginner. Thanks

---

### Post by icechen1 on 2007-11-28
Maybe it is compiz-fusion's problem i had this too but i since i didabled some plugins,it fixed the problem.Try disabling disktop effects and see what it happens.

---

### Post by Dapman01 on 2007-11-28
did you run a mem test (I think that there is one in the synoptic) 
I know that bad memory can cause lock ups in some machines

I have personally never had a lock up in Linux, although firefox can become glitchy sometimes

---

### Post by Daveski on 2007-11-28
> **Dapman01 said:**
> did you run a mem test (I think that there is one in the synoptic) 
I know that bad memory can cause lock ups in some machines


Indeed, memory is a good place to check. There is memcheck option if you boot from either of the Ubuntu CD's you have.

---

### Post by POWERVICE on 2007-11-29
I have previously run a memtest for some hours and no errors were reported.
When I click on desktop effects, it says  'The Composite extension is not available' which I take to mean they are not installed so I guess I will not be able to disable anything. Remember I have a 7.04 install just as the disk with the exception of different ATI drivers installed by 'ENVY', all current 7.04 updates and epiphany and opera web browsers- that is all. By the way it still locks up about every 20 -30mins. Please if anyone does know the fix let me know as I am beginning to like the system but will have to return to windows as it is unusable because of the lock ups.
    I have moved to fedora and the lockups are still occurring. In a last ditch attempt I decided to flash my Foxconn BIOS fully expecting it not to work and completely destroy the motherboard. However after following the Foxconn instructions to make the appropriate bootdisk containing the bios update I managed to flash the BIOS in less than 2 mins. That was 2 days ago and Fedora has not locked up since. I can only presume with Ubuntu loaded I would also be lock up free. So for all you people with lock up issues this may be the first place to start bearing in mind that all the time you waste trying every other idea could buy a new motherboard if it fails. It seems to have worked perfectly for me!

---

