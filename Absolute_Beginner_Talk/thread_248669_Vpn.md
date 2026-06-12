---
title: "Vpn"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by lodravah on 2006-09-01
What's the best VPN - client for Ubuntu Dapper?

---

### Post by Zed on 2006-09-01
vpnc (in universe) works fine with my employer's vpn. I haven't used others.

---

### Post by KingBahamut on 2006-09-01
[http://packages.ubuntu.com/dapper/net/kvpnc](http://packages.ubuntu.com/dapper/net/kvpnc)

For a nice graphical interface and so forth.

---

### Post by SeanHodges on 2006-09-01
I would also like to know this.

I've done a little bit of research. So far I've found a tool called kvpnc ([http://packages.ubuntu.com/dapper/net/kvpnc](http://packages.ubuntu.com/dapper/net/kvpnc)) that should allow connections using a KDE GUI. Though I havent played with it yet.

If that fails to work, it looks like we may be resorting to the command line, using some/all of the following tools:

pptp-linux - [http://packages.ubuntu.com/dapper/net/pptp-linux](http://packages.ubuntu.com/dapper/net/pptp-linux)
grml-vpn - [http://packages.ubuntu.com/dapper/misc/grml-vpn](http://packages.ubuntu.com/dapper/misc/grml-vpn)
vpnc - [http://packages.ubuntu.com/dapper/net/vpnc](http://packages.ubuntu.com/dapper/net/vpnc)

A howto that might be worth looking at is at [http://www.hku.hk/cc/services/vpn/linux/vpn_linux.htm](http://www.hku.hk/cc/services/vpn/linux/vpn_linux.htm), which uses yet another command-line tool, called "vpnclient".

I will be looking into this soon, and will post my findings. Any other help will be appreciated.

---

### Post by nrwilk on 2006-09-01
My university requires I use vpn to connect to their wireless network.  I just got it all configured after some trouble, so I may be of some help.

my very first tip is that you should NOT use kvpn.  Kvpn, also called kvpnc, is a front-end gui for vpnc.  I found it to be extremely flaky.  Using it, my vpn authentication got dropped about once an hour.  It also made it harder to authenticate with vpn than just using the CLI vpnc tool.

I am now using the CLI vpnc tool, and I really don't see much reason for a gui front-end.  It's simple, easy, and it works flawlessly.  Not to mention, it connects faster than Kvpnc, and after you set it up with a conf file that contains the network info for your vpn connection, it is much less work.

My quick vpnc howto:
Issue the following command:```
vpnc --print-config
``` This command will prompt you for the five pieces of info you need to connect to your vpn network.  After filling in each piece of info, it will print five lines of text in the format it likes in it's config files.  Copy these five lines to your clipboard.


 Now, create a config file for vpnc in the directory where it expects it with a name meaningful to you.```
sudo kate /etc/vpnc/<name>.conf
```You can call it whatever you want, just end the name with ".conf".  If you use gnome, then you should replace kate with gedit in the previous command.

Paste the five lines you copied from the terminal into the new file, and save it.  Close your editor.

you can now connect to your vpn network by issuing the following command:```
sudo vpnc-connect <name>.conf
``` 
I put it in a script in my path with a short name to make it even easier to type quickly.


You can at any time just issue the command, `sudo vpnc-connect`, but, doing it this way means that you have to enter all the five pieces of info each time you want to connect.  If you stick the info in the config file, you only have to enter it all in once.


I hope this helps someone.

nrwilk

---

### Post by Geoff2077 on 2006-09-01
after you establish the connection - how do you access folders and files on the server. Nautilus ??

Cheers
Geoff

---

### Post by nrwilk on 2006-09-01
> **Geoff2077 said:**
> after you establish the connection - how do you access folders and files on the server. Nautilus ??

Cheers
Geoff
I'm sorry, but I'm not familiar with using vpn with a fileserver.  At my university one must use it to do anything on the network (wired or wireless).  But, once authenticated via vpn you just use the network as you would on any other network.  You can log onto the network without vpn, but it will not let you access anything inside or outside of the university network.  So, if I'm on the network without authenticating with vpn, and I open my browser, the only page I get no matter what is an internal university page describing how to download and setup vpn.  I cannot even ping internal or external addresses.  But, once I've authenticated with vpn, I can surf the web and use all my other internet apps.  So, I just assumed it was a means of authentication to make sure that only authorized users could access the network.

---

### Post by n8bounds on 2006-09-01
> **Geoff2077 said:**
> after you establish the connection - how do you access folders and files on the server. Nautilus ??

Cheers
Geoff

yeah, use the text entry method of Nautilus

open a Nautilus window, click EDIT > PREFERENCES then goto the BEHAVIOR tab and put a check next to always use text-entry location bar

oh yeah, then put in something like
```
 smb://windowsmachinename/ 
```

---

### Post by lodravah on 2006-09-02
I installed vpnc, and tried running it. Came up short on all these. Are all the settings given by my school? I've been looking around the school pages, and I think I have some settings. Usrnm and pwd are my personal ones, of course. But whats this "secret" - thing? And what is the difference between gateway and ID? According to my school I don't need to use both, seeing as I can either use an IP or a vpn-name to log on til the network.. So, am I waaaay off base here? My first dealings with VPN since my school decided to switch from ftp til VPN this year. At least I think they did. 

Oh, and I guess I need to install PPTP first...?

List from sudo vpnc:

Enter IPSec gateway address:
Enter IPSec ID for :
Enter IPSec secret for @:
Enter username for :
Enter password for @:
vpnc: unknown host `'

alrighty then!:-\"

---

### Post by nrwilk on 2006-09-02
> **lodravah said:**
> I installed vpnc, and tried running it. Came up short on all these. Are all the settings given by my school? I've been looking around the school pages, and I think I have some settings. Usrnm and pwd are my personal ones, of course. But whats this "secret" - thing? And what is the difference between gateway and ID? According to my school I don't need to use both, seeing as I can either use an IP or a vpn-name to log on til the network.. So, am I waaaay off base here? My first dealings with VPN since my school decided to switch from ftp til VPN this year. At least I think they did. 

Oh, and I guess I need to install PPTP first...?

List from sudo vpnc:

Enter IPSec gateway address:
Enter IPSec ID for :
Enter IPSec secret for @:
Enter username for :
Enter password for @:
vpnc: unknown host `'

alrighty then!:-\"


When you install vpnc, it should also install any dependencies it needs.

To connect to the network at my university, I did have to use all five fields.  IPSec gateway address is the IP to the server.  IPSec ID is the name of the connection; for me it had to be 'csuvpn', or it would fail to connect.  IPSec secret is the network password, which they should have provided to you, it's the same for everyone.  username and password are your individual username and password.

---

### Post by geektron on 2006-09-08
> **nrwilk said:**
> 


I hope this helps someone.

nrwilk
It helped me a ton! Thanks a lot. :mrgreen:

---

### Post by nrwilk on 2006-09-08
> **geektron said:**
> It helped me a ton! Thanks a lot. :mrgreen:

Great!

And believe me, it's much easier that way than using kvpnc.

---

### Post by satbunny on 2006-09-15
My University uses the Microsoft PPTP protocol. If you want to use that with Ubuntu then the webpage for installing and setting it up is here:

[http://pptpclient.sourceforge.net/howto-ubuntu.phtml](http://pptpclient.sourceforge.net/howto-ubuntu.phtml)

---

