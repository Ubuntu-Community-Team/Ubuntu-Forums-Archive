---
title: "Internet OR Browser problems"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by mmarif4u on 2008-04-13
Hi.
I am trying to connect to Wi-Fi internet.it connect well with out any problem.but i open my browser,its No page found.
i tried the same in windows pc,and it works well.
The problem here is browser cannot detect OR something other problem, which is out of my mind.
I open the network tools manager there i ping the ip address,it send packets and recieve also but browser and messanger cannot work.
Any solution for this.

---

### Post by Duckyspetrie on 2008-04-13
Do you have a firewall (Guarddog, for instance) enabled?

---

### Post by wormser on 2008-04-13
Sounds like this could be a DNS issue.  Try pinging by IP address and domain name.  If the IP works and the domain does not then its a DNS issue.

```
ping ubuntu.com
```
```
ping 91.189.94.158
```

I recommend using [OpenDNS]("https://www.opendns.com/start/ubuntu.php") to resolve this.

---

### Post by mmarif4u on 2008-04-13
Nope,i didnot install any firewall till to  now.

Yeh,maybe its DNS issue.I am still far from my laptop.
If this did  not solve the problem.
Then any other idea to solve it.

---

### Post by Duckyspetrie on 2008-04-13
Is there any way to connect to the internet/your router wired and see if you are able to access webpages? That way you could isolate it to definitely a wireless issue.

---

### Post by mmarif4u on 2008-04-13
I am not using my own router for internet.i am using a company wireless,which they provide in our hostel.
But the thing here is that the same network works fine on windows.
I have two systems,one ubuntu and other windows.when today i try to connect to internet by gutsy.it refuses.but when i try to use windows,it worked fine that time and after.
So i think the problem is not from router OR server.i think its in gutsy.

---

### Post by Duckyspetrie on 2008-04-13
Have you successfully used wireless before with that computer and OS on another router/connection?

---

### Post by mmarif4u on 2008-04-13
I also use ubuntu on saturday in my OFFICE.it did not work also there.that time i think,dat its may be the problem with internet in office.
But now also in my room with diff network cant work.and the other PC works fine using windows.

---

### Post by mmarif4u on 2008-04-14
i tried to change the DNS and update it,but no luck.
Any bodyu have any idea,how to solve it.
its frustrating now.

---

### Post by Duckyspetrie on 2008-04-14
What kind of network card do you have?

---

### Post by mmarif4u on 2008-04-14
i am using card bus wireless card.
B4 two days it was working fine.

---

### Post by mmarif4u on 2008-04-14
any help...

---

### Post by wormser on 2008-04-14
Try putting this into Firefox: 
91.189.94.158

---

### Post by mmarif4u on 2008-04-14
I put the ip address.FF is busy for some time.and after that stop working.
Mean no result at all.

---

### Post by ByteJuggler on 2008-04-14
> **mmarif4u said:**
> i tried to change the DNS and update it,but no luck.
Any bodyu have any idea,how to solve it.
its frustrating now.

Have you done the ping commands? What were the output.  What version of Ubuntu are you running?  Have you managed to install any updates yet?

---

### Post by mmarif4u on 2008-04-14
Yup,i tried to ping by terminal as well as from network manager.its fine.
I am using gutsy.my system is up to date.

---

### Post by mmarif4u on 2008-04-14
These things are now more frustrated for me.
Dunno how to solve it.

---

### Post by mmarif4u on 2008-04-14
Any one?

---

