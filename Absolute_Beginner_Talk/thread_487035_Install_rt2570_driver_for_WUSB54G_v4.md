---
title: "Install rt2570 driver for WUSB54G v4"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by j_macattack67 on 2007-06-28
I would like to install the driver for the WUSB54G v4 adapter on Fiesty.  Right now I have an Actiontec DSL modem hooked up so I can access the net.  I downloaded the .tar.gz file for the rt2570 driver.  Now how do I install that on my computer.  Thanks.

---

### Post by chili555 on 2007-06-28
If you right click the tar.gz, you will see the option, Extract Here. A folder will be created which will contain a README file and, perhaps, an INSTALL file. Generally, the instructions to install the module will be in one of these text files.

You will need to install *build-essential*. I suggest also installing *linux-headers-`uname -r`.* Usually, after that, you cd to the directory that was created, run in a terminal:```
make
sudo make install
```Some of these tar.gz are pretty old and may not compile correctly on your shiny new Feisty kernel. Post back if you get stuck.

---

