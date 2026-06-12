---
title: "wifi help needed please"
date: 2006-02-21
forum: Absolute Beginner Talk
---

### Post by chrluc on 2006-02-21
I managed to get my wifi card working/reconized. I have 3 computers win xp w/lynksys router; win 2000 laptop with trendnet wifi card; and ubuntu laptop w/trendnet wificard. the win 2000 laptop sees and connects to my router w/no problems. the ubuntu, in terminal after iwlist scan, will see the router once every 10 to 15 scans. tried sudo iwconfig wlan0 essid linksys and nothing at all. so I got gtkwifi and it will show up every so often whe I try to connect, it says dhcp error and not connect. in system-admin-networking should I have the wireless connection configured differently? 

please help.

ps I'm sitting next to the router

---

### Post by TrendyDark on 2006-02-21
I have a Trendnet wireless card in my computer at home, and I had to use ndiswrapper to get it to work  correctly. Maybe try that if you haven't already?

---

### Post by chrluc on 2006-02-21
[QUOTE=TrendyDark]I have a Trendnet wireless card in my computer at home, and I had to use ndiswrapper to get it to work  correctly. Maybe try that if you haven't already?[/QUOTE]

yes you are correct I had to use a ndiswrapper to get it to be reconized by the system, I am that far what did yoy do after that to get on the network. I am sitting at the library (has free wifi) and using my windows machine to access the internet as we speak but nothing on the ubuntu machine.

---

