---
title: "what is WINE?"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by dhani99 on 2007-06-23
So, 
i needed to install shockwave player as i wanted to play games!!
but there is no such shockwave for linux so 
came to know about wine and came to know that it allows Windows-based programs from within Linux. THATS REALLY COOL, so i can deal with exe files from within linux, 
so before i proceed anything any instruction!!!
because i'm new to ubuntu...

---

### Post by Crafty Kisses on 2007-06-23
> **dhani99 said:**
> So, 
i needed to install shockwave player as i wanted to play games!!
but there is no such shockwave for linux so 
came to know about wine and came to know that it allows Windows-based programs from within Linux. THATS REALLY COOL, so i can deal with exe files from within linux, 
so before i proceed anything any instruction!!!
because i'm new to ubuntu...

Wine is basically a Windows emulator, it can run a lot of Windows programs, not all though. Hopefully though Wine will mature so it can run mostly all Windows programs.

---

### Post by rabideau on 2007-06-23
I think you'd be much better off using VirtualBox or VMware.  They allow you ti run a full blown Windoze in a box... Wine does not run everything and for games might be less than perfect.

---

### Post by dhani99 on 2007-06-23
so how do i install that??

---

### Post by Crafty Kisses on 2007-06-23
> **dhani99 said:**
> so how do i install that??

You can try:
```
sudo apt-get install wine
```

---

### Post by dhani99 on 2007-06-23
I don't play games at all.. 
So most important for me is to install some softwares....

---

### Post by Crafty Kisses on 2007-06-23
> **rabideau said:**
> I think you'd be much better off using VirtualBox or VMware.  They allow you ti run a full blown Windoze in a box... Wine does not run everything and for games might be less than perfect.

Those are really good too, it just depends what you need to do, I really like Wine though.

---

### Post by Crafty Kisses on 2007-06-23
> **dhani99 said:**
> I don't play games at all.. 
So most important for me is to install some softwares....

Then you'd probably want wine.

---

### Post by dhani99 on 2007-06-23
then wat do i do??

---

### Post by dhani99 on 2007-06-23
installation is in progress, 
i mean i'm done..

---

### Post by Crafty Kisses on 2007-06-23
> **dhani99 said:**
> installation is in progress, 
i mean i'm done..

Congratulations! :p

---

### Post by raul_ on 2007-06-23
**W**ine **I**s **N**ot an **E**mulator

that's what the name stands for ;)

---

### Post by dhani99 on 2007-06-23
> **Codename said:**
> Congratulations! :p

now what do i do??

---

### Post by Crafty Kisses on 2007-06-23
> **dhani99 said:**
> now what do i do??

Download the program you want to use, then right click on the .exe after you have downloaded it and there should be a option called "Run in Wine" select that one.

---

### Post by Crafty Kisses on 2007-06-23
> **raul_ said:**
> **W**ine **I**s **N**ot an **E**mulator

that's what the name stands for ;)

Funniest post all day. ;)

---

