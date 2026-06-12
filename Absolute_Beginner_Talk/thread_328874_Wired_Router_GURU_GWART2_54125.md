---
title: "Wired Router GURU GWART2 54125"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by davethesteam on 2006-12-31
Sorry, another newbie here who is completely befuddled with getting his nice new wired modem / router working on Edgy (BT as ISP).

Ethernet card is recognised (Netgear FA311 v2 - Linux compatible as advertised) and wired router also advertised as Linux Compatible.
Win XP Pro on original SATA drive - router and Internet working perfectly.

Ubuntu Edgy 6.10 on second SATA drive. Grub works fine.
Any ideas out there please - I have alreday downloaded ppoeconf but have since discovered that was probably unecessary!! This is my second day trying to get this resolved!!
Thanks for any help
PROBLEM SOLVED - SEE END OF THREAD

---

### Post by mayonaise15 on 2006-12-31
Go ahead and boot into Edgy and put these commands into the terminal, then reply here with what they output.

```
ifconfig
```
```
route
```
```
cat /etc/resolv.conf
```

I'm guessing that since you can't get your ethernet to work, you won't be able to copy and paste the output from the terminal.  Here is a trick you can use to redirect the output from a command into a text file:

```
ifconfig > ~/Desktop/ifconfig.txt
```
or
```
route > ~/Desktop/route.txt
```

That will save those as *.txt files on your desktop, so you can copy them to a flash drive and get them to another computer to post here.

Good luck

---

### Post by bigken on 2006-12-31
I had one of these I had to asign the dns server manually


[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=16474&d=1159448818[/IMG]

---

### Post by davethesteam on 2007-01-01
Thank you for your reply.
Finally, I can give attachments - read out from :
cat /etc/resolv.conf is:
nameserver 192.168.1.1
Best regards

---

### Post by davethesteam on 2007-01-01
Responses in main reply - thank you

---

### Post by davethesteam on 2007-01-01
All many thanks

Having spent a 3rd day on this problem, I am indebted to handy for his help with stabilising DNS addresse.
My fix was:
IPv^ (Firefox Fix

In firefox address filed: Enter **about.config**

Enter **ipv6 ** in the new **Filter:** field

Double click on the line left in the display window to change its boolean value to **true**

**Restart firefox**

Greatful thanks to all who offered help.

HAPPY NEW YEAR TO ALL UBUNTEANS - NEW AND OLD ALIKE!!!!

---

