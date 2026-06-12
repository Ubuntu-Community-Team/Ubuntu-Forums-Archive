---
title: "can't dial-up - resolv.conf trouble"
date: 2005-11-29
forum: Absolute Beginner Talk
---

### Post by Books on 2005-11-29
Today I installed Kubuntu Breezy (yay!). During the install it said that something called DHCP failed and it offered to let me set it up manually. Since I didn't know what to tell it to do I selected to set it up later. When I started KPPP to configure dial-up it said that resolv.conf was missing. I'm guessing that the DHCP failing was the cause of this.

"[I]Error - KPPP
/etc/resolv.conf is missing or can't be read!
Ask your system administrator to create this file (can be empty) with appropriate read and write permissions.[/I]"

I searched and found a post that said to create the file by pressing Alt+F2 and then "kdesu kwrite /etc/resolv.conf". I left the file empty and pressed "save". I started KPPP didn't pop up the error anymore. I found my serial modem on /dev/ttyS1 and tried to dial in. Now it is popping up an error message that it can't authenticate for some reason. :confused: (I saved the error message to /home/ but I can't access it under Windows :rolleyes:) Is this still due to resolv.conf ?

I checked my password and dial-up username - they are ok. There is some setting called "pap/chap" and I have no idea if that's right; I'm on Earthlink dial-up if that makes any difference.

Thank you for your help!!!

Books

---

### Post by Danielle on 2005-11-29
hi, Books. if you are getting PAP/CHAP errors it means you aren't able to talk to your ISP to get an IP address. i had the same problem, what i did was find the name of my modem then do a search for my modem on the forum.

---

### Post by blastus on 2005-11-29
What's the error message?

---

### Post by Books on 2005-11-29
[QUOTE=Danielle]hi, Books. if you are getting PAP/CHAP errors it means you aren't able to talk to your ISP to get an IP address. i had the same problem, what i did was find the name of my modem then do a search for my modem on the forum.[/QUOTE]

Thanks, Danielle and blastus

I just checked and my resolv.conf file is empty. I don't know if the error is a PAP/CHAP error (whatever that is). I searched and found a post saying that Earthlink uses PAP, so that might not be the problem. Here is the error message I'm getting. I'll try to dial up and the modem will make some noises and then there is a long SHHHHHHHHHHHHHH sound, then it hangs up. The report says:

[FONT="Courier New"]localhost pppd [7523]: The remote system is required to authenicate itself
localhost pppd [7523]: but I couldn't find any suitable secret (password) for it to use to do so.
localhost pppd [7523]: (None of the available passwords would let it use an IP address.)[/FONT]

I checked my password and username, they are fine.

Thanks!

Books

---

### Post by Danielle on 2005-11-29
i don't really know, but it sounds like a PAP error. what it does is authenticate who you are with a secret handshake. when it confirms you are who you say you are it will give you an IP address. it sounds like the handshake isn't working. it would be best to do a search for the error.

it wont be your password and username it uses something else.

---

### Post by Books on 2005-11-29
[QUOTE=Danielle]i don't really know, but it sounds like a PAP error. what it does is authenticate who you are with a secret handshake. when it confirms you are who you say you are it will give you an IP address. it sounds like the handshake isn't working. it would be best to do a search for the error.

it wont be your password and username it uses something else.[/QUOTE]

Thank you for helping! I can't figure this out, unless the fault is with resolv.conf which is an empty file. When I was setting up KPPP I forgot to put in the DNS settings. (I never had to do that under Windows, so I didn't know.) I put "earthlink.net" as the domain under the DNS tab and it didn't work. I looked up the manual earthlink DNS numbers and they didn't work either.

/etc/resolv.conf was missing after the install when I first started KPPP. The only thing that went wrong in the install was that DHCP failed to set up. I don't have a local network so I thought it wasn't an issue; there was an option to set it up later so I chose it. I manually replaced resolv.conf by Alt+F2 and "kdesu kwrite /etc/resolv.conf" then saving the blank file. The file is still blank.

