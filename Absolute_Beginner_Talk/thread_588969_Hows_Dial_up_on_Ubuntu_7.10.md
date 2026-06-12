---
title: "Hows Dial up on Ubuntu 7.10"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by fruitsofherwomb on 2007-10-23
Man; I would have installed it last night but my burn had a file corrupted (hopefully its not the download; :( )

Ok the question is; who here has gotten Ubuntu to dial out and CONNECT on 56k/ dial up

I have a win soft modem and there is drivers for it; but I can never get it to connect (it dials out and then when it has to connect nothing happens) just checking if (hopefully) they fixed it.

 Before people say 'JUST GET HIGHSPEED' its not THAT easy; I live in a remote area. No high speed packages offered here.

Thanks for your[COLOR="Red"]** feedback **[/COLOR]

---

### Post by Dr Small on 2007-10-23
I don't have dialup anymore, so I can't give any feedback on that, but you can check your download for errors by checking the md5sum of the download.

You can find a list of the MD5sums here:
[http://releases.ubuntu.com/7.10/MD5SUMS](http://releases.ubuntu.com/7.10/MD5SUMS)

And you can check your md5sum of your download by doing this:
```
md5sum ubuntu-7.10-*.iso
```

Dr Small

---

### Post by fruitsofherwomb on 2007-10-24
Getting Ubuntu online is more important then my family. So I refuse to unlock them out of the cellar till I get Ubuntu 7.10 online. Think about the children :mad:

/[COLOR="Red"]**BUMP**[/COLOR]

---

### Post by jandjfrench on 2007-10-24
Hi,

I don't know if this will prove helpful but...

I'm using an external modem on serial port 1 but also have problems connecting.  Here's what I've noticed:
The icon in the upper right of the screen always indicates "No network connection" whether I'm connected or not.
If I click on it and then click on "Manual configuration..." the Network Settings screen is displayed.  The only option I have is "Modem connection" so I make sure the little box on the right is filled in. Then I click on "Properties"  and on the General tab I have the "Enable this connection" filled in and the rest of the data entered properly.  On the "Modem" tab I have my Modem port set to the serial port (I assume yours has your Modem selected) and Tones and Loud selected. On the Options tab I have all selected.
Now the important part: With these settings I then restart the computer and I successfully connect.  Doing anything else causes the modem to dial out, make sounds like a connection is made and then terminate the connection.
Good luck.

---

### Post by fruitsofherwomb on 2007-10-24
Helpful more; I have a internal and its a struggle of life with it (literally) its fine on Windows.I bought one external modem and found out it doesn't work with Linux (great) and can't get it to work on windows (even better).

I'm willing to buy a hardware modem that actually works easily (or easier) with windows!

My kid is tired of being locked up; GET WITH IT PEEPS!

---

### Post by rundee_f on 2007-10-24
hmmm... i'm having the sam problems with u when im home.. but i got wilan access at college...

my suggestion would be:
1. try to change your internal modem with another one that supported FREELY for the drivers in 56 kbps
2. buy an external modem
3. my solution at home -> im using my nokia 2115i CDMA + CA43 cable data as a modem an it connects to the internet..

i also still find out another better and faster way to get online at home...

i hope this reply helps u... :)

---

### Post by fruitsofherwomb on 2007-10-24
oh yeah; what 'internet service providers' do you guys use? I have PPC and I get it to dial out without software (window dialer) but people say it might not work under Ubuntu; just wondering.

---

### Post by rundee_f on 2007-10-24
i guess no matter what ur provider is, if ur modem cant connect for more then 14 kbps, u will get connection problems.. it's all in the modem.. (for dial up issue of course)

fyi im using standar national telecom provider.. T_T

---

### Post by fruitsofherwomb on 2007-10-26
I connect at (slow I know) 23kbps a second. 

I know some people will shrivel in fear at my high speed octane fused connection but its not 'that' bad. Today after class (and some nap) I will possibly take my PC to a friends house (with HS) to get online with Ubuntu and update/install stuff and HOPEFULLY get 56k working on this! 

IF I do, Joy... I have been playing around with ubuntu offline and I'm VERY impress. :lolflag:

---

### Post by edwardLS on 2007-10-26
I am in a similar situation: remote, no good BroadBand alternative, and I use Modem Dialup on two computers with 3 Ubuntu installaltions: (Dapper, Feisty, and now Gutsy)

I just installed Gutsy on a Dell Laptop (Inspiron 9100) with an internal (WinModem)  It has been an adventure, but I think I have it all working smoothly now.  When I installed it the first time, enable the Restricted Driver and attempted Dialout to my ISP, it worked perfectly.  The following evening it would not work, and I suspect my ISP.  However, several attempt at dialup with both Gutsy and Windows XP, indicated that the ISP was OK.  Further investigation indicated that the Gutsy would dial the ISP number, and the local and distant modems would attempt negotiation.  However, the negotiation never ended until the distant modem finally gave up.

The following is not worthly of being called a fix, however it worked for me.  I re-installed Gutsy.  However, before continuing with the Installation, and booted into the LiveCD, I enabled the Restricted Driver, configured my dialer (phone number login and password), and then connected to my ISP.  Convinced that the Software Driver for my Modem was correct, I proceeded with the Installation.  After the installation and reboot, I was surprised that the Restricted Driver was already enabled.  I re-did my dialer with the phone number, login, and password, and it has been working flawlessly since.

The other two installations, Dapper and Feisty use an external Hardward Modem with absolutely no problem.

---

### Post by fruitsofherwomb on 2007-10-26
Thats quite a adventure :/. Hopefully its not 'that bad' with me. What ISP do you have? (glad that it isn't impossible to get online with a 56k win modem!)

---

### Post by edwardLS on 2007-10-29
Sorry for the delay.

I use Earthlink as my ISP.

---

### Post by mikeescott on 2007-11-03
I am using PPC with an external modem. I can never get more than 4 or 5 kb/s, which is like 10 times slower than windows. My wife is using PPC on an internal "winmodem" at the same speed with the slmodem driver. How can I speed up our connections?

---

### Post by Bartender on 2007-11-06
I think PeoplePC is always going to be troublesome.  I've tried using Juno and it does the same thing - incredibly slow connection.  Both Juno and PPC use their own proprietary dialing software so that may cause trouble when you dial in without it.
Get an old USR serial modem.  I've picked up several for no more than $10 or $12 each.  If your PC only has USB then get a Sabrent cable described at the end of this thread 
[http://ubuntuforums.org/showthread.php?t=480717](http://ubuntuforums.org/showthread.php?t=480717)

Shop for an ISP that will work with Linux.  Don't ask them if they support Linux.  They'll say no.  Doesn't mean it won't work.  ISP.com is one U.S. provider that advertises Linux compatibility.  I know for a fact that Copper.net also works.

---

### Post by RJQ on 2007-11-18
I just received my Ubuntu and had installed, after a few minutes now I am online using the lucent agere winmodem, this time the distribution seems to work better with the martian drive, here is a link to my post for feisty which now works for gutsy, but this time I skip the separate "make alls" since what ever it failed then now it is fixed, I hope it helps
[http://ubuntuforums.org/showthread.php?t=513395](http://ubuntuforums.org/showthread.php?t=513395)

---

### Post by madjr on 2008-01-03
a good and cheap actiontec external serial modem:

[http://www.amazon.com/Actiontec-USB-Serial-External-Modem/dp/B000EAQ08C/ref=pd_bbs_1?ie=UTF8&s=electronics&qid=1199382608&sr=8-1](http://www.amazon.com/Actiontec-USB-Serial-External-Modem/dp/B000EAQ08C/ref=pd_bbs_1?ie=UTF8&s=electronics&qid=1199382608&sr=8-1)

works really well.

---

### Post by Raval on 2008-01-03
> **madjr said:**
> a good and cheap actiontec external serial modem:

[http://www.amazon.com/Actiontec-USB-Serial-External-Modem/dp/B000EAQ08C/ref=pd_bbs_1?ie=UTF8&s=electronics&qid=1199382608&sr=8-1](http://www.amazon.com/Actiontec-USB-Serial-External-Modem/dp/B000EAQ08C/ref=pd_bbs_1?ie=UTF8&s=electronics&qid=1199382608&sr=8-1)

works really well.

I have one of these modems it was hell to get it to work in 7.04, are you using it with 7.10? and if so how easy was it?

---

### Post by madjr on 2008-03-08
> **Raval said:**
> I have one of these modems it was hell to get it to work in 7.04, are you using it with 7.10? and if so how easy was it?

gnome-ppp will detect it automatically for you.

patched version for gutsy
[https://bugs.launchpad.net/ubuntu/+source/gnome-ppp/+bug/121487](https://bugs.launchpad.net/ubuntu/+source/gnome-ppp/+bug/121487)

[http://launchpadlibrarian.net/10692409/gnome-pppfixedforgutsy_0.3.24-1_i386.deb](http://launchpadlibrarian.net/10692409/gnome-pppfixedforgutsy_0.3.24-1_i386.deb)

this should really be included in the live-CD

---

### Post by maniac_X on 2008-03-08
> **Raval said:**
> I have one of these modems it was hell to get it to work in 7.04, are you using it with 7.10? and if so how easy was it?

You don't even need to install any drivers. Use the serial cable and it works great. I have 2 of these modems, 1 serial/usb and the other just the serial version. Both tested and working in Fiesty and Gutsy.

BTW, here's a another link for a source that has them @ $9.99+shping
[COLOR="Red"]**[http://www.unitedsale.com/product_info.php?cPath=25&products_id=17119](http://www.unitedsale.com/product_info.php?cPath=25&products_id=17119)**[/COLOR]

---

### Post by Cifra on 2008-03-08
Have you guys bothered to try ndiswrapper with Windws drivers? It's a long shot but maybe it would work?

---

### Post by Raval on 2008-03-08
> **maniac_X said:**
> You don't even need to install any drivers. Use the serial cable and it works great. I have 2 of these modems, 1 serial/usb and the other just the serial version. Both tested and working in Fiesty and Gutsy.

My Pc's video is on board and uses the only serial cable so I never got to check if the serial cable would work.

Thanks for letting me know, I'm now using the connexant internal modem that came with my Dimension 1100 and the driver offered by Dell. 

The modem sits in a plastic bag in perfect condition but with the info you have provided I'm certain it will be of great use in the future.

---

### Post by maniac_X on 2008-03-08
> **Raval said:**
> My Pc's video is on board and uses the only serial cable so I never got to check if the serial cable would work.

Thanks for letting me know, I'm now using the connexant internal modem that came with my Dimension 1100 and the driver offered by Dell. 

The modem sits in a plastic bag in perfect condition but with the info you have provided I'm certain it will be of great use in the future.

I just recently got cable internet but before that for many years I was on dial-up. And when I discovered Ubuntu I did a lot of reading up on the whole modem situation and it wasn't a pretty picture for "win-modem" users. Originally I had no issues with my internal modem(a very old Zoom HCF/Fax modem) but later internal modems I tried/used would not connect even though they were same manufacturer and and practically the same model family. After more reading I found out just how important it was for internal modem users to have particular chips on those modems.

Of course now that dial-up has basically "gone out of fashion", just about the only internals you can buy are the "win-modem" variety and you would be very very lucky indeed to get one that works in linux. The external "serial" modems are the most hassle free because usually they are recognized and working right out of the box. That's why they get reccommended to most new people. They are also starting to become hard to find as well. That's why I think I'll be holding on to the few that I have that work on linux. Never know when some situation arises where the only option might be dial-up.

---

