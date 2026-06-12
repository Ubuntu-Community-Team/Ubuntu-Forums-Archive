---
title: "Problems Accessing My Webpage"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by McJuicy on 2006-12-03
Hello, I have recently pieced together an old computer in order to host a website. I followed the LAMP server tutorial and everything seems to be in order except the fact that i cannot access my webpage from outside the home network. I have ports 80 and 22 forwarded to my computer's internal ip but i am stuck on what i need to do in order for it to work outside my network. I am thankful for any help.

---

### Post by Kurt` on 2006-12-03
It's very possible that your ISP blocks those 2 ports. My ISP blocks port 80, too. :(

Apache and SSHD both listen on all interfaces (aka 0.0.0.0) by default, so if the ports are indeed forwarded correctly, the traffic is being intercepted and dropped somewhere else.

---

### Post by McJuicy on 2006-12-03
I can log in SSH but not apache. So i have to change the default port apache uses?

---

### Post by johnnymac on 2006-12-03
Can you answer this:

1.  So can you access it from your internal network using the systems IP? 

2.  If you use an IP address externally instead of your domain name can you access it?

3.  Did you recently make changes to the location you have your domain name hosted with?  If so it can take up to 72 hours for the settings to propagate.

---

### Post by McJuicy on 2006-12-03
1. I can access in the network using the domain name, the external IP and the internal ip, inside my home network

2. Can't access it externally just using the external ip

3. Haven't made any recent changes.

If i called up my ISP do you think i could get them to unblock these ports?

---

### Post by johnnymac on 2006-12-03
Not likely....there are quite a few ISPs that block those ports unless you pay for some monster business class package.  You could try changing /etc/apache2/ports.conf to some other port and open that one up.  Pick some silly port way high (just make sure it isn't used by anything you need).

---

