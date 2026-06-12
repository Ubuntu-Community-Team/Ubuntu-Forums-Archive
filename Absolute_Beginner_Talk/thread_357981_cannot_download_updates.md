---
title: "cannot download updates"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by warri0r on 2007-02-10
i m new to ubuntu and this is my 6th installation coz every time i update, it ll end up in a command prompt window when i reboot my pc. but later i discovered its the problem with the driver (nvidia) tat i installed. one of the friend here helped me.

but now i cant download updates. i can browse through all the websites and even downloaded files from different servers. wat is the problem. 

when i issue the command "sudo apt-get update" it ll roll up and stuck at 99% with some security.ubuntu.com

and when i use the graphical update tat pops up near the clock, it stays idle and when i kick it again and again it downloaded some updates and informed some updates cannot be downloaded.

wat i need to do. and im relly sorry for my long long story if u dont like tat. plz help

---

### Post by Perfect Storm on 2007-02-10
Can you give the full description of the place it stops?

Also
```
cat /etc/apt/sources.list
```

---

### Post by Spookster on 2007-02-10
Am having exactly the same problem here at the moment - trying to install something and it is hanging at:
> 99% [Connecting to security.ubuntu.com (82.211.81.138)]

---

### Post by Perfect Storm on 2007-02-10
It could that the mirror is down at the moment. Try wait a day, meanwhile comment it out the line in the sourcelist, if you want to install/use apt-get/aptitude/synaptic. Just remember to uncomment it again.

---

### Post by isenalim on 2007-02-10
Hi,
I have the same problem, apparently security.ubuntu.com is down. 
Do you know of any mirror? 
I am installing ubuntu on my parents' laptop to show them how cool linux is and this it's really sad!
Ciao

---

### Post by Perfect Storm on 2007-02-10
Try remove the land code from the sourcelists and see if it works.

---

### Post by Spookster on 2007-02-10
Thanks, commenting out those lines in sources.list did the trick. Now, must remember to put them back tomorrow...

---

### Post by warri0r on 2007-02-10
thanks for these lightning replies

but i hav got one more strange problem. i dont know whether i need to open a new thread or can continue in this. sorry if im wrong.

after installing those recommended updates as usual my ubuntu crashed. but this time i got a new error message some thing like "[some numbers]bug:soft, lock, cpu"  sorry i cant remember the exact error message but i can remember the above said words. this seems to be stupid but i got a bad memory :( .

i wont get regretted. again i made a fresh install. but this time i cant install my ralink wireless driver.wat the **** :( this is the only thing i done at great success rates, but now i cant install this.

my ubuntu hangs up when i try to configure my adapter with a static ip.

like when i issue this command

ifconfig ra0 192.168.1.3 netmask 255.255.255.0 up

i tried several times but it simply hangs up. :(

plz some one help me. wat i need to do. i want get rid of my windows box, plz help

---

