---
title: "How to connect a Linux Mint 11 system to a network printer(hp LaserJet M1132 MFP)."
date: 2011-08-02
forum: Any Other OS
---

### Post by ragesh.g on 2011-08-02
:confused:  I tried installing hplip3.11.7 on the Linux Mint machine but no success. It doesnt detect the printer in network which is connected to another pc using Fedora 15. I used samba to connect the printer to the network as one pc in the network works on windows. The Windows machine is connected to the printer now. But I want to connect other 2 machines which are using Linux Mint. I also tried using Cups but again it doesnt show the correct printer model no. I also tried using Administration option in Cups but didnt succeed as I had no clue how to configure it. Please help me I need to resolve it soon coz I've been trying this for past 3 days.

---

### Post by Perfect Storm on 2011-08-03
Moved to Other OS/Distro Talk.

---

### Post by Kromgol on 2011-08-03
Edit: Nvm i got it all wrong :D

---

### Post by skits on 2011-10-02
Like many others, I have spent a ridiculous amount of time trying to get printing going after installing Linux Mint 11. I tried many things I found in these and other forums with no success. Yet printing was working before the install and still was working from a W98 box on the network so I knew the printer, miniport and network were all OK.

My configuration: small home network, wired ethernet connection to  IOGear miniport print server (ip address 192.168.0.111) with USB cable to Brother HL-1435 laser printer.

The clue was here:
[http://forums.freebsd.org/showthread.php?t=21874](http://forums.freebsd.org/showthread.php?t=21874)

It's not a printer or network or miniport issue, it's a cups configuration issue. I browsed to the cups admin page (type in the address bar of the browser localhost:631). I had to set the printer connection as a socket
socket://192.168.0.111
then go through the steps selecting the printer manufacturer and model.
Voila! 

I hope this helps someone else.

ps: for the sake of completeness - the step before this was to go to the Brother Solutions site and follow their instructions to download and install their lpr and cups drivers for my printer. It didn't solve the problem at the time, but maybe ..... it may have helped with the last step?

---

