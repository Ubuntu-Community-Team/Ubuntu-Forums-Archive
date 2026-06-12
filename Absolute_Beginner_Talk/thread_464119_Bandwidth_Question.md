---
title: "Bandwidth Question"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by taekwondodogoof on 2007-06-04
Hi,
      I have a bandwidth of 6500 kb/s down and 350 kb/s up from RoadRunner ISP. I've configured azureus with all the "good" settings from their Wiki, opened the port and tested with a port tester, done firestarter, disabled ipv6 and done a broadband tweak I found in the forums. Now my question is, why does having 30 kb/s up from azureus and 100 kb/s down choke my bandwidth if I have so much left over? Thanks!

---

### Post by khardbored on 2007-06-04
You only have 350k up and your uploading at pretty much max. Lower your upspeed to half its current and see if your bandwidth problem is fixed. I hve 800k up and if I used all of that, about 75-80k, im down to a crawl. So I set it to 40. Also, maxing your connections up speed -WILL- slow your torrents.

---

### Post by taekwondodogoof on 2007-06-04
Ok, thanks!

---

### Post by phr0ze on 2007-06-04
Yes, I think you are mixing terms here Kbps is usually how the cable companies measure speed, and KBps is how software usually measures speed. 

Also, you should not have to limit your download, If you find torrents coming in at 6mbps, let me know where. ;)

---

### Post by dfreer on 2007-06-04
I knew there was a difference between Kbps and KBps, but I never knew why you would ever user use Kbps. So when my Fiber Optic ISP says I have 3.0Mbps download speed, what should be the max speed I can download? Is there a reference chart or a conversion table?

---

### Post by phr0ze on 2007-06-04
Divide by 8 for the theoretical max in KB. They usually never provide 100% of what they advertise. I'm sure there is a reason they started with bits (probably cause that's what modems measured speed with.) but now I believe it's all marketing. One company says 3Mbps and another says 375KBps, most users would assume the 3 MEGA bit connection is better.

At dslreports.com they have a tools section which will tell you what you are getting assuming you have no other software or devices using your net connection when you run the test.

1 Byte = 8 bits.

EDIT: Most people just take 80% of the max when setting bandwidth caps in software. If you run at 100% you will stop other devices from using your connection.

---

