---
title: "Getting Ralink working in XFCE"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by SpongeBob SquarePants on 2008-04-05
Just installed Mint XFCE. Everything seemed to go okay. Apart from my wifi card didn't connect. So I went to Wicd and it resisters both my wireless connection, and that of the dude next door. But it won't connect. Under driver, in the preferences I'm not sure what to choose. I have a bog standard ralink wifi card, which I usually get going with ndiswrapper. But surely I don't need to bother with ndiswrapper if Wicd can already see my connection when I open it . Surely it's working already?

Anyway. out of curiosity I installed my windows driver with ndiswrapper and again everything went as it should. I rebooted, chose ndisrapper in the preferences, and tried to connect. But it just sits looking of my IP address, until it just stops.

I'm not familiar running XFCE at all. Am I missing out on something obvious?

---

### Post by twright on 2008-04-05
just add the word 'ndiswrapper' to /etc/modules the run sudo modprobe ndiswrapper to get it working

---

