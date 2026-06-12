---
title: "speedtouch usb modem. Hmm"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by MichaelSM on 2007-04-27
This is very much more complicated than it should be. I've read every post I can find, but most of them date back to the 1800's (joking).

Tonight I downloaded  speedtouch_1.3.1-2_i386.deb which looked perfect so I tried to install it with GDebi. It returned the following:

Error: Dependency is not satisfiable :hotplug.

I'm using Edgy, by the way ....worries for all...

OK. so let's look for hotplug ....download...

/home/michael/Desktop/hotplug_0.0.20040329-11ubuntu10_all.deb.  Cool.

Open Gdebi. 'All dependencies are satisfied.' Okey dokey. Click "Install Package." Should be good. BUT....

No go. I can't copy and paste it, but there's a conflict with udev and hotplug,

'Conflicting packages: not installing hotplug'  was the last line.

Any ideas?

Mike.

---

### Post by alexjhill on 2007-04-27
Ditch the USB modem? 

That'd be my advice we have those here at work and they are horrific with XP let alone linux.... Routers are so cheap now why not get one?

---

### Post by MichaelSM on 2007-04-27
Thank you for your instant reply alexjhill. I'm on the net at the moment using a D-Link LAN router or modem. Because I live in a rural area without 'real' power, I have to use either a generator or an inverter coupled to batteries/solar. The D-Link modem/router craps itself with the tiniest voltage fluctuations. I got my USB ADSL unit from one of the Telstra  techies a year or so ago when I was running XP. It was the most reliable connection I've ever had. Being USB, it runs, or used to run, on a small voltage which was percentage-wise hardly shifting at all. Which was why I liked it, and so did the techies! It was their instrument of choice when testing connections. 
As I said, it worked like a dream with XP. Too bad I can't be bothered with MS any more. Which is why I'm Ubuntu now.
I took a long time explaining something so simple.
I appreciate your time, my friend. 
Cheers,
Mike.

---

### Post by alexjhill on 2007-04-27
Ah yes well that makes sense. I had a similar problem back when i had a speed touch a few years ago i'm almost certain i had to modify some entries to make the thing work with BT here in the UK.
 Tho this was with Red hat Linux. I'll see if i can find anything i came across when i had that problem.

---

### Post by MichaelSM on 2007-04-27
Maybe I''m a simpleton. When I look in Devices there's a huge list of stuff regarding the Alcatel USB modem. All there with bells and whistles. In Networking there's even an extra entry for possibilities. EthoO and Etho1 and Dial-up. when I ran lsusb I got 

michael@michael-desktop:~$ lsusb
Bus 004 Device 002: ID 0ecd:a100 Lite-On IT Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 06b9:4061 Alcatel Telecom SpeedTouch ISDN or ADSL Modem
Bus 002 Device 003: ID 04f9:0173 Brother Industries, Ltd 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:0a02 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  
michael@michael-desktop:~$ 

Which shows the blasted thing is there.

It must be an easy trek from now on.

Any help appreciated.

Cheers to all,
Mike.

---

### Post by paolo di canio on 2007-04-28
Maybe you'll find useful this [[COLOR="Red"]link[/COLOR].]("http://wiki.ubuntu-fr.org/materiel/modem_adsl_speedtouch_330_speedtouch_ng")
I know, it's in french, but you can use [[COLOR="Red"]google translate[/COLOR]]("http://www.google.com/language_tools").That's how I did it.

Good luck ! :)

---

### Post by Malibu Illusion on 2007-04-28
Heya,

Have you checked out [this page](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html) in regards to the Speedtouch USB?

I'm using the same modem and use that method with every distro I use.  Works fine.

---

### Post by MichaelSM on 2007-04-29
Thank you Paolo and Malibu. Delighted with your responses. I followed instructions from the French contributor which seemed simple and perfect; unfortunately, no luck. Re French Connection, there were some inputs required (VCI or something) which my ISP (Optusnet, Australia) basically laughed off when I enquired, because we use DHCP which switches all over the shop for security reasons I suppose. 

The main thing about the SpeedTouch I understand is that it accesses DSL but, unlike the small array of Ethernet LAN modems/routers I have; not only does it require specific drivers for one's OS, but (and I discovered this when I had XP) you get on line with a SpeedTouch USB as if it were a dial-up modem. In other words, it needs a dial-up number, password etc. plus the drivers, to operate. 

Because it looked like too much hard work, I shunned the link Malibu sent. That's the next stop! If it worked for him, it should work for me. I just was a bit appalled about splitting files and sending them all over the place. 

In the meantime,  my SpeedTouch USB, denied a line connection, is blinking at me, and I cannot assist it! It thinks it knows what it has to do, but it can't....

Regards, 
Michael

---

### Post by MichaelSM on 2007-05-01
Hello to Malibu. After a lot of uncertainty, I accessed the link you provided. Maybe my PC is clutterd by previous attempts to get my Stingray working. Including SpeedBundle and lots of other crap. I did what I was told, to no avail, but what's important to me is that for instance, if I get to it, I'll install Ubuntu on a spare HD and do it as a complete virgin, if you know what I mean. Without all the other stuff. The Stingray modem is or was a popular item in Europe, and it was the item of choice with Telstra Techies in Australia with Windows testing connections. I was lucky to get one; Funnily enough, the CD which came with it (later) messed up the connection I had with XP. I had to revert to the latest drivers to get it up and running in XP before I ditched it. XP I mean. 
I appreciate your advice. There's a slight matter of misunderstanding in the link you gave me. It's to do with planting files in places. Is it simply just a matter of copying and pasting inputs into Terminal, or was there a mention of something re. file-splitting which meant reading between the lines? 
Regards, Michael.

---

### Post by mckryptyk on 2007-05-02
The alcatel Speedtouch USB is actually a very good 'dumb' modem. 
Once you have it working it will keep on working. 

I used to use one for a long time until I upgraded :)

You will need to follow the howto below.

I have also included a few links of interest.


go here for the howto:

