---
title: "[SOLVED] Broadband connection using BSNL(India) ADSL MT882 Gutsy and pppoe"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by ksbalaji on 2008-01-11
I have Ubuntu gutsy installed.  I have newly installed BSNL(India) MT882 ADSL modem with broadband connection
My dual boot windows XP (enviably) works smoothly with broadband.
However gutsy does not work with this ADSL modem.  I tried installing and running pppoeconf.  After a few clicks, I am shown

"sorry your ...cannot be configured... check your connections.... or another pppoe is controlling the modem"

I do not understand the message.  My hardware connections are OK with WindowsXP - The da... thing works (unfortunately with MSW..) Also I do not know how to find the other pppoe which controls my modem or to control it.  
Please help.

---

### Post by julian67 on 2008-01-12
can you not connect the pc to the modem via the ethernet port and then used the webbrowser based admin to configure it manually? Here's a link which might be useful:  [http://broadbandrouterconfiguration.blogspot.com/]("http://broadbandrouterconfiguration.blogspot.com/") You should just need the relevant settings from *your* ISP i.e. the various wan settings specific to that ISP. 

If you google MT882 ADSL you can find lots of good advice. That MT882 ADSL modem has built-in PPPOE/PPPOA dialing so it can work with any OS, but I expect the set up CD that comes with it is Windows only, but with a few minutes research and a call to your ISP for their settings you should be OK.

---

### Post by ksbalaji on 2008-01-15
Thanks julian67!  Your suggestion to configure the ADSL modem manually helped a lot. Now my ADSL works.  But  I have somehow simultaneously damaged my working dial-up modem configuration !  - one from the Reliance company.  I am trying to configure that manually too. I think I have erred when instructing a 'sudo ifconfig'.

Thanks  again for your words which prompted me to tinker with the configuration.

---

