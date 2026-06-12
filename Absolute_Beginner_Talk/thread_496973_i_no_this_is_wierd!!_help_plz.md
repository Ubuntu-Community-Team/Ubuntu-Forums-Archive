---
title: "i no this is wierd?!?!? help plz"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by Korea91 on 2007-07-09
i had posted a thread in the fedora 7 core forum for help but none seems to no 

i have an ati mobility radeon x700 

when i had installed my ubuntu with the live cd the screen went blank while i thought it was installing but it had just stopped

so i had to download the text installer and tried but it said x system diagnosis and so on just stating it could not be found
so i found a site that said 
 put in these commands 
sudo apt-getupdate
sudo apt-get dist-update
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type=xv

then i rebooted and it worked.

now when i tried to install fedora 7 live cd on the same computer the screen went blank so im downloading the text installer dvd but i no its gonna have the same problem asking about the x system so im hoping unlike the people at fedora forum u guys will understand and if u do plz help 

like wat code or script must i put in, in the text installer?

---

### Post by KIAaze on 2007-07-09
Fedora is a distribution based on Red Hat and therefore uses .rpm packages and yum instead of .deb and apt-get like Ubuntu.

I did some research and would suggest this:

```
su
yum update
yum install xorg-x11-drv-fglrx
aticonfig --initial
aticonfig --overlay-type=xv
exit

```

You might have to update yum.conf. See here for more:
[http://www.fedorafaq.org/fc1/#InstallSoftware]("http://www.fedorafaq.org/fc1/#InstallSoftware")
[http://www.fedoraforum.org/forum/showthread.php?t=25880]("http://www.fedoraforum.org/forum/showthread.php?t=25880")

This being an Ubuntu forum, if you didn't get an answer on the Fedora forums, you might be better of with generic linux forums like [www.linuxquestions.org]("www.linuxquestions.org") or [www.linuxforums.org]("www.linuxforums.org").
There might be better Red Hat/Fedora specialists there. ;)

---

