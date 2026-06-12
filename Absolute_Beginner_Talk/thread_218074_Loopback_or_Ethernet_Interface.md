---
title: "Loopback or Ethernet Interface?"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by Scintillement on 2006-07-18
I don't understand either of these terms and have no idea which one I should have it set to. At the moment I only run off the liveCD until I can get my questions sorted out. I don't want to bork my machine by accident.

Also is there an equivilent in Ubuntu to ctrl+alt+del in Windows to check processes and CPU usage?

---

### Post by swamytk on 2006-07-18
Ethernet Interface - Your network card which connects you to your local LAN or internet through modem or router.
Loopback - You have nothing to do with it. It is nothing but a key concept to identify your own machine.
Please let me know when you are asked to select between these two while installing? more info?

Ctrl+Alt+Del equi: menu System->Administration->System Monitor

---

### Post by Scintillement on 2006-07-18
> **swamytk said:**
> Ethernet Interface - Your network card which connects you to your local LAN or internet through modem or router.
Loopback - You have nothing to do with it. It is nothing but a key concept to identify your own machine.
Please let me know when you are asked to select between these two while installing? more info?

Ctrl+Alt+Del equi: menu System->Administration->System Monitor

Since I only ever have run from the LiveCD I have never been asked to select either one. I just noticed the option to change between the two in the network tools I think it was.

By default it was set to Loopback. I connect straight to a cable modem via cat5 cable. Nothing wireless at all.

---

### Post by swamytk on 2006-07-18
Cool! Network Tool is going to monitor your network based on IP address. By default every machine comes with Loopback (127.0.0.1) for internal TCP/IP network. If you want to monitor your internet, you can select Ethernet card. It has nothing to do with Configuration of Network.

Configuration of network: System->Administration->Network

---

### Post by steve.horsley on 2006-07-18
Alt-Ctrl-Del:
Right-click the top or bottom taskbar, and choose **Add To Panel...**, then add **System Monitor**. Clicking the system monitor icon brings up a window where ou can look at the task list.

---

