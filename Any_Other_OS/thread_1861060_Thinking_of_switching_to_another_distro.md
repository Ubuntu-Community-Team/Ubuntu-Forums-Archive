---
title: "Thinking of switching to another distro"
date: 2011-10-15
forum: Any Other OS
---

### Post by kakashi_12 on 2011-10-15
Thinking of switching to another distro. Any suggestions?

Everyone is telling me to upgrade because 8.10 is not supported anymore. Then when I am ready to upgrade, it does not work any way. I'm stuck between a rock and a hard place here! Installation disc won't load! just goes to a black screen after choosing Install option.

---

### Post by hylogibbon on 2011-10-15
I would try 10.04 first. If you don't like the stability of a 'long term support' version you can give Mint a try. I've heard really good things about that one.

---

### Post by westie457 on 2011-10-15
> **kakashi_12 said:**
> Thinking of switching to another distro. Any suggestions?

Everyone is telling me to upgrade because 8.10 is not supported anymore. Then when I am ready to upgrade, it does not work any way. I'm stuck between a rock and a hard place here! Installation disc won't load! just goes to a black screen after choosing Install option.

Which version are you trying to install, The recommendation for you to use ATM is 10.04.3 LTS which is stable with most of the bugs fixed and is supported until 2013.

Or you could try the latest Xubuntu or Lubuntu. Both easy on resources and very fast.

Hope this helps.

---

### Post by kakashi_12 on 2011-10-15
10.04 32 bit IS the version i am attempting to install.
It loads at first, choose english, choose install
then a black screen for several mins. nothing happens

I'm so frustrated, i've lost hours on this.... days.

---

### Post by westie457 on 2011-10-15
Instead of going straight to the install option suggest you select 'Try' mode first to check whether you have graphic card issues. That goes for any version you care to look at and install.

If you get the same symptoms in try mode reboot the cd. hit Esc just after the POST screen to get to the menu then hit F6 to bring up a sub-menu for the graphics. Try those options one at a time until you get to a Desktop.

What Graphic card are you using, that will help us to help you.

---

### Post by Perfect Storm on 2011-10-15
Moved to Other OS/Distro Talk.

---

### Post by kakashi_12 on 2011-10-15
It's internal and i believe it's intel.

It's a laptop, Alienware Sentia 223, maybe you'll know what graphics card is in that

---

### Post by kakashi_12 on 2011-10-15
Why was the name of the thread changes?! Really? :roll:
I can see the moving it part.

Litterally, this is me with Ubuntu this week [SIZE=4]](*,)[/SIZE]

---

### Post by docbop on 2011-10-15
Try Fodera sometime when a Ubuntu does like the video on a computer I try a Fodera and it works.  But be aware Fodera is Red Hat based not Debian so things will be different.

---

### Post by kansasnoob on 2011-10-15
Don't sweat the little stuff like a thread being renamed or moved :)

Since you're running 8.10 you've not received any security updates since April 2010. That's bad!

So lets start with a hardware profile, please post the output of these commands:

```
lspci | grep VGA
```

```
cat /proc/cpuinfo
```

```
free -m
```

The output of those three commands should give us enough info so we can make some recommendations :D

---

### Post by kansasnoob on 2011-10-15
BTW, you'll not be able to upgrade from 8.10 because it's soooooooooo old. You will need to do a fresh install :)

---

### Post by kakashi_12 on 2011-10-15
That's exactly what i'm trying to do (a fresh install)
and it's NOT working... for the 10th time.
im so frustrated. I'd rather stick with ubuntu to be honest. I like it. I just hate the install process of it.

---

### Post by alex.rayu on 2011-10-16
Kakashi, if install fails, you should at least get an error message and tell it. A CD? Is CD corrupted? Try another one. 8.10 - is your laptop old? How old?

There is no reason to install for 10 times and waste days. Fails twice - need to analyze, tell the symptoms to the community. Sometimes it can be something banal (a bad cd), and sometimes your old hardware can be incompatible, or even some controller or device may be a bit burned or contacts went off the board.

---

### Post by linuxaddix on 2011-10-16
give mint a try i recommend mint 10 julia gnome or whatever your preference is.its a beautifully made distro.its ready to go right out of the box.when you get used to it move up to mint 11 or wait till next month mint 12 should be out.but i say mint it

