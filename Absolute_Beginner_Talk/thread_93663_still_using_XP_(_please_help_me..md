---
title: "still using XP :( please help me."
date: 2005-11-22
forum: Absolute Beginner Talk
---

### Post by Danielle on 2005-11-22
hi, can someone help me with these instructions? please. i want to use Ubuntu but i can't until i can configure my modem. here are the instructions.

this one says it's a script:
[http://steve-parker.org/speedtouchconf/](http://steve-parker.org/speedtouchconf/)

these are the same files with different instructions:
[http://cvs.sourceforge.net/viewcvs.py/*checkout*/speedtouch/speedtouch/INSTALL?rev=HEAD](http://cvs.sourceforge.net/viewcvs.py/*checkout*/speedtouch/speedtouch/INSTALL?rev=HEAD)

here are some more instructions:
[http://cvs.sourceforge.net/viewcvs.py/*checkout*/speedtouch/speedtouch/doc-linux/howto/SpeedTouch-HOWTO-en.html?rev=HEAD](http://cvs.sourceforge.net/viewcvs.py/*checkout*/speedtouch/speedtouch/doc-linux/howto/SpeedTouch-HOWTO-en.html?rev=HEAD)

can someone help me? i'm stuck and i want to use Ubuntu. i can never use Linux if i don't understand those instructions :(

---

### Post by topic58 on 2005-11-22
Go to System - administration - network. If you have a modem: type in your info there. Will take you quite some time downloading updates in Ubuntu though... :confused:

---

### Post by nikopol on 2005-11-22
Could you clarify a few things for me:
- What speedtouch are you using? USB or another one?
- Which version of Ubuntu are you running? Is it Breezy?

---

### Post by Danielle on 2005-11-22
thanks. for the replies :)

i'm using the USB ADSL PPP Thomson Speedtouch 330 it's the silver one.
i downloaded and installed the install version of Ubuntu afew days ago. i think it's the latest version. thanks

---

### Post by Brunellus on 2005-11-22
*sigh*

save yourself the headache and spend about USD 30 and get an adsl modem that speaks real ethernet instead of a USB one.  USB DSL modems are, as you've just discovered, not very well supported in linux generally, while ethernet is the preferred choice.

---

### Post by Danielle on 2005-11-22
[QUOTE=Brunellus]*sigh*

save yourself the headache and spend about USD 30 and get an adsl modem that speaks real ethernet instead of a USB one.  USB DSL modems are, as you've just discovered, not very well supported in linux generally, while ethernet is the preferred choice.[/QUOTE]
can you get "real ethernet" modems in silver? it's my favourite colour [size=1]**J/K[/size]**
other people have got it to work. i like my modem. ;)

---

### Post by Brunellus on 2005-11-22
you have to balance the fact that "other people have gotten it to work" against the irritation of not getting it to work right.

Also, you have to keep in mind that the driver is new and under heavy development.  

It all depends how much trouble you're willing to go through.  I pulled my hair out getting a wlan card up and running in linux (finally resorting to compiling ndiswrapper myself--fun!) but when the time came for my next purchase, I bought one which was known to be supported.  Could I have used another (slightly cheaper) card and struggled with it?  Yes.  But I was happier and less stressed--and had paid my hard-earned wages to a company that bothered to have real linux drivers.

---

### Post by flatliner2005 on 2005-11-22
Danielle,
I have set up the Speedtouch 330 USB in both Mepis and Debian. Trust me when I tell you that you are going to have a REAL headache with this!!!.

The speedtouchconf script does work, however I suffered problems with 2.6.x kernels.

Over on the Mepis forums I posted this [http://www.mepis.org/node/4836#comment-16065](http://www.mepis.org/node/4836#comment-16065) which briefly detailed how I got the Speedtouch working in Mepis.

Have you tried the method at [https://wiki.ubuntu.com/UKSpeedtouchDSLHowTo](https://wiki.ubuntu.com/UKSpeedtouchDSLHowTo) ?  Most of the stuff there that I have tried has worked every time.

Hope this helps
Flatliner

---

### Post by Danielle on 2005-11-22
hi, i could get a faster connection which would be good, i'll try a couple more tutorials though. i hadn't see the Wiki one so i'll see if i can understand it. it took me a few minutes to work out how to reboot :D thanks for the help :)

---

### Post by Brunellus on 2005-11-22
explain.  "faster connection" through USB?

---

### Post by Danielle on 2005-11-22
[QUOTE=Brunellus]explain.  "faster connection" through USB?[/QUOTE]
hi, i'm talking about a new ISP. i want to get something like 10 Mbps, i might as well if i'm thinking about a new modem.

---

### Post by Brunellus on 2005-11-22
that's not a bad thing.  

Be sure to call up your former ISP and tell them the reason you're taking your business elsewhere is because they provided poor support for Linux.

---

### Post by towsonu2003 on 2005-11-22
from what I understand from the above posts, making these usb adsl modems work is as hard (more? less?) as making a winmodem (a modem with nothing in it :) ) work...

In that case, they should have a forum somewhere, like linmodem.org has one (mailing list) for winmodems... you should try to locate that forum / mailing list, and ask your question there.. they will be much more experienced than most ubuntu users with those modems... linmodem.org people REALLY helped me a lot with the winmodem. They actually helped me for about 6 months (until it got solved, as I am here, thanks to them + ubuntu's niceness to this particular modem in this particular machine), across about 5-6 different distros...

Also, if you are stubborn enough (like me with my "dear" (sic) winmodem) with your usb modem, you may wanna try many different distros... This is from experience because this modem I'm using in this particular machine works ONLY in ubuntu (my threat on that: [http://wwwhttp://www.ubuntuforums.org/showthread.php?t=73049.ubuntuforums.org/showthread.php?t=73049](http://wwwhttp://www.ubuntuforums.org/showthread.php?t=73049.ubuntuforums.org/showthread.php?t=73049) , not related to your threat)

good luck...

---

### Post by gord on 2005-11-22
i have a speedtouch modem (same silver one i think), and it works fine every time i use it, allthough i have to run speedtouch conf every time.

make sure you have the speedtouchconf package (latest stable should do) from [http://speedtouchconf.sourceforge.net/]("http://speedtouchconf.sourceforge.net/") also grab the silver modem firmware from [http://steve-parker.org/speedtouchconf/rev4fw.zip]("http://steve-parker.org/speedtouchconf/rev4fw.zip") and untar the first package and put the rev4fw.zip into the direcectory that was created. then;

```
sudo apt-get install build-essential
```

you only have to do that once, then cd into the speedtouchconf directory and type

```
sudo ./speedtouchconf.sh
```

:)

---

### Post by Danielle on 2005-11-22
hi, i'm so happy to have some help :) towsonu2003 i'll have alook and see what i can find thanks for the idea. Brunellus, i'll let my ISP know what i think :D

gord, i hope you see this while you're here. i just had a quick try with your instructions, i had to come back to windows for the driver (alcaudsl.sys). i unpacked the archive and it's now sitting on my desktop, where have you put your speedtouch directory? can you try and put it in simple terms? i'm still a newbie :( how do i cd to a directory? is it cd or cd..

so i've upacked the archive and i'm going to put the other archive into it - rev4fw.zip 

then, i'll open a terminal and type:
sudo apt-get install build-essential

can you show me if i've done something wrong, i'll be so happy if i get it to work :) thanks. sorry if the post is abit rushed, i want you to see it before you leave.

[color=red]EDIT[/color] sorry forget about the cd question, it doesn't make sense to me, so i don't know what you might be thinking. i know how to cd to a directory, i was panicing abit :(

---

### Post by gord on 2005-11-22
hmm.. well ok, lets try this set by step;

download [this file](http://kent.dl.sourceforge.net/sourceforge/speedtouchconf/speedtouchconf_2.0_16_Oct_2005.tar.gz) and [this file](http://steve-parker.org/speedtouchconf/rev4fw.zip).

get them both from onto your ubuntu partition extract the files from speedtouchconf_2.0_16_Oct_2005.tar.gz into your home directory, then copy the full rev4fw.zip into /home/<username>/speedtouchconf-2.0_16_Oct-2005/. do not extract anything from the rev4fw.zip, put the whole thing into the directory created when you untared the first file. note, you do not need the 'Alcatel Microcode',  thats for non silver modems, ours are special and need rev4fw.zip instead ;)

open up a terminal and type 
```
 sudo apt-get install build-essential 
```

```
 
cd /home/<username>/speedtouchconf-2.0_16_Oct-2005/
sudo ./speedtouchconf.sh

```

it will then run a script that will install the drivers for you and set up your connection. you'll need to know some information about your connection (username, password vcp/vci numbers [mine is 0 38 as im in the uk]). 

and thats pritty much it. it will offer to setup your connection every time you boot into linux for you, you should type 'yes' but don't be supprised if it breaks there, it does for me. every time i want to connect to the internet i have to type sudo ./speedtouchconf.sh


sorry if your still confused but i have to sleep, gots to give blood tommrow so i gots to get my sleep :) if your still having problems, my e-mail is [email]gordallott@gmail.com[/email] and i'll help you out all i can :)

---

### Post by Danielle on 2005-11-23
OMG, it worked :p :D :cool:  i can't believe it's working. thank you so much for the help. i'm so happy. i'm abit worried now about a firewall, is there one running now? do i need to do anything to secure myself? and do i need to get the macromedia stuff?
i'm so happy. :D  thanks again

---

### Post by gord on 2005-11-23
:)
you don't need a firewall, linux doesn't have a virus problem like windows does, allthough you can set one up if you want

---

### Post by Brunellus on 2005-11-23
[QUOTE=gord]:)
you don't need a firewall, linux doesn't have a virus problem like windows does, allthough you can set one up if you want[/QUOTE]
Not true.

the firewall is not supposed to stop viruses, but rather to limit the number of open connections to the outside world.  

If I'm a malicious cracker (or even a merely curious hacker), I'm going to find your box and portscan it.  That'd be like driving by a house and seeing how many doors & windows are open, and where they are.  If I see a lot of open doors and windows, I'm going to try and look inside them...and then walk in.

The firewall blocks, allows, or forwards TCP/IP connections on ports that you specify.  If you don't need a port, you can close it, and thus close off yet another possible entryway.  

Luckily, I believe that ubuntu doesn't have too many ports open by default.  If you want a GUI-configurable firewall, you could try installing firestarter

```
$ sudo apt-get install firestarter 
```

which is a graphical frontend to linux's iptables utility (a very powerful tool that I'm only just learning about).

As far as multimedia, flash, java and other proprietary support, you might want to check out the wikipage on RestrictedFormats:

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

That worms use these ports to propagate themselves is also incidental, but the firewall is not about worms or viruses as much as it is about limiting access to your computer in a general sense.

---

### Post by gord on 2005-11-23
lets not make this complicated :) you can live without a firewall but if you like your security, its a good idea to have one :)

