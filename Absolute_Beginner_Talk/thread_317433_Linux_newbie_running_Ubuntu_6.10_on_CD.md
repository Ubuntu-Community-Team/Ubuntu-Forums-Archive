---
title: "Linux newbie running Ubuntu 6.10 on CD"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by rainb19 on 2006-12-12
Hi folks - I'm a complete newbie to Linux and have just downloaded and run Ubuntu 6.10 on my Dell Latitude D400 Windows 2000 notebook removable CD/DVD drive.

First, a big thank you to all you Ubuntu folks for making it freely available and for the free support available here. As a longtime Windows user, I've been wanting to try out Linux just to learn how it works and, hopefully, be able to contribute to the community in future.

One of the challenges I faced as a complete newbie was understanding how to use the .iso image. I downloaded it onto a CD thinking that would be the boot image - hence wasted some time and effort right there. Luckily a Linux-savvy friend mentioned that I should download it, open that file, and then burn it onto the boot CD. Perhaps you might want to consider adding this simple explanation and guidance to your download links to prevent similar hassles for other newbies? 

Another newbie tip you may want to add at the download link is how to get the system to boot from the CD drive vs. the default (hard drive) setting. Luckily I've seen this done before - not too many newbies will want to fiddle with their boot routines without expert guidance! 

Ubuntu booted just fine from the CD, however it didn't detect my wifi card (IntelPro Wireless Lan 2100 3A MiniPCI Adapter) out of the box. I checked the documentation ('wifidocs/wireless networking,wireless cards supported' and 'Connecting to the internet/wireless cards'). Two cards came close in the description:'Intel PRO/Wireless 2100 (Centrino)' and 'Intel Wireless 802.11b MiniPCI Adapter' so I decided to try again.

In 'wifidocs/wireless networking/802.11 wifi' instructions A and B work fine with 6.10, as does C1. However 'if your device supports scanning, your access points essid should display in the drop down list' doesn't apply because the system still isn't recognizing the device!

"C2: If you are using WEP..." unfortunately is not relevant to the actual 6.10 Interface properties screen which asks for 'Password type' instead of 'Key type' and 'Network password' instead of 'WEP key'. These are technical terms not familiar to most users, so again an explanatory note and an updated visual would be a great help. Luckily I had set up my Linksys wifi network with Linksys' help so I happened to know what to look for and where.

Anyway, my 'fiddling' worked and I am finally online with Ubuntu 6.10! However, my wifi card is now recognized as: 
Intel PRO/Wireless LAN 2100 3B Mini PCI
Status : Status
Bus type: PCI
Device type: Unknown
Capabilities: Unknown

Setting up my HP 6210 printer was a breeze although the database describes it as HP 6200. Haven't yet figured out how to set it up as a scanner/fax.

At this stage my questions are:
1. The left-click (return) functionality of my two button Logitech USB mouse doesn't seem to work - is that something I need to set up separately?
2. How do I get Adobe Acrobat Standard 7.0 (installed under Windows) to be recognized in Ubuntu and work off the right click mouse menu?
3. Since I'm running off the CD will I have to redo all my wifi/printer settings every time I reboot?
4. Where will any downloads/software installed under Ubuntu reside? 
Thanks in advance for your help with my first Linux experience!

---

### Post by ron999 on 2006-12-12
Hi rainb19

To get your extra mouse buttons to work correctly you need to edit a file. It's not difficult.
It's best to do that after you've installed Ubuntu.
:)

---

### Post by John.Michael.Kane on 2006-12-12
At this stage my questions are:
1. The left-click (return) functionality of my two button Logitech USB mouse doesn't seem to work - is that something I need to set up separately?
[B]Needs more info what model logitech mouse.
Note: most if not all standard mouse have two button and scrolling functions out of the box.
[/B]
2. How do I get Adobe Acrobat Standard 7.0 (installed under Windows) to be recognized in Ubuntu and work off the right click mouse menu?
[B]adobe reader should be in the ubuntu repos. search under synaptic for it 
Click system-->administration--->synaptic
Note make sure you have all the repo's uncomment.

On a side note the standard ubuntu install has a pdf reader already installed.[/B]

3. Since I'm running off the CD will I have to redo all my wifi/printer settings every time I reboot?
**Yes.The system it is running off the cd,and ram. you will have to redo all your configs after installing the OS. Running the livecd is only for testing your hardware to make sure things work.**

4. Where will any downloads/software installed under Ubuntu reside? 
**Most downloads are placed in your home folder or a folder you direct the download into.**

---

### Post by rainb19 on 2006-12-12
Ok thanks for the help :-)

---

### Post by rainb19 on 2006-12-13
> **SD-Plissken said:**
> At this stage my questions are:
1. The left-click (return) functionality of my two button Logitech USB mouse doesn't seem to work - is that something I need to set up separately?
[B]Needs more info what model logitech mouse.
Note: most if not all standard mouse have two button and scrolling functions out of the box.
[/B]
2. How do I get Adobe Acrobat Standard 7.0 (installed under Windows) to be recognized in Ubuntu and work off the right click mouse menu?
[B]adobe reader should be in the ubuntu repos. search under synaptic for it 
Click system-->administration--->synaptic
Note make sure you have all the repo's uncomment.

On a side note the standard ubuntu install has a pdf reader already installed.[/B]

