---
title: "HOWTO: Install Microsft Office 11 (2003) the right way"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by kernel tom on 2008-01-23
Hey all, I've noticed a lot of posts dealing wiht MSOFFICE that just don't work for me.  at all...

And i know there are a lot of Oo fans out there so please, don't post ur disgust for M$ on this page....

ASSUMPTIONS I'M MAKING 
-Using Ubuntu 7.04 (notes in there for 7.10)
-All of your downloads save to the Desktop
-You are connected to the internet

First off.  Get Wine using this method if you want it to be included anytime you do an update (this is what I did)
by the way all O's are o's not zeros

```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -

```
(this adds the key to your apt-list so it's an approved resource)
```

sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list -O /etc/apt/sources.list.d/winehq.list
```
NOTE: this is for Ubuntu distro's 7.04 you would replace that with your distro i.e. 7.10 would use gusty.list
```

sudo apt-get update
sudo apt-get install wine

```

Alternatively, you can go to this website and download the most recent, appropriate deb file and double click it to install it once its downloaded.
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)
but then it will not be included in any future updates on your machine

Now to set up Wine
```
winecfg
```
this will open your wine configuration window after creating some file paths.
Under the Applications tab, set Windows Version to Windows XP
Under the Libraries tab, add "riched20" and "riched32" from the New override for library menu
Select "riched20" from the existing overrides, and click Edit. Select Native(Windows)
Do the same for "riched32"
Click Apply, Click OK
Download the "riched30.exe" file here:
[http://media.codeweavers.com/pub/crossover/office/support/richedit30.exe](http://media.codeweavers.com/pub/crossover/office/support/richedit30.exe)
```
wine ~/Desktop/richedit30.exe
```
Agree to the licensing and whatnot to install it
Download "msxml3.msi" from here:
[http://www.microsoft.com/downloads/details.aspx?FamilyID=28494391-052b-42ff-9674-f752bdca9582&DisplayLang=en#filelist](http://www.microsoft.com/downloads/details.aspx?FamilyID=28494391-052b-42ff-9674-f752bdca9582&DisplayLang=en#filelist)
```
wine msiexec /i ~/Desktop/msxml3.msi
```
Agree to the licensing and whatnot here again
```
winecfg
```
In the Libraries tab, add "msxml3" from the dropdown list and Add it
Select "msxml3", Click Edit, and set it to Native(Windows) as well
Click Apply, Click OK

Now install Microsoft Office 11 (2003) as you would on any other Windows OS, be it from CD, Shared Network, whatever.  I did it from the CD and it worked fine, which I got free.

Your Applications will most likely be under Applications>Other (for feisty)
This seems to install all the shortcuts, even to programs you didn't select from the install.
To remove them
```
cd .local/share/applications/wine/Programs/Microsoft\ Office/
rm name_of_application
```

And there will no longer be a shortcut for that application in your menu

I was able to do both a Microsoft Update, and Register my version of office when and how "windows" asked me to.

Regards,
Tom

---

### Post by rhc on 2008-01-23
Long live AbiWord. : )

---

### Post by kernel tom on 2008-01-23
> **rhc said:**
> Long live AbiWord. : )

Yes I do love AbiWord :)

...but I do still get some formatting errors when I get .doc's from ppl and open them.  And when I have to edit the file and send it back, the formatting looks like crap on there end sometimes too.

---

### Post by rhc on 2008-01-23
> AbiWord is good,AbiWord is the way...

Yes maybe you are right.
Although,i won't use Ms Office anyway, this topic will help many people.
Thanks.

(The quote is from the best video game ever made,Sanitarium. :))

---

### Post by ragadanga63 on 2008-01-24
I have tons of MS Office files when I converted my biz to Ubuntu. No way those files will be opened properly by OO and Abiword.   New files though are created by OO. 

