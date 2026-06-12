---
title: "Intermittent Airport."
date: 2012-08-04
forum: Apple Hardware Users
---

### Post by killabuntu on 2012-08-04
G'day all,

I'm a relative newb to Linux and even newer newb to Ubuntu, so I'm needing a bit of help.

I've managed to install Ubuntu 12.10 onto my PPC G3 iBook and while it runs ok, it will never be a speed demon. The machine has 640 Mb of RAM and runs at 700 MHz so it will struggle a bit. I don't intend to use it for any high demand work, I have a quad core iMac running Lion for that sort of stuff, so generally, speed is not an issue.

It was only after I had it installed for a few days that I realised that 12.10 is still in alpha, go figure. For the most part, it runs really well, I've installed cairo-dock and a few other things so I'm finding my way around the OS ok.

As the subject line indicates, my issue is with the Airport card, common issue from what I read. The first time I booted up, the system recognised the card and the network but would not login. After some trying, I eventually grabbed the Belkin Surf & Share USB dongle I bought for my Puppy Linux install and plugged it in, voila, it connected straight up. So at least I have a working back up for when the Airport  just won't work.

I tried all the suggested fixes and workarounds and none seem to work. When I installed wicd and deleted the network-manager (using sudo apt-get), as suggested in a couple of posts, I didn't have any wifi, not even with my Belkin. There wasn't even an interface I could use to configure the wifi. Fortunately, ethernet came to the rescue, I quickly removed wicd and reinstalled the default network-manager.

Having done that, I see that wicd is still installed and running as a start-up process. According to one how-to about this whole issue, there can only be one wifi manager running, how is my situation possible?

At the moment, I get wifi intermittently, at first it was for about a minute then drop out but lately it has been connecting permanently but not every start up. I'm finding that I have to restart a few times to get it to connect. Is this normal? If anyone has any suggestions as to where I can look to make it to work every time I boot up, I would appreciate that.

Also, I am looking for kernel modules that I can stop from loading at start up just to get a bit more speed out of it. As I said before, I'm not needing a lot of speed but anything to get just a little more would help it run a bit smoother. Where would I start looking?

Thanks for any help. Also, if I need to add any further info, please let me know, I'm only too happy to supply what I can, I just don't always know what is needed. Cheers all.

---

### Post by rsavage on 2012-08-04
You may have more joy asking in the Network forum [http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336) .
 
The PowerPC FAQ does have a section about Airport cards [https://wiki.ubuntu.com/PowerPCFAQ#Will_my_wireless_work.3F](https://wiki.ubuntu.com/PowerPCFAQ#Will_my_wireless_work.3F) 
 
To uninstall wicd:

sudo apt-get remove python-wicd wicd wicd-daemon wicd-gtk
 
For more speed try the Xubuntu desktop and make sure you have your graphics acceleration optimised. [https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_install_a_derivative.3F](https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_install_a_derivative.3F)

---

### Post by 2blue on 2012-08-04
Lubuntu is the lightest of the ubuntu distros. It is somehow a bit different from Xubuntu even. You should try it ;-) I have successfully installed it on regular pc with 700 MHz cpu, and I rarely was able to benefit from much more than 300MB RAM with a cpu like that (I had managed to install 1GB on it). These days we often operate with very differnt hardware and specs, however lubuntu was not that different from the regular Windows 7 computer, at least running one or two applications at a time. Absolutely no struggle, promise! Light running and fast booting. I went straight for lubuntu 12.04 when I set up my old iBook G4 with 1.42GHz cpu, thinking most functions in Totem player and desktop environment in regular Ubuntu would not run very well on this old thing.

There are two "restricted" packages to be found in package manager / soft ware center where one of them activates hardware drivers for differen wireless cards. These two packages usually sort out most issues with hardware drivers and different codecs. They are the first ones I go for after running Update Manager. 

