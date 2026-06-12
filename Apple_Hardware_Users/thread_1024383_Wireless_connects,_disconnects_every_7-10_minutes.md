---
title: "Wireless connects, disconnects every 7-10 minutes"
date: 2008-12-29
forum: Apple Hardware Users
---

### Post by jrdemasi on 2008-12-29
Hey everyone,

I just installed Intrepid on my MacBook.  Everything works out of the box including my wireless which really pleased me.  I do have one slight problem.  When I connect to my wpa2 personal encrypted network the wireless cuts out every 7 to 10 minutes and I have to manually rejoin the network.  I have it set to automatically join, but I can't find a reason why it happens.  I was going to try wicd for kicks, but I wasn't able to get that installed either.  I don't have a lot of time to mess around because I have a bunch of school work to do over my Christmas break.  

Any help would be greatly appreciated


Edit:
This almost seems like it only happens while I'm shelled into my server.

---

### Post by hyperboloid on 2008-12-29
I had a similar problem with wireless dropping randomly, although with me it would reconnect automatically. 

So I switched to wicd and I haven't dropped a connection since.

---

### Post by wmoore on 2008-12-29
Check the DHCP settings (on your router?) and change the default lease time to about a week. I can't remember the specifics but I did have a similar problem some time ago and that was the fix.

---

### Post by jrdemasi on 2008-12-29
Thanks for the feedback.  The DHCP lease is a very long time, something like 3-4 days.  I don't know how to get wicd working under Intrepid because it's not in the repos as far as I know.  I googled and found the fix for Hardy but not Intrepid.  Help?

---

### Post by bryonak on 2008-12-29
Straight from the [download section]("http://wicd.sourceforge.net/download.php") of the WICD homepage, I just changed the Ubuntu version from Hardy to Intrepid:


Go to System > Administration > Software Sources > Third Party Software > Add..., and enter the following line:
```
deb http://apt.wicd.net intrepid extras
```
where intrepid is your version of Ubuntu in lowercase (dapper, edgy, feisty, gutsy, hardy, intrepid). You'll also need to add the key used for signing Wicd by running the following command in a terminal:
```
wget -q http://apt.wicd.net/wicd.gpg -O- | sudo apt-key add - 
```
Now, click Reload, and wait while the package lists are downloaded.


Then open a terminal and type
```
sudo aptitude install wicd
```
it will prompt you to uninstall the gnome network manager, type **yes**. You might have to start wicd by issuing Alt+F2 and typing **wicd-client**. Enjoy.

---

### Post by jrdemasi on 2008-12-30
> **bryonak said:**
> Straight from the [download section]("http://wicd.sourceforge.net/download.php") of the WICD homepage, I just changed the Ubuntu version from Hardy to Intrepid:


Go to System > Administration > Software Sources > Third Party Software > Add..., and enter the following line:
```
deb http://apt.wicd.net intrepid extras
```
where intrepid is your version of Ubuntu in lowercase (dapper, edgy, feisty, gutsy, hardy, intrepid). You'll also need to add the key used for signing Wicd by running the following command in a terminal:
```
wget -q http://apt.wicd.net/wicd.gpg -O- | sudo apt-key add - 
```
Now, click Reload, and wait while the package lists are downloaded.


Then open a terminal and type
```
sudo aptitude install wicd
```
it will prompt you to uninstall the gnome network manager, type **yes**. You might have to start wicd by issuing Alt+F2 and typing **wicd-client**. Enjoy.

I appreciate the quick response.  I installed wicd but now my network just shows up as <hidden> and won't connect.  I use wpa2 encryption. I had this problem when I used to use Gentoo but the fix that I used doesn't work in Ubuntu.

---

### Post by cyberdork33 on 2008-12-31
What you have described is a common symptom of using a hidden SSID. Just unhide it. Hiding SSID's is false security anyway as anyone with any skill whatsoever that might want to crack your AP would be able to see your AP anyway.

---

### Post by bryonak on 2008-12-31
Apart from cyberdork being completely right, can you log into the network by pressing the "arrow" button right of the "Network" button in the WICD interface, clicking on "Hidden Network" and entering your ESSID there?

The <hidden> tag just tells you that a hidden network has been detected, the functionality of figuring out its ESSID and connecting may work on certain cards, then again not on others.

Hiding networks is a concept called "Security by Obscurity", which means it's secure as long as noone bothers to scan it profoundly. Someone with the ability to crack a network (or even to set his own network card to "audit" mode, which isn't hard at all) will find it trivial to bypass this measure.

---

### Post by cyberdork33 on 2008-12-31
> **bryonak said:**
> Hiding networks is a concept called "Security by Obscurity", which means it's secure as long as noone bothers to scan it profoundly. Someone with the ability to crack a network (or even to set his own network card to "audit" mode, which isn't hard at all) will find it trivial to bypass this measure.
This is partly demonstrated by the fact that wicd sees that there is a hidden network available...

