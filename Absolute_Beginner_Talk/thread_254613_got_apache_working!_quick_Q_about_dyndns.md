---
title: "got apache working! quick Q about dyndns"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by emprog on 2006-09-10
My isp blocked port 80 so I used another port for my web server. Basically since I need to tack on that port to get the browser to my server how can I set up my dyn dns account? Right now I have emarquez.homelinux.net pointing to my ip but I cannot tack on : port in my settings there. Any ideas or would I just need my isp to unblock port 80 to use a domain with my site?

---

### Post by MiKuS on 2006-09-10
you need to edit the port apache listens too, my isp does the same deal so i just use port 8080, the location of my config file (i use apache2) is: /etc/apache2/ports.conf 
i then signed up to no-ip.com and set up a foward to my computer at home. 

after you edit the a[ache files you will need to run 
```
sudo /etc/init.d/apache2 restart
```

good luck

---

### Post by emprog on 2006-09-10
Hi, thanks for the reply. I already set the port in ports.conf and everything works fine but dyndns.com just lets me add an ip, not ip: port so I am not sure how to make emarquez.homelinux.net point to 67.23.32.16:84 since I cannot tack on : 84 in my settings at dyndns.com. I can use emarquez.homelinux.net:84 but was hoping to set this up so the user didn't have to add the port to the end

---

