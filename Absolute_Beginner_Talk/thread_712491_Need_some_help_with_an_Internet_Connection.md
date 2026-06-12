---
title: "Need some help with an Internet Connection"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by Chronotrigger_BG on 2008-03-01
Hello, I intend to make this short and quick.
I'm trying to connect to the net with Linux and I'm running into some very very basic problems (sorry)

How do I enter my username and password? I didn't see a menu about it in the network manager.

I have used successfully both internet on Linux on that same computer(didn't need password) and this particular connection with windows.
I get an IP assigned, this seems fine. My guess is that other than my own incompetence, nothing else is hindering me from Internet access.
Thanks in advance.

---

### Post by maniac_X on 2008-03-01
if you are using some type of "dial-in" account:
from your desktop panel, choose **System->Administration->Network**.
it may ask for your password, this is your login PW for Ubuntu.
you should now have a box named **Network Settings**.
choose **Modem Connection**, click **Properties**, and fill in your login info as relates to your ISP.

hope this helps

---

### Post by Chronotrigger_BG on 2008-03-01
I'm not running a modem connection.
It says "Interface not connected", as far as I recall.
The cable is (properly)recognized as a Wired connection.
In Windows I had to "create a new connection" for it, specifying a name for that connection (which I am told should be a specific name, not just whatever I make up). It falls under "Broadband".

---

### Post by pytheas22 on 2008-03-01
Can you provide more information on your ISP set up?  In Windows, at what point do you enter your username and password in order to connect?  What kind of connection is it exactly (ethernet or something else)?  What is the output of

```
ifconfig
```

---

### Post by maniac_X on 2008-03-01
are you on a wired nic or is it wireless?

---

### Post by Chronotrigger_BG on 2008-03-01
Seriously, this is the most basic-est connection imaginable. You plug the cable in, you're connected. It's just like any other Windows connection - you enter the username/pw right before you connect - in the two fields given for that. Apart from the whole name-entering thing I said, there's no more configuring to be done for it to work.

---

### Post by pytheas22 on 2008-03-01
Where exactly are these two fields given for name and password?  I've never had to enter a name or password in Windows to connect to an ethernet connection.  Do you enter these every time you connect or only once when you set up the connection?  Are you positive that you didn't have to install any software beforehand in Windows in order to make the connection work?

---

### Post by ferdostar on 2008-03-01
Check this [http://www.ubuntugeek.com/ubuntu-networking-configuration-using-graphical-tool.html](http://www.ubuntugeek.com/ubuntu-networking-configuration-using-graphical-tool.html)

---

### Post by Chronotrigger_BG on 2008-03-01
The fields must be filled every time. And no, no additional software installed.
That last tutorial was entertaining, but hardly functional - it didn't include anything about a password :)
By the way, when I'm with Linux the system gets download but doesn't get upload - I receive about 1K/s data but send 0 bytes.

---

### Post by Shazaam on 2008-03-01
To help us help you please open Terminal (Applications>Accessories>Terminal) and input a couple of commands. After each one prints an output copy and paste the results here.

```
ifconfig
```

and...
```
lspci
```

The first code prints out your network connections and the second one prints out a hardware list. The reason we need the second one is sometimes, depending on the ethernet card, you might need to install drivers.

As an aside are you doing the authentication (username and password) with your modem and not the pc?

---

### Post by ferdostar on 2008-03-01
Try this:
1) Unplug the cabel, restart, then enter all your information about your connection (without having internet)
2) After you save all the information you plug the cabel and you restart
ps don't forget to mark to start automatically 
Please post if there is any result

---