---

### Post by mystika1 on 2011-10-16
I would recommend that you try Lubuntu on your machine. Correct me if I am wrong but it seems that your machine may be a bit dated and that is Lubuntu's specialty.(works well with older hardware) Besides...It is really fast. It does not take long to install and is easy to use. Here is the download page if you are interested. 

[https://wiki.ubuntu.com/Lubuntu#Get_Lubuntu](https://wiki.ubuntu.com/Lubuntu#Get_Lubuntu)

You may have a badly burned disk which has caused your problems...I would burn a fresh disk of the above Lubuntu and try that before switching. 

HTH,

Penny

---

### Post by kakashi_12 on 2011-10-16
Well, it sounds like Lubuntu is a good option. How similar to Ubuntu is it?
 
Yes, my machine is a little outdated. It has a single core in it. 2.0 Ghz though.
 
And no, there is no error. Like I said before, just a black screen after the ubuntu screen.
 
I did not burn a disc actually. Because my disc drive is broken. There is one hardware problem. I just had my replacement dvd drive shipped to me yesterday. I've been using USB drive. Which I know it boots to, because it started... just didn't finish. I used the "USB Startup Creator" tool in Ubuntu.

---

### Post by kakashi_12 on 2011-10-16
As far as Lubuntu goes... or Mint for that matter. Here is what I need it to support. Can it do this (or at least some of this)....
 
- Grub loader (can I modify it easily or does it use a different loader)
- KDE Games
- VLC Player
- Wine
- Set up multiple users and permissions
- Access to Windows partitions
- Make the login screen input both username and password (not show the usernames)
- OpenOffice
- ClamAV
- Wireless network card

---

### Post by mips on 2011-10-16
Have a look at Xubuntu 11.10, really nice.

---

### Post by kurt18947 on 2011-10-16
> **mystika1 said:**
> I would recommend that you try Lubuntu on your machine. Correct me if I am wrong but it seems that your machine may be a bit dated and that is Lubuntu's specialty.(works well with older hardware) Besides...It is really fast. It does not take long to install and is easy to use. Here is the download page if you are interested. 

[https://wiki.ubuntu.com/Lubuntu#Get_Lubuntu](https://wiki.ubuntu.com/Lubuntu#Get_Lubuntu)

You may have a badly burned disk which has caused your problems...I would burn a fresh disk of the above Lubuntu and try that before switching. 

HTH,

Penny
I'll go along with Lubuntu.  I didn't care for Chromium, deleted it, tried Midori which works okay but is still "young", installed Opera and so far so good. PIII, 512 Mb. RAM. The only shortcoming is that flash is more like a slide show than video. I did have trouble on this machine when trying to install Xubuntu, it did the same thing as the O.P., a few flashes when starting then nothing. I'm not sure if it was a video problem or something else.

---

### Post by mystika1 on 2011-10-16
> **kakashi_12 said:**
> As far as Lubuntu goes... or Mint for that matter. Here is what I need it to support. Can it do this (or at least some of this)....
 
- Grub loader (can I modify it easily or does it use a different loader)
- KDE Games
- VLC Player
- Wine
- Set up multiple users and permissions
- Access to Windows partitions
- Make the login screen input both username and password (not show the usernames)
- OpenOffice
- ClamAV
- Wireless network card

Yes...Lubuntu can do all that you need. I have several KDE games on my machine along with VLC Player. Wine is in the repos. Multi users same as other buntu's. I also dual boot and can access my windows partition easily. Login screen asks you to input the users name then password....Openoffice suite is in repos and so is clamAV...

I don't have a wireless network but someone else may be able to chime in with that info.

HTH,
Penny

---

### Post by mystika1 on 2011-10-16
Hi again,
I use Firefox on my machine and use the addon called Flash-Aid. It installs the latest flashplayer and tells you when an upgrade is available. I got the best playback with flash-aid....

Just thought I'd mention that in case it would help you.

Penny

---

### Post by madjr on 2011-10-16
> **kakashi_12 said:**
> Why was the name of the thread changes?! Really? :roll:
I can see the moving it part.

Literally, this is me with Ubuntu this week [SIZE=4]](*,)[/SIZE]

we all had those days :o

the problem is always a combo between the **old hardware** and newer distros.

Gladly there are many choices out there and many nice people willing to help.

anyway lubuntu is a good choice.

anyway please try an "**alternate** installer"

"[I]Alternate installer details

The text-based alternate installer can be downloaded from a location near you. This installation CD is suited for computers unable to run the graphical desktop based installation, either because their computer does not meet the minimum requirements for the live cd or because their computer requires configuration after the installation is complete in order to use the desktop.[/I]"

[http://lubuntublog.blogspot.com/2010/10/alternate-install.html](http://lubuntublog.blogspot.com/2010/10/alternate-install.html)
[http://lubuntublog.blogspot.com/p/downloads.html](http://lubuntublog.blogspot.com/p/downloads.html)
[https://wiki.ubuntu.com/Lubuntu/DocumentationHelp/AlternateInstall](https://wiki.ubuntu.com/Lubuntu/DocumentationHelp/AlternateInstall)

for normal ubuntu
[http://ch.releases.ubuntu.com/](http://ch.releases.ubuntu.com/)

---

### Post by kansasnoob on 2011-10-16
If you're able to run 8.10 why not provide the info requested in post #10?

That would help us to help you immensely because we'd then know what CPU you have, what GPU you have, and how much RAM you have ;)

---

### Post by kakashi_12 on 2011-10-16
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)

processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 13
model name    : Intel(R) Pentium(R) M processor 2.00GHz
stepping    : 6
cpu MHz        : 600.000
cache size    : 2048 KB
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 2
wp        : yes
flags        : fpu vme de pse tsc msr mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe up bts est tm2
bogomips    : 1200.03
clflush size    : 64
power management:

 total       used       free     shared    buffers     cached
Mem:          1992        516       1476          0         14        171
-/+ buffers/cache:        330       1662
Swap:         2863          0       2863

forgot to add to my list of requirement, does Lubuntu support Swap partitions? Is swap standard for pretty much all Linux distros?

---

### Post by kansasnoob on 2011-10-16
OK, that graphics chip set has been problematic for some time now :)

Look here for some info about the current LTS:

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

But lets slow down and figure some things out, OK?

Someone else may jump in, and that's fine, but right now I'm physically and mentally cooked - so I'll check back tomorrow ;)

---

### Post by madjr on 2011-10-16
> **kakashi_12 said:**
> 
forgot to add to my list of requirement, does Lubuntu support Swap partitions? Is swap standard for pretty much all Linux distros?

no matter what desktop you use, linux is the same in the inside, so yes :)

---

### Post by PsyGeek on 2011-10-16
A few weeks ago my Xubuntu started to **** me off, mainly because of the 'bloat' (the overload of packages that I can do without). After trying a lot of distros I ended up installing Xubuntu again and removing almost half of the installed packages :p. The main reason I went back to (x)ubuntu is synaptic, it's the best packet manager that I know. Xubuntu is also a nice looking distro imo. 

To decide which distro to install, I suggest to find out which desktop environment that you prefer and looking for a distro by searching at distrowatch.com (which contains information about 150+ distros). The desktop environment is personal taste. I hate KDE with a passion, I'm neutral about Gnome and I like xfce and lxde (both light-weigh). Lxde is a new and promising one, but still lacks some functionality at the moment.  

Three noteworthy distros I came across are:
- Fedora (xfce spin): Fast, lightweight and stable (at first sight). I'm not sure why I removed it.
- openSUSE (with gnome): A great installer and very decent system, but ugly as hell. If I ever start a business, I would install openSUSE there.
- ArchLinux: Rolling releases with repositories that always contain the most recent stable releases of basically everything. This is probably the best system if you are a linux expert. If you are not, you won't get through the installation (like me). The installer only helps you setting up partitions, the clock and a very basic system. For a desktop environment, internet access, setting up a user account, etc, you are on your own :p.

---

### Post by kakashi_12 on 2011-10-16
Alright... so I'm trying before I install.
I am having a couple of problems.
Should I start a new thread since this is particular to this variant?

Mainly I am having issues with wireless network/internet.
Lubuntu comes with NDIS Wrapper by default (Windows Wireless Drivers)
I'm having the same issues that I did before (if you see my previous thread)
I have installed the inf file (wireless driver) and it shows. I enabled wireless. But I can't see any Broadcasted Wireless Networks. Did I miss a step?

Also, I am trying to run the ifconfig wlan up cmd and getting permission denied. Does anyone know the default root password on Trying Lubuntu?

---

### Post by mystika1 on 2011-10-16
Hi,

amjjawad may be able to help you. He also uses Lubuntu. If you do decide to start a new thread and show Lubuntu in the title...he would prob reply.

Penny

---

### Post by mystika1 on 2011-10-16
I found a thread which may be of help to you..

[http://forum.lxde.org/viewtopic.php?f=8&t=31170&p=37001&hilit=wireless+network#p37001](http://forum.lxde.org/viewtopic.php?f=8&t=31170&p=37001&hilit=wireless+network#p37001)

Penny

---

### Post by kakashi_12 on 2011-10-17
Well that didn't help. Those commands also require root access. Still trying to find the default lubuntu root password in live.

---

### Post by mystika1 on 2011-10-17
> **kakashi_12 said:**
> Well that didn't help. Those commands also require root access. Still trying to find the default lubuntu root password in live.

Have you tried typing the word root? Nearly every distro that I try live has the root password listed as "root." Sorry if you have already tried this. It is just a suggestion.

HTH,

Penny

---

### Post by kakashi_12 on 2011-10-17
Yes I tried. No that's ok... process of elimination.
Tried root, tried blank, tried su, tried sudo, and tried ubuntu, and lubuntu.

---

### Post by hansdown on 2011-10-17
Hi, kakashi_12.

I think this is it;

login: custom
pass: blank

---

### Post by kakashi_12 on 2011-10-17
How can a root password have a different username. The username is root.
 
I can't even get in Live now anyway. For some reason. It's asking for a username and password and i didn't even create any accounts. It must have saved some info to the bootable USB. I may have to 'reburn' the iso.

---

### Post by kakashi_12 on 2011-10-17
Well... I've got back into live session.
I'm having more problems with wireless than I was before. Arrrrrgh.
when running ifconfig it won't even see the wlan0. Why?

And to try and get root access, i tried to create the user root. Of course that wouldn't let me. Tried to add myself to the root group. No help there. Changing my account type and permissions didn't help. If root is a user, why the heck doesn't it show in Users applet?

---

### Post by madjr on 2011-10-17
not sure if this will help, but linuxmint also has an lxde edition you can try

[http://blog.linuxmint.com/?p=1802](http://blog.linuxmint.com/?p=1802)

hope things work out

---

### Post by MonolithImmortal on 2011-10-18
If you end up switching distro's may I recommend [Fuduntu]("http://www.fuduntu.org/")?

---

### Post by kakashi_12 on 2011-10-18
That's funny you mention that, because I decided last night I'll try out Mint while I'm waiting for a response to my question. (Someone suggested it a few posts back)

Fubuntu? Is that anything like Fedora? What's the F stand for? Why do you suggest it?

Looks like I'll be trying out a lot before I decide on one.

---

### Post by MonolithImmortal on 2011-10-18
> **kakashi_12 said:**
> That's funny you mention that, because I decided last night I'll try out Mint while I'm waiting for a response to my question. (Someone suggested it a few posts back)

Fubuntu? Is that anything like Fedora? What's the F stand for? Why do you suggest it?

Looks like I'll be trying out a lot before I decide on one.

It was originally based on Fedora 14, but they are forking it into a rolling distro of its own. The name implies that it is somewhere in between Fedora and Ubuntu in usability. One of its selling points is that it has Jupiter installed by default, which tremendously improves your battery life on a laptop. I installed jupiter in 11.10 and went from 3 1/2 hour battery life to 6 1/2 hour battery life.

---

### Post by amjjawad on 2011-10-18
Hi there,

A friend of mine has sent me the link of this thread.

Well, with all due respect to everyone here, I don't see any mention to "Have you checked MD5SUM?" which is the first step that anyone must do before even thinking what is the next step?
So, my question to the OP is:
Have you checked MD5SUM?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

My second question is:
What software are you using to create the Live-CD?
Are you following the correct directions?

[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

My third question is:
Have you tried Live-USB? what software are you using to create it?

[http://en.wikipedia.org/wiki/Live_USB](http://en.wikipedia.org/wiki/Live_USB)
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

My forth question is:
If your machine can't handle booting from USB and your CD Drive is not working probably so, have you heard of:
[http://www.plop.at/en/bootmanager.html](http://www.plop.at/en/bootmanager.html)

By the way, just make sure you are downloading the correct iso that work on your hardware and make sure to read the release note for whatever you'll choose so that you be familiar with the known bugs, the features, etc.

Above are the "first" steps you and anyone else need to follow in order to move to phase two which is "Do I have to try another distribution?"

Once we are done from this part, we can talk whether you need another distribution or not.

Free Advice: whenever you feel frustrated, please take a walk and breath some fresh air. Being frustrated is an alert that things will be bad if you carry on :) sometimes, could be worse.

Please FEEL FREE to message me any time but I do prefer threads so everyone will read and share.
In case you want to start a new one, PM me the link.

I'm NOT a Linux Guru/Expert but I do have my own style which is I do my best to help you no matter what.

Relax and your problem will be fixed, trust me.

---

### Post by kakashi_12 on 2011-10-18
Yes, someone else did already suggest to check the MD5checksum.
No I did not check it? Isn't that checking for proper burning?

Like I said before, I am using the Ubuntu app "Create USB Bootable" under Administration menu

Yes, that's what I'm using a Live USB

No I have not heard of that Plop Boot Manager. How will that help me?

Thanks for your comfort and help.

---

### Post by amjjawad on 2011-10-18
> **kakashi_12 said:**
> Yes, someone else did already suggest to check the MD5checksum.
No I did not check it? Isn't that checking for proper burning?

Like I said before, I am using the Ubuntu app "Create USB Bootable" under Administration menu

Yes, that's what I'm using a Live USB

No I have not heard of that Plop Boot Manager. How will that help me?

Thanks for your comfort and help.

If you go through my post again and all the links included in my post, ALL your questions will be answered ;)
That is exactly why I include links when I post :)

Let me know if something still not clear.

My previous post hold suggestions, guide, questions, etc. All in one:)

You are most welcome but I haven't done much yet ;)

---

### Post by kakashi_12 on 2011-10-18
Ok, still having the same issue with Mint that I did with Ubuntu.
It won't see the Wireless driver to activate it. Why does this have to be difficult? Not even using NDIS Wrapper this time.

.... Tried Mint. I don't care for the look of it much. It looks too much like Windows. If I can get it to work though, that's all I really care about.

---

### Post by kakashi_12 on 2011-10-19
Well.... one thing finally went right....
Thanks to the person that sent me this link...
[http://googlethem.com/ubuntu-live-cd-root-password-and-live-session-password-for-user-ubuntu/](http://googlethem.com/ubuntu-live-cd-root-password-and-live-session-password-for-user-ubuntu/)

I actually didn't try that before. That worked!... setting the root password. Now I have root access. I can finally run commands as sudo.

Now, I'm still having problems with NDIS Wrapper in Lubuntu. Currently I have the driver installed, and i can run ifconfig wlan0 down
But can not run ifconfig wlan0 up
No such file or directory found
which is a weird error for that.

If I unplug and plug back in the wlan card, it says disconnected. So it sees the card. Just not the wireless networks. Now what?


.... ok, now I've given myself permission to connect to wireless networks. Now when I run the commands, up or down, i get this error message...
ERROR while getting interface flags: No such device


.... ok, i did a reboot now, no when i go to the connections it says Wireless Networks (grayed out) under it says Device not ready missing firmware
How do I get firmware?

---

### Post by kakashi_12 on 2011-10-19
Per my previous thread, I downloaded and installed the firmware there. But I'm getting errors. Please see below...


root@ubuntu:/media/PublicZone/Apps/Drivers# sudo tar xvf Broadcom_Firmware.tar.gz -C /lib/firmware/
b43/
b43legacy/
b43/b0g0initvals5.fw
b43/b0g0bsinitvals5.fw
b43/a0g0initvals5.fw
b43/a0g1initvals5.fw
b43/a0g0bsinitvals5.fw
b43/a0g1bsinitvals5.fw
b43/b0g0initvals9.fw
b43/b0g0bsinitvals9.fw
b43/a0g0initvals9.fw
b43/a0g1initvals9.fw
b43/a0g0bsinitvals9.fw
b43/a0g1bsinitvals9.fw
b43/n0initvals11.fw
b43/n0bsinitvals11.fw
b43/n0absinitvals11.fw
b43/lp0initvals13.fw
b43/lp0bsinitvals13.fw
b43/b0g0initvals13.fw
b43/b0g0bsinitvals13.fw
b43/a0g1initvals13.fw
b43/a0g1bsinitvals13.fw
b43/lp0initvals14.fw
b43/lp0bsinitvals14.fw
b43/lp0initvals15.fw
b43/lp0bsinitvals15.fw
b43/ucode5.fw
b43/ucode9.fw
b43/ucode11.fw
b43/ucode13.fw
b43/ucode14.fw
b43/ucode15.fw
b43/pcm5.fw
b43legacy/a0g0bsinitvals5.fw
b43legacy/b0g0initvals2.fw
b43legacy/b0g0initvals5.fw
b43legacy/b0g0bsinitvals2.fw
b43legacy/a0g1initvals5.fw
b43legacy/a0g0initvals2.fw
b43legacy/a0g1bsinitvals5.fw
b43legacy/a0g0initvals5.fw
b43legacy/b0g0bsinitvals5.fw
b43legacy/a0g0bsinitvals2.fw
b43legacy/pcm5.fw
b43legacy/pcm4.fw
b43legacy/ucode11.fw
b43legacy/ucode5.fw
b43legacy/ucode4.fw
b43legacy/ucode2.fw
root@ubuntu:/media/PublicZone/Apps/Drivers# sudo modprobe -v b43
root@ubuntu:/media/PublicZone/Apps/Drivers# dmesg | grep b43
[   47.527463] b43-pci-bridge 0000:02:00.0: enabling device (0000 -> 0002)
[   47.527479] b43-pci-bridge 0000:02:00.0: PCI INT A -> Link[LNKB] -> GSI 3 (level, low) -> IRQ 3
[   47.527492] b43-pci-bridge 0000:02:00.0: setting latency timer to 64
[   48.151753] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[   48.284986] Registered led device: b43-phy0::tx
[   48.285062] Registered led device: b43-phy0::rx
[   48.286411] Registered led device: b43-phy0::radio
[   48.700994] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   48.700999] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   48.701003] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[  256.951604] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[  256.951610] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[  256.951614] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
root@ubuntu:/media/PublicZone/Apps/Drivers# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan2     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          
root@ubuntu:/media/PublicZone/Apps/Drivers# lsmod
Module                  Size  Used by
parport_pc             32114  0 
ppdev                  12849  0 
lp                     17455  0 
dm_crypt               22565  0 
parport                40930  3 parport_pc,ppdev,lp
arc4                   12473  2 
b43                   318816  0 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
mac80211              272785  1 b43
snd_intel8x0           33318  1 
snd_ac97_codec        106082  1 snd_intel8x0
cfg80211              172392  2 b43,mac80211
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80468  2 snd_intel8x0,snd_ac97_codec
ssb                    50682  1 b43
snd_seq_midi           13132  0 
joydev                 17393  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
pcmcia                 39822  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73673  0 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
snd                    55902  9 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              12990  0 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
shpchp                 32356  0 
squashfs               36095  1 
overlayfs              27481  1 
nls_iso8859_1          12617  2 
nls_cp437              12751  2 
vfat                   17308  2 
fat                    55577  1 vfat
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 622589  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
usb_storage            44173  2 
uas                    17699  0 
i915                  505108  2 
firewire_ohci          35854  0 
8139too                23283  0 
firewire_core          56937  1 firewire_ohci
8139cp                 22636  0 
crc_itu_t              12627  1 firewire_core
drm_kms_helper         32889  1 i915
drm                   192226  3 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  18908  1 i915

---

### Post by amjjawad on 2011-10-20
> **kakashi_12 said:**
> Well.... one thing finally went right....
Thanks to the person that sent me this link...
[http://googlethem.com/ubuntu-live-cd-root-password-and-live-session-password-for-user-ubuntu/](http://googlethem.com/ubuntu-live-cd-root-password-and-live-session-password-for-user-ubuntu/)

I actually didn't try that before. That worked!... setting the root password. Now I have root access. I can finally run commands as sudo.

I'm glad because the link I sent you was helpful :)

> Now, I'm still having problems with NDIS Wrapper in Lubuntu. Currently I have the driver installed, and i can run ifconfig wlan0 down
But can not run ifconfig wlan0 up
No such file or directory found
which is a weird error for that.

If I unplug and plug back in the wlan card, it says disconnected. So it sees the card. Just not the wireless networks. Now what?


.... ok, now I've given myself permission to connect to wireless networks. Now when I run the commands, up or down, i get this error message...
ERROR while getting interface flags: No such device


.... ok, i did a reboot now, no when i go to the connections it says Wireless Networks (grayed out) under it says Device not ready missing firmware
How do I get firmware?

One simple question.
Are you trying all that from the Live-CD or Live-USB? have you installed it or not yet?
The reason why I'm asking is because whatever you do, once you reboot, it's all gone. I just want to make sure that you are actually aware of that :)

---

### Post by kakashi_12 on 2011-10-20
Live USB. No, have not installed yet. Yes, I am aware of that that it will go away. The funny thing is is that when I did reboot, it FINALLY worked. That's because on a Live USB, it saves info. On a Live CD, it does not because CD-R are read-only. So i FINALLY got it to work. After installing the cutter firmware, rebooting. And running those cmds.

---

### Post by madjr on 2011-10-20
> **kakashi_12 said:**
> Live USB. No, have not installed yet. Yes, I am aware of that that it will go away. The funny thing is is that when I did reboot, it FINALLY worked. That's because on a Live USB, it saves info. On a Live CD, it does not because CD-R are read-only. So i FINALLY got it to work. After installing the cutter firmware, rebooting. And running those cmds.

glad you got it working. i wonder if the devs know about this problem and plan to issue updates to fix them for everyone...

---

### Post by kakashi_12 on 2011-10-21
Do you know how to get a hold of the DEV's?
I wish I did. If you do... tell them.
 
For everyone else, I finally installed Lubuntu as my choice. Haven't got much time to use it yet. So far the only down side is that I'm seeing the GRUB loader load slower than my older one. Other than that, everything else is ok.

---

### Post by amjjawad on 2011-10-21
> **kakashi_12 said:**
> Do you know how to get a hold of the DEV's?
I wish I did. If you do... tell them.
 
Ubuntu or Lubuntu?
You can do that yourself by the way :)

> For everyone else, I finally installed Lubuntu as my choice. Haven't got much time to use it yet. So far the only down side is that I'm seeing the GRUB loader load slower than my older one. Other than that, everything else is ok.
I'm glad to know that :)

GRUB is loading slower than before? how is that? could you please explain more?

---

### Post by madjr on 2011-10-21
> **kakashi_12 said:**
> Do you know how to get a hold of the DEV's?
I wish I did..
 


here you go:
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by kakashi_12 on 2011-10-21
> **amjjawad said:**
>  
GRUB is loading slower than before? how is that? could you please explain more?
 
Exactly what I mean is...
POST displays
Then I wait 5-15 secs until grub loads
the timer doesn't load until about 3-5 secs later
Then when I do press enter to select the OS I want, it still takes about 15 secs before switching to the next screen (black screen, before loading OS)
I'm wondering if it's because it's LXDE.
 
With Grub in Ubuntu, it was an instant load from the POST. And then when choosing an OS, it would instantly load. No lag.
 
But it's no biggie.

---

### Post by amjjawad on 2011-10-21
> **kakashi_12 said:**
> Exactly what I mean is...
POST displays
Then I wait 5-15 secs until grub loads
the timer doesn't load until about 3-5 secs later
Then when I do press enter to select the OS I want, it still takes about 15 secs before switching to the next screen (black screen, before loading OS)
** I'm wondering if it's because it's LXDE.**
 
With Grub in Ubuntu, it was an instant load from the POST. And then when choosing an OS, it would instantly load. No lag.
 
But it's no biggie.

Definitely with LXDE, it should be faster.
If the same PC was running Ubuntu and now Lubuntu, it should show some difference. If you like, I can help you with that. Your choice :)