[http://www.linux-usb.org/SpeedTouch/ubuntu/index.html](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html)

and then here for your VPI and VCI values
(I think yours is 8 / 35 but you should check)

[http://www.patton.com/support/faqs_detail.asp?id=142](http://www.patton.com/support/faqs_detail.asp?id=142) (for vci/vpi values)


miscellanious notes / links:

** NOTE: it says brazil 0 / 35 but some parts of northern usa and canada use it too, this just means that most ISP's share these values. So try 8 / 35 and then try some other ones if it doesn't work. **

search for "'vci" when you go here  to find it quickly:
[http://www.mail-archive.com/speedtouch@ml.free.fr/msg04203.html](http://www.mail-archive.com/speedtouch@ml.free.fr/msg04203.html)

search for "'vpi" when you go here  to find it quickly:
[http://bc.whirlpool.net.au/forum-replies-archive.cfm/703590.html](http://bc.whirlpool.net.au/forum-replies-archive.cfm/703590.html)

Good luck and someone should write this into a definitive howto :)

---

### Post by _L_ on 2007-05-04
Same goes for me ... it's the 2'nd day I spend trying to conFIGURE it out ;)

---

### Post by mckryptyk on 2007-05-08
Has your problem been resolved? 
If not post back here and let us know.
Also if any special steps were taken to get it working let the community know, that way everyone benefits from what steps you have taken to remedy the situation.

I'll check back here in a few days.

Cheers.

---

### Post by MichaelSM on 2007-05-09
Thank you MCKRYPTYK for your latest reply. 
Short answer: No I haven't been able to get the Speedtouch going yet.
Long answer:  When I was trying this set-up over a week or so, I installed a lot of stuff on this particular HD and possibly it's got some conflicts. My next step which might sound a bit stupid (that's me!) is to scrub a spare HD and load it up with Edgy. I'll do this soon. THEN, I'll use your previous post's suggestions and see what happens. I spoke the other day to a representative from my ISP (OptusNet in Australia) and he was a nice bloke. 
ON the record, OptusNet a) doesn't support Linux and b) doesn't support any modems other than the dsl LAN ones they send us. 
OFF the record: a) the SpeedTouch is a perfect USB modem, just get the drivers you need and go for it ( our Telstra techies have until recently used them as testing equipment across the board) which I think I mentioned beforehand, and b) there's no major issue with Linux at all. No,  I can't help you, but read between the lines, mate. Pull your finger out and get your drivers together! 
Well that made perfect sense.
As soon as I have any success, I'll let everyone know. 
It will be there with bells and whistles. 

As a long PS. Bear with me here. This might jolt somebody's memory!

When I  used the SpeedTouch with XP, I had to configure it as a dial-up modem. This was at least a year ago, which is why I'm a bit soft on it. In other words, the modem apparently needed a number to 'dial' rather than lucking onto a DHCP. Sorry if I'm talking S%#t. I must have tried that with Ubuntu, but it didn't work, due to the disabling of Admin>Networking>etc. Hmm. I might fiddle with wvdial and see what happens.  Another long night ......
Thank you again for your advice.
Regards as always,
Michael.

---

### Post by mckryptyk on 2007-05-09
MichaelSM: You have jolted my memory :).
 I now remember that you do use it as a "dial-up" modem and that I had a bash script that did the dialing/authenticating for the modem.
It also connected the internet for me on start up. 
The steps for you to use are included below:

*Do you use i386 or amd64? if you use amd64 you will have to compile the "brtcl-whatcha-ma-thing" thing (let me know then I'll find sources/dependancies for it. It wasn't hard if I remember correctly)

(Tell me the output from this command below)
This is to find the modem version (you will need to know this)
Also they call the modem "green" but my old one was a "dark-ish gray" but they consider that "green". (what color is yours)
"awk '/4061/ { print $5 }' /proc/bus/usb/devices"

revision 0 or a revision 2 modem use this firmware
The zip also includes firmware for revision 4
[http://www.speedtouch.com/download/drivers/USB/SpeedTouch330_firmware_3012.zip](http://www.speedtouch.com/download/drivers/USB/SpeedTouch330_firmware_3012.zip)
or this if revision 0 is tempermental
[http://download.ethomson.com/download/speedmgmt.tar.gz](http://download.ethomson.com/download/speedmgmt.tar.gz)

follow this link until you get to the "If your ISP uses PPPoE skip down to the PPPoE" section
[http://www.linux-usb.org/SpeedTouch/ubuntu/index.html](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html)

If you use PPPoATM continue down the linked page. 

If you use PPPoE go here next
[http://www.linux-usb.org/SpeedTouch/ubuntu/index.html#pppoe](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html#pppoe)

*When it says using Dapper "do this" or "go here" pretend you are using dapper even if you are using edgy.

*your firmware belongs in "/lib/firmware" (make sure it's permisions are correct)

*Also when you plug in the modem does it flash solid green on both lights (this is all from memory :) ) and then does one (the left light?) stay green while the other blinks? (red or is it orange?). (double green means internet on old revision 0 modem)

I'll check in from time to time to help with this. I do hope you write a guide if you get this working.

Cheers.

---

### Post by MichaelSM on 2007-05-09
Thanks for getting back so fast. The output of the command was 0.00 which I assume means a Rev 0 Stingray.  And my box is i386.

In /lib/firmware there's t files and nine text items. Probably too many; does that matter? They're all speedtouch related. 

So far as flashing lights on the modem are concerned. Um, I'm colorblind , but they seem to behave as they did when the modem was used with XP.  Two steady lights after some flashing. I'll get someone to look at them for me.

I went through the activities again as per the linux page. No luck as yet. 

I wish I knew how or where to enter the a telephone number for the modem to dial. I've tried to do that in both Gnomepp and KPPP but they can't interrogate the modem. Why?

I'll keep at it.

Mike.

---

### Post by mckryptyk on 2007-05-09
Well the good news is I can solve this! :)

I had the stingray rev 0 and it is a gray-ish modem but the guide calls it green :confused: 

you are using i386 so no compiling is necessary.

If both lights are green than the firmware is loading correctly :)

and it is just the initialization script that authenticates for you that we need to fix.

I'm going to write some scripts that will automate some of this for you.
Will post back soon.

Cheers.

---

### Post by mckryptyk on 2007-05-10
I just had the forums eat my post so here it is again. :mad: 

I just scripted a firmware splitter/installer.
The script resides in your home diectory
and creates a folder called speedtouch.
everything happens in speedtouch so it doesn't clutter you home directory.
The script splits and installs the firmware to /lib/firmware and sets appropriate permissions for it.
It also cleans up after itself.
It downloads br2386ctl to /home/user//speedtouch/br2385ctl/br2386.deb
I haven't done anything with it yet because I didn't know if you have PPPoE or PPPoA.
I'll post more when you can tell me.

Here is what I need you to do while using the script:
1) Download my script to your home directory
2) chmod +x speedtouch-script
3) ./speedtouch-script