---

### Post by Brunellus on 2005-11-23
[QUOTE=gord]lets not make this complicated :) you can live without a firewall but if you like your security, its a good idea to have one :)[/QUOTE]
It's not about making it complicated.  It's about remembering why you have these thigns in the first place.

Everybody went all firewall mad because windows--by design!--runs with all ports open unless explicitly closed.  Linux is a bit more sensible.

My firewall is built into my router, so I'm not too worried about it.  BTW, Daniell, that's another reason to go for ethernet over USB adsl modems--you can hook them up to routers and share connections among several computers, while also shifting the firewall to the boundary of your network.  very cool.

---

### Post by Danielle on 2005-11-23
thanks for the help. i love security :D i'm going to use the FW that runs on top of the iptables. i have to be quick i have a train to catch @2:54 :(

i just wanted to say that someone picked up a phone when i was connected and i lost my connection. i rebooted and it wont work again, i get this error:

The modem_run command failed (code 235)
modem_run results:
Mutex value not OK
FAILED because of modem_run error 235

any ideas ??? thanks, i'll be back in an hour or so :) thanks.

---

### Post by gord on 2005-11-23
its really dodgy, i get stuff like that all the time. the only solution i have found is to simply reboot and run speedtouchconf.sh again... its an awful modem ;)

