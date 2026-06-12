---
title: "Remote Desktop to Winodws"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by Black Mage on 2007-12-11
What can I use in Ubuntu to connect to a Windows Server 2003 remote desktop?

---

### Post by Joeb454 on 2007-12-11
Yep

Applications > Internet > Terminal Server Client

Protocol is RDP :)

---

### Post by wirah on 2007-12-11
Under Internet, choose "Terminal Server Client".

---

### Post by Black Mage on 2007-12-11
Ahhh, RDP, thnx. I kept trying VNC thinking that was it.

---

### Post by davidc502 on 2007-12-11
Just in case you need the syntax for krdc..

rdp://10.172.17.224

David

---

### Post by CaptainInsaneO on 2007-12-11
Well, you learn something new everyday! I didn't know this, glad to know it now though. I'm right in the middle of getting my MCSE certifications and was wondering if there was a Linux alternative to mstsc. Much thanks to everyone who posted replies and to the OP for posting the question for me. :)

(And no worries, I'm not some kind of MS spy for lurking around the Ubuntu forums just because I'm getting my MCSE... I promise it's for work. I still love you, Ubuntu!) :lolflag:

---

### Post by MetalMusicAddict on 2007-12-11
This is how my wife works from home and I set up 5 client machines at her work. Only the server runs windows. ;)

---

### Post by cmorse on 2007-12-11
A related question - going the other way.

I'm fairly new to Ubuntu and Linux in general - been running Edubuntu on an older machine at home for the kids and like it a lot.  I'm currently considering switching some of my XP machines at work over to Ubuntu but I'll need to have the same remote access that I currently utilize with RDP.  

What would I run on the Ubuntu machine that is equivalent to Remote Desktop Server that I could access from both Linux and Window machines?  I often need to log into my office machines from random WinDoze machines so need something reachable with a default client (RDP Client, or Terminal Client).

I haven't researched this fully, but since the question came up figured I'd ask while people were discussing it.  I've read a little about sshd - would this give me remote access to the gnome desktop from a remote windows client?

---

### Post by MetalMusicAddict on 2007-12-11
> **cmorse said:**
> A related question - going the other way.

I'm fairly new to Ubuntu and Linux in general - been running Edubuntu on an older machine at home for the kids and like it a lot.  I'm currently considering switching some of my XP machines at work over to Ubuntu but I'll need to have the same remote access that I currently utilize with RDP.  

What would I run on the Ubuntu machine that is equivalent to Remote Desktop Server that I could access from both Linux and Window machines?  I often need to log into my office machines from random WinDoze machines so need something reachable with a default client (RDP Client, or Terminal Client).

I haven't researched this fully, but since the question came up figured I'd ask while people were discussing it.  I've read a little about sshd - would this give me remote access to the gnome desktop from a remote windows client?

Id use VNC in this instance. You would have to have port-forwarding set up on your work router and you can connect to a work machine. On the work machine you would run x11vnc.

If you really want to get tricky, you can use X over SSH on a linux<->linux setup.

If you're in the states, PM me I dont mind doing a phone call if you're serious about doing this.

---

### Post by crjackson on 2007-12-11
> **CaptainInsaneO said:**
> (And no worries, I'm not some kind of MS spy for lurking around the Ubuntu forums just because I'm getting my MCSE... I promise it's for work. I still love you, Ubuntu!) :lolflag:

I doubt anyone would care.  I'm sure many MS employees use Ubuntu and I'd bet my hat even ol' Bill has tired it himself.

---

