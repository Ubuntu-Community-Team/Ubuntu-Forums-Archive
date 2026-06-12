---
title: "cannot install SMC 2662W Wireless Adapter"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by astr0bomber on 2008-04-04
I have looked all around this site and cannot find something that answers my question. 

I have an SMC 2662W Wireless Adapter. It does not work with Linux so far. I truly have no idea how I am supposed to get the drivers on the computer, that is how noobish I am. I transferred the tar file to my Linux machine using a flash drive, but I don't know what to do from there. I cannot do ANYTHING on my computer until I get internet access on there.

I have been told to do the following:
a) untar the package using the command:
---> tar zxvf SMC_USB_WIRELESS_2662W.tar.gz
b) cd SMC_USB_WIRELESS_2662W
c) ./setup.sh

The problem with this is that its not working, and I have no idea if I'm supposed to do something else as well. Is this assuming that the file is in a certain place? The file I downloaded also isn't a .tar.gz file, it's just a .tar file. It's also got a different name.

EDIT: I got as far as the ./setup.sh part. When I press enter, it says that vnetusb-2.6.6 or something doesn't exist in a certain directory. I checked, it does not exist, but version 4.2.2 or something does exist. Could I just change the name?

---

### Post by astr0bomber on 2008-04-05
I tried renaming the file, and all I got were "access denied" warnings after "./setup.sh". Is there maybe a generic wireless adapter thing I could install somewhere? I am getting really annoyed with this.

---

### Post by mikeyphi on 2008-04-05
Could you post the full name of the file?
Also say where it is (Desktop)?

From where did you download it?

---

### Post by astr0bomber on 2008-04-05
I believe the file was called SMC_WIRELESS_2662W.tar or something like that. I cannot reference it directly because I am running Windows right now.

Yes, the file is on the desktop. 

