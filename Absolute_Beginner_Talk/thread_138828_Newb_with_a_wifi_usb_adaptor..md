---
title: "Newb with a wifi usb adaptor."
date: 2006-03-02
forum: Absolute Beginner Talk
---

### Post by MetalGoat on 2006-03-02
First Post!
I just got Ubuntu 5.10 and I'm loving it but I'm very confused about how to get my Linksys WUSB54G to work. I've seen people say to use ndiswrappper but since I'm very new to ubuntu I cannot seem to get it to install. If someone who uses this adaptor or knows how to set it up can help me with it or give me tutorials to follow I would be very thankful.

---

### Post by paulmilliken on 2006-03-02
MetalGoat,
Can you post the output of "iwconfig" or "sudo iwconfig"?
Edit: Have a look at [https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards?highlight=%28wireless%29](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards?highlight=%28wireless%29) - this page says that your hardware won't work "out of the box".  So it might be tricky to get it working.  Indeed, they do recommend ndiswrapper though.

---

### Post by MetalGoat on 2006-03-02
Each one says "no wireless extensions"

---

### Post by Sandlst on 2006-03-02
by "cannot seem to get it installed" are you talking about ndiswrapper? If that is the case open a terminal (Applications/Accessories/Terminal) and put it:```
sudo apt-get install ndisgtk
``` This will put install a GUI front-end for ndiswrapper-access it in (System/Administration/Windows Wireless Drivers) After opening it, click on "Install New Driver" put the windows driver cd that came with your usb in the cdrom, click on the button that says (None) browse to the cd, and somewhere on it you should find a .inf file-select that file and click install.  After installing, it should come up under "Currently Installed Windows Drivers" with Hardware present: Yes.  If this is the case click on "Configure Network" and you should see an option for the usb adapter.  Hope this helps, post back if you have any problems.

---

### Post by paulmilliken on 2006-03-02
OK.  That means the operating system hasn't automatically detected your wireless device.  Unfortunately, getting it working with ndiswrapper is a bit beyond me so perhaps someone else can suggest a link?

---

### Post by MetalGoat on 2006-03-02
Sandlst,
Yes, I'm talking about installing ndiswrapper. I think I understand your directions but where can I download the ndis file you listed and where would I need to put it for the terminal codes you gave me to install it? Thanks.

---

### Post by Sandlst on 2006-03-02
Using the above code by itself should automatically download and install all the files you need, except for the .inf file, and that can only be found in your windows driver cd......this is assuming of course you have current internet access on the computer (wired) if thats not the case, is it possible for you to hook it up just long enough to use the command?

---

### Post by MetalGoat on 2006-03-02
The adaptor is the only way I can get internet on my computer. Ive been transfering the different ndis files with a jump drive from another computer. Is there a way I can download the file I need then put it on Ubuntu? And if so which one do I need, where do I put it, and how to install? - Thanks

---

### Post by Sandlst on 2006-03-02
After some poking around, I've found that ndiswrapper is on the default breezy install cd, which means to install it you would have to add the cd as a repository,  to add the cd in your repo, open synaptic (System/Administration/Synaptic Package Manager) click edit, then add cd with the install cd in your drive, then search for 'ndiswrapper' in synaptic, right click, select 'mark for installation' then click apply at the top of the screen, or run this in a terminal ```
sudo apt-get install ndiswrapper
```
After it is installed, go to this thread and read the second post on how to use it:
[http://www.ubuntuforums.org/showthread.php?t=138882&highlight=ndiswrapper]("http://www.ubuntuforums.org/showthread.php?t=138882&highlight=ndiswrapper")
Hope this works for you, good luck, and post back if you have any problems.

---

### Post by MetalGoat on 2006-03-03
Sandlst, Thanks for the link, it clears up alot, I installed it like it said but when I put in "sudo ndiswrapper -l" it says the .inf file (the one off my linksys install disc) is an invalid driver. Any help with this is really appreciated especially when I am so close. -Thanks

---

### Post by Sandlst on 2006-03-03
Are you sure there is only one .inf file? Sometimes they put more than one on the cd- alternatively, you could try and download one (sometimes the ones on the cd do not work properly)
For ndiswrapper troubleshooting try this link: [URL="https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirec
t=SetupNdiswrapperHowto"]https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto[/URL]
Look on this page to download another .inf file-to make this work type ```
lsusb
```It should come up with a list of things connected to your comp. via usb-one of those entries should be linksys, the number in front of the name is what you are looking for, or you could just search the list by title, either way it will provide a .inf file for you that hopefully will work, good luck! [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List")

---

### Post by MetalGoat on 2006-03-04
Each .inf that was on the adaptor cd says that it is an invalid driver when I listed them in ndis. It also won't let me uninstall them using the -e driver command (it says that they were never installed yet it clearly says they are when I list drivers) and when I list usb devices and try to use the one connecting my adaptor with my driver it says the driver was never installed properly. So I guess the ones off my cd aren't going to work. As for the page of drivers for my device I can't find one off of it that is .inf. I'm sooo close to getting this to work but ndis and drivers aren't cooperating like I wish they would. But on the upside through this I have learned to use the terminal well. Any help and/or good drivers for me to use are apprieciated.

---

### Post by Sandlst on 2006-03-04
While searching for a possible solution, I stumbled across this thread:
[http://www.ubuntuforums.org/showthread.php?t=106846&page=2]("http://www.ubuntuforums.org/showthread.php?t=106846&page=2")
Have you tried to follow the fourth post down?  It lists some .deb files, and where to find them, making for easy transfer between computers.

---

### Post by sailor2001 on 2006-03-04
see if your chip set is listed here  [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)
if so., download to desktop and then in terminal:
cd Desktop
sudo apt-get install ndiswrapper-utils
sudo ndiswrapper -i NET8180.INF
sudo ndiswrapper -l
sudo dhclient

---

