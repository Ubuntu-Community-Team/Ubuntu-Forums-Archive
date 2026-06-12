---
title: "[SOLVED] Dual Booting Vista-Gutsy--&amp;gt;Wireless Problem..."
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by Lazy-buntu on 2008-04-07
Alright here's my story: Last year I hear about this thing called "Linux" so I decided to check it out. After doing some research I thought it sounded pretty nice, so I nuked my old PC I had laying around (40GB HDD, 700ish MHz intel celeron processor, 196ish MB RAM, etc.) and installed Xubuntu 7.10.

I had to fight with the wireless (which I still have to reinstall the drivers with Ndiswrapper each time I log on), but that's a fight for another day.

I decided I felt comfortable enough to install Ubuntu on another partition of my laptop and dual boot it with Vista  (shrunk Vista partition to free up 30GB of space, booted up live cd, created a 1GB swap partition, created the ext3 partition for the Ubuntu install, installed GRUB just to that partition, installed EasyBCD on vista)--no problem booting into either OS



Okay here's the problem: no wireless :twisted: broadcom drivers again :confused:

So I try and tackle the problem based on some walkthroughs and this is about what I did:

1. I go into synaptics package manager, install ndiswrapper.

2. I navigate my way through the vista partition and find the WLAN folder of drivers and files and copy it over to a new folder in the ubuntu partition as "Wireless Drivers"

3.  sudo gedit /etc/modprobe.d/blacklist            
    I add "blacklist bcm43xx" at the bottom of the file and save

4. sudo ndiswrapper -i "/home/ubuntu-dualboot/Wireless Drivers/bcmwl6.inf"
    I install the only ".inf" file in the folder--which brings along the .sys and whatever else

5. sudo ndiswrapper -l
   shows the bcmwl6 driver installed--hardware present, bcm43xx alternate whatever

   sudo ndiswrapper -m
   talks about adding the alias wlan0

6.   sudo modprobe ndiswrapper
      sudo modprobe -r bcm43xx
   
6. Reboot my computer

7. I try iwconfig:

    lo and eth0 both don't have wireless extensions (eth1 was the wireless device)

8. sudo ndiswrapper -l
   driver and hardware is still present


Any ideas on what to do? I've tried the devoted HP 6000 thread, and numerous wireless threads to no avail.

Thanks.

---

### Post by icechen1 on 2008-04-07
[This]("http://ubuntuforums.org/showthread.php?t=706034&highlight=broadcom+easy") how-to should work.I think you forgot to add "ndiswrapper" in /etc/modules.

---

### Post by Lazy-buntu on 2008-04-07
Thanks I'll try that out, I'll post something soon if it works, since I'm quitting for the night soon.

---

### Post by MasterJS on 2008-04-07
7.10 is supposed to have a lot better broadcom driver support. It worked on my laptop really well. All i had to do was enable the restricted driver in the Restricted Driver Manager.

---

### Post by Lazy-buntu on 2008-04-08
I'm not at home right now, but when I tried to enable the restricted drivers I got the usual fw-cutter error, so I went ahead with Ndiswrapper.


I tried the how-to link, but wlan0 (eth1) still doesn't appear when I do iwconfig, same old lo and eth0 with no wireless extensions.

BTW: when I'm working on the ubuntu side of the dual boot I don't have an internet connection..I have to reboot into vista to post here or find any info on the topic. 

I won't be home until 3-4pm est, I'll more than likely start working on it then.

---

### Post by Lazy-buntu on 2008-04-08
I'm thinking I'll try a wired connection and update first. Then I'll follow this guide step-by-step:

[http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/](http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/)

Does this look like a pretty sound guide? I could also try using the restricted drivers/fwcutter after I get the wired connection. I'm just hoping my router/WAP has a built in switch/hub lol

---

### Post by arbulus on 2008-04-08
I installed Gutsy on my laptop with the broadcom43xx wifi card and the driver was installed automatically through the Restricted Drivers Manager. 

You said you were going to try to get a wired connection?  I would definitely try that, install all updates and see if the Restricted Driver will work for you then.

---

### Post by Lazy-buntu on 2008-04-08
Yeah I'll let you know how that works out, hopefully from a fully operational wireless connection :guitar:

---

### Post by Lazy-buntu on 2008-04-08
I've got some good and bad news: I'll give you the bad first..

-I couldn't get a wired connection to work for some odd reason, probably has to do with the router itself, worse yet is my f'ing CAT-5 cable is stuck in my laptop LOL  update:::put some elbow grease into it, now it's out woot::


Good news: I followed the guide that I linked and now when I run iwconfig I get a nice blurb on eth1 (my wireless device)

--if i click on the network button over by the time/logout button I can see my WAP as well as two neighbors', but when I go to configure my access point with WEP (not WPA, yeah I know WEP is crap, but it still keeps noobs off the network) it does not work


