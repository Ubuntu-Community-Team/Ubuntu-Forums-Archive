---
title: "[SOLVED] how do I connect to an SSID that requires websecure 2.0"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by quinnten83 on 2007-09-28
My school (and also where I work) requires you to install a program that is called websecure in order to connect to their wireless accesspoint.
This prgram is available for windows. I believe it sets certain certificate which you can use to connect to my schools SSID.
I would like to be also be able to connect to the wireless network at school using my feisty fawn, but I can't since I can't install the .exe for the secureweb2.0.
Do any of you know of a way around this? Support for linux at my school is completely nonexistant.

---

### Post by jgoguen on 2007-09-28
We need some more information about the wireless setup, if at all possible.  To start with:

Is this WPA Enterprise or WPA2 Enterprise?  I assume its one of those, since you need to install a program with a certificate.  Can you get this certificate separate from the program, perhaps from a friend with Windows?

What's the EAP method?  PEAP, TLS, or TTLS?

What's the key type?  AES-CCMP, TKIP, or Dynamic WEP?

What's the second phase authentication?  PAP, MSCHAPv2, MSCHAP, GTC?

Try to get all that, hopefully your school/work isn't so anti-Linux to not even give you that basic information.

---

### Post by quinnten83 on 2007-09-28
> **jgoguen said:**
> We need some more information about the wireless setup, if at all possible.  To start with:

Is this WPA Enterprise or WPA2 Enterprise?  I assume its one of those, since you need to install a program with a certificate.  Can you get this certificate separate from the program, perhaps from a friend with Windows?

What's the EAP method?  PEAP, TLS, or TTLS?

What's the key type?  AES-CCMP, TKIP, or Dynamic WEP?

What's the second phase authentication?  PAP, MSCHAPv2, MSCHAP, GTC?

Try to get all that, hopefully your school/work isn't so anti-Linux to not even give you that basic information.

I can see what I can discover from the instructions on the school website to connect in windows.
I must say that 98% of the stuff you just mentioned sounds like chinese to me.
I have the instructions but they are all in Dutch (and no pictures).

I'm using Feisty:
it says here that it is WEP
something about a key being delivered to me automatically, I assume that is automatically receive verification key ( I sorry, my computer with an English windows does not is a desktop with no wireless).
EAP-type is SecureW2
computer does not need to be verified
in certifcates, i don't need to verify the server certificate
it also asks to select PAP from the list.
This is as much as i can get out of my translation. 
I am sorry, but technical translation are veeeeeeery difficult and I have like ZIP understanding of Wireless connections.
I read on the net something about xsupplicant, but that is not installed on my pc, at least whereis did not yield a result for xsupplicant. Also the instructions threw me off after the second sentence.
I have attached the file with instructions (in dutch), if there is a genious out there who speaks dutch perhaps he can help.
Gawd I feel like such a NOOB.

---

### Post by quinnten83 on 2007-09-28
The program is called secureW2 btw and not websecure.
I just send an email to my school IT department, hoping that they will give me an answer.
But knowing my school, I am not holding my breath.

---

### Post by jgoguen on 2007-09-28
Actually, this isn't as bad as you may think :)  My university also requires the use of SecureW2, and it sounds like they've set up exactly the same configuration as mine.  It doesn't install a certificate, so you don't need to worry about that.  It uses TTLS, so your EAP type is TTLS.  Give this a try next time you're near the network:

0.  Click on the NetworkManager applet near your clock and choose 'Connect to Other Wireless Network'
1.  In the new window, under Wireless Security, choose 'WPA2 Enterprise'.
2.  In Network Name, enter the SSID of your network.
3.  From EAP, select 'TTLS'.
4.  Leave 'Key Type' as it is (should default to Automatic).
5.  From 'Phase2 Type' choose 'PAP'.
6.  In 'Identity' enter your username.
7.  In 'Password' enter your password.
8.  Leave everything else as it is, and click 'Connect'.

If that doesn't work, open a Terminal (Applications -> Accessories -> Terminal) and give me the output of this command:
```
modprobe -l | egrep 'ath_pci|mad'
```

---

### Post by quinnten83 on 2007-09-29
> **jgoguen said:**
> Actually, this isn't as bad as you may think :)  My university also requires the use of SecureW2, and it sounds like they've set up exactly the same configuration as mine.  It doesn't install a certificate, so you don't need to worry about that.  It uses TTLS, so your EAP type is TTLS.  Give this a try next time you're near the network:

