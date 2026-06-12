---
title: "How to get online?"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by john in vt. on 2007-06-19
Hi,
I can&#8217;t get online with Ubuntu.
Back ground. I have a duel boot HD WinXP/Ubuntu. 
I have a CD from my phone Co. &#8220;Easy Internet&#8221; Don&#8217;t know where or when to put it in. 
Also have my Access code, user name and password. The terminology is deferent, and I don&#8217;t what goes goes where.
I just put this on my computer the other day, hope you can help.
John in vt.

---

### Post by jrev on 2007-06-19
What sort of telephone line have you got ? RTC ? Broad band ?
What sort of ubuntu version ? Dapper Drake or something newer ?

---

### Post by Golyadkin on 2007-06-19
What you should do is the following:

[LIST=1]
[*] Boot into Windows XP and click on Start > Run... 
[*] Then type "cmd" without the quotes and press [Enter]
[*] Type the command "ipconfig /all" without the quotes and press [Enter]
[*] Write down on a piece of paper the numbers it gives you for ip-address, dns servers, default gateway and so on.
[*] Boot into Ubuntu
[*] Left click on the Network Manager icon (looks like two monitors) on the top right, and chose "Manual Configuration".
[*] Click on Wired Connection and click the [Properties] button.
[*] Fill out the numbers in the right places, from the piece of paper you wrote it on.
[*] Close the Windows by clicking [Ok].
[/LIST]

Now you should be online!

---

### Post by bluetracer on 2007-06-19
It sounds like you're using a dialup connection.  As long as you've got the phone number it calls, your username and your password, you won't need to use the CD from your service provider.

There is a thread [here]("http://ubuntuforums.org/showthread.php?t=308098") about getting dialup modems working in Linux.

Hope this helps.

---

### Post by sailor2001 on 2007-06-19
in ubuntu: system/network  dhcp most likely..or are you in dial-up? If dial-up check synaptics / wvdial

---

### Post by bluetracer on 2007-06-19
Further to the above, it might well be as simple as installing gnome-ppp

Go to System / Administration / Synaptic Package Manager

Click Search, type in gnome-ppp and hit the Search button.  Right-click gnome-ppp where it appears and choose Mark for Installation.  Click the Apply button in the toolbar.

Then go to Applications / Internet / Gnome PPP

Put in the username, password and access number in the relevant boxes and click connect.

---

### Post by p_quarles on 2007-06-19
> **bluetracer said:**
> Further to the above, it might well be as simple as installing gnome-ppp

Go to System / Administration / Synaptic Package Manager

Click Search, type in gnome-ppp and hit the Search button.  Right-click gnome-ppp where it appears and choose Mark for Installation.  Click the Apply button in the toolbar.

Then go to Applications / Internet / Gnome PPP

Put in the username, password and access number in the relevant boxes and click connect.
How is he supposed to do that if he doesn't have an internet connection in linux? Synaptic doesn't work in Windows. 

Anyway, the bottom line is this: you can't use the easy-setup CD in linux. If you tell us what kind of internet connection you're trying to get (wireless, ethernet or dial-up) we'll most likely be able to set you up.

---

### Post by bluetracer on 2007-06-19
> **p_quarles said:**
> How is he supposed to do that if he doesn't have an internet connection in linux? Synaptic doesn't work in Windows.

I'm pretty sure that gnome-ppp is on the CD, so he wouldn't need an Internet connection to install it.

Could be wrong, of course.

---

### Post by john in vt. on 2007-06-20
Jrev,
RTC? I don’t know what that is. I’m on dial-up.  I have “Ubuntu version 6.06”

The modem is a US Robotics 56K PCI Faxmodem for windows. (Maybe I can’t use 
This?) I have the drivers on CD.

P-quarles,
I’m on dial-up and new to all this. 

Everybody,

I’m totally new at this and hope someone can tell me a quick easy way to get on.
I’m sorry for being so long in getting back,
Please don’t lose faith will try,
Hope to here from you,
John in vt.

