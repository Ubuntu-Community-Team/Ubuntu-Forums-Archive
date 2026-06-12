---
title: "virtual box"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by basilwatson on 2007-02-26
Hi there 
having used gdebi to install Virtual box , the second install ( reinstall worked fine )  

Cant remember the error for the first install but it said check dmseg ,,which I did and found nothing ...( unusual ) 

After a reinstall it  installed and is in the menu BUT it wont launch, read  user manual and it said change 
 NMI_watchdog=1 to 0 

This was in grub  how do I do this 

Sorry for this 

Stephen

---

### Post by TonKi on 2007-02-27
I dont know if this is the source for your trouble but you have to add your user to the Virtualbox group.

System > Administration > Users&Groups and select "Manage Groups", then find "vboxuser" double-click and add yourself.

h2h

---

### Post by basilwatson on 2007-02-27
Sorry for that hurried question I had aphonecall from work ..I was late anyway  tried adding my details to group , will reboot , but  it looks like no Joy 

I am using Ubuntu 6.06 dapper and its a dual boot with windows ( if that helps )  can post dmesg ,,but I couldnt see anything that hinted towards Vurtual box ...only in the virtual box manual could I see anything and that was nim watchdog set to zero ,,,but where can I find that ?? grub ?? on boot ?

open to suggestions 

Kind regards Stephen

---

