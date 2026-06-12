---
title: "Program to send instant alerts/popups to LANed PCs"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2007-03-06
Hello!

I am looking to find a program that can send alerts to all LANed PCs.
This program should work on [color=red]Windows[/color], hopefully [color=red]Linux[/color] too, or **both** Platforms.

_Examples_:
1. An Administration wants to send an instant popup to all Clients to Reboot their PCs.

2. An Administrator wants to send an instant popup to all Sales Department Group that all Sales Department should meet in Sales Department Room in 10 minutes from popup.

_Clarifications_:
1. I don't care how much a program like this would cost (I am NOT paying for it - the company I work for will pay all costs involved)

2. The program must be able to create Groups for LANed PCs. Group creation would include: "Sales Dept.", "Warehouse Dept.", "Logistics Dept.", "All Dept.", etc etc...
In this manner, the Administrator could send an instant popup message to a Group of PCs & NOT to all LANed PCs.

3. Some people have suggested using MS Exchange Server, but it is NOT capable of sending instant messages... It just sends an Email - while I want a popup that shows up in the middle of your screen...
I.e. a user can ignore to read an incoming E-mail, but can't miss the popup showing in the middle of his PC screen.

4. Clients should NOT be able to send public messages - only the Administrator will.

Thanks.

---

### Post by compiledkernel on 2007-03-06
LinPopUp if your looking for the classic windows messenger style thingy.

---

### Post by dvarsam on 2007-03-06
[QUOTE=compiledkernel]LinPopUp if your looking for the classic windows messenger style thingy.[/QUOTE]

Can [color=blue]LinPopUp[/color] be installed in Windows too?
And can I create groups, so that the Popup can be customized to show only on the specific Groups selected?
Finally, is [color=blue]LinPopUp[/color] a program that only an Administrator could use?

Thanks.

---

### Post by compiledkernel on 2007-03-06
Linpopup mimmicks the classic interface to windows messeging ( a clone of winpopup the graphical interface to net send in windows). If the messenger service is enabled on a windows machine, they can recieve the messages you send via Linpopup. Additionally you can probably shell script out a bit for the use of smbclient (smbclient -M <machinename> does a similar thing as linpopup). But this is all pending on whether or not the messenger service is actually running. In the windows world some might consider this to be a vulnerability or a source of annoyance.

---

