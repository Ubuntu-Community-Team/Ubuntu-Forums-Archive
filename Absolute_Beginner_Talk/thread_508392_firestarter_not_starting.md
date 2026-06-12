---
title: "firestarter not starting"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by Balvinder25 on 2007-07-24
hi all,
         im just a newbie in the linux world..and ive installed ubuntu 7.04 .>i read somewher tht ubuntu dosent have  firewall of its own so we should download one.>i have installed firestarter.>now the probs is tht it dosent start automatically when i start the pc.>i was wondering if someone could show me how to do this..?that would be really great.and i dont like the bib circle icon for the firewall.>isnt there any way we would change this.??just out of curiosity.??any help would be great...

Thanks.

---

### Post by Paul820 on 2007-07-24
Ubuntu DOES have a firewall installed by default, firestarter is just the GUI for configuring it. If you want firestarter to start at boot, go to your main menu->system->preferences->sessions, when the sessions box opens, in the startup programs click new, in the name box type 'firestarter' ( without the quotes ), in the command box type 'sudo firestarter' ( without the quotes ). That's it, it will start when you boot up. You won't see it, it will be in the background. Hope this helps.

---

### Post by mcduck on 2007-07-24
Keep in mind that you don't need to run the graphical Firestarter tool for your firewall to work.

---

### Post by irish_flu on 2007-07-24
FYI- the installed-by-default backend folks are talking about is called "IP Tables".

---

### Post by xpod on 2007-07-24
You really dont need to run/start firestarter when booting up.

It`s just a gui tool  to use if your not too clued up on iptables but you mabey want to allow some service & open some port etc.As soon as you`d made your changes you would just close firestarter again.

Unless you want it on constantly to monitor your blocked connections or something:-?
Strangely lots of people panic when they start seeing all the BLOCKED connection in firestarter...usually after they`ve been using ssh or torrents etc mind you.
 
No need for the extra drain at startup though as iptables is doing it`s job either way.

---

### Post by wnelson on 2007-07-25
Firestarter creates a directory /etc/firestarter and and init file in like /etc/rc5.d/S20firestarter which init's /etc/init.d/firestarter. This then starts iptable and load all of the necessary modules.

Walt

---

### Post by p252 on 2007-08-05
I have installed firestarter on two of my Linux machines now and from my personal experience (and slight annoyance), firestarter does not start up or run the iptables script by default on-boot. On a fresh boot I open my command line and run the command 'sudo iptables -L -n' and I get

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  

This is iptables NOT configured with any rules. I understand that firestarter is just the front end to iptables but why is the configuration being lost when I reboot my computer? It does this on both my computers so I know it's not just the computer. . .

---

### Post by kukibird1 on 2007-08-05
sudo  vi   /etc/firestarter/firestarter.sh


Comment out 

if [ "$MASK" = "" -a "$1" != "stop" ]; then
       echo "External network device $IF is not ready. Aborting.."
       exit 2
fi


It should look like this  



#if [ "$MASK" = "" -a "$1" != "stop" ]; then
       #echo "External network device $IF is not ready. Aborting.."
       #exit 2
#fi


save  restart


Firestarter service does not start on boot if Network Manager is used

I believe it is because the network connections have not been set up by
network manager by the time the firestarter.sh script is called


I saved this little snippet from a mail list for for ubuntu-bugs  it worked for me .

---

### Post by isaacj87 on 2007-08-05
> **kukibird1 said:**
> sudo  vi   /etc/firestarter/firestarter.sh


Comment out 

if [ "$MASK" = "" -a "$1" != "stop" ]; then
       echo "External network device $IF is not ready. Aborting.."
       exit 2
fi


It should look like this  



#if [ "$MASK" = "" -a "$1" != "stop" ]; then
       #echo "External network device $IF is not ready. Aborting.."
       #exit 2
#fi


save  restart


Firestarter service does not start on boot if Network Manager is used

I believe it is because the network connections have not been set up by
network manager by the time the firestarter.sh script is called


I saved this little snippet from a mail list for for ubuntu-bugs  it worked for me .

Could this be the solution for my problem as well?
I've noticed that upon boot up (and shut down) when the screen is black and you see text...something catches my eye. It says something about "starting firefox" and to the far right in brackets and red letters it says **[fail]**. What's the deal?

---

### Post by p252 on 2007-08-05
Thank you very much, I'll give that a try. . .

---

### Post by p252 on 2007-08-07
Update. . . Commenting out those lines that kukibird1 suggested worked great. Firestarter now sets up the firewall on each boot. . . Thanks!

---

### Post by Hilko on 2007-09-18
It seems my firewall has not been running for over a year.
I'm glad I have come a cross this thread. Thanks.

---

