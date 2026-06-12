---
title: "Airport Extreme w/ WPA in Ubuntu 6.10 PPC"
date: 2007-04-16
forum: Apple PPC Users
---

### Post by Mjolniir on 2007-04-16
OK, so I spent several hours this weekend using various tutorials to get Airport Extreme working on my Ubuntu install on my iBook G4.  Basically the purpose of this thread is to put all the info I used in one place, since most of the time I spent working on this was spent hunting for info.  The actual stuff I had to do in Ubuntu didn't take to long at all.

Here we go.
Part 1.  ( from this thread: [http://ubuntuforums.org/showthread.php?t=314036](http://ubuntuforums.org/showthread.php?t=314036) )

> **webman2k said:**
> Hello all,

I tested this twice to make sure it would work the first time each time.  I've successfully gotten AE to work on an Edgy installation.  I have an iBook G4 (late 2004 model).  Your results might vary:

1. Connect the computer via ethernet cable, and install Edgy along with any available updates.

2. Enable the "Universe" repository from System > Administration > Synaptic Package Manager.

3. Download the following file, and copy it to your desktop:
[http://drinus.net/airport/wl_apsta.o](http://drinus.net/airport/wl_apsta.o)
If that link is dead, just google the file name and find a working download.

4. In terminal:
sudo apt-get install bcm43xx-fwcutter
cd Desktop
sudo bcm43xx-fwcutter -w /lib/firmware wl_apsta.o
sudo modprobe bcm43xx

5. Now set up your wireless in System > Administration > Networking

6. Close Networking, and unplug your ethernet connection ;)

Wireless works upon restart perfectly, annd hasn't dropped out in over a day.  It seems to be at 11M transfer, but I'm not going to complain - it's working! If you have trouble, try deactivating the wired connection in Networking - I had to do that on the second try. You can turn it back on later if you need it.

Based on instructions found here:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper)

-Mark
 
That stuff got me working just using the Networking under System>Administration, but I had to enter in my router ssid manually and I had to turn off WPA on my router.  But it did work.  But I am not comfortable running my router open for anyone so I went for WPA.

Part 2

I don't know exactly what thread I got this from, but it worked fine.

1.  Install network-manager-gnome.  I found this in Synaptic Package manager under networking.  After that installed and restarted, the network manager icon showed up in my tray, but it said it could find no devices.

2.  Go to System>Administration>Networking and under the properties for each device, UNCHECK make active if it is checked.

3.  Go to Applications>Accesories>Terminal, and enter:

sudo killall NetworkManager 
enter password if prompted
sudo etc/init.d/networking restart (this gives a bunch of feedback in terminal and takes a minute)
sudo NetworkManager

After this, you will see the network manager icon in the tray again.  If it still says it has no devices, restart and you should be good.  Now you can click the NetworkManager icon and choose your wireless network.  It will ask you for a passphrase assuming you have enabled WEP or WPA.  If you have WPA on your router, you will have to enter the hexadecimal version of your key, the plaintext will not work.

To get your hexadecimal WPA key:
1. Go to terminal,
sudo wpa_passphrase (your wireless ssid)
The Terminal will say it is getting it or something like that, and there will be a cursor below that line.
Enter your WPA password

Now Terminal will give you a very long string for your key.  I just copied and pasted it into NetworkManager's password prompt, and also in the keychain request that came up right after.

That was all.  Now AE is working flawlessly and fast.  I seem to be getting similar download speeds to what I get in OS X so I am happy.

Anyway, I thought it would be useful to put all that in the same place.

Thanks to the people who originated these steps.  I wish that I had saved all the threads I used, but you know who you are.

---

### Post by dJeez on 2007-04-18
This works like a charm, and saves me the time to find everything out by myself. Thanks a lot :p.

---

### Post by lbx on 2007-04-19
I can't get my system to connect to my router via WPA. I can't even get an option for WPA encryption in the connection dialog. I have tried Kubuntu with KNetworkManager as well, to no avail. I am using a 900mhz G3 iBook. Any advice?

---

### Post by travnewmatic on 2007-04-29
I have no idea why, but i thought that i was inputting the commands verbatim from the tutorials that I've been using.  No idea why, but yours did the trick.  I really appreciate it!

Now i just have to figure out how to get Java working in firefox...  :D

---

### Post by travnewmatic on 2007-04-30
...
looks like i'm going to have to do the whole thing over again...

i just upgraded to the latest version of ubuntu and it got rid of my wireless configuration.

here we go again.

---

