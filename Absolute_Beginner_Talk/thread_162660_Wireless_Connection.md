---
title: "Wireless Connection"
date: 2006-04-19
forum: Absolute Beginner Talk
---

### Post by mrpositive on 2006-04-19
I guess I should have titled this differently before, and could not figure out how to change the title....so here is the re-post!!

I just received my copies of Ubunto 5.10...I ran the LiveCD for testing with my wireless card. Networking setup saw it with no problems as ATH0. So I say to myself "Self, this one will work without having to download drivers from madwifi or using ndiswrapper."

So I did the install...wiped my drive clean and upon finally getting logged in, the card (WG511U) was not recognized!!

VERY FRUSTRATING!!!!

Any assistance with this would be great, as from reading what others have said about using madwifi or ndiswrapper, it is just better to use the actual driver.

Thanks in advance.

---

### Post by taylork on 2006-04-22
If you right click on the Network Manager applet, you should still be able to configure it. That's what I have in my notes for when I configured it at least (I have the AR5212 card) in Breezy.

In addition, if you download the Dapper Beta CD, it will find it and allow you to configure it 5 minutes into the install. I would recommend doing that.

Also, with that madwifi driver, it was slow to connect to my ancient router. If that happens to you, you might want to consider setting it up to use a static IP. You'll need to know the IP of your router in this case and possibly a domain name server (that should be listed on your router's website page).

---