Please indicate what version of wine is needed here as I read somewhere that it will only work on 9.5 or newer version (I'm on 9.53).

Thanks for this how-to kernel tom.  Really appreciate it.

BTW.  When I fire up the Equation Editor, it says feature needs to be installed when in fact I've installed it.

---

### Post by kernel tom on 2008-01-24
I've been using wine 9.53 as well... the most recent version of wine is usually the way to go... I think 9.49 and higher work.

As with the Equation editor, I believe thats why this received a "Gold" rating instead of a "Platinum" rating on Wine's AppDB site.

-kt

---

### Post by chewit on 2008-01-24
Great HOWTO, but I'm sorry. Linux is all about OpenSource. We should all be supporting opensource projects. I think it would be best if we encoraged new linux users (people I me) to live Windows behind and try out other great open source office packs.

There are many great office packs:

Open Office (my favourite)
Gnome Office
KOffice

---

### Post by newbeeman on 2008-01-24
> **chewit said:**
> Great HOWTO, but I'm sorry. Linux is all about OpenSource. We should all be supporting opensource projects. I think it would be best if we encoraged new linux users (people I me) to live Windows behind and try out other great open source office packs.
There are many great office packs:
Open Office (my favourite)
Gnome Office
KOffice

I totally agree, but at the same time it's not possible to give up years of work and have to reformat tons of docs etc. 
It's also impossible to edit videos or audio as well as can be done in Adobe.
So I have to stick to a dual boot system, as much as I would like to dump Windoze, it's just not possible.

---

### Post by emarkd on 2008-01-24
Not to mention having to interact with other people/organizations.  I use Linux and have managed to convert several people over the years, but there are still lots of people and businesses that don't and I still have to interact with them.  The problem goes much deeper than philosophical reasonings.  There are systemic problems that have not yet been overcome and unfortunately we Linuxers have to bend a little to get by in the current computing environment.  I don't like it any more than you do and we have to continue to **work together** to make a difference.

To the OP:  Nice tutorial.  I'm sure it will help many people who need it.

---

### Post by fourscore on 2008-01-25
The install  went fine, but when i launch  Excel or Word  , the application laucnches and I  get the following error window  :
"Microsoft Office Word has not been installed for the current user. Please run setup to install the current application".
When i click on  OK,  the  application closes.

Pls help

---

### Post by Theros123 on 2008-01-25
Weird.. I followed exactly what you said and the it started installing... However, after it started to do that (after I choose what programs to install) the installer disappeared and never came back?  Everything else worked up to that point?

---

### Post by kernel tom on 2008-01-25
> **fourscore said:**
> The install  went fine, but when i launch  Excel or Word  , the application laucnches and I  get the following error window  :
"Microsoft Office Word has not been installed for the current user. Please run setup to install the current application".
When i click on  OK,  the  application closes.

Pls help

When you installed MSOffice did you change the values of the fields when it prompted you for your name, initials, and organization?  Fill out somethign for ur name and intials, organization can be blank... also enter that same information when u start up word or excel when prompted

-kt

---

### Post by kernel tom on 2008-01-25
> **chewit said:**
> Great HOWTO, but I'm sorry. Linux is all about OpenSource. We should all be supporting opensource projects. I think it would be best if we encoraged new linux users (people I me) to live Windows behind and try out other great open source office packs.

There are many great office packs:

Open Office (my favourite)
Gnome Office
KOffice

I'm pretty sure Wine is opensource... but i understand your point

---

### Post by kernel tom on 2008-01-25
> **Theros123 said:**
> Weird.. I followed exactly what you said and the it started installing... However, after it started to do that (after I choose what programs to install) the installer disappeared and never came back?  Everything else worked up to that point?

How are you installing... CD or otherway?

What do you mean the "installer" disappears?  do you mean Setup.exe?

-kt

---

### Post by Theros123 on 2008-01-25
Okay... I had the wrong cd,  Now, after using the right one I've got it installed.  My only problem is with the extra icons, however I can't seem to get rid of them.

I'm cding to that directory you stated and then running

rm MSACCESS.EXE (that's what the Run Application menu told me what Access' name was)...  that didn't work, and I've tried doing Microsoft\ Office\ Access\ 2003, but that doesn't do it either...  Can you show me the correct command to do this?

Thanks

---

### Post by kernel tom on 2008-01-25
> **Theros123 said:**
> Okay... I had the wrong cd,  Now, after using the right one I've got it installed.  My only problem is with the extra icons, however I can't seem to get rid of them.

I'm cding to that directory you stated and then running

rm MSACCESS.EXE (that's what the Run Application menu told me what Access' name was)...  that didn't work, and I've tried doing Microsoft\ Office\ Access\ 2003, but that doesn't do it either...  Can you show me the correct command to do this?

Thanks

What folders are located in this path?
~/.local/share/applications/wine/Programs/Microsoft\ Office

-kt

---

### Post by fourscore on 2008-01-26
> **kernel tom said:**
> When you installed MSOffice did you change the values of the fields when it prompted you for your name, initials, and organization?  Fill out somethign for ur name and intials, organization can be blank... also enter that same information when u start up word or excel when prompted

-kt

I did enter, but the appln - word, excel  throw up the error msg and close immdtly.  Tried reinstalling  two different sources  but no luck.    Is there any other setting change required.

---

### Post by Crazy Jesus on 2008-01-26
> **fourscore said:**
> I did enter, but the appln - word, excel  throw up the error msg and close immdtly.  Tried reinstalling  two different sources  but no luck.    Is there any other setting change required.

Yeah I have the exact same problem. Does anyone know a solution? :(

---

### Post by fourscore on 2008-01-26
Solved the problem by :
- installing  wine ver 0.9.53  from  [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)
- reinstalling  msoffice2003SP3
Also installed the MScompatibility pack for 2007 successfully.  However the SP1 for the compatibility pack could not install.

Also refer to [http://wine-review.blogspot.com/2008/01/running-ms-office-2003-under-linux-with.html](http://wine-review.blogspot.com/2008/01/running-ms-office-2003-under-linux-with.html)
for some detailed instructions

---

### Post by fourscore on 2008-01-26
> **fourscore said:**
> 
............
Also installed the MScompatibility pack for 2007 successfully.  However the SP1 for the compatibility pack could not install.
............


correction -  the compatibility pack installs  but am unable to save int he new formats.

---

### Post by kernel tom on 2008-01-28
yeah i can't get that working either.

---

### Post by lift28 on 2008-01-31
do the above adding the repos  then repair option in setup :)

---

### Post by GayRockies on 2008-02-03
Hello,

Thanks for this thread.  It seems that I did get Office to install OKAY with this method.  However, I'm not able to get Outlook to work.

Word works, but for 99.9% of tasks, OpenOffice.org's word processor does as competent a job, and it works faster.  In fact, I use OpenOffice.org in Windows about as much as I use MS Office.

However, I have an absolutely massive email file, many of which are still yet to be dealt with.  If I can't access this in Linux (it's an office .pst file), then I'm going to have to move getting Windows to run right on this machine again up the list fast.

I really don't want to migrate to another program - at least not now, because I've yet to find another email program that can not only handle my email (they all do that well), but also sync my calendars with a portable device.  (ie: iPod)  If there is something out there that can do this that I'm not aware of, please, please let me know.  If not, could I get some hints on getting Outlook to run in Ubuntu?

Thanks,

M.J.

---

### Post by Whiffle on 2008-02-03
I'm pretty sure outlook does not work on wine, or has ever actually. 

I hate to say it, but I installed office 2003 with the 9.54 version of wine without making any changes to wine whatsoever.  It worked perfectly.  I may go back and add those dll's though just to be safe.

If you get the error that says "such and such is not installed for this user," run the setup program again and tell it to repair/reinstall, it should fix it.

---

### Post by swordphsh on 2008-02-08
I got it all installed and somewhat working. I also installed service pack 3, but when i start word, excel, or powerpoint i get a prompt to enter my serial number. Upon entering a correct serial, the program exits and reprompts every time i open it back up. When i first installed it, the installer has the serial number already entered via the setup.ini file, so it should not be asking me for it again anway.
Thanks in advance for the help.

---

### Post by sondad on 2008-02-11
thank you*** kernel tom***  for your wonderful post. it worked 100% but I faced a little problem !!! wine wouldn't support Arabic language and all my effort to make office support Arabic with wine failed> do you have any suggestions?

---

### Post by kernel tom on 2008-02-14
not off the top of my head, but i'll look into it and post if i find anything

-kt

---

### Post by CrazyArcher on 2008-02-14
Does Office 2007 work through Wine?

---

### Post by kernel tom on 2008-02-14
not yet

go to wine's appdb to get a good list of what has been tested to work with wine...

[http://appdb.winehq.org/](http://appdb.winehq.org/)

-kt

---

### Post by jimcameron on 2008-02-18
Hi Kernel Tom
I've done up tot he installing of the MSOffice
I have a CD i was just wondering if you could tell me where to go from here? Sorry i'm new to Linux and am jut getting to grips with it. 
Is it somehting to do with terminal?

Cheers jim

---

### Post by kernel tom on 2008-02-18
if you've gone through all the steps, insert the CD in your CD drive.

It should auto mount to the desktop, double click on it to open it up,,, find SETUP.EXE and double click that.

It should launch microsofts installer and you go thru the installation like you normally would on a windows machine

-kt

---

### Post by jacrider on 2008-03-06
kernel tom:  Many thanks for this HOWTO.

I had a couple of issues that I will outline, maybe to help others experiencing the same problems.

First, perhaps some of my issues were from installing  (my owned, legal copy) Office 2003 Professional as compared to Office 2003.

Initially, I couldn't get the installer to run.  I was receiving an error that the "Installation Source was Corrupted."  Some googling brought me to a site that said the msxml3.dll driver needed to be set to "native then builtin" as opposed to "native".  This worked and installation proceeded.

After installation, I could run Excel (all I need from MS Office) but it was flaky.  For example, trying to open a file would cause a crash.  Again more googling led me to a site that said I needed to set riched32.dll to native for excel.exe, winword.exe and pwerpoint.exe.  You do this in winecfg by selecting the application from the main tab, then going to the libraries and setting riched32.dll.

After this, I am now running smoothly.  

Some of the sites/sources that helped along the way in addition to this post:

[http://blog.napalmpiri.com/quickanddirtyhowtooffice2003wine](http://blog.napalmpiri.com/quickanddirtyhowtooffice2003wine)
[http://wine-review.blogspot.com/2008/01/running-ms-office-2003-under-linux-with.html](http://wine-review.blogspot.com/2008/01/running-ms-office-2003-under-linux-with.html)
[http://frankscorner.org/index.php?p=office2003](http://frankscorner.org/index.php?p=office2003)

---

### Post by kernel tom on 2008-03-06
Great looks with those websites...

I thought I put in my howto updating msmxl3 and riched32 but in any case it's good that you found you're way around it.

I had the exact same problems the first time i ran thru the install, but fixed it the same way you did

-kt

---

### Post by nanog on 2008-03-06
IMO, open office is far from a viable replacement for office. 

Impress crashes routinely when running large presentations (>20 megs) and has trouble working on professional grade projectors.

Calc still lacks basic error and regression functionality. Gnumeric and Office have had this for years. Also, calc has deeply flawed statistical algorithms.

Write lacks meaningful bibliographic support and is incapable of opening many word documents. Abiword does a far better job of opening word documents. 


I used to file bug reports at openoffice.org but the lack of progress turned me off a long time ago. I use Gnumeric, LyX, MySQL-phpmyadmin, <b>AND M$ OFFICE</b> because these applications actually work!

---

### Post by FatEddie on 2008-03-14
I've followed this how to and read throught the threadbut my Wine doesn't work at all, not for any windows install because it wo just says "cannot run this type of file .EXE" so there's obviously something fundamental wrong. Wine appears alright in the Applications menu. I uninstalled it and tried again but the same thing happened. Any ideas, cos I really needed Excel for something (complex spreadsheet won't run in Oo) and I don't want to have to set up a Dual Boot syatem?

---

### Post by kernel tom on 2008-03-16
how did you go about installing wine? And have you set up the wine config correctly? (As explained in my steps)

-kt

---

### Post by wordchisler on 2008-03-18
> **Whiffle said:**
> I'm pretty sure outlook does not work on wine, or has ever actually. 

I hate to say it, but I installed office 2003 with the 9.54 version of wine without making any changes to wine whatsoever.  It worked perfectly.  I may go back and add those dll's though just to be safe.

If you get the error that says "such and such is not installed for this user," run the setup program again and tell it to repair/reinstall, it should fix it.

[http://wine-review.blogspot.com/2008/01/running-ms-office-2003-under-linux-with.html](http://wine-review.blogspot.com/2008/01/running-ms-office-2003-under-linux-with.html)
I suppose if OL will run on Linux and Wine 0.9.52, it will run with ubuntu and Wine. 
Since I'm new to Ubuntu I am having some trouble following the instructions, but I hope I can figure it out.

---

### Post by wordchisler on 2008-03-18
The blog instructions are very similar except the following which comes, in his instructions, just before install:
> Now install the richedit30 update, make sure you go to ~/.wine/drive_c/windows/system32 and rename richedit20.dll, richedit32.dll and msxml3.dll to *.bak or the updates wont work properly. I am not sure I understand this step. Am I to rename all the .dll files to .bak files? Will that work?

> tom@tom:~$ wine richedit30.exe
fixme:midi:OSS_MidiInit Synthesizer supports MIDI in. Not yet supported.
tom@tom:~$not sure what that step is supposed to accomplish.

So far I have wine installed, but I am trying to decide whether to rename the .dlls or not.
During installation wine reported:
[INDENT]wine: creating configuration directory '/home/mrp/.wine'...
Could not load Mozilla. HTML rendering will be disabled.
[/INDENT]
Is there a way to renable if I need it?

---

### Post by kernel tom on 2008-03-19
have you followed my instructions as I have written them?

The reason I ask is that everyone tells you different ways to do things, and that my way should work for *most* Ubuntu users.  There should be no renaming of files or anything else that I have not stated in my original post.

I can't help you follow someone else's instructions, but I can help you if you are running into problems with my instructions.

-kt

---

### Post by wordchisler on 2008-03-19
I followed your instructions, glancing at the other set as I went along. 

After more errors, and no OL icon, I tried Crossover (trial version). OL 2003 suddenly appeared but I was faced with OL 2003 cannot start. Reinstalled with Crossover, and it worked like a charm, but I could not install the Agendus Outlook plug-in.

Have you been able to install Outlook 2003 with Wine (free)?
If so, do you know if it is possible to install plug-ins for Outlook?
Is it possible to install ActiveSync?

If so, I will try again, even if I need to reinstall Wine, because I would like to have OL in a window in Ubuntu. My other option is to try Virtualbox.

---

### Post by kernel tom on 2008-03-20
Nope, I haven't had luck with OL, even back when I had windows i used thunderbird.

I'm not sure that OL will ever work under wine, and I don't know why.  But there has to be a work around somewhere, so keep on looking I suppose.

kt

---

### Post by wordchisler on 2008-03-21
I tried Virtualbox and now have OL2003 with Agendus plug-in and ActiveSync to T-Mobile Dash running. Interestingly it seems to run faster than my dualboot. 

Setup was simple, but I complicated it by making two errors: 
- I used OSE instead of the Personal Edition. The latter is needed for USB support. (Messy fix).
- I enabled USB 2.0 which caused my Dash to be invisible to ActiveSync. (Easy fix).

OL2003 support in Wine would be nice, but I don't have enough knowledge of Ubuntu, let alone Wine to try to deal with it for the present. Oh well. Atleast I have Agendus(OL2003) & ActiveSync running in Ubuntu. :D

---

### Post by FatEddie on 2008-03-22
> **kernel tom said:**
> how did you go about installing wine? And have you set up the wine config correctly? (As explained in my steps)

-kt

Yes, I followed it all as described, I dont think it was a problem with your instructions, others have had it work fine for them. Probably just my setup. I did upgrade ordinary Ubuntu gutsy to Ubuntu Studio about a month ago, maybe that did something. Anyway, I've set up a dual boot system now to run XP and Excel and ebay turbo lister as I had some spare time after my router failed and I was waiting for a replacement, just a shame I couldn' get wine to work.

---

### Post by pingwing on 2008-04-02
Hi tom! I'm trying to get XL 2003 to run on wine in Gutsy, 'cos I've got a lot of VBA code.I followed your original post with no problem up to here:

Download the "riched30.exe" file here:
[http://media.codeweavers.com/pub/crossover/office/support/richedit30.exe](http://media.codeweavers.com/pub/crossover/office/support/richedit30.exe)
```
wine ~/Desktop/richedit30.exe
```
Agree to the licensing and whatnot to install it

at this point I get this:

~$ wine ~/Desktop/richedit30.exe
fixme:spoolsv:serv_main (0 (nil))
err:service:service_get_status service protocol error - failed to read pipe r = 0  count = 0!
fixme:setupapi:SetupDefaultQueueCallbackW notification 262144 params 32f728,0
err:setupapi:SetupDefaultQueueCallbackW copy error 0 L"C:\\windows\\temp\\IXP000.TMP\\riched20.dll" -> L"c:\\windows\\system32\\riched20.dll"
fixme:setupapi:SetupDefaultQueueCallbackW notification 262144 params 32f728,0
err:setupapi:SetupDefaultQueueCallbackW copy error 0 L"C:\\windows\\temp\\IXP000.TMP\\riched32.dll" -> L"c:\\windows\\system32\\riched32.dll"

and richedit30 doesn't appear in the dropdown.:confused:

I threw in the MSO CD anyway - the splash appears, but nothing happens when I click install.
I'm starting to think that either my box (HP Pavilion dv6000) or my head has got a bit or two missing. Could anyone pls help me out with the first?:rolleyes:

---

### Post by Tryfon on 2008-04-10
I'm trying to install the Office 2003 Service Packs but keep getting the message "The update can't be applied!". What must I do?

---

### Post by fourscore on 2008-04-10
> **Tryfon said:**
> I'm trying to install the Office 2003 Service Packs but keep getting the message "The update can't be applied!". What must I do?

You should first  integrate/slipstream  the SP3 into Office2003 and then install.    The how-to for slipstreaming can be found here - [http://www.howto-outlook.com/otherprograms/slipstreamo2k3sp.htm](http://www.howto-outlook.com/otherprograms/slipstreamo2k3sp.htm)

---

### Post by fourscore on 2008-04-13
Is it possible to  associate the  DOC XLS PPT files with   MSOffice (running in wine )  so that  when we double click they open the respective MSOffice app instead of  OpenOffice ?

---

### Post by jhorto1 on 2008-04-18
> **FatEddie said:**
> I've followed this how to and read throught the threadbut my Wine doesn't work at all, not for any windows install because it wo just says "cannot run this type of file .EXE" so there's obviously something fundamental wrong. Wine appears alright in the Applications menu. I uninstalled it and tried again but the same thing happened. Any ideas, cos I really needed Excel for something (complex spreadsheet won't run in Oo) and I don't want to have to set up a Dual Boot syatem?
Exact same thing here. I followed the instructions to the letter and got the same message when I click setup. 
The difference is that I don't see wine in any group under the Applications menu. I'm pretty sure it installed ok, because all of the command line commands worked.
I got through all the instructions without a hitch until I got to the part where I actually install Office from CD. When I click the setup file, I get that error. It's almost as if I never installed wine at all.

Any ideas? I'd really like to get wine working so that my wife can use excel in ubuntu. I'm try ing to convince her that linux is good, but first her outlook web mail won't work in firefox and now she can't use excel.

I'd really appreciate some expert advice. 

Thank you.

---

### Post by jhorto1 on 2008-04-18
Maybe I need to run setup.exe from the command line with wine? 

SOmething like wine setup.exe maybe?

What do you guys think. From everyone else's posts it just sounds like they clicked setup.exe and it ran just fine.

---

### Post by jhorto1 on 2008-04-19
Ok, that worked. I right clicked the setup.exe and said custom command. I then entered 'wine' and clicked ok.
It went through the setup and asked me for the product key. Took that.

Unfortunately, it then gave me the error that the source files were corrupted. I think I saw a post about that earlier in this same thread. Time to investigate.

---

### Post by jhorto1 on 2008-04-19
> **jacrider said:**
> kernel tom:  Many thanks for this HOWTO.

I had a couple of issues that I will outline, maybe to help others experiencing the same problems.

First, perhaps some of my issues were from installing  (my owned, legal copy) Office 2003 Professional as compared to Office 2003.

Initially, I couldn't get the installer to run.  I was receiving an error that the "Installation Source was Corrupted."  Some googling brought me to a site that said the msxml3.dll driver needed to be set to "native then builtin" as opposed to "native".  This worked and installation proceeded.

After installation, I could run Excel (all I need from MS Office) but it was flaky.  For example, trying to open a file would cause a crash.  Again more googling led me to a site that said I needed to set riched32.dll to native for excel.exe, winword.exe and pwerpoint.exe.  You do this in winecfg by selecting the application from the main tab, then going to the libraries and setting riched32.dll.

After this, I am now running smoothly.  

Some of the sites/sources that helped along the way in addition to this post:

[http://blog.napalmpiri.com/quickanddirtyhowtooffice2003wine](http://blog.napalmpiri.com/quickanddirtyhowtooffice2003wine)
[http://wine-review.blogspot.com/2008/01/running-ms-office-2003-under-linux-with.html](http://wine-review.blogspot.com/2008/01/running-ms-office-2003-under-linux-with.html)
[http://frankscorner.org/index.php?p=office2003](http://frankscorner.org/index.php?p=office2003)

Thanks. I'll give that a shot.

---

