---
title: "Back track 5"
date: 2012-05-08
forum: Any Other OS
---

### Post by tronnix75 on 2012-05-08
I hope this is correct forum for security.  I have BT 5 installed on this spare pc i have.  its a dell dimension 2400 P4, 40gig drive 2 gig of ram.  I installed a earlier version of 5 and plan on running the update to the latest.  well few questions if i may.

1.)how do i check to see what ver i have of BT in the terminal 5. something.

2.) how do i check to see if all hardware the dell has is working chipset, video etc.  

3.)  are there updates that apply to all components, apps etc to BT same as ubuntu like windows update where you can run update manager?

4.)which Wireless card is supported I was interested in a USB one if need be this kind: 
	
ALFA AWUS036NH 2000mW 2W Wireless N/G USB WiFi Adapter

5.) :p

---

### Post by codemaniac on 2012-05-09
1./etc/issue file contents can tell you what the system version is .
2.You can run dmidecode command to check the hw details .
```
sudo demidecode --type bios
```
3.yes there are security and component updates available .
4.Here is a list of supported and tested wireless cards in Backtrack .
[http://www.backtrack-linux.org/wiki/index.php/Wireless_Drivers](http://www.backtrack-linux.org/wiki/index.php/Wireless_Drivers)

---

### Post by oldos2er on 2012-05-09
Moved to Other OS/Distro Talk.

---

### Post by Antman on 2012-05-09
> **tronnix75 said:**
> I installed a earlier version of 5 and plan on running the update to the latest.  well few questions if i may.

1.)how do i check to see what ver i have of BT in the terminal 5. something.

The current version of backtrack uses kernel 3.2.6. You can verify your kernel by running:
```
uname -a
```
at the terminal.

> **tronnix75 said:**
> 3.)  are there updates that apply to all components, apps etc to BT same as ubuntu like windows update where you can run update 
You just stated that you installed an earlier version of BT5 and **plan to update to the latest.** 
If you are trying to upgrade BT to the current R2 release, just follow the instructions listed here: [Backtrack link]("http://www.backtrack-linux.org/backtrack/upgrading-to-backtrack-5-r2/")

---

### Post by tronnix75 on 2012-05-09
thank you all for the info.  getting up there with udnerstanding linux.  long way to go though but im in.  thanks again. :p

---

### Post by Ms. Daisy on 2012-05-10
You're not using backtrack for an everyday operating system, are you?  You understand that it's a specialized tool kit created to conduct advanced and specialized security tasks, and that it is NOT designed for normal computer users?  You will have unending problems if you try to use it for normal, day-to-day operations.

---

### Post by codemaniac on 2012-05-10
Though BackTrack is not recommended for Linux beginners it should not cause "unending problems" to users .However people with no introduction to all the security tools bundled with backtrack, may get puzzled what to do with these hundreds of unheard binaries in menu.

---

### Post by tronnix75 on 2012-05-10
no i am not using it for everyday use as a workstation per se but to learn the Tools of the trade.  I have a degree in Info security and want to learn and learn more about penetration testing, wpa/wep crack and so forth.  this is strictly for lab purposes.  I use Ubuntu on my other Desktop for working purposes.   thanks for the feedback.

---

