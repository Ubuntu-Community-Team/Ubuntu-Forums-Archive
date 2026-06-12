---
title: "Connect to manage a MSSQL database"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by cleardensity on 2007-05-09
after making the decision to jump on the ubuntu wagon for good - there's one thing holding me back... The ability to connect to and manage a microsoft SQL database. I must use MSSQL for work, so in order for me to fully make the switch, i need to find some way to still be able to have "Enterprise-like" managing of MSSQL. 

I've searched and searched for applicable applications without any luck - posting here is my absolute last ditch effort to find something to do this, so i can continue the jump. Any and all suggestions are greatly appreciated. I am in a holding pattern now, and i really don't want to have to dual boot, just to manage databases. Anyone have suggestions, experiences, or workarounds?

Thanks for your consideration.

---

### Post by Wim Sturkenboom on 2007-05-09
Have you looked at wine and try to run the client in there? No experience.

---

### Post by cleardensity on 2007-05-09
yes, the current app used from windows is Enterprise manager - it will not work under wine - at least not for me... that would work just fine, IF it was not buggy also. 

My preference would be to find a native linux alternative as to not be tied to anything windows... 

i know, sounds ironic - but i'm sure you understand what i mean...

Thanks for your help.

---

### Post by abadr on 2007-06-16
I run K/Ubuntu and use MSSQL all the time but not using a native application or wine. I simply remotely connect to the MSSQL server using KRDC (Kubuntu) or Terminal Services Client (Ubuntu). These 2 programs support the RDP protocol used by the Windows servers Terminal Services which you need to make sure its running on the windows server. I'm sussefully using those 2 program to connect to windows 2000 server and windows 2003 servers. 

It's amazing how well this works even across the Internet, the servers are in the US and I'm in Egypt. 

Another option is to use VMware player to run a guest operating system (windows in this case) in a window in Ubuntu and install any program you need in that. I use that all the time to run things like dreamweaver.

If you need anymore info let me know.

---

### Post by exile on 2007-06-16
I second Abadr's post. I have also just used a remote desktop to manage MSSQL. The only difficulty is if you had network administration issues such as not being able to stay connected remotly for long periods of time due to having a limited number of licensed connections etc.

---

