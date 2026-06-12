---
title: "Dsl router/modem wont connect"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by viking1au on 2007-09-25
Have a Seimens Speedstream 4200 router/modem which works fine with Win XP. Try & try , but I can't get it to work with Ubuntu. Have already been to the HELP pages, printed them out & followed directions but no go. There are 2 online manuals for this modem, one for general consumption & one for those (like me) who are connected via Optus. Both book versions are to be found here:
[http://www.siemens.com/index.jsp?sdc_p=lo1272700umc9dnsfp](http://www.siemens.com/index.jsp?sdc_p=lo1272700umc9dnsfp)
If you look down the left of the page, you will have links to both book versions.  Router connects to the 'net o.k.; suspect it is between the O.S. & the router.  Totally flumoxed!

---

### Post by kyphi on 2007-09-25
There is nothing wrong with your Siemens Speedstream since it works with another operating system. Therefore the solution lies with your network configuration in Ubuntu.

Go to System, Administration, Networking and insert the appropriate parameters (Hostname, Domain name, etc).    Then go to Properties (still in networking) and ensure that 'Enable this connection' is ticked.

That should do it.

---

### Post by viking1au on 2007-09-26
Na! That does not do it. There seem to be some differences. I notice you have Ubuntu 6.06; I have 7.04. There do seem to be differences with the instructions you gave. Anyway, it has been a month now, just trying to connect, and it is starting to look like something not too worthwhile. One puts all this effort in for zero out the other end and guess what?????? One gives up. The DHCP  SIMPLY DOES NOT WANT TO CONNECT WITH THE MODEM. tHE LAST RESORT WILL BE TO PRESS THE RESET BUTTON ON THE MODEM.   That is real desperate stuff, but I am down to that!!!!!!!!!1

---

### Post by kyphi on 2007-09-26
The configuration of your modem has nothing whatsoever to do with what operating system you use.  If you can acees the internet via XP on this modem then it is already configured.  You just need to set a few parameters for Ubuntu.

I ran a Speedstream 6520 for two years without any problem.

I run Ubuntu 6.06, yes, but I also have 7.04 here.

I will have a look to see how to configure this modem in Feisty and post a more detailed guide for you.

---

### Post by kyphi on 2007-09-26
Tried it in Feisty - procedure is the same.  The only difference is that in Feisty you can access 'manual configuration from the icon in the top panel but it leads you to the same screen as if you had gone via System, Administration, Network.

If your modem is configured to access your ISP (and you have said that it is currently working in XP) then Ubuntu should pick it up the connection automatically.

You only need to put the DNS numbers in, if they are not there already.  Check that they are correct.

---

### Post by viking1au on 2007-09-30
Tried and tried all that. It's dead in the water. Wondder if having the modem turned on and running when I loaded Ubuntu has upset anything?  Maybe my ISP is in cahoots with Microsoft, making things tough for Linux? Dunno. They are running DHCP and pppoe, but I do get very strange address info when I right click on the top right icon you mention, and click on properties or connection. The modem obviously works, but not with Ubuntu.

---