---

### Post by Danielle on 2005-11-23
hi, well maybe i will have to get a new modem :( i have tried over and over again and i always get that same error. is that normal with this modem? it's the exact same error about 10 times in a row. i tried turning off the PC, unplugging the USB, replugging, rebooting then running that script. i tried booting up then unplugging and replugging in the USB and still i had the same error. i even tried putting in a script in the speedtouch directory which makes the modem reconnect if ever it disconnects which i found from a different tutorial, but it won't work.

if i keep on rebooting will it work ever? i looked through all the files the script uses and there's no obvious mistakes :( i'm going to look up the error now. thanks :)

---

### Post by Danielle on 2005-11-23
hi, i'm not sure i should post this here because i have another thread about security, but i wanted to ask Brunellus "do you know anything about Kraal-GTK?" it sounds quite good, what do you think? 
[https://wiki.ubuntu.com/Kraal-GTK](https://wiki.ubuntu.com/Kraal-GTK)
[https://wiki.ubuntu.com/SoC-Firewall](https://wiki.ubuntu.com/SoC-Firewall)

it's not the same as firestarter, is it? thanks

---

### Post by Brunellus on 2005-11-23
don't know a thing about kraal, so I couldn't tell you about it.  If you don't have any daemons listening for outside connections, I wouldn't worry too much.  You're not running any globally-accessible servers on your computer are you?

---

### Post by Danielle on 2005-11-23
[QUOTE=Brunellus]don't know a thing about kraal, so I couldn't tell you about it.  If you don't have any daemons listening for outside connections, I wouldn't worry too much.  You're not running any globally-accessible servers on your computer are you?[/QUOTE]
no i'm not. but if someone can see me they can ping me, isn't that a problem?
i want to control icmp's

---

### Post by blastus on 2005-11-23
[quote=Danielle]i just wanted to say that someone picked up a phone when i was connected and i lost my connection. i rebooted and it wont work again, i get this error:[/quote]

Well that's just stupid. I thought the whole idea of ADSL was not only faster Internet access, but that you could talk on the phone at the same time. I have a dialup modem and even I can pick up the phone and hang it up and it doesn't affect my connection. Really primitive dialup modems had problems with someone picking up the line but not now. I can't imagine why an ADSL modem would have a problem with this unless it is a really crappy modem and/or the drivers for Linux are not functional enough to be useful.

---

### Post by Danielle on 2005-11-23
[QUOTE=blastus]Well that's just stupid. I thought the whole idea of ADSL was not only faster Internet access, but that you could talk on the phone at the same time. I have a dialup modem and even I can pick up the phone and hang it up and it doesn't affect my connection. Really primitive dialup modems had problems with someone picking up the line but not now. I can't imagine why an ADSL modem would have a problem with this unless it is a really crappy modem and/or the drivers for Linux are not functional enough to be useful.[/QUOTE]
hi, it's just one phone in the house that doesn't have the adapter that plugs into the phone socket. all the other phones have a special adpter that has two sockets which allow for the phone and computer to be connected at the same time. sorry i don't know the name of it.

---

### Post by Danielle on 2005-11-23
ADSL filter
[img]http://www.home-phones.co.uk/images_products/337.jpg[/img]

---

### Post by blastus on 2005-11-23
I see. It sounds like you just need to get another adapter and that would solve the problem since phones cannot be connected directly to the hard line.

---

### Post by Danielle on 2005-11-23
it was never much of a problem with XP, but i haven't been able to connect to the internet with Ubuntu since it happened, and as it's so difficult for me to reconnect i may get one of those filters tomorrow :D

---

### Post by CosaGaucha on 2005-11-23
> **gord]hmm.. well ok, lets try this set by step said:**
> this file[/url] and [this file](http://steve-parker.org/speedtouchconf/rev4fw.zip).

get them both from onto your ubuntu partition extract the files from speedtouchconf_2.0_16_Oct_2005.tar.gz into your home directory, then copy the full rev4fw.zip into /home/<username>/speedtouchconf-2.0_16_Oct-2005/. do not extract anything from the rev4fw.zip, put the whole thing into the directory created when you untared the first file. note, you do not need the 'Alcatel Microcode',  thats for non silver modems, ours are special and need rev4fw.zip instead ;)

open up a terminal and type 
```
 sudo apt-get install build-essential 
```

```
 
cd /home/<username>/speedtouchconf-2.0_16_Oct-2005/
sudo ./speedtouchconf.sh

```

it will then run a script that will install the drivers for you and set up your connection. you'll need to know some information about your connection (username, password vcp/vci numbers [mine is 0 38 as im in the uk]). 

and thats pritty much it. it will offer to setup your connection every time you boot into linux for you, you should type 'yes' but don't be supprised if it breaks there, it does for me. every time i want to connect to the internet i have to type sudo ./speedtouchconf.sh


sorry if your still confused but i have to sleep, gots to give blood tommrow so i gots to get my sleep :) if your still having problems, my e-mail is [email]gordallott@gmail.com[/email] and i'll help you out all i can :)