I have had wifi issues like yours with both a new dell laptop and with an iMac, after a lot of fuzz and expert help, the solution was to get a new router. Even when the router worked fine with several other computers, the iMac was not able to stay connected. I have now a white apple router.  Wireless can have weird issues some times. 

Your iBook G3 should run fine with most applications. The most difficult area for ppc seems to be media players in browser and different flash streams.

Best of luck ;- )

---

### Post by killabuntu on 2012-08-05
Thanks rsavage and 2blue,

I did try Lubuntu on my emac at one stage, just the live CD, I think it was about 10.X not sure now, but at that time I was just looking around for different Linux distros and trying whatever I could as long as it would run from a liveCD. I will consider trying L or X again on this machine on the recommendation of you two wise ones.

I am actually sending this from my iBook, I have a connection at the moment. Thanks too for pointing me to the Network forum, I'll give them a go.

The PowerPCFAQ was one of the places where I read about the workarounds that included the wicd step that didn't work. I'll continue to refer to them and of course the forums,

...but thanks again you two, you :guitar:

PS which version of L or X would you recommend I try?? The latest stable version? Thanks once more.

---

### Post by 2blue on 2012-08-05
I usually go for the latest stable version, at least if I depend on that particular comptuer for something. I have installed beta-relases too there is no point really unless you have time to report to the dev-and testers team. At least when you are fairly new to Ubuntu, it is much easier to determen what the bugs are and the solutions are all there. Come october most of us will do the upgrade. I think 12.04 is longterm support though, but for the odd computer I suppose that doesn`t matter too much. 

For me I have had Ubuntu run very slow on hardware it really should work well with, sometimes speed and functionability can be very dependant on model and hardware. It might have been driver issues, but I never found solutions for it. Ubuntu usually does very well though, it has only been the odd case. For Lubuntu, it is made to run well on minimal specs, that is why I recomended it. I have used it on three different computers with advantage to the other versions. I am on the lubuntu iBook now ;- )  I suppose you have to try it to see the difference, and if you like it. Lubuntu has LXDE desktop, but it is not the only thing making it run lighter. I used to take a screen shots of terminal running htop with different applications, it is a good indicator for load on cpu and memory at least. If you like Kubuntu and it runs fine, keep it. How does Totemplayer work with the old iBook?

---

### Post by killabuntu on 2012-08-05
Thanks 2blue,

I've just installed Lubuntu 12.04, mainly because I had already downloaded the iso sometime ago, and it certainly is quicker that Ubuntu 12.10. :) Of course, some of the same issues are there as they were for the Ubuntu install. I can't get a wifi connection with the Airport card but my Belkin USB dongle is fine, it has been a lifesaver. I will head over to the Network forum and check out solutions there.

One other issue that has reared its ugly head that wasn't in quantal is difficulty restarting and shutting down, for some reason neither process will complete. On the upside, the hibernate function isn't the problem that suspend was in quantal, it will actually come out of hibernate. :o

I'm not sure what Totemplayer is, 2blue, so can't report on it's functionality at this point.

I like the LXDE desktop system :D and am familiar with most of the apps installed with it so at this time I might keep lubuntu installed although I might give kubuntu a go at some time in the future, I guess I can install side by side with lubuntu??

Anyway, cheers for your help, all the best and see you around the forums. You too, rsavage.

---

### Post by 2blue on 2012-08-06
There seem to always be some stuff needing attention on a fresh install!

Sorry, my fault on the video player, Totem might be long gone by 12.10, hope not! I haven`t booted in full Ubuntu in some time, but I like it a lot. 