0.  Click on the NetworkManager applet near your clock and choose 'Connect to Other Wireless Network'
1.  In the new window, under Wireless Security, choose 'WPA2 Enterprise'.
2.  In Network Name, enter the SSID of your network.
3.  From EAP, select 'TTLS'.
4.  Leave 'Key Type' as it is (should default to Automatic).
5.  From 'Phase2 Type' choose 'PAP'.
6.  In 'Identity' enter your username.
7.  In 'Password' enter your password.
8.  Leave everything else as it is, and click 'Connect'.

If that doesn't work, open a Terminal (Applications -> Accessories -> Terminal) and give me the output of this command:
```
modprobe -l | egrep 'ath_pci|mad'
```

Dude,i love you in a totally nonsexual way. If this works, I will be veeeeeeery happy. I will even pass the information on to my school. Perhaps people with other distro's might also be able to use  it. You'll know on Wednesday if it worked.

---

### Post by jgoguen on 2007-09-29
I do want to make sure (because I didn't the first time...me == smrt) that you understand that if you're using the madwifi drivers, this won't work the first timeand if you're using the ndiswrapper driver, I haven't heard of anyone getting this to work at all.  You can open the Restricted Drivers applet (System -> Administration -> Restricted Drivers Manager) and see if anything's there.  If it says "Atheros Hardware Layer (HAL)" then you're using madwifi.  I don't know what appears if you're using ndiswrapper though...

If you are using madwifi, there's another set of directions I'll give you to compile the latest madwifi driver, compile the current NetworkManager with a hack to make it work, and then re-try the directions I gave for connecting.  It may take a bit to get going the first time, but I don't see why it wouldn't work.  

<TechnicalStuff>
Now, despite that I'm getting it working by hacking NetworkManager, it's actually madwifi that's broken.  They don't properly support wireless extensions, and so the way NetworkManager works doesn't play nice with it.  My hack tells NetworkManager to look for the existence of a file, and if it exists use madwifi instead of wext.  I think a proper solution would be to fix madwifi, but I don't know anywhere nearly enough about driver development or what needs to be done.
</TechnicalStuff>

---

### Post by quinnten83 on 2007-10-02
> **jgoguen said:**
> I do want to make sure (because I didn't the first time...me == smrt) that you understand that if you're using the madwifi drivers, this won't work the first timeand if you're using the ndiswrapper driver, I haven't heard of anyone getting this to work at all.  You can open the Restricted Drivers applet (System -> Administration -> Restricted Drivers Manager) and see if anything's there.  If it says "Atheros Hardware Layer (HAL)" then you're using madwifi.  I don't know what appears if you're using ndiswrapper though...

If you are using madwifi, there's another set of directions I'll give you to compile the latest madwifi driver, compile the current NetworkManager with a hack to make it work, and then re-try the directions I gave for connecting.  It may take a bit to get going the first time, but I don't see why it wouldn't work.  

<TechnicalStuff>
Now, despite that I'm getting it working by hacking NetworkManager, it's actually madwifi that's broken.  They don't properly support wireless extensions, and so the way NetworkManager works doesn't play nice with it.  My hack tells NetworkManager to look for the existence of a file, and if it exists use madwifi instead of wext.  I think a proper solution would be to fix madwifi, but I don't know anywhere nearly enough about driver development or what needs to be done.
</TechnicalStuff>

Hi there, 
I think that half of what you said just went completely over my head (and I am not even a noob!)
unfortunately it didn't work.
Checking to see if I use madwifi, i get the message: "your system does not require any restricted drivers". Which could be the case since my wifi worked right out of the box.
When I followed your instructions, I could not find anywhere to fill the "second phase authentication". Perhaps I am doing something wrong. I took a screenshot of the window I get when I try to make a new connection and attached it to this post:

The result of the terminal command was:
```
/lib/modules/2.6.20-16-generic/madwifi/wlan_acl.ko 
/lib/modules/2.6.20-16-generic/madwifi/wlan_ccmp.ko 
/lib/modules/2.6.20-16-generic/madwifi/ath_rate_amrr.ko 
/lib/modules/2.6.20-16-generic/madwifi/wlan.ko 
/lib/modules/2.6.20-16-generic/madwifi/ath_rate_sample.ko 
/lib/modules/2.6.20-16-generic/madwifi/wlan_tkip.ko 
/lib/modules/2.6.20-16-generic/madwifi/ath_pci.ko 
/lib/modules/2.6.20-16-generic/madwifi/wlan_xauth.ko 
/lib/modules/2.6.20-16-generic/madwifi/wlan_scan_sta.ko 
/lib/modules/2.6.20-16-generic/madwifi/wlan_wep.ko 
/lib/modules/2.6.20-16-generic/madwifi/wlan_scan_ap.ko 
/lib/modules/2.6.20-16-generic/madwifi/ath_rate_onoe.ko 
/lib/modules/2.6.20-16-generic/kernel/drivers/net/tokenring/madgemc.ko 
/lib/modules/2.6.20-16-generic/kernel/drivers/infiniband/core/ib_umad.ko 
/lib/modules/2.6.20-16-generic/kernel/drivers/infiniband/core/ib_mad.ko 
```

So I guess I am using madwifi after all???
For an open source project Linux is quite mysterious. 

Also I asked my school about the authentication and this is what they told me:
WPA2 enterprise
EAP: TTLS
key type: Dynamic WEP
second phase authentication: PAP


Well, try and see if this helps us any. I thank you for your help so far :)

---

### Post by jgoguen on 2007-10-02
I've been told that using modprobe isn't so accurate, since it returns the driver anyway.  I tried it on my system, and it says ndiswrapper is loaded even though I don't use Windows drivers at all on my MacBook :)  If Restricted Drivers Manager says no restricted drivers in use then you probably aren't using madwifi since it requires HAL which is restricted.

For some reason, NetworkManager doesn't show Phase2.  I thought it was there before, but maybe it only showed up when I compiled the latest.  Try this, it's the same version as in Ubuntu so I don't know why that makes a difference.  Compile options maybe :)

0.  Open a terminal (Applications -> Accessories -> Terminal) and make sure you have the build dependencies installed: sudo apt-get build-dep network-manager
1.  Download [http://jgoguen.net/src/network-manager-0.6.5.tgz](http://jgoguen.net/src/network-manager-0.6.5.tgz) and save it in your home directory.  I don't feel like looking for the official one right now, but you can use that one instead, everything works the same.
2.  Unpack the archive: tar zxf network-manager-0.6.5.tgz
3.  Go into the directory: cd network-manager-0.6.5
4.  Configure the package: ./configure --without-gnome
5.  Build (this may take a while): make
6.  Install: sudo make install

Restart NetworkManager (sudo /etc/dbus-1/event.d/25NetworkManager restart) and you should hopefully see Phase2 available now.

---

### Post by quinnten83 on 2007-10-03
OK, tnx man, 
I will try it as soon as I get back home from work.

---

### Post by quinnten83 on 2007-10-18
okay,
i tried again after recompiling ( that's what I did, right?) and i still don't get to see the phase2 option.
everything seems to have gone well. I got output for all which I did. Could it be the file I used?

---

### Post by jgoguen on 2007-10-18
Actually it's probably my fault, I forgot a couple important configure flags.  It just happened to work for me since /usr/local/sbin occurs before /usr/sbin in my path :)

First, go in the directory and run 'make clean' and try the directions above again, but this time use this command for configure:
```
./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var --without-gnome
```


Then, this command to make the required file to use madwifi:
```
sudo touch /etc/NetworkManager/.madwifi
```

---

### Post by quinnten83 on 2007-10-18
you are fast, 
I will try again soon...
thank you once again.

---

### Post by quinnten83 on 2007-10-18
Uhm wait-
is that do the instructions with the new configure, and after "sudo make install"  and restart of the network manager, run sudo touch /etc/NetworkManager/.madwifi

or is that run configure, then run touch and then the rest of the install?

sorry if it is a stupid question, I don't know much about the compilation process (yet).

---

### Post by quinnten83 on 2007-10-18
Nope tried it both ways and I still see no option for second phase.
I am starting to get that sinking feeling...

---

### Post by quinnten83 on 2007-10-18
lol 4 posts..
I just saw on the live CD that 7.10 does show the second phase authentication, Since I will upgrade/ reinstall anyway, I will go with that

thanks for your help.
if it works in 7.10 I will let you know.

EDIT:
It works like a dream, thanks for the help.
(how do I mark this solved?)

---

