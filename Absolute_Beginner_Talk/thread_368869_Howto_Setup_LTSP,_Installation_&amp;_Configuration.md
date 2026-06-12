---
title: "Howto: Setup LTSP, Installation &amp; Configuration"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by saadakhtar on 2007-02-23
**i am using an example ip i.e. 10.30.2.20 for the LTSP server. Please modify as necessary**

[B]Introduction
[/B]
MueKow is a new concept LTSP client that on Ubuntu uses Ubuntu's own package system to build the client image, previously custom builds of all the components were used.


I assume that you have installed and configured your ubuntu server appropriately.

[B]Install LTSP Server
[/B]
The LTSP server package includes the tools necessary to construct a MueKow image.
Install the ltsp-server package and start to build the client.

$ sudo apt-get install ltsp-server
$ sudo ltsp-build-client

If this process ends prematurely because all the packages cannot be downloaded delete the entire LTSP directory and restart. (Ensure debootstrap >= 0.3.3.0ubuntu7: see dapper-backports repository in sources.list below).

$ sudo rm -rf /opt/ltsp/i386  
$ sudo ltsp-build-client

At the end it should look similar to this.

[B]Cleaning up startup links in rcS.d ...
Cleaning up startup links in init levels: 2 3 4 5 ...
 * Re-exporting directories for NFS kernel daemon...                                                            [ ok ]
