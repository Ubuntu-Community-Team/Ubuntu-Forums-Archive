---
title: "Madwifi / Ndiswrapper Help - Nothing works!"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by TpyKv on 2008-03-23
Happy Easter everyone!

I am pulling my hair out! I wonder if you can help with this problem...

I have been trying to install madwifi or ndiswrapper for some time and with no success. I cannot remember all the commands now as I have tried to many, so wanted to ask for your advice...

[http://premium1.uploadit.org/mentholist//lspci-grep-Ethernet.png](http://premium1.uploadit.org/mentholist//lspci-grep-Ethernet.png)

[http://premium1.uploadit.org/mentholist//cantfind.png](http://premium1.uploadit.org/mentholist//cantfind.png)

[http://premium1.uploadit.org/mentholist//ifandiwconfig.png](http://premium1.uploadit.org/mentholist//ifandiwconfig.png)

[http://premium1.uploadit.org/mentholist//norestrictedextrasorndiswrapper.png](http://premium1.uploadit.org/mentholist//norestrictedextrasorndiswrapper.png)


I have disabled the atheros madwifi restricted drivers, but now I cannot even get the ndiswrapper packages.... there is something I am doing wrong so any help you can give would be greatly appreciated....!

Also does anyone have any experience with installing  orange USB mobile internet? I have this but can't imagine it will ever work...?

Regards,

Kevin

---

### Post by mikeyphi on 2008-03-23
Can only help find ndiswrapper - it's available through ADD/Remove - just enter 'ndiswrapper' in the search box.
Good luck with the problem.

---

### Post by which_chick on 2008-03-23
Kevin, if you've got a working windows install on the machine, try going into that and looking in control-panel -> network -> right click on the wireless and see what card it says you're using there.  Sometimes the Atheros 5007EG mis-identifies itself as a 5006EG.  (There's a way to check in the terminal window, too, if you don't have a windows install, but it's kind of complicated.)  The 5006EG is supposed to work out-of-the-box on 7.10

Are you using i386 or AMD64?  (There's a functional workaround for the i386 and the Atheros 5007 but I'm not sure of a *definitely works* solution for the AMD64 install.)

If you have the i386 install, the following is the workaround for the 5007EG card:

[http://madwifi.org/ticket/1679](http://madwifi.org/ticket/1679)  (It has an attached file with better instructions for running)

---

### Post by TpyKv on 2008-03-23
Cheers Mikeyphi - but that didn't work.... :(

Which_chick - thanks also! printout below - 

[http://premium1.uploadit.org/mentholist//windozw-printout.jpg](http://premium1.uploadit.org/mentholist//windozw-printout.jpg)

I dont seem to have the control panel-network-right click part that you speak of

 - does this tell you what we are looking for??

It is an i386  - a Sony Vaio VGN-NR10e - Dual core 1.5 ghz, 2GB Ram... will this patch work? 

thanks again!!!

---

### Post by TpyKv on 2008-03-23
Bump :)

For anyone reading, I need to determine my atheros card (have I given the correct info?) before I *try* to install this patch. 

Alternatively if there are 500 of you that would like a £1 piece of laptop, let me know before I start breaking things...& let's get a list going.... 

:)

---

### Post by scottro on 2008-03-23
[http://home.nyc.rr.com/computertaijutsu/rhhw.html](http://home.nyc.rr.com/computertaijutsu/rhhw.html) gives info on seeing if it's an AR5007EG

---

### Post by TpyKv on 2008-03-24
Thank you Scottro,

I did this and it looks as if I have the 168c:001c card, even though it says it's an AR5006 instead of AR5007...

[http://premium1.uploadit.org/mentholist//wireless-details.jpg](http://premium1.uploadit.org/mentholist//wireless-details.jpg)

I'll give Which_Chick's suggestion a go and see if it works :)

---

### Post by TpyKv on 2008-03-24
OK now I'm seriously confused, that ticket is not good for newbies...far too confusing...

Can anyone please tell me which file I need to extract/patch? 

there are two options - 

[http://premium1.uploadit.org/mentholist//whichfile.png](http://premium1.uploadit.org/mentholist//whichfile.png)

any advice would be greatly received...!!

---

### Post by mikeyphi on 2008-03-24
Use this one, where the site says: Alternatively you can download a readily-patched snapshot_ from here_.

[http://madwifi.org/ticket/1679](http://madwifi.org/ticket/1679)

---

### Post by TpyKv on 2008-03-24
thanks Mikey,

I tried that....did everything the ticket says - but when I go to do the patch command, the terminal says no such file or directory!!?!? 

is there a by step guide on how to do this, that newbies can understand??

---

### Post by mikeyphi on 2008-03-24
> **TpyKv said:**
> thanks Mikey,

I tried that....did everything the ticket says - but when I go to do the patch command, the terminal says no such file or directory!!?!? 

is there a by step guide on how to do this, that newbies can understand??

As I said - you MUST navigate in the terminal to the directory where the file is!!! otherwise the file won't be found!!

Try this code:
(make sure each command has finished before inputting the next!)

sudo apt-get install build-essential
wget 'http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz'
tar zxvf madwifi-ng-r3366+ar5007.tar.gz
cd madwifi-ng-r3366+ar5007
make clean
make
sudo make install
reboot

---

### Post by TpyKv on 2008-03-24
thanks again... but I must be too stupid to use linux.

I did everything you said up - got to the - 

tar zxvf madwifi-ng-r3366+ar5007.tar.gz

command and it still cannot open, no such file or directory, error is not recoverable, exiting now, child returned status 2, error exit delayed on previous errors

Is there anything else I should try? 

thanks for your patience, don't know where you get it from

---

### Post by mikeyphi on 2008-03-24
Did you see (in the terminal) the file 'madwifi-ng-r3366+ar5007.tar.gz' being downloaded and saved?

You should be able to 'copy and paste' each command - thus avoiding typos

If the file downloaded then the 'tar zxvf..etc...should find the file (unless somehow your system saves downloaded files to a different location)

Try again! If it doesn't work - look to see where the downloaded file is located - report back!
Don't give up yet!

---

### Post by TpyKv on 2008-03-24
I copied and pasted the EXACT commands and still have the same error....
i have found the file in /home/kevin...

so surely the command should work!!?!?

---

### Post by mikeyphi on 2008-03-24
Well, well - my typo!!!!

the ng should read nr!!!!

Use this in the terminal - should work now.


tar zxvf madwifi-nr-r3366+ar5007.tar.gz
cd madwifi-nr-r3366+ar5007
make clean
make
sudo make install
reboot

---

### Post by TpyKv on 2008-03-24
aha! 

I found the file and it is madwifi-nr instead of madwifi-ng :

madwifi-ng-r3366+ar5007.tar.gz

and this worked!! damnit that was painful :)

thanks for your help!!!

now I have wireless i can try to find out if the Orange Icon 2 USB mobile internet device will ever work! wish me luck :)

---

### Post by em3raldxiii on 2008-03-24
WOOT.  This *looks* like exactly what I am going to need.  Thanx to all three of you guys for going through this so concisely - it would be nice if every "help session" on this forum went this newbie-friendly :D

Cheers!

PS.  I will try following through this once I am at home on my own computer (at work 300km away right now).

---

### Post by scottro on 2008-03-24
I have a more newbie friendly guide at

[http://home.nyc.rr.com/computertaijutsu/rhwireless.html#5007](http://home.nyc.rr.com/computertaijutsu/rhwireless.html#5007)

---

### Post by TpyKv on 2008-03-24
The level of support for Ubunutu is ACE, I owe you guys :)

Only problem now! (you knew it was coming) is that when I reboot, all the wireless options have been lost. 

Is this to do with an ndiswrapper conflict?

---

### Post by TpyKv on 2008-03-24
Just reading your guide...

I typed ndiswrapper -l and it's saying there are no ndiswrapper utils found. So it can't be that making it lose the settings after reboot...must be something else...

and there is no ndiswrapper file to delete in /etc/modprobe.d 

...

---

### Post by TpyKv on 2008-03-24
OK now it works again!

I think it could have been down to two reasons,

after running the commands and rebooting, I may have booted into solaris or vista by mistake... 

and I disabled "enable roaming" - after running the commands again I was able to re-enable :)

many thanks to all involved... now I can rest peacefully :guitar:

---

### Post by AlanB66 on 2008-03-26
I feel your frustrations. It's not as easy as some people have posted.

Go this this link:
[http://ubuntuforums.org/showthread.php?p=4588599#post4588599](http://ubuntuforums.org/showthread.php?p=4588599#post4588599)

Follow my instructions I've put towards the end of the thread.
It should work.

---

### Post by TpyKv on 2008-03-26
thanks for that, but it's already sorted now :) Scottro's help worked & now wireless is always there. Only thing is the light does not come on when you flick the switch but I can live with that..

haha!

---

### Post by scottro on 2008-03-26
The only way I ever got the light working was with ndiswrapper and the net5416 driver.  However, I found the consistancy of ndiswrapper to be poorer than MadWifi. (Others have had the opposite happen, but for me, MadWifi was always better.)

It stayed steadily on, not blinking to show activity and after a brief flurry of excitement that I'd gotten it lit, it became an annoyance to me, as well as something that probably shortens battery runtime. 

It's amber, if anyone cares.  :)

---

### Post by em3raldxiii on 2008-03-29
I think this thread should be made sticky or something ... :D ... I can't wait to give it a try.  Unfortunately, I was only home for 2 days and didn't get the chance.  Now I am at work 300km away for another 6 nights.  I will post my results when I give it a try.

---

### Post by TpyKv on 2008-03-30
I'll leave the light idea alone then, thanks...

Good luck with getting yours to work em3raldxiii....

I'm now trying to get an Orange mobile internet USB card  working...i know this is possible but not for the one I have. 

enjoy the rest of your weekend

---

### Post by abhilashkumar on 2008-04-03
> **scottro said:**
> I have a more newbie friendly guide at

[http://home.nyc.rr.com/computertaijutsu/rhwireless.html#5007](http://home.nyc.rr.com/computertaijutsu/rhwireless.html#5007)

Your guide restored my faith in Linux :)

I had almost given up on getting wifi to work on my 64 bit distro. But after going through your guide I have now gotten wifi to run smoothly.

Thanks a lot man.

---

### Post by scottro on 2008-04-03
I'm impressed, since my guide didn't really cover 64 bit.  So maybe your faith should simply be restored in yourself.  :)

Anyway, glad you got it working.  I keep thinking of trying to organize a massive campaign of Linux/BSD users to boycott one manufacturer at a time, till they start making sure all of their hardware is Linux compatible, and if it isn't, buy from other hardware manufacturers.

---

### Post by abhilashkumar on 2008-04-04
It didn't work on 64. :(
I installed 32. :)

---

### Post by scottro on 2008-04-04
That's ok, you still deserve credit for not giving up.  Look at these forums and all the posts from people who did give up.  

Anyway, glad it helped.

---

### Post by TpyKv on 2008-04-04
Giving up is easy - making it work is much more rewarding! 

I've just bought all the skillsoft web based courses for the LPI certification, in the hope it will get my skills up to an acceptabel standard and it's waaaaay more interesting than reading books!

I am *this* close to having my USB datacard work in Ubuntu, then I'm deleting Vista! woop!

the boycott idea is a great one - let's start with Sony first :)

nice one again!!

---

### Post by abhilashkumar on 2008-04-04
Next Step: GAMES

---

### Post by TpyKv on 2008-04-07
Tell me about it,

the only problem is you need the internet to be able to make anything work, quickly, and I am never, ever at home to be able to do so. 

I have an orange mobile internet device so I can get over 100k out of the air :) but I can't use it in Linux yet....

as soon as I can - vista is going!!

Edit - VMZ kindly told me how to get the mobile card working, today is a great day for technology :)

---

### Post by kammpler on 2008-04-13
> **TpyKv said:**
> Happy Easter everyone!

I am pulling my hair out! I wonder if you can help with this problem...

I have been trying to install madwifi or ndiswrapper for some time and with no success. I cannot remember all the commands now as I have tried to many, so wanted to ask for your advice...

[http://premium1.uploadit.org/mentholist//lspci-grep-Ethernet.png](http://premium1.uploadit.org/mentholist//lspci-grep-Ethernet.png)

[http://premium1.uploadit.org/mentholist//cantfind.png](http://premium1.uploadit.org/mentholist//cantfind.png)

[http://premium1.uploadit.org/mentholist//ifandiwconfig.png](http://premium1.uploadit.org/mentholist//ifandiwconfig.png)

[http://premium1.uploadit.org/mentholist//norestrictedextrasorndiswrapper.png](http://premium1.uploadit.org/mentholist//norestrictedextrasorndiswrapper.png)


I have disabled the atheros madwifi restricted drivers, but now I cannot even get the ndiswrapper packages.... there is something I am doing wrong so any help you can give would be greatly appreciated....!

Also does anyone have any experience with installing  orange USB mobile internet? I have this but can't imagine it will ever work...?

Regards,

Kevin


hi kevin, last week i had the same problem as you had, my answer was insert the distro Cd when i try to install Ndiswrapper, the synaptics took the packages from the cd and install it, that was all, just remenber, start your Os normally, an then insert the distro Cd, don't start from live Cd.

i wish this tip could help you, sorry if a have some grammar mistakes... |o|

---

### Post by abhilashkumar on 2008-04-15
After I installed the latest system upgrade to hardy... the wifi has again stopped working...
I did a make...make install... modprobe all over again.... it worked once... showed me my wireless network but didnt connect...

then i restarted and tried modprobe again, but this time it is not showing me the wireless network;...

what to do now?

---

### Post by abhilashkumar on 2008-04-17
I tried using ndiswrapper also after removing madwifi... 
still the wifi refuses to work.

Any suggestions...

---

### Post by abhilashkumar on 2008-04-17
Since ndiswrapper and madwifi were not working on my laptop after the latest hardy online update, i was looking in synaptics for something to help me.

I found Wifi Radar. This progy detected my wifi network and connected to it when i gave the necessary arguements in the GUI.

Those having problems with wifi on acer 4520 can try this...

At this time ndiswrapper is still installed.

The program asks for a WPA driver. I didn't know what that meant so I just put in wpasupplicant there.

It connect and gives good speeds and whats even better... THE WIFI LED WORKS better than it used to in windows.

HA HA...

---

### Post by TpyKv on 2008-04-19
kammpler &  abhilashkumar - good effort!! happy to see it's working. 

Going to give wifi radar a go, i liked having no proprietary software on my machine.. :) 

take it easy,,,,

---

### Post by abhilashkumar on 2008-04-20
Correction to my post...
The wpa driver will either be madwifi or ndiswrapper. you can check by putting in wpasupplicant in terminal and checking the output there.

However now I am using something even better and simpler to use.

WICD... Try it... Configuration is easier than WIFI RADAR... At least i think so...


Good Luck

---

### Post by ninetoes on 2008-04-29
> **mikeyphi said:**
> As I said - you MUST navigate in the terminal to the directory where the file is!!! otherwise the file won't be found!!

Try this code:
(make sure each command has finished before inputting the next!)

sudo apt-get install build-essential
wget 'http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz'
tar zxvf madwifi-ng-r3366+ar5007.tar.gz
cd madwifi-ng-r3366+ar5007
make clean
make
sudo make install
reboot

Thanks this worked for me after changing the ng to nr using a hp pavilion dv6704nr system with vista ninetoes

---

