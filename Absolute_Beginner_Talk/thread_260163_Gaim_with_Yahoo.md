---
title: "Gaim with Yahoo"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by shailbond on 2006-09-18
**[COLOR="DarkRed"][/COLOR]**I have been working on Fedora for last two years. I was having problems with Gaim so i migrated to Ubuntu. Everything works fine less Internet. Firstly firefox refused to open all sites. This i resolved by typing about:config and setting IPV6 rule to true. now firefox is working fine. However Gaim is giving proble. I cant connect to Yahoo as well as Jabber with Gaim. Theres some problem with Gaim. i am not sure what. Same problem was coming in Fedora Core 5 also. 
          Someone please help

---

### Post by Metacarpal on 2006-09-18
I routinely use Gaim to connect to my Yahoo messenger account.  What you're experiencing sounds like it's probably a firewall issue.  Are you behind a network firewall, or using a router with a built-in firewall?  If so, you may need to open a port to connect to your Yahoo account.

---

### Post by shailbond on 2006-09-19
I cant see a means to access firewall  settings in Ubuntu. Can u help

---

### Post by Brunellus on 2006-09-19
> **shailbond said:**
> I cant see a means to access firewall  settings in Ubuntu. Can u help
The problem is unlikely to be on the ubuntu side but further upstream.  Do you have a router?  What make and model?

---

### Post by DLWood on 2006-09-19
I had the same issue with Firefox and have the exact same issue as shailbond with Gaim.

For the FF issue, I disabled the ipv6 globally.  See:

[http://www.ducea.com/2006/06/01/disable-ipv6-module-on-default-kernels/](http://www.ducea.com/2006/06/01/disable-ipv6-module-on-default-kernels/)

I do have an ActionTec GT704-WG DSL modem/router which gives me all sorts of headaches.  Many things work OK as is, but others don't.  I've had to use port forwarding for several applications.  Is this what I need to do here as well???

Thanks,
DLWood

---

### Post by shailbond on 2006-09-19
No router no proxy nothing. I have a straight connection to Internet through Hub. everything else works fine. Cant get anything.Try an help

---

### Post by Brunellus on 2006-09-19
hub may equal router.

---

### Post by DLWood on 2006-09-19
I tried port forwarding my ActionTec router for MSN and AIM with no success.  It still just sits there when trying to connect.

I keep reading that Ubuntu is a closed system and there's normally no need for a firewall.  How then does anything get through?  I've searched all over the place and can't find out much on opening up ports.  How does one do this?

---

### Post by Metacarpal on 2006-09-19
I can use GAIM for AOL and Yahoo (haven't tried MSN or Jabber, as I don't have those accounts) on my Ubuntu install without having to open any additional ports - they're already open.

---

### Post by shailbond on 2006-09-20
i resolved the problem. There is some problem resolving ip addresses. I just pinged the addresses and got ipv4 addresses. Used these in account prefernces in lieu of normal addresses eg 123.456.789.123  in lieu of scs.msg.yahoo.com and rest all such addresses. it is working fine now. however i cant fetch room list for Yahoo.  Anybody else having problem please ping obtain valid id and replace address. It will work. It was actually painful but working now.

---

### Post by Brunellus on 2006-09-20
> **shailbond said:**
> i resolved the problem. There is some problem resolving ip addresses. I just pinged the addresses and got ipv4 addresses. Used these in account prefernces in lieu of normal addresses eg 123.456.789.123  in lieu of scs.msg.yahoo.com and rest all such addresses. it is working fine now. however i cant fetch room list for Yahoo.  Anybody else having problem please ping obtain valid id and replace address. It will work. It was actually painful but working now.
I am guessing that the most elegant solution would be to disable ipv6 globally.

---

### Post by Metacarpal on 2006-09-20
> **Brunellus said:**
> I am guessing that the most elegant solution would be to disable ipv6 globally.

Ah, I do so love protocol change transition periods...

---

### Post by DLWood on 2006-09-20
Hey, thanks shailbond, that was good thinking on your part.  I tried your solution and it works for me too....almost.  I can't ping "messenger.hotmail.com" ... I get no response.  Do you have the numeric IP address for Hotmail?   It works for Yahoo and AIM and Gmail.

I already globally disabled ipv6 (see above post), and Gaim still didn't work w/o making these changes.

Perhaps this is the problem I'm having with Evolution too....same or similar issue.  I'll try it and see.

---

### Post by DLWood on 2006-09-21
That solution also worked for my Gmail account using the Evolution email client.

I still can't get Hotmail to work.  It won't recognize the "messenger.hotmail.com" address.  If I ping it from WinXP, it returns a "time out" message for address 207.46.96.141, which won't work either.

Anyone else have a workaround for Hotmail?

---

### Post by shailbond on 2006-09-21
Thanks i got it with hit and trial only. Yeah this works with Evolution also. Also for update manager if its not reading from repositories you just have to change site addresses to ipv4 addresses in /etc/apt/sources.list and it works a breeze. I dont know this is a bug probably and i will submit it to Ubuntu technical forum as lot of guys are having same problem. Hotmail i cant also ping, so hope someone can help you.

---

