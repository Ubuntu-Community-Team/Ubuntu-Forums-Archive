---
title: "WG511v2 Wireless PCI PC Card, Here is how to get it to work."
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by Retnuh on 2006-09-05
First off it has taken me 3 days of messing with this to figure it out. I have one friend to think, a couple of you here on the ubuntu forums, and finally this one guy called "breakthestate" here in the forums.
I am such a noob to Ubuntu and Linux. I didnt even know what a Terminal was, and no one even told me that I had to open it up and this was the place to type all these commands. A friend of mine gave me a dry run through and tried to cram all of what "breakthestate" was trying to get me to do in his tutorial he outlined for all of us. So I will be using his information as well and what worked for me to get my wireless up and running. 

This though has made me realize that there is a lot to learn with Linux, but it is fun learning and understanding what you are doing.

This will be for the Uber-Leet Noobs that have no idea on what they are doing.

I can guarantee that you will more than likely have wireless we you are done reading this thread.
Let's begin.
[B]
Three things you will need:[/B] 
Laptop running the latest Ubuntu
Netscape WG511v2 PCI PC Wireless Card
The software disc that came in the box.

Plug your wireless card into your laptop. Your green light is more than likely not lit up. 


Okay, so lets get the two files that we will need from the Netscape CD onto our Desktop.

1. Go to Places on the top toolbar
2. Go to the CD Drive 
3. Open up the Driver Folder
4. Open up the Windows XP Folder
5. Right click on each of these files and copy and paste them to the Desktop: the WG511v2.INF and the WG511v2.sys files

Okay, so we have both files that we need on our Desktop. 


Now let's open the terminal, this is what we are going to type commands into to install a few things.

1. Go to Applications
2. Go to Accessories and down to Terminal


Notice you should see your name then a ~$ at the end of it. This is the command line. The ~ signifies that you are in the Home Directory.

Now we need to Unload something called a Prism54. I believe this was a driver that is supposed to be used for our card through linux, but it doesnt work. If I am wrong about that, it doesnt matter (remember, I have only had 3 days of Linux/Ubuntu experience, LOL)

Type this into your Terminal, just like you see it below. If you get an error, then you need to make sure you added sudo. Also you will need to type your password when it prompts you to, this password is your username pass.
This will install "ndiswrapper"
```
sudo apt-get update
```
```
sudo apt-get install ndiswrapper-utils
```

Now we need to install the two files we put on the Desktop.
Type what you see below.
```
cd Desktop
```
```
sudo ndiswrapper -i WG511v2.INF
```
```
sudo ndiswrapper -i WG511v2.sys
```
****Note that you must type the file name exactly how it appears on your Desktop.

Now type this:
```
sudo ndiswrapper -l
```
-l means list and -i from above means install

You should see something like this now
```
Installed ndis drivers:
 wg511v2   driver present, hardware present
```

If you see that the .sys driver says "Invalid Driver", dont worry about this. This is what worked for me.

Now type this into your terminal
```
dmesg[CODE]

You should see something like this in the Terminal,but it does not need to say exactly what this does
[CODE][4298557.630000] ndiswrapper version 1.1 loaded (preempt=no,smp=no)
 [4298557.760000] ndiswrapper: driver 2802w (SMC,04/29/2004, 3.0.11.1) loaded
 [4298557.771000] PCI: Enabling device 0000:07:00.0 (0000 -> 0002)
 [4298557.771000] ACPI: PCI Interrupt 0000:07:00.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
 [4298557.772000] ndiswrapper: using irq 10
 [4298561.706000] wlan0: ndiswrapper ethernet device xx:xx:xx:xx:xx:xx using driver 2802w, configuration file 1260:3890.5.conf
 [4298561.706000] wlan0: encryption modes supported: WEP, WPA with TKIP, WPA with AES/CCMP
```

Okay, now your Netgear card is blinking with the green light.
You do not have wireless just yet.
You need to go to System --> Administraion --> Networking
You will notice that your wireless device is there.
click on it once and make sure that the Default gateway device is wlan0
Now click on Properties
Find your router name in the Network Name (ESSID)

