---
title: "Solution to slow internet"
date: 2005-07-31
forum: Absolute Beginner Talk
---

### Post by kevlar16 on 2005-07-31
If you are using Kernel 2.6 and connecting to the internet via ethernet & router, you may experience very slow internet connection. 

Here is how to fix it: 
open the file: '/etc/modprobe.d/aliases' as sudo or root user
find this line in the file: 'alias net-pf-10 ipv6'
chage it to this: 'alias net-pf-10 off'
save the change and reboot

This solution should work with other Debian based distributions as well as Ubuntu.

---

### Post by UbuWu on 2005-07-31
Firefox also has a setting: network.dns.disableIPv6
Do you know how these relate to each other? Or do they do exactly the same?

---

### Post by kevlar16 on 2005-08-01
I tried disabling IPv6 through Firefox on several distributions that have Kernel 2.6 available. It did not seem to work for my network setup, but I have heard that it worked for other people. It would not harm anything to try both methods.

---

### Post by bdn01 on 2005-09-22
I've made the change to aliases as suggested with no noticable difference. 
Disabling ipv6 in firefox did improve firefox though.

Is there a way to trace where the bottleneck is?

---

### Post by wmcbrine on 2005-09-22
[QUOTE=UbuWu]Firefox also has a setting: network.dns.disableIPv6
Do you know how these relate to each other? Or do they do exactly the same?[/QUOTE]One is just for Firefox (and just for that one profile), and the other is system-wide.

I had to disable IPv6 system-wide after I set up local DNS. It went like this:

1. Install Ubuntu. Point /etc/resolv.conf at my router. Firefox is slow. Set the disableIPv6 option. Firefox is fast!

2. Install DNS on my own system. Point /etc/resolv.conf at 127.0.0.1. Firefox is slow again. Disable IPv6 system-wide. Firefox is fast!

However, I didn't use Kevlar's method. I don't remember exactly what I did do.

BTW, I didn't see the problem with the Breezy LiveCDs I've tried.

---

### Post by bdn01 on 2005-09-22
I'm puzzled that nslookup works fine in the terminal but applications seem to have problems. Surely nslookup proves that DNS, resolv.conf, hosts, etc. are all  technically set-up ok....

---

### Post by JOKER_JOKER on 2005-09-22
Ok, I am the biggest absolute beginner when it comes to linux.  Firefox is ridiculously slow, and I typed in the command in the terminal, but it kept saying could not open "........" permission denied.  Before that I typed in "sudo -s" then typed in my password so I was in root.  How do I get access to it?

---

### Post by Kapre on 2005-09-22
[QUOTE=JOKER_JOKER]Ok, I am the biggest absolute beginner when it comes to linux.  Firefox is ridiculously slow, and I typed in the command in the terminal, but it kept saying could not open "........" permission denied.  Before that I typed in "sudo -s" then typed in my password so I was in root.  How do I get access to it?[/QUOTE]
 Joker_joker - if your trying Ubuwu's approach, you have to type "about:config" in the address bar of firefox (not in the terminal).

K

---

### Post by JOKER_JOKER on 2005-09-23
No, I'm talking about Kevlar16's approach to the problem.  It just keeps saying "permission denied."

---

### Post by wmcbrine on 2005-09-23
Try a root terminal. (Applications, System Tools, Root Terminal.)

---

### Post by ProPilot on 2005-09-26
Breezy - about:config method in Firefox worked like a charm

Tom

---

