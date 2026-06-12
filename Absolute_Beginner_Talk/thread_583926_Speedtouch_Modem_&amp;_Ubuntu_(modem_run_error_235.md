---
title: "Speedtouch Modem &amp; Ubuntu (modem_run error 235)"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by latheesan on 2007-10-20
I recently downloaded and installed the Ubuntu OS and i tried to get the internet working using my SpeedTouch ADSL Modem on it. 

I tried various tutorials and none worked. I found a solution which everyone says "might" work, so i tried it out. Its called speedtouchconf

I extracted it into home drive and cd into it and did this:

> chmod +x speedtouchconf.sh
./speedtouchconf.sh

First, it asked for VPI/VCI values. My internet company uses 1 50, so i entered that. Then, it asked for my user/pass to conenct, i also entered those.

Then it asked me, if those variables were correct, i entered Y and hit enter. It loaded the driver and did all the stuff. Then it showed me this error:

> *** Configuration finished. Starting the connection ***

Sat Oct 20 13:06:34 BST 2007
The modem lights should start flashing for approx. 60 seconds...
You might see some messages about USBDEVFS_BULK failed - you can ignore this.
Sat Oct 20 13:06:34 BST 2007
The modem_run command failed (code 235)
modem_run results:
Mutex value not OK
FAILED because of modem_run error 235
latheesan@laptop:~/speedtouchconf-27-Jun-2006$ Oct 20 13:06:34 laptop modem_run[28541]: modem_run version 1.3.1 started by latheesan uid 0 
Oct 20 13:06:34 laptop modem_run[28541]: modem_run version 1.3.1 started by latheesan uid 0

Can someone help me with this error please?  Without internet on my ubuntu, its pretty much useless right now...

---

### Post by ddrichardson on 2007-10-20
I *think* that is an error relating to firmware/microcode but don't know an awful lot about these modems - try [here.]("http://steve-parker.org/speedtouchconf/")

---

### Post by latheesan on 2007-10-20
aww :(

thanks anyway, i'll try emailig the speedtouchconf owner about this. I used my friend's and like i sad before on another thread, the internet "just works"... so its not the ubuntu or my internet cables/connection etc...

Why cant the ubuntu do something about this...? I mean seriously, there's like millions of people out there who still uses modems to connect and it'd be awsome if ubuntu start paying more attention to modem users over lan/cabe/router users. I hear PCLinuxOS works quite well with the modems. Apparently you plugin your modem (regardless of any make), and it asks you if u want to install firmware and make a diale for it... if only ubuntu had this, i wud wipe my Windows off my laptop and stick with Ubuntu forever!

---

### Post by latheesan on 2007-10-20
I found out what was wrong on the FAQ part of their site. Apparently i tried to load the speedtouchconf.sh one too many times. All i had to dowas run **sudo undo.sh** and reboot te machine.

When i ran the speedtouchconf.sh file again, everything worked out great, it even detected line speed etc. When it came to authenticating, it failed. It said check username/password and VPI/VCI info. Well, i entered everything correct, exactly as my ISP told me to enter, it it doesnt work :(

Anyway, i tried to connect again using this method: **sudo /etc/init.d/speedtouch start** and now i recieved these errors:

> latheesan@laptop:~$ su
Password: 
root@laptop:/home/latheesan# /etc/init.d/speedtouch start
[: 110: ==: unexpected operator
[: 510: ==: unexpected operator
Starting ADSL connection:[: 510: ==: unexpected operator
[: 510: ==: unexpected operator
[: 510: ==: unexpected operator
 failed.
root@laptop:/home/latheesan# 

Does anyone know what this is about...?

---

### Post by winh8r on 2007-10-21
hi , I too had a great many problems getting the speedtouch modem to work with Linux.
However I discovered that StevenHarper  has come up with a piece of code that works a treat.Go to [http://www.squeezedonkey.com/wiki/linux/index.php?=Main_Page](http://www.squeezedonkey.com/wiki/linux/index.php?=Main_Page)
and download the 0.5.4 release and run that.
IT is a very simple to operate method of configuring your speedtouch to work with Ubuntu- one word of warning though-I cant get it to function after upgrading from 7.04 FeistyFawn to 7.10 GutsyGibbon, so it's best if you stick to 7.04 Feisty fawn for now.(I am using Feisty and a speedtouch 330 usb adsl modem to write this reply!!!!!)
Good Luck- and keep trying, if you need any help just ask on the appropriate thread-the Ubuntu community is very friendly and helpful and will always try to help beginners and experienced users alike.

---

### Post by latheesan on 2007-10-21
aww..... but i like my gutsy :( the new features on it is awsome. I'll try it anyway and see if it works, if not, i guess i got no other choice but to go back to feisty :(

---

### Post by StevenHarper on 2007-10-21
Hi, I have just made a GUTSY Build...

I have tested it and It works for me

Please try it and give me feedback

[http://www.squeezedonkey.com/svn/linux/trunk/releases/ubuntu/32-bit%20i386/](http://www.squeezedonkey.com/svn/linux/trunk/releases/ubuntu/32-bit%20i386/)

Thanks

Steve

---

### Post by latheesan on 2007-10-21
Steve, You ROCK man!!!

Sadly, it wouldn't work on Gutsy, i am not too sure why, so i re-installed my OS to Feisty and it worked just like that. They should include your program into the future releases of Ubuntu, thats how awsome it is.

Thanks allot dude :)

---

### Post by latheesan on 2007-10-21
On gutsy, after installing it, all it does is says "Loading" forever... so i gave up on it and switched to Feisty. It works now :)

---

### Post by latheesan on 2007-10-22
Wopz, typo, i meant the program says "Starting Up" forever, it does nothing. I was getting tierd of feisty, and wanted the Gutsy back, so i used the upgrade option to go from 7.04 to 7.10 and the net stopped working. 

The modem manager says "Starting Up" forever... Steve plz look into this?

---

EDIT :: Nevermind, even tho it says "Starting Up" forever and never turn green, the internet is actually connected, s your software actually works on Gutzy :) *nice work*

---

