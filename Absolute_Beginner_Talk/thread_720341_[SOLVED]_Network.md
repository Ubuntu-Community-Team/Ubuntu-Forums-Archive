---
title: "[SOLVED] Network"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by samitharansara on 2008-03-10
I'am newbie to Ubuntu, using hardy 8.04 alpha release. When I logged on, I had to change the ip of my machine (hence hardy will reconfigure the network) , to access internet. I had to do this each and every time when I logged on. Whats the problem?

Thanks in advance.
Samitha

---

### Post by kesman on 2008-03-10
How did you change the ip? From the graphical network manager, or by terminal?

---

### Post by sayakb on 2008-03-10
And what problem do you face when you keep it on Roaming Mode?

---

### Post by samitharansara on 2008-03-10
I changed the IP in Graphical mode.(Right click on the network icon, and clicking manual configuration). Roaming mode doesn't support by the proxy that i used to connect to the internet.

Best regards,
samitha

:mad:

---

### Post by samitharansara on 2008-03-10
I changed the IP in Graphical mode.(Right click on the network icon, and clicking manual configuration). Roaming mode doesn't support by the proxy that i used to connect to the internet.

Best regards,
samitha

---

### Post by kesman on 2008-03-11
If you changed the ip that way, the setting should be permanent. Are you using the LiveCD by the way? In LiveCD, settings aren't saved.

---

### Post by samitharansara on 2008-03-11
No,I'm not using the live CD. I have installed ubuntu. How can I make those settings permanent? 

Thanks for the help.

Samitha

---

### Post by LeAstrale on 2008-03-11
my first question would be WHY!? do you use hardy alpha when you're not a dev or very good at ubuntu? (excuse the hard language i just have a really hard time understading it) hardy heron still has errors and are only meant for the small dev part of the community and those people who does serious bug finding on it.

when all this is said, could you please post the output of lspci ?

is it wireless or ethernet? What ip is your machine meant to have?

/Astral-1

---

### Post by hyper_ch on 2008-03-11
why don't you just use static IP instead? That should do the job then.

---

### Post by samitharansara on 2008-03-11
I'm using Static IP. But the problem is when I logged of and logged back in, I couldn't connect to the internet.  Always I had to change my IP (My IP was not taken by others when this takes place :) ). Then it reconfigure the network and only after that I can connect. 

Whats the problem?

---

### Post by kesman on 2008-03-11
Maybe this is a bug in the alpha version of Hardy? Try manually editing your /etc/network/interfaces -file after you have changed the "roaming" to "static ip" in the graphical network manager.

---

