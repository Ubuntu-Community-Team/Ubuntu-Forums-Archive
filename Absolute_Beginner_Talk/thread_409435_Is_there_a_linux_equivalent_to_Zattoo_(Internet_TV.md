---
title: "Is there a linux equivalent to Zattoo (Internet TV)?"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by kilou on 2007-04-14
Hi,

I'm trying to definitely switch from Windows to Linux (Ubuntu) but I'd need to find something equivalent to Zattoo that would run on Linux. I'd avoid using Wine or virtualization to do so, I'd prefer something that can run on Linux natively. What I'm looking for is a software to watch commercial TV channels (not podcats etc but real TV, european channels). A sort of linux version of Zattoo. Does anybody know if that exists?

Thanks

---

### Post by igknighted on 2007-04-14
> **kilou said:**
> Hi,

I'm trying to definitely switch from Windows to Linux (Ubuntu) but I'd need to find something equivalent to Zattoo that would run on Linux. I'd avoid using Wine or virtualization to do so, I'd prefer something that can run on Linux natively. What I'm looking for is a software to watch commercial TV channels (not podcats etc but real TV, european channels). A sort of linux version of Zattoo. Does anybody know if that exists?

Thanks

You might want to take a look at Democracy TV, I think that might do what you want.

---

### Post by kilou on 2007-04-14
I already tried Democracy Player but it cannot stream real TV channels. It seems it only allows to stream "free" TV channels. I'm looking for something that can stream famous TV channels like BBC, M6, Canal+, TF1, TSR etc such as Zattoo can. Is that possible natively on Linux?

---

### Post by kc5hwb on 2007-04-14
I am told there is a program called MYTH that acts as a PVR program for Linux.  I have not used this myself, but other people I know say that it works well.

---

### Post by kilou on 2007-04-14
Sound interesting but it seems it needs a TV card to work. Zattoo "read" the TV channel from the web so you don't need any hardware to run it, you can watch TV on internet. This is what I'm looking for but for Linux. I know I am a bit difficult :)

---

### Post by igknighted on 2007-04-14
According to google there is a zattoo client for linux, did you try their website to see if you could find a linux version?

Edit, grr, not YET there isn't one, but I think it is in the works from them or a 3rd party... sry

---

### Post by hyper_ch on 2007-04-14
They don't have a linux client... at least not now - I have suggested this to them already - and Zattoo does not run in wine either...
The only way I got it running is vmware and vbox...

---

### Post by justinjstark on 2007-04-18
You could use penguintv with rss feeds from tvrss.net.  :)

---

### Post by erikb5 on 2007-05-21
Yes, Zattoo has released it's client for Linux :KS 

It's available in i386 format For Ubuntu 6.10, OpenSuse 10.2, Fedora Core 6, but it's installable on Ubuntu 7.04 and other distros both in i386 and x86-64. You will find the client on the Zattoo site.

[Download Zattoo for Linux]("http://zattoo.com/downloadlinux")

[Zattoo for Linux (x86-64) install steps.]("http://bussink.ch/erik/technology/gnulinux/zattoo-for-linux-x86-64/")

---

### Post by hyper_ch on 2007-05-22
yes, a few days ago they published the linux client. The 6.10 version runs perfectly on 7.04 :)

One program less that requires me to load windows in vmware

---

### Post by newbie2 on 2007-05-23
> **kilou said:**
> Hi,

I'm trying to definitely switch from Windows to Linux (Ubuntu) but I'd need to find something equivalent to Zattoo that would run on Linux. I'd avoid using Wine or virtualization to do so, I'd prefer something that can run on Linux natively. What I'm looking for is a software to watch commercial TV channels (not podcats etc but real TV, european channels). A sort of linux version of Zattoo. Does anybody know if that exists?

Thanks

> The wait is over, Linux users out there. We just released the first Zattoo client for the operating system of your choice (and that of Michael Dell). The main supported distro is Ubuntu 6.10, but the package can also be made to work with Fedora Core 6 and OpenSuse 10.2 with a little extra effort.

Can’t wait to get TV on your Linux computer? Visit our homepage and download it now (if you’re in Switzerland or Denmark) or sign up to be notified when we launch in your country.

