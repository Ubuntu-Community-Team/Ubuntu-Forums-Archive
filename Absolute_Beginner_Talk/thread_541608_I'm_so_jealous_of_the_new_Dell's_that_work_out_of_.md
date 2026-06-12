---
title: "I'm so jealous of the new Dell's that work out of the box!"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by hiloguy on 2007-09-03
I just did a clean install on a Toshiba notebook to see if I’m ready to fully switch my office to Ubuntu before there is no longer any support for XP, after which the only other alternative would be Macs. 

So far, I love Ubuntu (6.10), but like so many others, I’ve got a few days into trying to get the wireless card working, and it still isn’t.  So my innocent question is, how is it that these geniuses who developed this elegant, powerful OS and the attendant GUI have so dropped the ball on getting wireless cards to configure?  From the posts I’ve been reading (lots of them), it seems a pervasive issue and that I’m going to have to really get into the intricacies of Ubuntu just to get online.  Why aren’t there one or two recommended cards with a simple installation procedure?  I’d go buy one whatever the cost!

Help!

---

### Post by PmDematagoda on 2007-09-03
Have you tried wireless support under Ubuntu 7.04?

---

### Post by wolfen69 on 2007-09-03
does windows wireless work out of the box? no, it doesnt. try ubuntu 7.04. if it doesnt work, come back here and we will help you.

---

### Post by dwhitney67 on 2007-09-03
I have a 2006 vintage Dell notebook.  It works "out of the box" when I installed with the alternate distro CD version 7.04.  I had to get a driver from ATI for the video chip set to get the video resolution I desired, but that was a breeze.  I cannot recall if I had to do anything special for the wifi chip-set (of which I have a Broadcom version).

Btw, most notebooks have a wired-ethernet port included.  Use that until you are able to go mobile.

Also, forget windows.  I had no heartache about blowing it away to dedicate my entire notebook to Ubuntu.  I made a similar decision during 2006 with my other notebook in which I installed Fedora Core.

---

### Post by anewguy on 2007-09-03
What is your network card?  Please post the output of the following back here and we'll see if we can help!:)

lspci -C network

lspci

---

### Post by Chris S. on 2007-09-03
> **hiloguy said:**
>  Why aren’t there one or two recommended cards with a simple installation procedure?  I’d go buy one whatever the cost!

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

They aren't really "recommended" cards, but you can go there to read more about what cards may or may not work with Ubuntu.  Many wireless cards do work out of the box.

---

### Post by hiloguy on 2007-09-03
> **anewguy said:**
> What is your network card?  Please post the output of the following back here and we'll see if we can help!:)

lspci -C network

lspci

I really want to thank everybody who responded to my post!  But here's the deal.  I'm very new to Ubuntu.  I'm and old XP-PRO guy who is sick of M/S and wants very much to make this work, but I have no idea what "the output of Ispci-C network" or "Ispci[?QUOTE]" mean.  I have no idea of what the pages of cryptic symbols and other info mean in all of the instructions I'm assuming I will need to learn in order to get my wireless card configured.

Somebody asked what the card is i'm using.  The one I tried using first is a Belkin FSD6020.  I read of so many problems with that card that I went into some of the lists that show cards that are supposed to work out of the box, and hey, the Belkin is one of them!  go figure.

And now several people have recommded I switch to another version of Ubuntu.  Sheesh,  I've already got the CDs for 6.06 LTS, 6.06.1 LTS and 6.10, and now should I really go get another one?  The ones I have came with books.  If I really need yet another one, where do I get it?  And will it really make this easier?

Somebody really needs to write a manual IN PLAIN ENGLISH on getting a wireless adaptor up and running.  :)

---

### Post by beefcurry on 2007-09-03
Get the newest Fiesty Fawn 7.04 , It has the best drivers support. Newer versions have better support for drivers. lspci just means list pci ports. It lets us see what devices you have connected so we can help solve the problem. you will get used to them soon enough.

---

### Post by Lord Illidan on 2007-09-03
New versions of Ubuntu contain newer drivers and the like. As for that website, it seems there are 3 belkin F5D6020...and they work with different results..We need more information here.

---

### Post by hyper_ch on 2007-09-03
When you get told to run a command like this:

```

lspci -C network

```

Open a terminal window and copy'n'paste it... ;)

Then you will get some output depending on the command issued... that's the output that is desired here to see what wifi card/chip you have.

If you want to know more about a given command (such as "lspci") just run in the shell the following command:

```

man COMMAND

```e.g.
```

man lspci

```
That will display the rather helpful man pages for the command... you can leave the man pages by pressing the "q" key.

