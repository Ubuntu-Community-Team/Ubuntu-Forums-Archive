---
title: "need help with ndiswrapper or something...?"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by TheTeZ on 2007-11-29
Hey,

i am completely new to linux, ive installed linspire a while ago and its  nothing more than windows, i got a laptop passed down its an old dell inspiron 7500, i have a wireless card [Netgear WG511v2] which i have been trying to get working for the last 3 days non stop,(oh yeah, im running Kubuntu 7.04] i think ive found everything on google that their is, and none of it worked.  
Heres the problem:
 i have the card and it has no linux drivers, the computer doesnt recognize the card [ive got two of the same one so its not the card]  and i cant install ndiswrapper, or any of its packages, it  wont find any of them when i try. i have downloaded packages and such that i read should be what i need.  
when i try installing them it says they cant be found .... weird i dont know what to do.... 

Can anyone walk me through this from the begining? remember im a pretty extreme beginner.  i am amaizing with windows, and problems seem to follow me there [although i can solve anything on windows] i wouldent be surprised if some of those "for no reason" problems followed me to kubuntu.

... or does anyone know if 7.10 will auto detect my card...?

---

### Post by NullHead on 2007-11-29
Well you should use 7.10 anyways ... It has allot of improvements :D 

But as for you're card you can detect what it is by using the terminal in applications>accessories>terminal and typing this in to the window that should show after you run it.

```
lspci
```

Past all of whats in that window and Ill let you know if you need ndiswrapper or not ;)

---

### Post by Sandlst on 2007-11-29
Did you install ubuntu with the live cd?  Ndiswrapper should be on the cd, try putting the cd in while running ubuntu, it should pop up a window asking if you want to add the cds packages using a package manager (say yes).  After this happens, you should be able to install ndiswrapper.

EDIT: actually this may not work the same way in kubuntu, if it doesn't try opening the package manager; there should be some way to add the cd as a repository.

---

### Post by TheTeZ on 2007-11-29
well i have  the version they shipped of 7.04 so yeah installed it from the live cd and when i put it in, it only asks me if i want to open it or copy it... not install software

---

### Post by SouthernPott on 2007-11-29
I am very new so my help will be limited.  This question is best addressed in the Networking and Wireless category where there is more specific help.  That being said here goes.

Do you have access to a wired network connection so you can get updates?

Click on System.

Click on Administration

Enter password.

Click on Synaptic Package Manager.

Go down the list and find two ndiswrapper packages.  You will also need to find ndisgtk which should be right above the two ndiswrapper packages.

If you don't have ndisgtk showing, this is where you will need to get the updates first.  I do it by hooking my computer up to a wired network connection first.   Then I get all the updates and ndisgtk will be one of them.

Once the updates are done, go back to the Synaptic Package Manager and mark the three packages for installation by clicking on the checkmark box next to each one.  A dialog box will open asking if you wish to mark for installation.

After these are installed, I left click on the Network Connection icon on the top panel or bar.  The two computer monitors in the upper right.  Then I select my my wireless network name.

After a short time, a box opens up for me to select my wireless security setting, mine is Hex 64/128 bit for my WEP and then I enter my key number and click Login to Network.

Some people are able to do all of this from the Terminal which is probably better to learn but I can't do it yet.

Good luck.

---

### Post by Sandlst on 2007-11-29
> **TheTeZ said:**
> well i have  the version they shipped of 7.04 so yeah installed it from the live cd and when i put it in, it only asks me if i want to open it or copy it... not install software
Try entering the following command in the Konsole: ```
sudo apt-cdrom add
```Then insert your cd.  If that works, try installing ndiswrapper with ```
sudo apt-get install ndiswrapper-utils
```

---

### Post by TheTeZ on 2007-11-29
hey thanks, i had to bring the laptop into another room to hook it up, let me run through the list of suggestions, itll take a min, i will get back to you in probably 5 mins or so, let you know what worked/didnt

---

### Post by TheTeZ on 2007-11-29
Hey, sorry no go on any of those,  with  the cd commands it mounted the cd unmounted it and told me to do it for the rest of the cd's in the set.... dunno what i did.... and then when i ran the 2nd command it said that the ndiswrapper-utils package coulent be found....

