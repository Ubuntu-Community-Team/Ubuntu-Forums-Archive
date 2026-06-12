---
title: "Gutsy: DSL wired connection works only for google"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by swarup on 2008-03-07
I have just installed Gutsy on my laptop, and am trying to get my wired DSL broadband to work. The DSL broadband is working fine I know, because it works wonderfully with my desktop (Win XP). When I connect it my Gutsy laptop, I can open the firefox browser fine, and can go to google and search any subject. In fact, I can use any google-related site like g-mail and all the wide range of google-sponsored sites. But if I try to open ANY other website like yahoo, earthlink, or ANY other site besides google, it will not go. Also, if I open the Add/Remove application window, Gutsy does not recognize that the computer is online and says it cannot get any software. But obviously, the computer is online because it can search google. So what is wrong?

---

### Post by dcstar on 2008-03-07
> **swarup said:**
> I have just installed Gutsy on my laptop, and am trying to get my wired DSL broadband to work. The DSL broadband is working fine I know, because it works wonderfully with my desktop (Win XP). When I connect it my Gutsy laptop, I can open the firefox browser fine, and can go to google and search any subject. In fact, I can use any google-related site like g-mail and all the wide range of google-sponsored sites. But if I try to open ANY other website like yahoo, earthlink, or ANY other site besides google, it will not go. Also, if I open the Add/Remove application window, Gutsy does not recognize that the computer is online and says it cannot get any software. But obviously, the computer is online because it can search google. So what is wrong?

Do you have to enter Proxy Server settings for your ISP?

If not, do a forum search for "disable ipv6" and try some of those solutions.

---

### Post by swarup on 2008-03-07
> **dcstar said:**
> Do you have to enter Proxy Server settings for your ISP?

If not, do a forum search for "disable ipv6" and try some of those solutions.

I did not as yet enter any Proxy Server settings for my ISP. Actually, it is "ADSL" and uses PPPoE. That much I know. 

ADSL is a common service provided in India, and on the Ubuntu India website I found instructions for installing it, and enclosed those instructions here below. Following those, I was able to arrive to the stage I described above, in which the browser will go to google but nowhere else. From what I've described, does it sound like I need to do the "disable ipv6" which you suggest above?

> 1.	Connect your ethernet wire to the port at the back of your computer. 
2.	Fire up the terminal and type in sudo pppoeconf 
3.	It should detect your modem. 
4.	Keep on pressing enter. Fill in your user name and password when indicated. 
5.	It should be easy to stick on to defaults. 
6.	You should be prompted back to your terminal when it would say pppoe loaded. Simple. That's the end of terminal. 
Now go to System>Administration>Networking. Click on it. You would be asked for your password to carry out the administrative job as root. You should be prompted to enter the following details. 
1.	Activate the Wired connection. 
2.	Highlight the wired connection and click on properties. 
3.	Check the box "enable the connection" 
4.	Configuration as Static IP. 
5.	IP Address : 192.168.1.2 
6.	Subnet mask fills on it's own as 255.255.255.0 
7.	Gateway address :192.168.1.1 

---

### Post by dcstar on 2008-03-07
> **swarup said:**
> I did not as yet enter any Proxy Server settings for my ISP. Actually, it is "ADSL" and uses PPPoE. That much I know. 

ADSL is a common service provided in India, and on the Ubuntu India website I found instructions for installing it, and enclosed those instructions here below. Following those, I was able to arrive to the stage I described above, in which the browser will go to google but nowhere else. From what I've described, does it sound like I need to do the "disable ipv6" which you suggest above?

If you have a modern router/modem, you should have it do the PPPoE login, not the OS you happen to boot up - that simplifies things considerably.

If the modem already does the ADSL login, then you shouldn't have Ubuntu also do it - it should just work (assuming your modem has a DHCP server).

---

### Post by swarup on 2008-03-07
> **dcstar said:**
> If you have a modern router/modem, you should have it do the PPPoE login, not the OS you happen to boot up - that simplifies things considerably.

