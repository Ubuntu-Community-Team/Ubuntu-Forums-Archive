---
title: "HOWTO Install M$ Office 2003 on Ubuntu!!!"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by Tahir on 2007-02-27
Hello all,

I have finally installed Microsoft Office 2003 on Ubuntu.  I have written this HOWTO so that people dont waste their time like I did going on winehq's forum and trying out different things. 

So here are fairly simple instructions:

(1) What you first must do is install wine and ies4linux on Ubuntu. After installation type "winecfg" in the command line once so that it creates your configuration files.
(2) Then install Orca on Windows (I am assuming that you haven't wiped it out yet!).
(3) Then do the following in Windows:

i.  Copy all of the contents of your Office11 CD (or DVD) to HDD.  Now you can remove the CD because it won't be needed anymore.
ii.  Find the following files that you copied to your HDD: OWC10.MSI,  OWC11.MSI and PRO11.MSI and do the following procedure with each one individually:

<procedure>
a. Open the file using Orca.
b. Choose table InstallExecuteSequence from the left.  You will then see the content of this table in front of you.  Search in "Action" column for the words "SchedSecureObjects", "ExecSecureObjects", "CreateAIInjData" and "CreateWRCDownload".  Delete all the rows containing these values.  (Only in PRO11.MSI will you find rows of the last two).
</procedure>

(4) Finally boot into Ubuntu.  I am assuming that you can access your Windows partitions from Ubuntu because this is where you copied the files from the Office installation CD to.  Now locate where the SETUP.EXE file is (its of course inside the folder that you copied the office CD files to). Then open a terminal and change to this directory (if you are using konqueror as your file explorer then just copy and paste the contents of the location bar into a terminal and type "cd " before it.  Finally type "wine SETUP.EXE".  It is recommended that you only install Word, Excel and Powerpoint.  I don't know why but that is what he said. Finished!!

If you have any questions please ask.  I am a total noob but I will try to answer your questions.

These are very simplified instructions I derived from this guide:

[http://appdb.winehq.org/appview.php?iVersionId=3214](http://appdb.winehq.org/appview.php?iVersionId=3214)

written by Nick right at the bottom.

---

### Post by Ek0nomik on 2007-02-27
So this guide requires Windows to be installed?

---

### Post by Tahir on 2007-02-27
> **Ek0nomik said:**
> So this guide requires Windows to be installed?

Sort of.  I am assuming that those who want to get Office 2003 to work on their system already have it on their Windows Partition.

One needs to run Orca to modify the MSI files and Orca does not install properly in wine.  If you click on the link in my first post, there is a small bit on running Orca in wine but it is so difficult that its not worth bothering with.  I have sort of got Orca to work but the problem is that no rows appear when you select on of the attributes.  Try it out yourself.  This way we can be certain that it does work.

---

### Post by Choad on 2007-02-27
must everyone write ms with a $ sign? thats sooo 2003

---

### Post by punx45 on 2007-02-27
> **Choad said:**
> must everyone write ms with a $ sign? thats sooo 2003

It's Office 2003.. so in this case M$ would be appropriate  :lolflag:

---

### Post by Quillz on 2007-02-27
Interesting guide, although I wouldn't go through all that trouble just to install Office 2003. I'd just use OpenOffice, since my personal needs don't extend much more than simple formatting, all of which OpenOffice can do.

---

### Post by Tahir on 2007-02-27
> **Quillz said:**
> Interesting guide, although I wouldn't go through all that trouble just to install Office 2003. I'd just use OpenOffice, since my personal needs don't extend much more than simple formatting, all of which OpenOffice can do.

Yeah thats true but sometimes you need MS Office because only that way can you be certain that the word documents you write using OpenOffice can also be viewed on MS Office.  Also for word files which are very long and use complex formatting... anyway why am I marketing M$ products to you?

---

### Post by Quillz on 2007-02-27
No, I agree... There are still times when only Word will work for me. But I run Ubuntu on a virtual machine on my iMac, so I can always fire up Word 2004, or just go to another Windows PC with Office 2003 on it.

Choice is great.

---

### Post by Tahir on 2007-02-27
> **Quillz said:**
> But I run Ubuntu on a virtual machine on my iMac

...using vmware?

> **Quillz said:**
> so I can always fire up Word 2004, or **just go to another Windows PC with Office 2003 on it.**

well, the whole point of installing office 2003 is so that you dont have to use another PC or reboot into windows.  It was the same for web developers and that is why they love the ies4linux because this way they can test their web pages without having to use another computer.

Anyway, although this is irrelevent, is there any point in using ubuntu on the iMac?  And did you buy the iMac because it looks good and is compact or are you a fan of apples?  I thought the main reason that people use ubuntu here is because windows xp sucks.

Trust me, xp gave me no end of trouble.  I had to wait such a long time for it to boot and stuff like that.  I am glad that I now have ubuntu and with MS Office installed on it!

---

### Post by Quillz on 2007-02-27
> **Tahir said:**
> ...using vmware?



well, the whole point of installing office 2003 is so that you dont have to use another PC or reboot into windows.  It was the same for web developers and that is why they love the ies4linux because this way they can test their web pages without having to use another computer.

Anyway, although this is irrelevent, is there any point in using ubuntu on the iMac?  And did you buy the iMac because it looks good and is compact or are you a fan of apples?  I thought the main reason that people use ubuntu here is because windows xp sucks.

Trust me, xp gave me no end of trouble.  I had to wait such a long time for it to boot and stuff like that.  I am glad that I now have ubuntu and with MS Office installed on it!
Well, I don't mean to get off topic here, but I bought an iMac because a) I got it extremely cheap through my college (a 55% discount, to be exact) and b) I like Mac OS X. 

As for the virtual machine, I use Parallels Desktop. One machine has Windows Vista, the other has Ubuntu 7.04 Herd 4. I generally use OS X, but I do start up Ubuntu occasionally for testing and other tasks.

I don't want to get off topic, though, so that's all I'll say here.

---

### Post by Tahir on 2007-02-27
[/QUOTE]
> **Quillz said:**
> a 55% discount, to be exact
wooooooah!!!! :)   

Which college did you go to? 

No wonder you bought it. Good luck to you anyway with ubuntu 7.04.

---

### Post by Jimbo2184 on 2007-03-24
Hi guys.

Disappointing that Microsoft Office 2003 won't work at all well (if at all?!) under Wine 0.9.33 and Ubuntu Linux 6.10 :(

I'm a uni student and unfortunately the uni do insist on us using Microsoft Office 2003 - especially for the excel/access VBA crap we have to do :( All I need is Excel and Access 2003...

Do you guys know if OpenOffice can code VBA script in the same (or similar) way that Microsoft Office 2003 does? We need to build databases so buttons in one application (say Excel) do something inside Access or vice versa.

Otherwise, it looks like I'll have to keep that spare laptop hard disk with Windoze XP lying around just to run office and nothing else :(

---

### Post by jharbert on 2007-03-27
Have you tried VMWare?  It allows you to run Windows inside of Ubuntu.  If all you need is MS Office, then it should be just what you need.

---

### Post by imariot on 2007-03-29
I use win4lin to run Office 2k3 since I need Visio and Outlook. I use StarOffice apps instead of word, excel, powerpoint, and access. It seems to work very well. 

Jimbo take a look at this in regards to openoffice and vba scripts:
[http://www.linux.com/article.pl?sid=06/11/08/1726205](http://www.linux.com/article.pl?sid=06/11/08/1726205)

---

### Post by skubisnack on 2007-05-30
Does anyone know how to get past the Activation Wizard?  I have called for an activation code, since I get an error when I try to do it online, but I can't enter the code in the wizard.  Is there somewhere in the registry that I can edit to get past this?  I can keep deleting and reinstalling, but that's gonna get old.

Thanks,
Greg

---

### Post by rovernaut on 2007-05-30
I sure it will run if you get a copy of Crossover.
 I have XP office running quite happily on feisty

---

### Post by Sethalos on 2007-05-30
You know for me the easiest way to do this is to just run VirtualBox, throw WinXp in there and install it that way. I tried going through the instructions, but as stated you can only use a few of the programs. If you need to use a Windows Program, I don't see why you wouldn't just use a virtual instance of it.

Seth

---

### Post by quinnten83 on 2007-05-30
> **imariot said:**
> I use win4lin to run Office 2k3 since I need Visio and Outlook. I use StarOffice apps instead of word, excel, powerpoint, and access. It seems to work very well. 

Jimbo take a look at this in regards to openoffice and vba scripts:
[http://www.linux.com/article.pl?sid=06/11/08/1726205](http://www.linux.com/article.pl?sid=06/11/08/1726205)

where would one get this win4lin?  I need to run visio too and there is no suitable alternative in ubuntu yet.

---

### Post by pinguin on 2007-05-31
I installed office 2003 by wine  0.9.37 i386 on Feisty i386 without particular procedure, only running wine /path/setup.exe :)
It works but there are problems with fonts (missing arial times new roman etc) :confused:
**Tahir, what about fonts whit your procedure?**

But I am not able to install it by wine  0.9.37 amd64 on Feisty amd64 :sad:

---

### Post by TravMan63 on 2007-06-15
Can you play wmv and mpg files in powerpoint with this method???
(that's the only problem I'm having ...)

I don't have windows installed on this machine, but have access to a winxp box that is networked to this one - should be easy to follow the 'how to' - 

sounds like a project for tomorrow...
TM

---- edit----
6/23/07 (+1wk)
I already had Office installed, so I did not perform the 'orca' method.
Installed IE4Linux today (had to copy files from a 98 install, and download the 249973USA8.exe and DCOM98.EXE files...)

Unfortunately, this did not correct my issue with powerpoint and inserting mpg/wmv files.

---

### Post by Gruelius on 2007-06-15
I like office 2003 more than openoffice for some reason dunno why. Running it in a VM would be a pain in the bum because of seperate clipboards, restricted to the VM window, cant  view local directory tree e.t.c.

So can you actually get it to run with most functions working or can you just install it?

---

### Post by ernstblaauw on 2007-06-17
I tried your 'howto'. However, (before and) after altering the .msi files, the installer crashes when it should start copying the files. So, I select I want a custom installation. select I only want to install Word, Excel and Powerpoint, I click next (so I see a overview of the programs I want to install), and then I click next (or finish?). Then the installer crashes.
I use Wine 0.9.38 i386 on a Kubuntu 7.04 64-bit instalaltion. Does someone know what could be wrong? Maybe I have a different installation CD, or I do not have certain 64-->32bit libs installed?
Hopefully, someone can help me.

---

### Post by Golyadkin on 2007-06-17
This seems so much trouble for just running Office. What I do is just run Windows XP in and put the Windows programs I need there. I share a folder between the virtualbox and my Ubuntu 64 bit host and everything is fine :) 

[img]http://www.android42.net/got/VirtualBox.png[/img]

---

### Post by ernstblaauw on 2007-06-17
> **Golyadkin said:**
> This seems so much trouble for just running Office. What I do is just run Windows XP in and put the Windows programs I need there. I share a folder between the virtualbox and my Ubuntu 64 bit host and everything is fine :) 
...image...

Is it possible to add a 'real' hard disk as a virtual harde drive inside Virtual Box? So you can edit your own files? That's not (easily) possible with VMware.

---

### Post by Golyadkin on 2007-06-17
Yeah, what I do is use Guest Additions in virtualbox to setup a shared folder named "Share". The folder I share is the root of my second harddrive. In virtualbox I simply open a DOS console and type:
> 
net use x: \\vboxsrv\Share

Which maps the shared harddisk to a network harddisk with driveletter X:\

Very simple, and it works like a charm.

---

### Post by ernstblaauw on 2007-06-17
> **pinguin said:**
> I installed office 2003 by wine  0.9.37 i386 on Feisty i386 without particular procedure, only running wine /path/setup.exe :)
It works but there are problems with fonts (missing arial times new roman etc) :confused:
**Tahir, what about fonts whit your procedure?**