---

### Post by TheTeZ on 2007-11-29
anyone? anyone at all.... or at least can someone tell me weather or not 7.10 will detect the netgear wg511 v2 card.

---

### Post by Sandlst on 2007-11-29
If the cd was successfully added, the package name might have changed (ndiswrapper-utils is what it is named in Gutsy) so try to do what SouthernPott suggested and install ndisgtk instead.  Try it with ```
sudo apt-get install ndisgtk
```

---

### Post by TheTeZ on 2007-11-29
"cant find package ndisgtk"

---

### Post by Sandlst on 2007-11-29
Just to be sure: you don't have access to a wired internet right now right?

---

### Post by TheTeZ on 2007-11-29
i did plug it into a wired connection. but i can only use one wired or wireless at a time...

---

### Post by Sandlst on 2007-11-29
Alright, with the cable plugged in try the following commands: ```
sudo apt-get update
``` ```
sudo apt-get install ndisgtk
```see if that works.  Even if it doesn't, solving this will be much easier with a wired connection.

---

### Post by TheTeZ on 2007-11-29
im starting to get excited, i feel like im getting close. ill let you know. im gonna try two things. and ill post weather or not they worked one being what you just suggested. Thanks again guys

---

### Post by TheTeZ on 2007-11-29
cool, i finally got ndiswrapper installed can someone tell me how to install the driver...? 

 umm if not ill google it... i found plenty of ways before.... 

mer dont even worry about it, ill let you know if i need some more assistance. 

Thanks

---

### Post by TheTeZ on 2007-11-29
hey, can anyone let me know where to get the drivers for the tiwan version of Netgear wg511v2 to use with kubuntu 7.04 ? no matter what drivers i use that ive found i havent been able to get one that didnt say "invalid driver"

---

### Post by NullHead on 2007-11-29
Please post the output of lspci.

---

### Post by NullHead on 2007-11-29
Are you running a 32-bit or 64-bit ubuntu? I have some files you can try.

