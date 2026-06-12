---
title: "LAMP server on ubuntu behind Zoom X4"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by lilalfyalien on 2006-11-05
Hi,

I have setup a LAMP server, setup Apache to listen on port 8080, IP 10.0.0.26. I have set my static IP to 10.0.0.26. I can connect to the Internet fine using this IP so it's communicating with my Zoom X4 (my router). I have setup a "virtual server" on port 8080 via my router as for some reason the X4 likes to hog port 80 for it's admin web server. So in theory when I type in my WAN IP followed by 8080, shouldn't it bring up my apache server? Because it doesn't and apache is running. I thought at first that it was the Zoom X4 and I hadn't changed a setting but if I type in localhost:8080 on my ubunto box should it bring up the apache server too?

Does anyone have any suggestions as to why nothing is working? Also, it was working yesterday but then I turned off the ubuntu box and then it didn't work...?! Do I need to maybe change some other settings on my router or in apache?

Any help would be really appreciated it's driving me mad!

Amy

---

### Post by lilalfyalien on 2006-11-05
I just got it to work with localhost:8080 and 10.0.0.26 through my windows box but my WAN address:8080 isn't working. I imagine that this is my routers fault! Are there any other settings that I might need to change except seeting up a virtual server for port 8080?

Thanks,

Amy

---

