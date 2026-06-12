---
title: "Help"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by b123 on 2007-01-01
hey wat up im new to ubuntu and i have just recently installed it on my hard drive and when i boot it up my screen res is stuck on 1024x768 and my wireless doesnt work and i dont know how to install the correct drivers and also my updates wont install an error always comes up. please help i have a gateway mx6956 laptop with a intel PROSet wireless 3954 a/b/g pci card](*,) ](*,) please help!!!!!!!

---

### Post by kepos on 2007-01-01
try installing newer drivers for graphic card. if you are using ati or nvidia, look heare for instructions: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#Graphics_Card](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Graphics_Card)

which error you get while updating? what does it says?

sorry, but i can't help you with wireless. try google like: "ubuntu PROSet wireless 3954".

---

### Post by linuchsan on 2007-01-01
I think you mean the 3945ABG not 3954ABG.
You can find out if the module is loaded with lsmod |grep ipw3945
For your your video problem, look at [http://www.intellinuxgraphics.org/](http://www.intellinuxgraphics.org/)

---

### Post by b123 on 2007-01-01
> **kepos said:**
> try installing newer drivers for graphic card. if you are using ati or nvidia, look heare for instructions: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#Graphics_Card](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Graphics_Card)

which error you get while updating? what does it says?

sorry, but i can't help you with wireless. try google like: "ubuntu PROSet wireless 3954".

it says error then it says "cant fetch" and whatever the url is to the updates i think its a problem with networking

---

### Post by kepos on 2007-01-01
> it says error then it says "cant fetch" and whatever the url is to the updates i think its a problem with networking

Does your internet connection work well on that computer? Could you please paste the output of 'sudo apt-get update' heare?

---

### Post by Tomosaur on 2007-01-01
If your wireless isn't working, and you aren't connected to the net using a cable, then updates will simply not download. You need to get your wireless card working first.

---

