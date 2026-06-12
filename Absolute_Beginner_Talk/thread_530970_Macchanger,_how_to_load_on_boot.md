---
title: "Macchanger, how to load on boot?"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by ubunuby on 2007-08-21
Could anyone explain to me how I can make macchanger run during boot so I can have a random MAC everytime I start up?

I understand how to run it but not how to automate it.

---

### Post by expatCM on 2007-08-21
I am very curious...........   why would you want to have a random MAC address on boot?

---

### Post by ubunuby on 2007-08-21
I think some guy is running a sniffer on my ISP's switch or router. He's been hacking my computer for a long time and he likes to stalk me when I play MMMORPGs 

I used to think I was getting hacked from the outside but I never see any signs of intrusion. I've got no open ports, no wireless connections and no untrusted files. Nothing shows up on chkrootkit, or rkhunter So what else could it be?

The thing is I've got DSL, which I thought was a private line, so where or how is this possible. Ive searched all over but I dont understand the possibilities.

---

### Post by raijinsetsu on 2007-08-21
Most ISPs only allow 1 MAC per device. I know on mine, I have to reset my cable modem to get it to accept a new MAC.

---

### Post by ubunuby on 2007-08-21
yeah I'm aware of the most legitimate use for it, but If I could do anything to avoid this guy a little more then it would help. 

But really, how can he be running a sniffer on my ISP side if I'm using DSL and the only one on the line. If thats not the case then I'm really getting omgwtfhax'd without any trace.

---

### Post by raijinsetsu on 2007-08-21
Just report it, with any output you have, to your ISP, and if you can, to his ISP. That's what I've done in the past. It works most of the time.

---

### Post by ubunuby on 2007-08-21
I just want to understand how I'm being followed around, and how to make it stop. Theres just too much to read and I dont know where to start.

---

### Post by wirelessmonkey on 2007-08-21
Your MAC address ends at YOUR router.  It doesn't propogate any farther.  Your router's MAC address continues onward to your ISP's router.  Your problem exists elsewhere. Explain in detail what this person is doing to 'hack' you, and what information this individual seems to be using that allows you to identify him.

---

### Post by ubunuby on 2007-08-21
Is sniffing traffic on someone's ISP then using it to follow them around without touching their box considered hacking? Hell, is it even possible? I'm running out of ideas. 

I bricked my router so for now I've got it hooked straight to the DSL modem with pppoe. (and no wireless) I was reading stuff about ARP poisoning, MAC spoofing and some "man in the middle" thing which i have no clue about. I remember reading my Linksys router's guide and it said the most common hack was MAC spoofing.  I guess the macchanger is only a sad attempt at obscurity.

This guy has been hacking me for years always following me around in games he'll make a free account with some character name like my password or something I googled 10 minutes ago. Hell, he even bothered following me to a Japanese game before. 

I really was hoping it was so simple as a trojan, so I switch to ubuntu, using only the repos and MD5 checking any games I was playing. Close all ports and services, check logs, setup firewall, check firewall, run chkrootkit and others, but nothing shows up.  I ran into him again yesterday and double check my machine, but of course nothing suspicious comes up. 

I dont care so much anymore because theres nothing I can do. It's become more of an annoying riddle that after all this time I still can't figure out how he's hacking my box. Its almost feels like I don't deserve any privacy until I find the answer :(

---

### Post by wirelessmonkey on 2007-08-21
After switching to Ubuntu, he can display your google searches from 10 minutes ago?  If all of this is still the case, it sounds like your DSL modem may have been compromised.  The fact that he can follow you to multiple games is disturbing, and removes the possibility that he's listening from a game server.  
When you say he displays your password, do you mean your computer password or game password? 
Much of the data that he seems to be using is passed cleartext on the internet, though the password thing is interesting. If your DSL modem has been compromised, he could be mirroring traffic to another address.  What is the make and model of your DSL modem?

---

### Post by ubunuby on 2007-08-21
Well no, not my password, but yes I've seen him use my  various login names. After running sniffers on my end I'm beginning to understand the cleartext thing. I've got a westell 2100 modem, but from what I've read its unconfigurable and the firmware is configured for my ISP.

I've looked through sniffer data and it makes little sense to me, what I dont understand is how could he always know whatever name of character and what server I would pick from only clear text? I'll have to look at it again.

---

### Post by wirelessmonkey on 2007-08-21
This link shows how to connect to your DSL modem:
[http://help.expedient.net/broadband/westell2100.shtml](http://help.expedient.net/broadband/westell2100.shtml)

See if there is updated firmware for it.   Try increasing your firewall settings on the modem as well.  You may need to copy all the network information from the DSL modem, and reset the modem to defaults and reconfigure it.   Be careful. 

If you are uncomfortable doing this, you should call up your ISP and have them either do this for you or replace the modem.

---

### Post by schorsch on 2007-08-21
Are you using a cabled connection or wireless?

---

### Post by wormser on 2007-08-21
I think changing you MAC on boot is not going to make a difference.  Something else is going on.    But this should work to change you MAC on boot.  Create a file will the command you use to change your MAC then make it executable.  Run the file in a shell to test it.  Then go to System> Preferences> Session and add that file.  Test it by rebooting.

---

### Post by ubunuby on 2007-08-21
I wish it were this easy, but unfortunately my modem version does not allow any configuration changes, because of the custom firmware it uses setup by my ISP.

> The 210015-04 is simply a bridge modem. It does not have a web interface, routing functions, or built in PPPoE.

And no I'm not using wireless

If obscuring my MAC address doesn't help then I guess its irrelevant. 

I was hacked long before my router died, when I was using windows. I doubt the modem is the cause.

---

### Post by wirelessmonkey on 2007-08-21
The modem and your game accounts are the only suspect pieces left. Since I doubt you use the same information to get into all your games, and that someone else would have access to those servers, we are left with the idea that someone is dilliberately sniffing your network traffic.  Since we are as sure as we can be that your Computer is not compromised, that leaves only 1 fail point.  The DSL modem.  Call your ISP and tell them that you have reason to believe that it has been compromised.

---

### Post by ShinyMcShine on 2007-10-10
This is my experience with getting a new, random mac address at startup.

I've created a script to run at the start at a session that set a new and random MAC address for my network connections on my computer at startup using this macchanger tool. This is tested on my Ubuntu 7.04 installation with Gnome Network Manager removed and Wicd installed instead. eth0 is my wired connection and eth1 my wireless connection.

1. Create two sh scripts, each with these commands:
   scriptfile "change_macs.sh"
      killall /opt/wicd/daemon.py # closes use of eth1 by Wicd
      sleep 1
      ifconfig eth1 down # deactivate eth1
      macchanger -A eth0 > /dev/null # change mac address for eth0
      sleep 1 # wait a little to get different random mac addresses
      macchanger -A eth1 > /dev/null # change mac address for eth1
      ifconfig eth1 up # activates eth1
      sleep 1
      /opt/wicd/daemon.py 2> /dev/null # starts Wicd daemon again

   scriptfile:  "start_change.sh":
     sudo sh change_macs.sh
     sleep 4
     /opt/wicd/tray-dapper.py > /dev/null&
     echo Done and done

2. Read the current mac addresses with the tool ifconfig.
3. Run the script with the command "sh start_change.sh". 
4. If the mac addresses is changed correct with the script then add the command "sh start_change.sh" to your session.

This works for me. If gnome network manager is used instead of Wicd then some other way of closing it's use of the wireless connection so macchanger can change the mac address. Use it if you find it of any use.

---

