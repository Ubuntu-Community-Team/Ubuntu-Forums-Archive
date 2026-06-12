---
title: "Connecting through modem"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by S15_88 on 2007-06-14
when using My desktop PC to connect to the internet I click on the sympatico icon, type in my password then it connects through an ethernet cable to a modem then out the modem through the phone line. Now if i took the ethernet cable out of the PC and plugged it into my laptop with ubuntu how would i connect? does sympatico have to be installed to allow me to enter the password or can i even connect without using the password?? Any help would be greatly appreciated

Thanks, Alain

---

### Post by RedSquirrel on 2007-06-14
Sounds like you have ADSL internet access.

Have a look at this:

[https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html#modems-adsl-pppoe](https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html#modems-adsl-pppoe)

You open a terminal, Applications -> Accessories -> Terminal.

type: 

```
sudo pppoeconf
```This command will ask for your Ubuntu login password. Then just follow the instructions.

There will be a question about connecting at startup... you probably don't want to do that.

Instead, once you're done configuring the connection,
you'll want to manually connect with:

```
sudo pon dsl-provider
```and disconnect with

```
sudo poff dsl-provider
```

---