---

### Post by kakashi_12 on 2011-10-21
No, no, no.... your choice.... lol.
 
I got time. What are you suggesting?
 
ps. haven't gotten to it yet, but I am going to shorten the grub menu by removing some menu lines. I am dual booting, so i only need two lines.

---

### Post by amjjawad on 2011-10-21
> **kakashi_12 said:**
> No, no, no.... your choice.... lol.
 
I got time. What are you suggesting?
 
ps. haven't gotten to it yet, but I am going to shorten the grub menu by removing some menu lines. I am dual booting, so i only need two lines.

Hahahaha, you need to trust your judgement :D

Ok, that will take some time so if you got time, let's do it.
I first need to look into your GRUB Structure so I can tell what is going on under the hood.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Please read carefully and post the output here and make sure to wrap up the text with "CODE" tags :)

---

### Post by kakashi_12 on 2011-10-21
I've got a small problem. WHen I right click on 'filesystem' from My Computer it lies to me about space. I want to know how much space is used from my partition. It says 0. It also says the capacity is 0.
 
I take that back... I don't have time to boot to Live. Maybe another time. I still have to set my settings, prefences, and gpo's in win. Thanks though.

---

### Post by amjjawad on 2011-10-21
> **kakashi_12 said:**
> I've got a small problem. WHen I right click on 'filesystem' from My Computer it lies to me about space. I want to know how much space is used from my partition. It says 0. It also says the capacity is 0.

