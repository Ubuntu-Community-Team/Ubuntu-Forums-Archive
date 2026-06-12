---
title: "Installing a driver for my wireless. What do I do with it?"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by CheshireMac on 2007-08-01
Hey folks. I'm installing a new driver for my wireless card, and I'm not sure if it will automatically place itself where it belongs . . .so before I unpack it, I'd like to know from someone who knows. Thanks. :)

---

### Post by bodhi.zazen on 2007-08-01
Best unpack it to a new directory in /home/<user_name>

I user ~/src for such things ...

At any rate, look at the README and ask if you have questions.

Otherwise, post more info ... card ? drive ? version of Ubuntu ?

---

### Post by CheshireMac on 2007-08-01
> **bodhi.zazen said:**
> Best unpack it to a new directory in /home/<user_name>
 
I user ~/src for such things ...
 
At any rate, look at the README and ask if you have questions.
 
Otherwise, post more info ... card ? drive ? version of Ubuntu ?
The card is Intel 2200BG, I run on Edgy, and what do you mean by drive? DrivER?

---

### Post by deadgobby on 2007-08-01
drive mainly means USB drive or wifi card input on older models of lap tops.
Gobby

---

### Post by deadgobby on 2007-08-01
Open up the terminal and inpit this command

lspci

Please copy and paste the response here.