---

### Post by jrdemasi on 2008-12-31
I realize anyone can still find it, The fact that it's hidden didn't matter though, even when I unhid it it didn't work, or type the essid manually.  I did a little more fishing around and fount that I have no /etc/wpa_supplicant/wpa_supplicant.conf file which could be part of the problem?

---

### Post by bryonak on 2009-01-01
> **jrdemasi said:**
> I realize anyone can still find it, The fact that it's hidden didn't matter though, even when I unhid it it didn't work, or type the essid manually.  I did a little more fishing around and fount that I have no /etc/wpa_supplicant/wpa_supplicant.conf file which could be part of the problem?

I haven't got that file either, no worries there.

Let's do some diagnosis... could you post the output of```
sudo dmidecode -s system-product-name
```(which you should include generally when asking for help with a Mac, so people will know what hardware you have)

Do you know whether you have an Atheros or a Broadcom card? The output of```
lspci
```will tell you (maximize the terminal before typing this).

Also when you open the WICD GUI and go to "Preferences", what is your WPA Supplicant Driver? Mine is wext, which is the recommended choice if you have an Atheros card and use the new Atheros modules. But first check what card you actually have...

On the other hand, could you be a bit more precise about the problem? Does it happen when you use SSH generally or only to one specific target? Could it be that your router/access point is dropping SSH tunnels? Sounds strange, but I've had my fair share of silly firmware errors with rather cheap routers...

---

### Post by jrdemasi on 2009-01-01
> **bryonak said:**
> I haven't got that file either, no worries there.

Let's do some diagnosis... could you post the output of```
sudo dmidecode -s system-product-name
```(which you should include generally when asking for help with a Mac, so people will know what hardware you have)

Do you know whether you have an Atheros or a Broadcom card? The output of```
lspci
```will tell you (maximize the terminal before typing this).

Also when you open the WICD GUI and go to "Preferences", what is your WPA Supplicant Driver? Mine is wext, which is the recommended choice if you have an Atheros card and use the new Atheros modules. But first check what card you actually have...

On the other hand, could you be a bit more precise about the problem? Does it happen when you use SSH generally or only to one specific target? Could it be that your router/access point is dropping SSH tunnels? Sounds strange, but I've had my fair share of silly firmware errors with rather cheap routers...

```
jonathan@pwnzor:~$ sudo dmidecode -s system-product-name
MacBook2,1

```

I won't waste the space and show an lspci output.  The card is Atheros.  WICD is set to use the wext wpa supplicant driver.

To be a bit more precise - the problem occurs when I am shelled into any server.  I tried multiple servers and the same thing happened.  I am using an Airport Extreme router and I don't have this problem on my other Ubuntu desktop using wireless.  It's not the same card of course but it proves that it isn't a network-wide issue. 

UPDATE: This isn't obviously related to ssh because while I was just downloading updates it disconnected and I wasn't shelled into a server at all (using network manager since wicd still isn't working)

---

### Post by lswb on 2009-01-02
> **cyberdork33 said:**
> What you have described is a common symptom of using a hidden SSID. Just unhide it. Hiding SSID's is false security anyway as anyone with any skill whatsoever that might want to crack your AP would be able to see your AP anyway.

Except, of course, the wicd and NetworkManager developers! :)

---

### Post by bryonak on 2009-01-02
> **jrdemasi said:**
> 
The card is Atheros.  WICD is set to use the wext wpa supplicant driver.



Since the problem persists with both the Gnome Network Manager and WICD, the main software error I can assume would be the wireless kernel driver. (Apart from a bug in your Ubuntu configuration, but let's try the obvious stuff first).
Do```
lsmod | grep ath
```
If this returns ath5k or ath9k, you're using the new Atheros modules (that were finally released this summer). If it returns ath_pci or ath_hal or if ```
lsmod | grep wrapper
``` returns anything at all, you're using legacy drivers, which will quite probably cause problems on Intrepid. They're still included because they were standard in Hardy and now might have been activated for some reason.

The other possibility on the client side would be faulty hardware, which can easily be checked by booting OSX on that laptop.
If your wireless gets recognized immediately with the Ubuntu liveCD, you might want to try and see if the problem exists there too.
If that works, it indicates a configuration glitch on your current install.

It doesn't hurt to double-check your router settings, though I can't really tell you what to look for on an Airport Extreme (good hardware btw).

A temporary work-around with WICD would be this: click on that little arrow left of your network name and select "Automatically connect to this network".
Then make sure that in the Preferences dialog the entry "Automatically reconnect on connection loss" is checked.


> I won't waste the space and show an lspci output.
Yep, that's why I didn't ask you to post it ;)

---

### Post by cyberdork33 on 2009-01-02
Just FYI, with the MacBook2,1 you should be using the ath9k driver.

---

### Post by jrdemasi on 2009-01-02
> **bryonak said:**
> Since the problem persists with both the Gnome Network Manager and WICD, the main software error I can assume would be the wireless kernel driver. (Apart from a bug in your Ubuntu configuration, but let's try the obvious stuff first).
Do```
lsmod | grep ath
```
If this returns ath5k or ath9k, you're using the new Atheros modules (that were finally released this summer). If it returns ath_pci or ath_hal or if ```
lsmod | grep wrapper
``` returns anything at all, you're using legacy drivers, which will quite probably cause problems on Intrepid. They're still included because they were standard in Hardy and now might have been activated for some reason.

The other possibility on the client side would be faulty hardware, which can easily be checked by booting OSX on that laptop.
If your wireless gets recognized immediately with the Ubuntu liveCD, you might want to try and see if the problem exists there too.
If that works, it indicates a configuration glitch on your current install.

It doesn't hurt to double-check your router settings, though I can't really tell you what to look for on an Airport Extreme (good hardware btw).

A temporary work-around with WICD would be this: click on that little arrow left of your network name and select "Automatically connect to this network".
Then make sure that in the Preferences dialog the entry "Automatically reconnect on connection loss" is checked.



Yep, that's why I didn't ask you to post it ;)

Before I post those outputs, I haven't successfully been able to connect to my network using WICD.  My network is using WPA2 but it shows up as <hidden> in WICD and won't connect.  If I add the network essid manually it has the same errors.  So I can't do your WICD fix unfortunately or I would agree that would be alright for now.

```
jonathan@pwnzor:~$ lsmod | grep ath
ath9k                 274232  0 
mac80211              216820  1 ath9k