To get a short info about a command use this:
```

COMMAND --help

```
That should print on the screen the basic usage.

P.S.: My LinkSys Ralink 2500 chip (PCI) worked out of the box also... however it seems that USB cards do have a few issues...

---

### Post by southernman on 2007-09-03
To open a terminal go to Applications > Accessories > Terminal

For future use when you do the above you can left click on it and hold the button while you drag it to your panel or desktop.

---

### Post by GSF1200S on 2007-09-03
My first try on Ubuntu was 6.10. I had a ethernet cable running to my laptop because wireless simply didnt work. My computer was at that time 1 1/2 months old.

Doing massive research and posting in these forums, I found out that 7.04 had an updated HAL and that madwifi drivers would possibly work for my card. 7.04 is also the version of Ubuntu that introduced the restricted drivers manager. As soon as I did a dist-upgrade to 7.04, the madwifi drivers worked.

Im not too much of a Gnome guy- I like it, but I like KDE a tad better. That said, I love the development cycle, community and general layout of Ubuntu. Therefore, I installed the Ubuntu 7.04 Kernel, and installed KDE core.

In order to do this, I had to have internet- low and behold my once impossible wireless card *worked out of the box!!* I didnt even have a GUI yet! I did some quick research on scanning and selecting a network from the CLI, and bam, I was linked and downloading KDE core.. Thats how fast this distro moves. Give 7.04 a shot, and if that doesnt work, give Gutsy a shot... Your card is bound to be supported soon.

---

### Post by Paulmd on 2007-09-03
[FONT="Comic Sans MS"]> **hiloguy said:**
> I really want to thank everybody who responded to my post!  But here's the deal.  I'm very new to Ubuntu.  I'm and old XP-PRO guy who is sick of M/S and wants very much to make this work, but I have no idea what "the output of Ispci-C network" or "Ispci[?QUOTE]" mean.  I have no idea of what the pages of cryptic symbols and other info mean in all of the instructions I'm assuming I will need to learn in order to get my wireless card configured.

Somebody asked what the card is i'm using.  The one I tried using first is a Belkin FSD6020.  I read of so many problems with that card that I went into some of the lists that show cards that are supposed to work out of the box, and hey, the Belkin is one of them!  go figure.

And now several people have recommded I switch to another version of Ubuntu.  Sheesh,  I've already got the CDs for 6.06 LTS, 6.06.1 LTS and 6.10, and now should I really go get another one?  The ones I have came with books.  If I really need yet another one, where do I get it?  And will it really make this easier?

Somebody really needs to write a manual IN PLAIN ENGLISH on getting a wireless adaptor up and running.  :)

I'll get to the networking part, but first, some Linux detangling is in order. 

To download ubuntu: 