3. Since I'm running off the CD will I have to redo all my wifi/printer settings every time I reboot?
**Yes.The system it is running off the cd,and ram. you will have to redo all your configs after installing the OS. Running the livecd is only for testing your hardware to make sure things work.**

4. Where will any downloads/software installed under Ubuntu reside? 
**Most downloads are placed in your home folder or a folder you direct the download into.**

Hi - thanks for your very helpful responses
> Needs more info what model logitech mouse.
The info off the back of the device is:
Cordless MouseMan Optical MN:MRR63
(sorry - it's a 3 button one with a scroll wheel - two buttons either side of the wheel, and one button on the side)
Logitech Mouseware 9.27

> Note make sure you have all the repo's uncomment.
Sorry - what does this mean?
TIA

---

### Post by pay on 2006-12-13
try ```
sudo nano /etc/apt/sources.list
```and remove all the #'s from the lines that start deb http//:[www..](www..)..

---

### Post by ElBuscador on 2006-12-13
Maybe I am misunderstanding what you mean, but it sounds as if you want to use a program you installed in Windows (Acrobat) while running in Linux. If so, this is not possible natively. You will need to install the Linux version, if there is one, or use a package such as Wine to run Windows apps from within Linux. If you just want to view PDF files, and not use the full functionality of Acrobat Standard, then as others have stated you have a few alternatives.

---

### Post by sawjew on 2006-12-13
> **pay said:**
> try ```
sudo nano /etc/apt/sources.list
```and remove all the #'s from the lines that start deb http//:[www..](www..)..

As a newbie to linux you may find nano a bit confusing so the graphical way is this;

When you install software in Ubuntu it downloads and installs it from online repositories, these are just servers where the software packages are stored.

To install extra software such as Acrobat you need to enable extra repositories.  The easiest way to do this is to got to your menus, select System>Administration>Software Sources

[LIST]
[*]You will see a window as shown below in the attachment.  Check all the boxes and this will enable a huge range of software to be installed.

[*]When it asks if you wish to update now say yes.

[*]You can then install Acrobat Reader or other software by going to Applications>Add/Remove
[/LIST]

Note that if you install software when running as a livecd it will not be there next time you boot up.

---

### Post by rainb19 on 2006-12-13
> **ElBuscador said:**
> Maybe I am misunderstanding what you mean, but it sounds as if you want to use a program you installed in Windows (Acrobat) while running in Linux. If so, this is not possible natively. You will need to install the Linux version, if there is one, or use a package such as Wine to run Windows apps from within Linux. If you just want to view PDF files, and not use the full functionality of Acrobat Standard, then as others have stated you have a few alternatives.

Great - thanks very much for the clarification - your understanding of my intent is perfect :-)

---

### Post by rainb19 on 2006-12-13
sawjew: <I>As a newbie to linux you may find nano a bit confusing so the graphical way is this;</I>

Thanks very much for your understanding and lucid explanation! :-)
> Note that if you install software when running as a livecd it will not be there next time you boot up.
So I'm slowly discovering :-) I guess I'll try it anyway just to see how it works
Thanks

---

### Post by rainb19 on 2006-12-14
Back to Windoze for this Linux newbie:

sawjew: > To install extra software such as Acrobat you need to enable extra repositories. The easiest way to do this is to got to your menus, select System>Administration>Software Sources

    * You will see a window as shown below in the attachment. Check all the boxes and this will enable a huge range of software to be installed.
    * When it asks if you wish to update now say yes.
    * You can then install Acrobat Reader or other software by going to Applications>Add/Remove

Tried this today - got a message 'database is not up to date - update now?'. On clicking 'Yes', it spun for a while then simply froze. After waiting another 10 mins. I just pulled the plug on it :-(

Had hoped to try out some of the downloads etc today and keep 6.10 running for the day. Am now back to Windows hence am able to post this.

---

### Post by peterj on 2006-12-14
> **rainb19 said:**
> Back to Windoze for this Linux newbie:

sawjew: 

Tried this today - got a message 'database is not up to date - update now?'. On clicking 'Yes', it spun for a while then simply froze. After waiting another 10 mins. I just pulled the plug on it :-(

Had hoped to try out some of the downloads etc today and keep 6.10 running for the day. Am now back to Windows hence am able to post this.

You really need to install the operating system to get a true feel. Everything is much slower when you boot off the cd. 
Are you familiar with open office? a free linux alternative to micro's? It has a built in pdf creator as far as I know. Thats about the only thing I ever used acrobat for.

---

### Post by rainb19 on 2006-12-14
> **peterj said:**
> You really need to install the operating system to get a true feel. Everything is much slower when you boot off the cd. 
Are you familiar with open office? a free linux alternative to micro's? It has a built in pdf creator as far as I know. Thats about the only thing I ever used acrobat for.

Thanks - shall check out open office 's pdf creator
I'm a total OSS rookie so I need to build some confidence with it in 'Safe'/CD mode before I take the deep dive of installing it on the HD. In exchange, I can live with 'slow' for the time being . What I wasn't prepared for was the slow>>freeze routine :-)

---

### Post by John.Michael.Kane on 2006-12-14
rainb19 the live cd is only for testing certain aspects like hardware,and certain software.

If your trying to install things from the repos using a live environment your going to have a rough time with ubuntu. You can install ubuntu with out removing your windows partition if this is your worry.

---

