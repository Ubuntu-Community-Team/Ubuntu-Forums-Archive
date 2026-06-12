---
title: "WG511T Wifi Issues"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by sumnone on 2007-02-09
I just installed Ubuntu and it seems nice.  The laptop I installed it on is rather ancient.  It's a PII 400 Micron with 128MB of RAM.  During the install it detected my wifi card, but couldn't detect an IP address.  I had encryption and restricted mac addresses set on my router, so I opted to configure it later.  I feel that was a mistake now as I can not get this card to work.

The help docs say the WG511T works perfectly with Ubuntu.  However, it is not detected unless I reboot and even then I can only get a single continuous blinking from the left LED and hints of it in the OS.  I've gone through Ubuntu forums, other forums and the Ubuntu help docs going as far as trying the config.opts modification.

When I run lshw, it shows the card as: *-network UNCLAIMED (it then goes on to describe the card) with a missing "configuration:" line (based on other entries).  When I run lspci, it shows:

02:00.0 Ethernet Controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

Iwconfig shows "no wireless extensions" for both lo and sit0.

The help docs are unclear to me as it states if I run lshw and can see the card, I'm good.  It then goes on to say if I run "sudo pccardctl ident" and see nothing ("no product info available" is what I see for both socket 0 and 1), "If you get no output then the memory on the card can not be read which could be the problem."  However, I don't feel that is the issue.

I don't feel I'm loading the drivers properly and feel the UNCLAIMED status and no configuration line is the key, but really am just guessing.  What am I missing?  Please be specific as I really don't know what I'm doing.  I appreciate the help.

Thanks.

---

### Post by shane634 on 2007-02-09
Take a look here:

[http://www.ubuntuforums.org/showthread.php?t=339810&highlight=AR5212](http://www.ubuntuforums.org/showthread.php?t=339810&highlight=AR5212)

  This should help ya out. Good luck.

---

### Post by sumnone on 2007-02-09
Thanks Shane634! That worked!

I had to research the command to get the modules (from the recommended post) installed in yet another forum. So, for those newbies who aren't good with linux (like myself), the specific command I ran is:

sudo apt-get install linux-restricted-modules-$(uname -r)

After inserting my 6.10 install CD (after being prompted) and waiting until completion, a restart of ubuntu allowed the adapter to show up in the Networking control panel.  At that point I specified my ESSID and enabled the card.

I'm not sure if this is normal or not, but in order to make it work, I wasn't able to just highlight the adapter, go into the properties, choose "enable this connection," modify the settings, and choose Ok.  I had to actually click the little box next to the adapter, a progress indicator popped up and then put me in the properties for the device.  Upon choosing my settings and hitting OK, a check mark showed up next to the adapter.  At that point it was working.

Now, I'm on to see if I can get all the security for the wifi setup again, among a couple other issues I'm having.

Once again, I really appreciate the help.

---

### Post by jml on 2007-02-09
Hang in there, getting wireless working in Linux is probably one of the toughest things you will have to do.  But it is doable.  It was actually a good thing that you did not configure the card with your install.  I'll explain below.  I have the very same card connecting wirelessly as I write this,  There are several general steps to the process.  First, you do not need to install any drivers separately.  Ubuntu recognizes the Atheros chip set, (the one your card uses,) out of the box.  Just reboot your computer with the card plugged in and it should be recognized.  The fact that one light is blinking and the file you posted mentions the atheros chip set supports this.

Second, do not use the default networking tool supplied with Ubuntu.  i.e. don't use System--->Administration--->Networking.  First download and install two applications:  network-manager and network-manager gnome.  After you do that you will see a small icon in the right upper corner of your screen.  The various functions of the application can be accessed by right clicking and left clicking on the icon.  BUT DON'T DO THAT YET.  ;) 

Next, disable all encryption on your wireless access point temporarily, along with MAC filtering.  Then first left click on the icon in the right upper corner of your screen.  If you see your network listed, click on the radio button to activate.  In about a minute or less you should see a message that you are connected.  If not right click again and select create new wireless network.  Once you have successfully connected.  turn encryption back on and attempt to connect again, you should be prompted for your encryption code.  Enter it ans after about a minute, you should be in.

joe

---

### Post by sumnone on 2007-02-12
Thanks Joe for taking time to spell all that out!  I need it....literally!

I used the "Software Updates" feature that pops up in the upper right hand corner.  It installed 130+ updates (in two phases) and then required a restart.  After the restart, I no longer have wifi again.

I'm back to a single blinking light.  So according to what you wrote, I should be good to try what you mentioned.  Hopefully, it will stick.  I'll let you know...

Regards.

---

