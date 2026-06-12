---
title: "Total Noob Here...Help With Network Card"
date: 2006-04-03
forum: Absolute Beginner Talk
---

### Post by MilkMoney on 2006-04-03
Hello. I have searched this issue thoroughly yet everyone's tutorials seem to complicated. My problem is I have recently tried installing Breezy Badger on an old 700 mhz pc I have. During the install process, the installation will not recognize my network card. This seems to be a common problem. From what I understand by reading other people's posts is that this is a driver issue. So I think to myself, oh sh&%, a driver issue. Ever since I began playing around with computers I have avoided driver issues because they are difficult for me to understand.

What I don't get is, if I can't connect to the Internet, how can I download the driver?

If I can connect with another computer, do I save the driver to a floppy disk?

Okay...where do I find the driver for linux for my card?

Once I have a driver, how do I go about installing it?

Please go easy on me. Explain it to me like I'm a two year old please. Thank you very much in advance for any help I receive on this isse.

~Milk

---

### Post by htinn on 2006-04-03
Wireless networking can be a chore to set up. You should probably start here:

[https://wiki.ubuntu.com/WiFiHowto](https://wiki.ubuntu.com/WiFiHowto)

---

### Post by Sweet on 2006-04-03
[QUOTE=htinn]Wireless networking can be a chore to set up.[/QUOTE]

Maybe an understatement!

Oh and you asked about getting native linux drivers for your card. Its not likely going to happen, so you can use a wrapper (ndiswrapper, etc) to use the windows drivers on linux. Anyway, read the HowTo posted above and you will see.

Good luck :)

---

### Post by dvarsam on 2006-04-04
I do NOT think the guy is talking about a Wireless Network Card.

I think he is talking either about a PCI Network Card or an Onboard Network...

Can you clarify, what type of Network Card you have?

1. Wireless
2. PCI, or
3. Onboard

P.S.> I do NOT know if "ndiswrapper" would work for Wired Network Cards...
        I think it works ONLY with Wireless...

---

### Post by jamesr on 2006-04-04
Also would you be happy to use the terminal commands. 
It may not a missing driver just the system needs a prod in the right direction.

---

### Post by MilkMoney on 2006-04-04
My apologies. Jamesr is correct. I call it a network card because that's what the error screen called it during the ubuntu installation. 

What is installed is actually a wireless B pci adapter. It is a Linksys 2.4ghz 802.11b (version 4). 

I have prior experience with terminal commands. In order to prod it in the right direction, I will need prodding first. Thanks for the tips so far, I have researched the links. I haven't tried anything yet because I am having difficulty pinpointing what is the problem, and thus, what is the solution.

---

### Post by MilkMoney on 2006-04-04
Sorry I should have said I have NO experience with terminal commands.

---

### Post by jamesr on 2006-04-04
Ok the first of the terminal commands. In one of the sections there will a terminal command window. Sorry about not being more specific but I do not know Gnome.

Any way once you have the terminal window open. Type the following commands```
sudo ifconfig -a
sudo iwconfig -a
``` and post the outputs.

With the sudo command you will need to enter the password that you setup during the install. The ifconfig & iwconfig get configuration about the interface (NIC).

---

