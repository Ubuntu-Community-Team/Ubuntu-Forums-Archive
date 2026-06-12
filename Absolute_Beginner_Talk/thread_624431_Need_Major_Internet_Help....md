---
title: "Need Major Internet Help..."
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by Idk123 on 2007-11-26
All right. Essentially, I just installed Xubuntu on my gateway solo 3100 laptop. It has 64mb of ram, a few years old, and only has a phone jack for dial up. Now... I'm trying to get the internet on it. 

So... I have this netgear wireless card. I tried to install it, however I found out that the software on the disk is only compatible with Windows. So... That didn't work.

I tried to somehow get ndiswrapper so I could run the software in Linux. Didn't quite work out too well. I put it onto a disk on my laptop that has Windows, burned it, and put it into the gateway solo, and it was fine. The only issue is that when I entered the set up, it first said that the set up was all ready pre-installed in the whatever section... Ignored it, as I tried that, and it said I needed an internet connection in order to download it. (How ironic, right? You need the internet to get the internet) So, I continued on in the set up until it downloaded it. It said whatever could not be downloaded, and that it needed an internet connection as well, I believe. So, I didn't know where to go. I don't have a modem connection... Just a slot for a wireless card, and a dial up jack in the back of the laptop.

So, I went ahead and tried to get the dial up connection to work, so that I could download ndiswrapper. Couldn't get it to work. I entered in the phone number and everything... Just wouldn't quite connect for some reason. So now I'm stuck, and I really don't know how to get the internet to work in this thing...


My options are as follows; or at least the way I see it. I can either find another way to install ndiswrapper, find some substitute software that I could put on a CD and install without any issues, or I can try to get this dial up connection working. 

Now... I really don't know where to go from here, and how to get this 'ndiswrapper' on this laptop, or really any other substitute software that would work so I could put this network card on this laptop and get it to work.

So... Help please? I really don't know where to go from here to get this network card working, and I really do not feel like going hunting through retail store and retail store, trying to find one that's compatible with Linux and waste another portion of my savings.

---

### Post by Threbus5 on 2007-11-27
The Xubuntu was probably a good choice.
I have Xubuntu on one of my older machines. 

If you have access to an ethernet based Internet connection try using an older wired ethernet card instead of the wireless card or hunt for an older compatible wireless card. 
Ubuntu has "issues" with modem connections and to new users the solutions are neither straightforward nor simple.

Good luck

---

### Post by Idk123 on 2007-11-27
Er... Alternate disks? I used the alternate install disk... What does that have to do with getting an internet connection up, though? :blink: What I'm trying to do is find a way to get my NetGear 54mb Wireless card (WG511 v2.) to work...

EDIT: Just saw you edited your post. I see... So is there really no real way to get an internet connection up, then, other than finding a network card that is compatible with Xubuntu?

---

### Post by Threbus5 on 2007-11-27
I updated my reply.,
You already have Xubuntu working and need no alternate disks. 
My fault for posting too quickly.

---

### Post by Idk123 on 2007-11-27
I saw. I edited my post as well with my response :)

But is there really no real other way to get the internet on my laptop, other than finding a compatible wireless card that works with Xubuntu? If so, do you know of any easy to find wireless cards that I could find in a retail store that is compatible with Xubuntu? Thanks so much for your help.

---

### Post by Threbus5 on 2007-11-27
Just finding a compatible card may be only half the problem.
Feisty and Gutsy Ubuntu versions also have DNS resolution issues.
But they are relatively new.
Which version did you install? 6.06 Dapper seemed to work OK for me on older machines.
And, yes, card compatability would help.

---

### Post by Threbus5 on 2007-11-27
Don't know what sources you have available.
I use Office Max and Staples old (generally low priced) cards.
The one most used is a 802-11G, backwards compatible to A,B. I think it is neatgear but do not have that computer in front of me.

---

### Post by Idk123 on 2007-11-27
No.... I believe I have the latest version. The Gutsy version... 7.something. Whatever the latest edition of Xubuntu is, I have that. As for the cards... I'm pretty sure my card is compatible... The only problem is, as I said, is that the **software** is only for Windows... And I can't get any software like ndiswrapper or wine or anything else like that on my laptop; even with a cd, as it won't download correctly and needs an internet connection to download them.

