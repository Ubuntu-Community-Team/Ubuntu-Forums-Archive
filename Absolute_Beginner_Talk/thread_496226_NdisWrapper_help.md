---
title: "NdisWrapper help"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by Lunatrix on 2007-07-08
well i downloaded it, burned it to a disk. and idk what to do from here? can anyone help me? thankd kause all the files are read inly fir sine reason

---

### Post by JasonL on 2007-07-08
If you are trying to use the files straight from the CD then that will be why they are read only, copy them over the the PC you are trying to get ndiswrapper working on.

---

### Post by Lunatrix on 2007-07-08
ok thanks ill try that

---

### Post by Lunatrix on 2007-07-08
that did not work, the files are still only readable files, i also extracted them.

---

### Post by JasonL on 2007-07-08
> **Lunatrix said:**
> that did not work, the files are still only readable files, i also extracted them.

Just to clarify what files are we talking about, the ndis installation files or the driver files?

---

### Post by Lunatrix on 2007-07-08
...uhm, i actually think they are driver files. kause i c a FOLDER name called driver. 

uhm can you get me the INSTALL files please? thanks.

---

### Post by splintercellguy on 2007-07-08
For installing ndiswrapper, why not sudo apt-get install ndiswrapper?

---

### Post by Lunatrix on 2007-07-08
will that work?

---

### Post by Lunatrix on 2007-07-08
nope that didnt work.

---

### Post by Lunatrix on 2007-07-08
can i still have that download link to the INSTALL FILES?

thanks

---

### Post by JasonL on 2007-07-08
There is a full guide to getting, installing and using ndiswrapper here: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Good luck.

---

### Post by Lunatrix on 2007-07-08
thanks. do you have a guide to installing beryl? i know its risky to have and i have read your warning but im willing to take the risk.

---

### Post by JasonL on 2007-07-08
I would not recommend trying beryl yet if you are new to Ubuntu, although there are guides depending on your version:

