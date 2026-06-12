---
title: "Unable to download updates / new software"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by phaze on 2006-08-22
Hi there, Compeltely new to ubuntu. 

After install I was unable to connect to the update server or download new software thorugh add/remove. I have tried the sudo apt-get update command and essentially it stays at 0% until it gives an unable to fetch and says connection timed out. Now firefox worked perfectly after i sorted out the ivp6 thing, i wonder do i need to change similar settings to enable updates to work. 
Im behind a router.

Any help would be much appreciated, don't be afraid to state the obvious and/or treat me like an idiot because I am as i said completely new to this.

---

### Post by royalez on 2006-08-23
hi
yes i have exactly the same problem
firefox works fine, package downloads dont download

any help would be much welcomed

---

### Post by gils0040 on 2006-08-23
sounds to me like a dns problem. this is common (especially with shitty actiontec routers). you can check this by going to system->administration->networking. click the dns tab and check that you have the correct servers entered.

---

### Post by phaze on 2006-08-23
I've got a D-Link DSL-g604t router and i have had problems with the DNS before but ive got it all working with windows. Im on windows now but il go a copy and paste the DNS addresses from the routers configuration screen into the ubuntu network settings see if that helps. From memory the DNS address in the network settings box is set to the local address of the router.

---

### Post by phaze on 2006-08-23
Cheers, it was the DNS. The DNS address was set to my router, I changed the dns in system/admin/netowrking to the DNS address my router was using, oddly the first addresss did not work but the back-up one did. Thanks for help. :wink:

---

