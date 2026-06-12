---
title: "Experiences with ubuntu. I need a little help..."
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by viriul on 2007-09-24
Hi all, 

I am a new Ubuntu user. Not that i choose to use Ubuntu but as I started a new work i was "forced" to use it. 
I don't consider myself a newbie in computers. My experience comes from the MS-DOS days so I'm not scared of a command prompt ( although i though i had passed that time lol) But i used all this years Windows, from 95 to XP.
My experiences with linux are few, i started a few years ago with a mandrake distro ( dual boot) but that didn't last long. I used also Caixa Magica 10 and 11 ( a portuguese distro) but also didn't last long and was mainly as a end user. But now I Have to learn to use ubuntu. 
At first i was a litle "scared" with all this ( i.e. the file installation is, in my opinion, not as intuitive as windows) but now i am becoming a little more comfortable. And i hope i will learn more and more as time goes.

Now for the help...
I'm having a few problems that i can't resolve myself so i am asking the community some help...
1 st - I installed a HP 2015 printer ( networked) and apparently everything is ok. I can print fine. I have just one problem. Whenever i send i print job i have to physically go to the printer and press the ready button otherwise it won't print. In windows the same printer will start printing immediately.
2 nd - If i put a .xls; .doc or .ppt file in my desktop and then try to start it, openoffice quits at start wih an error message. But the same file in a network drive ( windows 2000 ) acessed by nautilus in my PC will start just fine without any problems... 
If i start in root user i can open the file in my desktop, but i am not completely sure i just tested once.
3 rd ( and last for now ) - I am using SciTE text Editor to edit .asp files. Those files (company backoffice) are stored in the network drive. If i try to open them with left button-> Open with ... -> and choose SciTE i get an error. The only way i can open them is by opening first SciTE and them drag and drop the file or by SciTE file->Open

THis is a long post but i hope you read it all... any help you can give me i will appreciate.

Thanks

---

### Post by HereInOz on 2007-09-24
What are the error messages which you are receiving?  Also, when you attempt to open the file, are double clicking on the file, or are you opening the application and then attempting to open the file?

Post the error messages and someone may have had them previously.

---

### Post by anaconda on 2007-09-24
1st. This happened to me too. But our printer was kind enough to tell what was the problem. We use "A4-paper", but what the printer said was. "please insert Letter" (which is US standard paper size). and with ready-button it starts printing it to A4..
The solution was to change the paper type to be A4 from the printer settings..

---

### Post by viriul on 2007-09-24
Hi,

In the printer properties the paper size is A4 - plain paper, which is correct - so it doesn't seems to be it.

As for the problem in openoffice it happens when i double-click on the file that i'm trying to open. Wait, it also happens when i try to open openoffice from the aplication's menu... 
It sends a error window stating: The application cannot be started. An internal error occurred. 
It's very strange because i can open openoffice the other way...
By the way i didn't install openoffice myself. It was the standard ubuntu installation.

Thanks

---

### Post by viriul on 2007-09-24
Hi,

I have another problem, so i use this thread to post it

I had a standard monitor and my max resolution was 1024x768. 
That was ok, but now i installed a new monitor - 17 inches tft ( syncmaster 701n) and the max resolution is supposed to be 1280x1024 but i can't change it...

in the ubuntu system->preferences->screen resolution i can't see a new resolution...
I edited the xorg.conf file and added 1280x1024 modes to all the entry's. restarted but i still can't see the new resolution...

How can i make ubuntu check to see the new monitor and get the new resolution?

Thanks

---

### Post by viriul on 2007-09-24
I have managed to change the monitor resolution to 1280x1024...
I just had to restart the detection routine like in installation ( this is an example of a situation that widows does much better - lol ), but everything is fine now.

But i still need help with my openoffice problem... it's very annoying and it's harder to make any kind of work...
So if anybody can help me and explain what i have to do to make openoffice work correctly please come foward

Thanks

---

### Post by Daveth on 2007-09-24
just a thought but have you ever right clicked say a word doc, gone to properties, and selected Open with.. and then selected OpenOffice?
Will make all .docs open with OO.

---

### Post by aspen_dv on 2007-09-24
> **viriul said:**
> Hi,

In the printer properties the paper size is A4 - plain paper, which is correct - so it doesn't seems to be it.

Thanks

I have the same problem with HP Laserjet 2300d. This is how I did to get arround it:
On printer itself, change your paper selection to ANY Size. The print out may not be as correct as  you expect but this get rid off the annoying press-the-button-thing

---