[https://help.ubuntu.com/community/BerylOnFeisty](https://help.ubuntu.com/community/BerylOnFeisty)

[https://help.ubuntu.com/community/BerylOnEdgy](https://help.ubuntu.com/community/BerylOnEdgy)

Be sure to know that beryl is not yet supported in Ubuntu so if you do hit problems you may not be able to get support.

---

### Post by Lunatrix on 2007-07-08
how do i find out if i have feisty fawn or edgy?

---

### Post by Lunatrix on 2007-07-08
thats probably the most retarded questuon in the world. i know lol but i dont know which version i have i just clicked the download button on the homepage og ubuntu.com

---

### Post by JasonL on 2007-07-08
Open up a terminal window from Applications > Accessories and type ```
cat /etc/lsb-release
```

---

### Post by Lunatrix on 2007-07-08
sorry for the trip post but i have feisty i just checked.

---

### Post by Lunatrix on 2007-07-08
theres 3 download links for the ndiswrapper thing for fiesty at the like middle of the page. do i have to download all of them?

---

### Post by JasonL on 2007-07-08
Only ndiswrapper-common and ndiswrapper-utils are the only two required packages, ndisgtk is a graphical front end in case you do not want to use the terminal to configure ndiswrapper.

---

### Post by Lunatrix on 2007-07-09
ok thanks dude.

---

### Post by JasonL on 2007-07-09
No problem, here to help anytime. Feel free to post again if you have any more problems.

---

### Post by Lunatrix on 2007-07-09
ok well i ran both of those packages and they are now installed do i just go on with the tutorial or restart my computer?

---

### Post by JasonL on 2007-07-09
You should not need to restart unless the tutorial tells you to.

---

### Post by Lunatrix on 2007-07-09
ok i have found my cared driver or w-e (i just copied the whole thing.)

its:::   00:06.0 0280: 14e4:4320 (rev 03) 

then it told me to look in a list or something like that and i kant find my driver number.

---

### Post by Azoix on 2007-07-10
[B][COLOR="Red"]Try This -- I'm at the same entry level as you appear to be at , the confusion only gets WORSE.......... this worked for me.
Ignore the reference's to wg111v? , this was written as a guide for type 1 and type 2 Netgear WG111 USB Wireless Dongles.
Use your adapter type as the name in this circumstance.[/COLOR][/B]

The Install Procedure
Open a ROOT terminal to do these commands.To access a root terminal in Debian or KDE, open any terminal window and type 'su' , then insert your root password , this will then switch to the root terminal.

Just copy and paste the commands below into the window, one after the other, pressing ENTER for each seperate command of course !!
Each command returns a list of data in the terminal window, as it downloads , unpacks and ready's each part of the module.Some will ask if you wish to do some modifications to other files during install , (modifying library files to make things work,etc.) asking for simple YES / NO answers, just type yes and enter.

[COLOR="Lime"]apt-get update
apt-get install module-assistant
apt-get prepare module-assistant [/COLOR]&#8211;[COLOR="Black"]--this command may not be necessary[/COLOR]
[COLOR="Lime"]apt-get build module-assistant[/COLOR] [COLOR="Black"]&#8211;this command may not be necessary[/COLOR]
[COLOR="Lime"]apt-get install ndiswrapper-common
apt-get install ndiswrapper-source
module-assistant build ndiswrapper
module-assistant prepare ndiswrapper
modprobe ndiswrapper
ndiswrapper -l[/COLOR] &#8211; should give no driver found result, at this point in time.

Please Note : 

This way of installing ndiswrapper DID NOT work for me on Ubuntu, but if you install ndiswrapper, and the 3 other related packages through Synaptic Package Manager, it works fine.
The GTK component , the end user GUI interface , even though it reports as installed on this laptop , doesn't see the hardware as being installed , but NDIS runs fine , and my result was it WONT RUN without this GTK installed locally.
Open Synaptic , click on search and type in ndiswrapper, this finds all the needed, and related packages, tick for install, highlight ALL four, and then click apply, then ndiswrapper will work perfectly in the terminal.

My result through trying the installing in the terminal was the application installed OK, it even installed the driver, seen with `ndiswrapper -l ` command, but `modprobe ndiswrapper ` command returned an error saying ndiswrapper application not found ??? 
So i re-installed with Synaptic, and it worked first time.

Installing Window's Driver Component

**You need to log in as ROOT first, and make the folder /usr/bin/wg111v? write enabled.
If this is where you inserted the Window's driver files
** -- use the folder name where the .inf and .sys files for your hardware are located.


[COLOR="Lime"]ndiswrapper -i[/COLOR] [COLOR="Lime"][COLOR="Red"]/usr/bin/folder/.inf file*[/COLOR][/COLOR] (i found placing the .inf and .sys file for the Windows driver into a folder named wg111v? in the /usr/bin/ directory allows easy location of the file, and it works perfectly well from here.)*Use your own folder name and the file name with .inf extension.
To work this on a LiveCD , create the folder for the Window's Drivers on the desktop and run from there.
[COLOR="Lime"]
modprobe ndiswrapper[/COLOR] &#8211; should now show installed driver if compatable, and display the hardware if present.
You can now use the inbuilt Network Tools to configure and enable the wlan0 interface you have just set-up.
You can choose to set a static or DHCP provided I.P. address , either way should work on all systems.

**[COLOR="Red"]Configuration of iwconfig in terminal[/COLOR]**

[COLOR="Lime"]iwconfig wlan0 essid &#8220; &#8220; [/COLOR] -- enter your network ID here !! WITHOUT QUOTES !!
[COLOR="Lime"]iwconfig wlan0 key open " " [/COLOR] --YOUR WEP KEY HERE  **(either set open or restricted here WITHOUT the quotes)
[COLOR="Lime"]iwconfig[/COLOR] &#8211; check if all fields are set as requested 
[COLOR="Lime"]iwconfig wlan0 commit[/COLOR] &#8211; finalises settings to the network interface.**Needs to be supported by your hardware.

Output should resemble this : 

lo        
no wireless extensions.

eth0     
 no wireless extensions.

wmaster0  
IEEE 802.11g  Frequency:2.437 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     
IEEE 802.11g  ESSID:"Azoic"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:6C:92:56:C4   
          RTS thr:off   Fragment thr=2346 B   
          Link Quality=38/64  Signal level=10/65  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

irda0     
no wireless extensions.

And i'm using WEP encryption no problem.
[COLOR="Red"][B][I][U]
**All files made write-enabled for the procedure, can now be reset to read only if desired[/U][/I][/B][/COLOR]

---

### Post by anewguy on 2007-07-10
I know things are very different from 1 machine to another but I just did some very simple things and it worked fine for me.  I found this on a Ubuntu how-to, but I'll be danged if I can find it now when I want to post a link to it.  I have a Broadcom 4318 which is supposed to be hard to get working but it worked right away.  The steps I took follow; maybe you can replace your wireless adaptor card model and get it to work for you: 

- start up the synaptics package manager
- put the LIveCD in the CD drive, click edit and add CDRom, then click reload
- search for and install the ndiswrapper stuff (common, utils)
- using sudo, gedit the /etc/modprobe.d/blacklist file and add the following to the end:

# no native firmware, use ndiswrapper for Broadcom 4318
blacklist bcm43xx

- reboot
- located the Windows drivers for my wireless card: bcmwl5a.sys and bcmwl5.inf files
- via a terminal, did the following:

     - sudo ndiswrapper -l     <- lower case "L"
             this was to be sure no driver was listed
     - sudo ndiswrapper -i  *path to my bcmwl5a.sys file*
     - sudo ndiswrapper -l
             this should show the driver and hardware installed and working.  If it has any strange messages by it, or says something about "using bcm43xx", the driver didn't take (I got this when I didn't type in the path and filename correctly).  To fix this:

               -sudo ndiswrapper -r *driver name as shows in the ndiswrapper -l command*
               - redo the sudo ndiswrapper -i being sure to get the path and filename correct

      - sudo depmod -a
      -sudo modprobe ndiswrapper

I also installed, via synaptics package manager, the network-manager-gnome package as it makes managing WEP passwords and the actual connecting to a network much, much easier.

I don't know if it was needed or not, but I rebooted again after I had finished everything.

This is all I had to do.  If it doesn't work for you, perhaps it will work for someone else.

I am new to Linux and Ubuntu but found this was very easy to setup, thanks to the how-to page.  I'll edit and add the link if I can find it again!:)

---

### Post by mc4man on 2007-07-11
by far the easiest method for broadconm 4318
[http://ubuntuforums.org/showthread.php?t=197102]("http://ubuntuforums.org/showthread.php?t=197102")
ndiswrapper method
took about 2 min to do and connect

---