I downloaded the file from [http://www.opendrivers.com/driver/214686/smc-smc2662w-v.2-wireless-usb-adapter-driver-linux-free-download.htm](http://www.opendrivers.com/driver/214686/smc-smc2662w-v.2-wireless-usb-adapter-driver-linux-free-download.htm)

I am pretty sure I downloaded the correct driver. My adapter is an SMC2662W V.3 CA, part  #: 99-012084-133. 

I tried to find this driver on the SMC site, but I could not find it. It won't list any drivers for Linux for this piece of hardware.

---

### Post by astr0bomber on 2008-04-05
I absolutely cannot use Ubuntu without this, I do not have access to a ethernet cord long enough to reach my router, so this is quite important for me.

---

### Post by mikeyphi on 2008-04-06
OK!
1. Open a terminal and navagate to the Desktop
2. Use the untar command (with the correct package name!) as previously
3. Not in terminal - right click on the (now untared) package and select 'Open with Archive Manager'
   Look to see if there is an 'setup.sh' or equivalent
4. Back in terminal, in Desktop, change directory to untared package (cd package name)
5. Enter the ./setup.sh (or equivalent) command

6. If you get a message (as before) re dependences - you might have to force install a previous version of the package, as required.

---

### Post by astr0bomber on 2008-04-06
For some reason, when I reference the package in any way, it says the file does not exist. See the following:

```
astrobomber@astrobomber-desktop:~$ tar zxvf SMC2662WV2_Linux.tar
tar: SMC2662WV2_Linux.tar: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
astrobomber@astrobomber-desktop:~$ cd SMC2662WV2_Linux.tar
bash: cd: SMC2662WV2_Linux.tar: No such file or directory
```

The package in question is on the desktop. I even changed the name (to SMCLinux.tar) to make sure I am not typing it in wrong.

---

### Post by mikeyphi on 2008-04-07
It's possible that changing the package name somehow caused a problem......
Perhaps you should download the package again and retry?

---

### Post by astr0bomber on 2008-04-07
> **mikeyphi said:**
> It's possible that changing the package name somehow caused a problem......
Perhaps you should download the package again and retry?

That code up there was even before I changed the package name

---

### Post by mikeyphi on 2008-04-08
Quote: I downloaded the file from [http://www.opendrivers.com/driver/21...e-download.htm](http://www.opendrivers.com/driver/21...e-download.htm) 

I was unable to confirm your package source - site not found. Is it still working for you?

If the file is on your Desktop it should work!

Please enter the following in a terminal and post the result:

cd Desktop
ls

You should see a printout of what's on your Desktop - please confirm package is listed and its name!

---

### Post by astr0bomber on 2008-04-10
Here is the printout:

```
astrobomber@astrobomber-desktop:~$ cd Desktop
astrobomber@astrobomber-desktop:~/Desktop$ ls
Neutronium-Gtk2.tar.gz  Setups  SMC Drivers  SMCLinux.tar
astrobomber@astrobomber-desktop:~/Desktop$ 

```

The Neutronium thing is something unrelated. But the .tar file is the file I downloaded from the site. For some reason, whenever I link someone to the site, they cannot access it. 

Does this help at all? (I was told to look here and see if anything was listed on another forum):

```
astrobomber@astrobomber-desktop:~/Desktop$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:off/any  Nickname:""
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   
          Retry limit:8   RTS thr=1536 B   Fragment thr=1536 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

astrobomber@astrobomber-desktop:~/Desktop$ 
```

It looks like I managed to get ndiswrapper to do *something*. I just don't know what. I was shown the following page to try:
[http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/94685-wireless-lan-linux.html#post470915](http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/94685-wireless-lan-linux.html#post470915)

I just have absolutely no idea how to make the thing work.

---

### Post by mikeyphi on 2008-04-10
OK - so the tar file is on the Desktop, are the 2 other files related? Setups and SMC Drivers?

If you Open a terminal and cd to Desktop you will be able to enter the untar code.
If you already did that - the 2 files may be the result but they don't look like your first post.

First time you've mentioned ndiswrapper?? That is in the repos and is used with your nornal windows driver.....but (I believe) you can't have both drivers installed at the same time.
So where are you at now?

---

### Post by astr0bomber on 2008-04-10
I am getting some help with this from someone else on the Linux forums too. Although I have reached an endpoint there because it is obviously not working. See the thread here: [http://www.linuxforums.org/forum/ubuntu-help/118893-smc-wireless-adapter-not-connecting.html](http://www.linuxforums.org/forum/ubuntu-help/118893-smc-wireless-adapter-not-connecting.html)

The "SMC Setup" file is my driver setup stuff from Windows that I brought over to no avail. The "Setups" folder is just a folder of .deb files and packages that I have downloaded online and had a little trouble finding, so I just keep them.

---

### Post by mikeyphi on 2008-04-11
SMC Setup - for future reference, it's the *.inf file you need from your windows driver set - if you choose to use ndiswrapper.

What do you get from the following?
Open a terminal - enter cd Desktop
then enter tar xvf SMCLinux.tar

---

### Post by mikeyphi on 2008-04-11
I've read through the other forum posts - have you tried opening System/Administration/Network - highlight 'wireless connection' select 'properties' deselect 'roaming mode' then enter the required info in the fields.

You don't have to unplug your wired connection - you can still confirm that wireless is/is not working.

---

### Post by astr0bomber on 2008-04-11
> **mikeyphi said:**
> I've read through the other forum posts - have you tried opening System/Administration/Network - highlight 'wireless connection' select 'properties' deselect 'roaming mode' then enter the required info in the fields.

You don't have to unplug your wired connection - you can still confirm that wireless is/is not working.

I tried doing all that, but I don't know most of the settings to put in there. All I know is the wireless network I would be connecting to is called "default"

---

### Post by madsmaddad on 2008-04-11
when I had problems I copied the tar file into my Home directory. As you are used to XP, then it is similar - drag and drop. 

Terminal will open up in there. I cant find my notes but I think you have to tar -xvzf filename

-- at that point I am not sure that I have put in the right letters after the minus sign, but you had them earlier. 

once you start typing the file name you can TAB to get the rest of it, if it is there. 

Usually this unpacks the files into a subdirectory - cd there and see if a setup file is there to run. 

Hope that helps get you started.

---

### Post by madsmaddad on 2008-04-11
Ignore above- somehow I think that I got into the wrong thread? 

However- if iwconfig shows a device- does dmesg (in terminal) show that the device loads? 

I installed wpa_supplicant  and configured it as per kevdogs very good wireless thread.

---

### Post by mikeyphi on 2008-04-11
> **astr0bomber said:**
> I tried doing all that, but I don't know most of the settings to put in there. All I know is the wireless network I would be connecting to is called "default"

In that case - What happens when you enter 'default' in the ESSID box?

---

### Post by astr0bomber on 2008-04-11
> **mikeyphi said:**
> In that case - What happens when you enter 'default' in the ESSID box?

Well, after entering "default" in the ESSID box, choosing "WPA Personal" for password type (even though I don't need a password to join the network) and picking "Automatic Configuration" for configuration, the taskbar icon shows no internet connection, then it looks like it's trying to connect, and then it goes back to the wired connection.

---