I had the same trouble with hangups on the first few shuttdowns for some reason forcing use of on/off button, but it sort of smoothed its` self out. I actually don`t know if this was fixed by regular updates or some auto configuration sorting it`s self out. I think I had it on something like two shuttdowns and my iBook has behaved all fine since. I hope you sort out your Airport activation with ease this time.  

If I remember correctly you need a good swap partition to make hibernation functions work, and usually it is provided for by default installation.  Dual boot is fine with different versions of Ubuntu, easy if you have already an available partion. It is a good way to compare the setups. 

Regards

---

### Post by killabuntu on 2012-08-07
Well, I've had my iBook running all day, even with the lid closed, and had wifi for most of it. Since it connected after the first 5 minutes or so, it has not dropped out at all, that I am aware of. I was at work for about 6 hours and the lid was closed the whole time.

My wife tells me that at times, it would make a few disk noises but it was still running ok when I opened it up again. I have found that both Suspend and Hibernate don't work, it requires a hard shutdown and hard startup. I've read somewhere that the only reason for shutting down a Linux system is for hardware maintenance, so I'm considering leaving it run the whole time, just close the lid when not in use.

Does anyone know how an iBook goes being left running? Is heat an issue over the long term? What about battery life and staying on mains power? I know that the battery will last about 2 hours if it is not working too hard but if I let it get too low, it will go into suspend and I will have to do the hard shutdown routine.

It doesn't worry me to shut down at night (that is my normal routine with all my Macs) but the wifi is the only hassle to restarting each time. Of course, if it connects consistently each time, it won't be a problem only a minor inconvenience.

Anyway, I'm liking lubuntu a lot, I think I'll keep it. Cheers all and that for your help. :)

---

### Post by 2blue on 2012-08-07
How large is your swap? As I mentioned I have lubuntu 12.04 on a G4 iBook, 1.42GHz, 512 RAM. We should have pretty much the same hardware? I let lubuntu take all of the harddrive, using default installation method (wizard type), now disk utility shows 1.5 GB swap. I think there is a minimal swap space needed to make hibernation functions work properly, I cannot remember nubmers exactly. 

On this old iBook hibernation seems to work fine. If left alone I`m quite sure the system goes to sleep and I have to press enter (or something) for it to wake up and hard drive activates, I get a black screen with the cursor arrow, and a second press on enter makes the screen light up (I have bootup into active system, no logon password). I usualy leave lid open when I don`t do a full shutdown. 

I even get the white dot of light blinking when computer goes dormant, the one indicating power cord is plugged in (exactly like osx do, charging battery I suppose). In previous versions of lubuntu I have had trouble with both lubuntu and ubuntu dormant functions, but this time it seem to work fine with no extra fuzz. There has been no heat problem, or even the normal amount of heat when returning to a dormant computer.  I have been assuming it worked fine, maybe I should double check.

---

### Post by 2blue on 2012-08-07
You are right killabuntu, by iBook doesn`t go completely dormant either. There is something ever so slightly buzzing from the electrical. I think I will bootdown completely, it can`t be good for a hd to be on at all times?  There is no detectable heat though, I left it for two hours and all cool when I came back.

---

### Post by killabuntu on 2012-08-07
Ok, I decided to power down last night and see how it was this morning, it won't connect at all so far and it has been running for about an hour and a half. :(

I haven't connected my Belkin dongle yet, sometimes when I'm on line with the Belkin, the Airport decides it wants to play too. Of course, yesterday it connected all by itself. My usual routine when trying to connect is to authenticate and let it run its course trying to make the connection. But when it doesn't connect I leave it offline, that is when it usually connects on its own, not so far today, though??? :(

When I had the Ubuntu 12.10 install running, I tried all the workarounds and still didn't get a connection, except when I went back to the initial set up and then it was intermittent like it is now in L' without the workarounds. It makes me wonder what the problem could actually be???? :confused: Unfortunately, I am not a programmer or debugging guru so I wouldn't have a clue where to start or what to look for!#!#!#:( So, are the workarounds even worth the effort? They didn't work for me in U' 12.10 and I probably won't bother with them in L' 12.04?!?!?!?!

As to my swap size, the install set it at 841Mb, I don't remember setting anything so the system would have set it at that size. I have 640 Mb RAM, is that enough swap? I still have plenty of HD space to increase if necessary.

Thanks for your interest and help, 2blue.

---

### Post by 2blue on 2012-08-08
Your swap is probably fine. There is [swapfaq]("https://help.ubuntu.com/community/SwapFaq/") page where it suggests ways to increase swap and even dedicate it to dormant use. There seem to be no strict guide for size of swap, but 512MB seems to be on the small side, and 2GB on the large side, both acceptable.  I don`t really understand how it works, not sure if it will improve hibernation either. However, it seems this old thing might benefit from more RAM after all; regarding speed at least.

