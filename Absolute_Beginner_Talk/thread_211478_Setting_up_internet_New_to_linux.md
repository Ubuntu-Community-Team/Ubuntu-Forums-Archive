---
title: "Setting up internet New to linux"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by johaann on 2006-07-08
Hi,
i am new to linux. i have installed Ubuntu and it is working fine. The cd cover says Intel x86 edition. i am interested in Linux as i am always have to battle installing scripts over the net and it always seems to be slow.

i then later when i am familiar with Linux setup a webserver thru adsl connection running a few website of my own. i believe that can be done. i already have a reseller hosting account and have had it for just over a year.

I run XP on my main machine and XP Home on my laptop. I have just made up a 3rd machine with a AMD1.3 processor that have a network card installed.

My whole purpose of using Linux is that it want to setup a server, learn how to use it as i want to get a dedicated server soon, use it for testing perl/php scripts etc.

I understand the "limitation" with linux but that doesn't concern me as i have 2 other machine to use for my business etc.

I though i just give an introduction as to what i am planning to do. also i am a do it now person but want to learn and understand linux

Now that i have installed the Ubuntu everything is working but i can't get any connection to the internet. i presume i need to setup firefox etc.

I am using a adsl router with 4 ports at the back. When i got my laptop i just plugged it on and off i went. i also have my main computer just plugged and and another win98 machine. From my main  machine i can access the win98 machine but not the laptop. I am not interested in the network at present only getting on to the net at this stage.

Can anybody help please

When i run Firefox i am told connection refused when i enter my server ip address and when i enter a domain [www.google.com](www.google.com) i get could not be find

I noticed this forum said beginners so i ask to be treated this way as i am in the world of linux

Thanks
Johan

---

### Post by Sonofmoog on 2006-07-08
I can get you started.  Go to System-->Administration--->Network Tools.  In the Network Device, select Ethernet Interface.  Hit the Configure Button.  Check Enable this Connection.  In the connection list, select DHCP.  Plug your computer into your router/modem and try your internet connection.  If you still have no luck, reboot and try again.  

If you still can't connect, open Firefox and in the address window type the IP address of your modem/router.  On my system, it would be 192.168.1.254.  
Press enter.  You should then see the interface built into your router, and you can verify there that your connection is good.  If the router doesn't see the computer, you may have a hardware issue ..

HTH

---

### Post by johaann on 2006-07-08
Hi,
Thanks for reply. I battled to find this post again but have activated email notification.

i am on there but when i try to hit config it does nothing. Also under Network devices it says network devices not found. I used the machine on xp before and the network card works.

At the bottom under the info it says "not avalable" everywhere

maybe i need to install a driver for the network card. How do i do that

Thanks
Johan

---

### Post by johaann on 2006-07-08
Hi,
i have just checked to see if i can access my router but when i enter the ip address it returns refusing to connect.

So maybe the network card need drivers installed. any help on that please 
Thanks
Johan

---

### Post by Sonofmoog on 2006-07-08
> **johaann said:**
> 
So maybe the network card need drivers installed. any help on that please 
Thanks
Johan

Open Synaptic and search for ethtool.  If you don't have it on your system, install it.  Open a console, and issue the command:

```
sudo ethtool eth0
```

Good luck.  HTH.  If it doesn't I'm out of options for other things to try ..

---

### Post by Sonofmoog on 2006-07-08
> **johaann said:**
> Hi,
i have just checked to see if i can access my router but when i enter the ip address it returns refusing to connect.


The thought occurs, you may need to run Firefox as root.  I don't seem to have to do this on my system, but it is one more thing to try.  Refusing to connect is a different situation than unable to connect ..

Open a terminal, and type 

```
gksu firefox.
```

---

### Post by Willson on 2006-07-08
are you sure you entered the right IP Address? Sonofmoog's address will probably be different than yours.

---

### Post by johaann on 2006-07-09
Hi,
Willson my IP is 10.0.0.2 so thats not the problem. HTH i am trying to run firefox from the root but it is asking me for a password. I can't recall entering a root password when i installed ubuntu. i now my username and password when ever i startup the system.

Is there a default password?

Thanks
Johan

---

### Post by johaann on 2006-07-09
> **johaann said:**
> Hi,
Willson my IP is 10.0.0.2 so thats not the problem. HTH i am trying to run firefox from the root but it is asking me for a password. I can't recall entering a root password when i installed ubuntu. i now my username and password when ever i startup the system.

Is there a default password?

Thanks
Johan

When you say "open a console" is that the same as running a application from the application menu

---

### Post by Crosbie on 2006-07-09
> **johaann said:**
> When you say "open a console" is that the same as running a application from the application menu

No, it means you open a terminal window to type system commands.  Try Applications/Accessories/Terminal, or Applications/System Tools/Konsole.

---

### Post by johaann on 2006-07-09
Hi,
thanks for the reply. What i have done is reinstaslled ubuntu from the beginning and it seems fine now. i think i did something wrong in the beginning setting up the network section

Thanks for all your help thus far

Blessings
Johan:-({|=

---

