---
title: "wpa supplicant from source?"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by iClouseau88 on 2006-11-30
Hi,

I wish to set up my dual-boot laptop as a wireless client.  Since it appears that Dapper's wpasupplicant is not all that good from the threads I have read, I plan to install the latest supplicant program from source, i.e. [www.sourceforge.net](www.sourceforge.net).  First though, do I need to remove or blacklist wpasupplicant?  Secondly, where would I need to set up the new "WPA" folder or directory in order to download and extract the new software?

Thanks in advance.

---

### Post by wieman01 on 2006-11-30
"wpa-supplicant" can be found in the repositories. Simply fire up Synaptic & install the package or run this command from a terminal window:
> sudo apt-get install wpasupplicant
There is no need to compile it from source. This is how you use wpa-supplicant for wireless security:

[http://www.ubuntuforums.org/showthread.php?t=202834]("http://www.ubuntuforums.org/showthread.php?t=202834")

---

### Post by iClouseau88 on 2006-12-04
Hi wieman01,
I followed your June 24/06 HOWTO, but I am stuck with the following:
1.  What is "network", e.g. 192.168.168.0?
2.  How do I get "network"?  iwconfig & iwlist scan don't show it.
3. WPA-PSK Generator does not work well with mixtures of symbols and alpha-numerics, as the former creates syntax errors.  It appears shorter and simpler phrases with very few selected symbols do work.  Any suggestion to improve or get around the problem? Being reluctant to simplify the existing passphrase in view of security, I would hate to re-config my DLink DI-624c router after efforts spent to keep it from rebooting.  By the way, I use DLink WNA-2330 wireless card which has Atheros chipset.

Thanks in advance.

---

### Post by wieman01 on 2006-12-04
Hello iClouseau88:

1. Are you using DHCP? Then you don't need the IP section. All these settings specify a network using fixed IP.
2. Again, if you have DHCP enabled, you don't need this section. Just follow one of the sample instructions for DHCP & wireless security (appendix).
3. Simply add quotes (""). Thanks for highlighting this, I have updated my guide. I am also in favor of strong encryption keys using specials characters, etc. Should work now.

---

### Post by iClouseau88 on 2006-12-04
Hello wieman01:

Thanks for your reply.

1. Yes, I am using my laptop as a DHCP client, and enabled it accordingly as you suggested.
2.  Thanks for the update.  Since your revision/update notes only appear at the end of the HOWTO, some newbie like myself may not notice.  How about a little revision, e.g. "passphrase including a mixture of alpha-numerics and special characters" (Quotes ""INCLUDED in this case)? Another revision: No quotes required for normal/asci/hex characters.  You got my drift?

3.  I am a bit hazy about your Post#2.  I am confused about the sequence of the commands.  You must have meant the following?

cd /etc/init.d
Add "networking restart" after /etc/init.d/
sudo gedit wireless-network.sh
sudo chmod +x wireless-network.sh
 
cd /etc/rcS.d/
sudo ln -s/etc/init.d/wireless-network.sh S40wireless-network

4. What is boot sequence S40?  Where do I find info on this and other boot sequences?

Regards

---

### Post by wieman01 on 2006-12-04
Hello iClouseau88:

I have updated the guide. Please let me know if that is any clearer now. Point taken.

Not sure what the second problem relates to though... Run this from a terminal window & it will open text editor:
> sudo gedit /etc/init.d/wireless-network.sh
The paste this & save the file:
> /etc/init.d/networking restart
From terminal again, change the permissions of the script we have just created:
> sudo chmod +x wireless-network.sh
The create a symblink (terminal):
> sudo ln -s /etc/init.d/wireless-network.sh /etc/rcS.d/S40wireless-network
That should do. Google for "run levels" & "init" if you want to know more about startup scripts, etc. Does that help?

---

