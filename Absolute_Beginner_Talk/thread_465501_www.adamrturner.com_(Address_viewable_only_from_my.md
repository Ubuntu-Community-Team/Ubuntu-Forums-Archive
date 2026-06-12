---
title: "www.adamrturner.com (Address viewable only from my network)"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by A_Squirrel on 2007-06-05
I'm trying to set up a web server using Ubuntu inux and apache, I've got the server running and looks like it's working from my network, but when I call a friend's house and ask her to check it, it times out. What could be causing that? 

I set the permissions for the index.html for access from anyone, but it doesn't load outside of a computer on my network (I've checked three comp's on my network). I've got my router/modem set to single static IP for my server, and I forwarded the port, and I registered the domain with godaddy.com yesterday.

What am I leaving out?

The address is [www.adamrturner.com](www.adamrturner.com)

---

### Post by Phantom784 on 2007-06-05
Some ISPs, especially home ISPs, block incoming traffic on port 80 to prevent you from hosting websites on your home network.  I'd suggest renting a monthly hosting plan.  You could run apache on another port if you want to try that, too.

---

### Post by southernman on 2007-06-05
Are you using a static ip from your isp? 

If not you'll need to setup a (can't recall exactly atm) a dns forwarding account and create an a record with the service.

Works like a charm, back when I tinkered with this sort of thing...

found it again @ [http://www.zoneedit.com/]("http://www.zoneedit.com/")

Here is the site where I got all of my info on how to do this from home. [http://www.dslwebserver.com/]("http://www.dslwebserver.com/"), can't believe their still using the exact design (for lack of a better word) for this site. Must of been 7 - 8 years ago. *sighs*

---

