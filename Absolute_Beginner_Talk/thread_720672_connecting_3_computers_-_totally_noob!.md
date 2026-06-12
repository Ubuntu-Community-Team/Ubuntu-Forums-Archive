---
title: "connecting 3 computers - totally noob!"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by the_nomad on 2008-03-10
hello.
im sorry for this bilion'th thread regarding this issue but im totally noob to everything that means connecting computers via cables and so and so on...

ok here's the thing: i have 3 computers: my first (the one that has an internet connection via a LAN),my second one, and my mother's - last 2 DO NOT have internet access.
what i want to do is to connect them such a way that they can all access internet

a friend told me i should use a switch but i must be advised that what i want to do with my second pc (that is hosting 2 servers - one for unreal tournament and one for a website which of course i want them be accessible remotely) can't be done because the 3 computers will all have the same IP address

so: how do i connect them in such a way they meet all the conditions above? :)

many thanx!

---

### Post by imanoob on 2008-03-10
Buy a router. [HERE]("http://linksys.com")

---

### Post by Duck2006 on 2008-03-10
Use a router to connect the computers. 
What type of internet connection do you have?

---

### Post by Rocket2DMn on 2008-03-10
Using a router, you can forward the correct ports to the server computer's internal IP so it will appear to the outside world that your server is immediately at the public IP address.  Note that your IP will probably change when you put the router on the front end, unless you clone the server's current MAC address onto the router (which is sometimes possible through the software/web interface to the router).

---

### Post by dgray_from_dc on 2008-03-10
I agree.  A router will get an IP address from your ISP and then create an internal LAN off of which all connected PCs can get an internal IP address and connect to the web.

You can find them for under $30 if you hunt a little.

---

### Post by the_nomad on 2008-03-11
thanx alot for replying! i will try to look for some documentation upon what you've suggested me and if i face out some problems i will post them here....

---

### Post by hyper_ch on 2008-03-11
if you want to buy a router with wifi (in case one of your computers has wifi) then I'd go for a Linksys WRT54GL (and replace the firmware on it to use dd-wrt or tomato).

---