All so see
[https://help.ubuntu.com/community/WifiDocs/Driver/Intel_4965_AGN_WiFi_Driver/Fiesty?highlight=%28intel%29](https://help.ubuntu.com/community/WifiDocs/Driver/Intel_4965_AGN_WiFi_Driver/Fiesty?highlight=%28intel%29)
Gobby

PS Grr rocks

---

### Post by CheshireMac on 2007-08-01
> **deadgobby said:**
> Open up the terminal and inpit this command
 
lspci
 
Please copy and paste the response here.
 
 
All so see
[https://help.ubuntu.com/community/WifiDocs/Driver/Intel_4965_AGN_WiFi_Driver/Fiesty?highlight=%28intel%29](https://help.ubuntu.com/community/WifiDocs/Driver/Intel_4965_AGN_WiFi_Driver/Fiesty?highlight=%28intel%29)
Gobby
 
PS Grr rocks
Okay . . .I'm unable to copy and paste anything due to the lack of connection, but what is it that you're looking for?

---

### Post by CheshireMac on 2007-08-01
AHHHHHHH!!!!!!!! Someone please tell me what I'm not doing!!!!! I have the firmware, I have the driver . . .I don't know what to do with them, and I'm about to flip!!! Two weeks of troubleshooting without any progress. This is driving me up the wall!

---

### Post by deadgobby on 2007-08-01
OK Gur Zimm is trying to help you here. Lets go back to basics. Is your wifi card pluged into a USB port? What have you tried to do? Have you gone into network settings and try the simple way?  Copy and paste should be simple. Like opening up the terminal and input 

lspci 

 Open up the text editor or Open Office and paste the information there for safe keeping if you want. When your net connection is good. Post that tib bit here. All so look at the link I gave you  too

---

### Post by CheshireMac on 2007-08-01
> **deadgobby said:**
> OK Gur Zimm is trying to help you here. Lets go back to basics. Is your wifi card pluged into a USB port? What have you tried to do? Have you gone into network settings and try the simple way? Copy and paste should be simple. Like opening up the terminal and input 
 
lspci 
 
Open up the text editor or Open Office and paste the information there for safe keeping if you want. When your net connection is good. Post that tib bit here. All so look at the link I gave you too
Sorry Zim . . .I'm just frustrated because I've been through so many steps to show people my info, and then nothing is solved. I have no way to show you the info for lspci without hand-typing it, and I'm not doing that again.
My card is internal . . .I'm not sure if it's USB or not. It's 2200BG, rev 05. That's the readout for it in lspci.
I've tried my network manager in every way possible. I have a driver, I have firmware, both as of today. They're in my home folder right now, unpacked and waiting for placement, or whatever it is that they need to have done to them.

---

### Post by thefoolisme on 2007-08-01
Well if you've posted all the info before, why not provide the link to your previous posts?  Might be more helpful than saying you're going to type it all over again.  Have you read the instructions for NDISwrapper? Are you having a specific issue, or just looking for a how to guide?

 I noticed you had about 5 different posts for this issue.  Might have been better to just keep the one going, then everyone would have all the info.  just a thought.

Edit:  Did you read the link in Gobby's post?  Sounds like exactly what you need.

---

### Post by CheshireMac on 2007-08-01
> **thefoolisme said:**
> Well if you've posted all the info before, why not provide the link to your previous posts? Might be more helpful than saying you're going to type it all over again. Have you read the instructions for NDISwrapper? Are you having a specific issue, or just looking for a how to guide?

 I noticed you had about 5 different posts for this issue. Might have been better to just keep the one going, then everyone would have all the info. just a thought.

Edit:  Did you read the link in Gobby's post?  Sounds like exactly what you need.
I see that you've found all my posts without links . . .and as for having five instead of one, well I did that to assess the problem from different angles after each angle went dead. 
I love that you're trying to state the things I've been doing wrong here . . .very productive. I did read every single link that was given to me, and believe me, I've tried every approach offered. If this was a simple issue, it would have been solved by now. But thanks for YOUR input, which was very helpful.

---

### Post by thefoolisme on 2007-08-01
The reason I found all your posts is because I was trying to help you by doing a search for your particular wireless card.  Many others could probably just tell you what you needed to do if they had all the information, which they don't.  That's all I was pointing it out.  Instead of being an a$$, you could have just provided the links for the others.  

If you want help, you have to explain what you need.  Gobby's link seemed to be how to install ndiswrapper and the drivers for your wireless card.  So what didn't work with the post that gobby posted?  What about that didn't fit your situation? What's different that we should be focusing on?

---

### Post by CheshireMac on 2007-08-01
> **thefoolisme said:**
> The reason I found all your posts is because I was trying to help you by doing a search for your particular wireless card. Many others could probably just tell you what you needed to do if they had all the information, which they don't. That's all I was pointing it out. Instead of being an a$$, you could have just provided the links for the others. 

If you want help, you have to explain what you need. Gobby's link seemed to be how to install ndiswrapper and the drivers for your wireless card. So what didn't work with the post that gobby posted? What about that didn't fit your situation? What's different that we should be focusing on?
I'm sorry I was rude. I'm having one of those days, and this computer is about to go out a window . . .
Okay . . .The Ndiswrapper guide that was given is stopped at the first step because it says it's an invalid location. 
But also, the guide says it requires a connection of some sort, which I have not. 
Is there a way to manually install this driver . . .I'm thinking maybe I want to just reinstall the OS and start from scratch(all I have right now is some music and minor adjustments).  
Again, I'm sorry for my comments. I appreciate the help.

---

### Post by IamAcoconut on 2007-08-01
What's the problem with copying?
Are you now using a different computer than the one on which you encounter problems?

Type lspci in the terminal. Mark the text that comes out. Paste it here with middle mouse button. Or right click on the marked text, select 'copy', than paste here. Or make a screenshot of the terminal and attach it.

---

### Post by CheshireMac on 2007-08-01
> **IamAcoconut said:**
> What's the problem with copying?
Are you now using a different computer than the one on which you encounter problems?

Type lspci in the terminal. Mark the text that comes out. Paste it here with middle mouse button. Or right click on the marked text, select 'copy', than paste here. Or make a screenshot of the terminal and attach it.
I am currently without any connection at all on the computer in question. I've been using someone else's computer trying to sort through all of this. 
lspci comes up with all the info, but I'm not sure what I'm looking for . . .my network controller is Intel 2200BG, rev 05. There's a tonne of info here though, and I'm not sure what I'm looking for. 
That, I think is the main issue here. I don't actually know what the problem is. 
I've typed lspci, lshw, iwconfig, I've scanned for connections, I've turned the card on and off manually (Terminal), and I've done all this as root also.

---

### Post by deadgobby on 2007-08-01
We need all that info from the command. Look for for example
 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)


Gobby

---

### Post by CheshireMac on 2007-08-01
Okay . . .something strange just happened.
I did a manual switch for the wireless card for the hell of it, and it came on without any i/o errors . . .I checked, and the power is actually on, and it picks up ESSID 'netgear' . . .but I'm still connected. 
This is a huge breakthrough. I'm not sure what happened, but I'd like to know how I can activate this connection. I've got 90% signal, which is fantastic. I think it has something to do with me switching the hotkey in BIOS.

---

### Post by IamAcoconut on 2007-08-01
Does the computer in question have no floppy drive, no cd-burner? Without any output it will be hardly possible to help you.

Just to be sure, is the driver in question a Linux one? What's its extention?

---

### Post by CheshireMac on 2007-08-01
Alright . . .so here's what I think I've assessed. Tell me if I'm wrong. 
I've managed to successfully switch the wireless card on by going through the BIOS and activating the hotkey. 
The icon and connection management shows 86% signal strength, but still shows the two monitors with an "X" in red. This tells me (again, I think) that the card is recognized, and powered on, but isn't communicating with something it needs to connect properly. 
Am I close to it? I feel this is a big breakthrough. Thanks for all the help so far, folks. This is great!

---

### Post by CheshireMac on 2007-08-01
I thought of something else. I scanned and this time, the scan came back with nine cells. This is encouraging, but I'm not sure what to do with it . . .
Also, I've moved from where I was just working, and now I can't seem to get a signal, although everything else seems to be the same as the last message. Sorry for the intervals, people, but I'm really inexperienced with this sort of issue.

---

### Post by anewguy on 2007-08-01
I have no idea what you have done in the past, and I'm not about to go searching for the links, so I'll post something here and see if it helps you:

(1) if you never got ndiswrapper installed, do the following:

put your LiveCD in the drive (with Ubuntu already booted).  It will come up with something about a disk containing software packages was found and do you want to run the package manager - say yes.

EDIT:  If it doesn't do the above, leave the LiveCD in the drive, then system/administration/synaptics package manager.  When that starts, click "edit" and "Add CD-rom" and follow the prompts on the screen.  When it has finished reading the CD, click "no" to the the question about adding another CD.  When it gets back to the main package manager screen, click on "reload", then continue below.

Once the package manager is up, click "search" and type in ndiswrapper then click to search.

When the search finishes, find ndiswrapper-common and ndiswrapper-utils-xxx (mine says 1.9), click them and mark for installation, then click apply.

When that finishes you can exit the package manager.  Ndiswrapper is now installed.

(2)  open a terminal window  applications/accessories/terminal

type:

ndiswrapper -l    <-- that's a lower case "L"

If it returns anything about a driver:

sudo ndiswrapper -r xxxxxxxx   <-- where xxxxxxxx is the name of the driver that shows in the list command above

do the above until ndiswrapper returns nothing.

type:

sudo ndiswrapper -i xxxxxx  <-- where xxxxxx is the complete path and filename of the driver file for your wireless adaptor.   As an example, if your driver file is called "driver.xxx" and located on your desktop, the command would be "sudo ndiswrapper -i ~/Desktop/driver.xxx".

Now, do the ndiswrapper -l  again to list the drivers, and report back here what it says.  That's going to be the only way we can help.  Please give the complete results, not just a summary, okay?:)

---

