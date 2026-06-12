---
title: "Configuring Winmodem and not winning"
date: 2006-02-26
forum: Absolute Beginner Talk
---

### Post by agarwaldvk on 2006-02-26
Hi Everybody

I was trying to configure my WinModem in Ubuntu.

Got ScanModem and ran it.

Then downloaded the binary zipped file from Linuxant and tried to run the command to build essential header-'uname -r'

Tried to run the following 2 statements from the relevant 'HowTo' document.

> If compiling from source
On your way to configuring your modem drivers, you may find out that you need to compile from source (which means, typing commands beggining with sudo make). In that case, prior to compiling, do the following: Insert installation CD 

sudo apt-get update
sudo apt-get install build-essential linux-headers-`uname -r`

The first statement went OK.
The second one, it complained that cannot find package 'uname -r'.

The ran the "uname -r" command on the terminal and got the output as :-

2.6.10-5.


Just for information, the ModemData.txt file indicated the Modem type as :-
125d....

which I take is one of those that can run within Ubuntu!!!!!!!!!!!

Any further suggestions on what can I do next?


Best regards



Deepak Agarwal

---

### Post by andrewsawyer on 2006-02-27
You could just try ```
sudo apt-get install build-essential linux-headers-2.6.10-5
```
and see if that works.

---

