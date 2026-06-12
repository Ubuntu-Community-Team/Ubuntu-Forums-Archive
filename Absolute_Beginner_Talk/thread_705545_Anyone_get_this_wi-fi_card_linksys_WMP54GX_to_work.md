---
title: "Anyone get this wi-fi card: linksys WMP54GX to work?"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by iBuntuKnow on 2008-02-23
Anybody actually get it to work with/in Ubuntu?

I'm having a devil of a time myself and would appreciate some advice or answers...

its this one in particular:

[http://www.hitecempire.com/catalog/images/Linksys_WMP54GX.jpg](http://www.hitecempire.com/catalog/images/Linksys_WMP54GX.jpg)

someone out there got it to work damnit, I just know it lol

---

### Post by Squish on 2008-02-23
bump
Anyone at all?

---

### Post by iBuntuKnow on 2008-02-23
bump


come on someone?

---

### Post by anewguy on 2008-02-23
A Yahoo! search with Ubuntu and linksys WMP54GX yielded several things to look at.  One was a list from sourceforge that I think is saying what driver to use with ndiswrapper to make a particular card work.  In this case, the relevant entry is:

  - Card: Linksys WMP54GX
    * Chipset: Airgo networks Inc unknown device 0001
    * pciid: 17cb:0001
    * Driver (linksys): use the driver found on the linksys website at [http://www.linksys.com/servlet/Satellite?blobcol=urldata&blobheadername1=Content-Type&blobheadername2=Content-Disposition&blobheadervalue1=application%2Fzip&blobheadervalue2=inline%3B+filename%3DWMP54GX_v10.zip&blobkey=id&blobtable=MungoBlobs&blobwhere=1129216876336&ssbinary=true](http://www.linksys.com/servlet/Satellite?blobcol=urldata&blobheadername1=Content-Type&blobheadername2=Content-Disposition&blobheadervalue1=application%2Fzip&blobheadervalue2=inline%3B+filename%3DWMP54GX_v10.zip&blobkey=id&blobtable=MungoBlobs&blobwhere=1129216876336&ssbinary=true)

I have not looked at that yet, as I don't use that model.  However, if you extract the .sys and .inf files from it, you can then use ndiswrapper to install the driver and get things working.

Try doing the download first and looking at what is in it.  Then post back here and we'll go from there.  :)

---

### Post by iBuntuKnow on 2008-02-24
alright...when i try to install ndiswrapper it doesnt work and i get the following:

unpacking replacement ndiswrapper-utils-1.9...
setting up bcm43xx-fwccutter (--configure):
Error parsing proxy url [http://:8080/:](http://:8080/:) invalid host name.
dpkg: error processing bcm43xx-fwcutter (--configure):
 subprocess post-installation script returned error exit status 1
setting up ndiswrapper-common (1.43-lubuntu2) ...
setting up ndiswrapper-utils-1.9 (1.43-lubuntu2) ...
errors were encountered while processing:
 bcm43xx-fwcutter
e: sub-process /usr/bin/dpkg returned an error code (1)

...and a couple more things i dont feel like typing, but it basically repeats itself


any idea what that means?


in fact a lot of things (commands) i try in the terminal or stuff i install bring back nothing but errors...

---

### Post by iBuntuKnow on 2008-02-24
bump

---

### Post by anewguy on 2008-02-24
Did you try ndiswrapper -l and it failed, and that's why you tried to install it?  What package did you use to try to install it?  I would normally go through synaptic package manager (System/Administration/Synaptic Package Manager).

Have you tried ndiswrapper -l since your messed up install?

We'll go from there once I know those answers.  :)

---

### Post by Aeph on 2008-02-24
Does your card have an install CD that came with it?

---

### Post by iBuntuKnow on 2008-02-24
yeah actually...I went through the package manager and checked both ndiswrapper "files" and hit apply...then when it didnt seem to work, (or when i got error messages) i typed ndiswrapper -l...but I dont really remember what it said...gotta give me a sec, I'll have to boot up ubuntu and do it again


plus i just woke up ;)

---

### Post by iBuntuKnow on 2008-02-24
ok i get this:


netani : invalid driver!


which i assume has something to do with the linksys driver i tried to install

---

### Post by anewguy on 2008-02-24
Okay, it appears that ndiswrapper at least runs - that's critical.

Now, we need to go back to a "clean slate" as far as drivers it knows.  So, open a terminal window and do the following:

sudo ndiswrapper -r netani

That will remove the "bad" driver.

Next, either look on  the CD that came with the device or look up at linksys and get the Windows drivers.  I believe for you device that will include a .sys file, a .inf file and a .bin file.  Copy these files to your desktop then post back here for the next step.

I want to take this a step at a time so any errors will be isolated.

Thanks! :)

---

### Post by Aeph on 2008-02-24
This is a step-by-step process that should get you what you need. Its basically what I do every time I reinstall Linux. I use a different wireless card, but it should work as long as you have Gutsy.

1. If you haven't install Build Essential.
2. Assuming you do not have internet access on the machine you are trying to set up, you will need to download the Ndiswrapper source code and extract it to your Linux desktop.
3. Enter the following code into the terminal:

cd ~/Desktop/ndiswrapper-1.51 (or whatever version you are using. It will be the name of the folder)
sudo make uninstall (the terminal will have instructions to repeat this until it stops displaying something. Do what it says, I had to do it twice)
make
sudo make install
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist

4. This is where you need the install CD. Get the .inf and .sys files from wherever they are and copy them to the desktop. You will also either want to restart the terminal or enter "cd" (without the quotes) to get out of the ndiswrapper directory.
5. Enter the following code into the terminal:

sudo ndiswrapper -i ~/Desktop/***.inf (enter the name of the .inf file that you copied to the desktop in place of the ***)
sudo ndiswrapper -m
sudo modprobe ndiswrapper
sudo gedit /etc/modules

6. This will open a text file. Add the line "ndiswrapper" (again, without the quotes) at it's end.
7. Restart your computer.
When your computer restarts, simply enter whatever information you need to connect to your internet connection. Then open up Firefox and see if it worked. Tell me if it doesn't.

---

### Post by iBuntuKnow on 2008-02-24
alright fellas, I'll try em both and post back

---

### Post by iBuntuKnow on 2008-02-24
anewguy:


tried the "sudo ndiswrapper -r netani" command


got this error:

sudo: ndiswrapper: command not found


Aeph:


downloaded ndiswrapper-source file, put it on desktop...and then installed Build Essential...

but after entering the command "sudo make uninstall", I get this:


make: *** No rule to make target `uninstall'.  Stop.

any ideas?

---

### Post by Aeph on 2008-02-24
> **Aeph said:**
> sudo ndiswrapper -i ~/Desktop/***.inf (enter the name of the .inf file that you copied to the desktop in place of the ***)

I think you literally typed in sudo ndiswrapper -i ~/Desktop/***.inf
The *** in the ***.inf is just a sort of "insert applicable text here" What you want to do is replace the *** with the name of the .inf file you copied from the CD onto your desktop.

For example, the .inf file for my wireless card is called bcmwl5.inf
Therefore I open the terminal and type sudo ndiswrapper -i ~/Desktop/bcmwl5.inf

---

### Post by iBuntuKnow on 2008-02-24
actually this is what i typed:

sudo ndiswrapper -i ~/Desktop/ndiswrapper-1.8/netani.inf

the "/ndiswrapper-1.8" is the folder name and the "/netani.inf" is my cards drivers

---

### Post by iBuntuKnow on 2008-02-24
btw i put the wi-fi card drivers in the same folder as the ndiswrapper...since it was on the desktop...so they're both in the same place

which is the/ndiswrapper-1.8 folder

---

### Post by aktiwers on 2008-02-24
Got it working easy using this guide!
[http://hehe2.net/linuxhumor/howto-linksys-wmp54g-pci-wireless-adapter-on-ubuntu-gutsy/](http://hehe2.net/linuxhumor/howto-linksys-wmp54g-pci-wireless-adapter-on-ubuntu-gutsy/)

The download link in step 1 doesnt work, so here is a working one:
[http://network.free-driver-download.com/Linksys/28375/Linksys-WMP54G-v4-Wireless-G-PCI-Adapter-Driver-2.2.7.0.html](http://network.free-driver-download.com/Linksys/28375/Linksys-WMP54G-v4-Wireless-G-PCI-Adapter-Driver-2.2.7.0.html)

Step 3 can be done easyer if you connect a network cable, go to synaptics (System => Administration => Synaptics) and search for: ndiswrapper

And install the packages.

In step 8, you could use gedit instead of nano. Gedit is graphical while Nano is terminal based text editor.

Simply replace "nano" with "gedit" in the 2 commands, like this:
```
 sudo gedit /etc/modprobe.d/blacklist
```

and add the 3 lines the guide says, and again the other command in step 8 :
```
 sudo gedit /etc/modules
```

and add "ndiswrapper" as the guide says.

Now it should work! :)

---

### Post by Aeph on 2008-02-24
Do you have the netani.sys file in the ndiswrapper-1.8 directory with the .inf file? You don't have to do anything with the .sys file it still has to be there.

---

### Post by iBuntuKnow on 2008-02-24
will try it, thanks

EDIT: the link you gave me for the driver doesnt work...but i think the one i have might work...

either way, i'll be back ;)

---

### Post by aktiwers on 2008-02-24
The link works fine here? :)

---

### Post by iBuntuKnow on 2008-02-24
> **Aeph said:**
> Do you have the netani.sys file in the ndiswrapper-1.8 directory with the .inf file? You don't have to do anything with the .sys file it still has to be there.

yep, its in there...basically everythig I saw in the wi-fi drivers folder (which were like 5 things) I dragged and dropped in the ndiswrapper folder on my ubuntu desktop

---

### Post by iBuntuKnow on 2008-02-24
> **aktiwers said:**
> The link works fine here? :)

got it...browser was acting funny

---

### Post by Aeph on 2008-02-24
You could try skipping the sudo make uninstall step, in case they are already uninstalled, and just continue from "make"

Or, if can temporarily hook your PC up to your modem, you could try using the synaptic package manager to install it.

Other than that, I don't know. That tutorial was just what I have to do. If I think of anything else I'll let you know.

---

### Post by anewguy on 2008-02-26
First off, sorry for taking so long to get back here - I had deleted my bookmark.

You should know that in my experience, once you have a "bum" driver loaded via ndiswrapper, you won't be able to get things to work until you remove that driver.  My previous instruction for doing so had a type (an "r" in place of an "e").

You want to do this in terminal:

sudo ndiswrapper -e netani

then:

sudo ndiswrapper -l (lower case "L", for "list")

There should be no output from the above - if there is remove the driver as per the previous step.

Now something else I have found when using ndiswrapper:  change your default directory to the folder containing the .inf and .sys, etc., files needed for the driver prior to using ndiswrapper.  If you have the files on your desktop, you would:

cd ~/Desktop

then:

sudo ndiswrapper -i xxxxxx.inf (where xxxxxx.inf is the name of your .inf file)

You do not need to put the full path in the above, only the file name.  I have found that for some reason if I don't cd to the directory holding the files first, and instead specify a full path, that sometimes ndiswrapper doesn't find the rest of the driver files.  It will say "xxxxx" installed when you do an ndiswrapper -l, but in reality it won't work.  You always need to remove anything that shows in the ndiswrapper -l output before attempting to reload the drivers.

If you have done the blacklisting, then I assume you have also followed the ndiswrapper install command with the following:

sudo depmod -a

sudo modprobe ndiswrapper

sudo ndiswrapper -m

and finally, as super user (gksudo) edit the /etc/modules file and add ndiswrapper to the end of the file, save the file, exit, and reboot.

:)

---

### Post by sholmes555 on 2008-04-12
Hey guys, this tutorial was very helpful...i followed all the steps from both aeph and anewguy. 
i removed the older netani.inf file, and then got ndiswrapper to re-install the correct file that i placed into a directory i called linksys in my home folder, and did sudo depmod -a, modprobe ndiswrapper, and ndiswrapper -m and added ndiswrapper at the end of that file, etc etc....

so.. when i type ndiswrapper -l, i get:
netani : driver installed
              device (17CB:0001) present
my light on my antenna is on, i can see wireless networks in the area...everything seems okay except that i cannot connect to my network. we have our own passphrase or something, so i type that in using the wep-128 encryption selection and it just hangs there searching and then that same dialog box asking me for the password comes up again....after a few similar tries, i see the same thing. i also even tried selecting ASCII

i don't know what to do, can anyone provide help? Thanks! please keep all instructions as close to n00b level as you can PLEASE!! thank you very much!! :)

---

### Post by sholmes555 on 2008-04-12
****FIXED*************

Sorry guys, I tried more choices and for some reason I guess our encryption is set to Hex. I tried that, and it works! I finally have internet! Thank you so much guys!

---

### Post by Aeph on 2008-04-13
For future reference, the message:

```
make: *** No rule to make target `uninstall'. Stop.
```

means (as far as I can tell) that the location is invalid. Check your spelling and that the filepath is accurate.

---

