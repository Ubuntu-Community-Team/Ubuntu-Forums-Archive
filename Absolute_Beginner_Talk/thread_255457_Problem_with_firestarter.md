---
title: "Problem with firestarter"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by mdysonr on 2006-09-11
I installed firestarter on ubuntu, and now i cant connect to the internet

---

### Post by Najand on 2006-09-11
How did you set it up? And for what purposes did you install firestarter?

---

### Post by Najand on 2006-09-11
Do you have connection when you stop firestarter and exit it?

---

### Post by mdysonr on 2006-09-11
i have a adsl dial up modem and my computer is connected to network

yes when i stop the firewall i have connection

---

### Post by Najand on 2006-09-11
And what else? Can you give me more details?

---

### Post by mdysonr on 2006-09-11
> **Najand said:**
> And what else? Can you give me more details?


yes when i stop the firewall i have connection

---

### Post by Klaidas on 2006-09-11
When you installed, did your internet connection just disappered?
Did you configure it? What did you configure?
Did you make sure it's not in state "locked"? Or "Restrictive by default" for outgoing traffic?

We can help, but we can't read your mind :)

---

### Post by Najand on 2006-09-11
which device did you select during setup wizard? eth0 or ppp0? did you have any errors during thgat wizard?

---

### Post by mdysonr on 2006-09-11
i select etho0! the ppp0 dont appear! and i didnt have any errors

---

### Post by Najand on 2006-09-11
It is a simple application. So the chance of faults during configuration is very low. Hmm, Let me see, You have not locked the firewall, have you?

---

### Post by mdysonr on 2006-09-11
no

---

### Post by Najand on 2006-09-11
What about 2 options of:
1 Start the firewall on dial-out
2 IP address is assigned via DHCP
Did you select them?

Please send me the output of netstat and ifconfig while the firewall is on.

---

### Post by mdysonr on 2006-09-11
> **Najand said:**
> What about 2 options of:
1 Start the firewall on dial-out
2 IP address is assigned via DHCP
Did you select them?

Please send me the output of netstat and ifconfig while the firewall is on.

Yes i select both of them

but what is the output of netsat?

---

### Post by Najand on 2006-09-11
Do you have a static ip address or it is something automatically set when connecting to the internet?

netstat and ifconfig are two commands... You must execute them in terminal... Please write down the output and I will see how can I help you then.

---

### Post by jdong on 2006-09-11
Have you considered uninstalling Firestarter as it is fairly pointless to be running a firewall on the typical Ubuntu install?

---

### Post by Najand on 2006-09-11
Hmm, I have the same idea... But maybe some security issues is what he concerns... 
And I am curious to see what is the problem too.

---

### Post by Najand on 2006-09-11
And also, can you tell me something, jdong?
how can I erase previously written messages of mine?

---

### Post by mdysonr on 2006-09-11
l

---

### Post by jdong on 2006-09-11
> **Najand said:**
> And also, can you tell me something, jdong?
how can I erase previously written messages of mine?

If you go to edit your post, you should have a delete button..

---

### Post by Najand on 2006-09-11
Hmm, something is wrong with ip addressing... However why do you need a firewall at the begining?

---

### Post by mdysonr on 2006-09-11
ok is better to uninstall the firewall

---

### Post by jdong on 2006-09-11
Unless you have a really good reason to be running the firewall, uninstalling it would be your best approach. It really doesn't increase your security in any way.

---

### Post by Najand on 2006-09-11
> **jdong said:**
> If you go to edit your post, you should have a delete button..

Hmm, unfortunately it cannot be found anywhere... Maybe it is just me to have such a problem.

---

### Post by Najand on 2006-09-11
Well, I used to have a Local Natwork with ubuntu as a server containing some windows machines inside, so I had to use some firewalls, however if you want it for your desktop machine, firewalls are not needed...

---

### Post by mdysonr on 2006-09-11
ok thank you very much for the help

---

### Post by andb on 2006-09-11
mdysonr, I wouldnt say its better to uninstall the firewall, just easier. See it as a change to learn about iptables :) Turn it off when you need to work, and try to sort it out. Problems are the best way to learn! Ive always prefered to have a modem/router instead of a usb modem, makes setup much easier. Good luck!

---

