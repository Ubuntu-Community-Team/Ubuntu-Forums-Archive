---
title: "D link WDA 1320"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by blk03mitsues on 2007-09-27
i have issues with my D link pci card. for instance when i have it as roaming i will have access to the internet but it will go away from time to time. even thou i'm like 3 feet away from the router i have about 40% signal. both power and activity lights blink at the same time. if i try to go from roaming to manual then i cant connect to the net at all, power light will blink then activity light blink, one after the other. i have downloaded ndiswrapper, i loaded the driver from D link's website to the "windows wirless drivers" loaded fine but it says " but it says "hardware not found"

i've read that other people have no issues with it and i didnt have issues when i had this card installed in another machine running linux mint cassandra. btw i'm running ubuntu feisty. any ideas as to what i did wrong?

---

### Post by overdrank on 2007-09-27
> **blk03mitsues said:**
> i have issues with my D link pci card. for instance when i have it as roaming i will have access to the internet but it will go away from time to time. even thou i'm like 3 feet away from the router i have about 40% signal. both power and activity lights blink at the same time. if i try to go from roaming to manual then i cant connect to the net at all, power light will blink then activity light blink, one after the other. i have downloaded ndiswrapper, i loaded the driver from D link's website to the "windows wirless drivers" loaded fine but it says " but it says "hardware not found"

i've read that other people have no issues with it and i didnt have issues when i had this card installed in another machine running linux mint cassandra. btw i'm running ubuntu feisty. any ideas as to what i did wrong?

HI this thread may help
[http://ubuntuforums.org/showthread.php?t=523567&highlight=WDA+1320](http://ubuntuforums.org/showthread.php?t=523567&highlight=WDA+1320)
And here is the search for that card
[http://ubuntuforums.org/search.php?searchid=27863079](http://ubuntuforums.org/search.php?searchid=27863079)
I hope this helps and good luck!

---

### Post by blk03mitsues on 2007-09-27
well one thread says to unsinstall network manager......... how do i do that and then how would i set up my wireless network?

other threads say they have no problems with my card. in some of those threads people have the same issues as i do but they dont seem to be answered.....

thanks for trying to help thou

---

### Post by blk03mitsues on 2007-09-28
bump?

---

### Post by blk03mitsues on 2007-09-28
really disappointed that i could not be helped out.

---

### Post by overdrank on 2007-09-28
> **blk03mitsues said:**
> really disappointed that i could not be helped out.

Ok have you tried anything in the threads? As I understand it  if you remove the network manager as mentioned in one thread you will still be able to setup your network under applications, system, network. Just activate your wireless card and set it up. If this does not work you can still reinstall network manager.

---

### Post by blk03mitsues on 2007-09-28
i did uninstall network manager and that didnt do anything different. the guy in that thread says that the card worked before feisty then after feisty it didnt. he removed network manager and then it worked. but my card worked in feisty somewhat and signal goes on and off. 

other threads just talk about the card working right from the start

---

### Post by overdrank on 2007-09-28
> **blk03mitsues said:**
> i did uninstall network manager and that didnt do anything different. the guy in that thread says that the card worked before feisty then after feisty it didnt. he removed network manager and then it worked. but my card worked in feisty somewhat and signal goes on and off. 

other threads just talk about the card working right from the start

Ok I am sorry, I am by no means a network expert and I am just trying to help until some one with this network card will jump in. :(
Please post the output of the lspci command in the terminal

---

