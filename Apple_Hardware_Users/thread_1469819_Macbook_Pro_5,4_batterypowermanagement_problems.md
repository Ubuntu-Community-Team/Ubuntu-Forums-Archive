---
title: "Macbook Pro 5,4 battery/powermanagement problems"
date: 2010-05-02
forum: Apple Hardware Users
---

### Post by unixninja92 on 2010-05-02
I am having several problems with what i believe to be gnome-power-management. Power management will randomly say that either i do, or don't have a battery. This means that the icon in the notification area does not appear, and I can not access the settings for on battery power. also, when i tell Ubuntu to suspend, it just goes to the screensaver and nothing happens. conky is still able to read the battery just fine, its power management thats having problems.

---

### Post by paulinchen on 2010-05-02
Same for me with a macbook pro 5.5. Randomly showing the battery when I'm coming from osx.

---

### Post by benzolchemie on 2010-05-03
Hey there,

I'm running Lucid on a MBP 5,5 with rEFIt and I am having the exact same issue. I only experience the problem when I start up my Mac WITHOUT the power cord attached - when running on AC, the machine behaves correctly. Yet, the gconf-editor shows the correct power management specs even when the different tabs in the power management settings are missing.

Greetings,

Dennis

---

### Post by paulinchen on 2010-05-04
Its definitely a problem with the gnome-power-manager, cause even in the powercontrol of docky and cairo-dock you can see the battery.
Funny as well that, when I plug-off the ac-power the brightness gets lowered, as I set it up, when running on battery. 


I found this in the log-file of  "gnome-power-manager --verbose 2>&1" .Maybe it's useless cause I'm not that expert, but who knows ...
```
(gnome-power-manager:5841): devkit-power-gobject-WARNING **: Error invoking GetAll() to get properties: Message did not receive a reply (timeout by message bus)
```

---

### Post by unixninja92 on 2010-05-04
> **paulinchen said:**
> Funny as well that, when I plug-off the ac-power the brightness gets lowered, as I set it up, when running on battery. 

I have that problem too. Every now and then it works right, but most of the time it dims way too much, and there does not appear to be away to change it. I tried messing with the pommed config file, and that worked for a little bit, but its messing up again now.

---