I don`t know why &#7809;e ended up with different swap size, since we both followed the regular install guide. I have to look into this, I have no idea really. 

It`s really weird with your wireless, mine connects right away from dormant mode and from restart. We should have the same wireless card? 
I now my father had major troube with wireless on an iMac he bought autumn 2011. For some reason it kept disconnecting when all other computers in the house had no problem. It truned out there was some kind of interference, and a guy from the Apple store came, installed a new router (the apple one being much better of course) and I think he aslo configurated some kind of setting for the Mac to be first priority connecting. I thought it was bit weird, but it worked, and for a while it was my mothers laptop that had issues with connecting. 

I live in an old house, and I have a desk in a spot where there is some kind of interference with wireless signals. I`m not quite sure what it is (maybe the cast iron beams in the ceiling) but when I connect to a USB wireless adaptor I have with antenna it connects fine. At night it can work fine with out the extra USB antenna improved thing, in daytime not a chance. Wireless is odd sometimes.

---

### Post by killabuntu on 2012-08-08
Wifi certainly is finicky, my Airport has not connected all day but just sitting here reading your post, 2blue, and I've realised that it is actually connected. I've just disconnected the Belkin and all is fine. :D But of course, will it connect tomorrow again??? Who knows??

I have a mid 2011 iMac and my wife has a Macbook (2009 I think) and we have the occasional issue with our wifi which is an Apple Airport Express, it sometimes just doesn't connect, usually coming out of sleep, but its not too much of a problem, just sometimes inconvenient.

Anyway, thanks for the  info about the swap size too, I think I'll leave mine as it is at the moment. If I work out that I need to change it later, I'll look into it then.

But back to the wifi, I guess someone will come up with a real fix sometime?!?!?!? In the meantime, I'll keep going with it the way it is. Thanks again for your help and interest, 2blue.

---

### Post by rsavage on 2012-08-09
> **killabuntu said:**
> 
When I had the Ubuntu 12.10 install running, I tried all the workarounds and still didn't get a connection, except when I went back to the initial set up and then it was intermittent like it is now in L' without the workarounds. It makes me wonder what the problem could actually be???? :confused: Unfortunately, I am not a programmer or debugging guru so I wouldn't have a clue where to start or what to look for!#!#!#:( So, are the workarounds even worth the effort? They didn't work for me in U' 12.10 and I probably won't bother with them in L' 12.04?!?!?!?!

I would urge you to look again at the PowerPC documentation and the links it provides.  The information will be there for you to solve your problem.  If all else fails then you can use wpa_supplicant directly as they do in crux [http://cruxppc.org/Airport](http://cruxppc.org/Airport) (ask on the network forum about this).  It very much depends how you want to connect (WEP/WPA) and what firmware you have flashed on the card.  When you've figured it out (I mean when you've rigorously tested the workarounds....no bodges please) then you can edit the PowerPC documentation to improve the experience for others.

---

### Post by 2blue on 2012-08-09
I don`t know if it helps at all, but my wireless shows as "Broadcom BCM4318 (AirForce One 54g) 802.11g", and my router is set to WPA2. Everything is autodetected.

---