hello people, i´m from Argentina(do you know where is it? :) ) and i´m a complete newbie with linux. I installed kubuntu 5.10, and now i´m figthing with the speedtouch330 configuration. I did all the steps that all of you said. But when i run the ./speedtouch script, it gave me the error "240 - Modem not found" from modem_run....
i tried to install it a lot of times, but allways with the same result.. Once i copied the speedmgmt.... (zip) into the speedtouch........2005 folder, once i tried to do the same, descompressing this file inside this folder, and it gave to me the error "235...."

can someone help me with this borried step to connect to internet?
thx a lot!! (and sorry me about my bad english!..)

---

### Post by Danielle on 2005-11-23
hi, what colour is your modem? is it silver?

if you have the silver modem try this.
1, go to your Speedtouch folder and make sure you have rev4fw.zip and not alcaudsl.sys, mgmt.o files in it

then in the terminal type:
cd /home/**username**/speedtouchconf-2.0_16_Oct-2005/

sudo ./undo.sh

NOTE if your version of speedtouch has a different date make sure you type it correctly.

type YES to clear the script's info. then reboot and run: sudo ./speedtouchconf.sh
from the speedtouch folder.

it worked for me when i had that error.

do you know your vcp/vci  numbers? you need to enter them when you run the script.

---

### Post by CosaGaucha on 2005-11-23
[QUOTE=Danielle]hi, what colour is your modem? is it silver?
[/quote]
           Hi Danielle, thanks for your reply! my modem is silver.

