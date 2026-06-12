---
title: "installing nvidia drivers"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by credadun on 2008-04-05
I just got a new 6200LE so i downloaded the latest drivers from nvidia.com but nothing iv tried has got the .run file to work. none of the commands iv tried have worked so im not sure if im making a mistake somewhere or if im trying to go about it the wrong way.thanx for helping

---

### Post by stefangr1 on 2008-04-05
You first have to log out, and then log in again in console mode (one of the options in the login screen). Then you cd to your installer file, and execute:

sudo sh ./nvidiablabla.run

Another possibility is to use a program called envy for an automated install of nvidia drivers.

---

### Post by bumanie on 2008-04-05
You would be better off trying the ubuntu supplied drivers first. System--> Administration --> Restricted Drivers. Click the small square to enable the driver and the driver should automatically be downloaded.

---

### Post by credadun on 2008-04-05
thanx alot. i think il give envy a try. for some reason i dont have restricted drivers in administrator menu, no idea why.

---

### Post by sisco311 on 2008-04-05
> **credadun said:**
> thanx alot. i think il give envy a try. for some reason i dont have restricted drivers in administrator menu, no idea why.
press Alt+F2 and type: ***restricted-manager ***to run the Restricted Drives Manager

---

### Post by credadun on 2008-04-05
thanx for the reference to envy it seems to have worked :)

---

