---
title: "Networking across OS's..."
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by online14230 on 2007-05-24
Hi there.Sorry about the cross post, but....


Im TOTALLY new to networking in linux, let alone Ubuntu. So heres my problem:
I have a 4 port router (Texas Instruments Mega 100WR) and tons of network cable... 
We (a few friends and I) want to set up a mini LAN for gaming (Need for Speed UG2, MW, Carbon) and filesharing. The PCs are as follows:

1 x P4 dual booting XP Pro sp2 and Dapper
1 x Acer Travelmate 2501LC (no wireless/bluetooth) dual booting XP Pro sp2 and Ubuntu 7.04
1 x P4 running XP Home
1 x P4 running Dapper
1 x HP Laptop running XP Pro, which Ill update to SP2 today (this will have to use wireless) and will not run any games
1 x Piii. This machine will be used primarily to host files eg music, movies etc.

What I was thinking of, was to leave the P3 running permanently. Connect the router to it via USB and place it in a central location (the basement of the main house will be fine, since my laptop and my friends are within VERY close range to it.) and connect our FUTURE DSL line to it, using it as a gateway. It CAN be formatted to run ANY OS. The problem comes in with the Ububoxes. We can get the XP machines connected quite fine, but none of us have any idea how to set up Ubuntu to log into the LAN. We intend just setting up a workgroup in XP, using dynamic IPs as assigned by the router (Ive set that up already) on login. It works already, using 2 desktops (wired) and a laptop (wireless) with no hassle.

Any idea how we could get Ubuntu to work? 
I gather I can get the wireless working (from the sheer volume of posts here) just by reading, but to get the wired machines working is a REAL B%$#H!!!

Thanks for any and all help...

PS: ALL machines have onboard NICs, including the P3, which also has a whopping 600GB of real estate available, not counting the 100 odd GBs of music on it already 


B.

---

### Post by onbongos on 2007-05-24
just plug it in and it should work

---

### Post by Zzl1xndd on 2007-05-24
for file sharing you want Samba.

---

### Post by ruy_lopez on 2007-05-24
If you set sharing on some folders in the MS boxes, you should be able to see them from Ubuntu's Network browser. Places-->Network. Try that first. See if you can access any of the shared folders.

---

### Post by online14230 on 2007-05-31
okay peeps, thanks for ALL the help. Heres what happened:
1. Onbongos suggested  I "just plug it in" and it should work. Ideally, that would happen. Nope. No such.
2. Samba: hehehe... heah, I laugh. Samba, to you, is easy to setup. Me, on the other hand...
well, lets juust say I have a habit of locking my keys in the car....
3. I have the MS box (yes, now we only have 1. It seems a friend has decided to sponsor us a copy of Cedega. Now we run NFS U2 over that. MUCH clearer graphics, better speed... I can now play with all display options set to max and the game runs BEEEEEEAAAAOOOOOTIFULLY!!!!) set up for filesharing quite nicely. I have an FTP server AND Ive installed apache. Both have been set up CORRECTLY, as I accessed them VIA the router with another MS box... Ive even managed to stream some music, which in and of itself, is a real TIME WHO@E. 
I just cant seem to access the LAN with the Ububoxes. Incidentally, Ive transfered all my data to the MS Box and clean-installed 7.04 on all machines, except the server. Now, I cant seem to access the server with ANY machine.. Please help!
Also, any idea how I could get NFS:PU working?

---