But I am not able to install it by wine  0.9.37 amd64 on Feisty amd64 :sad:

What about wine 0.9.37 i386 on Feisty amd64?

---

### Post by daxumaming on 2007-06-17
I have OpenOffice, what more can I ask for? Office 2003 has features I don't need and will never use. Maybe advanced users need Excel, but the rest of use are content with OO.o.

---

### Post by TravMan63 on 2007-06-23
> **ernstblaauw said:**
> I tried your 'howto'. However, (before and) after altering the .msi files, the installer crashes when it should start copying the files. So, I select I want a custom installation. ...  Then the installer crashes.
I use Wine 0.9.38 i386 on a Kubuntu 7.04 64-bit instalaltion. Does someone know what could be wrong? Maybe I have a different installation CD, or I do not have certain 64-->32bit libs installed?
Hopefully, someone can help me.

I had a similar problem: Verify that 'windows 2000' is the windows version selected in winecfg
I simply installed from the cd (Xubuntu 7.04 - 32 bit) - note I have problems inserting wmv and mpg etc into powerpoint - (and can not find files with windows media player)
Other than that - Powerpoint runs well (and it's faster than Impress on this machine)

also see:
[http://ubuntuforums.org/showthread.php?t=470842](http://ubuntuforums.org/showthread.php?t=470842)

check Cookies posts on that thread...

TM

---

### Post by ernstblaauw on 2007-06-23
Also if I select Windows 2000, the installer crashes.

---

### Post by zero244 on 2007-06-23
I think dollar signs when typing M$ or Apple$ is appropriate considering the amount of money these two companies suck out of the general public.

---

### Post by HermanAB on 2007-06-23
Go to Codeweavers and download the trial version of CxOffice, install that and install MS Office.  CxOffice is a special version of Wine and it works properly.

Cheers,

Herman

---

### Post by the8thstar on 2007-06-23
> Hello all,

I have finally installed Microsoft Office 2003 on Ubuntu. I have written this HOWTO so that people dont waste their time like I did going on winehq's forum and trying out different things. 

So here are fairly simple instructions:

(1) What you first must do is install wine and ies4linux on Ubuntu. After installation type "winecfg" in the command line once so that it creates your configuration files.
(2) Then install Orca on Windows (I am assuming that you haven't wiped it out yet!).
(3) Then do the following in Windows:

i. Copy all of the contents of your Office11 CD (or DVD) to HDD. Now you can remove the CD because it won't be needed anymore.
ii. Find the following files that you copied to your HDD: OWC10.MSI, OWC11.MSI and PRO11.MSI and do the following procedure with each one individually:

<procedure>
a. Open the file using Orca.
b. Choose table InstallExecuteSequence from the left. You will then see the content of this table in front of you. Search in "Action" column for the words "SchedSecureObjects", "ExecSecureObjects", "CreateAIInjData" and "CreateWRCDownload". Delete all the rows containing these values. (Only in PRO11.MSI will you find rows of the last two).
</procedure>

(4) Finally boot into Ubuntu. I am assuming that you can access your Windows partitions from Ubuntu because this is where you copied the files from the Office installation CD to. Now locate where the SETUP.EXE file is (its of course inside the folder that you copied the office CD files to). Then open a terminal and change to this directory (if you are using konqueror as your file explorer then just copy and paste the contents of the location bar into a terminal and type "cd " before it. Finally type "wine SETUP.EXE". It is recommended that you only install Word, Excel and Powerpoint. I don't know why but that is what he said. Finished!!

If you have any questions please ask. I am a total noob but I will try to answer your questions.

These are very simplified instructions I derived from this guide:

[http://appdb.winehq.org/appview.php?iVersionId=3214](http://appdb.winehq.org/appview.php?iVersionId=3214)

written by Nick right at the bottom.

Does it work with Office 2007 too?

---

### Post by the8thstar on 2007-06-24
Hello, so no replies???

---

### Post by ranran on 2007-10-24
> **HermanAB said:**
> Go to Codeweavers and download the trial version of CxOffice, install that and install MS Office.  CxOffice is a special version of Wine and it works properly.

Cheers,

Herman

Yes, and it also costs $40....... :)

---

### Post by SunnyRabbiera on 2007-10-24
yeh but it might run better for the new user then wine...
I would suggest crossover myself.

---

### Post by akiratheoni on 2007-10-24
> **Gruelius said:**
> I like office 2003 more than openoffice for some reason dunno why. Running it in a VM would be a pain in the bum because of seperate clipboards, restricted to the VM window, cant  view local directory tree e.t.c.

So can you actually get it to run with most functions working or can you just install it?

Actually with VirtualBox I was able to share files and even share the same clipboard. Plus there's integration so I don't need to click inside the Windows window to be able to the Windows pointer; as long as you mouse over the window, it will switch to it automatically.

Plus I like the full screen option; it legitimately looks like I'm running Windows XP :P

---

### Post by Ryklou on 2008-06-21
I installed m$ office 2003 thru playonlinux.

---

