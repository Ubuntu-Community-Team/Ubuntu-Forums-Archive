---
title: "amule issues / internet connection!"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by TURNER on 2007-05-07
Hi all, 

Perhaps someone is kind enough to help me out of this pickle! :) 

I have recently downloaded and started using amule, no immediate issues with the program set up, and within a few minutes I had my first download under way...

however, whilst amule is connected and actively downloading, my internet connection fails, I basically receive the infamous connection time out error in firefox!

I am accessing the internet via a router (not wireless), and when amule isn't interfering it works faultlessly. 

any recommendations? Or perhaps someone can send me in the way of further reading?

thanks!

Dale

---

### Post by tbresson on 2007-05-07
What you are describing does not relate to the aMule application as far as I know.

I've experienced the same thing as you and there are a few things you can do to solve the problem.

1. The reason your connection fails is due to overload, I suggest you make sure your upload rate is below you connection limit, e.g. if you get 50 kb/s upload from your ISP, try not to set max upload in aMule above 40.

2. Check out the settings of aMule for the number of connections your PC can handle. It might be a good idea to lower the number of connections to give your router a break so it can handle all the traffic.

3. Buy a more expensive router. Cheap routers are usually cheap for a reason.

Hope it helps.

---

### Post by Hallvor on 2007-05-07
Sounds like a router problem to me. Try limiting the max number of connections and you should be fine. Also, test your router if it can drop connections a little faster to solve the problem. Too many connections at once will cause timeouts.

---

### Post by TURNER on 2007-05-07
Thanks for your feedback!

is there an easy way to administer the router within Ubuntu? or any CLI code you can throw my way?

---

### Post by Hallvor on 2007-05-08
Try typing 192.168.1.1 in a browser. Then type your login and password. (Check your router manual for defaults if you haven`t changed them.)

---