Removing `local diversion of /sbin/start-stop-daemon to /sbin/start-stop-daemon.distrib'
[/B]

[B]Update MueKow
[/B]
Edit the apt configuration in MueKow and ensure the update repositories are enabled, /opt/ltsp/i386/etc/apt/sources.list

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

Then synchronise upstream.

$ sudo chroot /opt/ltsp/i386/ apt-get update
$ sudo chroot /opt/ltsp/i386/ apt-get upgrade
$ sudo chroot /opt/ltsp/i386/ apt-get dist-upgrade


[B]Setup SSH
[/B]

To reduce network bandwidth used by X11 all traffic is tunneled through ssh, this proves remarkably effective compared to NX compression. In order for the LTSP clients to access the server the server needs to have its IP address configured and available for SSH. Edit /etc/hosts and if you have a host line 127.0.1.1 change to the LTSP server IP address.

10.30.2.20 ubuntu.example.org ubuntu

If you update the hostname also update the /etc/hostname configuration file and update the environment.

$ sudo sh -c "echo ubuntu.example.org > /etc/hostname"
$ sudo hostname ubuntu.example.org

If you changed the hosts file you will also need to update the LTSP client with the new ssh keys, these are encryption keys used to verify the remote host of a ssh connection is who it is supposed to be, i.e. not another host with the same IP address.

$ sudo ltsp-update-sshkeys


[B]Configure LTSP Clients
[/B]

The configure file /opt/ltsp/i386/etc/lts.conf contains a list of X11 and LTSP configuration options that can be specified for individual or groups of machines. This can include X11 servers, mice, keyboards, attached devices, etc. The minimum configuration is the SERVER address, here we drop down to high colour graphics to improve performance a bit.

[B][Default]
# LTSP server IP address
#SERVER                 = server
SERVER                  = 10.30.2.20

## Network syslog
#SYSLOG_HOST            = server

## X11 driver, e.g. auto, vesa, i810
#XSERVER                 = auto
#X_COLOR_DEPTH           = ""
X_COLOR_DEPTH           = 16
#XF86CONFIG_FILE        = ""

## Keyboard configuration
#XKBLAYOUT              = us
#XKMODEL                        = pc105
#XKBRULES               = xorg
#XKBOPTIONS             = lv3:ralt_switch
#XKBVARIANT             = ""
#CONSOLE_KEYMAP         = ""

## Mouse configuration
#X_MOUSE_DEVICE          = /dev/input/mice
#X_MOUSE_PROTOCOL        = auto
#X_MOUSE_EMULATE3BTN    = True

## X11 font server
#USE_XFS                 = False
#XFS_SERVER             = server

## SSH compression between LTSP client and server
#NETWORK_COMPRESSION     = False

## Network swap device for clients < 48 MB system memory
#NBD_SWAP                = ""
#SWAP_SERVER            = server
#NBD_PORT               = 9572

## Local printers
#PRINTER_0_DEVICE       = ""

## Sound configuration
#SOUND                   = False
#SOUND_DAEMON            = esd

## Terminal sessions
#SCREEN_07              = ldm

## Linux modules
#MODULE_01              = ""

## Custom startup scripts
#RCFILE_01              = ""
#LDM_REMOTECMD          = ""
[/B]

---

### Post by s4s on 2007-03-18
Thanks for posting this howto.

I tried to follow this HowTo. When I booted a client thru pxe, it did not get an ip address and was not presented with a login screen.

What more do I have to do? 

Hoping for your assistance.

s4s

---

### Post by saadakhtar on 2007-03-23
sorry abt the late reply.
i have been working on this project too.
tried it but same for me.
how ever i took some help from this howto and got it to work.
[https://help.ubuntu.com/community/ThinClientHowto](https://help.ubuntu.com/community/ThinClientHowto)

try this and let me know if you need any more help. cuz after fooling around with the whole idea of ltsp i have come to figure out a lot of tweaks and stuff.

---

### Post by s4s on 2007-03-28
It seems that ltsp setup in ubuntu is not yet so straightforward.

Am trying edubuntu and work my way to replace edubuntu artwork with that of ubuntu. 
The ubuntu artwork is preferred since ltsp is installed in a government agency.

I am just wondering why the ltsp setup in ubuntu is not included in the installation cd just like that of edubuntu and xubuntu.

thanks a lor for your reply.

---

### Post by iMav on 2007-03-28
Are [these directions](https://help.ubuntu.com/community/ThinClientHowto) still relevant?  (for an Edgy install, that is)

---

### Post by saadakhtar on 2007-03-28
actually, the instructions that i have put together are not really something that would get ltsp up and running. this is merely some help with configurations. the only way i got my setup to work was by setting up dedicated edubuntu server.
i am going to be setting up ltsp on a 6.10 or the known "edgy" server in the next few days will post all steps and configs in detail.
so please check back.

---

### Post by shagpile on 2007-04-01
Would be better to be honest if you started from scratch using the new Feisty server.

It says it has all you need and the fact that it has the latest version of LTSP built in as well as a few funky tweaks is really interesting.

Besides, its beta now. Not alpha so it should still work perfectly. Besides, these things take a while to set up propperly and most people reading this would want to get the latest version because it will be current by the time it works.


The thing is, although it claims to have everything already there and ready to use. Its not exactly just going to boot a thin client into a command line....... is it?

A really good how-to is required.

---

### Post by tentwelveeight on 2007-04-03
I agree, I have been trying to set up an edubuntu LTSP for over a month now and can't even get a thin client to boot up at all. My situation is a little different because I'm an educator at a school and we have a mother network assigning all the IPs and I can't access the hardware on that network, but from what I'm told I should still be able to setup some LTSP servers in classrooms and run thin clients off of them. I'm not sure what I'm doing wrong.

The how-to will need to be VERY detailed though. I'm just learning, but I don't even know what to put as the server IP address when prompted as I have two cards (eth0 and eth1) on the server and they both have different IP addresses. Of course we are also on a NAT system at school so our IP address to the Internet is different as well. All of this will need to be very clear in an adequate how-to. Of course, if it was done correctly, it would open the door to tech-novice educators and thus a new generation of school children learning linux, something I'm sure we're all anxious to see happen. -joe

---

### Post by tentwelveeight on 2007-04-03
Okay, I finally got it to work! I think my problem was the computer I was using for the server because I set up a different computer as the server and it fired right up! No problems, just like I've been reading it should be! I still think a really clean how-to would be useful, but I'm so impressed now whereas 60 minutes ago I was ready to shoot myself in the face. Cheers! -joe

---

### Post by saadakhtar on 2007-04-05
for me, the edubuntu server booted my clients no problem. All i had to do was make sure which eth card was doing what and setup the eth card that would be used for pxe boot to have the same gateway and dns addresses as the eth card  # 2.
For edubuntu i would certainly suggest that you should have two network adapters available and a minimum of 550 Mhz with atleast 128 MB of ram. Atleast thats what i used. But how they say the more sugar u put in the sweeter its gonna be. So a faster terminal server means more fast and functional clients.
it is possible in ubuntu but needs a little work. you have read a lot for it.

---

### Post by derekagar on 2007-04-05
What about a web based manager such as the symbio workstation manager?
[http://www.thesymbiont.com/index.php?option=com_content&task=blogcategory&id=90&Itemid=116]("http://www.thesymbiont.com/index.php?option=com_content&task=blogcategory&id=90&Itemid=116")
I found this in an older issue of Linux Mag.
[http://www.linux-mag.com/id/1973]("http://www.linux-mag.com/id/1973")

I would think that this would greatly ease the pain.

---

### Post by butters on 2007-04-09
The urge to turn an Apple TV into an LTSP client is unbearable.

---

### Post by amac777 on 2007-04-10
I tried setting up a simple LTSP server using Feisty and it *almost* worked. 

I used the quick install method from here (the first one on the list):

[https://help.ubuntu.com/community/UbuntuLTSP](https://help.ubuntu.com/community/UbuntuLTSP)

I'm just trying to do this at home to use an old Pentium 3 for websurfing and general usage by someone else when I am using the main computer (which is my LTSP server).

Those instructions almost worked perfectly. I saw the graphical login screen on the thin client, I could login, I even heard the ubuntu welcome sound when the desktop loads (but sound in firefox at youtube did not work)...

But what didn't work and what I am confused about is that logging into the thin client seems to have messed up my account when I then go back and login to the server. I'm wondering whether we are supposed to make a new user for when logging in from the thin client or if I can login using my main user that I made during the install of Feisty. (Ie, use the same user account on both the client and the server.)

I tried using the same account at first because I didn't even think about this issue and I can login and see my regular desktop ok on the thin client and I was amazed and happy. But from that point on, when I login using that user on the server I don't get the welcome sound when the desktop is loading, don't get sound from certain programs like the game tremulous, and I if I click the upper right hand button to see the logout/turn off the computer menu then X freezes and I must CTLR-ALT-BACKSPACE. This only happens when I am using the server.

I guess this is due to some settings in my home directory getting changed when I login with that user on the thin client.

To test that, I made a new user on the server and it works fine from the server (sound works and logout menu works great like normal). But once I login using this user on the thin client then I have the same problems with sound and X freezing when I use this user on the server again.

So it seems like the user accounts that are used on the thin client should be kept separate from the accounts that are used on the server and everything will be fine. I'm just wondering why. Seems a little inconvenient to have to use two different accounts.

Anyone have any experience or suggestions for using the ltsp setup on feisty?

---

### Post by didijeeeke on 2007-04-10
do i need the ubuntu-desktop installed on the ubuntu server ?

sry if this is a dumm question

---

### Post by amac777 on 2007-04-10
Just a quick update about that sound problem I was having above. 

By deleting these files in your home directory upon login from the server everything is fine. I put this into the beginning of the PreSession scripts for gdm.

sudo vi /etc/gdm/PreSession/Default

add these lines at the top:

rm /home/$USER/.asoundrc
rm /home/$USER/.asoundrc.asoundconf
rm /home/$USER/.pulse-cookie

That fixes everything on my system and I can now login using the same accounts on either the thin client or the server.

---

### Post by s4s on 2007-11-15
am still using edubuntu 6.10 for ltsp with several thin clients. my info is that logging to 2 or more pcs with the same username is unsupported and may cause problems. i'll be trying shortly edubuntu server 7.10 and see if this issue still persists.

---

