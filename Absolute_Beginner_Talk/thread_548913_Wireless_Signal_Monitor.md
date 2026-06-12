---
title: "Wireless Signal Monitor"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-09-11
I'm looking for a program that sits beside the time and shows Wireless signal strength
such as the one that came with Ubuntu 5.10 long ago.

Anyone know of a good one.

---

### Post by jimrz on 2007-09-11
> **Orbital75 said:**
> I'm looking for a program that sits beside the time and shows Wireless signal strength
such as the one that came with Ubuntu 5.10 long ago.

Anyone know of a good one.

that is the network-manager applet and it should be there by default in feisty. on the panel, go to System > Preferences > Sessions > the "Startup Programs" tab and make sure that "Network Manager" is there and that it's box is has a check mark in it.

---

### Post by Orbital75 on 2007-09-11
Ah,  I am using Xubuntu 6.06 LTS, Can I do as you said with this version?
If not how do I get it up and running.

Thanks for your help..... :-)

---

### Post by jimrz on 2007-09-12
> **Orbital75 said:**
> Ah,  I am using Xubuntu 6.06 LTS, Can I do as you said with this version?
If not how do I get it up and running.

Thanks for your help..... :-)
you can install network-manager + network-manager-gnome via Synaptic OR
```
sudo apt-get update
sudo apt-get install network-manager network-manager-gnome
```
and after install, I think, that you will need to manually add the nm-applet to your Startup Programs.
Though these are gnome apps they work, or at least did under dapper which is the last time I ran a Xubuntu install, fine with Xubuntu without adding a great deal of additional overhead.

---

### Post by Orbital75 on 2007-09-12
Thanks for the tip.... I went into synaptic and install both network-manager and 
network-manager-gnome.

Sorry to do this but I'm a newbie and don't know how to put them in start up,
or even to run them.  Nothing was put in my menu as you said would be
expected.

Also, do I need to back anything up, could this cause damage to
anything?

If you could show me the command, that would be great....

Thank you for your help.....  I'm really learning a lot about linux.
It's about time I kicked windows to the side. :KS

---

### Post by jimrz on 2007-09-12
been a while since I used xubuntu not sure where to do, but think I might have a live cd around here somewhere to check it out and post back

---

### Post by swoll1980 on 2007-09-12
try sudo network-manager in terminal

---

### Post by jimrz on 2007-09-12
> **jimrz said:**
> been a while since I used xubuntu not sure where to do, but think I might have a live cd around here somewhere to check it out and post back

ok, found it

to add to start up, right click on your desktop, go to Settings Autostart Applications, click "Add", enter the following:
name= "network applet"
command= ```
nm-applet --sm-disable &
```

