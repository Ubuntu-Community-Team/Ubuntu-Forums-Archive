---
title: "New users, Security - DON'T forget it!!!"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by fatality_uk on 2007-12-03
While the vast majority of responses on this forum are clear, and very helpful, I have seen one or two that give an impression that Linux (Ubuntu) is bulletproof and that little or no serious precautions need to be taken. While true to a point, if you only have an ADSL modem for instance, you should have at software firewall running directly within Ubuntu nothing but essential ports blocked. If you transfer, view, edit or use windows files and shares with Windows users, then anti-virus software is required. Not for Ubuntu as such, but because the code can "travel" through your machine and infect a 3rd party Windows user.

---

### Post by eye208 on 2007-12-03
There are no system services listening for inbound connections on external network interfaces in Ubuntu's default configuration.

A firewall is not required.

---

### Post by ukripper on 2007-12-03
All the information you require is here - Read this thread [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by Sarteck on 2007-12-03
I'll cover my mouth when I sneeze, but I'm not going to stay in my house so I don't infect the neighborhood.

My point being, if Windows users somehow -do- get infected from someone using Linux, let them worry about it.  Let them take the proper precautions.  After all, we are, are we not?

---

### Post by hyper_ch on 2007-12-03
> **Sarteck said:**
> I'll cover my mouth when I sneeze, but I'm not going to stay in my house so I don't infect the neighborhood.

My point being, if Windows users somehow -do- get infected from someone using Linux, let them worry about it.  Let them take the proper precautions.  After all, we are, are we not?

I agree... why should I waste my computing power in order to protect other computers? It's their responsability to secure their boxes.

---

### Post by de_valentin on 2007-12-03
> **hyper_ch said:**
> I agree... why should I waste my computing power in order to protect other computers? It's their responsability to secure their boxes.

Agreed if they would use linux they wouldn't have to live with the constant fear of virii or adware or clogging up (i know the last one is off topic)

---

### Post by lamalex on 2007-12-03
> **fatality_uk said:**
> While true to a point, if you only have an ADSL modem for instance, you should have at software firewall running directly within Ubuntu nothing but essential ports blocked.
You have one by default, iptables is part of the OS. It's just transparent. If you're looking for a good config tool, then firestarter is a GUI, and shorewall is a very robust config file based one. My iptables configuration tool of choice. VERY robust.

---

