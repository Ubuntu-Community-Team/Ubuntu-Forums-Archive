---
title: "Edubuntu LTSP - can't get to work"
date: 2005-12-10
forum: Absolute Beginner Talk
---

### Post by adajar99 on 2005-12-10
hello,

i've tried installing edubuntu to be used as ltsp server.  i followed all instructions, but when i run the thin client, i get a console login (runlevel 2), wherein i can't get any userid to work.

1)  am i correct to assume that after the installation as specified in the ubuntu site, i don't need to do any other configuration? do i need to tweak any other files (e.g., lts.conf, fstab, etc.)?  when i turn on the thin client, i get a message that says that the /etc/fstab file misses some parameters, but it will kludge around to make it work in the meantime.  any ideas?
2)  i have read from one thread that the implementation of ltsp in ubuntu is different from the regular ltsp installation.  which means that i cannot use the ltspadmin program.  for example, xdmcp is not installed, and according to jim mcquillan, xdmcp is not used by the ubuntu ltsp installation.
3)  would i be better off using another distro and then get the ltsp package from ltsp.org?  the documentation from ltsp.org looks good, and seems to describe everything that needs to be done.  on the other hand, ltsp from ubuntu has installation notes, but doesn't give any other info in case it doesn't work.

i a newbie, and although i've installed several distros in the past, this is the first time i'm working on a linux as a server.  

any help would be appreciated.  thank you.

adajar99

---

### Post by jgregory on 2006-03-15
I'm having the same problem - Edubuntu Breezy / LTSP...

Did you ever find a solution?

John

---

### Post by Ted Salad on 2006-03-15
Me to! I'm a Newbie and just want to get the ltsp going. The way it comes over to me is if you have Edubuntu installed you have the server running. Is this true or like others here do you have to tweak it?

cheers
Ted

---

### Post by redjim on 2006-05-03
I have installed and run edubuntu right out of the box.  The trick is to set up your server with the ip 192.168.0.1 for it to take the default and work.  

Please read 
[https://wiki.edubuntu.org/Howto-setup-LTSP-server-on-Ubuntu-Breezy?highlight=%28server%29%7C%28ltsp%29](https://wiki.edubuntu.org/Howto-setup-LTSP-server-on-Ubuntu-Breezy?highlight=%28server%29%7C%28ltsp%29)

to see the how to.

Thanks, James

---