---

### Post by bluetracer on 2007-06-20
No worries, we all were new to this once.

Try installing gnome-ppp as per the instructions in my first post above.  This is a little program that, assuming Ubuntu has installed your modem ok (probably), will let you put in your access number, username and password, and get you online.

To save you scrolling, you can install gnome-ppp as follows:

Go to System / Administration / Synaptic Package Manager

Click Search, type in gnome-ppp and hit the Search button. Right-click gnome-ppp where it appears and choose Mark for Installation. Click the Apply button in the toolbar.

Then go to Applications / Internet / Gnome PPP

Put in the username, password and access number in the relevant boxes and click connect.

---

### Post by Bartender on 2007-06-20
john in vt. -
Welcome to the sandtrap of the Linux world, dial-up.  It is highly unlikely that your modem works in Linux.

Can you tell us anything about that USR modem?  A model number maybe?

bluetracer's directions are very helpful but you've got to get connected first.  I think so anyway.  

*Is* gnome-ppp on the LiveCD, available for installation later but not included in the default install?  I don't know.

Can you unplug your PC and take it somewhere that does have a broadband connection?  Work, school, a friend's house?  If so, plug in the ethernet cable before starting up your PC.  Fire it up, go into Networking, enable the network device (assuming you have onboard network chip or a PCI card), cross your fingers, it's fairly likely to connect.  May have to turn it off and on again after enabling network device.  Then try downloading gnome-ppp.

Gnome-ppp will help you configure a modem that Ubuntu can talk to.  But gnome-ppp won't help you any if the modem is just a cheap winmodem that Ubuntu can't talk to.  The simplest solution for that is an external serial full-hardware modem like the USR Sportster.

---

### Post by bluetracer on 2007-06-20
> **Bartender said:**
> bluetracer's directions are very helpful but you've got to get connected first.  I think so anyway.  

*Is* gnome-ppp on the LiveCD, available for installation later but not included in the default install?  I don't know.

Pretty sure it is (can't check right now - anyone?).  I figured it was worth a shot, anyway, since if a) it is and b) Ubuntu has picked up his modem (USR is pretty mainstream, so perfectly possible) then it is a quick and easy solution to his problem.

And we like quick and easy :)

---

### Post by Bartender on 2007-06-20
Hi, blue -
I've got several Ubuntu/Kubuntu/Xubuntu LiveCD's of varying ages.  Willing to check this out later today on test PC.  How would I ask the PC to look on LiveCD for a program?

---

### Post by bluetracer on 2007-06-20
Probably just cd into the relevant directory and then do something like ls -a | grep gnome-ppp*

---

### Post by john in vt. on 2007-06-20
Golyadkin,
All I got from run with “cmd” was cannot find.

Bluetracer,

I was able to bring up “gnome-ppp” When I right clicked on it nothing happened. 
I could not find “Mark for installation”
Where to now?
John in vt.

---

### Post by john in vt. on 2007-06-20
Bartender,

The USR # 5699B
This is a secure setup, the computer is bolted in place. And yes, it can be taken out, but man what a job. 

Will be back,
john in vt.

---

### Post by p_quarles on 2007-06-20
> **john in vt. said:**
> Golyadkin,
All I got from run with “cmd” was cannot find.

Bluetracer,

I was able to bring up “gnome-ppp” When I right clicked on it nothing happened. 
I could not find “Mark for installation”
Where to now?
John in vt.
That's strange. The "mark for installation" dialogue should come up whether you right-click or left-click. Try it again, and if nothing happens, make sure you are clicking right on the checkbox next to the listing. 

Of course, that could mean it's just not on the CD. 

If that's the case, you might be able to use Windwos to get the .deb package. It appears (to the best I can tell) that Ubuntu has all the dependencies in a standard installation. So: 