There is NO "My Computer" in Lubuntu so I'm not sure what you really mean?

 
> I take that back... I don't have time to boot to Live. Maybe another time. I still have to set my settings, prefences, and gpo's in win. Thanks though.Never mind, whenever you got time, let me know :)
I'm subscribed to your thread so once you post, I'll be notified :)

---

### Post by kakashi_12 on 2011-10-21
Ok. Not My Computer, just Computer. Go to Places Then Computer. Select 'file system' .... in Windows Language "C Drive".

---

### Post by garth813 on 2011-10-21
I have been running ubuntu 10.10 and it has been running great, I would highly recommend it.  I have been considering another distro like you, and a friend at work gave me the latest version of linux mint, it is debian based so it may be worth a try.  As for your black screen problem during the installation process, press the f6 key at startup and then find the boot option nomodset.  If you can boot into the system  successfully using this method you can install the necessary drivers and such.

---

### Post by kakashi_12 on 2011-10-22
Like I said, I already tried that.
Trust me, I like Ubuntu. It just isn't compatible with my old hardware. So I chose Lubuntu :)

---

### Post by 23dornot23d on 2011-10-22
If you have 0 space on your root drive ...... as you are implying .... that will cause it to slow 
boot .... and may even lock up ....

to free a little space

sudo apt-get clean
sudo apt-get autoclean

