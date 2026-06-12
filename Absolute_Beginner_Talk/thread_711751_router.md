---
title: "router"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by deadmnky on 2008-03-01
can any one recommend a good router that has ethernet ports for a direct desktop connections with a wifi signal for my laptop. i got a linksys today but idnt notice the tiny print that says for xp and vista only. damn impetuous buying. so i was going to return it tomorrow and get one that works well with linux and fairly easy to get up and running as well
thank you in advance

---

### Post by kool_kat_os on 2008-03-01
wrt54g/s it works for linux

EDIT: it works fine

---

### Post by kool_kat_os on 2008-03-01
Why does it matter what OS you have on your computer???

---

### Post by deadmnky on 2008-03-01
that was the one i got and figured it wouldnt since the dont put linux supported on a lot of things that i have noticed. ok i guess i will give it a try do i have to go through with the erasing of the Vxworks driver and re flash it for the linux drivers. i am unfamiliar wth setting up a router but wanted to give it a  try so i could work on the wirless card for the laptop. any info to move this along would be helpful or some sites for the right direction.
thank you for the quick responses

---

### Post by blastus on 2008-03-01
[Belkin N Wireless Router F5D8233-4](http://catalog.belkin.com/IWCatProductPage.process?Product_Id=372043)

It works great with Linux. You don't need Windows or a MAC. Everything is configured via a web browser by hitting [http://192.168.2.1](http://192.168.2.1).

---

### Post by AndyCooll on 2008-03-01
> **deadmnky said:**
> that was the one i got and figured it wouldnt since the dont put linux supported on a lot of things that i have noticed. ok i guess i will give it a try do i have to go through with the erasing of the Vxworks driver and re flash it for the linux drivers. i am unfamiliar wth setting up a router but wanted to give it a  try so i could work on the wirless card for the laptop. any info to move this along would be helpful or some sites for the right direction.
thank you for the quick responses

No. Routers are OS agnostic. You should (usually) be able to access your router settings simply by pointing your web-browser to the relevent IP address. E.g. your router address is usually 192.168.x.1, where the "x" is a 0,1 or 2. So by connecting your pc to your router and typing in 192.168.1.1 (return) into the web-browsers address on your pc, you should then be able to access your routers settings. 

As for assistance setting up your laptop to connect to your router, that depends on your laptop (and in turn what wireless card you have installed).

:cool:

---

### Post by deadmnky on 2008-03-01
cool i will try settin it all up now. the only instructions with  it are for win so i wasnt sure i will try to get it going now.
the laptop is a broad com i forget the number now i bought it off a friend other wise i would have chosen different components i will let you know what happens when i try the ip address.

---

### Post by deadmnky on 2008-03-01
ok so i tried the 192.168.1.1 it asked for a user name  and password whitch i dont have and was trying to set up with the cd but it is for win so i guess i would go about it by flashing it with this other system dd-wrt i believe. how would one go about it.
 does any one know of a way to set it up with out doing the flashing

---

### Post by Whiffle on 2008-03-01
It should give you the name/password in the manual for your router.

---

### Post by Rolcol on 2008-03-01
> **deadmnky said:**
> ok so i tried the 192.168.1.1 it asked for a user name  and password whitch i dont have and was trying to set up with the cd but it is for win so i guess i would go about it by flashing it with this other system dd-wrt i believe. how would one go about it.
 does any one know of a way to set it up with out doing the flashing
The default Linksys username is blank while the password is: admin

---

### Post by deadmnky on 2008-03-01
cool thank you the cd is the manual it says you have to go through the start up process i did not read much since it was geared toward windows users i was searching or linux instructions.coo we shall see what happens.

---

### Post by deadmnky on 2008-03-01
i checked the cd for any kind of password and user name but there was noe and admin would not work for the password to get into it to set it up.
the cd all says you need to go through the sutup wizard.

---

### Post by AndyCooll on 2008-03-01
The CD will say you need to go through the setup process ...but you don't! Ignore that information. The fact that you were being asked for a user name and password indicates that you (could) have access to the router settings themselves.  If you went through the CD setup process it would also ask you for the password sinceall that the setup process is is a friendly front end to get you going, nothing more nothing less.

So put the CD into your computer and explore the CD itself. On it is likely to be a user manual. Somewhere in that manual it will tell you what the defaults are. Otherwise download the manual from the website.

With regard to dd-wrt (which is great by the way), I'd walk before you start running. judging by the questions you are asking, just at the moment I wouldn't rush in and flash your router. First get a basic understanding ...then fair enough go ahead. Just that if it goes wrong, it's complicated to get it all back if you don't fully understand what you are doing.

:cool:

---

### Post by deadmnky on 2008-03-01
With regard to dd-wrt (which is great by the way), I'd walk before you start running. judging by the questions you are asking, just at the moment I wouldn't rush in and flash your router. First get a basic understanding ...then fair enough go ahead. Just that if it goes wrong, it's complicated to get it all back if you don't fully understand what you are doing.

:cool:[/QUOTE]

i would concur to that statement i went back and switched router to hopefully make this process easier. i now have a d-link wbr-2310 it says it will work with mac. sadly the people here i town are dumb when it comes to procuring linux friendly components, (maybe i dont knwo anyone here useing linux yet.
ok i got to set it up it seemed to wo rk and go through with all the info but would not let me on the internet via a wired connection. i was wondering if there was a command to find out all the info to manually enter the info for the router.
pleas excuse my ignorance i am really just setting up my frisr computer by myself and based on my comments earlier you can tell it is a lonely mission as far as physical bodies in my presence goes. serously thank you for all the support i dont know what i would do with out the ubuntu team to assist.

---

### Post by deadmnky on 2008-03-01
i got the desktop runnign through the router via direct connect so no i wil let you know any troubles with getting the laptop wireless chip working it may be  a b since it is a broadcom chipset i dont have the numbers yet just turned on the lap top so i will let you know.
thank to all or the assistance i say it a lot but mean it sincerely always

---

### Post by deadmnky on 2008-03-01
ok so i have everything set up i believe i connected to teh wifi signal i set up i have 73% strength but i can no tuse the internet yet with it what woul be my next step?
i get two wired connections just fine. i will post the ifconfig here in a second
sctrch that i have a white gnome term box and dont know how to copy the out put i xterm
but when i ran ifconfig it only showed eth0 eht1 so now i am stuck at this point any one know any one know of any good links
i have a broadcom 43xx chipset for a wifi card. not my choice.

---

### Post by deadmnky on 2008-03-01
solved it all works now thanks

---

