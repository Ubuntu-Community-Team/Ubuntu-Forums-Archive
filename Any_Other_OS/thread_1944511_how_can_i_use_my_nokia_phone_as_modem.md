---
title: "how can i use my nokia phone as modem ?"
date: 2012-03-21
forum: Any Other OS
---

### Post by tahsin rahman on 2012-03-21
i use linux mint. how can i use my nokia mobile as an internet modem ? can anyone help me ? i am a new linux user

---

### Post by Mark Phelps on 2012-03-21
Don't know that is possible.

Looked into doing something like this when my Laptop couldn't connect to Verizon Wireless because their 3G network was down.  Verizon told me that although I could use my phone to call a number, I would require both "Dial Up Access" and "Tethering" -- the first to dial one of their ISP phone numbers, the second to connect my phone to my laptop -- and BOTH were plans I would have to PURCHASE.

So, even if it CAN be done in Linux, it's probably going to be expensive to do it.

---

### Post by ksa618 on 2012-03-21
It depends on which Nokia phone it is. On my old N900 I just had to choose "PC suite mode" when connecting it to the USB port, and Network Manager would recognize it as a modem.

---

### Post by Perfect Storm on 2012-03-21
Moved to Other OS/Distro Talk.

---

### Post by winh8r on 2012-03-21
This is an old guide but the principles should still be the same. probably best to do a bit of digging around before you go doing anything drastic though!!

[http://davesource.com/Solutions/20070520.T-Mobile-Nokia-E65-Ubuntu-Linux.html]("http://davesource.com/Solutions/20070520.T-Mobile-Nokia-E65-Ubuntu-Linux.html")

---

### Post by Paddy Landau on 2012-03-21
Would you be connecting via USB cord or Bluetooth?

I don't know specifics, but I managed to use my phone as a modem (it is not a Nokia). I will tell you what I did, and hope it helps you.

I successfully connected it via a USB and, when I had lost the USB cord, via Bluetooth.

**For USB cord:**[INDENT]There is an option in the phone to say what to do when connecting the USB cord; I chose to use the phone as a modem. In Ubuntu's network applet, I selected the phone, and it just worked.
[/INDENT]**For Bluetooth:**[INDENT]Likewise, there is an option in the phone to say what to do when connecting via Bluetooth; I chose to use the phone as a modem. When connecting from Ubuntu, choose to use the phone as a modem. Don't select the default plan, but select APN (you can find the correct setting in your phone) -- this is a one-off. Then select the phone from the networking applet.
[/INDENT]As I say, this is what I did, and it was easy. I hope it works the same for you. If you use Bluetooth, you may need different settings from mine; try the default settings first.

---

### Post by tahsin rahman on 2012-03-21
> **ksa618 said:**
> It depends on which Nokia phone it is. On my old N900 I just had to choose "PC suite mode" when connecting it to the USB port, and Network Manager would recognize it as a modem.

wow great,,,, thanx greatly,,,, i used mass storege mode previusly,,,, b8 today i selected nokia ovi suite mode and linux automatically detects my phone as modem,,,, thanx thanx,, now i can use my phone as modem,,, really amazing,,thnx

---

### Post by Paddy Landau on 2012-03-22
> **tahsin rahman said:**
> ... now i can use my phone as modem...
Fantastic. To help others who may have the same problem, please [mark the thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

