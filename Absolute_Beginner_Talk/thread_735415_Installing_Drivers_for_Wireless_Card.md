---
title: "Installing Drivers for Wireless Card"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by m60dude5 on 2008-03-25
Hi.I have been trying to install ndiswrapper to no avail for several days. So I gave up and looked on the cd that came with my wireless card. There is a folder in there that says Linux Debian. So I opened it, and see a tar.gz folder with a bunch of .bin, .dat files. I have no clue what these are or how I should put them in the drivers folder. I have a Ralink Wireless Card. Thanks for any help.

---

### Post by jan quark on 2008-03-25
is there no install readme file in this folder?

it would be good to know the exact content of the folder

can you navigate in terminal into that folder using the cd command
so for instance
```

cd /media/cdrom/folder
```

and run the command
```

ls -a
```

to list all files in this folder
then post the out put here

if there is a bin executable you can execute it by running it through the terminal
```

/path/to/file.bin
```

perhaps you must make it executable with
```
sudo chmod a+x /path/to/file.bin
```

---

### Post by stchman on 2008-03-25
> **m60dude5 said:**
> Hi.I have been trying to install ndiswrapper to no avail for several days. So I gave up and looked on the cd that came with my wireless card. There is a folder in there that says Linux Debian. So I opened it, and see a tar.gz folder with a bunch of .bin, .dat files. I have no clue what these are or how I should put them in the drivers folder. I have a Ralink Wireless Card. Thanks for any help.

Give us an lspci output.  We need to know what kind of chipset your wireless card has.  Ralink may use many different chipsets in that wireless model.

---

### Post by m60dude5 on 2008-03-25
I got it. Thanks though. I managed to click some things and suddenly my connection worked!:popcorn:
Thanks.

---

### Post by jan quark on 2008-03-25
lucky you :)

---

### Post by m60dude5 on 2008-03-26
I know. :guitar: I heard so many things about Wireless cards in Ubuntu. I know this is luck. Trust me I was quite happy.

---

### Post by forrestcupp on 2008-03-26
Tell us what things you just clicked on to get it to work.  Maybe someone will have the same problem sometime and your solution will help them.

---

### Post by m60dude5 on 2008-03-26
Sorry about that, I probably should have said that. Anyway. I clicked on the network symbol up in the right hand corner and chose Connect to another network like I had done before. I then clicked on my other computer with the internet connection to broadcast the SSID. As soon as I did, I was connected. So for anyone looking for a solution here are some things I've learned in my last week atempting to get my WiFi to work.

First, make sure the wireless card is recognized by clicking System, Preferences, Hardware Info. Search for your card. if it is recognized (if it is it will have its name there, such as "Ralink") then you're good. If not, check the CD for your card first. I did this last, and it actually had linux drivers. If it doesn't, use ndiswrapper to install the windows drivers (do this if your card wasn't recognized in the hardware info as well)

If it is recognized, try entering the SSID and keyphrase again. If this doesn't work, enable SSID broadcasting on the wireless router. This is what solved my problem. Then, try typing the name and pass again. 

On another note, I am now using Ubuntu as my Primary OS thanks to everyone's help here for getting me online.

The whole world is not a fence, so who needs Gates?

---

