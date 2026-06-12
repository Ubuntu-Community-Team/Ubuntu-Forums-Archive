---
title: "How To Install Dreamweaver 8 and Fireworks 8 on Ubuntu Feisty 7.04:"
date: 2007-06-24
forum: Art &amp; Design
---

### Post by toddbmobile on 2007-06-24
[B]
Step 1[/B]
Remove any existing installs of &#8220;wine.&#8221;
[B]
Step 2[/B]
Delete the &#8220;.wine&#8221; folder in you home holder (remember it is hidden) and its contents. (regretfully this would remove any preexisting windows program installs) 
[B]
Step 3[/B]
Goto Winehq for the latest version of &#8220;wine.&#8221; (must be 0.9.39 or newer)
[http://www.winehq.org/](http://www.winehq.org/) and download Wine 0.9.39 or newer.
[B]
Step 4[/B]
Once at the site select &#8220;Binary packages for various distributions will be available from:&#8221;

  [http://www.winehq.org/site/download](http://www.winehq.org/site/download)

**Step 5**
Then select Ubuntu link.
[B]
Step 6[/B]
Next, open a terminal window. Then add the repository's key to your system's list of trusted APT keys by [B]copying and pasting the following code below at the prompt &#8220;$.&#8221;

wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

Step 7[/B]
Next, add the repository to your system's list of APT sources. Do this by selecting copy and then paste the below code in the terminal prompt &#8220;$.&#8221;
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list](http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/winehq.list
[B]
Step 8[/B]
sudo apt-get update      (**updates the above repository on you system**)
[B]
Step 9[/B]
sudo apt-get install wine (**Installs &#8220;wine.&#8221; Select &#8220;y or yes&#8221; if asked to do so.**)
[B]
Step 10 [/B]
(The remaining steps and paths will change based on wither you are installing Dreamweaver or Fireworks)

Also in a terminal window type the code below at the prompt &#8220;$&#8221;:

cd /cdrom
cd fscommand (or which folder your  Dreamweaver or Fireworks EXEs are in)

**Step 11**
(Type the &#8220;wine&#8221; command for which ever of the two  Dreamweaver or Fireworks you are installing at the terminal prompt &#8220;$&#8221;)

wine dreamweaver.exe

or

wine fireworks.exe

**Step 12** 
[I][B](VERY IMPORTANT STEP &#8211; Untick/Uncheck for both  Dreamweaver or Fireworks all the associated files types, don't worry you still can use these programs to open supported file types.)
[/B][/I]
**Step 13**
When you have finished installing both programs you can create a desktop icon/link by right clicking the desktop, and left clicking &#8220;Create Launcher.&#8221; In the command field enter the below code changing out your home folder name &#8220;**yournamehere**.&#8221;

**Dreamweaver:**
env WINEPREFIX="/home/**yournamehere**/.wine" wine "C:\Program Files\Macromedia\Dreamweaver 8\dreamweaver.exe"
[B]
Fireworks:[/B]
env WINEPREFIX="/home/**yournamehere**/.wine" wine "C:\Program Files\Macromedia\Fireworks 8\fireworks.exe"

Both work like a charm. I hope this helps someone. Feel free to contact me for assistance.
[B]
5/20/2010 UPDATE
This works fine under 10.04 lucid lynx LTS.[/B]

---

### Post by fromgi on 2007-06-26
THANK YOU!  Worked like a charm!

I've been trying to install DW and FW for at least a month without much success.

I'm trying to setup a primary browser within DW, but not having much success location it.  Can you help me find it within Ubuntu?  The only browser I have is Firefox supplied with 7.04.

Thanks,
Larry

---

### Post by toddbmobile on 2007-06-29
Glad you liked the post, and that it worked for you. As for as the browser issue, I did not set one myself. I will play with it today, and post back what I find out. I had just been openeing my html from the browser itself. What browser do you want to use?

---

### Post by fromgi on 2007-06-29
I use the Firefox version installed with Ubuntu.   I hope can use this version, but afraid we might have to install IE.  Thanks for your time!

---

### Post by Glen Darby on 2007-06-30
Hi,

I have gone through the routine of placing both Dreamweaver and Fireworks on my system using wine, however I can not seem to get the launcher working.

I put dreamweaver and Fireworks on through root and have tried to set up the Launcher in my normal account in ubuntu and was wondering if that was the problem and how to get over that problem.

Regards.
Glen.

---

### Post by Glen Darby on 2007-07-01
Hi,

No Worries! Found my error, all working realy well, ta!

Glen.

---

### Post by chrisf79 on 2007-07-01
I am trying to install Dreamweaver 8 from the install CD and in my fscommand directory, I just have a dw_client_installer.exe.  This is what I get when I try to run it:

chris@desktop:/cdrom/fscommand$ wine dw_client_installer.exe 
wine: could not load L"D:\\fscommand\\dw_client_installer.exe": Module not found

I've copied and pasted your commands exactly how they are but it isn't quite working.  Any advice would be greatly appreciated!

---

### Post by sunyata on 2007-07-04
Hi,
I'm running Ubuntu Studio (Feisty Dawn). When running Wine, I get this.
wineserver: could not save registry branch to /home/lars/.wine/user.reg : Permission denied

I suppose I need to be root to run Wine. I don't have a root pwd, never was asked to enter root pwd at installation. Are you supposed to be able to log in as root  in Ubuntu Studio?

Best regards

Lars

---

### Post by REDISISTone.nl on 2007-07-04
Good tuturial! It works...:p

---

### Post by turezky on 2007-07-05
> **sunyata said:**
> Hi,
I'm running Ubuntu Studio (Feisty Dawn). When running Wine, I get this.
wineserver: could not save registry branch to /home/lars/.wine/user.reg : Permission denied

I suppose I need to be root to run Wine. I don't have a root pwd, never was asked to enter root pwd at installation. Are you supposed to be able to log in as root  in Ubuntu Studio?

Best regards

Lars
Your own password is the passwd for root. Try "sudo su **yourpassword**". Then you'll have the root privileges!

---

### Post by oxalá on 2007-07-06
> **chrisf79 said:**
> I am trying to install Dreamweaver 8 from the install CD and in my fscommand directory, I just have a dw_client_installer.exe.  This is what I get when I try to run it:

chris@desktop:/cdrom/fscommand$ wine dw_client_installer.exe 
wine: could not load L"D:\\fscommand\\dw_client_installer.exe": Module not found

I've copied and pasted your commands exactly how they are but it isn't quite working.  Any advice would be greatly appreciated!

try *wine DW_Client_Installer.exe*
evidently capitalization matters (i.e. the exact filename) matters.

---

### Post by des4ij on 2007-07-06
Hey you dont actually have to do all that... if you get the portable version of those software sunning on windows, then wine should run them perfectly fine... even photoshop 8 (CS) but photoshop requires one registry edit in wine...

---

### Post by bgarrant on 2007-07-07
I have dw8 installed and it works well.  Only issue so far is some pages show greyed out until I click another page.  For example, I click FILE, NEW and I briefly see list of page types and then box is full grey color.  If I click on TEMPLATES tab and then back toGENERAL I can see them all as normal.  ANy idea why pages are loading in gray>

---

### Post by sunyata on 2007-07-09
> **turezky said:**
> Your own password is the passwd for root. Try "sudo su **yourpassword**". Then you'll have the root privileges!

i'm not sure I got it right.  When I do "sudo su Mypassword", I get "unknown id: Mypassword"
Did you mean: "sudo su Myusername"?
Well this is what happens when I try Macromedia in wine

lars@lars:/media/sda1/Program/Macromedia$ wine Dreamweaver.exe
wine: could not load L"c:\\windows\\system32\\Dreamweaver.exe": Module not found
lars@lars:/media/sda1/Program/Macromedia$ wineserver: could not save registry branch to /home/lars/.wine/system.reg : Permission denied
wineserver: could not save registry branch to /home/lars/.wine/userdef.reg : Permission denied
wineserver: could not save registry branch to /home/lars/.wine/user.reg : Permission denied

Regards

Lars

---

### Post by bgarrant on 2007-07-10
> **bgarrant said:**
> I have dw8 installed and it works well.  Only issue so far is some pages show greyed out until I click another page.  For example, I click FILE, NEW and I briefly see list of page types and then box is full grey color.  If I click on TEMPLATES tab and then back toGENERAL I can see them all as normal.  ANy idea why pages are loading in gray>

ANyone know how to fix this strange condition?  Does Studio MX work any better than verison 8?

---

### Post by toddbmobile on 2007-07-15
chrisf79, sorry you are having trouble. There is a chance that based on the disto of the Macromedia CD you have that the folders that contain the .exe may be different than what I posted here. For example I know there are student, professional, and trial versions of Studio 8. Also when installing something the programs if you cant just "wine dreamweaver.exe" try "sudo wine dreamweaver.exe:, but you should NOT have to do that. Make sure youe are following directiions to the "T".

---

### Post by toddbmobile on 2007-07-15
REDISISTone.nl, glad it worked out for you.

---

### Post by moody1371 on 2007-08-01
Hi, 
I have followed these instructions and all worked fine to the point of starting Dreamweaver. 
The window for the activation/trials opens, I choose trial (for the moment) and then.. nothing appears. 
Fireworks opens and can be used normally. 
I wonder what happens and how it can be repaired. 

Thanks

---

### Post by toddbmobile on 2007-08-02
I wanted to add to the post that FLASH from Studio 8 will also install successfully using the above steps.

---

### Post by toddbmobile on 2007-08-02
As  for as the greyed out tabs, I too get the same issue you have. Currently I have been doing what you do. I tick another tab and come back and it shows up fine. As for as Dreamweaver choosing trial option I have not done that because I have a key I activated mine, I am not sure if that makes a difference or not. Did you install Fireworks as trial too?

---

### Post by por100pre1 on 2007-08-02
Nice tutorial. I think this should either be included in the [Tutorial and Tips]("http://ubuntuforums.org/forumdisplay.php?f=100") or be given a sticky. :)

---

### Post by scorpiox on 2007-08-03
Ok, followed the steps to the letter, i think. Although, i installed WINE from the repository, will that make a difference?
The terminal showed a bunch of code, but as soon as the PC got to begining the install, the progress just Stopped. Nothing is happening at all. Any suggestions??
THANKS!

---

### Post by scorpiox on 2007-08-03
I am indeed stupid :P
I got it working, after realising that i wasnt using the most upto date version of WINE - for some reason it installed an old one... All sorted now, you SAVED my skin, i need DW for web design work :P

THANKYOU THANKYOU THANKYOU!

---

### Post by moody1371 on 2007-08-03
Hi, thanks for your answer.
Yes I installed Fireworks 8 also as trial and it worked fine. 
Now I have tried to do all over again, cancel .wine uninstall wine and restart all the procedure but all goes the same. 
Also with reinstalling Ubuntu!!

---

### Post by KilianValkhof on 2007-08-06
quick question, i have dreamweaver running perfectly on ubuntu through wine now, but now my home folder is filled with .asi files. is there a way to hide/store these files in a different place? cheers!

---

### Post by eldersoares on 2007-08-09
Thank You Very Much!!!!!!!!

---

### Post by lyceum on 2007-08-10
This is what I have been looking for! Thank you, Thank you!!! 

:popcorn:

---

### Post by lyceum on 2007-08-11
david@lyceum:~$ wine "/media/cdrom0/accessibility/install flash 8.exe"
wine: could not load L"Z:\\media\\cdrom0\\accessibility\\install flash 8.exe": Module not found
david@lyceum:~$ wine "/media/cdrom0/accessibility/install dreamweaver 8.exe"
wine: could not load L"Z:\\media\\cdrom0\\accessibility\\install dreamweaver 8.exe": Module not found

What am I doing wrong? I do not use wine much, is it not reading my CD player?

---

### Post by KilianValkhof on 2007-08-12
you can use the graphical interface as well, just right click the .exe and select "open with wine" :)

---

### Post by shadows123 on 2007-08-19
lol...
i was trying to install dreamweaver cs 3...


when i wined it it said :
This software can not be installed because it requires windows xp, service pack 2 or later. Please upgrade or adjust ur system to meet these minimum requirements and restart the installer later


any idea??
Thanks a lot..

---

### Post by llamakc on 2007-08-19
Same thing happened here: asks for WXP SP2.

---

### Post by toddbmobile on 2007-08-19
shadows123, snds like wine is not installed correctly. You are running the version stated in the tutorial or newer correct?

---

### Post by mjmcdonald21 on 2007-08-22
I followed the tutorial exactly but still get the following error.

```

fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls"

```

When I run this...

```

wine "C:\Program Files\Macromedia\Fireworks MX 2004\fireworks.exe"

```

Ideas?  Thanks.

---

### Post by juiced on 2008-01-15
I've got a little question.
Was trying to istall fireworks CS3 through wine, but got an Jscript error.
Anyone know how to slove this?

Thx in advance

---

### Post by faical117 on 2008-01-17
THANK YOU ! working very well :guitar:

---

### Post by ade_kusniawan on 2008-03-11
Yes..... It's Work!
Thanks


Let get Party with DW:guitar:

---

### Post by anselm1109 on 2008-03-15
How to install fireworks 8 (or dreamwever 8 I presume) from the Studio 8 CD in Ubuntu

Solves the problem of getting a "Module not found" error from wine which apparently means that the file is not executable by the current user. Hence the chmod command in the instructions.

Disclaimer: I'm using the Alpha Version of Hardy Heron, but this should work with anything.
I'm also running wine version 0.9.57 which is just the default Hardy Version.

**Step 1:** make a directory in your home folder called "studio8"

**Step 2:** Next open a terminal and run the following commands:
* note that the sudo command will ask you for your password. supply it when prompted*
```

sudo cp -r /cdrom/* ~/studio8/
sudo chmod -R 777 ~/studio8
wine ~/studio8/fscommand/fw_client_installer.exe

```

**Step 3: **Follow the instructions and you should be good to go.

---

### Post by Ryadt on 2008-07-17
Works like a charm..
thx

---

### Post by tommytomato on 2009-07-18
Any of you guys got MySQL running with Dreamweaver MX

I use Ubuntu 9.04 with Wine, I've installed Dreamweaver MX OK, but no matter what I tried I cant get it to make a database connection because I get Access denied  Huh

I've created the database, added a user and password to the database in question.

another fault is when testing the URL for localhost when defining a site, I get Access to Z:\var\www\temp.html was denied

I have apache2 installed so the path would be ```
/var/www
```
I also have MySQL running, able to use with webmin and phpmyadmin

this allso happens when using CrossOver

Any one at all know any thing about it, I can't seem too find much using google, I've read alot to NO fix sofar, posted a bug about it too

TT

---

### Post by bhencetotozo on 2010-02-13
[http://www.youtube.com/watch?v=NLSeFyN023M]("http://www.youtube.com/watch?v=NLSeFyN023M")


I was also having Module Load problem...
It wouldnt work for me from the terminal...

I tryed wine Fireworks8-en.exe .... it didnt work. gave me module error...
I clicked won Applications>>wine>>uninstall software

I installed it from there..

The link about will send you to a Video where I installed it sucessfully.
Hope this helps.
Good luck.

---

### Post by Merk42 on 2010-02-13
Considering the last post was 7 months, and then a year before that, and this thread is about **7.04**, I'm pretty sure it can be closed.

---

