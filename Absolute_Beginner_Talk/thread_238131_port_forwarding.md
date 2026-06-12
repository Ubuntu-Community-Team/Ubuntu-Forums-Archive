---
title: "port forwarding"
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by mlie on 2006-08-17
How to open port or port forwarding? I am not even familiar with these terms.
I have azureus and Amule with low ids. I don't have firewall or anti-virus program installed, but azureus says that I have firewall installed and that I should open this port? How do I do that?

---

### Post by huygens on 2006-08-17
To check if you have a firewall, open a terminal. It is in the application menu (top-left of your screen), then you go under Accesories and you will find an entry named terminal. Click on it.

A window with a [prompt]("http://en.wikipedia.org/wiki/Command_prompt") will be displayed. Simply type the following entry and hit the Return key (on your keyboard):
```
sudo iptables -L
``` It might prompt you for a password, enter your user password.

If you see something like:
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
``` 
Then you do not have a Firewall on your Ubuntu computer. If you have more lines in between. Then, you have a firewall.

Before we proceed further, could you tell us the output of the above command?

Huygens

---

### Post by Klaidas on 2006-08-17
Or, you can install a GUI for iptables - Firestarter
```
sudo apt-get install firestarter
```

---

### Post by huygens on 2006-08-17
> **Klaidas said:**
> Or, you can install a GUI for iptables - Firestarter

Hi Klaidas,

My guess was that as Ubuntu is not installed with a Firewall by default, there is none on his system. Thus, the thing bothering Azureus is something outside Ubuntu.
I thought perhaps of a router, between the Internet (perhaps his ISP) and his computer, is blocking some network request entry. Then, the solution would probably be to forward the port on the router. Note that the router could be simply another computer sharing the connection...
So I would prefer that there is no Firewall GUI installed yet...

Huygens

---

### Post by mlie on 2006-08-17
I have put the sudo command, and I have the exact the display as you have predicted. So, how do I forward the port on the router? By router, do you mean the ADSL modem? Sorry, I'm not too familiar with the terms here.

---

### Post by huygens on 2006-08-17
> **mlie said:**
> So, how do I forward the port on the router? By router, do you mean the ADSL modem?

To explain you a router is a small box that is on one side connected to an ADSL modem (or it has it integrated) and on the other side he is offering many connections to different computers. So more than one computer can access internet with the same ADSL connection.

If you just have an ADSL modem (there is only one similar socket on this box that could be connected to your computer), then it probably does not have a firewall integrated.

So your situation is *weird*. I think I remember that Azureus has a tool to check your port. It is in the Option menu I think...
Anyway if it is not here, try this web page: [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

There is a "proceed" button that you will have to click. Then in the middle of the page, you will see a kind of blue box where it is written "ShieldsUp!! Services". Just under is a text box where you can enter the port of Azureus (go to the options of Azureus, to find out which port you are using). Then click on "Use specified custom port probe". If it is telling you that the port is Open, then you should have a high id because there is no firewall interfering, and it is another problem related to Azureus (in which case, I am not of much help...)
If it is reported as Closed, then Azureus is using another port, or could not open one. If it is reported something else, then you have a firewall.

Huygens

---

### Post by b_martinez on 2006-08-17
> **mlie said:**
> I have put the sudo command, and I have the exact the display as you have predicted. So, how do I forward the port on the router? By router, do you mean the ADSL modem? Sorry, I'm not too familiar with the terms here.

Your ADSL modem is (usually) a router. In the documentation that came with it there should be a section on advanced set up. Look there for 'Port Forwarding'. 
The documentation  will also contain the router address. Most, but not all, will have an address of '192.168.0.1'. In the 'HELP' section of 'Azureus', it will explain which ports need to be forwarded, and how to check them.
hope this helps
Bill

---

