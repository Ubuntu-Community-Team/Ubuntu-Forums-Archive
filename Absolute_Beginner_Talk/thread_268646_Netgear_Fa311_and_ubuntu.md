---
title: "Netgear Fa311 and ubuntu"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by GCDB on 2006-09-30
A big hi to all, first post but sorry for questions.
Have installed ubuntu ok dual booted with xp.
Problem is the ethernet card i have fa311(national semiconductor dp83815 macphyter) is not listed in networking. Searching these forums and googling brings up others have had problems as well. I think my card is fa 311 v1 which according to netgaer support is not supportive of linux. Some people have managed to get it working but not me as yet.
Lspci brings up the card and it is in device manager,
Have tried sudo modprobe netsemi(driver which has worked for others) then when i try dhclient eth0 it gives error while getting interface flags:no such device.
if i try sudo ifconfig eth0 up it just brings up error setting interface flags:no such device
lsmod shows netsemi present but no uses.
lspci | grep mii brings up nothing.
After trying all these i have hit a brick wall apart from buying a new card which is a shame as it works flawlessly in xp.
Thanks for reading and this is my first linux and lost already.
Gav

---

### Post by GCDB on 2006-10-01
I guess its go and buy a more compatible card?

---

