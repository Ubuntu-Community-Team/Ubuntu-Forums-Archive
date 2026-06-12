---
title: "MAKE prefix=/ ????"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by ckn on 2007-04-26
im a long time windows user :P

and first time linux/ubuntu user, i installed it recently and have experimented on how to get things running.

it seems i am running a ac97 software modem on my asus w3 centrino notebook.

so i used scanmodem tool and downloaded the appropriate driver, seemed to install fine.

i then went to terminal and did the ppgconfig thing.. and set up my dial up,
did pgo, then plog...and it came up as "cant get terminal parameters: input/output error, device ttyS1 is locked by pid 5604"

now i want to use wvdial, because i heard that is an altern dial app.

but i open the install how to... and it gives me this "make" and prefix and "as the root"

im completly confused...please could someone guide me?

---

### Post by Seisen on 2007-04-26
Can you post exactly what is says for make and the prefix, I think  I understand what you are asking but I need more information.

---

### Post by annda on 2007-04-26
you don't need to compile wvdial, it is available in the repositories.

---

### Post by ckn on 2007-04-26
what do u mean repos?

i am very new to linux u need to understand...

could u tell me....how i could open wvdial ????

i need a connection on the linux...also here is the instructions that confused me...:


Installation of WvDial 
Install WvDial by running the following commands: 

make PREFIX=/usrNow, as the root user: 

make PREFIX=/usr installConfiguring WvDial 
Config Files 
/etc/wvdial.conf and /etc/ppp/peers/* 

Configuration Information 
Perform the following two commands as the root user: 

touch /etc/wvdial.conf &&
wvdialconf /etc/wvdial.confwvdialconf will test that you have a working modem and try to determine its exact setup. You will then need to enter your ISP's phone number, login name and password into the /etc/wvdial.conf file. 

You then start wvdial with:

---

### Post by annda on 2007-04-26
i mean you can install it by simply typing this in the terminal:
sudo apt-get install wvdial

as for configuration, you will have to consult the website.

running programs is usually as simple as typing the name in the terminal.

---

### Post by ckn on 2007-04-26
-_-'

im so confused... i just want to connect to dial up.....-_-'

---

### Post by solarix on 2007-04-26
> **ckn said:**
> -_-'

im so confused... i just want to connect to dial up.....-_-'


:)  Don't be confused.  

1. step

Open a terminal please:

2.  now we're searching for wvdial package. Write now in your terminal

```
sudo apt-cache search wvdial 
```

now you will have an output for wvdial 


```
 apt-get install   wvdial 

<,and the other related packages shown by apt-cache> 
```


At least

```
  sudo wvdial /etc/wvdial.conf 
```


Hope that helps

---

### Post by ckn on 2007-04-26
ill go and try that, ill have to reboot into ubuntu then come bak to xp to connect. thanks...also where will i find the program once i install it?

---

### Post by ckn on 2007-04-26
hey, i did those steps....

and i got a reply....

no username
no phone number
no password....


so i DONT KNOW :(

LOOK... could u PLEASE tell me how to install programs and run them....

i have alot of programs im trying to use...but they open in a tar,zip,gz file..... and are all spread out files...
no installation...if u could tell me step by step how to install these i could do it! ...thanks u

---

### Post by solarix on 2007-04-27
> **ckn said:**
> hey, i did those steps....

and i got a reply....

no username
no phone number
no password....



so i DONT KNOW :(

LOOK... could u PLEASE tell me how to install programs and run them....

i have alot of programs im trying to use...but they open in a tar,zip,gz file..... and are all spread out files...
no installation...if u could tell me step by step how to install these i could do it! ...thanks u



Look you have to put in to username  your Username from your Provider  the Phone Number to which your Modem is responding. And the Password for this.


Maybe i unterstand something wront but what Do you want with Programs in tar.gz

Programs in tar.gz  are mostly Sourcecode Tarballs. What Do you want with Source Code Tarballs when you could get  the Binary Versions with apt-get and Synaptic.

It may be easier to help you if you could describe what do you want to do.

Thanks in advance for it.  :)

---

