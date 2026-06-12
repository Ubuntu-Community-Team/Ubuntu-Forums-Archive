---
title: "[SOLVED] Sharing Printer with Gutsy"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by shaft350x on 2007-12-08
I have two computers both running Gutsy, and I cannot share the printer between the two of them.

The printer is connected to the desktop, and I had it shared when the computers were running Feisty.  Any help would be appreciated.

---

### Post by nikoPSK on 2007-12-08
it would help if you listed the model name and manufacturer.

---

### Post by shaft350x on 2007-12-08
The printer is an HP PSC 1510

---

### Post by nikoPSK on 2007-12-08
have you tried hplip?

---

### Post by shaft350x on 2007-12-08
well according to synaptic I have hplip installed.  Though looking at the printer setup I seem to have hpijs in use.

---

### Post by nikoPSK on 2007-12-08
goto hplip.sourceforge.net and download install and follow the instructions.

---

### Post by shaft350x on 2007-12-09
Ok, I did install it, it successfully printed from the host computer.  But the other computer still doesn't seem to see it.  I checked it to share the printer, and to have the other one look for shared printers.

(Thank you for the help so far, I do appreciate it)

---

### Post by nikoPSK on 2007-12-09
well, sorry, that's about as far as I can go as I do not do shared printing. Sorry, 9is it ubuntu and xp that's sharing???)

---

### Post by shaft350x on 2007-12-09
No they are both Ubuntu systems.  Just upgraded them to Gutsy.  I had the printer working and shared under Feisty.

---

### Post by shaft350x on 2007-12-09
as an aside, I followed the directions on the HPLIP site, and the folder is now installed on my desktop.  Can I move it without causing problems?  Or will I have to put it somewhere else and install it there?

---

### Post by HereInOz on 2007-12-09
You need to change the cupsd.conf file in /etc/cups to have the second section read like this

# Only listen for connections from the local machine.
Listen localhost:631
Listen /var/run/cups/cups.sock
Listen 192.168.1.3:631

Change the last line so that the ip address is that of the machine hosting the printer.  Do not forget to add the :631 at the end of it.

You then access the printer from the other machine as an internet printer, using the address of [http://192.168.1.3:631/printers/name_of_printer](http://192.168.1.3:631/printers/name_of_printer)
Change 192.168.1.3 to the ip address of the printer host, and name_of_printer to the actual name of the printer on the host machine.

Hope this helps

---

### Post by stchman on 2007-12-10
> **shaft350x said:**
> I have two computers both running Gutsy, and I cannot share the printer between the two of them.

The printer is connected to the desktop, and I had it shared when the computers were running Feisty.  Any help would be appreciated.

I have a procedure to share printers with Feisty to other Ubuntu and Windows machines.  It is actually very easy.

[http://www.stchman.com/share_printer.html](http://www.stchman.com/share_printer.html)

For Gutsy you have to do some things a little different.

[https://help.ubuntu.com/community/NetworkPrintingFromWinXP](https://help.ubuntu.com/community/NetworkPrintingFromWinXP)

Follow the first part about how to enable printer sharing in Gutsy.

---

### Post by shaft350x on 2007-12-10
Ok so I finally got it to work.

I sort of did what HereInOz recommended.

[QUOTE=HereInOz]Change the last line so that the ip address is that of the machine hosting the printer. Do not forget to add the :631 at the end of it.[/QUOTE]

Except that I did that IP address of the **client machine**.  Although I am not sure if this step was necessary, as I had already gone into printing and shared the printer.

On the client machine (laptop) I went to System > Administration > Printing.  Then I went to New Printer, and selected **Internet Printing Protocl (ipp)** in the host box I entered the IP of the host computer (desktop with printer attached).  I hit the Find Queue button and it found the printer connected to the host computer, and also put in the URI which was **IPP://192.168.1.xxx/printers/Printer_Name**  (it was IPP instead of HTTP)

Also on Firestarter it had already detected the attempts by the client computer to attempt printing before, so I had already given it permission to connect on port 631.

---

### Post by ghoran on 2007-12-18
THANKS FOR THIS THREAD!

I had great success and I think I skipped some steps that can be left out with 7.10.

I do not mean to insult anyone I just think that the latest UBUNTU may take care of things that you gurus had to do in the past.

I did something VERY similar.
I installed 7.10 and took all the updates on two computers.
Computer One has an HP PSC1507 all-in-one attached through a USB port.
Computer One simply saw the printer and prints to it. I did not install HPLIP.

SETUP SHARING: From computer One I did need to setup sharing:
1) Open the Printing window (System -> Administration -> Printing).
2) Click Server Settings in the list of printers.
3) To the right, under Basic Server Settings, check the box that reads, "Share published printers connected to this system". 

