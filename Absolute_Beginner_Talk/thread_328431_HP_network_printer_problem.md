---
title: "HP network printer problem"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by philip360 on 2006-12-30
Hi, I cannot get my hp printer to work. I have dapper i386 on my desktop which has dual boot with win xp. This is connected to a D-link DSL-604+ adsl router. My hp deskjet 6840 is also connected to the router. I originally set it up with Windows and it works well when booted in xp.
I have not found other posts that are helpful to me (I'm not very computer literate)

Internet works fine.

I have done the install new printer, selected "windows printer (smb)" and put in the url for the computer and printer. When I selected the printer model I clicked on the "install driver" button, but did not know where to put it. so I clicked cancell. When I click "print test page" the print icon is on the top task bar and there is a job listed, but nothing....

If anyone can help or recommend where to get easily understood instructions that would be super. Philip

---

### Post by toorima on 2006-12-30
instead of smb, chose lpd, add ip for router in host and in queue you need to put something, you probably find it in the routers manual, or in your config in windows, I have an asus router and have LPRServer in queue. 
With a HP printer you shouldn't have to install a driver, can't you find you printer in the list?

---

### Post by philip360 on 2006-12-30
Yes I did find the printer on the list and it showed the driver, I justdidn't know if I had to also install it. I will try your other suggestions. Thanks, P

---

### Post by philip360 on 2007-01-05
I have solved my printer problem and my HP 6840 now prints!!!!!
Here are a few notes that I hope may be helpful to others in the future. Philip

I spent 4 days reading forums, documentation, websites and none helped me or educated me to solve my problem of making my printer work

The result was discovered by trial and error.

1. Uninstall printer: System=>Administration=>Printing=>Password, Right click on printer icon, click remove icon

2. In the Printers window from step 1 I clicked on Global Settings and Detect LAN printers. Click yes I accept the risk

3. Same Printers window. Select Install New Printer
    Select Network Printer
     Select HP JetDirect Printer.

    I never discovered how a person would know how to decide to select CUPS, SMB etc. I tried them all and in my case HP JetDirect worked.

   Connection: Host: 192.xxx.x.x (I put in the IP address for the printer here-numbers only) I got this address  by printing a report from the printer.

                      Port: 9100  (this was already filled in)
  
  Printer Model: Selected HP, Deskjet 6840 
     On the bottom of this window it said: Driver hpijs (recommended) HPLIP (Suggested)
    I did not click Install driver as I could not select one or the other.

  General: The window here showed the printer model and I guessed the fields available were text fields, so I put in 
   Description: thePrinter
   Losction:  besidemydesk

4. Print test page: Success!!! 2 weeks into linux I have a printer! A moon shot next???

5. I de-selected Detect LAN printers from step 2 to see if that step was necessary- still prints

I have no duplex printing and I read on the net that the HPLIP driver has that functionality but I don't know how to do that....

I gave each step in a very basic and un-sophisticated manner in hopes that it is descriptive enough to help other green users that don't know all the basic assumed stuff in all the documentation. Cheers Philp

---

### Post by tribble222 on 2007-01-10
Thank you philip360!  Worked great for my Deskjet 6980

---

### Post by philip360 on 2007-01-10
> **tribble222 said:**
> Thank you philip360!  Worked great for my Deskjet 6980

Glad the info could help you. I still have not switched drivers to get duplex printing. I have not had time to track down how to do it. When I do I'll post. If you do please post, I'll stay subscribed to this thread. Philip

---

### Post by Neil Woolford on 2007-01-11
You should be able to set duplex (two sided) printing on the 'paper' tab in the properties dialogue for the printer.  You get this by right clicking the printer icon and selecting 'properties'.

Lots of other things like default paper size and printing qualities are set here too.

Neil

---

### Post by 11hjpphty76lkjj on 2007-01-12
> **philip360 said:**
> I have solved my printer problem and my HP 6840 now prints!!!!!
Here are a few notes that I hope may be helpful to others in the future. Philip

I spent 4 days reading forums, documentation, websites and none helped me or educated me to solve my problem of making my printer work

The result was discovered by trial and error.

1. Uninstall printer: System=>Administration=>Printing=>Password, Right click on printer icon, click remove icon

2. In the Printers window from step 1 I clicked on Global Settings and Detect LAN printers. Click yes I accept the risk

3. Same Printers window. Select Install New Printer
    Select Network Printer
     Select HP JetDirect Printer.

    I never discovered how a person would know how to decide to select CUPS, SMB etc. I tried them all and in my case HP JetDirect worked.

   Connection: Host: 192.xxx.x.x (I put in the IP address for the printer here-numbers only) I got this address  by printing a report from the printer.

                      Port: 9100  (this was already filled in)
  
  Printer Model: Selected HP, Deskjet 6840 
     On the bottom of this window it said: Driver hpijs (recommended) HPLIP (Suggested)
    I did not click Install driver as I could not select one or the other.

  General: The window here showed the printer model and I guessed the fields available were text fields, so I put in 
   Description: thePrinter
   Losction:  besidemydesk

4. Print test page: Success!!! 2 weeks into linux I have a printer! A moon shot next???

5. I de-selected Detect LAN printers from step 2 to see if that step was necessary- still prints

I have no duplex printing and I read on the net that the HPLIP driver has that functionality but I don't know how to do that....

I gave each step in a very basic and un-sophisticated manner in hopes that it is descriptive enough to help other green users that don't know all the basic assumed stuff in all the documentation. Cheers Philp


Philip,
Go to [http://hplip.sf.net]("http://hplip.sf.net/") and follow the instructions for installing hplip.  Once installed the hp-setup utility will run. Follow the instructions for installing a network printer.  Few clicks and you are done. :-D

A

---

### Post by philip360 on 2007-01-12
Hi guys. Neil your suggestion worked; my printer prints in duplex mode. 

Kalosaurus, I guess my install must have put the HPLIP driver in after all. The install wizard is not clear which it installs. That was where my confusion was-not knowing how to check what driver something is using with ubuntu O/S.  I did not realize I just needed to find the tab to click to enable as Neil's suggestion indicated. Thanks for the help, Philip

---

### Post by stueyboy on 2007-01-15
Thanks for the info Phil. That worked a treat.

I have a HP PS2710 and I can't get it to connect to my PC by USB because for some obscure reason, my BIOS has an option to boot from a USB device and it thinks my printer has some sort of hidden OS in it!

So , I did the jet direct install and instant success, so mucho kudos as that was the last thing to get sorted after getting Beryl latest version to run with my radeon card.

Ta

---

