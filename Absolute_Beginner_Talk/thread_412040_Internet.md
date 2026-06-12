---
title: "Internet"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by Robert98374 on 2007-04-17
Hello again everyone,
I love Ubuntu runs great on the computer and i have messed with some of the settings, now i would like to move on to connecting the computer to the internet to access more information and applications Etc. Where can i go to start the automaticly configure the internet connection? I dont use a Username or password its directly connected as soon as i plug in the cables. I tried the process listed [Here]("https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/connect-to-internet.html#internet-basic-procedure") and for some reason it looked like it all worked, i would then try Firefox and it said that i wasnt able to connect like i was offline. I understand that i am totally new to this thing and i probably missed a step somewhere but i am not sure where. Thank you for the help in advance :-)

---

### Post by Bachstelze on 2007-04-17
What kind of internet connection do you have ? Dialup, ADSL with USB modem, Ethernet ? Do you have a router ?

---

### Post by Robert98374 on 2007-04-17
As of right now i am using DSL, i am connecting directly to the modem through the ethernet port in the back

---

### Post by wuzzerd on 2007-04-17
I bet you have an Actiontec modem.  There is a bug in it that effects firefox in Linux.  This is funny because the modem runs on a small version of linux.

Ok try this:

In firefox enter about:config in the location.

In the filter enter ipv6.  

You should see network.dns.disableIPv6 under preference name.  

If Value = false, double click on the line and it should say true.

This should fix it.  

If it doesn't go into Network Settings.  This probably shows you are on the Wired connection.  

Select the DNS tab.

There should be two or three entries.  The one at the top is probably 192.168.0.1.  

Delete it IF it is not the only entry, which should be the case.

Hope this works for you.

---