The script will ask you via "gksudo" to authenticate
This is so it can clean up after splitting the firmware
and to set the correct permissions so ubuntu can use it.

At the end of the script it will bring up gedit and I will need you to copy into gedit.
(If you do not have gedit,
open the script with "kate" and change the words "gedit" to the words "kate")

In gedit/kate add what I have written below:

:)"username@isp" "*" "password":) 
COPY EVERYTHING IN BETWEEN THE :) (sorry for the yelling but it is important) 

Your username is your name given to you by your isp 
for example 
OpTus234@optus
your password is your isp password
*optus could also be optus.au, or rogers.ca, etc. 

Save this. (it should be called secrets)

Now run this command to install the authentication:
cd ~/speedtouch/config/secrets
sudo install -m 600 secrets /etc/ppp/chap-secrets &&
sudo install -m 600 secrets /etc/ppp/pap-secrets 

I will write more when I know if you are you PPPoE or PPPoA.

I hope this helps.
See here for more info:
[http://www.linux-usb.org/SpeedTouch/ubuntu/index.html](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html)

Cheers.

(BTW This will leave a folder called speedtouch in your home directory.
It's structure is important for the next script I'll write once I know what PPPoE/PPPoA 
connection you have.)  I had to call it speedtouch-script.txt to upload it.

---

### Post by MichaelSM on 2007-05-10
Hello again! I'm more than delighted that you're prepared to do so much work on this on behalf of what must be a fair few people who'd like their SpeedTouch working in Ubuntu, ESPECIALLY ME!

Oz uses PPPoE. I'm pretty sure the code for Australia (the VX.VY one) is 8.35.

Being a bit of a newbie, some of this is a bit daunting, though I've learned a bit about Text Editor and fiddling with things. 

My only concerns revolve around the amount of crap I've already input to the system; there's SpeedTouch everywhere. I've run through and done most of what's on the Linux(Ubuntu) page but there's obviously something simple missing. And, I don't mind being yelled at one bit! Is there a command I should use to clean things up before trying again?

I haven't looked at your script attachment yet, presuming it'll need some fiddling re. PPPoE.

PS. I've cleaned everything related to SpeedTouch etc. out of my Home folder or directory and stored it in a file on Desktop so there's no confusion at the easy end, if you know what I mean. I won't get queries about landing things in places they already exist, sort of. I have never done a computer course, so this is all fascinating. One last question; is case-sensitivity an issue when entering the ISP name? 

I've been careful to use all the " s in the right places, with correct spacing; what does the * in the middle signify? Also, believe it or not, I can't find someone to tell me what OptusNet's ISP name actually IS ... I mean, is 'Optus' what's required, or should it be 'OptusNet' ....? I'll find out before I do anything further. 

Please excuse my long-winded replies. It's the only way I can think.

Thanks again,
Michael.

PPS. A neighbor of mine just visited to verify the modem lights colors. 'Green on left, blinking red on right, flash of green, back to red..(plug in telephone line) ...red on right, no green, red ,green green. Yup. Both settled on green' You sure? 'Yep, both green. How come you can't see that?' Don't worry, thanks 'Rinda. Now that's with the firmware I've previously installed, which has a different number-code from your one which I haven't input yet. At least we know the modem is thinking right.

---

### Post by MichaelSM on 2007-05-10
I just spoke to a dude in Mumbai who informed me that my ISP's name is 'optusnetdsl' which was great news. All lower case(?) and one word, no dots. Now, how on Earth do I re-visit where I've been-probably most of the galaxy- to alter the ithe ISP names I've input at various times, or just run through the install as if nothing ever happened? 

I knew the whole shenannigan must have been hanging upon one specific input - in this case, a incorrect ISP name - so where to now? No wonder the bloody modem couldn't connect. It didn't have a destination it could cope with ....

Won't do anything until I hear from you again. I'm used to hopes dashed!

Best wishes, Michael.

---

### Post by mckryptyk on 2007-05-10
Well, I'm now writing the next part of the script, so it shouldn't be too much longer. (PPPoE method)

I will need to know which previous method you have used to get your modem working as the previous installations will conflict with the new script I'm writing. 

The script will be divided  into parts to make it easy to follow along with and I will post clear details when it comes time to install it. (Should be done later today) 

Please do not install what I have attached before. (speedtouch-script.txt)
Feel free to have a look at it though. (it's ugly but it does what I intended it to do)

I will need links to the homepages of the previous methods that you have used, so that we can "work-backwards" to undo what has been previously installed. (There may be items in /etc/rc0.d--/etc/rc6.d)

Cheers.

---

### Post by mckryptyk on 2007-05-10
Here it is Revision-02 of the script(s) for PPPoE only. 

They are now numbered and have been tested so they wont damage anything and are completely removable.

Just follow the numbered order of them and you should be fine.

The scripts are named according to the sections in the following [LINK]("http://www.linux-usb.org/SpeedTouch/ubuntu/index.html")
to make it easier to follow along and see what they are doing.

Also go [HERE]("http://www.linux-usb.org/SpeedTouch/ubuntu/index.html#pppoe") for the PPPoE section of the first link.

This is the link to the [MAILING LISTS]("http://www.linux-usb.org/SpeedTouch/links/index.html") of the above guide.

Cheers.

---

### Post by MichaelSM on 2007-05-11
I have that .tar.gz on my Desktop. I had a peek inside ... a few questions ;

I'm not sure I've worked extensively with scripts; Do I C&P them, unit by unit, into Terminal? Well, that would make sense ..or is it line by line? 

I haven't cleaned out any previous files yet; should I? 

Do I need to download a a speedtouch .deb first? I didn't see one in the scripts.

Since you have worked it so as to make it easy for a beginner, I guess I'll get prompts for gedit (saw them there -yes I 'have' gedit.)

RE. Q2 here. I've done re-installs before, and when terminal finds I'm gonna replace something which is already there, I usually go 'y'. OK? I obviously do not want to stuff this up!

Probably my first two question are the most important........

Thank you, MCKRYPTYK. I'll await your reply.

Michael.

---

### Post by mckryptyk on 2007-05-11
Hi Mike,

I'm going to answer your questions one by one, here goes:

You will have to clean out all the previous files from any other install attempts including my first script.
(You might be able to skip this part but I doubt it will work then)

You can delete the speedtouch folder from my first script made in your home directory. 
(new script makes a new one)

The Good news is you won't have to download anything. The script takes care of downloading and installing all .debs needed. (1 only) 
(it even downloads the correct firmware for your modem and prepares/installs it :))

You will then have to right click on the tar.gz file and select extract, you may have to rename this folder to 
" speedtouch-rev2 " if it isn't already.

Next you will have to open the terminal and type/copy-paste (without quotes) this: 

"chmod +x ~/speedtouch-rev2/*.txt"

That command will mark the scripts as executable, so they can be run. (chmod +x)


Now in the terminal you will type "cd ~/speedtouch-rev2"

This command will take you to the script directory. (It uses the ~ to mean your home folder.)


Before you run the scripts I suggest you open firefox and look at the webpage in my previous link.
(The first one about speedtouch and ubuntu and the PPPoE one, they are the same, just different sections)

You can look in the script folder for the names of each script and search for them in firefox using "ctrl+f" .(find) (but remove the 1 or 2 etc. in the name from the search)

If you type in the scripts name it will take you to the section that the script is 99% based off of.
The script uses the same file names as the howto webpage for easy following 

The script will ask you to type in your password each time it requires it, in a graphical dialog box. 
(that is called gksudo)

You will have to copy/paste/edit the sections from the web page to the gedit window and click save when done.
(The section you will copy from the webpage is the same name as the file you will save into)

For example, in firmware-install1 you will need to search for "secrets" in firefox. It will show you this:
:)"username@isp" "*" "password":) (I know you must remember this part)
Copy from the green boxes only.
Edit it to include your isp details (all undercase for isp-name in this example)

