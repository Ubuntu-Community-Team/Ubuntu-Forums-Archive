---
title: "Ubuntu 5.04 PPPoE Problem"
date: 2005-07-29
forum: Absolute Beginner Talk
---

### Post by ChristophorusX on 2005-07-29
Hello, I have recently installed Ubuntu on my computer , everything is working fine, but I can't figure out how to setup a dial-up PPPoE connection.

I have tried to do what is told on [http://ubuntuguide.org/](http://ubuntuguide.org/) but as I'm not connected to the internet I cannot use **wget -c [http://frankandjacq.com/ubuntuguide/rp-pppoe-3.5.tar.gz](http://frankandjacq.com/ubuntuguide/rp-pppoe-3.5.tar.gz)**, so I downloaded the file in Windows and copied it to a floppy disk and logged into Ubuntu as **root**.

There I copied the file to the /opt directory and tried to execute in the Terminal **sudo tar zxvf rp-pppoe-3.5.tar.gz -C /opt/** but again it didn't work.

It's very furstrating, because I really need my internet connection on Linux, when I first tried Knoppix 3.9 setting up the connection was so easy I just had to go to Knoppix >>Internet>>PPPoE.. and it took care of the rest and asked me about username and password , and after entering those I was connected.

Please could someone explain to me in a detailed way how to setup my PPPoE connection on Ubuntu ? Keep in mind that I have been using it for less than 1 day  :) 

Thanks !

---

### Post by adwait on 2005-07-29
Try the command
sudo pppoeconf

Any luck?

---

### Post by ChristophorusX on 2005-07-30
Thanks it worked !   :grin:

---

