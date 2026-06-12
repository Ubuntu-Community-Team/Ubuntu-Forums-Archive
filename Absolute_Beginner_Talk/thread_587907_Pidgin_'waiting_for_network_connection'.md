---
title: "Pidgin 'waiting for network connection'"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by latheesan on 2007-10-23
There seems to be a on-going problem with the new Pidgin (AKA Gaim) program.

I use it to connect to my MSN account. So, when i add a new profile to it, it connects fine and works great.

When you exit it and load it again, the Pidgin hangs at this error 'Waiting for network connection' even though the program was just working fine seconds ago...

Did anyone find a way to fix this? I really don't want to delete my existing profile and then add it again, just so that it can connect every time...:(

---

### Post by realvz on 2007-10-23
do you start pidgin automatically when your session begins or you launch it manually for the 1st time?

---

### Post by latheesan on 2007-10-23
I launched pidgin manually from Applications -> Internet -> Pidgin

---

### Post by realvz on 2007-10-23
can you try this...
launch pidgin
let it connect
close it after it gets connected....
goto terminal and type 
killall pidgin
start pidgin again...and let me know what happens

---

### Post by latheesan on 2007-10-23
> killall pidgin
pidgin: no process killed

When i try to connect, i get the same error i earlier mentioned...:(

---

### Post by realvz on 2007-10-23
so what do u have to do to have pidgin connected again...restart the computer...or restart x?

---

### Post by latheesan on 2007-10-23
remove my msn account from profile, add it again, tick the checkbox for "Enabled" and it connects again =/

---

### Post by realvz on 2007-10-23
hmmm...that is really strange...because...i use 3 msn accounts in pidgin and dont face the problem..

try one more thing...

rename your .purple folder in you home folder...and tehn configure pidgin from scratch and see if it still happens...

i think its just problem with some config files.

---

### Post by mattack on 2007-10-24
I am having this same problem. I renamed my .purple and .gaim folders and restarted from scratch. No luck. Any fix would be greratly appreciated.

Edit. I just found a fix. You have to know a little bit about how your network is set up though.
System -> Administration -> Network
Select your network connection, in my case it's *Wired connection*, and click properties.
Un-check the box labeled *Enable roaming mode* and then select the appropriate configuration from the drop-down*Configuration* menu.
Most likely you want *Automatic configuration (DHCP)*, but that may not be the case.
Click *Okay* and then *Close*.

Then add your MSN account to Pidgin (if necessary) and reconnect.

---

### Post by Desigen on 2007-10-26
Hi, I don't use network connection. I connect using a Modem. I unchecked Enable Roaming Mode and select DHCP and nothing change. 

Thanks

---

### Post by chaumurky on 2007-10-26
Same thing here. On startup, Pidgin seems to think there is no connection and appears to wait. I connect wirelessly with wifi-radar so I need roaming mode enabled in my network settings for it to work. Disabling and re-enabling the accounts always gets me out of trouble but it's a pain.

---

### Post by Raval on 2007-10-31
> **latheesan said:**
> There seems to be a on-going problem with the new Pidgin (AKA Gaim) program.

I use it to connect to my MSN account. So, when i add a new profile to it, it connects fine and works great.

When you exit it and load it again, the Pidgin hangs at this error 'Waiting for network connection' even though the program was just working fine seconds ago...

Did anyone find a way to fix this? I really don't want to delete my existing profile and then add it again, just so that it can connect every time...:(
I have this problem too but I noticed it happened after enabling plugins for Evolution and Pidgin. Did anyone else do this before this problem showed up?

---

### Post by summetj on 2007-11-02
After upgrading from 7.04 (feisty) I'm having the same problems.

One way to make it connect:
Set my status to "offline", and then re-set it to "avaliable".
Another way to connect:
Go into the accounts->add/edit dialog, and then uncheck and re-check the "enabled" checkbox.

I will attempt the "turn off roaming" fix, but I use wifi-manager, not gnome networking, so I hope that won't mess anything up.

Jay

---

### Post by chaumurky on 2007-11-02
> **Raval said:**
> I have this problem too but I noticed it happened after enabling plugins for Evolution and Pidgin. Did anyone else do this before this problem showed up?

  Any difference if you disable them? Didn't for me...

---

### Post by koleoptero on 2007-11-02
A nice bypass is to change your status (e.g. from Available to Away or Do Not Disturb) and then it connects.

---

### Post by chaumurky on 2007-11-02
> **koleoptero said:**
> A nice bypass is to change your status (e.g. from Available to Away or Do Not Disturb) and then it connects.

Now to create a script that does it on startup...

That's so Linux...

:lolflag:

---

### Post by Eastisle on 2007-11-02
I also had the same problem as soon as I upgraded to 7.10. I solved the problem by re-entering my DSL connection information via terminal command: sudo pppoeconf ... Pidgin now connects normally, hope it also solves your problems.

---

### Post by koleoptero on 2007-11-02
> **chaumurky said:**
> Now to create a script that does it on startup...

That's so Linux...

:lolflag:

I'm always after the easiest solution :lolflag:

---

### Post by Desigen on 2007-11-03
Yea, we can make Gaim connect putting it in Avalible status, how we write a script for starup ?? 

Bye

---

### Post by eriksallstrom on 2007-11-14
I get the same problem with pidgin. Also, when I start epiphany, it's in offline mode and the same goes for the rss reader I use, Liferea. But, when I start nm-applet (which I don't start on startup), all these connect as they should.  So, there seems to be an online/offline flag somewhere that all these programs see... Does anyone know if this can be toggled to online without starting nm-applet?

---

### Post by LIEFofEeofol on 2007-12-05
i tried changing from roaming mode... no change...

---

### Post by gupta_sumesh63 on 2007-12-05
Best would be to reinstall pidgin after uninstalling the current one. Then reconfigure and try.

---

### Post by philinux on 2007-12-05
[https://answers.launchpad.net/ubuntu/+question/13016](https://answers.launchpad.net/ubuntu/+question/13016)

---

### Post by eriksallstrom on 2007-12-10
The solution is, either make sure nm-applet (the network manager applet) is running and knows you're connected, or uninstall network manager. The problem occurs somehow when applications like Pidgin, Epiphany etc. tries to check with the network manager if you're connected to internet, but nm-applet isn't running/doesn't know you're connected and therefore they're told you don't have an internet connection.

---

### Post by cryptoD on 2008-01-04
I had the same problem using DSL connection, i unchecked Roaming Mode and chose DHCP for the Wired connection and the problem is gone! thanks

---

### Post by tkat on 2008-02-22
I just got this, I fixed it by doing Accounts -> (your account here) -> disable
Then enabling it again.

---

### Post by iliopetra on 2008-05-01
Try this:

1)determine your IP using ifconfig from the command line (ifconfig lists all active and inactive connections  - so you choose the IP your active internet connection has)

2) go to pidgin->tools->preferences->network
uncheck the "Autodetect IP address" field and set the IP you just noted down in the Public IP.

That solved the problem for me (however, if you get a different IP address everytime you connect to the internet, u r still in a mess)

---

### Post by persianprez on 2008-05-01
try changing the port settings in the preferences, or you may need to port forward your router settings.

---

