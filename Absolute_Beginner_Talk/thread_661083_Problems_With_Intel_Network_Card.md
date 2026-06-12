---
title: "Problems With Intel Network Card"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by Crumpets and Jam on 2008-01-07
Me again. Sorry about these stupid simple questions that I have.

After lots of preparation I am going am to install Ubuntu on my desktop. I booted into the Live CD have Linux Mint and booted up Firefox just to see if it worked. It did.

I then booted up the Live CD of Ubuntu 7.10 as this is what I have decided on intalling. I tried Firefox again but this time, I can't get a connection to anything. I suspect that Ubuntu can not detect my network card. Can anyone help me?

The card is an Intel PRO/100 VE.

Thank you to everyone.

---

### Post by candtalan on 2008-01-07
It sounds like you used firefox with mint and also got a connection ok to the internet? Is this true?

---

### Post by Crumpets and Jam on 2008-01-07
> **candtalan said:**
> It sounds like you used firefox with mint and also got a connection ok to the internet? Is this true?

No. It was just plug and play. I connected to the Internet no trouble in Mint. Nothing happened in Ubuntu though.

---

### Post by candtalan on 2008-01-08
Mint is based on ubuntu anyway so it is very strange that you should see such problems. Since mint works I would suspect the ubuntu CD. The live CD has a 'check CD' facilty in the initial boot menu - might be worth a try, it will verify both the CD and the drive reading it.
hth

---

### Post by peabody on 2008-01-08
When you booted ubuntu, what did the network manager say?  That's the little networked computer icon next to the clock.

---

### Post by Crumpets and Jam on 2008-01-08
> **peabody said:**
> When you booted ubuntu, what did the network manager say?  That's the little networked computer icon next to the clock.

Not at that machine right now. I'll check when i next get the chance.

---

### Post by Crumpets and Jam on 2008-01-09
> **peabody said:**
> When you booted ubuntu, what did the network manager say?  That's the little networked computer icon next to the clock.

Hmm. [This is what it looked like]("http://img81.imageshack.us/img81/5528/screenshotnl1.png"). When I hover my mouse over it, it says that I have a wired connection.

When I start up Firefox and try to get to Google, nothing happens.

---

### Post by Crumpets and Jam on 2008-01-09
Anyone got any ideas?

---

### Post by peabody on 2008-01-10
Did you right click the network manager?  Did you play around with its settings?  Did it say you had an ip address that was not self assigned? (such as 169.254.x.x).

---

### Post by gupta_sumesh63 on 2008-01-10
Your ISP should have given you an IP address, network mask, Gateway address and DNS addressess.
In Administration->Network tools check the configuration of your connection. 
Disable roaming and choose static IP address and then fill in the details about your connection. I think that shoul allow you to connect.

---

### Post by Crumpets and Jam on 2008-01-10
> **gupta_sumesh63 said:**
> Your ISP should have given you an IP address, network mask, Gateway address and DNS addressess.
In Administration->Network tools check the configuration of your connection. 
Disable roaming and choose static IP address and then fill in the details about your connection. I think that shoul allow you to connect.

I will give that a try and report back what happens. Thanks for the help.

---

### Post by gupta_sumesh63 on 2008-01-10
My mistake. Instead of Network tools change your configuration in System->Administration->Network.
Select the wired connection shown and click properties. There do the changes. Choose all the tabs in the window and change the default settings as per your details. 
Then reboot for the changes to take effect.
Then go to System->Administration->Network tools and check if the configuration has been updated for your network card.

---

### Post by Crumpets and Jam on 2008-01-10
> **gupta_sumesh63 said:**
> My mistake. Instead of Network tools change your configuration in System->Administration->Network.
Select the wired connection shown and click properties. There do the changes. Choose all the tabs in the window and change the default settings as per your details. 
Then reboot for the changes to take effect.
Then go to System->Administration->Network tools and check if the configuration has been updated for your network card.

OK, I am running it from a Live CD though so will the reboot set the changes back to the defaults again?

---