What does /etc/resolv.conf do, anyway?

If DHCP not being set up by the installer is the problem, how can I do it? Do I need to run the installer again?

Thank you SO MUCH for helping, to all who have posted!!!

Books

---

### Post by Danielle on 2005-11-29
[QUOTE=Books]Thank you for helping! I can't figure this out, unless the fault is with resolv.conf which is an empty file. When I was setting up KPPP I forgot to put in the DNS settings. (I never had to do that under Windows, so I didn't know.) I put "earthlink.net" as the domain under the DNS tab and it didn't work. I looked up the manual earthlink DNS numbers and they didn't work either.

/etc/resolv.conf was missing after the install when I first started KPPP. The only thing that went wrong in the install was that DHCP failed to set up. I don't have a local network so I thought it wasn't an issue; there was an option to set it up later so I chose it. I manually replaced resolv.conf by Alt+F2 and "kdesu kwrite /etc/resolv.conf" then saving the blank file. The file is still blank.

What does /etc/resolv.conf do, anyway?

If DHCP not being set up by the installer is the problem, how can I do it? Do I need to run the installer again?

Thank you SO MUCH for helping, to all who have posted!!!

Books[/QUOTE]
are you using windows ATM? if so the command is Start>Run>cmd> ipconfig /all

that should give you two DNS servers.

the DHCP is the same as the PAP stuff and the conf file is probably the file that has the infomation, but i'm not sure.

i'd lookup the error with the name of your modem to find the answer.

---

### Post by Books on 2005-11-29
[QUOTE=Danielle]are you using windows ATM? if so the command is Start>Run>cmd> ipconfig /all

that should give you two DNS servers.

the DHCP is the same as the PAP stuff and the conf file is probably the file that has the infomation, but i'm not sure.

i'd lookup the error with the name of your modem to find the answer.[/QUOTE]

Hi, Danielle

Thank you for helping! My modem is a external serial Creative Modem Blaster V92. I did find something on this forum that was interesting. The thread **[pppd dies on connect to earthlink]("http://ubuntuforums.org/showthread.php?t=49447")** describes my problem almost exactly -- and we both use Earthlink -- but the poster didn't get an answer. :(

---

### Post by Danielle on 2005-11-29
i was just reading through some tutorials and i found this. i don't know what modem you have but if it's an ADSL PPPoE this might help.
[https://wiki.ubuntu.com/ADSLPPPoE](https://wiki.ubuntu.com/ADSLPPPoE)

---

### Post by blastus on 2005-11-29
[QUOTE=Books]Here is the error message I'm getting. I'll try to dial up and the modem will make some noises and then there is a long SHHHHHHHHHHHHHH sound, then it hangs up. The report says:

[FONT="Courier New"]localhost pppd [7523]: The remote system is required to authenicate itself
localhost pppd [7523]: but I couldn't find any suitable secret (password) for it to use to do so.
localhost pppd [7523]: (None of the available passwords would let it use an IP address.)[/FONT]

I checked my password and username, they are fine.[/quote]

"sudo nano /etc/ppp/peers/kppp-options" and change "#noauth" to "noauth"

---

### Post by Books on 2005-11-29
[QUOTE=blastus]"sudo nano /etc/ppp/peers/kppp-options" and change "#noauth" to "noauth"[/QUOTE]

Thanks, blastus. I did that and I can now connect to the internet -- sort of -- but only at 9600 baud. (Ouch!) I set it for the higher setting and lower settings, but each time it settles on 9600 baud.

It's a *serial* Creative Modem Blaster external v.92. I know the PCI Blaster versions are Conexant HCF modems and won't work with Linux, but I got a serial modem because serials are known for Linux compatibility... at least I thought.

So my question is... is the problem in this thread "solved" and being stuck on 9600 baud is *another* problem, or it is the same problem?

Thank you!

Books

---

