---
title: "Nvidia Driver install help."
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by Conano on 2007-03-28
Evening Folks. I'm new to ubuntu. I have a nice clean install with duel boot of windows xp pro. I am using 6.06 LTS dapper Drake release. And to tell you, Quite frankly i havent a clue what i'm doing. 

I do not understand how to install new programs. With windows it's simply click a .exe file and away we go. I'm finding this Far more complicated and almost not worth the effort. I would like to learn this operating system and learn some about linux. But i havent a clue where to start. For the moment however what i want is to know how to install the driver for my video card. I am using a 7800 GS OC Nvidia card. Without drivers i'm not getting the full potental outta my card. Or the full screen resolution which should be 1440x900. instead i'm getting 1024x768. I have looked and looked at instructions, but i dont understand those complicated commands for compiling and what not. So any help would be MOST appriciated. 

If anyone is willing to help me with this, i can check back here. or i can be contacted via yahoo messanger at [email]viktorrge@yahoo.com[/email]. 

Thanks.

---

### Post by kpkeerthi on 2007-03-28
[http://help.ubuntu.com](http://help.ubuntu.com)

Do not start to mess with your system until you finish reading Ubuntu Desktop Guide located there.

(More links in my signature. But start with the desktop guide first)

---

### Post by Conano on 2007-03-29
Ok I read the Documentation. And i actually figured out how to get my MP3 files to play using alternate programs that were in the add/remove. And i tried using Envy to install the Nvidia Driver, however this is causing issues. I dont know if envy is not compatable or not. it was usign a deb file extention. And the program installed fine. It's just that i get an error everytime i try installing the nvidia driver set they have listed in envy. 

I'm confuzzled when it comes to the nvidia driver....

---

### Post by bodhi.zazen on 2007-03-29
Error message ?

To install envy use these commands :

```
mkdir -p ~/src/envy
cd ~/src/envy
wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.1-0ubuntu3_all.deb
sudo dpkg -i envy*
sudo apt-get install -f
sudo dpkg -i envy*
sudo envy -t
```

Yes, I know sudo dpkg -i envy* is listed twice, but that is what works :p

---

### Post by Conano on 2007-03-30
Ok Bodhi i tried what you said to do and this is all the Text i input, and the OS and program responces. :(

--------------------------------------------------------------------------------------------------------------------------
dmitry@dmitry-desktop:~$ mkdir -p ~/src/envy
dmitry@dmitry-desktop:~$ cd ~/src/envy
dmitry@dmitry-desktop:~/src/envy$ wget [http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.1-0ubuntu3_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.1-0ubuntu3_all.deb)
--18:09:57--  [http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.1-0ubuntu3_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.1-0ubuntu3_all.deb)
           => `envy_0.9.1-0ubuntu3_all.deb'
Resolving albertomilone.com... 68.178.232.90
Connecting to albertomilone.com|68.178.232.90|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 333,980 (326K) [text/plain]

100%[====================================>] 333,980      321.69K/s

18:10:07 (320.89 KB/s) - `envy_0.9.1-0ubuntu3_all.deb' saved [333980/333980]

dmitry@dmitry-desktop:~/src/envy$ sudo dpkg -i envy*
Password:
(Reading database ... 83414 files and directories currently installed.)
Preparing to replace envy 0.9.1-0ubuntu3 (using envy_0.9.1-0ubuntu3_all.deb) ...Unpacking replacement envy ...
Setting up envy (0.9.1-0ubuntu3) ...
dmitry@dmitry-desktop:~/src/envy$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
dmitry@dmitry-desktop:~/src/envy$ sudo dpkg -i envy*
(Reading database ... 83414 files and directories currently installed.)
Preparing to replace envy 0.9.1-0ubuntu3 (using envy_0.9.1-0ubuntu3_all.deb) ...Unpacking replacement envy ...
Setting up envy (0.9.1-0ubuntu3) ...
dmitry@dmitry-desktop:~/src/envy$ sudo envy -t


       +-------------------------------------------------+
       |                                                 |
       |             Welcome to Envy 0.9.1               |
       |                                                 |
       |    Developed by Alberto Milone (aka tseliot)    |
       |                                                 |
       +-------------------------------------------------+


       +-----------------------------------------------------------+
       |    Envy Menu ver.0.9.1                                    |
       |                                                           |
       |    1 - Install the NVIDIA driver                          |
       |                                                           |
       |    2 - Uninstall the NVIDIA driver                        |
       |                                                           |
       |    3 - Install the ATI driver                             |
       |                                                           |
       |    4 - Uninstall the ATI driver                           |
       |                                                           |
       |    5 - Install the ATI/NVIDIA driver Manually             |
       |                                                           |
       |    6 - Clean the Installation of any Nvidia driver        |
       |                                                           |
       |    7 - Restart the Xserver                                |
       |                                                           |
       |    8 - Exit                                               |
       |                                                           |
       |    NOTE: IF THE SCREEN TURNS BLACK, PLEASE TYPE ALT+F1    |
       +-----------------------------------------------------------+
Please select one of the activities displayed above and press ENTER:

1
ENVY ERROR: Your Operative System does not seem to be supported by Envy
dmitry@dmitry-desktop:~/src/envy$

-----------------------------------------------------------------------------------------------------------------
now i'm totally lost.... perhaps i installed something badly during the OS install? dont see how though, it was practicly all auto.

---

### Post by bodhi.zazen on 2007-03-30
LOL I though that error message was just me ...

Try this version :

wget [http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.7.5-0ubuntu1_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.7.5-0ubuntu1_all.deb)

(remove / delete that version you just downloaded)

---

### Post by .oops on 2007-03-30
About installing programs and such, I suggest you read [this](http://www.cutlersoftware.com/ubuntuinstall/) article. It helped me alot. :)

---

### Post by Conano on 2007-04-08
I must be totally missing something here, cause that artical didnt really help me much. all i would like to do is downlad and install my nvidia drivers for my 7800 GS OC, But it seems thats too easy to do, instead linux has to be a pain in the butt, and make nothing simple. Sorry folks, but i've decided linux is NOT a viable operating system for me to switch to. I prefure User friendly over wasting my time trying to type in lines of code to get something to work. 

Maby one day when Linux finally settles on ONE aperating system, rather than 50 different OS's. And actually becomes User firendly then maby i'll return to take another look. Admittedly it's come far from the old mandrake that i tried about 10 years ago. But it's just not good enough. Going to look into Mac OSX10 or Keep my Windows XP.

---

### Post by bodhi.zazen on 2007-04-08
> **Conano said:**
> I must be totally missing something here, cause that artical didnt really help me much. all i would like to do is downlad and install my nvidia drivers for my 7800 GS OC, But it seems thats too easy to do, instead linux has to be a pain in the butt, and make nothing simple. Sorry folks, but i've decided linux is NOT a viable operating system for me to switch to. I prefure User friendly over wasting my time trying to type in lines of code to get something to work. 

Maby one day when Linux finally settles on ONE aperating system, rather than 50 different OS's. And actually becomes User firendly then maby i'll return to take another look. Admittedly it's come far from the old mandrake that i tried about 10 years ago. But it's just not good enough. Going to look into Mac OSX10 or Keep my Windows XP.

Well, best of luck to you. 

You are always welcome to come on back any time.

FYI, there are versions of Linux with the nvidia drivers pre-installed.

My favorite it Sabayon, although under the hood it may not be what you ar looking for as it is based on Gentoo ...

But there are others, Dream Linux comes to mind ...

You could always look here [Distrowatch](http://distrowatch.com/)

---

### Post by ayenack on 2007-04-08
The easy way to install Nvidia Linux drivers is this. Install Automatix or Automatix Bleeder. These are programs that make it easy to install extra programs. They have the Nvidia drivers ready and waiting to be downloaded and installed.

To install Automatix do this in a terminal (Applications>Accessories>Terminal).

sudo gedit /etc/apt/sources.list 

    * Add the following lines at the end of file 

## Automatix repo
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

    * Now save and close /etc/apt/sources.list and run the following commands from terminal (one by one, hitting enter after each step) 

wget [http://www.getautomatix.com/keys/automatix2.key](http://www.getautomatix.com/keys/automatix2.key)
gpg --import automatix2.key
gpg --export --armor E23C5FC3 | sudo apt-key add -

gpg --keyserver subkeys.pgp.net --recv CC919A31E23C5FC3
gpg --export --armor CC919A31E23C5FC3 | sudo apt-key add -

    * Update APT 

sudo aptitude update

    * Run the following commands to install Automatix2 

sudo aptitude install automatix2


    * Automatix2 can be started from the the Menu 

Menu -> System -> Automatix

    * Automatix2 can be run from terminal by typing the folowing 

automatix2

Best of luck. ayenack.

---

### Post by Nythain on 2007-04-08
its good to know im not the only person in the world who hasnt been able to get an automatic script or aptitude to correctly install my nvidia drivers... i found it much easier to just manually install them, and since its so easy i dont mind reinstalling them if when i do a kernel upgrade...

---

### Post by jhenager on 2007-04-08
Add/Remove
search on Nvidia
click it and go OK

Shouldn't be too hard for anyone, even a Windows user.

---

### Post by ayenack on 2007-04-08
This may not work. If it dose not try this.

In terminal type

sudo gedit /etc/apt/sources.list

This will bring up a text screen with your config change all the instances of nv to nvidia. This should make it work. I still say use Automatix.

Best of luck. ayenack.

---

### Post by jhenager on 2007-04-08
I was going to suggest automatix as well, but since it is listed in Add/Remove, that saves a few steps.

---

### Post by Conano on 2007-09-24
i decided i would give it another shot. instead of a 7800 gs oc now i'm using a 8600 GT PCIExpress 16 card. 

I tried the above menchoned things, and no dice.... still cannot get my full screen resolution for my monitor. my monitor is a samsung syncmaster 941bw thats supposed to run at 1440x900 but max i can get it to is 1024x768. Plus it's saying my video card is unknown. even thoug i have the Nvidia binary X.Org Driver installed. 

Once mor ei have spent hours trying to figure this out and once more i'm growing very frustrated. I tried downloading nvida's new drivers, but they are in a bin format which i cant seem to access or install.....

---

### Post by alienexplorers on 2007-09-24
Did you use ENVY to load your video drivers?  If so, did you remove your old drivers first.  Then you can go ahead and load the new video drivers.  You should then be able to use nvidia-settings to set up your resolution and refresh rate.  To run nvidia-settings use:
> gksudo nvidia-settings
Pick the resolution and refresh rate you want and then Apply and click to save to x configuration file.  This will create a line in your xorg.conf file that would look like so if it worked.
> Option         "metamodes" "1400x900_70 +0+0"
You may also need a modeline to force x to use the resolution you want.  A sample modeline looks like so:
>   # 1400x900 @ 70.00 Hz (GTF) hsync: 65.59 kHz; pclk: 123.31 MHz
  Modeline "1400x900_70.00"  123.31  1400 1488 1640 1880  900 901 904 937  -HSync +Vsync
This modeline should be pasted into the "MONITOR" section of xorg.conf........

---

### Post by corowakid on 2007-09-24
> **Conano said:**
> i decided i would give it another shot. instead of a 7800 gs oc now i'm using a 8600 GT PCIExpress 16 card. 

I tried the above menchoned things, and no dice.... still cannot get my full screen resolution for my monitor. my monitor is a samsung syncmaster 941bw thats supposed to run at 1440x900 but max i can get it to is 1024x768. Plus it's saying my video card is unknown. even thoug i have the Nvidia binary X.Org Driver installed. 

Once mor ei have spent hours trying to figure this out and once more i'm growing very frustrated. I tried downloading nvida's new drivers, but they are in a bin format which i cant seem to access or install.....

FWIW, I have just gone thru what you're experiencing, and I had half decided to give it all away and go back to XP - whihc I *definitely* didn't want to do.

I posted like you, and got some great responses, which at first meant nothing to me. Then I got referred to a site called:

[http://albertomilone.com/](http://albertomilone.com/)

and all things started to fall into place. First though, you've got to stop thinking in Windows speak - like you, I'm really comfortable with .exe files, and seeing things happen with really no input from me. Today I dedicated the afternoon (I'm retired, so that's not hard), locked myself away in my computer room (seeing my wife rolling her eyes when I told her I was going to get Ubuntu to work like I wanted it to), and started reading and referring to the various sections on Alberto Milone's website.

By mid-afternoon I had my nVidia graphics card installed, got my resolution of 1680x1050 as the default, edited files with his instructions (which made me read the files, and see what was going on under the hood), and then told my wife (triumphantly) "got it going, do you want a look?). She did, and said how good I was. Actually the reality was that I posted here, I got enthusiastic help from a number of knowledgable people, and great websites to go look. Now I know how to do it, and I also know more about Linux.

So I'd really recommend you visit Alberto's site, either save his pages as PDF, or perhaps print them out and have them alongside you, and get into it. Like me you're going to balls things up, and think you're not getting there, but then you'll post here and folks will give you avenues to try. 

Best of luck - don't quit - doing these exercises are great for the morale when they pay off, and as Linux continues to grow and refine, you'll be able to experience computing way beyond what you'll get from Windows, and at no cost.

Best of luck

---

### Post by Conano on 2007-09-24
Thanks Coro, i'm hoping th einformation you gave me will work. we shall see....

---

### Post by Conano on 2007-09-25
SWEET Thanks man. It worked...... Now to get down to business...... Envy worked great. 

It's jsut so confusing. cause i have read atleast 7 different ways to install nvidia drivers. Setteling on one simple one would be nice.

---

### Post by Shazaam on 2007-09-25
Conano,
Read this-
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)
and remember Linux isn't HARD, it's just DIFFERENT.

---

### Post by tsh on 2007-09-25
I have a 8600 GT card, and installed the binary drivers without too much trouble. My problem now is that whenever I reboot, I get a blank screen. Booting in recovery mode and re-installing the drivers seems to be my only route at the moment to getting X to work. I assume that the nv drivers are being loaded on boot, and failing to detect my card - where should I look to fix this?

Thanks,

Sean

---