---

### Post by Threbus5 on 2007-11-27
In about 10 - 12 hours I will be home and can look at the card in that machine.
If you are still interested I can update then.

---

### Post by Presto123 on 2007-11-27
Go here and D/L the top .tar file for WINE: [HTML]http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=77449[/HTML]

You can put that on a disk or something to put on your Xubuntu computer.

But, first, see what other people reply to this...it might not work. Someone else will probably know the code to get it working.

---

### Post by Threbus5 on 2007-11-27
OK, understand that you believe the card is compatible.
I have not had to use install software for the wireless or wired cards.
Can you set network properties for the card?
That is usually available somewhere under network configuration.

---

### Post by Idk123 on 2007-11-27
All right... I've got to go, anyway, so... By the time I get back, hopefully a few more people will have responded, and I'll be able to do some troubleshooting :P Thanks so much.

EDIT: Threbus5  Threbus5, the wireless card isn't even on when I insert it... Is there a way to access properties of it, though? I don't believe there is, because I don't believe it is reading it. Where do I have to go to get to the properties for it; assuming it is reading it?

---

### Post by SouthernPott on 2007-11-27
I may not be much help here because I was adding a wireless card to an old desktop with a new install of Ubuntu 7.10 and when I was going through the forum it seemed there are lots of issues.

Does Xubuntu have the same Synaptic Package Manager that Ubuntu does?  I did the following and it pretty much recognized the card automatically.  An Airlink 101 

Click on System.

Click on Administration

Enter password.

Click on Synaptic Package Manager

Find these three items in the list.

ndisgtk       0.7.2 -1ubuntu1
ndiswrapper-common  1.43 -1ubuntu2
ndiswrapper-utils-1.9   1.43 -1ubuntu2

Click on the checkmark box next to each and "mark them for installation".  The boxes will already be marked if you have installed them.  In my case the boxes are white or blank when not installed and green when installed.  So you may not have to install all of them.

Once you have all three marked, click the "Appy" button at the top.  

Once this was done the Ubuntu seemed to recognize the wireless card immediately and picked up my wireless access point relatively quickly.  In the box that opened up for entering the security password I had to change the security type to "hex 64/128 bit" and then enter my pass number.  I think the default setting is for WPA and a pass phrase  but I have the access point set for WEP for an older wireless card on another computer.

Again, I haven't used Xubuntu so I don't know what it looks like, and my apologies if I am way off base.

---

### Post by namich2007 on 2007-11-27
I understand that it is a relatively old laptop, however do you have any USB ports available on it ?
If this is available trying looking into using a USB to Ethernet adapter. Link sys has excellent choices that work in Linux.

---

### Post by Idk123 on 2007-11-27
Yes, actually it does :) Despite only having a single one, yes. It does.


EDIT: I was able to find and install all software except for the ndisgtk one. Was that one necessary, or should I be all right with just those two? If not, are there any substitutes for that one?

2nd EDIT: In addition, the packages do not appear to be actual programs. Just add ons to the OS, as I cannot find them anywhere. It still is not picking up my wireless card, I believe; no lights are coming onto the card.

---

### Post by Idk123 on 2007-11-27
Yeah... I've just tried everything I could think of to get it to detect it, and it isn't... The thing is, when I insert it, it **tries** to read it. You can hear the processor clicking rapidly when you insert it,and when you take it out. It just isn't showing up on the OS.

---

### Post by kpictjl on 2007-11-27
This is to add to what SouthernPott said...

According to this [link]("http://packages.ubuntu.com/gutsy/allpackages"), Gusty comes with... 

> ndisgtk (0.7.2-1ubuntu1 [amd64,i386], 0.6-0ubuntu3 [all]) [universe]
    graphical frontend for ndiswrapper (installation of Windows WiFi drivers)
ndiswrapper-common (1.43-1ubuntu2)
    Common scripts required to use the utilities for ndiswrapper
ndiswrapper-utils-1.9 (1.43-1ubuntu2)
    Userspace utilities for the ndiswrapper linux kernel module

