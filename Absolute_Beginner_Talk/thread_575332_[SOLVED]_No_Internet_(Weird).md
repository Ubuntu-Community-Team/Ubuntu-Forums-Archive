---
title: "[SOLVED] No Internet (Weird)"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by ghost_ryder35 on 2007-10-13
Ok I have searched and searched and searched.  I have a **dual boot **setup with Windows Vista and Ubuntu 7.10.  I can not "get online" with Ubuntu **kind of**.  Internet works perfectly fine on Windows Vista.  Ubuntu **gets **an IP address, Gateway and DNS servers but when I search the web using **Firefox** I can not get anywhere.  The funny thing is if I open a terminal session **I can ping anything **i.e. [www.google.com](www.google.com) [www.yahoo.com](www.yahoo.com) etc...  If I ping [www.google.com](www.google.com) and then copy the IP address from the terminal window and paste it into FireFox I can get to the website, but just typing it into the Firefox address bar I can not.  I do have port forwarding set up on my router using **computer names **not static IP address's.  Why is this?  I have thought of everything using a wired cable instead of wireless etc... I can not get it to work.  I can download updates and download any program in the "Add/Remove" section of the "Applications" toolbar with no problem but I cannot surf the web with Firefox unless I copy and paste the IP address from the terminal.  I thought it was DNS but since the web address gets resolved in the terminal I have ruled DNS failure out.  Any help would be appreciated.  Is there a special port I have to forward for Firefox now adays?

---

### Post by milosz.galazka on 2007-10-14
Did you tried *firefox -safe-mode* or any other web browser?

---

### Post by ghost_ryder35 on 2007-10-14
> **milosz.galazka said:**
> Did you tried *firefox -safe-mode* or any other web browser?
no not yet. Is there another web browser in the repositories?

---

### Post by beyboo on 2007-10-14
[http://www.opera.com/download/](http://www.opera.com/download/)

---

### Post by ghost_ryder35 on 2007-10-14
thanks for the link.  I'll ping it to download :)

---

### Post by ghost_ryder35 on 2007-10-14
heres a thought.  I am using an Actiontec router and modem combination.  Is this known to be a problem with Ubuntu.  I know it shouldnt effect it but I am desperit.

---

### Post by ghost_ryder35 on 2007-10-15
ok downloaded opera and it didnt solve my problem.  I'm really confused right now.  The only thing I can think of is somehow somewhere something is blocked with a firewall but everything is perfectly set up.  HELP

---

### Post by ghost_ryder35 on 2007-10-15
bump.... somebody has to have an answer for me on this.  I'm stumped to the end.

---

### Post by obesus_puer on 2007-10-15
Sounds like a problem with DNS to me. Did you try manually setting your IP DNS and what not?
First post!

---

### Post by milosz.galazka on 2007-10-15
What happens if you boot ubuntu live cd? Do you experience same problem?

---

### Post by ghost_ryder35 on 2007-10-15
> **obesus_puer said:**
> Sounds like a problem with DNS to me. Did you try manually setting your IP DNS and what not?
First post!
if a terminal session resolves the IP address why would it be a DNS issue?  Its resolving the address :)

---

### Post by ghost_ryder35 on 2007-10-15
> **milosz.galazka said:**
> What happens if you boot ubuntu live cd? Do you experience same problem?

IDK.  I'll try that right now.

---

### Post by obesus_puer on 2007-10-15
> **ghost_ryder35 said:**
> if a terminal session resolves the IP address why would it be a DNS issue?  Its resolving the address :)

Your right im retarded :lolflag:

---

### Post by obesus_puer on 2007-10-15
What are your settings in firefox under tools > options > advanced > network tab > settings?

---

### Post by ghost_ryder35 on 2007-10-15
> **obesus_puer said:**
> Your right im retarded :lolflag:
instead of saying I might be retarded how bout you shed some light on the situation.
Settings in FireFox are default settings.  Havent played with it at all.

LiveCD session has same problem with wired connection directly to router.  Can ping [www.yahoo.com](www.yahoo.com) but cant get to it through FireFox

---

### Post by milosz.galazka on 2007-10-15
Maybe there are set proxy settings somewhere in GNOME?

---

### Post by ghost_ryder35 on 2007-10-15
I'll hunt around for some settings.  If I cant find a proxy setting maybe I should say automaticly detect the proxy settings instead of direct connection.

---

### Post by ghost_ryder35 on 2007-10-15
[IMG]http://i192.photobucket.com/albums/z150/ghost_ryder35/Screenshot.png[/IMG]
Heres a screen shot

---

### Post by obesus_puer on 2007-10-15
Do you get the same results after releasing and renewing your IP address?

---

### Post by ghost_ryder35 on 2007-10-15
> **obesus_puer said:**
> Do you get the same results after releasing and renewing your IP address?

Yep.  I can statically assign it and the DNS servers all day long and get the same result

---

### Post by obesus_puer on 2007-10-15
> **ghost_ryder35 said:**
> Yep.  I can statically assign it and the DNS servers all day long and get the same result
Thats bizzare. I really wish I could help but I'm still an Ubuntu nooby. Good luck!

---

### Post by ghost_ryder35 on 2007-10-15
**SOLVED**
When I was looking through my DNS entries I got confused.  After statically assigning an IP, Gateway, and DNS server everything went well but the DNS.  The nm-applet remembered the DNS server that my router had dynamically assigned earlier and used it as the priority DNS server.  To fix the problem I moved the router's DNS server to the bottom of the DNS list and the DNS server I statically assigned to the top of the list.  Now I can even use DHCP :)  I am using Firefox right now in Ubuntu.  stupid nm-applet ;)  For some reason it shows my routers DNS server as primary but it isnt as you can see in the left box.
[IMG]http://i192.photobucket.com/albums/z150/ghost_ryder35/Screenshot-3.png[/IMG]

---

### Post by obesus_puer on 2007-10-15
WOOT I was right-ish

---

