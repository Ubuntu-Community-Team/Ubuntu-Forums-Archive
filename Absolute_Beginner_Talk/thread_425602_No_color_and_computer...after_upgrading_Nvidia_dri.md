---
title: "No color and computer...after upgrading Nvidia drivers"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by anadelady on 2007-04-27
Hi
 Im new here  I installef Ubuntu 6.10 sucessfuly about a month ago no problems and upgraded 
to 7.04 no problems.then I decided to enable desk top effect.It said it had to install Nvidia drivers
I said yes Install ,everything is fine until I reboot I have a Kaser Nvidia Geforce FX5200 128 MB video 
card  .The problem is the computer starts fing get thru the loading screen then turns to back and
screen that I can't make heads or tails of cant log in or nothing How do I get into safe mode and 
once there how do I fix this?
any help is very appreciated
Thank you
anadelady

---

### Post by Martin on 2007-04-28
Hi. Same thing has happened to me. Try this. Start the pc and let it get to where it normally gets. Now my memory gets hazy but I am sure there is a combination of the alt key plus one of the function keys (F1 or F2 etc) that when pushed together kills the x windows system so that it does not automatically restart. If that works (let me know if it doesn't) and you end up at a console type "sudo dpkg-reconfigure -phigh xserver-xorg" and answer the questions. This will recreate a new xorg.conf file. Once it has finished type sudo startx and you should have your system up and running again.

---

### Post by overdrank on 2007-04-28
> **Martin said:**
> Hi. Same thing has happened to me. Try this. Start the pc and let it get to where it normally gets. Now my memory gets hazy but I am sure there is a combination of the alt key plus one of the function keys (F1 or F2 etc) that when pushed together kills the x windows system so that it does not automatically restart. If that works (let me know if it doesn't) and you end up at a console type "sudo dpkg-reconfigure -phigh xserver-xorg" and answer the questions. This will recreate a new xorg.conf file. Once it has finished type sudo startx and you should have your system up and running again.

Hi I believe what you are saying is ctrl,alt,f1 through f7 just opens the terminal, ctrl,alt, backspace will restart x. :-k

---

### Post by Martin on 2007-04-28
Thats cool. as long as you end up with a terminal where you can type in the command. In the past I was having to redo my x config on an almost daily basis.

---

