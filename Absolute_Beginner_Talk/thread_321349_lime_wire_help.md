---
title: "lime wire help"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by troll380 on 2006-12-18
I have all of the current java and frostwire installed and it is launching. It just won't connect. It gets perpetually stuck in the "starting connection" mode while detecting a firewall that isn't there. I don't have a firewall installed on my home network directly and don't have one enabled on Edgy. FW worked fine under dapper but simply won't connect now. I don't know what the problem is. I tried a solution involving the gnuetella.net file suggested on the FW forums but that didn't work either. I'm at a loss. Anyone?

---

### Post by stsss8 on 2006-12-18
```
sudo apt-get install firestarter
```
It lets you monitor your firewall, and you can allow Frostwire to connect with that tool.

Edit: Here is some further reading about it if you have problems. [http://www.ubufied.com/2006/11/12/how-to-install-a-firewall-in-ubuntu-linux/](http://www.ubufied.com/2006/11/12/how-to-install-a-firewall-in-ubuntu-linux/)

---

### Post by troll380 on 2006-12-18
ok i have  fire starter now how do i use it

---

### Post by stsss8 on 2006-12-18
> **troll380 said:**
> ok i have  fire starter now how do i use it
Read that link I posted.

I had the same problem when I first started using Frostwire on 6.10. If Frostwire is blocked, you'll see a huge repetition of the same event under the 'events' tab. Right click it and select 'Allow Connections From Source.' Restart Frostwire (make sure you completely close it) and it should connect.

---

### Post by hodad on 2006-12-19
I'm having the same problem with Firestarter. I've been trying for two days to get rid of the firewall brick wall icon in order to enable connections.  Tried  your suggestion , but it doesn't work in my case.  Have tried many suggestions I've come across on this and Frostwire sites to no avail.  I see IP addresses scrolling by in the "connections" tab, but also get a notification that I'm "starting the connection" that never goes away.

](*,)

---

### Post by cheezewiz25 on 2006-12-19
I had the same problem with mine when i installed Frostwire last week.  I'm completely new, however, I discovered that I had to set the port to open on my router through my XP machine that the router is configured through.  I knew nothing on opening ports but tried to set port 6749 I think and set the program to use that port.  Works great so far.  Maybe that will help?

---

