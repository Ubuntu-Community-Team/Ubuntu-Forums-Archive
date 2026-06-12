---
title: "Switching network addresses..."
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by GeneticFlea on 2007-11-06
hey everyone! Im quite new to ubuntu and linux, so please be gentle :P

Im trying to solve a problem here on campus. I live on a small college, which unfortunantly in an effort to not upgrade our bandwidth, has put caps on how much each user can download in a day.That number is currently 240 mb/day. I know that our school keeps track of who's using what by our Nic cards(mac address, nic address? something like that) and that is how they can tell when i go over my limits. As everything is downloaded from the net in Linux, im having trouble with my bandwidth caps and the school is angry at me. Many of my friends however said that they never use theirs and im free to use their bandwidth if i can figure out how. Even one of my friends on windows has successfully done this. 

Can anyone help me switch between Nic's using ubuntu? ideally some way in which i could switch between a number of them throughout the week.

Thanks!

---

### Post by rudeboyskunk on 2007-11-06
These were the best results a search yielded, sorry if they're not too helpful:

[http://www.linuxforums.org/forum/suse-linux-help/77331-how-change-nic-names.html](http://www.linuxforums.org/forum/suse-linux-help/77331-how-change-nic-names.html)

[http://ubuntuforums.org/showthread.php?p=3701677](http://ubuntuforums.org/showthread.php?p=3701677)

[http://unix.derkeiler.com/Mailing-Lists/FreeBSD/questions/2006-07/msg00995.html](http://unix.derkeiler.com/Mailing-Lists/FreeBSD/questions/2006-07/msg00995.html)

---

### Post by GeneticFlea on 2007-11-06
thanks for the help! I just found this link to a program called Macchanger: [http://www.ubuntugeek.com/change-your-network-card-mac-address-on-ubuntu.html](http://www.ubuntugeek.com/change-your-network-card-mac-address-on-ubuntu.html)

and it seems like it would be the program to use. However im not sure how to because its all command line and the instructions dont make sense to me, in other words im not sure how to word my commands, i tried what i thought the author was saying but nothing happens and it just keeps showing me the help file.

thanks!


edit: Ok so i found a program called macchanger-gtk that allows me to change the mac in a GUI which helps some. I click on specific macadress and it asks for the mac addres and a network interface....what should i put in the network interface column?

---

### Post by GeneticFlea on 2007-11-06
ok i read some more and now i understand MAcchangers interface, so i typed in
 sudo /etc/init.d/networking stop, like the tutorial said to stop the network, then i typed:
 macchanger --mac=00:19:d1:0b:4f:32 eth which if i understand should change the mac address. Instead it says this :

Current MAC: 00:50:8d:e3:37:3c (Abit Computer Corporation)
ERROR: Can't change MAC: interface up or not permission: Operation not permitted


any clues?

---

### Post by Seisen on 2007-11-06
Try sudo in front of the command

---

### Post by GeneticFlea on 2007-11-06
hah, that was all i needed, dumb me, thanks for the help!

---

