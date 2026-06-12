---
title: "Vpn"
date: 2005-12-06
forum: Absolute Beginner Talk
---

### Post by satbunny on 2005-12-06
I need to connect to a VPN server for work. Which package should I use?
I know how to setup VPN in Windows so I hope I'll be able to configure it easily.

---

### Post by markr on 2005-12-06
I think it depends on what VPN Server application is running that you wish to connect to;  I have no end of problems with CheckPoint as they don't provide a Linux client.

I think a  popular vpn client for Linux is [www.openswan.org](www.openswan.org).

Mark.

---

### Post by bluefrog on 2005-12-06
pptp client. there is a mppoe (or something like it trick) to make it work with a windows vpn

james

---

### Post by fishbroetchn on 2005-12-06
i had tons of problems with the original cisco vpn client. it did not get it to compile. anyway i tried vpnc and it worked right away. get the .deb packages via apt-get or packages.debian.org and install it.

good luck:rolleyes:

---

### Post by Nequeo on 2005-12-06
I would use 'pptp-linux'. It's in the Ubuntu repositories, so you can search for it with Synaptic, or just type 'apt-get install pptp-linux' from the command-line, if you like doing things the fast way.

There is a graphical program to set up your connection, but it's not included in Ubuntu! Oh well. You can find plenty of documentation to help you set things up here:
[http://pptpclient.sourceforge.net/](http://pptpclient.sourceforge.net/)

Or, if you're connecting to a Microsoft Windows Domain, I wrote a script that will set everything up for you. You can download it here:
[http://members.optusnet.com.au/~sger/Scripts/pytp](http://members.optusnet.com.au/~sger/Scripts/pytp)

Let me know if you have any trouble running it, and I can step you through it. 

Hope that helps.

Cheers,

---

### Post by mishranurag on 2005-12-08
I got a PPTP CLient installed on my UBUNTU system. Ideally after connecting to the VPN, I should be able to Map the netwrok drives in my college, cause that's what I do in windows. Could you please guide me what could be the issue??
I would really appreciate that.
Thank you
Anurag


[quote=Nequeo]I would use 'pptp-linux'. It's in the Ubuntu repositories, so you can search for it with Synaptic, or just type 'apt-get install pptp-linux' from the command-line, if you like doing things the fast way.

There is a graphical program to set up your connection, but it's not included in Ubuntu! Oh well. You can find plenty of documentation to help you set things up here:
[http://pptpclient.sourceforge.net/]("http://pptpclient.sourceforge.net/")

Or, if you're connecting to a Microsoft Windows Domain, I wrote a script that will set everything up for you. You can download it here:
[http://members.optusnet.com.au/~sger/Scripts/pytp]("http://members.optusnet.com.au/%7Esger/Scripts/pytp")

Let me know if you have any trouble running it, and I can step you through it. 

Hope that helps.

Cheers,[/quote]

---

### Post by mishranurag on 2005-12-12
Still no help :(
Anurag


[quote=mishranurag]I got a PPTP CLient installed on my UBUNTU system. Ideally after connecting to the VPN, I should be able to Map the netwrok drives in my college, cause that's what I do in windows. Could you please guide me what could be the issue??
I would really appreciate that.
Thank you
Anurag[/quote]

---

### Post by mishranurag on 2005-12-13
Anybody there to help yet??
Anurag :(
[quote=mishranurag]Still no help :(
Anurag[/quote]

---

### Post by mishranurag on 2005-12-14
Still no body
:(:mad::eek::???::confused:

[quote=mishranurag]Anybody there to help yet??
Anurag :([/quote]

---

### Post by Mr. Electric Wizard on 2005-12-14
Have you been able to dial in via VPN at all?
Is it connecting?

---

### Post by mishranurag on 2005-12-15
Yeah! It does connect and receives a lot of packets but sends none :(
Anurag

[quote=Mr. Electric Wizard]Have you been able to dial in via VPN at all?
Is it connecting?[/quote]

---

