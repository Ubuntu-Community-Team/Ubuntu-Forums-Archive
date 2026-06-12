---
title: "Installed Firestarter - where did it go?"
date: 2005-11-29
forum: Absolute Beginner Talk
---

### Post by Books on 2005-11-29
This is my first day on Kubuntu. I just installed Firestarter using the Adept package manager and it said that it installed.

So... where did it go? It isn't listed on the start menu under Applications anywhere. I looked under Internet, System, Utilities, everywhere.

I know this is a *stupid* question, but really... I'm clueless.

Thank you for your patience!

Books

---

### Post by Manny C on 2005-11-29
Have you tried running the command:
```
 firestarter 
```
from the command line? (I think this is the command)

Sometimes the Menu list refreshes only after a restart and sometimes never, because you may have deleted a subfolder of the menu previously.

---

### Post by Books on 2005-11-30
[QUOTE=Manny C]Have you tried running the command:
```
 firestarter 
```
from the command line? (I think this is the command)

Sometimes the Menu list refreshes only after a restart and sometimes never, because you may have deleted a subfolder of the menu previously.[/QUOTE]

Thank you, Manny!

Well, Firestarter is there. I typed "firestarter" in the terminal and it said this:

[I]Insufficient privileges
You must have root user privileges to use Firestarter.[/I]

I have the sign-on password, and it's the only password it has asked for so far. What is this "root" password? I found this -- [www.ubuntuguide.org/#usersadministration]("http://www.ubuntuguide.org/#usersadministration")  -- but I'm not really understanding. Isn't my sign-in password considered "root"?

Thanks for helping a beginner!!!

Books

---

### Post by Manny C on 2005-11-30
What do you mean by sign-on password? Did you install Ubuntu on your machine?

---

### Post by Books on 2005-11-30
[QUOTE=Manny C]What do you mean by sign-on password? Did you install Ubuntu on your machine?[/QUOTE]

The password that KDE asks for when it boots. I've heard people on this site mention "Admin password", but I thought Admin and root were one and the same thing.

I found a way to turn on firestarter, I think. Typing "sudo firestarter" asks for the password I've been using and then there were a bunch of error dialog messages in the terminal and Firestarter came on with a setup wizard.

I think it works, but it isn't recognizing my dial-up modem. It only says:

[I]Local Network connected device:
Detected device(s): Ethernet device (eth0)[/I] :confused: 

Unfortunately broadband is in short supply where I live (boonies).

The journey continues... :rolleyes: :cool: 

Thanks, Manny, for your help!

Books

---

### Post by Manny C on 2005-11-30
Hmm...a couple of points:
[LIST=1]
[*]I don't know much about Firestarter
[*]This is because Linux has an inbuilt "firewall" that is automatically on by default and which is excellent.
[*]A dial-up modem is not going to be likely hacked.
[*]The three points above mean that I can't help you further and that you should consider not using Firestarter, unless you have a very important reason.
[/LIST]

---

### Post by arphe_el on 2005-11-30
I already installed firestarter using synaptic and it's working fine on root and on user level in application menu. But my question is to how to run it properly? since it is installed and running i won't able to connect to the internet and by disabling it i'm able to connect.

Is there any default set-up for it to run properly?

thank you any help will be appreciated. GODspeed!

---

### Post by gord on 2005-11-30
you should still be able to connect to the internet when its running, the only way i can see that you might think that you wern't connected is if you managed to block every single port

the way firewalls work is by blocking ports, which are used by programs to connect to other computers. firestarter is set to be permissive by default on outbound traffic, so anything can access the internet unless you specify that it can't. (its all set up in the policy tab). 

the inbound traffic is set up to be restrictive by default, so that only the ports you specify can be 'listening' for connections. this only applys for webservers and the like. if you use software like bittorrent though, you will need to open certain ports for it, you should consult the programs documentation to find out which ones.

there isn't any default setup because its depends heavly on how you set up your system

---

### Post by Danielle on 2005-11-30
hi, this is how i have it setup on my standalone PC

go to System>Preferences>Sessions

then click the Startup Programs tab and add:
gksudo firestarter 

that will get it running at boot, you'll still have to put in a password at boot time.

then run it and click on Preferences>icmp filtering
and tick echo reply (pong) and Unreachable.

at startup after you put in your password you can either just close it and it will look like it has shut down but it won't have, or there's an option in Preferences for it to minimise to the tray.

if you shut it down you can run this to check it's still running:
sudo /etc/firestarter/firestarter.sh status

---

### Post by noigeaR on 2005-12-01
[QUOTE=Manny C]Hmm...a couple of points:
[LIST=1]
[*]I don't know much about Firestarter
[*]This is because Linux has an inbuilt "firewall" that is automatically on by default and which is excellent.
[*]A dial-up modem is not going to be likely hacked.
[*]The three points above mean that I can't help you further and that you should consider not using Firestarter, unless you have a very important reason.
[/LIST][/QUOTE]
firestarter is just a frontend for iptables (the inbuilt firewall). using firestarter is just a comfortable and easy way to set-up and configure iptables. iptables (the actual firewall) keeps running even if you close firestarter. there are other graphical frontends for iptables that you can try if you don't like firestarter or if you can't get your internet connection to work with it. guarddog is one example, firewall builder another, although firestarter is in my experience the easiest to use for beginners.

---

### Post by frodon on 2005-12-01
What you need to keep in mind, as noigeaR said, is that don't need to have the firestarter GUI opened to get firestarter running, the behaviour is not the same than windows firewalls.
Here the Gui is only usefull when you want to changes some rules, enable some ports (for exemple if you want to use bittorent). If you want to be sure that you firewall is running type this command in a terminal : ```
sudo /etc/init.d/firestarter status
```
I can confirm that firestarter is a reliable frontend for iptables and ipchains, i never met someone in this forum who's got security problems or any annoyance with firestarter.

For those who use firestarter for the first time, i advice to read that : [http://www.fs-security.com/docs/faq.php](http://www.fs-security.com/docs/faq.php)

---

### Post by silvagroup on 2005-12-02
I understood that iptables is installed on ubuntu but that it is inactive until configured by the user, therefore a gui like firestarter makes the process for us 'nuxbies easier to set up. Anyway still having problems with it myself. Installed guarddog and it ran fine but changed my ICEauthority file, finally got that worked out but removed it in favor of a gnome friendly program. Which firestarter does not appear to be the best choice.

---

### Post by Avionix on 2005-12-08
Hi ,
I have just upgraded to Breezy and now have Firestarter, with the firewall active I can not access any internet page, I have selected the default outbound traffic policy of permissive by default. The only way I can access the net or even my email is to stop the firewall. This doesn't make sense with what I've read in this forum, what am I doing wrong here???

---

### Post by jwd45244 on 2005-12-08
Clearly, there is some confusion about firewalls and Linux.  The Linux networking code has very advanced "firewalling" capability built in. This capability is manipulated by rules using a program called iptables.  Firestarter is just a friendly front-end to iptables.

Hopully this helps.

---

### Post by Avionix on 2005-12-09
As I'm new to Linux it's great to learn stuff like this, but can anyone help with my firestarter problem, I cannot access the net with the firewall active in the default mode of Permissive by default (outbound traffic), I'm on ADSL 2 using a Belkin Router, do I need to configure Firestarter somehow to allow access to the router?
Thanks for your help.

---

