---
title: "Gutsy Gibbon: More dialup support?"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by Goregamod on 2007-11-25
As a dialup user, I couldn't stand feisty fawn, so I stuck with it for a week or two then retreated back to winblows.
In the latest version of Ubuntu, have there been any improvements to dialup support, or should I not hold my breath?

---

### Post by fenixphire07 on 2007-11-27
Hi Goregamod, I was in your same boat with 7.04 (Feisty Fawn). well I think you can take a nice deep breath now :-D

First, start up windows connect via your modem to the internet and then do this

 Start > Run > cmd
 this will open the MS-DOS Prompt
 enter the following code

 C:\ipconfig > ipconfigdata.txt
 
 this will save you IP CONFIGURATION in this txt file on ur C drive, make sure you have permission

 Next close cmd (exit) and open my computer > c: > ipconfigdata.txt
 
 check if the DNS Servers IPs are listed in there. Sorry i cant give you a copy of sorts coz my mac dnt have Windows running

 if you have it then awesome. The IPs will be the standard XXX.XXX.XXX.XXX format

 also check the dial up connections properties for username, password, dial tone (pulse or tone), and authentication type

 install ubuntu Gutsy Gibson and then do this


**You will need to know the following information: ISP Phone Number; Username; Password; Domain Name Server (DNS) addresses (the IPs).**

Important:  if you dnt have the above, dnt try coz you myt jus waste a lot of ur time

   1. Open Network Manager(System &#9656; Administration &#9656; Network)
   2. Select the Connections tab.
   3. Select Modem Connection
   4. Choose Properties and fill out the fields.
   5. Click OK
   6. Select the DNS tab.
   7. Click add, enter your DNS address.
   8. Click Close.

most probably this shud work. Please if you try this and it does add any more suggestions for others. Also if you have any problems post them coz Ubuntu is About Humanity towards Humans (i think)

Good Luck

PS. I'm not recommending that you install ubuntu on a dial up unless its relatively high speed (I'm only familiar with 56K modems). Coz Ubuntu relies alot on internet, for updating security risks, applications, repositories, etc. It myt be an unpleasant first few weeks with dial up. 

Think before you leap.

---

### Post by madjr on 2007-12-22
> **Goregamod said:**
> As a dialup user, I couldn't stand feisty fawn, so I stuck with it for a week or two then retreated back to winblows.
In the latest version of Ubuntu, have there been any improvements to dialup support, or should I not hold my breath?


install gnome-ppp patched:
[http://launchpadlibrarian.net/106924....24-1_i386.deb](http://launchpadlibrarian.net/106924....24-1_i386.deb)

bug report for patch found here:
[https://bugs.launchpad.net/ubuntu/+s...pp/+bug/121487](https://bugs.launchpad.net/ubuntu/+s...pp/+bug/121487)

also make sure you use a compatible modem or an external serial one
[http://www.amazon.com/Actiontec-USB-Serial-External-Modem/dp/B000EAQ08C/ref=pd_bbs_1?ie=UTF8&s=electronics&qid=1198353430&sr=8-1](http://www.amazon.com/Actiontec-USB-Serial-External-Modem/dp/B000EAQ08C/ref=pd_bbs_1?ie=UTF8&s=electronics&qid=1198353430&sr=8-1)

---

