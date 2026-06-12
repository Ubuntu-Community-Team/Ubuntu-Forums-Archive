---
title: "Has anyone got CUPS to work over a network on Ubuntu?"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by Busta999 on 2007-01-24
Despite multiple reinstalls of CUPs on Dapper it keeps dying

Installed printer - works fine right up until I try to share it. Then, if it accepts my password, which it only intermittently asks for BANG dead CUPS

Copy old cupsd.conf back and off we go again......

I have obviously added my user mikeh to the lpadmin group and the cupsys to the shadow group.

Also - disabled root.

Is there a special incantantion to make this work??

I wouldn't mind if it were consistent, I work out what it is trying to do, but I get different problems each time I completely remove it and start over.

Before it would not accept my username password for the localhost:631 Admin pages, now it does ask me then bombs out.

I have just spent two weeks getting this box working for file shares and as amedia server to LiteOn Netplayers, it would be so very convenient for it to be able to print as well.

It pisses me off having to keep a windows XP box running to provide basic print services as the Ubuntu box is incapable of doing it.

Can anyone recommend a distro of Linux that supports shared printing services for MACs and Windows?

Thanks

---

### Post by PilotJLR on 2007-01-24
I have Ubuntu serving multiple printers to Windows and other Ubuntu clients, so it certainly can work...

First thing is obviously to get cups running without crashing. Try removing cups, then PURGE the config files with dpkg, then reinstall with apt-get.
At least get to a point where you can print locally... only then modify the conf file to allow browsing and access from the whole subnet.

---

### Post by Busta999 on 2007-01-24
Thanks for the help - much appreciated.

The CUPS is flakey indeed, but I managed to share the installed printer through SAMBA and it works!!!!

I wish Ubuntu was more reliable though, it is just very flakey indeed. Very inconsistent, but I hope that once something works leave it well alone!!!!!

Thanks again

M

---

### Post by bluenova on 2007-01-27
Don't know why you are doing all that to try to share the printer. All I do is make sure that my cupsd.conf is setup to allow connections on port 631 and make sure port 631 is open. That's it, everything then just works. I have attached a copy of my cupsd.conf for anyone else, trying to get it to work. Note my network is using 192.168.0.0 255.255.255.0

---

### Post by dsimpson on 2007-01-28
Hello bluenova, 
I extracted your sample of cupsd.conf, hoping it will work for me also, but have several questions before I go into making big changes to my cupsd.conf files. I have had serious problems trying to get my computer to print to the network printer. I cannot set up an ipp address on my local computer that will print to the printer,  and this is the computer that the printer is connected through. I have had to reinstall cups many times now because it will lock up and not allow me into my printer or I am even unable to browse cups (the web interface) to make any changes.  

On the browse address and allow from lines on your conf. there are addresses 10.0.0.0 and 172.16.0.0/12 and I was wondering what addresses they designated. Also on your local dns it says 192.168.0.0/16, could you please clarify the last part of that (.0/16). My computer has the dns of 192.168.2.3 (the computer with the printer) my other computer is 192.168.2.2. and the address of the router is 192.168.2.1, could you please tell me how to change each computers cupsd.conf to make them both print to the printer. My host computer is connected by wireless and the other computer is connected by ethernet. 

In your opinion, would I just remove existing cupsd.conf and replace with your cupsd.conf and make minor changes to the addresses? If you can give me the basis for the changes I would appreciate it immensely, I don't want to have to guess on the changes and go by trial and error if knowledgable help is available. :D

---

### Post by Busta999 on 2007-01-28
Hey BlueNova,

Thanks for the files, I'll check em out and great news you managed to get it going.

Obviously I have the cups working at one level because I am sharing it over Samba, but I cannot get and XP or MAC to connect to it on ipp:// or http://

---

