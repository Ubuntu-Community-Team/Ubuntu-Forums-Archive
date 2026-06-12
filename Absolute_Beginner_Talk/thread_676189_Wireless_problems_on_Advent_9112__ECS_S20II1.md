---
title: "Wireless problems on Advent 9112 / ECS S20II1"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by david_stott on 2008-01-23
Hello-
I've recently installed Ubuntu (gutsy) on my brand new shiny Advent 9112 laptop (as a dual boot with Vista- my first Linux experiment). This machine is apparently a rebranded ECS S20II1.  Everything works fine and dandy apart form the wireless....

I can connect to networks but nothing happens when I open firefox. When I use other services (such as update manager) and watch the network history in System Monitor there is lots of activity for a brief period & then it all goes quiet. The wireless card is built into the machine.

I assume this is a driver problem so I started out trying to find out what card I've got- 
Device Manager says it is a* Ralink 802.11bg Wlan with a usb vendor specific interface*. This seemed a bit vague so i tiried looking it up in windows device manager- it is similarly vague- *Ralink 802.11g Minicard Wireless adapter*.

in an attempt to find more specific info i followed the advide on the wifi docs pages and used the following command in terminal:
lspci -v | less
It says absolutely nothing about any wireless card! Remembering that the device manager said something about usb i tried the same command for usb stuff (i dont have it to hand just now but it's on the wifidocs pages)

Can anyone help me find out what driver i need? / how to fix this problem?
many thanks!

D

---

### Post by Hospadar on 2008-01-23
I would try a couple things:

First, use the "iwconfig" command to check and see if your wireless card is really being detected as a wireless network device, it'll be obvious from the output if it is.

Second, if it is detected, I would try using a manual connection instead of letting network manager do it for you.  I have a ralink usb adapter that I sometimes use on my desktop, and when I let network manager handle things, it frequently drops the connection, but when i configure my wireless manually, it works fine.  That said, WPA encryption is a massive pain to set up manually, you can try it, but I've never once successfully done it.  If it's your home network, try opening it up or using wep (which is not very secure, if you are worried about that sort of thing) to at least see if you can make it work at all.

If you still have the same issues with manual configuration (assuming you set up the manual config properly, again, try it on an open wifi network so you can be more sure that the problem is drivers and not configuration) then I'd do some googling or call the manufacturer and figure out exactly which ralink chipset you have.  you might glean some extra info by seeing which kernel module is loaded.  for example, my ralink is an "rt73" and as such it uses the "rt73usb" module.  so try doing a "lsmod | grep rt" and see what you get.

Once you've figured out which chipset, you can try using the [serialmonkey ralink drivers]("http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page").  you may want to search around google or these forums for more info on how to build them and set them up, they are pretty commonly used for ralink hardware.  These drivers will probably not play well with manual configuration.


A couple notes:
if you are going to attempt a manual configuration, you'll need to uninstall network manager as per "sudo apt-get remove network-manager network-manager-gnome" and restart  your machine.  you may want to re-install them first so that they will be cached locally if you need to re-install them [without a network connection]. "sudo apt-get install --reinstall network-manager network-manager gnome"

As for manual configuration, check the community documentation or google and you'll no doubt find some stuff.  but for a brief example, here's my file:```
auto lo
iface lo inet loopback     #this is the loopback, for when you connect to "localhost" or 127.0.0.1

auto eth0                 #this section is for the wired connection, you'll need to add it after you uninstall network-manager if you want a wired connection
iface eth0 inet dhcp

#auto wlan0       #this section is the wifi, note that it is commented out because I'm not currently using it, remove the '#' in front of it to make it active
#iface wlan0 inet dhcp
#       pre-up ifconfig wlan0 up
#       pre-up iwconfig wlan0 essid <your essid>
#       pre-up iwconfig wlan0 key <your hex wep key, if you don't have one, you don't need this line>

```Hope this helps point you somewhere vaguely in the right direction

Also, if you get it working, but are having issues with your wireless encryption, you might want to [leave it open]("http://www.wired.com/politics/security/commentary/securitymatters/2008/01/securitymatters_0110").

---

### Post by rowinggolfer on 2008-01-25
Hi David,

I'm having the exact same issue (bought this model yesterday)

What is VERY odd here, is that the wireless functionality on this laptop works absolutely great with the Live CD!! I was very careful to check this in the store!

I've also had it working from my dual boot vista/ubuntu set-up.... but only intermittantly. 
Sometimes i get no wireless functionalty at all, other times it finds networks, but can't get connected.

I think there is an issue with the way the device is configured in the PCs BIOS, in particular the power management of the device.

Try booting back into Vista... and find a setting which allows windows to turn the device on/off.

If I get a definate fix I'll post it here.

Neil.

---

### Post by RedStar1916 on 2008-01-25
Having only bought the model yesterday, I'm still on the pre-installed Vista package so I can't try anything myself, but I found this:
> Anyway, this is a consumer information post for those considering one of those. As Ubuntu is our standard distro nowadays, Gutsy was what we tried. Basically, everything worked out of the box (although it took us a good while to figure out that we had to enable the built in camera with a Fn-sequence).

In spite of what is said on the tech guys page, the wlan card didn't seem to be a Intel card but a realtek one (**the rt73usb driver was used**). We noticed network issues after hibernation sometimes but didn't care enough to examine those.

[http://blog.freyhult.net/2008/01/linux-on-advent-9112.html](http://blog.freyhult.net/2008/01/linux-on-advent-9112.html)


Also regarding detection of the wireless card, did you remember to turn it on at the bottom of the laptop? There's a switch just beneath the power light...

Brilliant buy though, isn't it? Don't think I've ever seen such good specs for so cheap.

---

### Post by rowinggolfer on 2008-01-26
Hi guys,

I've fixed it!

What I really couldn't understand was how the wireless card worked "out-of-the-box" with an Ubuntu 7.10 Live CD, but failed once the distro was installed to the hard drive.

I compared the dmesg files from both, and what jumped out at me was that 2 kernel modules were loaded in a different order.

on the live CD... order was rt73usb then rt2500usb.
on the installation ..... other way around.

So, I manually removed both, then re-installed in the correct version.

To try the same, open a terminal and type.

sudo rmmod rt2500usb
sudo rmmod rt73usb
sudo modprobe rt73usb
sudo modprobe rt2500usb.

(rmmod removes modules/dependencies.... and modprobe manually installs them)

A great laptop now this major irritation is removed.

Note - the switch which turns wireless on/off  doesn't work... it's always on. That's the next thing I'm going to investigate.

Neil.

---

### Post by david_stott on 2008-01-27
Hello again- thanks for all your replies
been busy so I've only just got round to trying to sort it again today. It is indeed a great laptop for the money!

Neil- I tried what you suggested in terminal but it doesn't seem to work-it says there is no rt2500 driver.

also when I boot up Ubuntu it comes up with an error in in the kernel regarding a PCI device - it flashes up so fast I cant read it properly- suspect it might be something to do with the wireless card. Guess I'll try and see if I can find it in the system log.

Will keep youz posted

---

### Post by rowinggolfer on 2008-01-27
David,
sorry to hear that the fix didn't work for you.

this isn't a PCI issue though... I wouldn't worry about those messages, I think they simply relate to unused PCI slots.

One other thing you may want to try is booting into windows, and unchecking the option which allows windows to switch the device off for power saving reasons.

If this still doesn't work, then could you save your dmesg output and post it here? I'm very interested to see what modules are being loaded.

BTW - I hope this isn't patronising, but the best way to save terminal output from a cript such as dmesg is to use the ">" function in the terminal. This will output to a file in the current directory.

So type
"dmesg > dmesg_output.txt" 
in a terminal (without the quotes), then cut and paste your output here.

Neil.
p.s. yes, it is a good laptop for the money. I'm really disappointed with the battery life though. I'm only getting 90minutes... crap for such a small machine. And I can source a spare battery!
p.p.s. Webcam very good quality... I'm using it with "cheese"

---

### Post by david_stott on 2008-01-27
Hi again!
Got it to connect! Progress! Now the only problem is it is running really slowly..... It takes a good couple of minutes to bring up Google. Is this still a driver problem or something else now?

Neil- I am disappointed with the battery life too- I get longer in ubuntu but in windows it only lasts a bit longer than an hour with the most drastic of power management settings. A bit annoying when most of my work happens in a muddy field away from a power outlet. Did you say you can source a spare battery? Where? 

Thanks,

David

---

### Post by nspur on 2008-01-27
Neil

Your solution just worked fine for me with a new Advent 9912 (the baby brother to the 9112 which I bought to test some of my software under Vista). Thanks very much. Been banging  my head against the wall trying to figure it out.

Now to see if I can get access to the Windows network and the printer which I successfsully did from the live CD.

Thanks again

Nick

---

### Post by rowinggolfer on 2008-01-28
Guys,

I posted my findings further up the food chain, and I was informed (very succintly!) that unless I have two cards, I only need one module. Turns out for this machine the rt73usb is the one we need.

So I experimented a few times, and here is the permanent fix (survives a reboot too).

open a terminal
$sudo gedit /etc/modprobe.d/blacklist

then add this line at the bottom of the file.

rt2500usb

Save the file..... reboot and you're done.

BTW - battery life - I've ordered an external battery - should be good for my 9 hour flight to Vancouver next week.

---

### Post by GrahamJ on 2008-01-31
> **rowinggolfer said:**
> Guys,



BTW - battery life - I've ordered an external battery - should be good for my 9 hour flight to Vancouver next week.



Rowinggolfer

Where did you get one of these batterys? Cannie find anywhere. Managed to turn off enough services to manage an hour and 45 out of it but mroe would be ideal


And thanks all for the wireless tips. Tried but failed so gave up, this should do it...

---

### Post by rowinggolfer on 2008-01-31
Hi Graham,

There's a rake of them on Amazon.
The one I've got is a tad expensive.... but fits perfectly underneath the 9112, and has a massive capacity.
here's a link
[http://www.amazon.co.uk/2-Power-Universal-External-Longlife-Battery/dp/B000EBDBGU/ref=sr_1_1?ie=UTF8&s=gateway&qid=1201785575&sr=8-1](http://www.amazon.co.uk/2-Power-Universal-External-Longlife-Battery/dp/B000EBDBGU/ref=sr_1_1?ie=UTF8&s=gateway&qid=1201785575&sr=8-1)

Cheers

Neil.

---

### Post by rowinggolfer on 2008-01-31
whoops,
amazon link too long...

try this
[http://tinyurl.com/ys5qhu](http://tinyurl.com/ys5qhu)


BACK-ON-TOPIC.
this wireless card does seem a little temperamental under Ubuntu 7.10. Mine stopped working again (after 3 days of faultless performance).

I went back into Vista, and found it wasn't working there either! 
Whilst I was there though, I decided that I may as well check the windows driver for this device is up to date... mine wasn't. So I updated it.

I can confirm though that all is working again i Ubuntu with the blacklisting of the rt2500usb driver

So here are my recommended things for you to try if you are having issues.

1. get it working it windows.
2. blacklist the rt2500usb driver if it is mentioned when you run " lsmod" in a terminal.
If you still need to do this, open a terminal and type....

you@you-machine:#$ sudo gedit /etc/modprobe.d/blacklist

then add the following 2 lines to the bottom of the file.

# this is simply a comment line - put what you wish here
blacklist rt2500usb

save it, and reboot.

good luck.

---

### Post by GrahamJ on 2008-02-01
Thank you Rowinggolfer, 

On both accounts, I noticed my wireless was flakey last night, more so when you flick the switch to turn it off then back on again... In fact that just made matters worse!

Shall give that a bash, 

Cheers

---

### Post by rowinggolfer on 2008-02-01
yes, be VERY wary of that switch, espescially if you boot into windows.

It is not a hardware switch (i.e. it doesn't directly control the power to the radio devices), but a software one.

and it is not currently supported in Linux.

More info on sourceforge, 

[http://rfswitch.sourceforge.net/](http://rfswitch.sourceforge.net/) 

Neil.

---

### Post by wildcard58th on 2008-02-05
I tried the blacklisting and the compiling of the rt73usb.ko module - neither worked for me. 

What does work (well at time of writing I've put a couple of 700mb plus files through the wireless) is using the Hardy Heron kernel and related Ubuntu kernel modules.

1 Simply download the following packages from [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

linux-image-2.6.24-5-386_2.6.24-5.8_i386.deb
linux-restricted-modules-2.6.24-5-386_2.6.24.6-5.16_i386.deb
linux-restricted-modules-common_2.6.24.6-5.16_all.deb
linux-ubuntu-modules-2.6.24-5-386_2.6.24-5.9_i386.deb

* note that Hardy Heron is still in development and as such the kernel updates are likely to be frequent. I'm using the one listed above and its working. Can't vouch for any other kernel build.

2. Put the files in a folder - e.g. ~/Desktop/files/
3. Open a terminal - Applications -> Accessories -> Terminal
4.type  'sudo dpkg -i Desktop/files/*.deb '
   (assuming you put the files in the folder in [2])
5. Restart using the 2.6.24-5 kernel

I had a quick look at the rt73usb.ko file itself and the latest Gutsy kernel module is a bout 0.2 KB smaller than the Hardy Heron one.

---

### Post by rowinggolfer on 2008-02-14
As I've posted here before, I've got the wireless card to work well by blacklisting the rt2500usb module. (no need to upgrade the kernel on my machine.........)

The wireless works well enough to stream mythtv from my local server. We watched over two hours in this way yesterday with no problems. I guess that's a high bandwidth.

However, that is with the laptop running on external power.
On battery, I get disconnections, often requiring a reboot to fix!

Has anyone else found that the wireless functionality is better when on AC?

Neil.

---

### Post by rowinggolfer on 2008-04-25
Just a quick note to say that Ubuntu release 8.04 works perfectly with this laptop.

I used the graphical distribution tool to upgrade from 7.10, and it spotted my modified /etc/init.d/blacklist file (where I had blacklisted rt2500usb).

I clicked on "replace modified file with newer version" and the laptop is singing along.

(Incidentally I am using the WICD network manager rather than the standard gnome one... but that's largely irrelevant I think).

BTW - one thing of interest - if I perform lsmod the rt2500 module is in there now... but I'm more than happy to leave it there.

BTW2 - Hardy is fantastic on this laptop. Doesn't need any proprietary drivers, and supports full desktop effects etc...

Neil.

---