here's what I did: went to network -> changed wireless from roaming mode to enter my ESSID, I enter in my WEP code, and configure as DHCP

if i go to run another iwconfig the essid does not work (yes i've got the correct essid and it's set to broadcast--WEP is also correct, but I will triple check that next)

i'm wondering is there a file i can sudo gedit and just manual write in the info like

eth1
essid="my essid"
WEP="my hex WEP code"

etc etc...

Thanks.

---

### Post by Lazy-buntu on 2008-04-08
sort of answered my own question: 
I found   [http://ubuntuforums.org/showthread.php?t=684495&highlight=manually+enter+essid+WEP](http://ubuntuforums.org/showthread.php?t=684495&highlight=manually+enter+essid+WEP)  

copying and pasting: and assuming my device is eth1


sudo ifconfig **eth1** down
sudo dhclient -r **eth1**
sudo ifconfig **eth1** up
sudo iwconfig **eth1** essid "ESSID_IN_QUOTES"
sudo iwconfig **eth1** "type key here without quotes" HEX_KEY 
****Additional Comand that may be needed  -- sudo iwconfig <interface> key open  
sudo iwconfig **eth1** mode Managed
sudo dhclient **eth1**


does that look about right? but then to get it to do this when I boot up I have to do these steps(?):

Setting the Wireless Interface to Connect at Boot  ***Courtesy of Maricaibo

If you are successful in bringing up the Interface Manually, the commands may be placed inside the /etc/rc.local file to run the commands at boot, and establish a wireless connection. There is no GUI to give visual confirmation of the connection. The user should type ifconfig at the command line to verify an IP address has indeed been granted by the router.

The process of adding the commands to the /etc/rc.local file is documented below (this connects to an unencrypted network -- to connect to a WEP or WPA encrypted network, some modifications as used above will need to be added):

Code:

gksu gedit /etc/rc.local

This opens up the file in the gedit utility and allows you to make changes and save the file

Code:

ifconfig <wired network connection interface> down
ifconfig <wireless network connection interface> down
dhclient -r <wireless_interface>
iwconfig <wireless_interface> essid <router name>
iwconfig <wireless_interface> mode Managed
ifconfig <wireless_interface> up
dhclient <wireless_interface>

Be sure this text goes into the /etc/rc.local file BEFORE the line reading "exit 0".

Save and close the /etc/rc.local file.

Open up a Terminal window (the shell) and type in:

Code:

sudo chmod +x /etc/rc.local

This command turns the rc.local file into an executable that will run at startup. Here's an example of what the /etc/rc.local file should contain. Your device names may be different:

Code:

#
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

ifconfig eth0 down
ifconfig wlan0 down
dhclient -r wlan0
iwconfig wlan0 essid "ESSID_IN_QUOTES"
iwconfig wlan0 mode Managed
ifconfig wlan0 up
dhclient wlan0

exit 0

NOTE: The first line in the rc.local file downs your wired connection, so if for some reason you need the wired connection back just open up a Terminal window (shell) and type:

sudo <wired_interface> up
sudo dhclient <wired_interface>

---

### Post by randypr on 2008-04-08
I'm sure you're getting all kinds of wonderful expertise in  sudo, etc., but you could probably avoid all the typing by installing **Ubuntu 8.**

It supports WPA2. 

I had serious problems with 7.10 on a network with WPA2-TKIP (it refused to hook up my AirLink wifi w/ ralink driver),  but an install of 8 had me hooked up to the Internet with two clicks of the button and typing in the passkey.

Bam!: Internet.

You can download Ubuntu 8 using a BitTorrent client (I use Azureus) in about 20 minutes).

As for the speed problem: "196ish RAM" is really insufficient to run even a clean OS such as Ubuntu. You really need 512 or better, plus a graphics card of at least 128 RAM in order to get the best graphics and watch moviez, or even to enable the standard graphics on the desktop to their best advantage.

---

### Post by Lazy-buntu on 2008-04-08
That was my former project, my current project is my dual boot laptop (specs are in my signature), I'm using WEP too.

Wireless light is blue, last I checked I could see networks, but I couldn't connect to any of them.

I've tried the stuff I posted, but none of that worked either. Anyone have a similar problem of not being able to connect to a wireless network they could see?

---

### Post by Lazy-buntu on 2008-04-08
Okay here's what I've tried since my last post: (as recommended by ubuntu help topics in the OS)

It mentions how IPV6 can cause problems so it says to gedit /etc/modprobe.d/aliases

there's a line:

something-----pf 10 ipv6

which it wants changed to      pf 10 off

i rebooted, tried roaming mode just to see networks, my network is shown and a popup wants the WEP key, I input the key and the network icon shows the blue lights moving in a circle

i thought it would work, but about 20 seconds later I get the same pop up