For the rest of them you will search using the name of the script.

For example:
for secrets2.txt you will search for "speedtch"
for speedtch3.txt you will search for "dial"
(sorry about the confusion)

for bootscripts4.txt and cleanup5.txt you will not have use gedit at all.
(you should still read about them anyway on webpage) 


Now to run each script you will type:
" ./*1.txt " or " ./*2.txt " etc. (don't forget to skip the quotation marks when copying)

Hope I was precise enough, I don't want to cause confusion or unnecessary complication either.
The script is real ugly inside but it is 99% base off that website and that is how I got my modem working long ago (when I use to use the speedtouch).

Once all the wrinkles are ironed out, I will rewrite the script so it is nicer internally and more user friendly.
(It was a rush job, so you could get internet up)

Cheers.

---

### Post by MichaelSM on 2007-05-11
Hello my friend. Unfortunately you have met a fool. Me. Your last post left me gasping for breath, figuratively speaking. Too much info.

These things can cascade of their own accord. Dunno why, but it happens.

Let's get back to square one. 

1) Firmware for the speedtouch is installed (the lights are both green) Which means I suppose that the modem is in the right place and conversing with Ubuntu.  Well, as far as I understand it, that's what the firmware is supposed to do. 

2) As of previous installs, drivers are in place, including the bridging PPPoE /home/michael/ SpeedTouch Software/br2684ctl_20040226-1_i386.deb

What was always missing was the correct ISP name originally entered into 'secrets' and it was the wrong one, to my regret. I've mentioned this before.

Let's assume that all protocols have been followed up to the stage of entering  username@ISP followed by password. I've done everything by the book EXCEPT to enter or re-enter the ISP name correctly. I suspect that that's all I really have to do. In other words, I have to sudo gedit the file which contains my username and ISP and password, and should just alter "optusnet" to "optusnetdsl" Is that a fair way of looking at it? Trouble is, I don't know how to edit that particular file.

I just got back from work and it's a bit hazy. Lots of things to do.

Your patience is extraordinary. I'm doing my best.

"'ave a good weekend."

Hi from downunder.

Michael.

---

### Post by mckryptyk on 2007-05-11
Hi there,

You will need to edit two files actually so here are the commands to do that.
Both files look the exact same and are clones of each other, but ubuntu treats them differently depending on your connection detail. (This isn't important to know, just some extra info)

Here are the commands:

"gksudo gedit /etc/ppp/chap-secrets" (enter password)

and

"gksudo gedit /etc/ppp/pap-secrets" (enter password again)

You will need to write something like this:

"your isp username@optusnetdsl" "*" "yourpassword" (you must keep the quotations)

You will also have to edit this config:

"gksudo gedit /etc/ppp/peers/speedtch"

Make sure it says something like this:

noipdefault
defaultroute
user 'your isp username@optusnetdsl'
noauth
updetach
usepeerdns
plugin rp-pppoe.so
nas0


You will also need to verify your VCI/VPI settings:

"gksudo gedit /etc/init.d/dial"

It will have this line in it:

br2684ctl -b -c 0 -a VP.VC

Change it to:

br2684ctl -b -c 0 -a 8.35

Hope that helps :)

BTW did you try the script?

Cheers.

---

### Post by MichaelSM on 2007-05-11
MCKRYPTYK I ran your script. Here's what happened:

michael@michael-desktop:~$ cd ~/speedtouch/config/dial
bash: cd: /home/michael/speedtouch/config/dial: No such file or directory
michael@michael-desktop:~$ "gksudo" install -m 744 dial /etc/init.d
install: cannot stat `dial': No such file or directory
michael@michael-desktop:~$ "gksudo" ln -s /etc/init.d/dial /etc/rc2.d/S95dial
ln: creating hard link `/etc/rc2.d/S95dial' to `/etc/init.d/dial': File exists
michael@michael-desktop:~$ "gksudo" ln -sf /etc/resolv.conf /etc/ppp/resolv.conf
gksudo: invalid option -- f
GKsu version 1.9.3