```

lsmod | grep wrapper didn't return anything so I guess it doesn't apply.

---

### Post by bryonak on 2009-01-04
> **jrdemasi said:**
> 
```
jonathan@pwnzor:~$ lsmod | grep ath
ath9k                 274232  0 
mac80211              216820  1 ath9k

```

lsmod | grep wrapper didn't return anything so I guess it doesn't apply.

Well, at first sight your setup should be working, though WICD not being able to connect prompts to some faulty config.

For your WPA2 encryption, do you use a *passphrase* or a *preshared key*? Maybe you selected the wrong one in WICD's "Advanced Settings" menu (the button below your network name after you click that little arrow)

Let's try some debugging...
If you could install WICD again, open a terminal and type: ```
sudo killall wicd wicd-client
```
Then```
sudo wicd
```Leave that terminal open and start a new one (with Ctrl+Shift+N for example) and there type (without sudo, since we want to have only user rights on this one)```
wicd-client
```
Then try to connect with the wicd-client (the standard GUI via the tray icon) and post any output that appears in the terminals here.

Could you also post the output of```
cat /etc/network/interfaces
```

Granted, WICD isn't as accessible or for that matter "user friendly" as Gnome's manager, but I find it way superior for advanced usage... so the reason why I mainly tell you about WICD is that I'm using it exclusively on all my machines.

---

### Post by stream303 on 2009-01-05
I just went through this myself - maybe just dropping the speed of the wireless card itself might help - unless you need absolute speed with networking transferring large files, movies, etc among a local network, maybe slowing down the card speed would help for general purpose internet use.  (if your internet speed isn't 54mb, why not knock the speed down?)

[http://ubuntuforums.org/showthread.php?t=1028556](http://ubuntuforums.org/showthread.php?t=1028556)

Essentially the change is made to /etc/rc.local for whatever you are using (wlan0, ath0, etc)

```
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

iwconfig wlan0 rate 5.5M fixed

exit 0
```

I also like to make sure that I'm at least about 2 channels away from strong neighbors:

```
sudo iwlist wlan0 scanning
```

and see what channel they are on, and change the router accordingly.

---

### Post by jrdemasi on 2009-02-07
> **stream303 said:**
> I just went through this myself - maybe just dropping the speed of the wireless card itself might help - unless you need absolute speed with networking transferring large files, movies, etc among a local network, maybe slowing down the card speed would help for general purpose internet use.  (if your internet speed isn't 54mb, why not knock the speed down?)

[http://ubuntuforums.org/showthread.php?t=1028556](http://ubuntuforums.org/showthread.php?t=1028556)

Essentially the change is made to /etc/rc.local for whatever you are using (wlan0, ath0, etc)

```
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

iwconfig wlan0 rate 5.5M fixed

exit 0
```

I also like to make sure that I'm at least about 2 channels away from strong neighbors:

```
sudo iwlist wlan0 scanning
```

and see what channel they are on, and change the router accordingly.

Thanks.  This didn't solve the problem completely but it does seem to disconnect less, maybe coincidental.  I have just been using another wireless adapter right now until a fix becomes available.

---

