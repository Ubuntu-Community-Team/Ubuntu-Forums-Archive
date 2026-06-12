---
title: "Super Confused.. Just started playing with ubuntu"
date: 2006-06-17
forum: Absolute Beginner Talk
---

### Post by demonicdude on 2006-06-17
Ok well, i went to my friends house the other day and he installed ubuntu on one of his old computers :) . It looked cool and all so i thought i'd give it a try. So i installed  it with very little problems. (live cd sometimes wouldn't load but i figured out i messed up burning the cd hehe ). Anyways, so now i have Windows Xp and Ubuntu on my computer. 
      Problem now is, i have no clue at all how to install anything or fix my internent connection! I've been searching through the forums to find out, only thing i found is that you should use ndiswrapper to do something with the drivers in windows.. Very confusing to me :?: . Anyways, would anyone be able to tell me how to install stuff and fix my internent or point me in the right direction?. 
      Oh and also, another problem is viewing movies. How do i get avi or mpgs working in ubuntu? Sorry for so many questions, complete noob here :D .

---

### Post by Patsoe on 2006-06-17
What brand/model is your network card? Is it wired or wireless?

For the avi stuff, you might want to search for something called "easyubuntu". But read well before you use that, otherwise it might install a real lot of stuff.

---

### Post by oscar on 2006-06-17
To install things the easiest way is to go System > Administration > Synaptic Package Manager . Search for the program you want, select for installation and Apply.
To help you get your internet working we need more information, how do you normally connect to the internet, through a dial up modem, a dsl modem, an external router etc.

---

### Post by demonicdude on 2006-06-17
I'll try that snypatic thing soon.

anyways for my internent i have a wireless router card in my computer. Its a linksys b -broadband router BEFW11S4 ([http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1115416826220&pagename=Linksys%2FCommon%2FVisitorWrapper](http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1115416826220&pagename=Linksys%2FCommon%2FVisitorWrapper))

Uh... what other information do you need? :D (complete moron at this stuff)


Also, So i tried that snypatic thing. How would i install ndiswrapper with it? I searched through the things, not there. Then i downloaded on windows and then got it to linux and click add download packages. And it doesn't show up.

Also also, Very weird thing. Whenever i do something with like snyaptic or open the ndiswrapper folder, and i go back to windows, it sends me to a blue screen saying something about messed up drivers? Now I dont think this is supposed to be happening... It tells me to restart and to try again, and if message shows follow these steps bla bla. I restart everything is fine.. Just making sure i'm not doing anythign wrong here..

---

### Post by DarkOx on 2006-06-17
Software in Linux is distributed in "packages", which can easily be installed with the program Synaptic (if you're using Ubuntu) or Adept (if you're using Kubuntu). If you're using Ubuntu, click &#8220;Desktop&#8221; on the top of the screen. Select &#8220;Administration&#8221; and then &#8220;Synaptic Package Manager&#8221;. If you're using Kubuntu, click the menu, select &#8220;System&#8221; and then &#8220;Adept&#8221;.

Regardless of which one you're using, enter in the search item &#8220;ndiswrapper&#8221;. You need to select the package &#8220;ndiswrapper-utils&#8221; for installation. This will allow you to use ndiswrapper from the command line. Unfortunately, the program that allows you to use ndiswrapper with a graphical user interface is only availbile on-line, not on the CD. Note that very nearly all the software you use in Ubuntu can be installed in the same way, by searching for it, selecting it, and clicking "Apply".

With ndiswrapper, you can now install windows drivers for your wireless card (I'm assuming you're trying to connect to a wireless network here). It may also work with a wired network card, but it is not guaranteed. Check out [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List) for a full list of cards that are known to work with ndiswrapper.

First, you need the wireless drivers for your card. These can be found on the installation CD that came with your card. You're looking for a file that ends in ".inf" and a corresponding one that ends in ".sys". Copy these files (you should be able to just drap-and-drop) somewhere convenient, such as your home folder (which is "/home/username", replacing "username with whatever your log-in name is.)

Start up a terminal. If you're using Ubuntu, this can be found by going to &#8220;Applications&#8221;, then &#8220;System tools&#8221; and selecting &#8220;terminal&#8221;. In Kubuntu, select the menu, then &#8220;system&#8221; and &#8220;konsole&#8221;.

