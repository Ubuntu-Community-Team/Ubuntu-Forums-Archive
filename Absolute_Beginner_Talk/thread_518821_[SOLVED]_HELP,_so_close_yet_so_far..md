---
title: "[SOLVED] HELP, so close yet so far."
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by kennyn on 2007-08-06
I installed eponym, it works great. Now this is what I have.

If I go to [http://www.kennynproductions.com](http://www.kennynproductions.com) within my local network, it pulls up just fine. But I cannot get to that website outside of my network. I tryed many different browsers/computers outside my network last night and today.

Any Ideas on how to fix this. I seem to be so close yet so far.

I have my netgear router set to port 80 for HTTP. The thing I am worried about is that my ISP is blocking that port. I am not sure .

Where do I go from here is the question.

---

### Post by Dr Small on 2007-08-06
Did you enable port forwarding on your netgear router to port 80 and have it point to your internal ip of your server, and open your firewall to allow all incoming requsts on port 80 ?

---

### Post by kennyn on 2007-08-08
Ok, let just say I am there but just frustrated. I finally got my server to work. The downfall is my ISP blocks port 80, so I had to set my port to 81.

So if you go to: [http://www.kennynproductions.com:81](http://www.kennynproductions.com:81) you should get my website.

This is really agrivating, I dont want to have to put in :81 after it. Does anyone know how to disguise this or fix this without having to get a new domain and mask it to that address??

Thanks.

Also one more question, my current full time job blocks anything on 80, 81 etc. I know that they do not block 443. Any way of getting around this so that i can pull my website up here from work as well as everyone else in the real world still being able to see it??

---

### Post by igknighted on 2007-08-08
Try updating your DNS servers to point your domain name to your IP address:81

---

### Post by igknighted on 2007-08-08
> **kennyn said:**
> Ok, let just say I am there but just frustrated. I finally got my server to work. The downfall is my ISP blocks port 80, so I had to set my port to 81.

So if you go to: [http://www.kennynproductions.com:81](http://www.kennynproductions.com:81) you should get my website.

This is really agrivating, I dont want to have to put in :81 after it. Does anyone know how to disguise this or fix this without having to get a new domain and mask it to that address??

Thanks.

Also one more question, my current full time job blocks anything on 80, 81 etc. I know that they do not block 443. Any way of getting around this so that i can pull my website up here from work as well as everyone else in the real world still being able to see it??

Do they have port 21 blocked?  You could SSH into your box (via putty if your work PC is windows). Or VNC.  I dunno what port that is, but I know my office leaves VNC open so people can get to their work PCs from home, not sure if you can go the other way tho.

---

### Post by asmoore82 on 2007-08-08
[size=6]Turn Off And Block **telnet**[/size]

---

