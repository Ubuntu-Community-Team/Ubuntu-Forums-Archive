---
title: "Networking PPPOE (Newbie) HELP ME!"
date: 2006-04-03
forum: Absolute Beginner Talk
---

### Post by manutd on 2006-04-03
I cannot for the life of myself connect to the internet! 
I've hit a wall! ](*,) more then once! 

I'm trying to connect with a pppoe high speed, ethernet connection! 
I have a router as well but I'm not worried about hooking that up yet (its not out of the box yet)! 
I'm more worried about just connecting to the internet! 

I cant figure it out and most of the people I talk to, tell me my computer is possesed! I'm starting to believe them! 

It a refurb from zellers...lol... but it was $450 (canadian) for a 2Ghz Processor, 40Megs on Ram, and 512 Ram! Its IBM! Not a bad deal I figured

I install Ubuntu and the DHCP thing tries to do the Networking part itself.
It can't...so it asks me to to it manually! 
I put my IP address in but I'm pretty sure that it changes (meaing the ip) everytime I reconnect to the high speed. U get a new one right?!

anyway it doesnt work, so once Ubuntu is loaded onto my PC I go to System-->something else(newbie lol)--->Networking
Put my password in and config it like that! 
I put my DNS server numbers (2 of them) and I dont have a default gateway and my IP address changes but I put the current one in anyway and the 255.255.255.0 in the other spot! 
It wont connect!  

I go to the internet and select "tool" then "preferences" then "connecting something or other". move the dot from the first option to the second option.
That doesnt help! 

I've also looked into wiki and did eveything they suggested and it doesnt work! 
I'm starting to get fed up with Ubuntu and Linux in general! 
I really dont want to use Windows again because I get viruses and a load of other problems with it! 

I need help! Step by Step help! :???: 
I bought a new ethernet card but I havent installed the drivers for it yet! WHY? because its to dam hard to install anything in Ubuntu. It opens the CD up when I put it in but thats it... I cant figure out anything to install! Thats my next plan. Maybe thats why I cant connect, i need drivers???! but the system does see the ethernet card! It does know its there!
"ifconfig" & "if config -a"

I've reinstalled Ubuntu about 5 times now thinking maybe it had problems during the installation! No luck! 

I'll shut up for now but pls someone pls help me out! 
I dont wanna have to go back to supporting Bill! [-(  He has enough money!  

THANKS EVERYONE!

---

### Post by az on 2006-04-03
[QUOTE=manutd]I cannot for the life of myself connect to the internet! 
I've hit a wall! ](*,) more then once! 

I'm trying to connect with a pppoe high speed, ethernet connection! 
I have a router as well but I'm not worried about hooking that up yet (its not out of the box yet)! 
I'm more worried about just connecting to the internet! 

I cant figure it out and most of the people I talk to, tell me my computer is possesed! I'm starting to believe them! 

It a refurb from zellers...lol... but it was $450 (canadian) for a 2Ghz Processor, 40Megs on Ram, and 512 Ram! Its IBM! Not a bad deal I figured

I install Ubuntu and the DHCP thing tries to do the Networking part itself.
It can't...so it asks me to to it manually! 
I put my IP address in but I'm pretty sure that it changes (meaing the ip) everytime I reconnect to the high speed. U get a new one right?!

anyway it doesnt work, so once Ubuntu is loaded onto my PC I go to System-->something else(newbie lol)--->Networking
Put my password in and config it like that! 
I put my DNS server numbers (2 of them) and I dont have a default gateway and my IP address changes but I put the current one in anyway and the 255.255.255.0 in the other spot! 
It wont connect!  

I go to the internet and select "tool" then "preferences" then "connecting something or other". move the dot from the first option to the second option.
That doesnt help! 

I've also looked into wiki and did eveything they suggested and it doesnt work! 
I'm starting to get fed up with Ubuntu and Linux in general! 
I really dont want to use Windows again because I get viruses and a load of other problems with it! 

I need help! Step by Step help! :???: 
I bought a new ethernet card but I havent installed the drivers for it yet! WHY? because its to dam hard to install anything in Ubuntu. It opens the CD up when I put it in but thats it... I cant figure out anything to install! Thats my next plan. Maybe thats why I cant connect, i need drivers???! but the system does see the ethernet card! It does know its there!
"ifconfig" & "if config -a"

I've reinstalled Ubuntu about 5 times now thinking maybe it had problems during the installation! No luck! 

I'll shut up for now but pls someone pls help me out! 
I dont wanna have to go back to supporting Bill! [-(  He has enough money!  

THANKS EVERYONE![/QUOTE]

Install without configuring the internet - skip that step.

Once you have a desktop, open a terminal and run

sudo pppoeconf

and enter your isp's information.  PPPOE is a different protocal than what you use to connect to any other network, so you have to configure it differently.

If you connect your router to the dsl modem, it will connect via pppoe and you will connect to your router via DHCP (The regular protocol).  Yes, one day, pppoe will be configured graphically - it's just a little rare, so it seems.

---

### Post by manutd on 2006-04-03
I will give that a shot but I did do that already but I probably played with other things during that time so it might have messed up the process...
I will reinstall AGAIN and try and see what happens tonight! 

They had that info on the wiki site! 

Thanks eh...ill keep u posted!

---

### Post by manutd on 2006-04-04
SWEET! Thanks...I connected perfectly! 
Now onto Email! lol and then to Wine and then Ohhh so much more..but now at least i can connect and find out online how to do everything else! 

Thanks again for all your help!

---

