---
title: "[SOLVED] Why does changing my network settings destabilize gutsy?"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by jlhs1971 on 2008-03-07
Hi all

I'm having a lot of problems with networking: whenever I change to roaming from manual configuration it seems to slow down and destabilize Gutsy. When I log in the next time, it goes into safe mode. Also, when i change to WPA encryption, my mac logs in without a sweat but my Gutsy system does not.  I'm running a dell d410 and am clueless as to what the problem is. 

many thanks in advance for looking and any advice

kind regards
julian

---

### Post by SloYerRoll on 2008-03-07
I think NetworkManager bytes.

If your interested in trying another solution. Try Wicd. I had a terrible time w/ NM and switched over to Wicd and it's been a breeze ever since. 

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

To get it to run at startup, add an entry to your session (System, Preferences, Sessions) click on "Add" then enter "/opt/wicd/tray.py" (minus the quotes) into the command line and name it whatever you want. 

(learned this from "jimv")

Best,

---

### Post by jlhs1971 on 2008-03-09
Thanks friend

I have followed your advice and installed Wicd and the good news is that it has at least stabilized Gutsy. Unfortunately, I am still having problems changing the settings on the wireless networks. As soon as i change the password or change to WPA from WEP, Wicd has problems connecting. This is really strange since the system can quite happily connect to other people's WPA or WEP network.


Any help or suggestions are gratefully received.

cheers
Julian

---

