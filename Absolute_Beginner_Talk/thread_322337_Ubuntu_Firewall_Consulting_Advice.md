---
title: "Ubuntu Firewall Consulting Advice"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by aznlnx on 2006-12-20
Hi guys... I have quite a number of computers at home.

Two pcs are running Ubuntu including an OSX and XP machine all behind a DLink router/firewall.

I'm not concerned about the Ubuntu and OSX machines security...but I am concerned for the XP machine. Reason why is the XP machine is running Pro Series 2006 that my roommate uses to file taxes.  IRS is requiring tax filing through the internet these days....but thats not what is important...

Which leads me to this question...

what do you guys recommend me doing in this scenario?

Should I place a linux or ubuntu firewall in front of the Dlink router?

I can really use some expert advice here.

Tax season is coming soon and I need to get this going.

Thanks so much :)

---

### Post by ashrack on 2006-12-20
Your current network configuration is OK.
All that U must do is secure Windows. Have a decent firewall, check for ADAWARE daily with AD-AWARE from lavasoft, antivirus is a must and with it u must have realtime scanning enabled(AVG GRISOFT is free, NOD32 one of the best I've tried), Windows must be updated thru WindowsUpdate, and use FIREFOX or OPERA instead of Internet Explorer, be sure U have a password set for your user account and files.

---

### Post by user007usa on 2006-12-20
> **aznlnx said:**
> Hi guys... I have quite a number of computers at home.

Two pcs are running Ubuntu including an OSX and XP machine all behind a DLink router/firewall.

I'm not concerned about the Ubuntu and OSX machines security...but I am concerned for the XP machine. Reason why is the XP machine is running Pro Series 2006 that my roommate uses to file taxes.  IRS is requiring tax filing through the internet these days....but thats not what is important...

Which leads me to this question...

what do you guys recommend me doing in this scenario?

Should I place a linux or ubuntu firewall in front of the Dlink router?

I can really use some expert advice here.

Tax season is coming soon and I need to get this going.

Thanks so much :)

In your case since you say you have many computers, I would look into IPcop or smoothwall.  These are essentially dedicated firewalls.  You will need 2 - 3 NIC cards for this.  Put your main network behind one -- router first, then computers from the router.  This is the GREEN zone.

While IPtables is pretty good, it is usually best to have a dedicated firewall from a security standpoint.

---