In the terminal type:

> cd /path/to/files

replacing "/path/to/files" with wherever you saved the file to. This can be found by locating the file, right-clicking on it, selecting "properties" and looking at the location information.
Then type:

> ndiswrapper -i filename.inf

replacing &#8220;filename&#8221; with whatever the relevant .inf file is called. If all goes well, the drivers should be installed. To check, type

> ndiswrapper -l

This should return something like: filename          driver present, hardware present
if it does, it's safe to proceed. Type:

> ndiswrapper -m

then type:

> sudo depmod -a

and finally type:

> sudo modprobe ndiswrapper

After you use the 'sudo depmod -a' command, it will ask for your password. Enter it. Nothing will appear on the screen, not even *******, but this is perfectly normal.  Your card should be installed at this point. You can check by typing:

> iwlist scan

if it returns something like:

Cell 02 - Address: 00:05:6B:C3:BF:A2
                    ESSID:"Somename"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-80 dBm  Noise level:-256 dBm
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

then your card is working fine. At this point, you'll probably want ndiswrapper to load automatically when you start your computer. If you're using Ubuntu, type:

> gksudo gedit /etc/modules

Or, if you're using Kubuntu type

> kdesu kwrite /etc/modules

either way, a text editor should pop up. Simply add &#8220;ndiswrapper&#8221; to the bottom of the file, save, and exit the program. Ndiswrapper should now load automatically at boot time. Assuming you don't need to use encryption on your wireless network, you should be able to access the internet with Ubuntu.

---

### Post by demonicdude on 2006-06-17
Thanks for the info DarkOx. I'll try that, but i dont want to screw up my computer :). Will this at all affect my computer? Right now in my other post i'm seeing that blue screen and its really making me parionoid lol. 

Also, i downloaded ndiswrapper off of windows and then moved it to linux. (mounted windows all ready yay :) ). Should i not extract it and just leave it as it is and search for it on the synaptic thing? Or will it just be there.? I tried searching and it wasn't there..

---

### Post by Patsoe on 2006-06-17
You don't need to install ndiswrapper, it comes with a standard install. You need to install ndiswrapper-utils from the install cd. 

Synaptic only looks in "trusted" places when it looks for installable packages (this is actually nice in terms of security - you can never by accident get something from an untrusted repository!). That's why it doesn't find a file you just placed somewhere.

---

### Post by PriceChild on 2006-06-17
For playing more types of media, check out [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by demonicdude on 2006-06-17
Umm... so i searched for ndiswrapper and nothing came up... Could this be a problem? I installed ubuntu using the livecd. 

And: Thanks for that website pricechild :)

Also: No one has input about that blue screen problem?

Also Also: Thanks for all the help you guys are giving me :). Jeez these forums are loaded with people lol. I post in the morning and by afternoon its on the third page!

---

### Post by demonicdude on 2006-06-17
OK! Being the idiot that i am, i finally found out where that ndiswrapper thingy is and i installed it. So then i began following your instructions. And i got to ndiswrapper -i filename.inf step and then when i type that in it says cannot create directory etc/ndiswrapper/...

What would be the problem here?

---

### Post by Drakkor on 2006-06-17
Hey, PriceChild just got done talking to you on Qunu, Cheers ! :D

---

### Post by demonicdude on 2006-06-18
*bump*

---

### Post by RRS on 2006-06-18
[QUOTE=demonicdude]..........when i type that in it says cannot create directory etc/ndiswrapper/...

What would be the problem here?[/QUOTE]

Does it give a reason? Try preceding the command with "sudo" if it's a permission issue.

Also, is the file still in windows or where did you move or copy it to in Ubuntu? I usually need to put a file into /home in order to make a directory to it but I've probably been doing something else wrong all along, still works though. 

If none of the above helps post back with any error messages you've received.

---

### Post by demonicdude on 2006-06-18
AH OMG YES!!!!

Thank you rrs it was the sudo thing. Maybe i shouldve gave the full error because it was saying that i should try root.

Anyways! Its working and i'm posting this from ubuntu!:D . Thank you so much guys for your help!

---

### Post by RRS on 2006-06-18
No problem, sometimes I get lucky.

Welcome aboard and have fun! :)

---