Check to see if each are installed...
1. Open System &#8594; Administration &#8594; Synaptic Package Manager (I'm not sure what the path is in Xubutnu).
2. search for each of the above package
3. if the little box is checked/filled in then the package is installed.

If they aren't installed try [Installing packages without an Internet connection]("https://help.ubuntu.com/7.10/add-applications/C/offline.html").

After the all those packages are installed then configure wireless networking as shown [here]("https://help.ubuntu.com/7.10/internet/C/wireless.html").  Your first action is probably to install the windows drivers as shown [here]("https://help.ubuntu.com/7.10/internet/C/ndiswrapper.html").

Not sure if this helps or not.

---

### Post by Idk123 on 2007-11-28
The only issue I have which is effecting everything is that I cannot find ndisgtk (0.7.2-1ubuntu1 [amd64,i386], 0.6-0ubuntu3 [all]) [universe]. I searched everywhere for it, and I just can't find it. Everything else is installed, except for that which I simply cannot find. I do not think it came with the OS. Is there any other way to get this installed? Maybe through a disk? If so, where can I download this package, so I can burn it onto a disk?

---

### Post by SouthernPott on 2007-11-28
I think I did try to download that package (although mine is for 32 bit) after I found it in the Networking & Wireless category  when I was looking for help.  Not sure if it was already in my Synaptic Package Manager or not and I don't yet understand the whole download and extract thing yet so I may have just gotten lucky when I tried it.  The only thing I do remember is that the answers in the Networking and Wireless category specifically mentioned using the ndisgtk package alongside ndiswrapper.

If it is not in your Synaptic Package Manager you will definitely have to find it somewhere else and I believe you can put it on a disk and then install it.  Maybe try a Google search for it or search for it in the Networking and Wireless category.

Sorry my information is so weak but I am still learning, mostly trial and error so far.