Usage: gksudo [-u <user>] [options] <command>

  --debug, -d
    Print information on the screen that might be
    useful for diagnosing and/or solving problems.

  --user <user>, -u <user>
    Call <command> as the specified user.

  --disable-grab, -g
    Disable the "locking" of the keyboard, mouse,
    and focus done by the program when asking for
    password.
  --prompt, -P
    Ask the user if they want to have their keyboard
    and mouse grabbed before doing so.
  --preserve-env, -k
    Preserve the current environments, does not set $HOME
    nor $PATH, for example.
  --login, -l
    Make this a login shell. Beware this may cause
    problems with the Xauthority magic. Run xhost
    to allow the target user to open windows on your
    display!

  --description <description|file>, -D <description|file>
    Provide a descriptive name for the command to
    be used in the default message, making it nicer.
    You can also provide the absolute path for a
    .desktop file. The Name key for will be used in
    this case.
  --message <message>, -m <message>
    Replace the standard message shown to ask for
    password for the argument passed to the option.
    Only use this if --description does not suffice.

  --print-pass, -p
    Ask gksu to print the password to stdout, just
    like ssh-askpass. Useful to use in scripts with
    programs that accept receiving the password on
    stdin.

michael@michael-desktop:~$ cd ~
michael@michael-desktop:~$ "gksudo" rm -R ~/speedtouch
gksudo: invalid option -- R
GKsu version 1.9.3

Usage: gksudo [-u <user>] [options] <command>

  --debug, -d
    Print information on the screen that might be
    useful for diagnosing and/or solving problems.

  --user <user>, -u <user>
    Call <command> as the specified user.

  --disable-grab, -g
    Disable the "locking" of the keyboard, mouse,
    and focus done by the program when asking for
    password.
  --prompt, -P
    Ask the user if they want to have their keyboard
    and mouse grabbed before doing so.
  --preserve-env, -k
    Preserve the current environments, does not set $HOME
    nor $PATH, for example.
  --login, -l
    Make this a login shell. Beware this may cause
    problems with the Xauthority magic. Run xhost
    to allow the target user to open windows on your
    display!

  --description <description|file>, -D <description|file>
    Provide a descriptive name for the command to
    be used in the default message, making it nicer.
    You can also provide the absolute path for a
    .desktop file. The Name key for will be used in
    this case.
  --message <message>, -m <message>
    Replace the standard message shown to ask for
    password for the argument passed to the option.
    Only use this if --description does not suffice.

  --print-pass, -p
    Ask gksu to print the password to stdout, just
    like ssh-askpass. Useful to use in scripts with
    programs that accept receiving the password on
    stdin.