### Post by Spr0k3t on 2007-02-12
I'd like to post my findings on this.  Every time there is a kernel update, the same procedure will need to be done.  I have an AR5212 card from Netgear as well (WG311T).  After the kernel update, I had to reinstall the restricted modules.  Even though I had the multiverse/universe set correctly in my sources.list, the modules did not install by default.  Once i did the following

```
sudo apt-get install linux-restricted-modules-`uname -r`
```

I had to rebuild my kernel with the nVidia drivers again.  This works.  And from what I have read from others, every time the kernel is updated, the third party drivers will need to be rebuilt into the new version of the kernel.  So keep the information handy and be prepared to use it again later on.

I hope this helps.

---

### Post by sumnone on 2007-02-13
So I tried what Joe recommended and installed network-manager and network-manager-gnome and I see the icon in the upper right hand corner.  However, I don't see my network and I don't have the option to create a new one (or anything similar to that).  The wifi adapter is still in an UNCLAIMED status when executing a lshw.

As a test, I pulled the adapter out and put it back in hopes that it would somehow detect it and magically work. ;)  However, the card was dead and a restart was required to get my single blinking light back.

So I thought I'd try what Spr0k3t recommended and at least get back to where I started with some connectivity.  (I was also GUESSING that what Joe recommended may be related to these modules somehow?)  However, now when I try to install the linux-restricted-modules, the procedure is trying to make a connection to security.ubuntu.com and of course it's failing because the wifi is dead.  Ugh.

I really need to do my homework and get a better understanding of all these procedures and how they relate to one another, if at all.  It also looks like my pcmcia (wired) NIC may be a useful tool in solving these issues.  Now I just have to find it...

As always, I appreciate the help!

---

### Post by Spr0k3t on 2007-02-13
If you can't get connected with wireless, you will need to try to connect with wired.  Once I was able to update the kernel with the linux-restricted-modules and update the other components of the kernel, my wireless card came back like it didn't skip a beat.

I'm still learning all this as well, but the kernel update was a radical curve in my learning and has forced me to jump in head first without looking.  I'm still debating making my learning the linux curve journal public or not.  I'd have to really work on cleaning it up and segmenting it out.  But it would give a good limelight on a new/returning user (pre-X user that is).

---

### Post by drs305 on 2007-02-18
First, thanks to all who contributed to this thread. I'm a Linux/Ubuntu newbie and have read LOTS of posts regarding wifi in order to get mine working. This thread did the trick. Special thanks to JML for the hints about final configuration. I would make one comment for newbies who may be as dense as I am: when you reset the wifi to accommodate encryption, make sure you select the appropriate format. My security settings default to 128 bit but I had to use the drop-down menu to select 64 bit hex before it would accept my WEP codes. That's just how I'd set up my codes years ago in XP, I don't know what the Netgear defaults are. Once I did that everything worked great.

Now I have a couple of questions:

1. When I take this laptop on the road and am using the WG511T card, will I have to change or get rid of my security settings before the card will find unencrypted signals? I'm thinking I'd have to click on network manager and establish a new source but I don't know. I'd rather find out now rather than when I'm on the road and unable to connect!

2. My Lenovo laptop comes with an internal modem. I've been struggling for more than a week to get it working but have had no success. I think it's a Broadcom 4311 and I know there are lots of issues with Broadcom. Anyway, can I mess up my WG511T settings if I try to get the internal modem to work or would I be best served by leaving everything the way it is now and just forgetting the internal wifi card (perhaps until Feisty)?

Again,thanks to everyone for their continued support of us newbies.

---

### Post by ubuntu_demon on 2007-02-22
I would suggest to not use ndiswrapper. If you have used ndiswrapper first undo the steps you have done trying to make it work with ndiswrapper. Then install the restricted modules for your kernel.

$uname -r

Then choose which one to install based on that result :
$ sudo aptitude install linux-generic
$ sudo aptitude install linux-386
$ sudo aptitude install linux-686

This packes makes sure that you will always have the relevant restricted modules even after a kernel upgrade.

Login to your router and set your router to unsecured.

Now do a reboot and configure your network using system->administration->networking.

If all is well now you will have wireless internet :).

Otherwise you might need to modprobe some modules but we'll see about that later if necessary :)

Assuming you have wireless internet :

Now you will need to configure some security settings. One which is very easy is mac-filtering. You can do this in your router and you don't have to do anything on your pc (wireless) settings.

You can additionally use WEP if you decide to use WEP you need to configure this on your router and in system->administration->networking.

Instead of WEP you can use WPA(2). Which is harder to setup. If you decide to do this then here's a guide :
[http://www.ubuntuforums.org/showthread.php?t=202834](http://www.ubuntuforums.org/showthread.php?t=202834)

---

