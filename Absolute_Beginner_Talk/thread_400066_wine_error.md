---
title: "wine error"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by slavisa4ec on 2007-04-03
i get this when i try to start win app for my cash register

slavisa4ec@DarkLady:~/PUNJAC$ wine Punjac.exe
fixme:comm:set_queue_size insize 1024 outsize 1024 unimplemented stub
wine: Unhandled page fault on read access to 0x00000000 at address (nil) (thread 0009), starting debugger...
Modules:
Cannot get info on module while no process is loaded
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
00000008 (D) (null)
        0000000d    0
        00000009    0

any suggestions????
btw, i didnt configure wina at all, i dont know how :(

---

### Post by mikeyphi on 2007-04-03
Did you run 'wine cfg' after installing wine?

---

### Post by slavisa4ec on 2007-04-03
yes, i have started the application, but i cant do nothing with it, allways says: "error with communicating with cash register" and thats it.... I guess i will have to install vmware with Win98 just tu work with my cash register, or are there any other suggestions?

---

### Post by david_kt on 2007-04-03
Is your cash register supposed to run on windows or DOS? Windows could run dos program. But in linux, you need to run it under Dos emulator instead of wine. You could try Dosbox.

Please let us know more about your software you want to run, link to trial software if possible so that we could try it.

DK

---

### Post by mikeyphi on 2007-04-03
> **slavisa4ec said:**
> yes, i have started the application, but i cant do nothing with it, allways says: "error with communicating with cash register" and thats it.... I guess i will have to install vmware with Win98 just tu work with my cash register, or are there any other suggestions?

If you do decide to install vmware, have a look here: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Virtual_Machine_Manager_.28VMware_Server.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Virtual_Machine_Manager_.28VMware_Server.29)

---

### Post by slavisa4ec on 2007-04-03
unfortunatly there is no link to this software... what could i say, I am from Serbia, where internet dont have more then 90% people :(

i start the program but when i try to connect with my cashreg i get error: error with communicating with device" on my language...

---

### Post by Lucifiel on 2007-04-03
> **slavisa4ec said:**
> unfortunatly there is no link to this software... what could i say, I am from Serbia, where internet dont have more then 90% people :(

i start the program but when i try to connect with my cashreg i get error: error with communicating with device" on my language...

Do you mean you can't find the program? If so, try this link(and VMware player is free if you don't want to try Server):

[http://www.vmware.com/products/server/](http://www.vmware.com/products/server/)

---

### Post by david_kt on 2007-04-03
> **slavisa4ec said:**
> unfortunatly there is no link to this software... what could i say, I am from Serbia, where internet dont have more then 90% people :(

i start the program but when i try to connect with my cashreg i get error: error with communicating with device" on my language...

I am not sure whether it is program issue or device issue. If you said it already started the program, than wine should be ok. What you could do is to check the device connection, may it is not detected.

If the device is not detected, there is no use (imo) even if you install emulator. And to run operating system in emulator also require you to have license of that operating system. So, could you investigate more detail of your problem?

DK

---