If the modem already does the ADSL login, then you shouldn't have Ubuntu also do it - it should just work (assuming your modem has a DHCP server).

I read about the ipv6, and it sounds like that may be my problem. I will try disabling it in firefox using about:config and see if that solves the problem. But even then, it will not help me with updates for gutsy or software application downloads.

I do not know whether the modem does the ADSL login or not. How can I find out? But do you think this login point is the cause of the problem I describe? After all, the computer does go online. It is just limited to google. Sounds strange I know, but it is true.

---

### Post by swarup on 2008-03-07
I disabled ipv6 in firefox, but it hasn't made any difference. The problem remains as described above. Any suggestions greatly appreciated!

---

### Post by lsmobrian on 2008-03-07
Well, if its a DNS problem, ipv6 in ff wont matter, need to disable in ubuntu

[http://ubuntuforums.org/showthread.php?t=6841](http://ubuntuforums.org/showthread.php?t=6841)
1. sudo gedit /etc/modprobe.d/aliases (or your preferred text editor)
2. Find the line: alias net-pf-10 ipv6
3. Edit this to: alias net-pf-10 off
4. Save the file and reboot


also could comment out ipv6 in /etc/host

---

### Post by swarup on 2008-03-07
> **lsmobrian said:**
> Well, if its a DNS problem, ipv6 in ff wont matter, need to disable in ubuntu

[http://ubuntuforums.org/showthread.php?t=6841](http://ubuntuforums.org/showthread.php?t=6841)
1. sudo gedit /etc/modprobe.d/aliases (or your preferred text editor)
2. Find the line: alias net-pf-10 ipv6
3. Edit this to: alias net-pf-10 off
4. Save the file and reboot


also could comment out ipv6 in /etc/host

I did the above, but it hasn't made any difference. 

It is so strange- the laptop goes online just fine and searches all over google without a hitch. That includes all the google search engines like images, photos etc. But I can't go to any other website BESIDES google. How odd! Any suggestions please?

---

### Post by wpshooter on 2008-03-07
Hmmmmmmm.  First have you tried re-initializing your router/modem ?

I am wondering if perhaps you might have a problem with your Firefox installation ?  I think I would first try uninstalling and then re-installing Firefox.  If that did not work then I would consider doing a complete re-installation of Ubuntu.

But first you might consider trying to talk to tech support representative of whomever is providing your internet service.  But if they are anything like Verizon here in the USA, when you mention the words Ubuntu and/or Linux you are not going to get much help.

Good luck.

---

### Post by redroad55 on 2008-03-07
If you are using Firefox browser go to tools / options / advanced / network / settings...here make sure it is set to what you want..:)

---

### Post by kpkeerthi on 2008-03-07
Duplicate threads.

Anyway.. try this post and let us know
[http://ubuntuforums.org/showpost.php?p=4469678&postcount=11](http://ubuntuforums.org/showpost.php?p=4469678&postcount=11)

---

### Post by swarup on 2008-03-07
> **wpshooter said:**
> Hmmmmmmm.  First have you tried re-initializing your router/modem ?

I am wondering if perhaps you might have a problem with your Firefox installation ?  I think I would first try uninstalling and then re-installing Firefox.  If that did not work then I would consider doing a complete re-installation of Ubuntu.

But first you might consider trying to talk to tech support representative of whomever is providing your internet service.  But if they are anything like Verizon here in the USA, when you mention the words Ubuntu and/or Linux you are not going to get much help.

Good luck.

I do not think it is a problem with firefox, because the Ubuntu Add/Remove and Synaptic tools are also not working. Something is odd about the online connection, but i can't put my finger on just what it is. It IS online--but it can only go to google and nowhere else. It may be related with how ADSL works with the VSNL server--perhaps something in the settings? I have written to the Ubuntu India tech support forum, and will see what they say. But I see it is not a very active forum, with few replies--so I don't know that I'll get an answer there. As for tech support here, I think you are correct. They won't know anything about linux.

---

