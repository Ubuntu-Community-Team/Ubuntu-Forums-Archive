---
title: "x server error - no screens found"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by ministoat on 2007-09-01
i've somehow managed to fubar my x server..i've tried the following with no luck:

1st
sudo dpkg-reconfigure xserver-org

2nd
sudo apt-get update
sudo apt-get upgrade

3rd
wget [http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server=xorg-core_1.0.2-0ubuntu1-_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server=xorg-core_1.0.2-0ubuntu1-_amd64.deb)

sudo dpkg -i xserevr-xorg-core_1.0.2-0ubuntu0_amd64.deb

i haven't got a whole ot of info about the error but here's what i've noted down

Parse error-line 41 input device file   /etc/X11/xorg.config

problem parsing config file
error parsing config file

fatal error= no screens found

a couple of other htings is shows atm - 

in xf86closeconsole  VT-GETMODE and KDSETMODE have bad file descriptors

what can i do about this? is there a way to reconfigure x server through commandline?

---

### Post by sumguy231 on 2007-09-01
> what can i do about this? is there a way to reconfigure x server through commandline?
That's what 'sudo dpkg-reconfigure xserver-xorg' is supposed to do. I've never seen it write a broken xorg.conf file before. Could you post your /etc/X11/xorg.conf file here?

---

### Post by ministoat on 2007-09-02
maybe i'm tired..tried the steps again and the dpkg-reconfigure command did start the config process! 

can't rly post any log files, it'd take me about an hour to write it down ;)

i'm still haveing problems with the x server config, tho i think i just need to find which drivers to select for my card (nvidia6800)..i was guessing that it was tga and that didnt work at all

---

### Post by ministoat on 2007-09-02
well i have run the x server reconfig a few times now, and i seem to be choosing the wonrg options - i am mostly choosing the defaults, but when i reboot or startx i get a lot of modules showing up as mismatched and "newer than server"

i'm considering a plain reinstall of ubuntu tbh, at a loss here :/

---

### Post by sumguy231 on 2007-09-02
> **ministoat said:**
> maybe i'm tired..tried the steps again and the dpkg-reconfigure command did start the config process! 

can't rly post any log files, it'd take me about an hour to write it down ;)

i'm still haveing problems with the x server config, tho i think i just need to find which drivers to select for my card (nvidia6800)..i was guessing that it was tga and that didnt work at all

You need either the nv or nvidia driver. The nvidia driver does 3d hardware acceleration, the nv one doesn't. If you want the nvidia driver, you need to install nvidia-glx.

---

### Post by ministoat on 2007-09-02
i tried runnig the xconfig with nv driver, but still got the error..on 3rd reinstall already :(

---

### Post by detox187 on 2007-09-02
I know the pain, what were you doing when you fubared the x server config?

---

### Post by jonathanku on 2007-09-03
Yeah, let us know what caused it. I'm in a similar situation. I've got Feisty for AMD64, and Nvidia 7300 GT.

When I tried to enable the NVIDIA driver in the restricted drivers manager, I got the error of NVIDIA kernel version not matching the X kernel version. So I installed nvidia-glx instead of nvidia-glx-new - and I think at this point, I got the error "no screens found". Frustratingly difficult to solve.

I just want 3d working so I get all the juicy compiz / kxdocker stuff :confused:

---

### Post by ministoat on 2007-09-04
first time i dont exactly know, i'd set upa  lot of things in one go..the latest time i've borked it was by trying to reinstall the nvidia drivers, and i think one time was from using envy too.

---

### Post by nowshining on 2007-09-04
try
 
sudo apt-get update
sudo apt-get upgrade



then reboot

---

### Post by jonathanku on 2007-09-04
Again - similar situation to me. I've actually re-installed the OS on another partition to see if it's something I screwed up or if it's an OS / Hardware incompatibility (I actually went for Kubuntu Feisty this time - KDE seems like a good interface) </rabbit trail>

I'll let you know if I manage any better with a clean install.

---

### Post by jonathanku on 2007-09-05
Update, as promised.

I installed Kubuntu Feisty then followed the instructions on this page to install the Nvidia drivers:
[http://www.albertomilone.com/latest_nvidia_udsf_feisty.html]("http://www.albertomilone.com/latest_nvidia_udsf_feisty.html")

**<interesting for 64bit users>**
Before I ran these instructions I did a search for linux-generic in Adept (KDE's equivalent of Synaptic), and noticed a 64-bit version - so I installed that, and it installed the regular linux-generic package too. **</interesting>**

Anyway, followed the rest of the instructions, and I now have nvidia drivers working! In 3d too - "glxgears" works too.
-JK

---

### Post by ministoat on 2007-09-05
are you running anything in wine jon? i'm having problems with my WoW fps, wondering if its a driver issue, i haven't noticed 64bit nvidia drivers.

---

### Post by jonathanku on 2007-09-06
I've not used wine yet. Or WoW.

You'd only need the 64-bit drivers if you're using 64-bit processor _and_ running 64-bit Ubuntu.

J

---

### Post by ministoat on 2007-09-06
yes to both of those...i maybe have the 64bit nvidia drivers installed actually, the page was in my history so i probably did get them from there

---

