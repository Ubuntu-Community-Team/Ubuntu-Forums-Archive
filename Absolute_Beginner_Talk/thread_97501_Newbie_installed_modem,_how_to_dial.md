---
title: "Newbie installed modem, how to dial?"
date: 2005-12-01
forum: Absolute Beginner Talk
---

### Post by RhinoHornZa on 2005-12-01
Hi, I finaly got my modem recognised by Ubuntu, and used pppconfig to do the setup.  It still does not want to do the dial up.  What did I do wrong, what else to do?

---

### Post by Books on 2005-12-01
[QUOTE=RhinoHornZa]Hi, I finaly got my modem recognised by Ubuntu, and used pppconfig to do the setup.  It still does not want to do the dial up.  What did I do wrong, what else to do?[/QUOTE]

Hi! I just installed Kubuntu for the first time two days ago and had a real time getting my modem to work. Exactly what is happening? Is it trying to dial up and then disconnecting after the the handshake (the "SHHHHHHHHHHH" sound from the modem.) Is there an error message?

I don't know what pppconfig is yet. I used KPPP but on Kubuntu.

What kind of modem do you have? Is it a PCI card, an external serial modem, or a USB modem? Most (all?) serial modems will work since they are hardware-based. PCI/USB modems can be tricky. Some of them have drivers that really don't work all that well. Go over to [www.linmodems.org]("http://www.linmodems.org") and see if they have any info on your model.

When I was having difficulty I found quite a bit of information by searching this site for the words "dial-up" or "modem", selecting to search by titles only. One post had just the advice I needed.

Books

---

### Post by RhinoHornZa on 2005-12-01
I am using a PCMCIA modem and I cannot even make it give any dial tone

---

### Post by akiro.yamamoto on 2005-12-01
Click on:
System >> Administration >> Networking
A dialog will come up:
Highlight Modem ppp0
Click Configure
Enter you info, when your done click OK then click on activate...
Hopefully if all goes well... the status will change from Inactive to Active
All of this will work as stated as long as your modem really has been correctly setup....
If not you'll have to do some work before you get to this stage... :smile:

---

### Post by akiro.yamamoto on 2005-12-01
If you have a pci soft modem (AKA winmodem) you may still be able to get it to work .... check here for futher details....
[http://linmodems.technion.ac.il/](http://linmodems.technion.ac.il/)
Use the scanmodem utility to check your modem...

---

