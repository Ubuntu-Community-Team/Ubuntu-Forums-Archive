---
title: "ubuntu on notebook for graduate school?"
date: 2006-02-17
forum: Absolute Beginner Talk
---

### Post by mellamogsd on 2006-02-17
Hi all. I'm running a dedicated ubuntu desktop at home for about 6 months now and I can't complain about anything. Any problems have been solved quickly and easily with a search in these pages.:D  
  I still use winXP on my laptop, which is an IBM t42 (very compliant with ubuntu so I've read), mainly for the reason that I am interfacing daily with the network at my University, i.e. for setting up presentations, connecting to the school networks, printer sharing, etc etc. I would like to get ubuntu up and running on this comp because of the stability and performance of linux (obviously). I am very concerned, however, that I will lose connectivity at school and that the learning curve for networking and presentation setup is steep. You see I am not by any means an expert. 
  I'd like some feedback about this, especially from anyone with experience with this kind of situation. Any comments, suggestions, ideas, anything is welcome! 

~graham

---

### Post by twisted_steel on 2006-02-17
I also have a T42, and used Linux almost exclusively last semester at school (I continue to use it, but finished in December). Networking worked well for me, as ethernet ports are available in most studio classrooms, and 802.11b wireless was available elsewhere. Wireless worked fine for me in my apartment using the GNOME networking tools, and would have at school as well, however the Cisco VPN client available at the time caused lockups with the kernel. From what I understand, that problem has been fixed. An alternative client is available through Synaptic that does not require kernel modules, and works fine for me. I think the package name is vpnc. As for printing, I have trouble with the Lexmark printer in my apartment, but the printers on campus worked fine, as I could use the generic Postscript driver to print to them. I did not try hooking the laptop up to a projector and using Fn+F7 to switch the screen, as my group ended up presenting with a Windows laptop. There wasn't time to test my laptop beforehand, and we didn't want to chance anything :).

---

### Post by damianubuntu on 2006-02-17
Hi there
It might be worth having a word with the IT support at your uni.  I have a similar situation where I have to run a VPN to remotely connect to my uni, so I checked with the support guys first.  It turns out (of course) that they run most of the uni stuff on Linux anyway, and where extremely knowledgeable and helpful about it.  I should guess that anything you're going to set up, you're going to need to know what their arrangements are anyway....

Good luck with it
D.

---

### Post by phen on 2006-02-17
ibm laptop's acpi functions should work out of the box. it is ibm's goal to make their laptops operating system independent (acpi standards compliant). I don't know about the wlan interface, though. you should check that.

my university uses a cisco vpn for access control. as long as these connections don't need a "certificate", the linux vpn client (from cisco, too) works well. for us students, the linux client software is available at the it department.

presentations work very well with open office. an excel addin i needed to use was compatible with calc. 

i used a windows-shared printer some time. it works! (check wiki for the printer type!)

i love linux on my notebook, and it has never stood in my way until now!

if you need ms office, you can try crossover or wine!
matlab works better than in windows, but there's a lack of powerful CAD software...

hope i could help!

for scientific software (dunno about your subject...), see:

[https://wiki.ubuntu.com/UbuntuScientists?](https://wiki.ubuntu.com/UbuntuScientists?)

---

### Post by mellamogsd on 2006-02-17
Thanks all for the comments. All excellent suggestions. 

Phen, I'm biochemistry and the science wiki is very useful! Thanks for the direction!

~graham

---