[https://help.ubuntu.com/7.10/internet/C/ndiswrapper.html]("https://help.ubuntu.com/7.10/internet/C/ndiswrapper.html")

I know I saw a much more detailed page or two listing common wireless card drivers and help but I have misplaced it.  My only thought is to look in the Network & Wireless category again.  That is where I found everything.

---

### Post by SouthernPott on 2007-11-28
[http://linuxappfinder.com/package/ndisgtk]("http://linuxappfinder.com/package/ndisgtk")

The link above has everything listed but 64 bit for Gutsy Gibbon.  Maybe just try the 32 bit app since the others seem to be the same for each.  Way over my head at this point.

---

### Post by ugm6hr on 2007-11-28
@ldk123:

I think you should start from the beginning.  

I am assuming you have internet access available on a pre-existing wifi network.  If so, the best option is to try and get your Netgear card working, rather than resorting to dial-up (which will likely be more difficult anyway).

First thing to do is to turn the laptop on with the PCMCIA wifi card plugged in.

Then, in Terminal:
```
lspci
```

You are looking for the line that mentions Ethernet / Network Controller.
Copy and paste those lines here, and we can get you started....

Also - what encryption do you use on your wifi (i.e. WEP / WPA etc)?

---

### Post by SouthernPott on 2007-11-29
I worked on refurbishing an old DELL XPS T600 desktop last night with a fresh install of Ubuntu 7.10 and paid a little more attention to it this time.  This one is also with an AirLink 101 Wireless G card. 

My LiveCD did not have ndisgtk installed on it.  Only the two ndiswrapper packages I listed in an earlier post.   I wasn't sure if it came preloaded but it must not.  Anyone know why it is not part of the LiveCD as it seems to be needed from what I have been reading?

The ndisgtk package installed automatically with the first set of updates but I did these through a wired network connection.  Once the updates were done, I opened Synaptic Package Manager and installed them from there.  Then I left clicked on the network icon on the top panel and selected my wireless network name.  Changed the setting to hex 64/128, entered my key number and it picked up my wireless access point perfectly.

---

### Post by Idk123 on 2007-12-02
All right. I've essentially got everything up and running, only I need the driver for it, which I cannot find **anywhere.** Does anyone know where I can find it?

The exact name of the wireless card is, "Netgear 54 mbps Wireless PC Card WG511 v2."

---

### Post by kpictjl on 2007-12-02
is this what you mean?

[http://kbserver.netgear.com/products/wg511.asp](http://kbserver.netgear.com/products/wg511.asp)

---

### Post by Idk123 on 2007-12-02
Yup. As I said, I just can't find a driver for it which would work, and would also actually be compatible with Xubuntu Gusty Gibson in order for it to work with that ndisgtk thing.

---

### Post by kpictjl on 2007-12-02
I must be going crazy.  I would have swore I downloaded the inf file off netgear.com.  

Anyway...I have WG511v2.INF for you...  This is the XP driver for the WG511v2 that I'm using right now...it works for (X)Ubuntu Gutsy...for me at least.

The rub is I'd like to post it some where and link to it from this forum... how can I do that?

---

### Post by Idk123 on 2007-12-02
Eh... Here.

There's two ways that I know of.

[http://ripway.com/](http://ripway.com/)

Or, alternatively, try uploading it here:
[http://www.freedownloadscenter.com/author.htm](http://www.freedownloadscenter.com/author.htm)

---

### Post by kpictjl on 2007-12-02
Here's a link to the page where I have the inf file ...

[http://tod.larson.googlepages.com/filestoshare](http://tod.larson.googlepages.com/filestoshare)

---

### Post by Idk123 on 2007-12-02
I just tried burning it to a disk, and installing it. However, all that I got was a notepad like program opening up with what seemed to be the source code. Do I have to compile it from source? If so, how do I go about doing this? I have literally no such experience with this.

---

### Post by kpictjl on 2007-12-02
in a terminal...  type 
```
sudo ndiswrapper -l
```

post results

---

### Post by kpictjl on 2007-12-02
didn't mean to make my last post so short and snappy.  

No need to compile.   The .INF file I gave you will be what ndiswrapper uses.  I think step one though is to make sure you've got ndiswrapper installed.

If ndiswrapper -l works...meaning tries to list the windows drivers but finds none then we'll install this driver with the "-i" command.

```
sudo ndiswrapper -i /direcotry/to/WG511v2.INF
```

In ndiswrapper -l doesn't run then we need to get the ndiswrapper-utils package for you.

---

### Post by Idk123 on 2007-12-02
Well, I can't exactly copy and paste it due to the fact that it's on a completely different computer,  but... Generally, it shows a bunch of steps. For example, "-iinffile install driver described for 'inffile," "-a devid driver use installed 'driver' for 'devid' (dangerous)," etc. Then it says, "where 'devid' is either PCID or USBID of the form xxxx:xxxx. as reported by 'lspci -n' or 'lsusb' for the card"

I think I should choose the first option? It reads, ""-iinffile install driver described for 'inffile."

EDIT: Didn't see your last post. You know what, let me actually try just installing this in the ndisgtk application. And yes, I do have all of that ndis stuff :P

EDIT 2: Yeah... Invalid driver. Let me go do what you said now.

---

### Post by kpictjl on 2007-12-02
mmm, I didn't expect it to say anything, it's just suppose to list the drivers it has loaded.

Do you think you ever even installed the ndiswrapper package?

---

### Post by Idk123 on 2007-12-02
Yes. I installed every last one of them that's needed.

---

### Post by Idk123 on 2007-12-02
EDIT: Sorry, I actually mistook the l for a 1. Sorry. Let me go re-do that step.

EDIT: Sorry... Nevermind. It actually was a 1. So, yes. It shows all of those steps. Which one do I choose, or rather, what do I do next?

---

### Post by kpictjl on 2007-12-02
this link says it can give you the deb packages for ndiswrapper and ndisgtk as well for burning to cd and moving to you troubled machine...

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-5fffb979baaebf3a1e3a62759fe9d93326c2b8ab](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-5fffb979baaebf3a1e3a62759fe9d93326c2b8ab)

---

### Post by kpictjl on 2007-12-02
> **Idk123 said:**
> EDIT: Sorry, I actually mistook the l for a 1. Sorry. Let me go re-do that step.

EDIT: Sorry... Nevermind. It actually was a 1. So, yes. It shows all of those steps. Which one do I choose, or rather, what do I do next?

meant to be a lower case L...as is list...

but check out the link in my previous post as well...might be of value.

---

### Post by Idk123 on 2007-12-02
Eh... Wait. Why do I need another package? I have **all** of the ndis stuff. Everything. All I need is the proper driver for my card. I'm completely lost now...

EDIT: When I replace the 1 with an l, it simply says "command not found."

EDIT: And when I simply type in, "ndiswrapper -l," nothing comes up. Just goes to the next line.

---

### Post by kpictjl on 2007-12-02
> **Idk123 said:**
> EDIT: Sorry, I actually mistook the l for a 1. Sorry. Let me go re-do that step.

EDIT: Sorry... Nevermind. It actually was a 1. So, yes. It shows all of those steps. Which one do I choose, or rather, what do I do next?

you must be getting this... right?  It's just saying "-1" is a bad parameter and then listing the valid parameters. 

```
$ ndiswrapper -1
install/manage Windows drivers for ndiswrapper

usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid' (dangerous)
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information

where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or 'lsusb' for the card
```

---

### Post by Idk123 on 2007-12-02
Yes. That's exactly what I'm getting.

---

### Post by kpictjl on 2007-12-02
> **Idk123 said:**
> 
EDIT: And when I simply type in, "ndiswrapper -l," nothing comes up. Just goes to the next line.

excellent...

now copy that WG511v2.INF file to anywhere... lets say your Desktop "~/Desktop"

then install the driver using...

```
sudo ndiswrapper -i ~/Desktop/WG511v2.INF
```

the list the drivers again

```
ndiswrapper -l
```

---

### Post by Idk123 on 2007-12-02
After I type in the first step, I get this. "couldn't create /etc/ndiswrapper/wg511v2: Permission denied at /usr/sbin/ndiswrapper-1.9 line 152."

Also... This operating system is quite interesting... How you download things. Through the prompt; or rather terminal like that. Very different from Windows, or even MAC.

EDIT: Nevermind. Didn't see that you added the sudo in there. Hold up.

---

### Post by Idk123 on 2007-12-02
All right. Now I'm getting this error...


installing wg511v2 ...
couldn't find "WG511v2.sys" in "/home/levine/Desktop"; make sure all driver files, including .inf, .sys (add any firmware files) are in "/home/levine/Desktop" -
Installation may be incomplete
couldn't find "WG511v2.sys" in "/home/levine/Desktop"; make sure all driver files, including .inf, .sys (and any firmware files) are in "/home/levine/Desktop" -
installation may be incomplete

---

### Post by kpictjl on 2007-12-02
I posted 4 more files from the netgear CD to this page... I didn't think you'd need them...

[http://tod.larson.googlepages.com/filestoshare](http://tod.larson.googlepages.com/filestoshare)

try putting these other 4 files on your desktop, run the ndiswrapper -i again ... so how she goes.

Do you have a usb drive to make the file transfers easier?

---

### Post by Idk123 on 2007-12-02
Yes, but, eh... I find transferring it via CD a lot easier :)

---

### Post by Idk123 on 2007-12-03
Eh... Now how do I download them? One is a .tbm which is a text file, the other is a .cat which won't even open, and the other two are .sys which Xubuntu doesn't know what to open them with.

---

### Post by kpictjl on 2007-12-03
> **Idk123 said:**
> Eh... Now how do I download them? One is a .tbm which is a text file, the other is a .cat which won't even open, and the other two are .sys which Xubuntu doesn't know what to open them with.
right-click, save link as.

---

### Post by Idk123 on 2007-12-03
Eh... No. I think you mis-understood. I got those files onto a disk, and put them onto my laptop with Xubuntu. On Xubuntu, I can't run them or anything. As I said, one is a text file, the other won't open, and the other two Xubuntu doesn't know how to open them. And right clicking them in Xubuntu gives no option to save the link or anything like that.

---

### Post by kpictjl on 2007-12-03
> **Idk123 said:**
> Eh... No. I think you mis-understood. I got those files onto a disk, and put them onto my laptop with Xubuntu. On Xubuntu, I can't run them or anything. As I said, one is a text file, the other won't open, and the other two Xubuntu doesn't know how to open them. And right clicking them in Xubuntu gives no option to save the link or anything like that.

my bad.

copy them to your deskop.  Don't try to run these files or anything.

After copying them to your desktop then do back into the command line and do...
```

sudo ndiswrapper -i ~/Desktop/WG511v2.INF
```

---

### Post by Idk123 on 2007-12-03
All right. And sorry if I came off sounding like a jerk there or something :P Just re-read it, and, well... Yeah :P

And I just typed that in, and now I'm getting "driver wg511v2is already installed." :)

The light on the card still isn't coming on yet? Should I go into the ndisgtk application and try adding it now?

---

### Post by kpictjl on 2007-12-03
> **Idk123 said:**
> 
And I just typed that in, and now I'm getting "driver wg511v2is already installed." :)
?

good stuff...  no sweat tedious stuff

is this the only output of ndiswrapper?

> $ ndiswrapper -l
wg511v2 : driver installed
        device (11AB:1FAA) present


---

### Post by Idk123 on 2007-12-03
Eh... What do you mean output? Do I have to type something into the command prompt?


Sorry... I've been with Windows for so long... I just got into Xubuntu a couple weeks ago :lol:

---

### Post by kpictjl on 2007-12-03
I mean when you go to the command line and type "ndiswrapper -l" what do you see?

---

### Post by Idk123 on 2007-12-03
Hell...

"wg511v2 : invalid driver!"

---

### Post by kpictjl on 2007-12-03
> **Idk123 said:**
> Hell...

"wg511v2 : invalid driver!"

might be from trying to install the .INF file without the other files.  So lets remove this invalid driver and add it back in.
```

sudo ndiswrapper -r wg511v2
```

then do this to make sure ndiswrapper sees nothing...

```
ndiswrapper -l
```

then do this to re-install the driver...now that we have the other files on your desktop as welll

```
sudo ndiswrapper -i ~/Desktop/WG511v2.INF
```

then

```
ndiswrapper -l
```

---

### Post by Idk123 on 2007-12-03
After the last step, I got a rather loud beep sound. Then, I pressed enter again, and I got "install/manage Windows drivers for ndiswrapper"

Then, I got that long list of options again.

---

### Post by kpictjl on 2007-12-03
> **Idk123 said:**
> After the last step, I got a rather loud beep sound. Then, I pressed enter again, and I got "install/manage Windows drivers for ndiswrapper"

Then, I got that long list of options again.

weird. 

Sorry, but i'm going to have to punt...after midnight and I gota work in the morning...  sorry we couldn't fix it.

mostly these steps are in the Feisty Fawn documentation.  The Gutsy documentation assumes you have ndisgtk so it doesn't walk you though the ndiswrapper stuff..

[https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html#wireless](https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html#wireless)

good luck.

---

### Post by Idk123 on 2007-12-03
Dear... I might very well just bring it to my local computer repair shop and see if they can fix it, or rather at the least know a think or two about Xubuntu :P

---

### Post by Idk123 on 2007-12-03
Actually... I think I'm just going to buy a new card. I don't think this card is very compatible with Xubuntu, so I'm going to go look into the 3com 3CRUSB10075. Hopefully that one will work flawlessly, as reviews have said.

---

### Post by kpictjl on 2007-12-03
> **Idk123 said:**
> Actually... I think I'm just going to buy a new card. I don't think this card is very compatible with Xubuntu, so I'm going to go look into the 3com 3CRUSB10075. Hopefully that one will work flawlessly, as reviews have said.
Why not try to install a fresh copy of Ubuntu first?   Doing a clean install of ubuntu will take about 30 minutes, then you can install gdistk and then use the documentation on the ubuntu web site and all the instructions will match the gui you are working with.  You can very simply install Xubuntu (sudo apt-get install xubuntu) over the top of ubuntu and then just set your session to aalways log into xfce if you need the lightweight interface.  No fuss, no extra memory wasted, etc.

ndiswrapper doesn't care which flavor of ubuntu you have.  You most likely have something else going on.

If you are going to buy anything, i'd say get a device that will allow you to connect a network cable to you laptop.  Then you can use that to get on the internet as needed.  Think of it as a fail-safe.  You can always connect to your network with the hard-wire.

either way, good luck.

---

