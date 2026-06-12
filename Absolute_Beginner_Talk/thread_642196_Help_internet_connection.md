---
title: "Help internet connection"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by florescu109 on 2007-12-16
Hello. I recently installed the latest Ubuntu. I am a new Linux fan. I have a big problem .... My internet provider uses a program through I can have acces to the internet. In order to use that program(CZONE) I have to install some software, manually(cause I can not connect to the internet...). The problem is I can't install 3 out of 4 programs. I.ve put  a screenshot ant the first 2 of the programs I should install here [http://www.filebox.ro/download.php?key=e6b23c6441c3ecaca6d013e4e4d9f4a0](http://www.filebox.ro/download.php?key=e6b23c6441c3ecaca6d013e4e4d9f4a0) . I guess I installed the first one, I guess, because I did not see any eroor. But when I followed instruction on the secont one(php) I get an eroor when I give the make command. Please help me, I do not know what to do.

---

### Post by duruttye on 2007-12-16
Have you tried to ask some help from de ISP? Maybe they can help you.

Untill then, it would be helpfull to see some error messages.

Gogd luck!

---

### Post by kajillin on 2007-12-16
My question is why do you need a program to connect to the internet. All your isp need is your mac address, and they connect you. You should call them see whats up. And i couldnt find thid czone your talking about what is it and what does it do, and most impotantly why do you need itt?

---

### Post by florescu109 on 2007-12-16
I asked them but I got the answer that I should know Linux...I will make a printscreen with the error messages and post it.

---

### Post by seventhc on 2007-12-16
No matter what your isp says, I don't think you need their software. I've had many different isp's in the past, all gave me software, but only used it in the very beginning. Once I figured out the settings I was able to connect without it. I used it when I knew absolutley nothing about computers and just did what I thought I had to do. Everything has a workaround. How do you connect??I would think only dial up would try to give software (thats what I was on at the time) Maybe some dsl isp's but it isn't needed as far as I know. Who's your provider?? What settings does the software want?? If your on cable or DSL you should be able to get in with your browser using an ip address. (maybe 192.168.0.1 or 192.168.1.1 but could be different depending on what make and model) Do you have a router?? give the specs of what your using and how it's set up. If you have windows set up already you can open the command promp and type ipconfig the default gateway should be your modem/router ip address and you can enter your settings there.

is this anything??
[http://mistypencil.wordpress.com/2007/11/29/internet-connection-sharing-czone/](http://mistypencil.wordpress.com/2007/11/29/internet-connection-sharing-czone/)

---

### Post by florescu109 on 2007-12-16
I have a cable connection. And a program that asks username and password. It is not dial-ul.

---

### Post by florescu109 on 2007-12-16
CZONE is a little program that asks for a username and a password. In Windows is very simple to use. You just install it, fill the username and password and it connects you to the internet. If you stop it, internet doesn't work.

---

### Post by CCNA_student on 2007-12-16
You should not need any software. All you should have to do is connect your cable internet connection to your cable modem, and then connect your modem to your computer or wireless router with an ethernet cable. That is what you do right?

    Sin Cere,

    CCNA_student

---

### Post by florescu109 on 2007-12-16
I have no modem. Cable, and this Romanian soft, CZONE :( Here it is [http://www.filebox.ro/download.php?key=8ac06dece535af3822ce758a6de9cffb](http://www.filebox.ro/download.php?key=8ac06dece535af3822ce758a6de9cffb)

---

### Post by CCNA_student on 2007-12-16
You have a cable internet connection without a cable modem? How do you connect to the internet then? What I mean is how is you cabling setup? And that link did not help much since it was not in English. Please give more details.

   Sin Cere,

   CCNA_student

---

### Post by seventhc on 2007-12-16
> **CCNA_student said:**
> You should not need any software. All you should have to do is connect your cable internet connection to your cable modem, and then connect your modem to your computer or wireless router with an ethernet cable. That is what you do right?

    Sin Cere,

    CCNA_student

If it's DSL there might be a user name and password in the modem and maybe change a setting  ( pppOe or pppOa) depending on the default configuration.

---

### Post by florescu109 on 2007-12-16
I will tell you the whole procedure : 
A)  Windows :
1) I install windows with a cable sticked in my network drive
2) I access a local page in Internet Explorer [http://acces.czone.ro](http://acces.czone.ro)
3) I download frome there a little program called Czone Installer
4) I run this Czone installer and install a program called Czone Agent
5) I run this Czone Agent and type a ussername and a password given by the intenet providerand I press connect
6) I am connectet to the internet, and that program is giving me a IP address, DNS, etc,


B) Linux : 
1) I install UbuntWwith a cable sticked in my network drive
2) I access a local page in Internet Explorer [http://acces.czone.ro](http://acces.czone.ro)
3) I download and install libmcrypt, PHP, Zend, Wget and Czone.sh
4) ...


The problem is that I can not install PHP... It gives me an error. I will switch to Linux and printscreen it in 15 min

---

### Post by xeth_delta on 2007-12-16
What is your ISP? I think that what you need to configure is pppoe. If you don't have pppoeconf yet, install it with:

```
sudo aptitude install pppoeconf
```

Run it, it will ask for user name and password, then run pon, and you should be good to go.

---

### Post by duruttye on 2007-12-16
For Romanian users there is an ubuntu derivate with some minor changes, including that pppoeconf with a gui interface. Im no expert by far, but last time I used it I managed to configure an USB modem without any problem. It is called Kiwi, and you can download it from kiwilinux.org. I think you can try configuring it from the live cd as well.

It is basicly the same solution xeth_delta suggested, but with some little modifications of the whole operating sistem.
It would be nice to see some errors when you get stuck with the installation.

Good luck!

---

### Post by florescu109 on 2007-12-17
Hello again. I tryed with installing ppoe but it doesn't work. Here [http://www.filebox.ro/download.php?key=04929f5f99ebbcbfa85ee601d184b56b](http://www.filebox.ro/download.php?key=04929f5f99ebbcbfa85ee601d184b56b) are two printscreen with the errors I get :(

---

### Post by florescu109 on 2007-12-17
I really appreciate your support. That's Ubuntu comunity !

---

### Post by xeth_delta on 2007-12-17
> **florescu109 said:**
> I really appreciate your support. That's Ubuntu comunity !

You are welcome! Can you please post the errors here, as text? I get an error while trying to access the link you gave us.

---

