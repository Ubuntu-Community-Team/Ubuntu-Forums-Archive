---
title: "yet another'can't conect to internet"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by petsno123 on 2007-11-01
My question is similar but with different details to otheres.I have installed ubuntu Feisty Fawn and am really enjoying getting to know it!Now I wish to connect to the web.Have gone into System and SynapticPackage Manager.Neither led me into how to install my QvisLink Evo-W54PCMv2 cardbus G-Wireless adapter.Have managed to indicate that this is a 'wireless connection.No indication that things had been recognised  happenedI could give the details of my set'up but that seems pointless for now.Can see how the size of memory,speed of CPU and video card would help with the problem.Have read the many pages of both the ubuntu installing info and the pcmech articles on 'Windows to Ubuntu Transition Guide.Both said very,very little about the details of submitting SSID and WEP,26 digit encripition code.Can anyone advise me on these necessary details for connecting to the net.Thank you all,petsno123.

---

### Post by damotor on 2007-11-02
if your network interface is in eth0, your essid is myessid and your password is the string password:
> sudo iwconfig eth0 essid myessid key s:password
if your network interface is in eth0, your essid is myessid and your password is the hexadecimal value 00112233445566778899aabbcc:
> sudo iwconfig eth0 essid myessid key 00112233445566778899aabbcc
I think you should use the second one, to see what network interfaces do you have type > iwconfig and use the one with wireless extensions.
Once you've got the right settings use the graphical network manager or edit /etc/network/interfaces and it will be fine the next time you reboot

---