michael@michael-desktop:~$ cd ~                              
michael@michael-desktop:~$ mkdir -p ~/speedtouch/firmware    
michael@michael-desktop:~$ cd ~/speedtouch/firmware          
michael@michael-desktop:~/speedtouch/firmware$ wget [http://download.ethomson.com/download/speedmgmt.tar.gz](http://download.ethomson.com/download/speedmgmt.tar.gz) 
--10:20:47--  [http://download.ethomson.com/download/speedmgmt.tar.gz](http://download.ethomson.com/download/speedmgmt.tar.gz)
           => `speedmgmt.tar.gz'
Resolving download.ethomson.com... 157.254.235.78
Connecting to download.ethomson.com|157.254.235.78|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 293,547 (287K) [application/octet-stream]

100%[====================================>] 293,547       51.84K/s    ETA 00:00

10:20:55 (48.44 KB/s) - `speedmgmt.tar.gz' saved [293547/293547]

michael@michael-desktop:~/speedtouch/firmware$ tar xvzf speedmgmt.tar.gz         
mgmt/mgmt.o
mgmt/speedtouch
mgmt/speedtch.usermap
mgmt/INSTALL
mgmt/iface.h
mgmt/Makefile
mgmt/LICENSE
mgmt/VERSION
mgmt/ChangeLog
michael@michael-desktop:~/speedtouch/firmware$ cd ~/speedtouch/firmware/mgmt     
michael@michael-desktop:~/speedtouch/firmware/mgmt$ wget [http://www.linux-usb.org/SpeedTouch/firmware/firmware-extractor](http://www.linux-usb.org/SpeedTouch/firmware/firmware-extractor) 
--10:20:56--  [http://www.linux-usb.org/SpeedTouch/firmware/firmware-extractor](http://www.linux-usb.org/SpeedTouch/firmware/firmware-extractor)
           => `firmware-extractor'
Resolving [www.linux-usb.org](www.linux-usb.org)... 66.35.250.210
Connecting to www.linux-usb.org|66.35.250.210|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 11,901 (12K) [text/plain]

100%[====================================>] 11,901        22.67K/s             

10:20:58 (22.59 KB/s) - `firmware-extractor' saved [11901/11901]

michael@michael-desktop:~/speedtouch/firmware/mgmt$ chmod +x firmware-extractor &&    
> ./firmware-extractor ~/speedtouch/firmware/mgmt/mgmt.o 
** Boot block from /home/michael/speedtouch/firmware/mgmt/mgmt.o:
   CRC: 0xd80bf9f7
   Length: 991
** Firmware block from /home/michael/speedtouch/firmware/mgmt/mgmt.o:
   CRC: 0x94a45435
   Length: 526187
michael@michael-desktop:~/speedtouch/firmware/mgmt$ cp speedtch*.bin ~/speedtouch/firmware/ 
michael@michael-desktop:~/speedtouch/firmware/mgmt$ cd ../                           
michael@michael-desktop:~/speedtouch/firmware$ "gksudo" rm -R mgmt              
gksudo: invalid option -- R
GKsu version 1.9.3

Usage: gksudo [-u <user>] [options] <command>

  --debug, -d
    Print information on the screen that might be
    useful for diagnosing and/or solving problems.

  --user <user>, -u <user>
    Call <command> as the specified user.

  --disable-grab, -g
    Disable the "locking" of the keyboard, mouse,
    and focus done by the program when asking for
    password.
  --prompt, -P
    Ask the user if they want to have their keyboard
    and mouse grabbed before doing so.
  --preserve-env, -k
    Preserve the current environments, does not set $HOME
    nor $PATH, for example.
  --login, -l
    Make this a login shell. Beware this may cause
    problems with the Xauthority magic. Run xhost
    to allow the target user to open windows on your
    display!

  --description <description|file>, -D <description|file>
    Provide a descriptive name for the command to
    be used in the default message, making it nicer.
    You can also provide the absolute path for a
    .desktop file. The Name key for will be used in
    this case.
  --message <message>, -m <message>
    Replace the standard message shown to ask for
    password for the argument passed to the option.
    Only use this if --description does not suffice.

  --print-pass, -p
    Ask gksu to print the password to stdout, just
    like ssh-askpass. Useful to use in scripts with
    programs that accept receiving the password on
    stdin.

michael@michael-desktop:~/speedtouch/firmware$ "gksudo" rm speedmgmt.tar.gz*    
michael@michael-desktop:~/speedtouch/firmware$ 
michael@michael-desktop:~/speedtouch/firmware$ cd ~/speedtouch/firmware                 
michael@michael-desktop:~/speedtouch/firmware$ "gksudo" cp speedtch* /lib/firmware      
michael@michael-desktop:~/speedtouch/firmware$ "gksudo" chmod 755 /lib/firmware/speedtch*   
michael@michael-desktop:~/speedtouch/firmware$ mkdir -p ~/speedtouch/br2684ctl          
michael@michael-desktop:~/speedtouch/firmware$ cd ~/speedtouch/br2684ctl                
michael@michael-desktop:~/speedtouch/br2684ctl$ wget [http://mirrors.kernel.org/ubuntu/pool/universe/b/br2684ctl/br2684ctl_20040226-1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/universe/b/br2684ctl/br2684ctl_20040226-1_i386.deb) 
--10:21:00--  [http://mirrors.kernel.org/ubuntu/pool/universe/b/br2684ctl/br2684ctl_20040226-1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/universe/b/br2684ctl/br2684ctl_20040226-1_i386.deb)
           => `br2684ctl_20040226-1_i386.deb'
Resolving mirrors.kernel.org... 204.152.191.39, 204.152.191.7
Connecting to mirrors.kernel.org|204.152.191.39|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 7,362 (7.2K) [text/plain]

100%[====================================>] 7,362         24.70K/s             

10:21:02 (24.64 KB/s) - `br2684ctl_20040226-1_i386.deb' saved [7362/7362]

michael@michael-desktop:~/speedtouch/br2684ctl$ 
michael@michael-desktop:~/speedtouch/br2684ctl$ mkdir -p ~/speedtouch/config/secrets     
michael@michael-desktop:~/speedtouch/br2684ctl$ cd ~/speedtouch/config/secrets           
michael@michael-desktop:~/speedtouch/config/secrets$ touch secrets                            
michael@michael-desktop:~/speedtouch/config/secrets$ "gedit" secrets                          
michael@michael-desktop:~/speedtouch/config/secrets$ cd ~/speedtouch/config/secrets
michael@michael-desktop:~/speedtouch/config/secrets$ "gksudo" cp secrets pap-secrets                
michael@michael-desktop:~/speedtouch/config/secrets$ "gksudo" cp secrets chap-secrets 
michael@michael-desktop:~/speedtouch/config/secrets$ "gksudo" install -m 600 secrets /etc/ppp/chap-secrets 
michael@michael-desktop:~/speedtouch/config/secrets$ "gksudo" install -m 600 secrets /etc/ppp/pap-secrets 
michael@michael-desktop:~/speedtouch/config/secrets$ 
michael@michael-desktop:~/speedtouch/config/secrets$ cd ~/speedtouch/br2684ctl
michael@michael-desktop:~/speedtouch/br2684ctl$ "gksudo" dpkg -i br2684ctl*.deb
dpkg: need an action option

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
michael@michael-desktop:~/speedtouch/br2684ctl$ "gksudo" chmod 755 /usr/sbin/br2684ctl
michael@michael-desktop:~/speedtouch/br2684ctl$ 
michael@michael-desktop:~/speedtouch/br2684ctl$ mkdir -p ~/speedtouch/config/speedtch
michael@michael-desktop:~/speedtouch/br2684ctl$ cd ~/speedtouch/config/speedtch
michael@michael-desktop:~/speedtouch/config/speedtch$ touch speedtch
michael@michael-desktop:~/speedtouch/config/speedtch$ "gedit" speedtch
michael@michael-desktop:~/speedtouch/config/speedtch$ cd ~/speedtouch/config/speedtch
michael@michael-desktop:~/speedtouch/config/speedtch$ "gksudo" install -m 600 speedtch /etc/ppp/peers
michael@michael-desktop:~/speedtouch/config/speedtch$ 
michael@michael-desktop:~/speedtouch/config/speedtch$ mkdir -p cd ~/speedtouch/config/dial
michael@michael-desktop:~/speedtouch/config/speedtch$ touch ~/speedtouch/config/dial/dial
michael@michael-desktop:~/speedtouch/config/speedtch$ "gedit" ~/speedtouch/config/dial/dial
michael@michael-desktop:~/speedtouch/config/speedtch$ 

That's where it stopped.

Previously I'd edited the pa/chap secrets files and input 'optusnetdsl' where needed. VCI.VPI was correct. The file /etc/ppp/peers/speedtch was a bit different from your version, but I input the usernam@isp afer 'user' and saved it.

I'll re-start and see what happens.

Regards,
Michael.

Didn't work. I have to go to work now. Be back in 12 hrs. Thanks again.

---

### Post by Farhan on 2007-05-11
hello there!
i had been using Edgy for a couple of months untill i decided to finally upgrade to Feisty (fresh install actually, in a new partition) today morning and after upgrading, i could not get my Speedtouch330 to work anymore and that is my only way to connect to the Internet! so i kept looking for solutions and trying different things out (including [http://www.linux-usb.org/SpeedTouch/ubuntu/index.html](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html) and mckrytyk's scripts for PPPoE) by painfully switching back and forth rebooting between Fiesty and Edgy but the kept getting the same error: > unrecognized option 'nas0'
whenever i tried dialing to connect by saying: > sudo pppd call speedtch


so i checked what messages the speedtouch modem was giving by typing:
> dmesg | grep "speed"

and found from the messages that there was something wrong with my firmware:
> [   17.088409] usbcore: registered new interface driver speedtch
[   17.159982] speedtch 2-1:1.0: found stage 1 firmware speedtch-1.bin
[   17.212311] speedtch 2-1:1.0: found stage 2 firmware speedtch-2.bin
[   19.212522] speedtch 2-1:1.0: speedtch_upload_firmware: read BLOCK2 from modem failed (-110)!
[   19.212530] speedtch 2-1:1.0: speedtch_heavy_init: firmware upload failed (-110)!

**then i tried the [french website mentioned earlier]("http://wiki.ubuntu-fr.org/materiel/modem_adsl_speedtouch_330_speedtouch_ng") in this thread and voila! it worked!**

all i did was:
> 1. get these packages and install them only by one in this order (due to dependency issues): 
[QUOTE]a. [http://packages.ubuntu.com/edgy/libs/libatm1](http://packages.ubuntu.com/edgy/libs/libatm1)
b. [http://packages.ubuntu.com/edgy/net/br2684ctl](http://packages.ubuntu.com/edgy/net/br2684ctl)
c. [http://www.moigeeknevro.com/speedtouch-ng/files/1.3.1/speedtouch-ng_1.3.1_all.deb](http://www.moigeeknevro.com/speedtouch-ng/files/1.3.1/speedtouch-ng_1.3.1_all.deb) (this one has a visual configuration wizard)

2. type in these commands as mentioned in the French website, even though the first two commands most probably were of no significance to me (or so i thought):
> sudo update-rc.d -f pppd-dns remove
sudo update-rc.d pppd-dns start 39 S .
sudo dpkg-reconfigure speedtouch-ng 

3. rebooted my machine
[/QUOTE]

hopefully this helps!

---

### Post by mckryptyk on 2007-05-12
Hi Mike,

I read your post about the errors in the script and have to ask, did you run the scripts in the correct order?  

I do know that the scripts are ugly and do throw errors but when I tested them they did put the correct files in the right places. 

Still they are far from a perfect solution, for instance when I had a speedtouch, I used the website that I kept linking to earier in my posts and it did work every time I tried. 

I was just attempting to automate that, guess I didn't do so well.

Mike, I need you to type the following commands for me and post the output of them here for me to see, so I will know what is not working correctly on your computer.

ls -la /lib/firmware/ >> ~/Desktop/diagnostic1.txt
ls -la /lib/firmware/* >> ~/Desktop/diagnostic2.txt

sudo cat /etc/ppp/peers >> ~/Desktop/diagnostic3.txt (if this one errors, just ignore it)
sudo cat /etc/ppp/peers/speedtch >> ~/Desktop/diagnostic4.txt

sudo cat /etc/init.d/dial >> ~/Desktop/diagnostic5.txt
ls -la /etc/ppp/ >> ~/Desktop/diagnostic6.txt
ls -la /etc/rc2.d/ >> ~/Desktop/diagnostic7.txt

These will appear on your desktop, please "tar.gz/zip" them up and post them here for me.

Also please download and install these programs (br2684ctl,libatm)

[http://mirror.optus.net/ubuntu/pool/universe/b/br2684ctl/br2684ctl_20040226-1_i386.deb](http://mirror.optus.net/ubuntu/pool/universe/b/br2684ctl/br2684ctl_20040226-1_i386.deb)
[http://mirror.optus.net/ubuntu/pool/main/l/linux-atm/libatm1_2.4.1-17_i386.deb](http://mirror.optus.net/ubuntu/pool/main/l/linux-atm/libatm1_2.4.1-17_i386.deb)

Also have you tried typing this to start your internet?:
"sudo pppd call speedtch" 
 
(BTW, I heard that the amount you download is charged heavily in AU, and someone told me that it won't count on your costs to use Optus' local ubuntu mirrors for your downloads, so I picked those.)

Cheers.

---

### Post by MichaelSM on 2007-05-12
Hi all. Home early, modem a go-er. That 'french connection' software was already on my comp. and had not worked BUT I read Farhan's post carefully and entered 'sudo pppd call speedtch' which all looked OK until a couple of lines appeared which read something like;

Timed out waiting for PADS  ......
Could not ......PPPoE Discovery.

PADS ???? Looked them up on Google......what colour red is embarrassment?

Now, you might ask; How is Michael connecting to the Internet without his speedtouch? Answer; unreliable LAN connection. As in router. As in a still-connected router which will block anything in its domain. Still-connected means LAN cable plugged in at both ends. No power on, no phone line connected. I threw the router into the next room, re-booted with the SpeedTouch, and all's perfect in the world.:roll: 

There's not much to learn from this other than BEWARE OF IDIOTS like this correspondent. Well, maybe ; that I finally grabbed a spare box which had never had SpeedTouch anything on it (Ub 6.10) and quickly did the 'french connection' on that one. It hasn't worked yet, but that's something I'll look at later. Trouble is, I don't know which particular install is running the SpeedTouch, since there's about four of them still on board this main HD. After all his efforts I hope mckryptyk's scripts did the trick. (Yes I did them all in order - I think- but I wouldn't trust me on anything more complicated than hard-boiling an egg if I were you.)

If there's something I can run which will show up what's working and what's excess baggage, please let me know. 

Maybe other people are dumb enough to leave things plugged in which shouldn't be; I doubt it ....!

As mckryptyk said, it's important to get all the relevant info together and build a definitive HOWTO re the SpeedTouch. It is a bloody fast and handy modem.

Cheers,
Michael

---

### Post by mckryptyk on 2007-05-12
Well I'm glad to hear that you have your modem working, the worst is over. :)

Now as for cleaning up the installation, if you run the "diagnostic.txt" commands in my last post, you will have all the info needed to determine just what is going on and what all the cruft is.

I don't mind looking at it if you want, but keep in mind: "If it isn't broke, don't fix it" :)

I suggest you make backups of your working configuration, especially if you are going to change it.

The best way to do that is to install "sbackup" and use the default settings.
"sudo apt-get install sbackup"
It will save your backup to a hidden folder in your home directory.

On a sidenote, 
The main reason I chose ubuntu over any other distribution of linux, is for the community support, which is second to none.

So as you learn more, be sure to give back, by helping those using ubuntu who need a little step in the right direction.

I'll check this tomorrow to see if you have any questions.
If not, good luck and take care :)

Cheers.

---

### Post by MichaelSM on 2007-05-12
Hello mckryptyk. Hope I got this attachment right. I'll have a look at the files to see if anything in there makes sense to me, which I doubt. 

If you can figure out what's happening, please let me know.

And I aint' fixin' anythin' which ain't broken... !

Regards,
Michael.

---

### Post by mckryptyk on 2007-05-13
These appear to be the files that not needed.

There are multiple speedtouch firmware that are not being loaded, as the computer is loading the first instance of the firmware, namely speedtch-1 and speedtch2. 

The others also are for a different revision of modem than revision 0.

All of the firmware are official alcatel/thomson firmware though.


Below is based on the assumption that you are using "Alcatel Speedtouch USB Rev. 0" modem.    

for diagnostic 1:

-rwxr-xr-x  1 root root    297 2007-05-10 11:50 speedtch~                (this is a leftover from gedit)
-rw-r--r--  1 root root    991 2006-09-23 22:05 speedtch-1.bin.0.00      (this is not getting loaded because speedtch-1 is loaded first)
-rw-r--r--  1 root root    991 2006-09-23 22:05 speedtch-1.bin.2.00      (this is not the right firmware version for your modem) 
-rw-r--r--  1 root root    935 2006-09-23 22:05 speedtch-1.bin.4.00      (not right version)

-rw-r--r--  1 root root 526187 2006-09-23 22:05 speedtch-2.bin.0.00      (this is not getting loaded because speedtch-2 is loaded first)
-rw-r--r--  1 root root 762650 2006-09-23 22:05 speedtch-2.bin.2.00      (this is not the right firmware version for your modem) 
-rw-r--r--  1 root root 775545 2006-09-23 22:05 speedtch-2.bin.4.00      (not right version)

for diagnostic 6:

-rw-------   1 root michael   104 2007-04-23 02:22 chap-secrets.old     (this has been replaced by the new chap-secrets)
-rw-r--r--   1 root root    13208 2006-07-11 05:13 options~             (this is a leftover from gedit)
-rw-------   1 root root     1652 2007-04-20 10:11 pap-secrets.bak      (this is your backup that is not being used)
-rw-------   1 root michael  1653 2007-04-23 02:22 pap-secrets.old      (this has been replaced by the new pap-secrets)

Also I should note that there are permission problems with two of the files.
They say "root:michael" but they should say "root:root".

Since they are to be deleted it doesn't really matter, just mentioned it to be thorough.

That should be it, just make sure to backup those files just in case there is a problem.

Cheers.

---

### Post by MichaelSM on 2007-05-13
Mckryptyk, I think you're trying to tell me that the ST scenario on my computer is like a dog's breakfast. ....!:KS  Re the unnecessary enties; Should I just work my way through them and delete them, or leave it all like it is in case I hit a wrong key and delete something vital?

How you figure out what you do amazes me. I'm just a dumb welding engineer. The hardest thing I ever do is use AUTOCAD badly.

Is there more you need to know re. writing the  HOWTO? 

Cheers again,
Michael.

---

### Post by mckryptyk on 2007-05-13
Hi Mike,

It doesn't really matter if you want to delete them, you don't need to.
For some people, It's all about how "clean" the system is.
It's completely up to you.
Just back them up first if you do.

(You probably know this already)
You can use the copy command:
"cp /path/to/file/name-of-file /path/to/new/file/name-of-file 
For example: 
"cp /home/a-file.txt /home/Desktop/my-copied-file.txt"

(Be careful with this one :) )
To delete, use the "remove" command:
Just replace "cp" with "rm" like so:
"rm /path/to/file/name-of-file.txt"
For example:
"rm /home/Desktop/my-copied-file.txt"

You will have to add sudo on to it for files owned by root.

Hey what are the odds!

I use to do some automotive repair long ago, nothing like using a  MIG or TIG welder,  except of course oxy/acetylene!

And the cool photos your friends take of you when you have the flame turned all the way up .. Priceless! :)

Cheers.

---

### Post by MichaelSM on 2007-05-14
Hello again, mckryptyk. A lot has happened in the last day or two. First thing: the 4-week-old new HD I was setting up with everything I needed crapped itself totally, so I installed Edgy on a spare one. 
It was the plugged-in router scenario after all which caused the problems I had. On this new/old HD I followed the 'french connection' instructions and re-booted. Perfect. That method has a graphic interface which one uses to input all the info required. The mouse won't work; one has to use  tab and enter to get through it. Interestingly enough, when I used a HD with Xandros 3.02 OC yesterday, and tried to do the same install, there was a pile of unmet dependencies, so I couldn't be bothered any further. Xandros was frightening to revisit esp. with KDE. What a clutter. 
'What's the odds ...?' you wrote. Maybe it's practical people who ditch MS and head for the hills. On one hand, if I counted the hundreds of hours I've spent learning how to do things with Linux, and multiplied them by some arbitrary hourly rate of pay, I'd have a fantastic new Mac with all the bells and whistles. On the other, this is all BRAIN FOOD; what took me so long to set up originally now takes an hour or so with things like Java (for Frostwire) and the SpeedTouch business. 
I can't say enough about your fantastic assistance throughout a saga which should never have got past the first page in the thread. Every bit of it was a learning curve about files, gedits, etc. which makes things much easier in the future. 
Thanks again, mckryptyk. Next time I light up an oxy/acet torch I'll be reminded of you ..
Cheers, my friend.
Michael.
OH, PS. I have a small issue with another box for my Mum. I'll bother you with that at a later stage if that's OK. Probably shouldn't be using Forums as a chat site! Mike.

---

### Post by Farhan on 2007-05-21
sorry for bumping a dead thread without any substantial reason but just found this on Gutsy forum:
> [https://launchpad.net/usb-adsl-modem-manager](https://launchpad.net/usb-adsl-modem-manager)
an USB ADSL Modem manager written in Python that supports Speedtouch 330 modems revisions 0 - 4

PPPoE is not supported yet but it is on the TO DO list. hopefully it will put an end to all troubles for USB modem users!

---

### Post by spaarks on 2007-05-30
How is it that PCLOS 2007 detects and sets up the Speedtouch 330 without the user having to run scripts and changing the Speedtouch firmware?

---

### Post by StevenHarper on 2007-06-04
> **Farhan said:**
> sorry for bumping a dead thread without any substantial reason but just found this on Gutsy forum:


PPPoE is not supported yet but it is on the TO DO list. hopefully it will put an end to all troubles for USB modem users!

I have fixed PPPoE in 0.4.9

You can get it here

[http://www.squeezedonkey.com/svn/linux/trunk/releases/](http://www.squeezedonkey.com/svn/linux/trunk/releases/)

Both the 64bit and 32bit ones are Tested (off a LIVE CD with no internet connection) and work

Please post to me on This Thread [http://ubuntuforums.org/showthread.php?p=2664939](http://ubuntuforums.org/showthread.php?p=2664939)

If you need any support

Steve

---

### Post by MichaelSM on 2007-06-06
Hello mckryptyk.
It looks as if the speedtouch picture has reached nearly it's end. And a positive one too.
Thank you for helping an idiot.
Mike.

---

