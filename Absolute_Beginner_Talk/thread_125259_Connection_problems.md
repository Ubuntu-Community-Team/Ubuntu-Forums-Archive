---
title: "Connection problems"
date: 2006-02-03
forum: Absolute Beginner Talk
---

### Post by prib on 2006-02-03
HI 

I am new to ubuntu and have jsut installed a fresh version but cannot for the life of me work out how to set up the internet

i am runnign through an router. and i can ping both the router and websites but as soon as i try and veiw a site through a web browser it doesnt work 

i have tried both auto setup of settings and also tried usign static details (ip,dns,ect) and again could only ping stuff but not access it thrugh a web browser

any one got any ideaS?

---

### Post by bscbrit on 2006-02-03
In Firefox, check Edit > Preferences -> Connection Settings, and ensure that Direct Connection to the Internet is selected.

---

### Post by prib on 2006-02-03
[QUOTE=bscbrit]In Firefox, check Edit > Preferences -> Connection Settings, and ensure that Direct Connection to the Internet is selected.[/QUOTE]

Yeh i tried that still not luck though

---

### Post by bscbrit on 2006-02-03
Have you got a firewall operating?  It might be configured to allow pings but be stopping http - I haven't a clue why it should be so configured but it would explain what you are seeing.... :-?

---

### Post by bscbrit on 2006-02-03
[http://www.ubuntuforums.org/showthread.php?t=78337&page=2](http://www.ubuntuforums.org/showthread.php?t=78337&page=2)

Try this thread for a possible explanation (Thanks mips)

---

### Post by prib on 2006-02-03
Yeh i thought along those lines but unless ubuntu automatically does that then no i havent and i cant see anything in the router that would do that and there is also the fact that it works fine through windows which owuld suggest it is nothing to do with the router

---

### Post by prib on 2006-02-03
[QUOTE=bscbrit][http://www.ubuntuforums.org/showthread.php?t=78337&page=2](http://www.ubuntuforums.org/showthread.php?t=78337&page=2)

Try this thread for a possible explanation (Thanks mips)[/QUOTE]


Thanks i will have a look through it

ok on looking through that i use firefox in windows fine through my router whihc makes me htink it might not be that problem i also tried a different browser as well which didnt work

---

### Post by depeche on 2006-02-03
I'm having similar problems connecting to a wireless connection.  I've read through some threads, but nothing seems to provide an answer.

I activated the eth0, and tried connecting automatically - didn't work.  I then typed in the interface properties ie. ip, subnet, etc. - still no luck connecting.

Any suggestions?  Thanks in advance.

---

### Post by bscbrit on 2006-02-03
prib - you are using Firefox on both windows and Ubuntu, but you are not using the _same_ Firefox - the configuration of each could be very different.

depeche - how far through this troubleshooting guide do you get before you hit snags? [https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)

---

### Post by depeche on 2006-02-03
I only searched the forum and the help section of the OS - didn't browse wiki.

I guess I have a project this weekend.  

Thanks.

---

### Post by prib on 2006-02-03
i found another post  by gravediggers which solved the problem

in the location bar in firefox type about:config
then in the filter type network
scroll down till you find network.dns.disableIPv6
right click, choose toggle, and it changes to true
this hopefully will cure it!

---

### Post by bscbrit on 2006-02-04
I think that's what my post #7 suggested :)

---