### Post by x00r on 2010-05-05
Same problem for me. MacBook Pro 5.5 and Ubuntu 10.04 :(

---

### Post by alexmurray on 2010-05-05
Check under Power Management in Preferences menu to see if it says to show the icon all the time or only when charging / discharging.

---

### Post by paulinchen on 2010-05-05
Thats definitly not the solution ...

---

### Post by unixninja92 on 2010-05-05
paulinchen is right. I have mine set for showing when a battery is detected.

---

### Post by x00r on 2010-05-06
The icon does not matter at all.

If i start the MBP without the power cord attached, it behaves like a desktop... If I close the lid, nothing happens. Power manager does not even know it should have a battery...

---

### Post by ercoppa on 2010-05-06
Can someone open a bug on launchpad? I am under gentoo and have the same issues (but GNOME 2.30 isn't in *gentoo repo* so I can't open a bug in my distro).

Greets, ercoppa.

---

### Post by Calash on 2010-05-06
Similar issue here.  I have not tried starting with it unplugged so I can not comment but after starting it plugged in the default power management does not even show a battery is there.

Worse, if the battery runs out it does not detect and just shuts off.  Real bad in the middle of an update.


I have to reload my g4 tonight but after that I can get some info for the bug report.

---

### Post by paulinchen on 2010-05-06
There is ...

[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/555585](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/555585)

---

### Post by WildMagic on 2010-05-07
I'm having the same problem on my 13" MacbookPro5,5 with Lucid Lynx. Everything worked well earlier.

Does anyone have a solution yet?

[The bug report mentioned in the previous post will be deleted soon, says  the page.]

---

### Post by flying_mule on 2010-05-13
> **WildMagic said:**
> I'm having the same problem on my 13" MacbookPro5,5 with Lucid Lynx. Everything worked well earlier.

Does anyone have a solution yet?

[The bug report mentioned in the previous post will be deleted soon, says  the page.]

Same here. Although everything was running ok (with 10.04) until I updated (through update manager). After updating gnome lost the battery status data.

---

### Post by paulinchen on 2010-05-15
I can't believe none of the "professionals" in this forum has this kind of issue, or knows a fix.

Where are you community? We need help and not another post, that this affects me too...

---

### Post by alexmurray on 2010-05-16
The problem appears to be upowerd crashing, which in turn is caused by a [bug in libusb]("https://bugs.launchpad.net/ubuntu/+source/libusb/+bug/427805") - also [occurs in Fedora]("https://bugzilla.redhat.com/show_bug.cgi?id=580570") as well.. No solution yet, except there is [some evidence]("https://bugs.launchpad.net/ubuntu/+source/upower/+bug/526895/comments/8") that replacing libusb-0.1 with a hand-compiled version of libusb-compat-0.1 can fix it.

---

### Post by ace55 on 2010-05-18
> **alexmurray said:**
> The problem appears to be upowerd crashing, which in turn is caused by a [bug in libusb]("https://bugs.launchpad.net/ubuntu/+source/libusb/+bug/427805") - also [occurs in Fedora]("https://bugzilla.redhat.com/show_bug.cgi?id=580570") as well.. No solution yet, except there is [some evidence]("https://bugs.launchpad.net/ubuntu/+source/upower/+bug/526895/comments/8") that replacing libusb-0.1 with a hand-compiled version of libusb-compat-0.1 can fix it.

I can confirm this solution works, at least on 10.04 x64. Suspend now works, and the battery status is displayed properly even when cold booting the system from battery. 

Steps to implement this fix:

Install libusb-1.0-0-dev in Synaptic. This is needed to compile libusb-compat. Do not uninstall libusb-0.1-4.

Download the latest version (0.1.3) of libusb compat from [http://sourceforge.net/projects/libusb/files/libusb-compat-0.1/](http://sourceforge.net/projects/libusb/files/libusb-compat-0.1/)

./configure, make, make install

Libraries will be installed into /usr/local/

Copy the following binaries from usr/local:

libusb-0.1.so.4 to /lib/libusb-0.1.so.4
libusb-0.1.so.4.4.4 to /lib/libusb-0.1.so.4.4.4

libusb-0.1.so.4 to /usr/lib/libusb-0.1.so.4

Again, this fix worked perfectly for me, but you of course apply this fix at your own risk. Screw it up and you could screw up your system - make sure any important files are backed up before you attempt this fix.

Hope this helps.

---

### Post by alexmurray on 2010-05-18
Looks like [upstream upower]("http://cgit.freedesktop.org/DeviceKit/upower/commit/?id=2b826a316954eec9951b9bf98b853560cfd70828") has just replaced the libusb-0.1 API with the new libusb-1.0 API so this should also fix upower from crashing when this lands in Ubuntu (probably won't be till Maverick though...). In the meantime I plan to try and debug this still with the libusb-0.1 API to see if it can be fixed in Lucid still but havent got much time at the moment plus I'm having trouble reproducing this on my MBP5,1

---

### Post by somethingkindawierd on 2010-05-18
I [had the same problem]("http://www.ubuntuproductivity.com/journal/tips/05/2010/battery-always-0-in-ubuntu-10-04/") and simply added the command 'upower' to my startup items...fixed the problem permanently on my Macbook 2,1.

[IMG]http://www.ubuntuproductivity.com/journal/wp-content/uploads/2010/05/Selection_001.png[/IMG]

---

### Post by breimer273 on 2010-05-19
> **ace55 said:**
> I can confirm this solution works, at least on 10.04 x64. Suspend now works, and the battery status is displayed properly even when cold booting the system from battery. 

Steps to implement this fix:

Install libusb-1.0-0-dev in Synaptic. This is needed to compile libusb-compat. Do not uninstall libusb-0.1-4.

Download the latest version (0.1.3) of libusb compat from [http://sourceforge.net/projects/libusb/files/libusb-compat-0.1/](http://sourceforge.net/projects/libusb/files/libusb-compat-0.1/)

./configure, make, make install

Libraries will be installed into /usr/local/

Copy the following binaries from usr/local:

libusb-0.1.so.4 to /lib/libusb-0.1.so.4
libusb-0.1.so.4.4.4 to /lib/libusb-0.1.so.4.4.4

libusb-0.1.so.4 to /usr/lib/libusb-0.1.so.4

Again, this fix worked perfectly for me, but you of course apply this fix at your own risk. Screw it up and you could screw up your system - make sure any important files are backed up before you attempt this fix.

Hope this helps.

Just thought that I would add that this worked like a charm "somethingkindawierd"'s method did not work for me. Maybe this info can help with the production of the bug fix or at least help narrow it down. I am using a MBP 5.5 with lucid and all current updates.

---

### Post by somethingkindawierd on 2010-05-22
The fix I posted earlier stopped working. The other fix on this thread about libusb also did not work for me on my MacBook 2,1 running 32 bit Ubuntu. So I investigated further. Then I came across this article at Apple: [http://support.apple.com/kb/HT3964?viewlocale=en_US]("http://support.apple.com/kb/HT3964?viewlocale=en_US")

I reset the System Management Controller and now my battery is working fine without any fix or hack.

---

### Post by tenuki on 2010-05-23
The solution posted by ace55 worked great for me too (Macbook 5,4, 10.04 x64). Thanks guys.

Now I just need to get the isight camera working consistently...

---

### Post by x00r on 2010-05-23
Thank you for the how to!
Here are the commands i have used:

```

sudo su
apt-get install build-essential
cd /usr/src
wget http://downloads.sourceforge.net/project/libusb/libusb-compat-0.1/libusb-compat-0.1.3/libusb-compat-0.1.3.tar.bz2?use_mirror=netcologne
tar xvjpf libusb-compat-0.1.3.tar.bz2
cd libusb-compat-0.1.3
./configure
make
make install
cp /usr/local/lib/* /lib
shutdown -r now

```(worked for me on MBP 5.5 with Ubuntu 10.04)

---

### Post by captwiggum on 2010-05-25
I have mbp 5,5 and have the same trouble, and same error from gnome-power-manager, "devkit-power-gobject-WARNING"  

This bug is related:
"Power Management Applet doesn't show concerned tabs in some particular conditions"
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/520020](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/520020)

For me, the devkit-power pkg mentioned in this bug is missing from my install.

---

### Post by x00r on 2010-05-25
Hi [captwiggum]("http://ubuntuforums.org/member.php?u=822425"),

I do not think these 2 bugs are related. But if you have the opposite problem on the smae macbook as i have, then run the code above. It will resolve it.

The problems we are facing on the MBs is that you do not have a battery tab if you power up your notebook without the power cord attached (plugged in).
But if you power up the notebook with the power cord connected, you can use the battery tab also if you disconnect from power source.

If this is your problem, use the instructions above.

---

### Post by NiñoScript on 2010-06-10
When I run "./configure" it says: 
```
checking for LIBUSB_1_0... configure: error: Package requirements (libusb-1.0 >= 0.9.1) were not met:

No package 'libusb-1.0' found
```

I tried running apt-get install libusb-1.0, but it says it's already installed :\

---

### Post by x00r on 2010-06-11
apt-get install libusb-1.0-0 libusb-dev

---

### Post by bademeister on 2010-09-02
Hi,

ace55's solution seems to work for me too, thank you so much!

cheers Paul

---