then since network-manager in 6.06 only works with interfaces NOT listed in your current networking conf, go to terminal and do
```
sudo cp /etc/network/interfaces /etc/network/interfaces-original
```
this backs up your current conf...always a good idea, then
```
sudo mousepad /etc/network/interfaces
```
then comment out (by putting a #  at the beginning of each line) each line of all sections EXCEPT this one ```
auto lo
iface lo inet loopback
```
then restart and you should see the applet on your top panel

if you get into it and decide to stay with ubuntu, I would recommend that you download and install feisty 7.04 ( or maybe wait about a month or so and move to gutsy 7.10) 
when you get a bit more comfortable and familiar with ubuntu, as 7.04 really does have many improvements over and above 6.06

---

### Post by Orbital75 on 2007-09-13
Thanks so much for the command text....  I'm going to try that out in a bit.
As far as upgrading, Not sure that is possible.  The Laptop I have is an old
1998 AMD 400Mhz with 192 megs. This is an old PC I had long ago and had
seen better days.  I figured it would be a perfect candidate for Xubuntu.
I had a good bit of trouble getting linux on it but finally got her up and running.
I had to use the 6.06 Alternative CD, that's the only version that would install.

I am currently using Ubuntu 7.04 on my Desktop so I am sorta familiar with
Linux.  I'm a newbie hopping to convert sometime soon. Currently I'm running
Ubuntu in Virtual Box on a Windows XP Pro machine that I built a few years
ago.

Thanks again for the help !!!!  :KS

---

### Post by jimrz on 2007-09-13
no prob

I,too, have an old laptop running ubuntu. ThinkPad 600x - PIII 500 Mhz 384 Mb ram - that used to run Xubuntu but with feisty is able to handle gnome pretty nicely. So I think that, with the specs on yours, that Xubuntu is the choice but that you might see a nice performance gain by moving to 7.04

---

### Post by Orbital75 on 2007-09-13
Ah, really? I figured that an upgrade would slow it down.
Should I hit the upgrade button to upgrade to 6.10 in Synaptic 
then once it shows 7.04 upgrade to it?

I tried the 6.10 and 7.04 LiveCD but they wouldn't install.
Is this a bad sign?

Just curious, I've never preformed an upgrade before.

---

### Post by Orbital75 on 2007-09-14
Thanks again for the Command line Text......

Before I implement this I'd like to know a few things.

1.  Is this going to do anything to my normal Wireless SetUp?  What I mean by this is 
When I want to change anything such as the SSID or WEP key, I go into  Network and choose 
my Wireless card then hit edit or something.  Is this going to change the program I am
using for my Network setup settings.

2.  Is there a risk that this may break my internet connection and make my card not work?
If something does go wrong, since you showed me how to back it up, how do I restore it.
Is this a guarantee it will work after the restore if something goes wrong.

3. Anyone have a Screenshot of what it looks like?

---

### Post by Orbital75 on 2007-09-14
Bump  :KS

Just want to make sure I have all the facts before I implement. Thanks

---

### Post by Orbital75 on 2007-09-15
can anyone verify that this works for me.  I went half way throught the process
and it puts a generic icon up near my time.  What is it supposed to look like.
I thought it would be a small vertial line with a progression of bars and when
you doubled clicked, it would show a large horizontal bar showing strength.

---

### Post by dustigroove on 2007-09-15
[FONT=Arial][SIZE=2][COLOR=Black]You should see something similar to [this]("http://www.gnome.org/projects/NetworkManager/images/wireless-at-tealuxe.png").

.
[/COLOR][/SIZE][/FONT]

---

### Post by Orbital75 on 2007-09-15
dustigroove...

Thanks..... Well with the directions above,  
How do I get the bar icon beside the time.
It's just a gear looking like thing, do I have to choose it?
Once I got to that point I stopped because I didn't think I
could get it to work......

When I install Network-Manager and the gnome Applet,
why didn't it install it for me?

Just curious..... Seem like the OS would have put this in
my system tray during installation. does Xubuntu not do this?

---

### Post by dustigroove on 2007-09-17
> **Orbital75 said:**
> Seem like the OS would have put this in
my system tray during installation. does Xubuntu not do this?

Unfortunately my friend I will be of very little value answering that question as I'm not at all familiar with XFCE's workings for applets.

Any other Xubuntu users out there that can help Orbital?

.

---

### Post by Orbital75 on 2007-09-17
Well, I followed the command line directions to a certain point but
I went to "Autostart Applications" under the settings menu
and added "network applet".  Now when I start the PC
everything works fine and I have an icon of a computer
beside my time with an exclamation point ontop of it.
However my internet still works. I'm thinking it's
because I didn't comment out anything in my 
/etc/network/interfaces 

I'm really scared to put # signs infront of my 

# The primary network interface
auto eth0
iface eth0 inet static

Below this is all my settings.
What will happen if I comment these lines?
I am thinking it will break my network

---

### Post by dustigroove on 2007-09-17
[FONT=Arial][SIZE=2][COLOR=Black]It may temporarily nick your network until you get NetworkManager connected, but you can always remove the commenting (#'s) and it will be back to normal.
[/COLOR][/SIZE][/FONT]

---

### Post by Orbital75 on 2007-09-18
Are you sure.... I thought it would reconfigure everything.
I don't think taking the # signs off will fix it back.

---

### Post by Orbital75 on 2007-09-20
Well, I went ahead and commented out the information in the Interface file
and rebooted.  The Network Manager apeard in my system tray just as I expected
and saw a few Wireless access points. It didn't list mine because I have my
network set not to transmit SSID. So I double clicked on the network manager
applet and choose connect to another wireless network.  A box came up and
aksed me to fill out some info about the network I want to connect to.  Well,
I filled out My Networks Name (SSID) then picked the encrytion type and
cut and pasted my key into the box.  Well, it won't connect.  I'm thinking
it's because there is no where to fill in a Static IP and Network. With
the default connection manager, it had me fill all this out IP, Network, DNS.
See I have all my PC's setup with Static IP's and I have turned off DHCP on
my router.  Could this be the issue?

---

### Post by Orbital75 on 2007-09-20
Is there no GUI I can use to enter in a static IP, subnet, and DNS?

---

