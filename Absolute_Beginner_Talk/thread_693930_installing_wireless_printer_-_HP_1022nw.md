---
title: "installing wireless printer - HP 1022nw"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by halfhearted on 2008-02-11
I'm trying to set up a HP1022nw printer. The advice here -
[https://help.ubuntu.com/7.10/printing/C/printing.html#local](https://help.ubuntu.com/7.10/printing/C/printing.html#local)
assumes that I understand a lot of things that sadly I do not.
If I go System &#8594; Administration &#8594; Printing &#8594; New Printer
I am then faced with choices I don't understand -

Print into PDF file                       cups-pdf:/
LPT #1                                       Printer connected to parallel port
Windows Printer via SAMBA    smb://[workgroup/]server[:port]/printer
AppSocket/HP jetDirect             Hostname             Port number 9100
Internet Printing Protocol (ipp)   Host: Queue: URI:
LPD/LPR Host or Printer            Hostname:   Printer name:
Other                                         Enter device URI

It's obviously not the 1st, 2nd or 3rd choice (I hope). What on earth
is 'Host' or 'Hostname'? How do I find out what my Host or Hostname is?
How would I find the missing names in the SAMBA line? Thanks for any
help.

---

### Post by djbsteart1 on 2008-02-11
have you got hplip installed? if so it should be nie and easy. the printer is on a wireless network, so you choose the network option, 5, the wizard should display the name of you printer click it and follow the intructions. i am assuming here that the printer is connected to a router, if it is connected to another computer that runs windows, does the samba option give you any thing when you try it, if not i cant help much with that as i dont have any experience with samba. sorry. 
if anything needs more clarification then please ask.

---

### Post by halfhearted on 2008-02-11
What is hplip? How do I know if it is installed?The HP 1022nw is a wireless network printer. It isn't connected physically to anything. What does Host and Hostname mean? How do I find out what these things are in my system? As far as I know this is not a windows printer. Option 5 asks for Host, Queue and URI What are these and how do I find out what I should enter? Thanks for replying.

---

### Post by halfhearted on 2008-02-11
I can access the printers embedded web server through Firefox on [http://192.168.2.4/](http://192.168.2.4/)    Is this good? How does it help me install the printer? Thanks for any suggestions.

---

### Post by halfhearted on 2008-02-11
Simple question. What does hostname and host mean in the context of trying to install my HP 1022nw wireless printer please? Thanks.

---

### Post by stchman on 2008-02-11
> **halfhearted said:**
> I'm trying to set up a HP1022nw printer. The advice here -
[https://help.ubuntu.com/7.10/printing/C/printing.html#local](https://help.ubuntu.com/7.10/printing/C/printing.html#local)
assumes that I understand a lot of things that sadly I do not.
If I go System &#8594; Administration &#8594; Printing &#8594; New Printer
I am then faced with choices I don't understand -

Print into PDF file                       cups-pdf:/
LPT #1                                       Printer connected to parallel port
Windows Printer via SAMBA    smb://[workgroup/]server[:port]/printer
AppSocket/HP jetDirect             Hostname             Port number 9100
Internet Printing Protocol (ipp)   Host: Queue: URI:
LPD/LPR Host or Printer            Hostname:   Printer name:
Other                                         Enter device URI

It's obviously not the 1st, 2nd or 3rd choice (I hope). What on earth
is 'Host' or 'Hostname'? How do I find out what my Host or Hostname is?
How would I find the missing names in the SAMBA line? Thanks for any
help.

That printer needs the foo2zjs driver.

Do you have the printer hooked up to your wireless router?  Are you using wired or wireless?

I have scripts here to install the foo2zjs for Feisty or Gutsy.

[http://www.stchman.com/foo2zjs.html](http://www.stchman.com/foo2zjs.html)

There is very little documentation on the 1022 family of printers.

Try my scripts out and use gteweb ./1022

If that works let me know.

---

### Post by halfhearted on 2008-02-11
Very kind of you to go to the trouble. While I was away from the Forum I took a wild guess that it was the fourth option, namely, AppSocket/HP jetDirect which requires Hostname: and Port number 9100. I tried a Hostname of socket://192.168.2.4/ For reasons that I cannot even guess at it worked. HP does not provide a PPD file for this printer as far as I can see so I didn't pick that option. I chose the Foomatic/hpijs printer driver for HP LJ 1022. After a few re-boots it worked. What can I say. Hardly intuitive.

---

### Post by djbsteart1 on 2008-02-11
glad it worked. the hplip is hp's printing server. just incase you wondered. enjoy printing!

---

### Post by stchman on 2008-02-12
> **halfhearted said:**
> Very kind of you to go to the trouble. While I was away from the Forum I took a wild guess that it was the fourth option, namely, AppSocket/HP jetDirect which requires Hostname: and Port number 9100. I tried a Hostname of socket://192.168.2.4/ For reasons that I cannot even guess at it worked. HP does not provide a PPD file for this printer as far as I can see so I didn't pick that option. I chose the Foomatic/hpijs printer driver for HP LJ 1022. After a few re-boots it worked. What can I say. Hardly intuitive.

Ubuntu should have detected the network printer when you started the Printers manager.

---

