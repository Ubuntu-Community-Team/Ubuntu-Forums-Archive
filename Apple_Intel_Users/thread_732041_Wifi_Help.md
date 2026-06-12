---
title: "Wifi Help"
date: 2008-03-22
forum: Apple Intel Users
---

### Post by Noob1234 on 2008-03-22
Alright, so i have ubuntu 7.10 installed and i also ran through the ndiswrapper steps to try to get my wifi going.  Didnt work.

When I go to wireless manager I dont even get the wireless connection option, all I see is wired connection and modem connection.

What should I do next?

---

### Post by blznazn on 2008-03-22
They have different wireless cards depending what generation of MacBook you bought.  Mine uses the atheros drives(I bought mine July '07), others use the broadcom (I think that's what it's called).  Also if you installed 64 bit ubuntu, atheros does not have a 64 bit driver out for windows yet, but madwifi works.  Also you should check if you added ndiswrapper to your modules to load on boot, or you can also load it manually by typing sudo modprobe ndiswrapper.

---

### Post by veiho on 2008-03-22
> **Noob1234 said:**
> When I go to wireless manager I dont even get the wireless connection option, all I see is wired connection and modem connection.

What should I do next?

You should find out, what WiFi card is in your macbook. Posting output of 'lspci' is good start.

---

### Post by Noob1234 on 2008-03-22
> **blznazn said:**
> They have different wireless cards depending what generation of MacBook you bought.  Mine uses the atheros drives(I bought mine July '07), others use the broadcom (I think that's what it's called).  Also if you installed 64 bit ubuntu, atheros does not have a 64 bit driver out for windows yet, but madwifi works.  Also you should check if you added ndiswrapper to your modules to load on boot, or you can also load it manually by typing sudo modprobe ndiswrapper.

I also bought mine in july of 07 and I did make it boot automatically by adding it to my modules.  I dont even get any icon in regards to wifi.

But I have not done anything with madwifi, what and how do I need to set that up?

Edit: I just checked and I have Atheros AR5418

---

### Post by Noob1234 on 2008-03-22
Humm Im sort of at a stand still, I have tried a couple different things with no luck.  Can somebody with atheros give me exacly what worked to enable their wifi?

Thanks

---

### Post by cvasilak on 2008-03-22
Check the Wireless section in the Wiki

[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)

and follow the instructions.

I have the same card as you and it is working perfectly!

Regards,
Christos

---

### Post by blznazn on 2008-03-23
> **Noob1234 said:**
> I also bought mine in july of 07 and I did make it boot automatically by adding it to my modules.  I dont even get any icon in regards to wifi.

But I have not done anything with madwifi, what and how do I need to set that up?

Edit: I just checked and I have Atheros AR5418

Mines the same.  If you have the 32-bit Ubuntu, you can install ndiswrapper-utils-1.9 and then if you have leopard you can put the leopard cd in, copy the windows xp atheros driver from the cd (it's in Driver/atheros/atherosxpinstaller.exe (i think)) and the other I don't know much about lol)  then unrar x atherosxpinstaller.exe into a folder.  then sudo ndiswrapper -i net5416.inf then modprobe ndiswrapper and add ndiswrapper to /etc/modules (it's a text file).  

If you installed the 64-bit Ubuntu.  Then you need to use madwifi (At least I had to :-\).  You need to install subversion gcc g++ make build-essentials.
[QUOTE=https://help.ubuntu.com/community/MacBook]
sudo apt-get install build-essential subversion autoconf automake
svn co [http://svn.madwifi.org/madwifi/trunk](http://svn.madwifi.org/madwifi/trunk) madwifi
cd madwifi
make
sudo make install-modules
echo -e '#!/bin/sh\n/sbin/iwpriv ath0 bgscan 0' | sudo tee -a /etc/acpi/resume.d/99-madwifi-bgscan.sh
sudo chmod 755 /etc/acpi/resume.d/99-madwifi-bgscan.sh
sudo modprobe ath_pci
sudo iwpriv ath0 bgscan 0[/QUOTE]
They forgot to throw in add ath_pci to /etc/modules so that it loads on boot

You could probably just copy and paste it into a script and run it :-\

---

### Post by cyberdork33 on 2008-03-23
Yea, if you have an atheros card, you should be using madwifi. You should follow the instructions for your hardware in the wiki. 
[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)
[https://help.ubuntu.com/community/MacBook_Santa_Rosa](https://help.ubuntu.com/community/MacBook_Santa_Rosa)

---

### Post by veiho on 2008-03-23
> **blznazn said:**
> They forgot to throw in add ath_pci to /etc/modules so that it loads on boot

You could probably just copy and paste it into a script and run it :-\

There is no need to load ath_pci during boot, because it activates wireless and this is not desirable unless user wants wifi active from start. Wifi takes quite much power and shortens battery life. Same logic goes with other hardware as well. There are laptop-mode tools and network manager to load/unload modules when needed.

---

### Post by blznazn on 2008-03-24
> **veiho said:**
> There is no need to load ath_pci during boot, because it activates wireless and this is not desirable unless user wants wifi active from start. Wifi takes quite much power and shortens battery life. Same logic goes with other hardware as well. There are laptop-mode tools and network manager to load/unload modules when needed.

Oh oops, lol, sorry, I live on campus where everything is pretty much wireless, so that's what I usually use. 

But on 32-bit Ubuntu ndiswrapper is usable (and more stable so it sounds like from the help wiki thing, it works because apple supplies a 32-bit windows driver), but on 64-bit madwifi appears to be the only thing that works.

---

