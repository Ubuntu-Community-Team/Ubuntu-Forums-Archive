---
title: "cant connect to dialup with three modems"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by usr001-25-8387 on 2007-08-10
have tried hsf modem.  usrobotics, and compaq system.  conflicts with lan and ppo dialup.  

changed to dual boots and the installation goes fine but then the windows dialup messed up too.

now i have xp on the emachine with the hsf modem and the compact is loaded with only feisty dawn. 

synaptic fails and cannot use update manager.

have the ubuntu linux bible.  and have gone thru the beginners installation,  can get some of the softwqre to work but cannot update or stay connected with dialup.

the bloom is off the rose.  please someone help me.
james](*,):lolflag:

---

### Post by edwardLS on 2007-08-10
I am running a multi-boot system which includes Dapper Drake and Feisty Fawn.  I have a USRobotics Modem and it works very well with Dapper Drake, but I have had problem with dialup under Feisty.  From much reading here on the forums, it is my understanding that dialup was broken in Edgy Eft (release between Dapper and Feisty) and further broken in Feisty.  Those that seem to have success with Feisty and Dialup have been using an older release of the kernel.  
I have dialup (with the USRobotics) working under Feisty, but not as I would prefer.  I use Dapper as my main productive Linux installation, and just play with Feisty.  In System -> Administration -> Networking I activate the dialup modem connection.  That fails, but the system continue to think that I have an active connection.  When I next boot into Feisty, during the bootup, the modem comes to life and dials and connects to my ISP.  If I deactivate the connection, and then later attempt to activate it again, it fails as before.  So, I just leave the dialup in an Activated state.
Good luck.

---

### Post by usr001-25-8387 on 2007-08-15
thanks edward, still unable to connect. dell released a new driver but cant get ubuntu to open it.

bought an old compaq presario and it loaded edubuntu and not ubuntu,from the same 7.04 cd.  

manually configured but it wont dial.

im lost and really want to use ubuntu on the compaq and looking for a laptop that is cheap but will take broad band.

not able to get gnome-ppp, synaptic or the package manager to work.

thanks for trying edwardls
james

im on the dedicated xp emachine.  impressive, eh.

---

### Post by plucky on 2007-08-15
There is a website that has debian packages for HSF and HCF modems for UBUNTU
The free version only runs at 14.4K max but you can purchase a license to run at 56K.
You need to run the scan modem utility to identify your modem and then choose the right package.


[HTML]http://www.linuxant.com/drivers/[/HTML]

I managed to get an HCFV90 Coexant modem running using this driver and Gnome-ppp

Best of luck

---

### Post by usr001-25-8387 on 2007-08-15
tried the hsf route and even when it connected it was too slow .   eventually i want to put together a server.

i want to do this with ubuntu  because it the peoples os; 

thanks anyway plucky.

---