### Post by killabuntu on 2012-08-09
> **rsavage said:**
> I would urge you to look again at the PowerPC documentation and the links it provides.  The information will be there for you to solve your problem.  If all else fails then you can use wpa_supplicant directly as they do in crux [http://cruxppc.org/Airport](http://cruxppc.org/Airport) (ask on the network forum about this).  It very much depends how you want to connect (WEP/WPA) and what firmware you have flashed on the card.  When you've figured it out (I mean when you've rigorously tested the workarounds....no bodges please) then you can edit the PowerPC documentation to improve the experience for others.

Thanks, rsavage, but can I ask- what documentation are you referring to specifically? I haven't read any other than the FAQs and forum posts really. Is there a help file that comes with the install? Or is there a link/s you could share? Thanks.

I did have a look at the Crux info but some of it doesn't mean a thing to me, I can't even get past point 2 on that page. :confused:

Regarding my comment about the workarounds not being worth the effort, I still stand by that to the extent that, if the Airport card connects by itself without the fixes, even though it doesn't work first up necessarily, why bother? It certainly is frustrating while it is doing this, though.

My question is- why is it that something 'comes right' after a while and why try to 'fix' it? I've just had another thought, I purchased a refurbished Airport card, could it just be that it needs to warm up a bit to connect?? I wonder??? :confused: If that is the case, then maybe I should pull it out and reinsert it, maybe that would seat it better?? I might give that a go at some point. Maybe, it is working properly but is purely a hardware issue??? Who knows?

On the wpa_supplicant option, I saw on the Software Centre an app for wpa manipulation, it was called Wpa_gui, I think. Does anyone know anything about it?

2blue, my Airport card (original/classic) is listed as AppleKeyLargo something.

Thanks to all of you, for your patient responses. I find that having come to this later in life (I'm over 50 :(), it takes a long time to make some of the connections needed to understand the workings of systems like Linux. And coming from a Mac background where it is 99% gui and 'just works', it is a steep learning curve for me.

Thanks again, cheers.

---

### Post by rsavage on 2012-08-10
The relevant bit of the CRUX instructions start at 7.2.  I knew they would seem complicated which is why I suggested you seek help on the network forum.  I'm not passing the buck by suggesting you go on there, just you'll get more expert help and probably quicker responses.

The PowerPC FAQ is the PowerPC documentation I was referring to.  The linked bug shows a problem with the Airport card.  You need to have ap_scan=2.  Hopefully the network forum people will be able to give you a debug command to see what ap_scan you are using (and confirm this is your problem).

Wicd was supposedly a workaround that worked in 10.04.  The source of this is probably dubious at best, but I think I can see how to make it actually work (I currently have 10.04 installed) by modifying a misc.py file.  It would be interesting if the Network forum people come up with the same (12.04 may have changed so I'm not going to waste your time with my suggestions at the moment).  

Btw, what version of flashed firmware do you have?  Are you using wep or wpa?

I'm afraid you have been let down by the people before you with an Airport Classic card.  I don't have one of these.  If I did I would of thoroughly tested it and made sure a solution was in place on the PowerPC FAQ.  Btw, the FAQ has all useful information from the Apple forum in it (certainly from the past year and a half since I've been using linux) so there is really is no need to search the Apple forum.


EDIT: reminder to myself (please ignore the following for now):
/usr/lib/pymodules/python2.6/wicd/misc.py symlinked to /usr/share/pyshared/wicd/misc.py

relevant bit:
```

def ParseEncryption(network):
    """ Parse through an encryption template file

    Parses an encryption template, reading in a network's info
    and creating a config file for it

    """
    enctemplate = open(wpath.encryption + network["enctype"])
    template = enctemplate.readlines()
    config_file = "ap_scan=1\n"

```[http://wicd.sourceforge.net/punbb/viewtopic.php?id=700](http://wicd.sourceforge.net/punbb/viewtopic.php?id=700)

Useful files here:
/var/lib/wicd/configurations        (the configuration files of the setup networks)
/etc/wicd/encryption/templates  (note, if you create your own template then add it to the active file)

EDIT2: In 12.04 the file is /usr/lib/python2.7/dist-packages/wicd symlinked again to /usr/share/pyshared/wicd/misc.py

The code has changed a bit:

```

def ParseEncryption(network):
    """ Parse through an encryption template file

    Parses an encryption template, reading in a network's info
    and creating a config file for it

    """
    enctemplate = open(wpath.encryption + network["enctype"])
    template = enctemplate.readlines()
    if network.get('essid'):
        config_file = "ap_scan=1\n"
    else:
        config_file = "ap_scan=0\n"

```

---

### Post by rsavage on 2012-08-11
I'm pretty sure I can get wicd working for you now if you want to try.

---

### Post by killabuntu on 2012-08-11
Thanks, rsavage, for that follow up info, I will get onto the network forum in the next day or so.

But to answer your questions, here are entries from today's syslog:

Aug 11 13:48:05 rays-laptop kernel: [   28.326603] airport 0.00030000:radio: Hardware identity 0005:0001:0001:0002
Aug 11 13:48:05 rays-laptop kernel: [   28.326740] airport 0.00030000:radio: Station identity  001f:0001:0008:0046
Aug 11 13:48:05 rays-laptop kernel: [   28.326755] airport 0.00030000:radio: Firmware determined as Lucent/Agere 8.70

Aug 11 18:34:39 rays-laptop kernel: [   34.260501] airport 0.00030000:radio: Firmware determined as Lucent/Agere 9.48

And I am logging into the network under wpa/wpa2 (personal).

I've just now seen your newest post re: wicd and will follow up with you in the next little while, thanks heaps for your interest in my situation. It gives us beginners some hope, thanks again. See you soon on the forum.

---

### Post by rsavage on 2012-08-11
Install wicd:

sudo apt-get install wicd

Say yes to install the extra packages.  It'll ask if you want to join the netdev group.  Press spacebar to put a star by your name and then press enter/return.

Remove network-manager

sudo apt-get remove network-manager

Say yes to remove the two packages.

Now we need to edit a file:

gksudo leafpad /usr/share/pyshared/wicd/misc.py

Use the find facility and look for "ap_scan".

Change this bit of code:

```

    if network.get('essid'):
        config_file = "ap_scan=1\n"
    else:
        config_file = "ap_scan=0\n"

```to 

```

    #if network.get('essid'):
    #   config_file = "ap_scan=1\n"
    #else:
    #    config_file = "ap_scan=0\n"
    config_file = "ap_scan=2\n"

```As you can see I've commented out (the #s) the bit of code that sets ap_scan and added an extra line that sets it to 2.

Reboot the machine.

Setup your connection.  Hopefully it will connect.

This setup will probably only work with your Airport card wifi from now on (so you'll have to undo the changes to use a USB dongle).  It probably is possible to do something more flexible with template files though.

If you are not happy and want to return everything back to how it was:

sudo apt-get install network-manager
sudo apt-get purge python-wicd wicd wicd-daemon wicd-gtk

Reboot.

---

### Post by killabuntu on 2012-08-12
Thanks, rsavage, I know that this may not work but I'll give it a go again. I did it in Ubuntu 12.10 with a negative result and I reverted to the original setup with minimal hassle. If this doesn't work and the revert is ok then I'll (hopefully) just be back to where I am now.

It is connecting relatively quickly, usually within 10 minutes of booting up, at least most times.

Thanks and here goes...

---

### Post by killabuntu on 2012-08-12
...And now, rsavage, a great big thank you, the wicd option worked!!!

At least this time I got an interface that I could use, I connected and rebooted (just to be sure it had taken) and it automatically connected.

The instructions I followed last time were different to the ones you gave me this time. The other ones didn't mention the ap_scan thing but edited a different file, can't remember which one it was now.

Anyway, thanks again for your patience with us newbies. I'll post this and mark it solved, :D Yippeeee!!!!

---

### Post by 2blue on 2012-08-12
Good to hear the wireless is finally working. Sometimes it is a bit of a struggle. Luckily rsavage is clever with these things ;-)

---

### Post by killabuntu on 2012-08-12
Yes, 2blue, it is good that something worked although I was happy to get a connection the way it was happening before as it was connecting fairly soon after boot up but better to connect straight away, the way it should happen.

And thanks again for your input along the journey, cheers.

---

### Post by rsavage on 2012-08-13
Killabuntu, that is great news!!  Is it still working or was it a fluke?!!

You've actually done me a favour by making me investigate wicd more.  I've been having multiple problems with network-manager in 12.04 (like this [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/965895](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/965895) ), but wicd seems to be behaving well.

Out of curiosity could you please tell me the ap_scan value you get from these commands:

cat /var/log/syslog | grep ap_scan
cat /var/log/syslog.1 | grep ap_scan

One thing to note is that when wicd gets updated (shouldn't happen very often) your changes will probably get overridden.  You may like to take a note of what you did to the misc.py file.

Anyway, I'm glad it worked!  If you can confirm it is still working then I'll link the post on the bug report so that others can benefit.  Thanks

---

### Post by rsavage on 2012-08-13
One thing that I think lets wicd down are the icons.  Luckily it is easy to create new ones!  

Attached are the icons I created for xubuntu.  They are just the elementary-dark network-manager icons (although I changed the no-signal icon - there are 3 versions of that to choose from).  One day I'll be more imaginative and properly make my own!

To install, extract the contents and copy the icon files to

/usr/share/pixmaps/wicd

I've included a script that should help if you want to create your own icons based on your theme.

---

### Post by killabuntu on 2012-08-13
No fluke, rsavage, it is firing up each time, cold boot and restart equally well. Thanks so much for your input and for the icons as well, I'll have a look at them and the script and see if I can come up with something original for mine.

With the output of those commands you asked about, I get no output at all from the first one, is that right??? And for the second one, I get a value of 1 but nothing for yesterday and this morning. I get results for Saturday and Sunday only. :confused:

Anyway, it is working and well too as far as I can see and I'm glad that I was able to help you to find something that can be helpful to others as well.

Thanks again and cheers.

---

### Post by rsavage on 2012-08-14
Okay that is all good.  Those ap_scan values are from when you were using network-mangager.  They confirm that you were hitting the bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/715438](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/715438) .  I've added a comment linking to the wicd workaround.  Thanks for making me aware there was still a problem with the Airport Cards.  I hate the PowerPC FAQ not having reliable info (I've linked that now too).  With your help I think we've now got a good workaround.  Cheers

---

### Post by killabuntu on 2012-08-14
I'm stoked that, in some small way, I was able to contribute to the resolution of an issue that probably affects a few people. Of course, the major kudos go to you, rsavage, because you have the knowledge to be able to suggest the right options to try.

Anyway, it's out there now and hopefully many others will benefit, great stuff. And that, folks, is the power of the forums. :D

---

### Post by bipa on 2012-11-10
Thank you very much for your efforts gentlemen.

After struggling many hours I finally got an Airport classic card connecting from an iMac G3 DV (450 MHz slot-in) under Ubuntu 12.04 using wicd.

However the situation seemed to be quite different for me so I'm adding some comments here about my experience : in case it might help other (?) users of those old machines.

My access point is configured with 128-bit WEP authentication (I know it's a bad thing but that's another story) and I kept getting that infamous authentication failure (e.g. "bad passwd" with wicd) in both networkmanager and wicd. The connection works flawlessly from within MacOS X 10.4.11 "Tiger" BTW, so there is nothing wrong with the hardware itself.

I found a lot of information about the Linux airport/orinoco driver only working with "ap_scan=2", but in fact, even after forcing "ap_scan=2" through rsavage's wicd hack, my Airport still wouldn't authenticate successfully ("wpa authentication may have failed" etc... "bad passwd").

Eventually, it is changing the firmware file /lib/firmware/agere_sta_fw.bin (actually moving it away to make the airport driver revert to the built-in firmware) that made it work. According to driver messages, my Airport card has firmware revision 8.40 built-in : apparently it does not support WPA-PSK, but the 128-bit WEP authentication works (actually I don't even know whether the "ap_scan=2" trick helped or not).

Before that I had tried two other, much more recent, revisions of the firmware : Ubuntu comes with revision 9.48 out-of-the-box, which claims to support WPA-PSK (which I could not test) but would never authenticate with my WEP-128 AP. In the process of trying to fix it, I also used "agere fw utils" to extract the latest firmware from its MacOS X "kext" (revision 9.52, don't know why Ubuntu doesn't provide this one instead of 9.48 btw, since it apparently dates back to 2007). This one seems to load correctly with the airport driver, and also claims WPA-PSK support, but still no luck for WEP-128 authentication.

I have no clue as to the differences between 9.48 and 9.52 but in case anybody wants to try the latest revision, just let me know and I'll e-mail the file or try to upload it somewhere.

My guess is that I'll be stuck again as soon as I'll dump my old WEP-128 setup and switch to a WPA access point authentication... but I have no way to test it at the moment. Maybe by this time I'll have to switch back to the newer firmwares 9.48 or 9.52.

EDIT : After disabling rsavage's wicd hack (so back to "ap_scan=1" I presume), the WEP-128 authentication still works. That's quite puzzling (given all the information about airport requiring this "ap_scan=2" thing) but it looks like my issue was merely due to the more recent firmware revisions (again : 9.48 and 9.52 won't authentitacte with WEP-128 ). There is a hint in the Ubuntu PowerPC FAQ about moving the firmware file out of /lib/firmware to force the driver reverting to the built-in card firmware : I can confirm that it helps a lot (at least with WEP-128 and built-in firmware 8.40). I'd be willing to add a confirmation about this in the FAQ but the wiki does not seem to allow such edits (page is not editable for me). If I ever try with WPA authentication at a later time (which will definitely not work with the old firmware) I'll try to remember to update this thread.

---

### Post by rsavage on 2012-11-11
bipa, thanks for the feedback.  You've confirmed my understanding of Airport Classic - i.e. to use WEP you have to use an older version of the firmware.

Would it be possible to zip up your 9.52 firmware and post/attach it here?  It may well be useful to others requiring WPA and network manager. 

> 
I'd be willing to add a confirmation about this in the FAQ but the wiki  does not seem to allow such edits (page is not editable for me).

Have you got a launchpad account?  It's a bit funny when you first log in to the wiki pages; you seem to have to do it twice.

---

### Post by bipa on 2012-11-12
Hi rsavage.

Here's the 9.52 revision of the airport classic firmware (attached).

I extracted it from the latest Mac OS X 10.4.11 Airport utility "kext" (in /System/Library/Extensions) with an extraction tool from the "agere firmware utils".

I have verified that it loads OK with the airport driver (when renamed /lib/firmware/agere_sta_fw.bin) but it did not work for me (authentication problem with WEP-128 ). I haven't tested it with WPA-PSK either but it claims it supports it (just like version 9.48 ).

Regarding the FAQ: no I don't have a launchpad account (only a "Ubuntu SSO account"). That must be the problem. I'll give it another try in a few days.

---

### Post by rsavage on 2012-11-13
Thanks.

I suspect there are two problems (please don't read this as fact):

With version 9.48 you get the wrong ap_scan value.
With version 9.48 and higher WEP no longer works.

If you have network manager installed then you can check if the ap_scan value changes with the different firmware:

```

* grep ap_scan* */var/log/syslog*

```

---