As said you need to run the script file ......


[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

 for boot info ..... that will let people know how
your disk / disks are set up ...... it will also show where it boots from ...... and lots more information about the boot operations including the cfg

---

### Post by amjjawad on 2011-10-22
> **kakashi_12 said:**
> Ok. Not My Computer, just Computer. Go to Places Then Computer. Select 'file system' .... in Windows Language "C Drive".

If you are using Ubuntu, check the File Manager and it should tell you the used space and free space.

From Terminal, you can do that too: [https://help.ubuntu.com/community/UsingTheTerminal#File_.26_Directory_Commands](https://help.ubuntu.com/community/UsingTheTerminal#File_.26_Directory_Commands)

Check "du" and "df".

---

### Post by kakashi_12 on 2011-10-22
Thanks. Does this answer my question properly

kakashi12@Sentia:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda3             26764348   3330240  22074544  14% /

So, only 14% of the partition is used so far?

STARTING A NEW THREAD AS THIS ORIGINAL ISSUE IS SOLVED
OS CHOOSEN
THANK YOU ALL! :)
(new thread under general help)

---

### Post by amjjawad on 2011-10-22
> **kakashi_12 said:**
> Thanks. Does this answer my question properly

kakashi12@Sentia:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda3             26764348   3330240  22074544  14% /

So, only 14% of the partition is used so far?

> **df**: The **df** command displays filesystem disk space usage **for all mounted partitions**. "**df -h**" is probably the most useful - it uses megabytes (M) and gigabytes (G) instead of blocks to report. (**-h** means "human-readable") 

The only mounted partitions ;)
sda3 is where Ubuntu (or Lubuntu?) is installed into your system.
14% is used.

---

