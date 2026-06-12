---
title: "Problems connecting to secure network (UT Austin)"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by Th3sandm4n on 2007-09-12
I read through the instructions located here: [https://management.pna.utexas.edu/static/faqs/dot1x/dot1x-linux.html](https://management.pna.utexas.edu/static/faqs/dot1x/dot1x-linux.html)

and followed it to the dot. But once I get to running, well, i can't. I'm pretty new to Linux so it sucks that they intro this right when I decide to try it out :(
Anyways, heres what I have done in the console:

**NAVIGATION**:
frank@franks-Latop:~$ /usr/local/sbin/wpa_supplicant -Bw -Dipw -iath0 -c/etc/wpa/config
bash: frank@franks-Latop:/usr/local/sbin: No such file or directory

how I have to get there:
frank@franks-Latop:~$ cd ..
frank@franks-Latop:/home$ cd ..
frank@franks-Latop:/$ cd usr
frank@franks-Latop:/usr$ cd local
frank@franks-Latop:/usr/local$ cd sbin
frank@franks-Latop:/usr/local/sbin

I think it might have something with the way I am trying to run it, because it doesn't seem to be getting to the wpa supplicant using "/usr/local/sbin/wpa_supplicant" straight up. 
I tried using $/usr/local/sbin/wpa_supplicant, but still nada. I'm just not sure how to access there without physically DOING it. This might be the entire problem, but heres more:

[B]
USAGE[/B]:(of the WPA_Supplicant
usage:
  wpa_supplicant [-BddehLqqvwW] [-P<pid file>] [-g<global ctrl>] \
        -i<ifname> -c<config file> [-C<ctrl>] [-D<driver>] [-p<driver_param>] \
        [-N -i<ifname> -c<conf> [-C<ctrl>] [-D<driver>] [-p<driver_param>] ...]

drivers:
  hostap = Host AP driver (Intersil Prism2/2.5/3)
  atmel = ATMEL AT76C5XXx (USB, PCMCIA)
  wext = Linux wireless extensions (generic)
  ipw = Intel ipw2100/2200 driver **The driver I am using(I have this wireless card)**
  wired = wpa_supplicant wired Ethernet driver
options:
  -B = run daemon in the background
  -c = Configuration file
  -C = ctrl_interface parameter (only used if -c is not)
  -i = interface name
  -d = increase debugging verbosity (-dd even more)
  -D = driver name
  -g = global ctrl_interface
  -K = include keys (passwords, etc.) in debug output
  -t = include timestamp in debug messages
  -h = show this help text
  -L = show license (GPL and BSD)
  -p = driver parameters
  -P = PID file
  -q = decrease debugging verbosity (-qq even less)
  -v = show version
  -w = wait for interface to be added, if needed
  -W = wait for a control interface monitor before starting
  -N = start describing new interface

**WHAT I RUN**:
frank@franks-Latop:/usr/local/sbin$ wpa_supplicant -B -Dipw -iath0 -c/etc/wpa/config
ioctl[SIOCSIWPMKSA]: Operation not permitted
ioctl[SIOCSIWMODE]: Operation not permitted
Could not configure driver to use managed mode
ioctl[SIOCGIFFLAGS]: No such device
Could not set interface 'ath0' UP
ioctl[SIOCGIWRANGE]: No such device
socket(PF_PACKET): Operation not permitted
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not permitted
Failed to set encryption.
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not permitted
Failed to set encryption.
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not permitted
Failed to set encryption.
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not permitted
Failed to set encryption.
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not permitted
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not permitted
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not permitted
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not permitted
ioctl[SIOCSIWAP]: Operation not permitted
ioctl[SIOCGIFFLAGS]: No such device

I'm not too sure exactly what the interface "ath0" is, but it was in the example on the site.






I hope this is semi organized :)

---

### Post by hyper_ch on 2007-09-12
WPA Supplicant is in the repos:

[http://packages.ubuntu.com/feisty/net/wpasupplicant](http://packages.ubuntu.com/feisty/net/wpasupplicant)

no need to compile it yourself.

---

### Post by Th3sandm4n on 2007-09-12
i said i was new, so I just wanted to follow instructuions first, but ok I installed the lates via synaptics, buuuut now I am in the dark, do I do anything different?

---

### Post by hyper_ch on 2007-09-12
just follow what they say except for the "install wpa supplicant" section.

---

### Post by Th3sandm4n on 2007-09-12
Ya that's what I did. But my problem here was the **Running wpa_supplement**.
I included(in my original post) what happens when I try running it, along with some commentary on other stuff.
       Such as how I think the path I am using is wrong, but I don't know how to point there without being in there =/

I set up the cert fine, and configured the wpa_supplicant, it's just running it that I'm having difficulties with.

Thanks for the responses so far though. :)

---

### Post by Th3sandm4n on 2007-09-13
I'm just bumping this because this is my only resource for help. The ITS told me to come here for help because they didn't have the resources regarding linux :(

---

### Post by Nulifier on 2007-09-13
As far as I understand WPA_supplicant is installed by default but I can't test this as I only have gutsy now.

But you do not need to do the installing section of your walkthrough as all you need is:

sudo apt-get install wpa_supplicant

and that should work (or look for it in synaptic if it says package not found)

but anyways you should not need to do most of this as Network-Manager should be there just try connecting through that

Heres how I think you should do it using my version of Network Manager:

Click on the applet in the toolbar
Press connect to other wireless network
a window will pop up.
In Network Name type: restricted.utexas.edu
For wireless security go to WPA2 Enterprise

Now select these settings:
EAP Method: TTLS (PEAP may work differently bu they sugest TTLS)
Leave key type alone
Phase2 Type: MSCHAPV2
Identity: is your UT EID (your university gives you this)
Password: see above
Anonymous Identity: Anonymous (don't know why you need this)
CA Certificate File is the one that they give you on the page

this should log you on properly and everything should work.

The problem with being in linux is that there are many distros which don't use things like WPA and NM by default and so you get these walkthroughs that are unessisarily complex and actually break things on a properly configured one.

This is all assuming that you have NM installed by default and that it works and that all the messing about didn't break it

If you do not have Network-Manager jsut install it and Network-Manager-gnome too

I hope this helps and if it makes you feel better this all should be automatic unlike mine which requires a ssh session each time you connect

---

### Post by Th3sandm4n on 2007-09-13
thanks I'll give it a try tomorrow when I'm back on campus :)

I'm assuming the other options I just leave as is?

And also, I didn't have an option for Phase2 Type. But thanks, this way seems alot more easy.

---

### Post by llamakc on 2007-09-13
You questioned about the path: when you install wpa_supplicant from Synaptic, the path to THAT binary is different, and is already in your path. You do not need to type the whole path to it.

You can see which ones are in your path with the command in a console or terminal:

which wpa_supplicant

---

### Post by Nulifier on 2007-09-13
The phase2 type did seem pretty important in the walkthrough but if it works then good luck
you may try updateing the NM

---

### Post by Th3sandm4n on 2007-09-14
thanks llamakc  , useful lil command :)

And Nulifier, I have the latest version(0.6.4-6ubuntu7) so i dunno exactly. Do you have the Phase2 option in yours? Either way, time will tell manana :) Thanks again.

---

### Post by Nulifier on 2007-09-14
I am only running Gutsy (pre-release) but I am using the Gutsy repos so if it doesn't work for you then the feature is in Gutsy which is due out sometime in October or you could try to get the updated version (0.6.5-ubuntu11).

the source can be gotten [here]("http://ftp.gnome.org/pub/GNOME/sources/NetworkManager/0.6/") if you need it you will need to compile it and I recommend searching for how to compile on this forum

---

### Post by Th3sandm4n on 2007-09-17
Thanks Null, those settings worked :)

