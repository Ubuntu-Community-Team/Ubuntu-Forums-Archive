---
title: "Slow net connection etc"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by rapattack1 on 2007-03-01
Hi I installed Edgy on a friends computer and he has a wireless internet connection. I am not sure if the first time we connected that the speed was slow as I didn't have time to observe. After that which was maybe a week ago my friend has been on the net 3 or 4 times and it seems the speed is as slow as dialup. Also when he visits sites that need plugins like maybe Adobe flash there is no little green icon to show it is needed to be downloaded. I try to install it via the browser but it is taking way too long for it to detect that the plugin is needed. I went to download the player manually but the net speed was insanely slow. I use dialup myself but at that time of the download it was worse. Did I do something wrong when I was installing Edgy? Maybe it was because I installed Gnome PPP which is for dialup. I didn't know what to do for fast connections and should have done some research beforehand. Obvioulsy we don't connect via Gnome PPP but just by clicking onto the browser which I did by mistake and found that it was working so we use that method ever since to connect.
Also is there a program that I can get my friend that will show the speed of his connection as it happens?
Ok and the last thing is that I installed Skype but the GUI is just way too small. The lettering and the icons. I was able to fix the text everywhere else but how do you fix this within applications/programs?
Thanks would love some advice as I am still very much a newbie.

---

### Post by laidback on 2007-03-01
Had a problem with internet speed on a friend of mine's pc too. 
He was using DHCP, I switched it to DNS, wow, now super fast, in fact far better that with XP.

---

### Post by rapattack1 on 2007-03-02
Ah so is DNS that series of numbers that must be obtained from the isp he has? Then to be entered into the properties somewhere? I seem to remember doing something like that to speed up things back in the win3.1/win95 days. Is my memory correct?

---

### Post by xyz on 2007-03-02
If interested...
[Local DNS Cache for Faster Browsing]("http://ubuntu.wordpress.com/2006/08/02/local-dns-cache-for-faster-browsing/")

---

### Post by rapattack1 on 2007-03-02
Thanks for that page but it talks about cable/broadband and my friend has Wireless.

---

### Post by laidback on 2007-03-03
Yes correct, things like 195.164.226.8
My friend's isp actually uses DHCP, but when he was connected a dns number was evident in his networking configuration utility (I have no idea where it came from), I just used that, wow fantastic. Download speeds of around 400kb/s+ and vitually instantaneous web access. He pays for a 2Mb broadband line. It's been working like that for a number of months now, I can tell you he's really happy. Who wouldn't be.

---

### Post by rapattack1 on 2007-03-03
Yes I can even see dns settings when I go into System>Administration>Networking on my machine but will have to check what is on my friends machine that is questioning his connection. We will lose him back to windoze if he keeps getting annoyed so I want to solve this quickly.
So does my friend need to ring his isp if the dns numbers are not there and put them in manually somewhere?

---

### Post by Amenemhet on 2007-03-03
No, just choose dns, your friends isp should upload the address' for at least 2 dns srvers, although I had a few issues with dns on edgy a while ago , but only going through a private network. You should be ok. When I am at home it is fine. Also, if he is using wireless,(as I do) be sure that it is not the routers built in firewall that is choking the connection. If you choose dns and still have a problem, turn off the firewall, and see if that speeds things up, then you can turn it back on and set it to allow certain address etc. It could also be the isp, never forget...if a dns server is down somewhere that can reduce speed a lot. The domain name server basically translates the web page name you ask for, via your brouser, to an ip address. You could try pinging an ip address as well, just to test connection speed as well.

---

### Post by laidback on 2007-03-03
Might be an idea to use cable to start with as this eliminates one possible source of problems. Then move to wireless when you are more confident.

---

### Post by rapattack1 on 2007-03-03
This is a friends computer/connection and i think it would be a bit too expensive to pay for two internet connections.
I am the one that convinced him to go over to Linux and I think we will lose him back to windoze.

---

### Post by rapattack1 on 2007-03-05
Hi Amenemhet. Sorry I didn't read your response until now. How do I choose DNS? That is good thta you have had experience with Wireless as that seems to be rare outside of Australia. He has no network btw. It is a standalone pc. You mention a firewall well he hasn't installed one. I heard that Itables ....gee I think that is the name....runs in the background. Is that cool or are you talking about some other manually installed firewall?
I sort of remember what pinging is but it has been a long time. Can you please refresh me how and it may be different in Edgy than crappy old windoze.

---

### Post by Onurzaim on 2007-03-05
Thanks for the link xyz, it worked fine for me.

---