[http://www.ubuntu.com/](http://www.ubuntu.com/)

Click the big friendly button that says "Download Now." You can also order CDs.

A new distribution of Ubuntu is issued on a schedule of about every 6 months.  The rule of version numbers isn't the typical one. Ubuntu's is little more than a date code in the format YEAR.MONTH.

6.06 was released June 2006. The latest release is 7.04, released in April of this year. The next revision is scheduled for October.

The command line (terminal) is similar to the command line in XP. But with more functions, not available through the menus.

You get to terminal by clicking applications->accessories->terminal.

So if someone asks for the output of lspci, navigate to the terminal and type 'lspci'. [COLOR="Red"] Commands are case sensitive, lspci is not the same as LsPCI, or Lspci. [/COLOR] As in DOS you can redirect the output of a command to a file, by using the '>' symbol.   

For example, 

```
# lspci > myfile.txt
```   (it's a lowercase l).



 will create a file named 'myfile.txt' and populate it with the output of lspci, which would otherwise just print to the screen.

To find out what a particular command does type:

```
man [command]
```

Man is the manual. To exit the manual, type 'q'. Man is THE single most important command in linux.

A good resource is [http://hardware4linux.info](http://hardware4linux.info)

To find out a list of good wireless cards for Ubuntu, click on the Search button, select 'working wireless cards form the 'type' drop-down, and select 'Ubuntu (your version here)' from the 'linux' dropdown menu.


In your cases,  Ubuntu 6.06 returns just 2, as does 6.10. But the latest released version (7.04) returns 53 (but there is some that are listed multiple times, and the ones with negative ratings are to be avoided). With several models of Intel wireless cards recieving top ranking. This is why people are recommending the newer version to you.

the Belkin F5D6020 is not on any list (on this site).  But the F5D7000 is listed as working under 7.04.

Hope this helps,

Paul

[/FONT]

---

### Post by hiloguy on 2007-09-03
Thank you, thank you for all the assistance!  It's all very encouraging to know I'm not swimming this murky pond all alone.  I'll go ahead with Feisty Fawn 7.04 and then get back here with my progress -- or lack of it!

Aloha from Hawaii!

---

### Post by Paul133 on 2007-09-03
Good luck. We'll be here to help.

---

### Post by nonewmsgs on 2007-09-03
the netgear WPN511 rangemax comes close to working out of the box.  i have bought a few of them and you type 3  commands in the console and it's set up and it supports wep.  they'll run you ~$35 on ebay.

---

### Post by hiloguy on 2007-09-03
> **nonewmsgs said:**
> the netgear WPN511 rangemax comes close to working out of the box.  i have bought a few of them and you type 3  commands in the console and it's set up and it supports wep.  they'll run you ~$35 on ebay.

Sounds good!  And if I go buy one of those, where do I find the 3 magic commands?  Also, is it likely to work with version 6.10?  I've tried several times to burn the 7.04 download to a cd and it will  not finalize on a 700 MB cd.

I love you folks - - - you are so patient!  :)

---

### Post by GSF1200S on 2007-09-03
> **hiloguy said:**
> Sounds good!  And if I go buy one of those, where do I find the 3 magic commands?  Also, is it likely to work with version 6.10?  I've tried several times to burn the 7.04 download to a cd and it will  not finalize on a 700 MB cd.

I love you folks - - - you are so patient!  :)

I cant tell you the 3 commands, but I can suggest some help on burning 7.04. Are you using an .ISO burning program? ImageBurn is a free ISO burning program you can download and use....

---

### Post by hiloguy on 2007-09-04
> **Paulmd said:**
> [FONT="Comic Sans MS"]

I'll get to the networking part, but first, some Linux detangling is in order. 

To download ubuntu: 

[http://www.ubuntu.com/](http://www.ubuntu.com/)

Click the big friendly button that says "Download Now." You can also order CDs.

A new distribution of Ubuntu is issued on a schedule of about every 6 months.  The rule of version numbers isn't the typical one. Ubuntu's is little more than a date code in the format YEAR.MONTH.

6.06 was released June 2006. The latest release is 7.04, released in April of this year. The next revision is scheduled for October.

The command line (terminal) is similar to the command line in XP. But with more functions, not available through the menus.

You get to terminal by clicking applications->accessories->terminal.

So if someone asks for the output of lspci, navigate to the terminal and type 'lspci'. [COLOR="Red"] Commands are case sensitive, lspci is not the same as LsPCI, or Lspci. [/COLOR] As in DOS you can redirect the output of a command to a file, by using the '>' symbol.   

For example, 

```
# lspci > myfile.txt
```   (it's a lowercase l).



 will create a file named 'myfile.txt' and populate it with the output of lspci, which would otherwise just print to the screen.

To find out what a particular command does type:

```
man [command]
```

Man is the manual. To exit the manual, type 'q'. Man is THE single most important command in linux.

A good resource is [http://hardware4linux.info](http://hardware4linux.info)

To find out a list of good wireless cards for Ubuntu, click on the Search button, select 'working wireless cards form the 'type' drop-down, and select 'Ubuntu (your version here)' from the 'linux' dropdown menu.


In your cases,  Ubuntu 6.06 returns just 2, as does 6.10. But the latest released version (7.04) returns 53 (but there is some that are listed multiple times, and the ones with negative ratings are to be avoided). With several models of Intel wireless cards recieving top ranking. This is why people are recommending the newer version to you.

the Belkin F5D6020 is not on any list (on this site).  But the F5D7000 is listed as working under 7.04.

Hope this helps,

Paul

[/FONT]

Thanks a bunch, Paul!  Most of that helped a lot.  "Detangling" is an apt description.  I downloaded 7.04 but it will not boot.  I guess I'll try it again when I get a chance, but in the meanwhile I tried to decipher the pages of info on "HowToMD5SUM" and I got nowhere, again because of the cryptic nature of writing that assumes the reader knows what it all means.  This is going to be a challenge, but I'm up to it.  What I need right now is a beer.  Maybe two.  I'll be back!

Thanks again; I've never had such help from any other forum on anything!

---

### Post by Paulmd on 2007-09-04
> **hiloguy said:**
> Thanks a bunch, Paul!  Most of that helped a lot.  "Detangling" is an apt description.  I downloaded 7.04 but it will not boot.  I guess I'll try it again when I get a chance, but in the meanwhile I tried to decipher the pages of info on "HowToMD5SUM" and I got nowhere, again because of the cryptic nature of writing that assumes the reader knows what it all means.  This is going to be a challenge, but I'm up to it.  What I need right now is a beer.  Maybe two.  I'll be back!

Thanks again; I've never had such help from any other forum on anything!

[FONT="Comic Sans MS"]Ignore MD5SUM, for now. It's a bit advanced, and you just need it to work. :) It can be used to verify that a CD image is valid, but in general, I've found it pretty useless. (I just don't have that many failed downloads) Don't borrow extra headaches. If you just have to know about md5sums, all they do is read the file, and compute a relatively small codestring. Which is then compared against one previously calculated (found on the site you downloaded the file from). If the file is altered in transit, the md5sums don't match. If course, if the site doesn't list md5sums, there's no point in calculating them, as there's nothing to compare against.



One place where people often steer wrong on burning ISOs is they burn it as a file on the CD, instead of using the Burn Image feature that is built in to various CD writing programs. The built in CD burning feature on XP doesn't do images. You need a real program for that, such as Nero, or if you want a decent free one:

(reaonably full featured)
[http://www.cdburnerxp.se/](http://www.cdburnerxp.se/)

(barebones, but you can hardly go wrong, as long as you don't need dvds)

[http://www.burnatonce.net/downloads/](http://www.burnatonce.net/downloads/)

If you feel frustrated, take a break, frustration can lead to irrational decisions. I've been there, All too often :).


In Linux, you should have k3b available already. There are others, but i've not used them.

[/FONT]

---

### Post by hiloguy on 2007-09-04
[http://www.burnatonce.net/downloads/](http://www.burnatonce.net/downloads/)

If you feel frustrated, take a break, frustration can lead to irrational decisions. I've been there, All too often :).


In Linux, you should have k3b available already. There are others, but i've not used them.

[/FONT][/QUOTE]

Wow, what a deal.  so simple and it worked!  In half the time it took to burn the 7.04 download (that would not boot) with Nero, BunrAtOnce made ont that works.  I like it.  Progress!

Stay tuned . . . :)

---

### Post by odinb on 2007-09-04
What I have learned is that just because someone says that their Belkin-card works out of the box, does not mean that all Belkin cards will....

What you need to find out is what chip manufacturer built the chip the WLAN card is based on. I have installed 7.04 with 5 different WLAN cards on 4 different laptops so far,

My conclusion so far is backed by what I've read in other places here in the forum as well:

Intel worked with no configuration other than WPA.
Prism worked with no configuration other than WPA.
Broadcom1 worked with FWcutter.
Broadcom2 (Dell card in a HP machine) worked with reinstall of 7.04 and compiling of NDISWRAPPER v1.47 (ubuntu 7.04 includes v1.38). Ofcourse that broke saturday with the kernel-updates, and I had to recompile to get it working again.

Belkin (and most others) uses chipset from several different vendors, and Broadcom is one of them. This is why you need to figure out what chipset your card is based on.

Like the others said in here lspci will help you resolve this issue.

Good luck and do not give up!

---

### Post by hiloguy on 2007-09-04
> **odinb said:**
> What I have learned is that just because someone says that their Belkin-card works out of the box, does not mean that all Belkin cards will....

What you need to find out is what chip manufacturer built the chip the WLAN card is based on. I have installed 7.04 with 5 different WLAN cards on 4 different laptops so far,

My conclusion so far is backed by what I've read in other places here in the forum as well:

Intel worked with no configuration other than WPA.
Prism worked with no configuration other than WPA.
Broadcom1 worked with FWcutter.
Broadcom2 (Dell card in a HP machine) worked with reinstall of 7.04 and compiling of NDISWRAPPER v1.47 (ubuntu 7.04 includes v1.38). Ofcourse that broke saturday with the kernel-updates, and I had to recompile to get it working again.

Belkin (and most others) uses chipset from several different vendors, and Broadcom is one of them. This is why you need to figure out what chipset your card is based on.

Like the others said in here lspci will help you resolve this issue.

Good luck and do not give up!



Well, things are looking up!  I installed 7.04 and instantly at least my ethernet connection worked, which it did not with 6.10.  So I've been looking for an Intel notebook adaptor and all I can find are desktop cards.  Do you know if Intel makes a notebook adaptor?  My Belkin adaptor is pre-hisotirc and needs replacement anyway.  I also have acess to  new Linksys WPC54G, but I haven't read anything really promising about them on this forum.  They work, but not without effort. Is there a "best" wireless adaptor?  This is for a Toshiba 1135 that is my old reliable workhorse.  

And here's a non-related quesiton:  Is there a way I can eliminate the need for the administrator's (that would be me) password?  Nobldy uses this rig besides me . . .

---

### Post by Brightbelt on 2007-09-04
One thing I've learned over time with Ubuntu is not to give up so fast. Many things that look difficult on the outside are not all that hard once you dig in.  With that said,....
Check out this thread for the WPC54G   [http://ubuntuforums.org/showthread.php?t=5645](http://ubuntuforums.org/showthread.php?t=5645) 

Also, there might be a simpler way. If you're using the Gnome desktop interface (it's the default one for Ubuntu; KDE comes with Kubuntu), I recommend going to Add/Remove which is one of your program installers...You'll need to be on ethernet here to get online.

Once there, in the upper right drop-down menu, choose 'All Available Applications'. Then in the search box at the top left, type 'Windows Wireless Drivers'. That program should come up in your main list area as a choice with a check-box to click - choose it to install and click apply. 

This program is a GUI version (Graphic User Interface version) of Ndiswrapper, a program that makes windows drivers work for Linux. It's FAR easier to use for beginners. It also gets you around using the command line.

Now I'm on my Macbook now so I can't be sure, but I think you'll find the Windows Wireless Driver program on the Applications/System menu once you've installed it. If it's not there, I know it's right in the same list as 'Synaptic Package Manager'.   

All you have to do is pull up the Windows Wireless Drivers program, click the 'Install File' button and navigate to the INF file in your windows driver folder. Needless to say you will need to have downloaded the windows driver from the Linksys website and have it available on your desktop or in your files. There is usually one INF file in the windows driver folder and that's what you use with Ndiswrapper for Ubuntu.

Good Luck, Frank B.

---

### Post by Brightbelt on 2007-09-04
Also, I should mention this since it's happened to me more than once. This graphic interface version of Ndiswrapper tends to "break" easily. What I mean is that it works for a time or two and then I've had the experience of choosing it from my menu and having nothing happen, IE,  meaning that the program just does not appear for some reason.

But it's a place to start until you get more comfortable with the command line. I know that being new to Ubuntu, you just want to get up and running.

Good Luck, Frank B.

---

### Post by Brightbelt on 2007-09-05
I'm on my Ubuntu System now. If you get the 'Windows Wireless Drivers' program installed, it should be located in the System Menu/Administration.

Frank B.

---

### Post by hiloguy on 2007-09-06
> **hyper_ch said:**
> When you get told to run a command like this:

```

lspci -C network

```

Open a terminal window and copy'n'paste it... ;)

Then you will get some output depending on the command issued... that's the output that is desired here to see what wifi card/chip you have.

If you want to know more about a given command (such as "lspci") just run in the shell the following command:

```

man COMMAND

```e.g.
```

man lspci

```
That will display the rather helpful man pages for the command... you can leave the man pages by pressing the "q" key.

To get a short info about a command use this:
```

COMMAND --help

```
That should print on the screen the basic usage.

P.S.: My LinkSys Ralink 2500 chip (PCI) worked out of the box also... however it seems that USB cards do have a few issues...


Thanks so much for your patient reply!  All of a sudden this stuff has clicked in, probably because I was weaned on dos back in the early 80s where commands ran everything.  I get it now!

Early 80s ... my first "real" computer didn't even have an OS.  The OS was on one 5-1/4" floppy and you put in the left (of two) drives and did your amazing work on the other one.  No HD, either.  Hey, I paid about $4500 for that thing!  About 20 computers later, I'm starting over with Linux -- and loving it!

---

### Post by R_U_Q_R_U on 2007-09-06
[I]I installed the Cisco Aironet CB21AG-A-K9 cardbus wireless card on a Dell D600. Wireless worked without any issues. I am using WPA security and Fiesty asked for me to select the SSID of my network...I find the old Dell laptops work great with Ubuntu 7.04. I did not have any configuration issues.
 :guitar:
[/I]

---

### Post by hiloguy on 2007-09-07
After trying three times to burn a downloaded 7.04 to a cd, you suggested [http://www.burnatonce.net/downloads/](http://www.burnatonce.net/downloads/).

Hey, that's slick!  Simple little app and it worked the first time and in half the time it took Nero to (not) do it.

Thanks a bunch!:)

I'm blown away with the competent helpfulness and cooperation of this Forum.  It makes me extra glad I decided to move to Ubuntu.

---