Yay for browsing stuff in class now!!

---

### Post by Nulifier on 2007-09-17
Glad to hear it!!!

and there are numerous updates to Network Manager in Gutsy so I discovered one of which is better WPA

---

### Post by nraney on 2007-10-09
ITS told me the same thing, one of the largest public schools in the country and there is zero support for Linux.  Anyone here from Utexas? The restricted network does some weird things to me.  for example; in certain classrooms the connection stays but the internet doesnt work.  other times the connection doesnt work at all, regardless of me using the right settings and it working only moments before.  Sometimes the gnome-network manager doesnt work at all and says there are no available networks (while im on campus which is absurd).

whats going on.. it could be an issue with my machine i suppose?  If so what?  anyone else with ubuntu experiencing these difficulties on UT campus?

---

### Post by Th3sandm4n on 2007-10-09
what buildings are you getting no connection. I know some buildings get no wireless, I'm thinking it was Geo but I can't remeber honestly. I usually only use it around the FAC or the library where I know it has wireless.

I do have the problem with sometimes connecting when coming out of hibernate(it just doesn't connect). But it solves with a restart. The only thing I hate is having to type in my info all the time(I'm not to keen on scripting things), but as long as it's working its good.

But other than that, I don't know.

---

### Post by kevdog on 2007-10-09
Go to the wpa section

[http://ubuntuforums.org/showthread.php?t=571194](http://ubuntuforums.org/showthread.php?t=571194)

---

### Post by nraney on 2007-10-10
It stops working in the business school and RLM which i know have wireless.  ill try messing with the WPA settings a bit more and see if that fixes it.  I can almost always fix it by running the command:
sudo wpa_supplicant -Bw -Dndiswrapper -i eth1 -c/etc/wpa_supplicant.conf which I think forces the wpa supplicant to run.. (this is specifically for my computer)

I did this because it seemed to forget that the restricted.utexas.edu was wpa and started asking for my hex passphrase to log on to the network in gnome network manager. it works again after that command.
-nraney

---

