---
title: "Set up as DMZ but STILL can't get thru router!"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by baylorbear on 2006-08-20
I set my router up to make my desktop the DMZ to receive all traffic that is unassigned... yet STILL no access to the server from the world-wide-web...

I am COMPLETELY lost on this one...

Please help!!

---

### Post by digby on 2006-08-20
> **baylorbear said:**
> I set my router up to make my desktop the DMZ to receive all traffic that is unassigned... yet STILL no access to the server from the world-wide-web...

I am COMPLETELY lost on this one...

Please help!!

Perhaps your ISP blocks incoming connections on port 80... it's not uncommon for that to happen.

---

### Post by baylorbear on 2006-08-20
Oops!  Sorry -- forgot to mention that part.

I called yesterday and then again today and they do NOT block any ports.

When I plug directly into the modem the server works perfectly -- on the router tho, nothing gets thru!

---

### Post by digby on 2006-08-20
> **baylorbear said:**
> Oops!  Sorry -- forgot to mention that part.

I called yesterday and then again today and they do NOT block any ports.

When I plug directly into the modem the server works perfectly -- on the router tho, nothing gets thru!
hmm... is the server pingable from outside?

---

### Post by baylorbear on 2006-08-20
> **digby said:**
> hmm... is the server pingable from outside?

Yes, just tried it.

---

### Post by NetworkGuy on 2006-08-20
Can you run a port scan on your connection to see if port 80 is open.   There are several webiste (can't think of any right now) that will allow you to run a free port scan.

---

### Post by uberg on 2006-08-22
I just went through this recently.  The router is the Gateway to the internet and sets up a private network in your home.  Make sure that your computer is set up as DHCP.  Use Network tools to do this.

---

### Post by baylorbear on 2006-08-22
I've tried it both ways.  For the longest time I was trying it by your suggested method -- and more recently, (since my router is configured to assign my computer the same IP every time), I told Ubuntu that it uses a static IP address...

This still did not work.

---