### Post by viriul on 2007-09-25
Thanks for your reply's. 
I will have to check the printer manual to see how to change the paper size, but if the print out wont be correct then i better forget it. I am not the main printer user and it works correctly for the other users (windows) so i have to live with this problem. thank god the printer is only 2 2meters away and not on the other side of the corridor :)

As for the OOffice problem, that is very important to me. Let me explain again...
OO was installed as basic ubuntu installation. No other changes were made.
I can open .doc .xls, etc documents with OO, provided they are in a Windows network drive, accessed from my pc by a mounted drive.
The SAME file copied to my desktop (or vice-versa) won't open. Whether i try to open it by double click or by pressing right MB and choose - > open with openoffice.org word processor  or open width -> and then choose openoffice word processor.
Also, if i go to applications menu->office->openoffice.org... it wont open.
The error it says is always the same:
The application cannot be started. An internal error occurred.

So anybody knows why openoffice is working strangely? 

Thanks

---

### Post by viriul on 2007-09-28
Hi,

It seems that i am the only one with this problem...

It's strange that no one as heard of this... 

it looks like my only choice is to reinstall OpenOffice, but i don't know if even then it will work.

---

### Post by hyper_ch on 2007-09-28
Just on a sidenote:
"the file installation is, in my opinion, not as intuitive as windows" --> why is it intuitive in windows to go online, search for a program, download it, run the .exe or .msi file?

I think it's more intuitiv to run the "Add/Remove" or "Synaptic" or "Adept" program, search for programs I want, tick them and then press "install"

---

### Post by viriul on 2007-09-28
> **hyper_ch said:**
> Just on a sidenote:
"the file installation is, in my opinion, not as intuitive as windows" --> why is it intuitive in windows to go online, search for a program, download it, run the .exe or .msi file?

I think it's more intuitiv to run the "Add/Remove" or "Synaptic" or "Adept" program, search for programs I want, tick them and then press "install"

Thats a personal question. For me i prefer to download a file, unpack it, then run .EXE and CHOOSE what i want to install and where. If i know of a new version i can do the same again, no problems.

In linux i have to use ( as far as i know): 

using sypnatic (don't know of the others) "hope" that the file i want is there. search it in a few thousands packages. and if i find it, select it to be installed. if everything is ok it will install (don't know where - no user information) but sometimes there are a few packages that need to be installed also... which may be a problem if i want to uninstall. If there is a new version i must wait until it goes into the sypnatic manager if at all...

i can also download the file and unpack it... but then to run it... i need to know what the file to run for my distro is. and the write one of many commands with lots of options to install it and hope i didn't do anything wrong.

In MY opinion windows does this much better. i hope this is an area where linux will improve.

As for my Openoffice problem i am getting desperate... i uninstalled OO and installed again and the same thing happens...

I learned that if i try to run any OO application in terminal with the command: sudo oowriter i.e. i can, but if i try just oowriter it stops with the errors...

[Java framework] Error in function createUserSettingsDocument (elements.cxx).jav
aldx failed!
[Java framework] Error in function createUserSettingsDocument (elements.cxx).

and stops with the previous error i mentioned, in a window.

I hope this information can help anyone pinpoint the problem better. Thanks anyway

---

### Post by hyper_ch on 2007-09-28
seems you don't have java installed... or you could deactivate java in OOo.

The repos way is much superior from the M$ way. No need to check if there are viruses... all in one place for update... when you re-setup your computer you just let a script run that fetches and installs all software you want... and: even my mom can use it ;)

---

### Post by viriul on 2007-09-28
> **hyper_ch said:**
> seems you don't have java installed... or you could deactivate java in OOo.

The repos way is much superior from the M$ way. No need to check if there are viruses... all in one place for update... when you re-setup your computer you just let a script run that fetches and installs all software you want... and: even my mom can use it ;)

It works... Thank you, thank you, thank you.

I never though of checking Java because i could run OO in root mode, and i was convinced i had java installed before. But as i was so desperate i though it wouldn't hurt to check java or try to update it if possible. I was surprised not to see any java installed. but now everything works ok. Thank you again.

I agree with you on the virus, although if you are careful in windows you don't get a virus (I don't use antivirus in my windows system and never had any) but i am more used to the windows way (for example: there is a new version of OO - 2.3 and in sypnatic i can only find 2.2). but maybe with time i can get more used to the linux way :)

Ok, I think this thread may be closed, my main problem is solved.

---

### Post by offroad64 on 2007-09-28
I had the same problem with my HP 2605. By default the printer selects tray 1. On my printer this was the single sheet feed I fixed it by selecting tray 2 in the printer defaults.
Jeff

---

### Post by hyper_ch on 2007-09-28
the newest version isn't always the best... Ubuntu has a new version coming out every 6month and so will the packages updated ;)

---

