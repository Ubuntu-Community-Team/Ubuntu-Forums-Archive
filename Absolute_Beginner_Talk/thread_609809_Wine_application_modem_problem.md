---
title: "Wine application modem problem"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by mastromitsos on 2007-11-11
Hello all,

I run a Windows application (Avaya Site Administrator) to access pbxs via modem or TCP with wine .
I have installed Connexant drivers on modem of laptop and it is workin fine under Linux (KPPP, minicom).
Although the application works fine when using TCP connection via KPPP  i cannot use  modem  . When trying to connect i get an "rx serial error".

i have tried ln -s /dev/modem       COM1,2,3,4(modem runs on Com3 normally)
                              /ttySHSF0
                              /ttyS0,1,2,3,,etc  
When i configure a wrong port i get a "device not ready" , when use possible modem setting (/dev/modem ---/dev/ttySHSF0)  i get a reply "serial rx error "

Is there something i should configure and i missed .
Any help welcome , thanks in advance .

---

