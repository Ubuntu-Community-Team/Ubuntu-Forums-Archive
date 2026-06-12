---
title: "Adding a subnet"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by quarkhirad on 2008-02-14
I have created a file server. Using samba. Now it is on a private ip. Now its ip is x.y.a.z. Now i want it to be accessible even on the b subnet. Hence i typed in the terminal sudo /sbin/ifconfig eth0 add x.y.b.z . Now i can access it through all the computers connect to my network with subnet a and b. 
Now the problem is if i restart my network it only gives access to computers connected on subnet a. I have to manually add the subnet b. What do i do so that even after restarting the server it automatically adds the subnet b.

---

### Post by yaraju on 2008-02-14
Hi Khirad, 
I belive the first FAQ on [http://www.faqs.org/docs/Linux-mini/IP-Alias.html](http://www.faqs.org/docs/Linux-mini/IP-Alias.html) answers your question. Only this was written for RedHat. IIRC, the same steps work on Ubuntu. Not on a Ubuntu box right now, but do give it a shot. If I notice it's different, I'll update on the thread. :)

Regards, 
Avanish

---

### Post by quarkhirad on 2008-02-15
Dear yaraju

I think it is different as when i browse the folder /etc/ there are folders named rc?.d where ? = 0,1,2,3,4,5,6. There is no directory called /etc/rc.d then within any of the folders rc?.d there is no file like rc.local. the file rc.local exists only in the /etc folder . However it has a comment that reads this file doesnt do anything. It doesnt look at all like the contents in the manual.

---

### Post by Trail on 2008-02-15
Use the file /etc/init.d/rc.local

The comment says it does nothing by default becuase it's empty by default. Add your piece of code right before the return statement, and it will be executed every time you boot.

So basically add your command to that file (without sudo).

---

### Post by quarkhirad on 2008-02-16
Dear trail thank you but what are the commands that i should type. And when you say without sudo what does that mean

Thanks

---

