---
title: "At a loose end with PPTP..."
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by anarkistic on 2007-02-25
Hi everyone,

I hope someone can help me before I go nuts over this. 

Here's the situation/what I understand so far:

- To access the internet at my location, I need to dial into a VPN connection.

- To use VPN, i need the package network-manager-pptp, or the pptp-linux one from sourceforge. Or both.

- To get this package, I need to get it off one of the repositories, universe I believe.

**HOWEVER. **
I cannot get access to the repositories to get the VPN package I need, because I need a VPN package to get access to the internet in the first place!!

Catch-twenty-two it would seem.

Unless there was a way to download everything I need onto my windows PC? Then copy it across to the linux machine. But I dont know what to download or where from. If thats even a viable solution.

I'm sure hope someone can help!

---

### Post by karls0 on 2007-02-26
Hi,
I had the same problem at home (in Austria where we use PPTP for internet-connections). I downloaded the pptp-client from sourceforge and did a manual configuration (much like the last of my links suggest). 

You can get the pptp-client for linux at
[http://sourceforge.net/projects/pptpclient/](http://sourceforge.net/projects/pptpclient/)

There is also a thread in this forum
[http://ubuntuforums.org/showthread.php?t=91249](http://ubuntuforums.org/showthread.php?t=91249)

good instructions - if you have pptp-linux :( 
[http://pptpclient.sourceforge.net/howto-ubuntu.phtml](http://pptpclient.sourceforge.net/howto-ubuntu.phtml)

this could be helpfull (a GUI-client)
[http://home.gna.org/kvpnc/en/index.html](http://home.gna.org/kvpnc/en/index.html)

if you speak german, maybe this will help you too
[http://www.bytewise.at/knowhow/debian-adsl.html](http://www.bytewise.at/knowhow/debian-adsl.html)

If all this doesn´t help, try googling with "ubuntu pptp"

hth
Karl

---

### Post by anarkistic on 2007-02-26
Unfortunately most, if not all of these solutions require that somewhere along the line, my linux machine needs to connect to the internet.

Can anyone offer a solution to my problem on the basis that my linux machine has NO internet access at all. (Because it doesn't). However I do have a windows machine that does have internet access.

---

### Post by karls0 on 2007-02-27
> **anarkistic said:**
> Unfortunately most, if not all of these solutions require that somewhere along the line, my linux machine needs to connect to the internet.

How about a diskette or if you are in for this new stuff - a USB-stick :) ?

Karl

---

### Post by HereInOz on 2007-02-27
Can you connect to the Windows machine with a standard ethernet connection?  If so, you could enable Internet connection sharing on the Windows machine - you may need to install a network card to achieve this - and then connect your linux machine to the Windows machine and thence to the Internet.

I don't know how your Windows machine is connected to the Internet, but however it connects, you add another ethernet card if you haven't already got one spare, in the Windows machine, run the Network Setup Wizard (if it is XP) and enable Internet connection sharing.  Plug the Linux box into the Windows box with a crossover ethernet cable and you have them both connected.

Or have I totally missed the point??

---

### Post by jaredssix on 2007-02-27
Newbie here--
Am I to download each file listed (pptp, pptpconfig, and pptpconfig dependencies)?
When I click on any of the above files, several .rpm files are listed as as "subfiles". Am I to download each .rpm file, one at a time?
And where do I download the files to?

I am assuming that this vpn download applies to 6.06/Dapper.

Thanks!

---

### Post by walter.r on 2007-03-01
I solve this problem installing on Windows machine, that was able to connect to Internet, a freeware proxy software, like proxomitron or proxy+.
Then, I set in Ubuntu machine the IP address of the Windows machine and the proxy port in the proxy setting.
That's all. Ubuntu can connect Internet through Windows proxy software.

---

