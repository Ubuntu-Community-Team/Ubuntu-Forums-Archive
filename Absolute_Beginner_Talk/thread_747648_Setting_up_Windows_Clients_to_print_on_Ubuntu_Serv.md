---
title: "Setting up Windows Clients to print on Ubuntu Server"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by mrpippal on 2008-04-06
I'm trying to set up a Lexmark 4200 printer as a network printer, with my VPR Matrix running Ubuntu as the client.  I also have a Mac Mini, and two laptops; one running Windows XP and one running Vista.

I was able to successfully install the printer and make it networked.  The Mac picked up the printer with no issue.  However, when I tried to connect with the windows laptops, I keep getting errors that the printer can't be found on the network.  I followed the instructions listed [here]("https://help.ubuntu.com/community/NetworkPrintingWithUbuntu"), and still no success - the windows laptops just won't recognize the printer.

I figure the networking must be successful, since the Mac had no issue picking up the printer.

I've spent hours reading and trying different things, and still have had no success.  I'm brand new to both Ubuntu and networking, so please bear with me,  Anyone know how I can get these windows boxes to see this printer?

---

### Post by motoperpetuo on 2008-04-07
i've heard that lexmark printers are notoriously difficult to use in a linux environment ("almost a no go" is the quote i remember), but i've never tried so i'm not sure. i did find this link that might help:

[http://www.soddengecko.com/09/2006/install-lexmark-printers-ubuntu/](http://www.soddengecko.com/09/2006/install-lexmark-printers-ubuntu/)

not sure if you've tried that yet.

---

### Post by mrpippal on 2008-04-07
Thanks for that info - I actually didn't have a problem installing the Lexmark on my Ubuntu.  This link on the forums was what helped me do that:

[http://ubuntuforums.org/showthread.php?t=83079](http://ubuntuforums.org/showthread.php?t=83079)

My issue is more related to getting the two Windows laptops I have to be able to see the network printer where my ubuntu box is the client.

---

### Post by motoperpetuo on 2008-04-08
this is probably a stupid question, but you've got samba installed, right? i think you'd need samba to get a windows client to see a printer on a linux server (which is the way you have things set up, if i understand correctly).

if you do have samba installed, are your windows clients able to access shares on your linux machine? i don't actually own a printer to test this directly, but i'm able to access shares on my linux machines from my windows machines no problem through samba, so i assume it wouldn't be much harder to access a linux printer. but then again, i'm barely above noob level, so who knows?

---

### Post by mrpippal on 2008-04-08
Thanks for that.  I spent some time last night installing and configuring Samba, but couldn't see it on my XP box (didn't try the Vista box).  I plan on fooling with it some more tonight.

It's very possible that I'm not doing something right from a network side, but my reason for thinking that might not be the case is because my mac pick up the new printer on the network right away.  I also don't think it's because my two laptops are connecting to the network via wireless, because I'm connecting to my network on the mac using wireless. 

I guess I'm confused too because in some docs I've read, it says you don't need samba to do a shared printer with ubuntu as a client.  I guess I wouldn't be surprised if I did indeed need to use samba for the shared printer, as it seems samba is the way to go for sharing with other windows boxes on your network.

---

### Post by motoperpetuo on 2008-04-08
i'm no genius with networking either, but when you mentioned that the mac client can see the printer and the windows clients can't, i thought samba. (i'm guessing that a mac, due to its unix-like nature, would have a better chance of seeing a printer on a linux server without any configuration.) have you been able to access shared folders on your linux box from the windows clients? if you can do that, you'll at least know that samba is working correctly.

if not, here's the link that taught me how to set up samba:

[http://ubuntuforums.org/showthread.php?t=202605&highlight=samba](http://ubuntuforums.org/showthread.php?t=202605&highlight=samba)

---

### Post by mrpippal on 2008-05-26
I solved part of this problem - I installed [firestarter]("http://www.funnestra.org/ubuntu/gutsy/#firestarter"), and now my windows machines are able to see the printer.  However, they are showing the printer as being offline.  I think the issue is related to the fact that every time I go into my CUPS Admin page, select "Allow Printing from the Internet", and then submit the chnged settings, when it refreshes, that box is unchecked.  I'm experiencing the same thing on the printer admin page.

Again, the mac is working like aces, so I'm not sure what the difference is between it and the Windows boxes.

Has anyone else experienced this?

---