DETERMINE PRINTER DRIVER: On computer One find out what printer Driver you are using:
1) If you closed the Printer configuration dialog, reopen it (System -> Administration -> Printing).
2) Click the printer on the left. See the make and model. 

DETERMINE IP ADDRESS OF COMPUTER ONE: 
1) Open a terminal. ( Applications -> Accessories -> Terminal )
2) Type: ip addr 
3) hit enter
4) See the inet value under eth0. Something like 192.168.0.xxx where xxx is a number for your machine. This is the ip address of Computer One

SEEING THE PRINTER FROM COMPUTER TWO: 
From computer Two:
1) Open the Printer configuration dialog. (System -> Administration -> Printing -> New printer)
2) In the New Printer dialog choose :Internet printing protocol
3) Type the ip address of computer one in host (192.168.0.xxx)
4) Click find queue
5) PSC_1500_series showed up as a queue.
6) Click on it and choose OK
7) Click forward on the new printer dialog box.
8) After a few seconds a list of printer drivers come up.
9) Choose hp and clicked forward.
10) Select the model based on finding it on Computer One (DETERMINE PRINTER DRIVER) above and click forward.
11) The next dialog box you can fill in with whatever makes sense to you.
12) From the Printer configuration dialog box select the printer on the left and choose print test page. 

VIOLA!!!

---

### Post by shaft350x on 2007-12-18
I had been thinking of revisiting this thread and writing up a concise HOWTO on this for anyone who experienced difficulties like I did.  So I'm glad that our working this out was helpful to you, and thank you for your well written HOWTO of the relevant steps.

---

### Post by ghoran on 2007-12-18
Thanks for the compliment. I enjoyed writing the "how to".
This forum is awesome and I am happy with any way I can help.

---

### Post by rob.webinator@gmail.com on 2008-02-07
I followed ghoran's howto but I'm stuck at the "Scanning..." for IPP printer on computer 2.  IPP Browser scans for about 5 minutes then says "No queues".  I do not have ICMP filtering turned on on either computer 1 (server) or computer 2 (client) and I can ping between these computers.  Printing on computer 1 works great.  The printer is a HP C4100 and I'm using hplip.

Any ideas?

Rob

---

### Post by shaft350x on 2008-03-06
Rob have you been able to work through the problem yet?  I haven't really checked in on this thread, and I'm not really much of an expert, as you'll notice I got through this basically by trial and error until I got it to work thanks to some of the advice from others.

I'm assuming that you've upgraded to Gutsy even though your profile shows Dapper.  Which would have been my first guess but you wouldn't have chosen this thread I don't think if that were not the case.

If you can ping and "see" the computer with the printer attached, but not the printer itself I would guess the issue may be to do with the sharing of the printer connected to the first computer.

If you are still having this problem (I hope you're not since it has been quite some time since you posted) you may want to start a different thread, as I don't know that many of the more experienced users check on threads that are marked Solved.

---

### Post by texasjim on 2008-03-07
Great HOW-TO.  With this post and the one at

 [http://ubuntuforums.org/showthread.php?t=487890](http://ubuntuforums.org/showthread.php?t=487890)

I was finally able to get an inherited Canon Pixma ip1500 installed, printing, and networked in 
about an hour.  Now when my forehead heals from all the bashing I'll try it from my sister's
windows system.
Thanks a bunch.
  Jim

---