[http://ubuntuforums.org/attachment.php?attachmentid=44623&d=1190994539](http://ubuntuforums.org/attachment.php?attachmentid=44623&d=1190994539) 32-bit file

[http://ubuntuforums.org/attachment.php?attachmentid=44622&d=1190994539](http://ubuntuforums.org/attachment.php?attachmentid=44622&d=1190994539) 64-bit file

---

### Post by TheTeZ on 2007-11-29
oh yeah. sorry i never did that... 
... ... ... yada yada .... ... 
02:00.0 ethernet controller: marvel technology group ltd. 88w8335 [libertas] 802.11b/g Wireless (rev 03)

---

### Post by TheTeZ on 2007-11-29
arg.... nope... they dont work... wonder why... any other suggestions... did the info help? do you want something else from the terminal?

---

### Post by NullHead on 2007-11-29
OK please remove all of the drivers you've installed ...but leave ndiswrapper installed please ... I'm working on a driver that you should be able to use.

Ill get back to you later with it.

---

### Post by SouthernPott on 2007-11-29
I am going to ask a dumb question.  When you started the CD, did you boot from it or did you just run it after booting (starting up) in Windows?

---

### Post by TheTeZ on 2007-11-29
im not in the live cd. i ran it after booting

---

### Post by NullHead on 2007-11-29
> **NullHead said:**
> OK please remove all of the drivers you've installed ...but leave ndiswrapper installed please ... I'm working on a driver that you should be able to use.

Ill get back to you later with it.

OK I have some drivers you should try ... look at my attachments.

assuming they're on you're desktop.

Extract them by opening a terminal and moving to you're desktop.
```
cd ~/Desktop
```

Now extract them.
```
tar -xvf WG511v2.tar.gz
```

Move to that folder that was created.
```
cd WG511v2
```

Install the driver.
```
sudo ndiswrapper -i netmw13b.inf
```

Check the driver status 
```
ndiswrapper -l
```
It should say some thing like driver installed; device present

Set it up with modprobe
```
sudo ndiswrapper -m
```

Start the driver```
sudo modprobe ndiswrapper
```

allow the driver to start automatically```
sudo cp /etc/rc.local /etc/rc.local-backup && sudo wget http://download119.mediafire.com/rwhxczmhjxrg/7mnftpdgd10/rc.locall  -O /etc/rc.local
```

Restart and see if it worked. 

Note I don't have this card so I don't know if this will work.

---

### Post by TheTeZ on 2007-11-29
thanks ill let you know how it turns out..

---

### Post by SouthernPott on 2007-11-29
Sorry for being so dense but what operating system is/was on your computer?  It just sounded to me like you copied the disk into Windows and tried to run it from there.

I don't have a Kubuntu disk so I am assuming it installs the same way Ubuntu does.  When you were getting ready to install it, did you reset your boot sequence so that your computer booted up from the CD first rather than the hard drive?  Then when your computer restarts with the Live CD in it you will get a screen asking for you to select an install or run without installing option, a check CD for errors option, plus some others.

Did you have to go through a setup sequence of specifying what language you wanted and how you wanted your disk partitioned?

---

### Post by TheTeZ on 2007-11-29
i have kubuntu 7.04 

yes yes and yes... same thing, 

why... what are you trying to figure out... maybe i can anwser rather than trying to beat around the bush...

---

### Post by TheTeZ on 2007-11-29
that last command produces this:

mv: missing destination file operand after `/etc/rc.local-backup'
Try `mv --help' for more information.

---

### Post by NullHead on 2007-11-29
Try it again please.

Edit: I've changed a few thing in the last command so make sure to copy it again.

---

### Post by TheTeZ on 2007-11-29
hey nullhead, and everyone else, i really appreciate it, just wanted to say that.... 

now when i use that last command 

cp: cannot stat `/etc/rc.local': No such file or directory


i wish i wasnt such a beginner its probably something in real easy, but i dont know much about it

---

### Post by TheTeZ on 2007-11-29
you think if i made that directory something might work

---

### Post by TheTeZ on 2007-11-29
didnt install anything.... :-(  ANYONE?!?!?!

---

### Post by NullHead on 2007-11-29
Hi .. sorry I was held up for a little bit ... we will do this the hard way ... 

ok go[ hear]("http://www.mediafire.com/?7mnftpdgd10") download the file to you're desktop and run the following command after it's done.```
sudo rm -rf /etc/rc.local && sudo cp ~/Desktop/rc.local /etc/rc.local
```

---

### Post by NullHead on 2007-11-29
> **TheTeZ said:**
> didnt install anything.... :-(  ANYONE?!?!?!

ok whats the output of ndiswrapper -l ? please post it.

---

### Post by TheTeZ on 2007-11-30
netmw13b : driver installed


and when i have the card in it tells me that the device is present

---

### Post by TheTeZ on 2007-11-30
sudo rm -rf /etc/rc.local && sudo cp ~/Desktop/rc.local /etc/rc.local

did nothing

---

### Post by NullHead on 2007-12-01
> **TheTeZ said:**
> sudo rm -rf /etc/rc.local && sudo cp ~/Desktop/rc.local /etc/rc.local

did nothing

OK ... do this and copy out what I post hear.

```
sudo kate /etc/rc.local
```
Select all the text thats in the file you opened .. if there is any ... and past this into it.

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

sudo modprobe ndiswrapper

exit 0
```

Save the file and reboot and you should be all set.

---

### Post by mschersten on 2007-12-01
Well, I'm glad someone else is working on this.  I picked up one of these this morning, and I'm trying to get it up.  First, I am running Gutsy, and I can tell you it does not automatically detect it.  So, upgrade to Gutsy for everything else, but it won't help here.

Here's where I am so far:  Installed ndiswrapper and ndisgtk.  I got the installation cd along with it, and I'm attaching the .inf driver I installed using ndisgtk (which looks pretty similar to the attachment in #25).  My output of lspci is identical to that of TheTeZ in #20 (although mine is made in China, not Taiwan), and ndiswrapper -l gives me

```
wg511v2 : driver installed
     device (11AB:1FAA)

```

Now, this is my absolute first experience with wireless, Linux or otherwise, so I have little idea what to expect.  The manual tells me that the card has two lights, green and amber.  For the green light, on means the card is plugged in, and blinking "indicates the WG511 is trying to establish a connection but is unable to do so."  For amber, it says "On/Blinking" means "If blinking, the WG511 has a connection and is transmitting or receiving data," and off means "there is no data transmission on the wireless network."  Here's the thing: I don't have a wireless access point at home.  My plan was to get the driver installed, make sure the card was recognized, and drive down and park in front of the coffee shop to see if it had worked.  Here at home, I got the green light blinking, and parked out in front of the coffee shop, it stopped blinking and went steady.  In network settings, the wireless connection is on roaming mode.  I assume that most public wifi hotspots are completely open?  Is that what I would use roaming mode for?

Also, the first place I looked for help was at [http://linux-wless.passys.nl/query_part.php?brandname=Netgear](http://linux-wless.passys.nl/query_part.php?brandname=Netgear), which directs me to prism54.org, but that was all over my head.  Maybe someone else can make sense of it?

Hope this helps.  Thanks!

---

### Post by mschersten on 2007-12-01
Also, I've just added
```

sudo modprobe ndiswrapper
```

to /etc/rc.local

---

### Post by TheTeZ on 2007-12-02
hey, thanks, im upgrading, and i had a problem doing so i so i fresh reinstalled and im upgrading to 7.10 so im gonna start all over again, and hopefully something works this time

---

### Post by Genecks on 2007-12-02
1. Install ndiswrapper
2. Find the drivers on the netgear website
3. Attach the drivers to ndiswrapper

It's not too complicated.
"sudo dhclient" tends to work better than the network manager

---

### Post by TheTeZ on 2007-12-02
drivers on the neat gear site havent worked. and they are .exe im pretty ...extreamly new to (k)ubuntu, and i dont know how to get the .inf and .sys from the .exe

---

### Post by NullHead on 2007-12-02
The file I attached is the .inf and .sys files .. there is two of each, but you should try both to see witch set works and witch doesn't.

---

### Post by TheTeZ on 2007-12-02
will do but im still waiting on the upgrade to complete, then i gotta reinstall ndiswwrapper and then load the drivers and hope something works.

---

### Post by NullHead on 2007-12-02
OK .. remember all you have to do to install ndiswrapper is.```
sudo apt-get install ndiswrapper-utils-1.9 ndisgtk
```
Then install the drivers using the GUI.```
gksudo ndisgtk
```

---

### Post by TheTeZ on 2007-12-03
wow... so things went a lot smoother with 7.10 then they did with 7.04  
anyway... still have a problem, updatetd, upgraded, installed ndiswrapper and tried a few drivers

the driver when loaded said hardware present: yes
ndiswwrapper -l presents:  netmw13b : driver installed
           device (11AB:1FAA) present 

but ... no lights.... doesnt work still, i know the card works....  but kubuntu finds no wireless devices

---

### Post by TheTeZ on 2007-12-03
[https://help.ubuntu.com/community/WifiDocs/Driver/mrv8k](https://help.ubuntu.com/community/WifiDocs/Driver/mrv8k)

THE ANWSER!!!! 
(for the china made card)

yes... i appreciate your help.  

i decided since the drivers wernt working switch the card with the other one i had [same brand diffrent place of manufacture] and it turned out to be the china one... i found these instructions, its currently booting up, and i saw some pretty lights on the card..


machine booted up, i right clicked the network manager clicked the network name and BOOYAH!!!

thanks again guys and that link above i posted to help those who may come across the same problem....
assuming you have the china card anyway....

---

### Post by TheTeZ on 2007-12-09
ARG!!!! so i typed in sudo apt-get ubuntu-desktop and it started installing ubuntu i ran out of space on the partition, so i made the partition bigger, what do i type to start up the installation from where it stopped, also when i now start up firefox or any web browser it says welcome to 7.04 i should have ... or did have 7.10 installed (kubuntu) that and my wireless isnt working again, but after i can get my adapt manager to work again i will get that working. Any help?

---

