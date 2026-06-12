---
title: "How do I connect to the Net. Major problems."
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by stuck on 2007-04-23
I'm am having major problems with Ubuntu and about to get rid of it if I dont make any progress.

I've been trying to get connected to the Net  for a week now, ive read page after page of instructions. Ive downloaded and installed lots of stuff. Ive given up trying to install Kismet to help mw with it. Ive been given the WEP key and name.

I think Ive managed to connect my card to a wirless network I'm using (internet cafe), I've never had a problem with XP or Vista so I know the network is fine. But when I try to use Firefox it is always not connected. Where am I going wrong, where is Ubuntu going wrong.

ATHEROS, Atheros AR5006EG PCI

Latest release of Ubuntu used, not even sure what Ive installed anymore. But I do have the latest version of "madwifi".

Would you anticipate me having the same problems installing all the other "unknown" devices, by my calculations 25 unknown devices at 1week per device is 6months before I get my laptop to work using Ubuntu.

Please help a disillusioned Ubuntu non-user.

---

### Post by xtreme35967 on 2007-04-23
Have you checked to see if you are really connected or not. Are you getting an IP Address and DNS Numbers from the Access Point? You can check this by going too System, Administration, and then Network

---

### Post by stuck on 2007-04-23
Trying to remember from the top of my head because I have to use Vista or XP to access here then reboot to Ubuntu to try something, then reboot again to MS to look for something else.

I tried administation, wireless network, then selected my card, then clicked properties, then put in WEP key and connection name, then clicked  ok.

Then i tried a number to command line codes to check connection, from these it looked like i was connected. If you tell me what commands I can try then post the results back here after a reboot.

Thanks for the help.

---

### Post by Patrick K on 2007-04-23
I don't have wireless but try pinging a known site like google.com. If you get a return then you are connected and the problem is elsewhere. DNS or hosts file should be looked at.

---

### Post by xtreme35967 on 2007-04-23
Also you need to confirm that you are getting an IP Address from the Access Point that you are trying to connect too. All I do is go to System, Administration, and then Network. There I can see what my IP is. Also If you will look at you Gateway Address that is the IP for the Router most of the time so then you could try pinging it to make sure they are communicating.

---

### Post by xtreme35967 on 2007-04-23
Also if you will upgrade to the new version of Ubuntu I think that will help you too. Feisty has better support for wireless networking. In Feisty all you have to do to connect to a wireless access point is to click on the wireless Icon in the top left corner of the desktop. Let me know if this didn't work and I will do some more testing.

---

### Post by stuck on 2007-04-23
Hello,

Thanks for your help. I think I have the latest Ubuntu, I downloaded it last week, but I cant tell what version it is.

Yesterday I could not connect to the Net (internet cafe) even though I had all the details. Then I tried to install Kismet (which failed and I still cant get to work) and still couldnt connect to the net. (I know the net was active as XP and Vista would connect.)

Well just to make a fool out of me Ubuntu has now connected to the net and I using it to type here. Ive done nothing different to yesterday (i think)

Thanks for the assistance.

Would you be able to offer any assistance on installing my unknown devices, 

Big thanks.

---

### Post by xtreme35967 on 2007-04-23
The new Ubuntu is 7.04  It is easy to check to see which you have. Just go too System and then About Ubuntu

---

### Post by stuck on 2007-04-23
Now Im on the Net there are 168 updates so I'm hoping this will solve some of my problems

Slightly less disillusioned than yesterday.

---

### Post by stuck on 2007-04-23
* 8.&#8194;What is GNU?
   
  Thank you for your interest in Ubuntu 6.10
                - the Edgy Eft - released in October 2006.
				

Ubuntu is an entirely open source operating system built around.........



I dont understand, i thought I downloaded the latest version from the Ubuntu web site.

Probably going to have to reboot after it has finished updating.

---

### Post by xtreme35967 on 2007-04-23
Ok you are using Ubuntu 6.10 the newest one is Ubuntu 7.04  Download all your updates and when you have them all you will see a place in the updates menu to Download 7.04. Download it and maybe you wont have as many problems.

---

### Post by xtreme35967 on 2007-04-23
Feisty Fawn aka Ubuntu 7.04 just came out a day or so ago

---

### Post by stuck on 2007-04-23
Download all updates but nothing much seems to work.  (that is nothing more than pre update)

Ive been trying to install Kismet but it doesnt want to install.

---

### Post by xtreme35967 on 2007-04-23
I have not used Kismet so i cant help you there. I just put Feisty on my laptop that was built in Intel wireless and it is working great. With Feisty there is an icon in the top right hand corner that you click on to pick networks. [Click Here For Link]("https://wiki.ubuntu.com/7.04Tour#head-1dec0464a1255dae3857e12bdf9f40b58362591d")

---

### Post by stuck on 2007-04-25
I was told to use Kismet to find the network details i wanted to connect to. But I had all the details (name, wep key), in the end i used:   iwlist ath0 scan

this gave me the details i needed (already had)

I dont know what ive done differently but now i can connect to the net without problems.

Thank you to everybody helping a newbie.

Stuck.

(Not as disillusioned as a week ago)

PS

Now only have to sort out graphics card, sound card, power buttons, function buttons, and all the other unknown items in device manager. Time to start googling, and hopefull take less than a week per item.

---