That is it, you are good to go now.
Enjoy your wireless connection.

---

### Post by djinni on 2006-09-13
These instructions helped me get going up to a point.

Some things I did differently:
I'm running Xubuntu 6.06 on a Toshiba Satellite 2755XDVD with 192M RAM.  I don't know if the difference was the Toshiba or the Xubuntu.

First I downloaded the new updated driver for my Win98 partition from netgear.  [[http://kbserver.netgear.com/release_notes/D102813.asp]](http://kbserver.netgear.com/release_notes/D102813.asp])

After that was installed, I was able to pull up the .inf and .sys file from the harddrive.  I copied the files onto a memory stick.

With those files, I was able to follow the instructions almost to the end.  I could get ndiswrapper to list the wg511v2 driver and hardware.  but dmesg didn't give me anything.

From another forum, I found these instructions:
#sudo ndiswrapper -i /netgear.drv/WG511v2.INF
#sudo ndiswrapper -m
#sudo modprobe ndiswrapper

I skipped the first line and typed in the next two commands.  That finally gave me the green LED to light up on the card.

I then went to Applications:System:Networking on the GUI.  The wireless network connection showed up and I set the properties for the hotspot I'm sitting in.

It's still not perfect though.  Like today, I couldn't get it to boot a few times.  It hung at the boot sequence with the yellow activity LED flashing.  After some tries in safe mode, it came up, and said the wlan0 was active, but internet didn't work.  (Though I wonder if that isn't because of the trying GAIM before going through the web to set the WiFi cookie).  After another couple of reboot tries, I disconnected the card, and it booted up just fine.  I then plugged in the card and it connected through.

---

### Post by Timothy Butwinick on 2006-09-13
This is why I like Linux: Things work sooner or later! XP freezes when I plug WG511v2 in, and I have waited for three days to get help from the support.

---

### Post by Timothy Butwinick on 2006-09-13
djinni: You have to configure it under System > Administration > Networking.
Selact WG511v2, click Properties and configure any encryption you might have. Then click the Activate button. It should work after a reboot.

I have got the startup issue too, but I don't know how to fix it.

---

### Post by djinni on 2006-09-14
i can go through applications:system:networking and the wlan0 shows up.  i configure and get on.

the current problem is getting it to boot in place.  when i boot with the card installed, it goes through the boot sequence up to pcmcia hardware.  at that point, it spits out a lot of text, starting with [numbers] and code.  the last line is something about preempt and fail.  then it just hangs with a cursor.

i do note that the green led on the card is on and flashing.  another time it was on steady and the yellow transmit led was flashing.  but in both cases, it hung and didn't get farther in the boot sequence.

right now what seems to work is to pop out the card, boot up to gnome, then plug in the card.  then if necessary go to applications:system:networking to configure for the network.

one thing i didn't mention, i'd used some other posting about blacklisting the mrv8k.  in a terminal, i went to /etc/modprobe.d.  i vi'd the file blacklist.  and added a line at the end: blacklist mrv8k.  that stopped some error messages.

i still don't understand what is modprobe and how it worked with ndiswrapper.

---

### Post by train2335 on 2006-09-17
Thank god I found this thread, I have been looking everywhere on the net for help with this. I will test it out tomorrow and hopefully get it working. I am installing Ubuntu for a friend, and he needs wireless internet or he won't be too happy :p

EDIT: does anyone know where I can find the right files to do this, my friend has his CD but I can't get ahold of him:frown:

---

### Post by djinni on 2006-09-19
train2335, which files are you looking for?

the linux files are on the xubuntu install cd.

if you need the driver for the netgear wifi card, you can go to the netgear website [[http://kbserver.netgear.com/release_notes/D102813.asp]](http://kbserver.netgear.com/release_notes/D102813.asp]), download the windows driver and install them. then in windows, search for the .inf and .sys files.

good luck

---

