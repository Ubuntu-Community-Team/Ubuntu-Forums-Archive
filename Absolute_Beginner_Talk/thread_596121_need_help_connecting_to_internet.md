---
title: "need help connecting to internet"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by fangorn752000 on 2007-10-29
Ok I'm pulling my hair out here!!! Ineed help connecting to the internet on my pc.  I just installed fiesty on my computer and it did not auto detect the settings like it did on the antique computer.  

the computer is kind of a recycled nightmare, but spec are as follows

  2.4g celeron processor
  compaq motherboard w/ integrated ethernet port
  router is a d-link di-604
  with mediacom high-speed cable internet

a step by step guide to do this would be helpfull and dumd it down as much as you can for me so I can get it right 

Thanx

---

### Post by scrooge_74 on 2007-10-29
open a terminal and type ifconfig  that should tell you if your card is recognize by the system, start from there

---

### Post by overdrank on 2007-10-29
> **fangorn752000 said:**
> Ok I'm pulling my hair out here!!! Ineed help connecting to the internet on my pc.  I just installed fiesty on my computer and it did not auto detect the settings like it did on the antique computer.  

the computer is kind of a recycled nightmare, but spec are as follows

  2.4g celeron processor
  compaq motherboard w/ integrated ethernet port
  router is a d-link di-604
  with mediacom high-speed cable internet

a step by step guide to do this would be helpfull and dumd it down as much as you can for me so I can get it right 

Thanx

Hi and welcome, please post the output of the command ```
lspci
``` 
In the terminal located under applications, accessories, terminal and this will identify your hardware and we may be able to help. And are you sure the onboard nic card is enabled in the bios of the system?

---