1. Go here:
[http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fg%2Fgnome-ppp%2Fgnome-ppp_0.3.21-1_i386.deb&md5sum=55f08ec5e5b96fe3c82e5958307506e5&arch=i386&dist=oldstable&type=main](http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fg%2Fgnome-ppp%2Fgnome-ppp_0.3.21-1_i386.deb&md5sum=55f08ec5e5b96fe3c82e5958307506e5&arch=i386&dist=oldstable&type=main)

2. Choose the download location nearest you, save it onto a CD or USB thumb drive

3. Boot into Ubuntu, import it onto your desktop, and double-click to run the package installer. 

If there ARE missing dependencies, though, dpkg won't be able to find them without an internet connection. Worth a try, though.

---

### Post by Bartender on 2007-06-21
A couple of things -
It looks like the USR 5699B is just another damn winmodem.  A pricey one, but a winmodem nonetheless.  Unless someone's written Linux drivers for it (I'm guessing that's highly unlikely) it's worthless to you in Linux.

I tried something yesterday and it worked.
[http://ubuntuforums.org/showthread.php?t=479663](http://ubuntuforums.org/showthread.php?t=479663)

I shoulda tried this a long time ago!  I'm no Ubuntu whiz.  It was simple to download the gnome-ppp package on my dial-up Windows PC, burn the package to a CD, and toss the CD into my Ubuntu PC.  The gnome-ppp package worked with Xubuntu and with Ubuntu.  After you install it gnome-ppp will show up in Applications>Internet.

For those who have a Linux-friendly external (or have successfully completed one of the arcane winmodem configurations) gnome-ppp at least provides a user-friendly interface.  

One thing I'm trying to figure out this morning is the /etc/resolv.conf file thing - you still have to create an empty file, don't you?

EDIT:  p_quarles's link is for the debian gnome-ppp package.  I used the ubuntu gnome-ppp package.  I don't know if there's any difference, but figured when in Rome...

---

### Post by john in vt. on 2007-06-21
Bartender,
I just ordered Ubuntu Ver 7.04
What do you would be a good modem that will work with both Win and Linux. (I order most I need from Ebay)
I ordered the free CD. On dual up I just can’t take that much time.
Will Ubuntu 7.04 overwrite Ver 6.06?
John in vt.

---

### Post by john in vt. on 2007-06-21
Bartender,
I just ordered Ubuntu Ver 7.04
What do you would be a good modem that will work with both Win and Linux. (I order most I need from Ebay)
I ordered the free CD. On dial up I just can’t take that much time.
Will Ubuntu 7.04 overwrite Ver 6.06?
John in vt.

---

### Post by bluetracer on 2007-06-21
Maybe something like [this]("http://www.newegg.com/Product/Product.aspx?Item=N82E16825104135")?

Or is that overkill?  What does everyone think?

---

### Post by p_quarles on 2007-06-21
I just did a quick search for Linux modems on Amazon, and found a couple with positive reviews from Linux users. You'll probably have more luck looking for online customer reviews like that, since I think that relatively few people here use dial-up modems.

---

### Post by Bartender on 2007-06-22
hi, blue -
that modem is the right kind, but you can find 'em cheaper by looking for used

---

### Post by zorkerz on 2007-06-25
John in vt.

I apologize if I missed something i did only skim the thread. 

You should check out the wiki page for dial up modems its prety helpful. 
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)
If you download the scanmodem tool in windows then use it in ubuntu it will tell you if your modem will work or not.

gnome-ppp is just a gui front end for wvdial. I think you may want to setup wvdial first although that may not be necessary.  Check out the wiki it is helpful.

By vt do you mean Vermont?  cause if you are I could possibly drop  of a feisty cd for you Im currently mostly in the Montpelier area.

Another thing you could try is to ask a friend to trade modems if they are using windows your modem will work in their computer and yo can probably find one that will work in yours.  Lots of people just ditch old computers with modems in them.

cheers

---