Feedback, as always, is most welcome. 
[http://zattooblog.wordpress.com/2007/05/08/penguins-rejoice-linux-gets-tv/](http://zattooblog.wordpress.com/2007/05/08/penguins-rejoice-linux-gets-tv/)
[http://zattoo.com/](http://zattoo.com/)
;)

---

### Post by Swab on 2007-05-23
Not available in the UK... which countries will they stream to?

---

### Post by hyper_ch on 2007-05-23
I think currently it's Switzerland only...

---

### Post by Swab on 2007-06-08
Woo hoo,  just received an email asking me to be one of the first UK users.  Signed up and installed and am now watching BBC online!

---

### Post by hyper_ch on 2007-06-08
You get also all those german speaking channels?

---

### Post by Swab on 2007-06-08
I get 7 BBC Channels, France 24 English, TVE Internacinal and TV Polonia.

---

### Post by hyper_ch on 2007-06-09
hmmm, you get different channels... interesting...

---

### Post by hyper_ch on 2007-06-24
I have problems with the new zattoo version... starting up is fine... selecting a channel also... buffering works also... then i see for a fraction of a second an image and then I get a segfault:


[email]hyper@xubi:~/.Zatt[/email]oo/Data/logs$ zattoo_player
11:20:36 AM 06/24/2007 [MSG]    Current locale is en_US.UTF-8
11:20:36 AM 06/24/2007 [MSG]    Welcome to Zattoo (2.2.10.6523)
11:20:36 AM 06/24/2007 [MSG]    Checking for update...
11:20:36 AM 06/24/2007 [MSG]    There are no updates available.
11:20:36 AM 06/24/2007 [MSG]    Further log messages will be written to /home/hyper/.Zattoo/Data/logs/zattoo.debuglog
Segmentation fault (core dumped)

Anyone else experiencing this?

---

### Post by the8thstar on 2007-06-24
**NOT AVAILABLE IN THE USA** Grr...

How is it that I can't install Zattoo yet? My country of residence is the USA, but I'd love to have these French speaking channels (I'm French). Anybody knows if there is a bypass for that?

---

### Post by hyper_ch on 2007-06-24
Because zattoo is available only in a few countries...

---

### Post by the8thstar on 2007-06-24
Yep, another dream going away... :(

---

### Post by Enverex on 2007-06-24
> **the8thstar said:**
> **NOT AVAILABLE IN THE USA** Grr...

How is it that I can't install Zattoo yet? My country of residence is the USA, but I'd love to have these French speaking channels (I'm French). Anybody knows if there is a bypass for that?

Use a proxy based in one of the countries they will stream to.

I HATE places that for no actual reason stop you from using something based on some unrelated factor.

---

### Post by Swab on 2007-06-24
> **hyper_ch said:**
> I have problems with the new zattoo version... starting up is fine... selecting a channel also... buffering works also... then i see for a fraction of a second an image and then I get a segfault:


[email]hyper@xubi:~/.Zatt[/email]oo/Data/logs$ zattoo_player
11:20:36 AM 06/24/2007 [MSG]    Current locale is en_US.UTF-8
11:20:36 AM 06/24/2007 [MSG]    Welcome to Zattoo (2.2.10.6523)
11:20:36 AM 06/24/2007 [MSG]    Checking for update...
11:20:36 AM 06/24/2007 [MSG]    There are no updates available.
11:20:36 AM 06/24/2007 [MSG]    Further log messages will be written to /home/hyper/.Zattoo/Data/logs/zattoo.debuglog
Segmentation fault (core dumped)

Anyone else experiencing this?


No, the new version worked fine for me... I used the deb.

---

### Post by Swab on 2007-06-24
> **Enverex said:**
> Use a proxy based in one of the countries they will stream to.

I HATE places that for no actual reason stop you from using something based on some unrelated factor.

It's because they need to work out agreements for each country.  That's why the UK has different channels available than Switzerland.

---

### Post by the8thstar on 2007-06-24
**Enverex** said:

> Use a proxy based in one of the countries they will stream to.

I HATE places that for no actual reason stop you from using something based on some unrelated factor.

How do I use a proxy?

---

### Post by netztier on 2007-07-02
> **hyper_ch said:**
> I have problems with the new zattoo version... starting up is fine... selecting a channel also... buffering works also... then i see for a fraction of a second an image and then I get a segfault:


[email]hyper@xubi:~/.Zatt[/email]oo/Data/logs$ zattoo_player
11:20:36 AM 06/24/2007 [MSG]    Current locale is en_US.UTF-8
11:20:36 AM 06/24/2007 [MSG]    Welcome to Zattoo (2.2.10.6523)
11:20:36 AM 06/24/2007 [MSG]    Checking for update...
11:20:36 AM 06/24/2007 [MSG]    There are no updates available.
11:20:36 AM 06/24/2007 [MSG]    Further log messages will be written to /home/hyper/.Zattoo/Data/logs/zattoo.debuglog
Segmentation fault (core dumped)

Anyone else experiencing this?

Exactly the same behaviour, on Ubuntu 7.04.

However it runs when I launch it from either a **root shell** or a panel launcher with **gksu /usr/bin/zattoo_player**. It just can't remember passwords etc when running with gksu - but it runs.

best regards

Marc

---

### Post by Kosimo on 2007-07-02
Hello guys.
I'm using Zattoo in Feisty.  
There is a Linux client, in a .deb compilation for Feisty. Just double click and works.
I can watch almost 10 channels from Barcelona.
Is exactly the same client than in Win. No differences at all.

;)

---

### Post by hyper_ch on 2007-07-02
@ Kosimo
What version are you running?

@ Netztier
Do you still have the old version .deb?

---

### Post by Kosimo on 2007-07-02
> **hyper_ch said:**
> @ Kosimo
What version are you running?

@ Netztier
Do you still have the old version .deb?

Hmmm I don't remember exactly (I'm in the office right now)
But the last .deb from the website I guess... (Downloaded one week ago from Zattoo Website)

Here works because they just added Catalonia in their "active" countries. Everything is a matter of licenses. If some Catalan channel buys some Italian movie, pays for that movie to be showed in Catalonia. Nowhere else. So, programs like Zattoo can't provide a German user to watch this Movie on this catalan channel.

---

### Post by netztier on 2007-07-02
> **hyper_ch said:**
> 
@ Netztier
Do you still have the old version .deb?

nope, sorry: I only ever had [B]zattoo-2.2.10-6523-i386.deb
[/B]

I posted a question on zattoo.com asking what the thing with/without sudo or gksu was, so we can debug further.

best regards

Marc

---

### Post by hyper_ch on 2007-07-02
It runs as root... hmm, do I really want that?

I guess until a new version comes out I'll stick to the VmWare-WinXP & Zattoo option...

---

### Post by Kosimo on 2007-07-02
> **hyper_ch said:**
> It runs as root... hmm, do I really want that?

I guess until a new version comes out I'll stick to the VmWare-WinXP & Zattoo option...

You mean the program?
It doesn't...
I don't need to give a root privileges to run it.

Witch version did you install?

---

### Post by quinnten83 on 2007-07-02
They don't stream to the Netherlands, so I am out of luck.
Does Joost have a linux version?

---

### Post by netztier on 2007-07-02
> **hyper_ch said:**
> It runs as root... hmm, do I really want that?


I don't think you do - neither do I want to run it as root. I never meant to suggest running it with sudo/gksu permanently.

The point I'm trying to make with suggesting to try it with sudo/gksu is this: if it runs as root, it's an indication that it basically works - that all libraries & plugins etc are there and that they do interact well with each other.

If it doesn't run as root, it's most often a problem that can be fixed relatively easy - giving write access to a temporary directory (or configuring it to use another one) or another ressource.

best regards

Marc

---

### Post by hyper_ch on 2007-07-03
I'll try tonight running it as root... thx for the suggestion :)

---

### Post by netztier on 2007-07-03
> **netztier said:**
> Exactly the same behaviour, on Ubuntu 7.04.

However it runs when I launch it from either a **root shell** or a panel launcher with **gksu /usr/bin/zattoo_player**. It just can't remember passwords etc when running with gksu - but it runs.



And now, to make the confusion a bit more complete: it runs on my desktop machine. The above statement applies to my laptop machine.

Both run Ubuntu 7.04, everything up-to-date.

**Desktop:** AMD Athlon64 3000+ (Venice) in a Shuttle SN95Gv3 barebone, 1GByte RAM, running 32bit-generic kernel, (*not* amd64), with restricted-modules and the nvidia driver for the Nvidia GeForce 7600GT AGP card (yes, AGP, not PCI-E).

**Laptop:** HP nc6000, 1.6GHz Pentium-M, 1 GByte RAM, 32bit generic kernel, with restriced-modules for the fglrx ATI driver and madwifi.

I can't help but my thoughts are circling around the difference "ATI vs Nvidia" - what do your systems running (or not) have as graphic cards and driver combinations?

regards

Marc

---

### Post by Dave_Man on 2007-09-14
Can't download it from my country.
Will it work if I get the deb from somewhere else?

---

### Post by hyper_ch on 2007-09-16
no, if it not available in your country then you can't use it... or you will need to run it through a proxy server in a country that is supported.

---

### Post by nemesis7 on 2007-10-02
Hi,

I tried to install zattoo on my feisty 64 but it is not working due to the architecture 64.


igor@X2:~$ zattoo_player 
zattoo_player: error while loading shared libraries: libgnomeui-2.so.0: wrong ELF class: ELFCLASS64
igor@X2:~$ uname -a
Linux X2 2.6.20-16-generic #2 SMP Sun Sep 23 18:31:23 UTC 2007 x86_64 GNU/Linux
igor@X2:~$ 

How did you manage to install it on x64 ?

---

### Post by doncristobal on 2007-10-21
I can use the new Zattoo client on my new Xubuntu 7.10 (gutsy gibbon), but _only_ with zoom=100%. Double size and full screen make the picture stop-and-go and after some seconds also the audio brakes. 

When I activate the restricted driver for my ATI graphics chip (I have an IBM Thinkpad T42), Zattoo does not even start up: It shows the frame of its window for 1 second and then disappears again. 

Does anyone have similar problems?

---

### Post by fonsi2099 on 2007-10-24
I resolve the same item, with the following thread: [http://ubuntuforums.org/showthread.php?t=474790&highlight=skype](http://ubuntuforums.org/showthread.php?t=474790&highlight=skype)

Now the cool thing on this is that  you can install getlibs " Automatically solves dependencies for binaries" from [http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb](http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb) and follow the same instructions for Skype, only be careful you need to replace skype with zattoo.

Tip: If it is a 32-bit .deb package and you are running a 64-bit Ubuntu/Debian you must use
Code:
**sudo dpkg -i --force-all zattoo-3.0.5.8208-i386.deb**
now:
code:
**$ getlibs /usr/bin/zattoo**

[I]Matched library libQtCore.so.4 to /feisty/libs/libqt4-core
Matched library libQtDBus.so.4 to /feisty/libs/libqt4-core
Matched library libQtGui.so.4 to /feisty/libs/libqt4-gui
Matched library libQtNetwork.so.4 to /feisty/libs/libqt4-core
Matched library libsigc-2.0.so.0 to /feisty/libs/libsigc++-2.0-0c2a
The following i386 libraries will be installed:
/feisty/libs/libqt4-core
/feisty/libs/libqt4-gui
/feisty/libs/libsigc++-2.0-0c2a
Continue? (y/n) y
Downloading.....Installing libraries ...
New depedencies have been detected:
libdbus-1.so.3
Matched library libdbus-1.so.3 to /feisty/libs/libdbus-1-3
The following i386 libraries will be installed:
/feisty/libs/libdbus-1-3
Continue? (y/n) y
Downloading.....Installing libraries .[/I]..

and it works! For me wonderfull on my 64Bit -Athlon- Gutsy 

:guitar: 
[FONT="Lucida Console"]la vida es un sueño y para soñar de debe estar despierto [/FONT]

---

### Post by the8thstar on 2007-11-09
> no, if it not available in your country then you can't use it... or you will need to run it through a proxy server in a country that is supported.

How can you run through a proxy server??? Is there a HOW-TO anywhere?

---

### Post by eldara5 on 2007-11-09
How do you get Zattoo ive been on the website but when i sign up i just keep being told ive been added to the witing list

---

### Post by hyper_ch on 2007-11-09
if you are in a country where zattoo runs then you will get an email in a few days...

---

### Post by the8thstar on 2007-11-09
And if you don't, HOW DO YOU CRACK IT?

---

### Post by hyper_ch on 2007-11-12
you need to go through a proxy server in a country where zattoo runs ;9

---

### Post by john_markh on 2008-04-29
Just downloaded a latest version (3.1.1) of Zattoo and it works like a charm (in UK); Have around 20 channels... TV guide... Good video and sound quality...
I'm in love!

---

