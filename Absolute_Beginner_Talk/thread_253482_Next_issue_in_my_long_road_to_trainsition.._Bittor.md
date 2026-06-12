---
title: "Next issue in my long road to trainsition.. Bittorrent"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by Rizla on 2006-09-08
I want to say that i appreciate all the help i've recieved over the past week to help me get started.  I've made alot of progress.  

Next issue im having is with bittorrent.  When i try to download a torrent in firefox it brings up bittorent as the default app to open it with.  I click it and it brings up bittorrent.  But thats it, it doesnt download it.  The timer just keeps running.

I had read somewhere that the bittorrent included with ubuntu had some issues and it would be best if you download the official client.  So i did that too.  Except now i dont know where its located.  The only way i can open it is if if do the run command:  alt+f2 and then type bittorrent in the prompt.  It brings it up and then i paste the torrent info, but it still doesnt download..  

WHy would it work in windows but not in linux.  Clearly its not a firewall/router issue:-k

---

### Post by skymt on 2006-09-08
It might actually be a router issue. The Windows client might use UPnP to automatically open a hole in your router. Have you forwarded the relevent ports (6990=6999 by default)?

The official client is pretty bad. I use Azureus; KTorrent and Transmission are also popular.

---

### Post by Rizla on 2006-09-08
> **skymt said:**
> It might actually be a router issue. The Windows client might use UPnP to automatically open a hole in your router. Have you forwarded the relevent ports (6990=6999 by default)?

The official client is pretty bad. I use Azureus; KTorrent and Transmission are also popular.

I'll add those ports directly, but i have a complete port passthrough from 1-9999 for this pc (i know its not 'safe').  Let me see what happens if i also give it that port range.

---

### Post by distroman on 2006-09-08
Are you running gnome? 
If so right click on your desktop, then right click “create launcher” in “command” type “bittorrent”. You can name it what ever you wish. You should be able to use the launcher now. 
As for your problem, with not downloading, try to save the torrent file to your desktop, then open it with bittorrent. 
If that works, you should look at portforwarding.

---

### Post by skymt on 2006-09-08
> **Rizla said:**
> I'll add those ports directly, but i have a complete port passthrough from 1-9999 for this pc (i know its not 'safe').  Let me see what happens if i also give it that port range.

Adding those specific ports won't do a thing if you already forward a range that includes them. Also, it is actually safe. I forward a range of around 200 ports in the 10000s.

I haven't had good results with the official client. Try one of the alternatives, they're better.

---

### Post by shanek on 2006-09-08
Do you have ports 6881-6889 open in your firewall? Oft times, a firewall will slow down or stop the ability to dowload a given torrent. I'm using Firestarter as my firewall interface. I just open up Firestarter and click on policy. Click in the Allow service area and right click, select add new rule, and you will get a interface for adding new services to allow. Bittorrent is the first one in the list :) just select it and confirm.

---

### Post by nudnik on 2006-09-08
Bittornado seems to work best with Ubuntu. As for the torrent files themselves, I download them to the desktop as a backup in the event of a malfunction. I then open the torrent file from there and select my aforementioned favourite client to do the job. This has worked very well most of the time.

I am currently experimenting with Azureus using the latest Linux Java to see if the runtime will correct issues with that client. Will post the results should they be favourable.

](*,)  << The Ubuntu Mascot :mrgreen:

---

### Post by distroman on 2006-09-08
You don't need to port forward, it just means your not connectible. You will only be able to connect  with clients that are connectible. 
Some client's you have to bind to the browser, if it's the case with bittorrent I do not know. 
I would recommend using another client as well.

---

### Post by powder on 2006-09-08
Bittornado works for me too.

---

### Post by Rizla on 2006-09-08
Alright so here's my update.  I downloaded azerus and it worked for me.  i was able to get downloads going.  My icon was yellow because it said i had probelms with my NAT settings.  After fiddling around on my router.  I assigned port forwarding directly to my IP for the bittorrent port ranges, before i had it set to Dynamic.  Now i have all green faces.  I did the UDP test, initially it was failing, then i added another policy for that udp port on my router and set it to my ip address.

All is well in torrent land now.  I think i've finally got my pc fully setup in Ubuntu.

To date this is what i've had to do as a complete noob:
1.)Install Ubuntu (harder than i thought, bunch of problems in the beginning)
2.)Had to learn how to use fstab to set the mount points for my drives
3.)created a shared thunderbird profile between linux and windows via my shared fat32 partition
4.)Got my ntfs data drives read/writeable so i can add/edit data.
5.) Got my ipod to work using gtkpod, tried yamipod, but didnt work for me
6.)Got bittorrent finally working.
7.)install the right codecs/players to view my movies and play my songs.

I think thats about it, it seems simple, but theres been a problem every step of the way.  I can now say i can use linux to do everything i used to do in windows.  It feels refreshing..

Next up, i just bought an GEForce6800 vid card.  I'll get it sometime next week, hopefully it takes to the sytem without too many issues.  With that i can install compiz/xgl for some nice eye candy.

---