next thing i try: the help topics says if the ESSID "" shows when you do iwlist <interface> scan then acpi support must be interfering so try booting with the options:  pci=noacpi

I'm not sure if I did it correctly--I'm dual booting so EasyBCD shows up, I choose Neosmart Linux--> GRUB loads so i press e to edit boot options (i think) i scroll down once to the kernel and press e again:
it pulls up > irqdebug (i think), so I add after that pci=noacpi


Honestly I'm running out of ideas: My wireless switch is blue and can be switched off to red, in roaming mode I can see my network and my neighbors', I just cannot connect...:confused:

---

### Post by Lazy-buntu on 2008-04-09
I was reading [http://ubuntuforums.org/showthread.php?p=4684447&posted=1#post4684447](http://ubuntuforums.org/showthread.php?p=4684447&posted=1#post4684447)

Is feisty a better choice for HP laptops? I posted a reply on that thread:

> **Lazy-buntu said:**
> I've got an HP Pavilion dv6308, I just started dual booting Gutsy on monday, and I have yet to get the wireless working. I started a thread: [http://ubuntuforums.org/showthread.php?t=748882&highlight=dual+boot+wireless](http://ubuntuforums.org/showthread.php?t=748882&highlight=dual+boot+wireless)

I don't know if this is an old thread or not, but what should I do? I haven't even started with the nvidia 6150 problems I know I will have.

Do I:

1. stick with gutsy
2. burn a feisty live cd and format the gutsy partition --> dual boot with feisty instead of with gutsy
3. or hardy heron beta

Vista hasn't given me any real problems, but it's a resource hog. I'm pretty new to linux, so I want a stable, effecient distro to dual boot with vista.

What features does feisty lack that gutsy has (if any)?

---

### Post by Ayuthia on 2008-04-10
> **Lazy-buntu said:**
> sort of answered my own question: 
I found   [http://ubuntuforums.org/showthread.php?t=684495&highlight=manually+enter+essid+WEP](http://ubuntuforums.org/showthread.php?t=684495&highlight=manually+enter+essid+WEP)  

copying and pasting: and assuming my device is eth1


sudo ifconfig **eth1** down
sudo dhclient -r **eth1**
sudo ifconfig **eth1** up
sudo iwconfig **eth1** essid "ESSID_IN_QUOTES"
sudo iwconfig **eth1** "type key here without quotes" HEX_KEY 
****Additional Comand that may be needed  -- sudo iwconfig <interface> key open  
sudo iwconfig **eth1** mode Managed
sudo dhclient **eth1**


does that look about right? but then to get it to do this when I boot up I have to do these steps(?):



It looks about right.  The only item that I see that I am not for sure if I understand is:
```
sudo iwconfig **eth1** "type key here without quotes" HEX_KEY
```
I think that it should be:
```
sudo iwconfig **eth1** key "Your hex key without the quotes"
```

I am not for sure about the last part (the /etc/rc.local portion) because I have not used it before.

---

### Post by Lazy-buntu on 2008-04-10
As it stood two days ago, I had gutsy gibbon installed with the ndiswrapper driver working and I could see wireless networks, but I could not connect.

Yesterday I reformatted the gutsy install and put feisty in place of it--wireless not working at all.

With both installs hard wired connection to the internet (through my router) does not work either. This might be the fault of my router.

Right now I'm looking into Fedora 8 (downloading the Live CD now) to see if that would be more compatible with my hardware.



**Thanks for the replies, but has anyone had a similar experience where they could see wireless networks, but not be able to connect to them? (in Gutsy, since I can always get that install back the way it was) **

or anyone with a HP Pavillion dv6308 (or similar HP laptop) have a distro recommendation --similar to Ubuntu (GNOME desktop, pretty easy to set up a network printer, synaptics package manager, etc.) for someone with Broadcom chipset and Nvidia graphics?

---

### Post by Lazy-buntu on 2008-04-10
Okay, didn't really like what I was seeing with Fedora, so I'm back to gutsy with my posted bold problem, I think I'll rummage through the wireless forum to see what I can find.

Thanks for the input

---

### Post by arbulus on 2008-04-11
> **Lazy-buntu said:**
> Okay, didn't really like what I was seeing with Fedora, so I'm back to gutsy with my posted bold problem, I think I'll rummage through the wireless forum to see what I can find.

Thanks for the input


What I'm thinking is that if you cannot connect with a hard line to the net, then you're going to have a hard time with installation.  The broadcom card is pretty much always going to need a driver installed post installation, and of course you can't get the driver if you can't get online.  So you have a difficult situation. And that's going to be the same for pretty much any distro you choose.

---

### Post by Lazy-buntu on 2008-04-11
opened new thread in wireless, going to mark this one as solved I guess

see: [http://ubuntuforums.org/showthread.php?p=4692890#post4692890](http://ubuntuforums.org/showthread.php?p=4692890#post4692890)

---

