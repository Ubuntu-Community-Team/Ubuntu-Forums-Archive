---
title: "Strange Folder Sharing Issue"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by jaspen.p on 2007-06-06
Hello,
I'm fairly new to the linux OS and I have run across an interesting problem. I got a new computer on the cheap from work and decided to install Ubuntu feisty on it since I had heard some pretty good things about it. Anyway my problem is this:

I had spare Linksys wireless game adapter laying around so when I set up my computer I plugged my ethernet jack into that and away I went. I managed to figure out how to share folders and install a network printer so I could print from my XP laptop. I have since moved my setup into the room with the wireless router and I figured I could just ditch the wireless adapter and plug straight into the router. 

The problem is that when I do this I can no longer see my ubuntu machine from my xp laptop. If I plug the ethernet cable back into the game adapter it shows back up. I selected the WINS server option in the shared network folder and I was able to see the folders but it said that I didn't have sufficient privileges to open them. 

To be honest I have no idea what a WINS server is, I was just messing around trying to get it to work. When the game adapter is plugged in a login box appears and I have setup a password and user name for that and it works fine. Is this a problem with my router or is this something that needs to be changed in the samba config file? 

It's not a big deal since I can leave the game adapter hooked up but it seems silly to have to use it when the router is about 6 inches away.

Thanks for the help in advance.

Oh, I almost forgot, my router is a Netgear WGT 624 vs3.

---

### Post by ryanVickers on 2007-06-06
This isn't anything wrong with your hardware, it just needs to be configured.  I have no idea what a wins server is either, but for making it work, make sure that the folders your sharing are (if you want write) full privilages from everyone (owner, specified group, others) and that "read-only" is not checked on in the sharing preferences for the folders (once again, unless you want it to be).

---

### Post by jaspen.p on 2007-06-07
Thanks for suggestion but as I said earlier I have the folder sharing working  when I use my wireless game adapter to connect to the network with reading and writing privileges enabled. It's only when I plug directly into my router that I can't access the folders.

The only thing I changed was plugging the other end of the ethernet cable into the router instead of the game adapter. I don't understand why it stops working.

Also, I did check to see If the IP address changed when I plugged the ethernet straight into the router but it didn't because I had set the computer to a static IP.

Does anybody have any other ideas?

---

### Post by ryanVickers on 2007-06-07
Is your router setup to protect each computer on the LAN from every other one or something like that?  look around in those options maybe...

---

### Post by jaspen.p on 2007-06-07
I looked at the router setting and I couldn't find anything that would restrict access to the wired connections. It seems to me that if the router was restricting access to other computers it would do it for both wireless and wired connections. This has me baffled, do you have any other ideas?

---

### Post by ryanVickers on 2007-06-07
Not really, I'm not much of a network expert, but just one more thing before I would look forsomeone more knowledgeable on the subject - is ubuntu setup to work in a wired mode (System > Administration > Network)

---

### Post by jaspen.p on 2007-06-07
I'm not either. I usually just fiddle around until I get it to work or give up. 


I looked at the network settings box and it's set to auto scan for network services, I'm not sure what some of the other options are for.

Anyway, the computer should "see" the same wired connection whether I use the game adapter or not. 

I guess I'll just keep using the game adapter for now.

Thanks again for your suggestions.

---

