---
title: "3 USB Modem driver"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by tobyimages on 2008-02-27
Hi i'm a total newbie and have just installed Debian, I cant connect to the internet though as i have a Huawei E220 usb modem and no idea how to get it installed. I've download a Vodafone mobile connect driver for Linux but i cant figure out how to install it into the Gdebi package manager. It says thats it is either corrupt or i do not have permission. I dont think its corrupt.
 I've also tried to use a deb file and that informs me that there is a dependency error with Python etc.

I know it is my lack of knowledge that is to blame but can anyone help me get on line. Thanks

---

### Post by pedro_orange on 2008-02-27
For a start; exact error messages help immensely compared to "It didn't like my face" :)

> It says thats it is either corrupt or i do not have permission. I dont think its corrupt.

Are you attempting to run it as root/su?

There should be adequate documentation that tells you how to install it within the package you downloaded.

If you're missing dependencies, google them, download them, install them. Then you've satisfied that dependency.

---

### Post by tobyimages on 2008-02-27
Hi the file i'm attempting to run is called vodafone-mobile-connect-card-driver-for-linux-20080104-installer.run
It doesnt have an installation guide with it.
I was attempting to run it with the gdebi package installer and it says that the file is either corrupt or i dont have the correct permissions. I'll give you the full error if it helps but i'm in my windows partition. I assume that i have to set it up so i have these permissions but i dont know what i'm doing really at the moment.
Thanks for your help :)

---

### Post by pedro_orange on 2008-02-27
Have you tried opening terminal, moving into the folder that contains the file and just going

```
./vodafone-mobile-connect-card-driver-for-linux-20080104-installer.run
```

or 

```
sudo ./vodafone-mobile-connect-card-driver-for-linux-20080104-installer.run
```

---

### Post by kaivalagi on 2008-03-01
Might be worth giving the attached file a try?

I setup my dad with a little wvdial script and some links to it, it works for the three network with their usb mode, which I think is the same type as vodafone.

You can either copy the files over manually to the correct locations, or use the install.sh script to put them there for you. Read the README file in the gz for more details.

Basically the following get installed:

/etc/wvdial-huawei.conf
/usr/bin/3g-on.sh
/usr/bin/3g-off.sh
/usr/share/pixmaps/3g-on.png
/usr/share/pixmaps/3g-off.png
/usr/share/applications/3g-on.desktop (In file manager will show as 3G On)
/usr/share/applications/3g-off.desktop (In file manager will show as 3G Off)

Cheers, 
Mark

---

### Post by tobyimages on 2008-03-27
Thats great it is a 3 usb modem anyway. How to i unpack it to the correct locations, at the moment it unpacks on to my desktop?

Thanks!

---

### Post by pedro_orange on 2008-03-27
A .tar.gz is a compressed/zipped file. Like WinZip does on Windows.
It doesn't matter where you unpack this compressed file to. It's whats inside the unpacked folder (ie. the .sh) you want

---

### Post by tobyimages on 2008-03-27
I shall fiddle about with that. 
With regards to the Vodafone driver, i installed all dependencies (manually as i dont have internet connection)  including Python 2.5  and still says that it depends on Python 2.5 to install even though it has been installed. 
Any other reasons for giving up and going back to Windows?

---

### Post by kaivalagi on 2008-03-27
tobyimages, I've updated the gz file above to include an install script instead to make things easier. 

Just download the new file and extract it, read and follow the README instructions and you should be well on your way. 

The install script needs to be run as root (sudo) as it basically copies the required files to the proper places and ensures they have the correct permissions set against them for them to work.

There is also an uninstall.sh in case you want to remove them again

Hope that helps

Cheers

---

### Post by tobyimages on 2008-03-27
Great thanks for that, i've installed it ok. I clicked on the 3g on in the menu and nothing happens except the spinning of the curse for a few seconds, the light on the modem does'nt come on so i presume its not connected. I have wvdail installed, i guess i need to do something else?

Thanks

---

### Post by kaivalagi on 2008-03-27
Can you try running what is inside the 3g-on.sh file in the console, so we can see what is up?

Run this:

```
wvdial --config=/etc/wvdial-huawei.conf
```

Maybe your usb modem isn't /dev/ttyUSB0?

---

### Post by kaivalagi on 2008-03-27
It wouldn't hurt to run the following, just so we know what you've got:

```
ls -la /dev/ttyU* 
```

If it doesn't find a device you may want to reboot with the usb modem connected to your PC, it may find it on boot up...it will mean however you need to have the modem connected to the PC before you turn it on each time for it to work...

Also, this thread ([http://ubuntuforums.org/showthread.php?t=633981]("http://ubuntuforums.org/showthread.php?t=633981")) has example .conf file contents for different networks, maybe you could try changing some of the settings in /etc/wvdial-huawei.conf if you still don't get anywhere

As the configuration I posted has only been tested with one network provider (three), I would think if you have an alternative network provider modem, some changes to the conf file will be required...

Have a look around all of the forum posts on "huawei 220 wvdial", you should find plenty of things to try out. 

I don't think I can provide any more help on this, as without being able to test your configuration I'm in the dark....However there are people out there who I am sure can help you further as they'll have been through the same issues.

Hope that helps

---

### Post by JimmyI on 2008-05-14
> **kaivalagi said:**
> Might be worth giving the attached file a try?

I setup my dad with a little wvdial script and some links to it, it works for the three network with their usb mode, which I think is the same type as vodafone.

You can either copy the files over manually to the correct locations, or use the install.sh script to put them there for you. Read the README file in the gz for more details.

Basically the following get installed:

/etc/wvdial-huawei.conf
/usr/bin/3g-on.sh
/usr/bin/3g-off.sh
/usr/share/pixmaps/3g-on.png
/usr/share/pixmaps/3g-off.png
/usr/share/applications/3g-on.desktop (In file manager will show as 3G On)
/usr/share/applications/3g-off.desktop (In file manager will show as 3G Off)

Cheers, 
Mark

Hi,

I'm using a different modem that 3 uses. It's the ZTE MF622. At the moment I can only log onto the web once by running wvdial. If the connection goes off then I have to reboot to be able to dial again. Does your tar.gz file provide a way to turn off the modem and then redial again? 

The setup for the ZTE seems to be pritty similar to the Huawei. Hopefully this script will work with it.

James

---

### Post by kaivalagi on 2008-05-14
> **JimmyI said:**
> Hi,

I'm using a different modem that 3 uses. It's the ZTE MF622. At the moment I can only log onto the web once by running wvdial. If the connection goes off then I have to reboot to be able to dial again. Does your tar.gz file provide a way to turn off the modem and then redial again? 

The setup for the ZTE seems to be pritty similar to the Huawei. Hopefully this script will work with it.

James

Not really, the off option just runs the following:

```
killall wvdial
```

I am sure there is a way to get your modem reconnected without a reboot, only windows needs reboots for any change...

There's no guarantee that this script works with your modem, but if it doesn't it will most likely be down to the wvdial conf file settings needing a tweak.

I don't think I'll be able to help with any of that...I don't even have a 3g modem myself, I knocked this stuff up for my old man :)

Good luck

---

### Post by JimmyI on 2008-05-22
Thanks I'll try that command later tonight hopefully that'll solve the reboot issues.

Jim

---

