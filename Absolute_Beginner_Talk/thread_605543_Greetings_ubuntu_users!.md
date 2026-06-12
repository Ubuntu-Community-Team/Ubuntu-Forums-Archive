---
title: "Greetings ubuntu users!"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by MaDeX on 2007-11-07
I'm completlely new to this, ive managed to accidentally wipe my 4 hard drives full of music trying to install unbuntu.

Now its installed onto my clear hard drive :(

I need to install 8800 nvidia gts drivers - I have read the forums and still know nothing, people are talking but i'm not registering what they mean.

I would love for someone to instant message me some help so I can install eve online to play.


Thanks - MaDeX

ICQ 55149484 or MSN [email]madexmatt@yahoo.com[/email]

---

### Post by MaDeX on 2007-11-07
Bumping for love of new OS..

:)

If it was too easy I wouldnt be doing this!

---

### Post by thenailedone on 2007-11-07
Hello from one n00b to another :)

Have installed and removed and lost data quite a few times when the urge for the alternative OS hits me (which is the case presently, just waiting for Gutsy to be delivered)...

Keep the faith and enjoy the ride ;)

---

### Post by laidback on 2007-11-07
Welcome to the world of Ubuntu.
Not sure about your graphics card issue, it's not listed on the supported video card list, but that's a little old now.:-

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia)

You may need Ndiswrapper...not something I've ever used but you can at least search for it.

I suspect other respondents will want to know which version of Ubuntu you are running and perhaps a litle more about the card.

Kindest Regards

Laidback

---

### Post by MaDeX on 2007-11-07
Hi, and thankyou for replies - I want to stay with ubuntu forever!

Could you explain what gutsy is?

---

### Post by Pumalite on 2007-11-07
For Nvidia 8800 you might want to try this:
When grub comes up select the second ubuntu option.

When its finished you should now have a terminal.

login

run sudo passwd

setup your 'root' password

now run

sudo apt-get install nvidia-glx-new

sudo nvidia-xconfig

sudo shutdown -r now

Then use the normal option to boot ubuntu.

---

### Post by Circus-Killer on 2007-11-07
gutsy gibbon is just the codename for version 7.10 of ubuntu (the latest version).

also, for your video card, try click on "System -> Administrator -> Restricted Drivers".
If the currently available nvidia drivers support your gfx card, then the Restricted Drivers section will give you an option to install the drivers. If there is nothing listed under the restricted drivers section, then that usually means either your card is too old, or too new.

if its too new, you will just have to wait till the drivers support your card. if its too old, often the best solution is to just run the open source drivers, which i'm sure someone else here can give you advise on about how to do that.

but as said, first go see under Restricted Drivers section to see if it gives you the option to install the proprietory nvidia drivers.

---

### Post by MaDeX on 2007-11-07
I'ts 7.04 version of ubuntu I believe - and whats grub?

Also gutsy is available for download?

---

### Post by PmDematagoda on 2007-11-07
Grub is the boot-loader of Ubuntu, when you start up the computer, you see a menu where you can select different choices where one includes a phrase "Recovery Mode", you should select that and boot Ubuntu in recovery mode where you can make the necessary changes as suggested by Pumalite.

---

### Post by mivo on 2007-11-07
Using a 8800GTS here and it is supported by the restricted drivers. Actually, Ubuntu should prompt you for it, too (small icon in the right upper corner), when you first login.

---

### Post by PmDematagoda on 2007-11-07
> **MaDeX said:**
> 

Also gutsy is available for download?

Of course, the iso can be found here:-

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by Circus-Killer on 2007-11-07
7.04 - Feisty Fawn
7.10 - Gutsy Gibbon

yes, gutsy gibbon is available for download.
grub is a program known as a bootloader. your computer never starts the OS directly, even in windows. all computers require a small program to be installed in the MBR (master boot record) of the harddrive. your computers bios will check the MBR during boot, and will run whatever is in the MBR, which will be the bootloader of choice (even windows uses a bootloader).

the bootloader itself then tells the computer "how" to start the OS in question. bootloaders are interchangable. for example, the default windows bootloader (that you never really interact with) can be set up to startup a linux OS, same as GRUB can be set up to start windows.

what bootloader you use is not important, but by default in most linux systems, GRUB is the bootloader of choice and is what is installed with ubuntu by default.

---

### Post by thenailedone on 2007-11-07
:lolflag:... man their are a lot of ppl on this forum... before I have even had a chance to read a post it has been answered by three different ppl :)  @ least I know that as soon as I start struggling with my installation I will get the answers I require...

---

### Post by MaDeX on 2007-11-07
LOL , these guys are amazing - I think the community makes the product too.


Thanks guys I will try restricted drivers tonight, however i'm sure I tried those and it gave me a error message saying unable to start X server?

(Or did I install from the nvidia site)

Bleh - was tired.

---

### Post by Circus-Killer on 2007-11-07
> **thenailedone said:**
> man their are a lot of ppl on this forum... before I have even had a chance to read a post it has been answered by three different ppl :)  @ least I know that as soon as I start struggling with my installation I will get the answers I require...

yeh, we rock! :lolflag:

---

### Post by MaDeX on 2007-11-07
Someones been talking about "envy" is this a automated download and installer for us newbs?

---

### Post by Maestro23 on 2007-11-07
> **MaDeX said:**
> Someones been talking about "envy" is this a automated download and installer for us newbs?

Has helped many people with their video card woes.

Envy: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

*Works for both ATI and Nvidia

---

### Post by Ub1476 on 2007-11-07
Usually, after a clean installation of Ubuntu, just go to System>Administration>Restricted Driver Manager, and enable the nvidia driver. If you get an error of some sort, go to Administration>Software Sources>Ubuntu Software tab> Enable all the options ("source code" is not necessary though..).

Envy is for graphic cards with **open** drivers. I'm quite sure nvidiea 8800 doesn't have that.

---

### Post by MaDeX on 2007-11-07
Should I download Gutsy?! Would that help?

---

### Post by PmDematagoda on 2007-11-07
Gutsy is 7.10, you can find it at the link I gave, and to Ub1476, no, Envy install's the proprietary Nvidia drivers by downloading them directly from the Nvidia website.

---

### Post by laidback on 2007-11-08
Gutsy is reported (claimed) to have better hardware support than Feisty, so I think I'd try 7.10 (Gutsy) to get the best chance of a good installation with your video card. It's also the latest version so you'll be as up to date as possible.
If you don't want to download Gutsy (or cannot) it is available from various sources. I use Linux-man who's here in the UK. Mail me for more info should you need it.

---

### Post by thenailedone on 2007-11-08
> **laidback said:**
> Gutsy is reported (claimed) to have better hardware support than Feisty, so I think I'd try 7.10 (Gutsy) to get the best chance of a good installation with your video card. It's also the latest version so you'll be as up to date as possible.
If you don't want to download Gutsy (or cannot) it is available from various sources. I use Linux-man who's here in the UK. Mail me for more info should you need it.

...or just order your free cd from [https://shipit.ubuntu.com/]("https://shipit.ubuntu.com/")... (well relatively free... sometimes their is a R20.00 import duty to be paid...)

---

### Post by liberalist on 2007-11-08
I have installed version 7.10 with quite some problems on my Intel iMac (ATI video card). Should you need any help over MSN/Yahoo, you can add me by e-mailing [http://xinbox.com/opera](http://xinbox.com/opera)

MSN/Live Messenger supports Yahoo! accounts since version 8 :)

---

