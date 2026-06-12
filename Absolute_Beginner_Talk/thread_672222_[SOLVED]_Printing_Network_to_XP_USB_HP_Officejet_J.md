---
title: "[SOLVED] Printing Network to XP USB HP Officejet J5780 All-in One"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by DutyDuty on 2008-01-19
Here is my situation: I am running Ubuntu on a Laptop in room A. There is a HP OfficeJet J5780 All-In-One in room B. This Printer is connected via a USB to an XP desktop, and is shared on the network which includes the XP, my Ubuntu laptop, two other XP laptops, and a OSX laptop. The XP laptops can print via this printer, as can the XP which it is directly connected to. I set up the printer in 7.04 and it printed. I upgraded to 7.10 and re-set it up when it did not work. It still does not work. I send the job and it is not acknowledged. Not blocked, just not noticed. I cannot print from either this laptop nor the Mac, but I'm only really concerned about this Ubuntu laptop. Yes, the XP box is on. 

I really need some help; this is becoming a huge inconvenience.

---

### Post by spiderbatdad on 2008-01-19
I struggled with a similar problem for a long time and never got it solved. The all-in-one I was trying to use had a default setting of "copy" the best I ever achieved was getting linux to send a job to it, then it would try to copy a document that wasn't in the copy tray, and spit out a blank page. I used the samba guide here:[https://wiki.ubuntu.com/ComprehensiveSambaGuide](https://wiki.ubuntu.com/ComprehensiveSambaGuide)

where file mode permissions are set. I think i had 1755, as 770, or what ever they show isnt a an octal and returns an error.

Good luck. hoping someone with some expertise pick up on this post, and helps you more.

---

### Post by randcoop on 2008-01-19
When you set up the printer, you'll need to print directly to its address.  So, for example, select SMB printer from the add printer window.  Then scan your network, remembering to scan the right addresses.  The default scan will probably be 127.0.0.1, but your network is likely either 192.168.0.1 or 10.10.10.1.  So correct the scan address before the scan.  Your system should then find the printer.

---

### Post by DutyDuty on 2008-01-19
Sorry, I must not have been clear. I see the printer and select it. In "Verify" it says "Inaccessible: This print share is not accessible"

---

### Post by randcoop on 2008-01-19
I misunderstood.  Sorry.  I don't have an answer for you.  Hope someone else comes up with something.

---

### Post by spiderbatdad on 2008-01-19
if the share is not accessible, then windows is probably not set up correctly. The guide i posted above is good for configuring windows to allow printer sharing with cups

---

### Post by DutyDuty on 2008-01-19
Nope, I followed the guide and got nowhere.

---

### Post by DutyDuty on 2008-01-24
bump

---

### Post by DutyDuty on 2008-01-25
re-bump

---

### Post by DutyDuty on 2008-02-02
Solved between some very long and boring manual setting up and a package from HP. 

Pleeeease let 8.04 not re-create the problem...

---

### Post by docker on 2008-03-10
Hey!

Could you place here the solution? I have the same problem... :(

---

### Post by AVH on 2008-03-19
Me too!
I had the printer working then up-graded to Gutsy and now can't print.
(Hp OfficeJet 6210)

---

### Post by AVH on 2008-03-19
I just found this thread. It solved the problem for me.
[http://ubuntuforums.org/showthread.php?t=683279&highlight=inaccessible](http://ubuntuforums.org/showthread.php?t=683279&highlight=inaccessible)

---

### Post by wpqc213 on 2008-03-21
What exactly did HP send that took care of your problem??
I am struggling with a F4140 AIO that is networked and connected to an XP Pro machine here. I have tried the downloads for drivers off the HP site ,which actually transfers to another site.  So far that has not worked either.

Thanks!

Wayne

Update to this..
I forgot to state that the printer share shows accessible.
The HP is connected via USB to the WIn XP machine.
I can see it and all that but I cannot get any drivers setup that will work this printer.
I have a Dell AIO connected the same way on another networked PC if that would work better I can use it

Wayne

---

