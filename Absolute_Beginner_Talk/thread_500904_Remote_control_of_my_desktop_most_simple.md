---
title: "Remote control of my desktop most simple"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by kyrhash on 2007-07-14
I am about to be away from home for about 2 weeks and want to be able to control the PC in my room from the one i'm taking with me.  The one i am controling is an x86_64 fiesty install, and the one that i am taking with me has Win XP home on it.  I dont know anything about ssh or port forwarding but i am behind a router at home.  Could anyone give me a simple way to access and control my home computer.  I know a very limited amount about networking.  Simple easy to follow guides are great.  Thanks in advance for any help.

---

### Post by kyrhash on 2007-07-14
anyone

---

### Post by jediborger on 2007-07-14
I've just recently attacked the same problem and it can be a little tricky. Using SSH is simple but it only gives you a commandline interface of your home computer. So if you're comfortable with just this type of interface or just want to copy files between the two computers than using SSH would be the easiest way to go. If you want to control your computer graphically, like using a mouse and seeing your home computer's screen on your laptop's then you'll need to set up VNC. 

So for just SSH, install openssh-server on your ubuntu computer through Synaptic or apt-get
```
sudo apt-get install openssh-server
```
Since your computer is behind a router you'll then need to set up port forwarding for the SSH ports.
There's a handy website with instructions for a lot of routers, here's a link to the page:
[http://www.portforward.com/english/routers/port_forwarding/routerindex.htm]("http://www.portforward.com/english/routers/port_forwarding/routerindex.htm")
From this page select your router, then it will give you a list of protocols (most of the list is games) but look for SSH (its in alphabetical order) and follow the instructions
As for how to actually connect, there's a handy wiki page here, [https://help.ubuntu.com/community/SSHHowto?highlight=%28ssh%29]("https://help.ubuntu.com/community/SSHHowto?highlight=%28ssh%29")
Although I also recommend PuTTY, which allows you log in to your computer through SSH on Windows:
[http://www.chiark.greenend.org.uk/~sgtatham/putty/]("http://www.chiark.greenend.org.uk/~sgtatham/putty/")
There should be adaquate instruction on both those pages to get you started with SSH, but remember that you need to use the ip address of your router or internet address, just go to [http://whatismyip.com/]("http://whatismyip.com/") if you're unsure what I'm talking about.
Another side note is that you'll need to open port 22 on your ubuntu computer because the firewall blocks it by default. This can done by installing firestarter through Synaptic, apt-get, or Add/Remove Apps. You'll find it under the System-Administration menu, go through the wizard to set it up then goto the policy tab and click in the lower box, then click Add Rule. Select SSH for Service and then click Add and Apply on the menu bar.
If this seems overwhelming, don't worry just ask for clarification.

Now for VNC:
Firstly you'll need to add another rule to your firewall, as Ubuntu blocks VNC connections by default also. Go back to the policy tab under Friestarter and add a service rule for VNC, port 5900 and click Add and Apply. Next goto System-Preference-Remote Desktop. Then check the first two boxes at the top, uncheck the Ask for permission and check the last box and set a password. This way you'll be able to connect to your computer without having to be there and give yourself permission. Next you'll need to go back to that PortForward website I mentioned before and instead of SSH select the VNC service and follow those instructions. Here's a page about VNC for reference [https://help.ubuntu.com/community/VNC?highlight=%28VNC%29]("https://help.ubuntu.com/community/VNC?highlight=%28VNC%29")
Although you'll need a VNC viewer for windows and here's a link to a free one: [http://www.realvnc.com/products/free/4.1/winvncviewer.html]("http://www.realvnc.com/products/free/4.1/winvncviewer.html")
That should be just about it. Again you'll need to use your internet ip address and if you have any questions, just ask. 

Hope this helps.

---

### Post by kyrhash on 2007-07-14
The first site tells me that i need to set up my ip address as static.  On which machine do i need a static address, I think it is the ubuntu computer that needs to be controlled.  how ever that website only has guides for windows and mac.  Can you tell me how to do it in ubuntu?

---

### Post by kyrhash on 2007-07-14
anyone

---

### Post by jediborger on 2007-07-14
Ok, so you need to make the address of your Ubuntu computer static. Goto System-Administration-Network. Select the device that connects to the router/internet and click Properties on the right side. Now under Connection Settings, select "Static IP Address" from the drop down list. Now for your IP Address type in 192.168.1.x where x is any number you want that isn't taken. Choose something in the 30's like 36. It really doesn't matter, just remember what you used because you'll need this number later. Subnet Mask should be 255.255.255.0 and your Gateway Address should be the address of your router, usually 192.168.1.1 or whatever you typed in to get to your routers configuration page. Click OK and you're done.

---

