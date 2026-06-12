---
title: "How to share a printer with windows PCs via wireless?"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by noo2bunto on 2007-02-19
Hello.  I have an ubuntu based system acting as a server for a wireless network.  I am interested in conencting a printer to it, and then making the printer available to a set of  windows based computers via the wireless network.  Essentially, I want to share a printer I plan on connecting to my Ubuntu based computer with other windows computers via an already established wireless connection.

Can someone please point me to a step-by-step tutorial on how to do this?  Or if, youhappen to have instructions, I'd appreciate that too...Thx in advance.  noo2bunto

---

### Post by chaplanger on 2007-02-19
Here is a  a tutorial to check out that I found helpful [https://help.ubuntu.com/community/NetworkPrintingFromWin2000](https://help.ubuntu.com/community/NetworkPrintingFromWin2000)  + some other settings information in the attached documeny (.odt format) that need to be looked into and understood.  This is a very helpful tutorial and goes into wonderful detail in how to accomplish this.

Check out the attachment as it tells how to correctly identify your machines IP address and an essential line needed in cupsd.conf.  Without knowing this, it just won't work. 

Post back if you need more assistance.

---

### Post by noo2bunto on 2007-02-20
Alea iacta est 

That was fairly easy.  Which brings to mind a question related to the warnings I got while making the printer available for sharing.

Aren't there any risks to having port 631 listening for inbound traffic?

---

### Post by The Mekon on 2007-02-20
I share my printer over a wireless network with two Windows PCs and there are security risks.  To minimize these I have set up my router to limit access to port 631 to local computers only.

I googled "port 631" and found numerous links.  The following gives a summary of the risks:

[http://www.seifried.org/security/ports/0/631.html]("http://www.seifried.org/security/ports/0/631.html")

Brian

---

### Post by chaplanger on 2007-02-20
> **The Mekon said:**
> I share my printer over a wireless network with two Windows PCs and there are security risks.  To minimize these I have set up my router to limit access to port 631 to local computers only.

Thanks for the warning.
So . . .  what specific steps did you take to accomplish this in Ubuntu?

---

### Post by noo2bunto on 2007-02-20
Do you have any guidance on limiting access to specific computers?

---

### Post by tgalati4 on 2007-02-20
CUPS CUPS CUPS
You can limit access to specific IP addresses (local or wide area)
The big risk is having someone send printouts from outside to your inside network.  There are plenty of posts in the forums on how to set up CUPS securely.  It has worked well for me over the past couple of years.

I can share windows-connected, network-connected, and mac-connected printers and even print from remote sites (friend's house for instance).  Once you master CUPS, printing becomes easy.  Wireless printing is just an extension of the network and really doesn't affect overall security--assuming you have rudimentary wireless security--WEP or WAP.

---

### Post by tgalati4 on 2007-02-20
My four years of Latin:  Alia iacta est   "The die has been cast"

[http://www.denelder.com/den/alia_iacta_est.html](http://www.denelder.com/den/alia_iacta_est.html)

---

### Post by noo2bunto on 2007-02-21
:)

---