> if you have the silver modem try this.
1, go to your Speedtouch folder and make sure you have rev4fw.zip and not alcaudsl.sys, mgmt.o files in it

           yes, i have the rev4fw.zip file, not other

> then in the terminal type:
cd /home/**username**/speedtouchconf-2.0_16_Oct-2005/

sudo ./undo.sh

           i did it twice...

> NOTE if your version of speedtouch has a different date make sure you type it correctly.

            ;) 

i´m pasting the message that i have when i run the script:

[....]
No further user interaction is required.
Configuring SpeedTouch Driver...
Software Configuration - SUCCESS
Building SpeedTouch Driver...
Software Build - SUCCESS
Installing SpeedTouch Driver...
Software Installation - SUCCESS
Creating ppp files in /etc/ppp
You can ignore any insmod hints here...

  *** Configuration finished. Starting the connection ***

dom nov 20 15:32:05 ART 2005
The modem lights should start flashing for approx. 60 seconds...
You might see some messages about USBDEVFS_BULK failed - you can ignore this.
dom nov 20 15:32:05 ART 2005
The modem_run command failed (code 240)
modem_run results:
Unable to locate firmware
If you have a silver modem, make sure you're using rev4fw.zip
[http://speedtouchconf.sourceforge.net/rev4fw.zip](http://speedtouchconf.sourceforge.net/rev4fw.zip)
FAILED because of modem_run error 240

---

### Post by Danielle on 2005-11-23
hi, this is where i found the answer to my error and it mentions the 240 error too - about the rev4fw.zip

#7 on this page
[http://steve-parker.org/speedtouchconf/faq.shtml](http://steve-parker.org/speedtouchconf/faq.shtml)

what's the path to your speedtouch folder?

---

### Post by Danielle on 2005-11-23
if i click Places>Home Folder my speedtouch folder is there next to the desktop folder. inside the speedtouch folder is the rev4fw.zip. it shouldn't be decompressed but left as a .zip

---

### Post by CosaGaucha on 2005-11-23
[QUOTE=Danielle]hi, this is where i found the answer to my error and it mentions the 240 error too - about the rev4fw.zip

#7 on this page
[http://steve-parker.org/speedtouchconf/faq.shtml](http://steve-parker.org/speedtouchconf/faq.shtml)

what's the path to your speedtouch folder?[/QUOTE]

home/juan/speedtouch-..........-2005

---

### Post by CosaGaucha on 2005-11-23
[QUOTE=Danielle]if i click Places>Home Folder my speedtouch folder is there next to the desktop folder. inside the speedtouch folder is the rev4fw.zip. it shouldn't be decompressed but left as a .zip[/QUOTE]

yes, i have the re4fw.zip inside the speedtouch folder, and not descompressed

other question.. in order to "hard-clean" all this and start again from zero, what happened if i delete the folder and start all one more time from my user folder?

---

### Post by Danielle on 2005-11-23
[QUOTE=CosaGaucha]yes, i have the re4fw.zip inside the speedtouch folder, and not descompressed

other question.. in order to "hard-clean" all this and start again from zero, what happened if i delete the folder and start all one more time from my user folder?[/QUOTE]
deleting should be OK but it won't take you back form where you started. the script changes other files e.g. if you run this you should see your username and password.
sudo gedit /etc/ppp/pap-secrets

but, it's what i'd do. run:
undo.sh
then turn off you computer for 2/3 minutes, unplug the replug your USB and redownload everything. that's all i can say, i'm a newbie too :(

---

### Post by Danielle on 2005-11-23
i did a similar search to this in google which helped:

[modem_run command failed (code 240)](http://www.google.co.uk/search?q=modem_run+command+failed+(code+240))

---

### Post by CosaGaucha on 2005-11-24
Hi!, i run it one more time, and i got the error 235 again... :(

i want to start from 0 again, how can i do this?... sorry for my "un-knowledgement"...

---

### Post by Danielle on 2005-11-24
[QUOTE=CosaGaucha]Hi!, i run it one more time, and i got the error 235 again... :(

i want to start from 0 again, how can i do this?... sorry for my "un-knowledgement"...[/QUOTE]
hi, i think by running:
undo.sh
it's in the speedtouch folder. when i said it wouldn't do a clean uninstall i think i was wrong. i was thinking of me - i had used other guides and made alot of manual changes that the script doesn't do. it seems for some reason when you run the script it can't see rev4fw.zip did you redownload it?

---

### Post by CosaGaucha on 2005-11-25
yeaaaaaaaaaahhhhhh!!!!!! i´m writing it from my kubuntu rigth now!!!the problem was fixed when i change the microcode for the alcausb.sys file from windows folder!!!

Danielle, THAKS A LOT for your support! :D :D :D :D :D :D

---

### Post by Danielle on 2005-11-25
that's great! i know how it feels to finally get internet access :)

---

