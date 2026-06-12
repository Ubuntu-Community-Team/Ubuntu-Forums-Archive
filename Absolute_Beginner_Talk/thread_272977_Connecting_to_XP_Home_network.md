---
title: "Connecting to XP Home network"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by pisapiag on 2006-10-07
I have a XP Home edition computer with which I created a home network. My only other machine is a new Linux box which I configured myself two weeks ago. I want this Linux box to connect to some shared folders on the XP Home computer. I managed to allow the Linux box to see the Windows network and see the shared resources. The problem is that once I try to connect to the shared folder I get an error message telling me that I don't have the necessary permissions to see the content of the shared drive. 
What is it that I should do?

---

### Post by unisol on 2006-10-07
im no expert but here goes open Connect to Server: select windows share from the drop-down menu,fill in the name of the server you want to connect to and the name of the share you want to connect to. if your network requires authencation, you can also configure the username and domain name in the window. once you have configured the share click the connect button. a new icon will appear on your desktop. double-click that icon to open the nautilus file browser to that share.if you are not sure about the settings for your windows share, you can click Browse Network to search the local network for any available windows share.

---

### Post by pisapiag on 2006-10-07
The problem is that once connected, the authentication does not work, even though I use the admin account on the XP box. It says I don't have the necessary permissions.

---

### Post by pisapiag on 2006-10-07
The actual message is: "Authentication required - You must log in to access (admin account)@(machine name)/(share name) domain (domain name). When I do input the requested information, the same box comes back and asks me the same  thing.

---

### Post by pisapiag on 2006-10-08
Well, I may have found the solution. It appears that the only share that Windows XP Home Edition will allow a Ubuntu box to connect to without any fuss is the SharedDocs one or any other share created under. As far as I'm concerned, any other won't work. I don't know the situation with XP Pro as I don't have such a box at home and I can't experiment that at work. I don't know if the fault is Windows' or Ubuntu's nor do I really care. I hope this post will help some of you.
Take care.

---