### Post by rabideau on 2007-06-23
vmware comes with Ubuntu and can be installed with synaptic (I think).  VirtualBox.org (my favorite) is to be found at: [http://virtualbox.org](http://virtualbox.org))  There are a lot of ubuntu users for both.

---

### Post by dhani99 on 2007-06-23
> **Codename said:**
> Download the program you want to use, then right click on the .exe after you have downloaded it and there should be a option called "Run in Wine" select that one.

I dont see any option says run in wine when i click right button

---

### Post by dhani99 on 2007-06-23
do i need to restart?

---

### Post by dhani99 on 2007-06-23
Still, I restarted my computer and reinstalled it but i dont see that option run in wine

---

### Post by Crafty Kisses on 2007-06-23
> **dhani99 said:**
> Still, I restarted my computer and reinstalled it but i dont see that option run in wine

DId you download the file you wanted to use in Wine.

---

### Post by Crafty Kisses on 2007-06-23
> **dhani99 said:**
> Still, I restarted my computer and reinstalled it but i dont see that option run in wine

Here's the screenshot:
[IMG]http://i81.photobucket.com/albums/j216/codenamexiii/Screenshot-11.png[/IMG]

---

### Post by insane_alien on 2007-06-23
have you configured wine yet?

if not run this in terminal:

```
winecfg
```

---

### Post by dhani99 on 2007-06-23
yes i did!!

---

### Post by dhani99 on 2007-06-23
but didn't config it..

---

### Post by dhani99 on 2007-06-23
what to do in config, 
i chose for windows xp

---

### Post by Crafty Kisses on 2007-06-23
> **dhani99 said:**
> what to do in config, 
i chose for windows xp

Did you see my screenshot?

---

### Post by dhani99 on 2007-06-23
yesss, 
but i dont see that option while i press right click...

---

### Post by dhani99 on 2007-06-23
my screenshot

---

### Post by Crafty Kisses on 2007-06-23
> **dhani99 said:**
> my screenshot

Hmmm, you should install a program called "AutoMatix" it installs "Wine" for you and it configures it too.

[www.getautomatix.com](www.getautomatix.com)

---

### Post by raul_ on 2007-06-23
what about choosing "open with another application" and then in the "use custom command" field, type wine

---

### Post by dhani99 on 2007-06-23
so do i uninstall that wine 1st??

---

### Post by Crafty Kisses on 2007-06-23
> **dhani99 said:**
> so do i uninstall that wine 1st??

Sure.

---

### Post by dhani99 on 2007-06-23
hey fren can u give to a download link??
i downloaded from this link, is it okay???
[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

---

### Post by Crafty Kisses on 2007-06-23
> **dhani99 said:**
> hey fren can u give to a download link??
i downloaded from this link, is it okay???
[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

What version of Ubuntu do you have?

---

### Post by dhani99 on 2007-06-23
and i saw that it did not install any program like wine!!

---

### Post by dhani99 on 2007-06-23
7.04

---

### Post by Crafty Kisses on 2007-06-23
> **dhani99 said:**
> and i saw that it did not install any program like wine!!

No go into terminal and type:
```
automatix2
```
So it opens Automatix, then when Automatix opens go to "Virtualization" and the check "Wine" then click Start and then you should be good.

---

### Post by Crafty Kisses on 2007-06-23
> **dhani99 said:**
> 7.04

Then download this one:
[http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/automatix2_1.1-4.7-7.04feisty_i386.deb]("http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/automatix2_1.1-4.7-7.04feisty_i386.deb")

---

### Post by dhani99 on 2007-06-23
i have downloaded which u suggested!!!

---

### Post by Crafty Kisses on 2007-06-23
> **dhani99 said:**
> i have downloaded which u suggested!!!

Then open Automatix.

---

### Post by dhani99 on 2007-06-23
si now i'm installing IIIT man..

---

### Post by Crafty Kisses on 2007-06-23
> **dhani99 said:**
> si now i'm installing IIIT man..
You're installing Automatix, or Wine with Automatix?

---

### Post by dhani99 on 2007-06-23
wine with automix and it's done! 
now it takes me to winecfg 
i don't have any idea ehat to do!!

---

### Post by Crafty Kisses on 2007-06-23
> **dhani99 said:**
> wine with automix and it's done! 
now it takes me to winecfg 
i don't have any idea ehat to do!!

Choose what version you want, then after that, it should do the rest for you.

---

### Post by UK-Wobbie on 2007-06-23
> **dhani99 said:**
> hey fren can u give to a download link??
i downloaded from this link, is it okay???
[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

If you like wine! Go to [http://www.winehq.org/site/download](http://www.winehq.org/site/download) and download the ubuntu deb. file :D
Click on the deb. file on your desktop  and it will open a window manu :p Click on install and put your password in!!! DONE

Reboot the pc! And for playing a game of a cd! Put your cd in the cd/dvd drive and yet it load, Open the cd drive folder! 
You will see a file named install,
Open it and it will load wine! If not right click on the install file and click on wine! That will make it load!
Install it as a windows game :p

If you need to unstall a game! You can unstall it from the game cd, By going to unstall or go to the wine start manu on the top left! Or go to \home\your user name\desktop\.wine\programes\ And then your game file look for unstall!!


If you like a more easyway on doing this unstall thing get winexs! You can download it from here [http://tsx.nl/index.php?p=winexs](http://tsx.nl/index.php?p=winexs) 
When you are on the site click on download the top one!

Yet it download to your desktop and click on it! It do not need to be installed :D
You can install or unstall and make your wine window in a tiny size!




What you was doing be for is not use for a new be on ubuntu! 

That file you download will go over the code you put in be for!
When done reboot your pc :)

I hope this will help you ;)

---

### Post by dhani99 on 2007-06-23
do i restart my pc?
bcaz still i don't see that option!!

---

### Post by Crafty Kisses on 2007-06-23
> **dhani99 said:**
> do i restart my pc?
bcaz still i don't see that option!!

Yeah go ahead and restart.

---

### Post by dhani99 on 2007-06-23
NOw i dooo

---

### Post by UK-Wobbie on 2007-06-23
> **dhani99 said:**
> do i restart my pc?
bcaz still i don't see that option!!

What have you installed? wine from the deb. file for ubuntu? 
If it says same version it means that it is installed! And now you can reboot :D

---

### Post by Crafty Kisses on 2007-06-23
> **dhani99 said:**
> NOw i dooo

Does it work?

---

### Post by dhani99 on 2007-06-23
YAAA, THankssss VERY MUCHHH 
IT HAS TO WORK NOWW> 
thanksss very much

---

### Post by UK-Wobbie on 2007-06-23
Hey  
 Codename do you no what winex3 is and will it work on ubuntu?:)

---

### Post by Crafty Kisses on 2007-06-23
> **dhani99 said:**
> YAAA, THankssss VERY MUCHHH 
IT HAS TO WORK NOWW> 
thanksss very much

No problem man anytime. For UK, I'm not sure, you should try installing it. I'm sure it wont hurt any.

---

### Post by dhani99 on 2007-06-23
yooo, i installed yahoo messenger and trying to install msn where do i find them after installation 
because i dont see them on desktop.

---

### Post by Crafty Kisses on 2007-06-23
> **dhani99 said:**
> yooo, i installed yahoo messenger and trying to install msn where do i find them after installation 
because i dont see them on desktop.
Possibly your home directory. I'm not sure where you have them go.

By the way, there is a MSN client for Linux it's called aMSN.
```
sudo apt-get install aMSN
```

---

### Post by UK-Wobbie on 2007-06-23
> **dhani99 said:**
> yooo, i installed yahoo messenger and trying to install msn where do i find them after installation 
because i dont see them on desktop.

You can put msn on wine like winamp or doom!:D
But in msn you have to do something in the file codeing to yet it download or something
Have a look here 
[http://www.winehq.org/site/download](http://www.winehq.org/site/download)

---

### Post by UK-Wobbie on 2007-06-23
> **Codename said:**
> Possibly your home directory. I'm not sure where you have them go.

By the way, there is a MSN client for Linux it's called aMSN.
```
sudo apt-get install aMSN
```

Amsn is COOL :D

---

### Post by dhani99 on 2007-06-23
it is installed in C:/program files 
but i checked in home folder not there

---

### Post by Crafty Kisses on 2007-06-23
> **dhani99 said:**
> it is installed in C:/program files 
but i checked in home folder not there

Are you trying to access it through Wine?

---

### Post by dhani99 on 2007-06-23
actually I didn't like it...

---

### Post by UK-Wobbie on 2007-06-23
> **dhani99 said:**
> it is installed in C:/program files 
but i checked in home folder not there

Amsn is not a wine tool! It is a linux self file tool :D
Look in Internet

---

### Post by dhani99 on 2007-06-23
I don't have any idea abt that 
what i know is just i installed them...

---

### Post by dhani99 on 2007-06-23
i have removed that aMSN application =...................................

---

### Post by UK-Wobbie on 2007-06-23
> **dhani99 said:**
> I don't have any idea abt that 
what i know is just i installed them...

[http://www.amsn-project.net/](http://www.amsn-project.net/) here the Amsn website! You can get the Ubuntu deb file from there,
And plugings:)

If Amsn is installed look in Internet on the left side of the screen at the top in the manu list! You will see Internaet then in it Amsn

---

### Post by dhani99 on 2007-06-23
> **dhani99 said:**
> it is installed in C:/program files 
but i checked in home folder not there
so i'm talking about the application which i installed, yahoo and msn exe files......
i installed them through wine so how do i access them?????

---

### Post by UK-Wobbie on 2007-06-23
> **dhani99 said:**
> so i'm talking about the application which i installed, yahoo and msn exe files......
i installed them through wine so how do i access them?????

yahoo and msn .exe? in wine? That will not work only if you no what you are doing and if you no how to do it lol :)

You can use Skype , Amsn , Xchat, And so on in ubuntu
[http://www.skype.com/intl/en-gb/](http://www.skype.com/intl/en-gb/)

---

### Post by Justin125 on 2007-06-23
> **dhani99 said:**
> so i'm talking about the application which i installed, yahoo and msn exe files......
i installed them through wine so how do i access them?????


I would recommend trying Gaim/Pidgen for a replacement of msn and yahoo which is in Ubuntu by default instead.

---

### Post by dhani99 on 2007-06-23
[QUOTE=UK-Wobbie;2900787]yahoo and msn .exe? in wine? That will not work only if you no what you are doing and if you no how to do it lol :)

yooo need help...

---

### Post by dhani99 on 2007-06-23
but it does not have facility of voice chat...........
and i came to know that in my msn contacts i'm not able to see them...

---

### Post by UK-Wobbie on 2007-06-23
> **dhani99 said:**
> [QUOTE=UK-Wobbie;2900787]yahoo and msn .exe? in wine? That will not work only if you no what you are doing and if you no how to do it lol :)

yooo need help...

And how do i need help? :D Am not the one installing msn.exe in wine here lmfao

If you do wanna have a go on installing msn 6.2 or 7.0 in wine you can! But it's not easy

Look here [http://wiki.winehq.org/MSN_Messenger_webcam_support?highlight=%28msn%29](http://wiki.winehq.org/MSN_Messenger_webcam_support?highlight=%28msn%29)

---

### Post by dhani99 on 2007-06-23
Ookay

---

### Post by The Wisedude on 2007-06-23
> **dhani99 said:**
> my screenshot

Open the terminal, Ill use an installer for example.

First you have to naviagte to the folder its in. Ill use my home folder so I will type

  cd /home/USERNAME/Everything/

Then I'd be in that directory, so now ill type

  wine installer.exe

You get it now :P ?

---

### Post by loell on 2007-06-23
since yahoo messenger in wine will never work.

and if you want yahoo voice, try 

[URL="http://ubuntuforums.org/showthread.php?t=414121&highlight=gtalk2voip"]  	   	
HOWTO: Voice call Yahoo Messenger using Ekiga and gtalk2voip service.[/URL]

this is by far the only closest path to achieve voice call in yahoo in linux ,

msn voice is also doable with this service.  

or install [http://www.gizmoproject.com/download.php]("http://www.gizmoproject.com/download.php")

it uses the same service to call  Yahoo, MSN / WLM users.

---

### Post by Enverex on 2007-06-24
Please don't use the Automatix version of Wine, ALWAYS use the version of Wine from the WineHQ site, there is a walkthrough and packages for Ubuntu on there.

Also Automatix DOES NOT install and configure Wine automatically. Wine's configure files are stored under ~/.wine which Apt will never touch. Configuration is always done by the user.

---

### Post by dhani99 on 2007-06-24
> **Enverex said:**
> Please don't use the Automatix version of Wine, ALWAYS use the version of Wine from the WineHQ site, there is a walkthrough and packages for Ubuntu on there.

Also Automatix DOES NOT install and configure Wine automatically. Wine's configure files are stored under ~/.wine which Apt will never touch. Configuration is always done by the user.

.SOOO 

HOW DO I REMOVE AUTOMIX???
and when i installe dwine through add-remove i was not able to see that option when i click right button.............

---

### Post by cmnorton on 2007-06-25
I have installed WINE. What is a good test to see that WINE installed correctly? Should I bring notepad over from my windows workstation? Is this as simple as bringing over the EXE and any dependent DLLs, or is there something more I have to do?

Thanks
cmn

---

### Post by Enverex on 2007-06-25
Just do "winecfg" to set Wine up, do "wine notepad" to see Windows notepad, etc. If both those work then at least the base of Wine works.

---

### Post by cmnorton on 2007-06-26
winecfg works fine.
I get these messages trying to run notepad (two different ways).
What should I look at next?

tnx
cmn

cnorton@linux-testU:~$ wine notepad
err:module:load_builtin_dll failed to load .so lib for builtin L"notepad.exe": /usr/bin/../lib/wine/notepad.exe.so: invalid ELF header
wine: could not load L"C:\\windows\\notepad.exe": Procedure not found
cnorton@linux-testU:~$ wine "c:\windows\notepad.exe"
err:module:load_builtin_dll failed to load .so lib for builtin L"notepad.exe": /usr/bin/../lib/wine/notepad.exe.so: invalid ELF header
wine: could not load L"C:\\windows\\notepad.exe": Procedure not found
cnorton@linux-testU:~$

---

### Post by Enverex on 2007-06-26
How did you install Wine? Did you add the WineHQ repo then install the package from that?

---

### Post by cmnorton on 2007-06-26
I did not install that way. I'll go try that.

---

### Post by cmnorton on 2007-06-26
It turns out I did install it the way that wineHQ recommended. On saving the new application, if I use global settings, notepad works. If I save it out as Windows XP, things don't work. I'm not sure why I have to save out as global settings, but it gives me some more to learn.

Thanks.
cmn

---

### Post by cmnorton on 2007-06-26
Thanks for the pointer. Using the WineHQ instructions, it turned out I had installed Wine correctly before, but I removed and then re-installed it from the command line. I need to read more about how winecfg works. 

Basically, if I add notepad.exe as an application, using either the w2k or xp settings, and then save to global settings everything works. It was saving to Windows XP settings that caused those errors.

---

