---
title: "Problem with Mercury-Messenger"
date: 2006-05-03
forum: Absolute Beginner Talk
---

### Post by Isoss on 2006-05-03
I installed Mercury-Messenger twice. first throguh it's website. I downloaded the .deb file and installed in using terminal and when I attempting to launch the program it gives me an error (couldn't find connection and stuff) and it told me to check my firewall. I stopped the fire wall and then started the program and the whole system froze so I had to reboot my PC using the power button. I removed the program and reinstalled it using Automatix and the same thing happened!

What the hell is wrong with my PC!? Gaim connects and disconnects in 10 minutes ... aMSN 0.95 is not connecting at all, and Mercury freezes the whole system!!!

I really like linux, but these stuff prevent me from switching 100% to linux! why is that?

Any help guys? please ... I hope somebody has a solution. everything is working properly, network, internet, Synaptic, Automatix ... only messenger software drive me crazy ](*,)  HELP!

---

### Post by manicka on 2006-05-03
Isoss, this script to install the latest amsn from cvs may solve your proxy issues

[http://www.ubuntuforums.org/showthread.php?t=102299](http://www.ubuntuforums.org/showthread.php?t=102299)

Those instructions will compile the latest asmn from cvs for you which solves the msn proxy problem. 

If that looks a bit messy then you can obtain and install  some recent deb packages with the script in this post

[http://www.ubuntuforums.org/showpost.php?p=978766&postcount=47](http://www.ubuntuforums.org/showpost.php?p=978766&postcount=47)

either one will probably solve your problems

---

### Post by Isoss on 2006-05-03
Alright, I'll try that, but what about Mercury? Anybody has a solution? or atleast an explaination of what's happening that cause the system to freeze?

---

### Post by Isoss on 2006-05-04
Please help me with this ... I dunno what's going on ... any clues or suggestions ppl?

---

### Post by manicka on 2006-05-04
How did you go with installing amsn-cvs?

---

### Post by Isoss on 2006-05-04
Actually, I am having some problems with wget , this is the thread: [http://www.ubuntuforums.org/showthread.php?t=169952](http://www.ubuntuforums.org/showthread.php?t=169952)

I can't download in anything in any way using wget.

---

### Post by nalmeth on 2006-05-04
thats odd
is your system up to date?
sudo apt-get update 
sudo apt-get upgrade

you can browse to that link in firefox and download the file that way
my mercury test-drive didn't work so well either, I still stick with new Amsn

---

