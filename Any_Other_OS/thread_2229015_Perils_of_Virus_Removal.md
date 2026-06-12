---
title: "Perils of Virus Removal"
date: 2014-06-10
forum: Any Other OS
---

### Post by Jonathan_Wright on 2014-06-10
Hey everyone, I have been trying to remove a virus on a friends computer for a while and I am really running out of options.  I don't know what to do anymore, and reformatting is not an option.  My friends computer has Windows 7 on it, and is infected with this strange rootkit / boot virus that as soon as you boot into the login, it says something about homeland security and how I need to pay a fine through moneypack.

So after making a ubuntu live CD, I have tried the following

-Avast.  This let me scan the windows install, delete some files, but most are "password protected," and it wont let me even read the files in there to scan them
-Hitman pro.  This program requires internet to run, and there are some wonky guides on how to get it to work, via settings or other things and I never got it to work.  It bypassed the virus's boot, but other than that it does nothing, because it cannot scan without the internet.
-Avira.  I tried this but it gave the classed "failed to selfcheck" error, and it wont get past that.

I have been on these boards for years.  I actually re-registered because it seems there is a master account we need to have to post on these boards anymore.  I am in need of assistance.  I will take any suggestions on how to remove this virus.  Thanks in advance.

---

### Post by QIII on 2014-06-10
Buy a new disk, flash the BIOS and restore your friend's file from backups.  

They were keeping backups, right?  

No?  Unfortunate.  This little gem has already encrypted whatever files it wants and unless the NSA has an interest in being nice enough to spend the next 5 years cracking the encryption or your friend pays the ransom, the game is already well over and the fans have left the stadium.

Bad news, I'm afraid.

---

### Post by WogBoy on 2014-06-10
>  it says something about homeland security and how I need to pay a fine through moneypack.

Thats Ransomware.
[https://en.wikipedia.org/wiki/Ransomware_%28malware%29](https://en.wikipedia.org/wiki/Ransomware_%28malware%29)

Go to bleeping computer ( Windows infection only) and follow the instructions. A Trained Malware Removal Team Member will help you with the clean up. You will need to join, Then post about your problem , A copy n paste of what you posted here should be fine, for now.

[http://www.bleepingcomputer.com/forums/t/182397/am-i-infected-what-do-i-do-how-do-i-get-help-who-is-helping-me/](http://www.bleepingcomputer.com/forums/t/182397/am-i-infected-what-do-i-do-how-do-i-get-help-who-is-helping-me/)

>                      Buy a new disk, flash the BIOS and restore your friend's file from backups.  
You do not need to do that.

You may also want to read this.
[http://www.bleepingcomputer.com/virus-removal/remove-ice-cyber-crime-center-ransomware](http://www.bleepingcomputer.com/virus-removal/remove-ice-cyber-crime-center-ransomware)

---

### Post by cariboo on 2014-06-10
Jailed accidental double post.

---

### Post by WogBoy on 2014-06-10
sorry admin.

PS.
I guess it was ok to post those links? Some forums get a bit jumpy about that.

---

### Post by CharlesA on 2014-06-10
IMHO but even if you are able to remove the randsomware, the machine should never be trusted unless you wipe it and reinstall.

The same thing applies if a Linux box is owned.

---

### Post by QIII on 2014-06-10
The OP is welcome to try, of course.  It is certainly possible to get lucky with year-old information when dealing with these things.  There may be some random older versions out there.  But since about mid-2013 the trend is towards encryption, with even this one having encryption variants.

In any case, the general wisdom with a ransomware rootkit is "Nuke from orbit, restore from backup."

Hopefully you are right and the OP gets lucky.

---

### Post by LastDino on 2014-06-10
If I was you, I would still flash the BIOS and buy a new disk.

---

### Post by WogBoy on 2014-06-11
With all due respect. Yes lets scrap the entire pc for something that hardly rates a mention on Malware Forums Removal anymore.

> The OP is welcome to try, of course.  It is certainly possible to get  lucky with year-old information when dealing with these things.

Its an old infection.

At the end of the day it's up to the OP.

---

### Post by Jonathan_Wright on 2014-06-11
Thank you all for the hastey responses.  I had another question: Should I reformat the USBs that I put into that laptop?  I mean I am even afraid to put these things in my machine after they have been in that laptop.

> **WogBoy said:**
> Thats Ransomware.
[https://en.wikipedia.org/wiki/Ransomware_%28malware%29](https://en.wikipedia.org/wiki/Ransomware_%28malware%29)

Go to bleeping computer ( Windows infection only) and follow the instructions. A Trained Malware Removal Team Member will help you with the clean up. You will need to join, Then post about your problem , A copy n paste of what you posted here should be fine, for now.

[http://www.bleepingcomputer.com/forums/t/182397/am-i-infected-what-do-i-do-how-do-i-get-help-who-is-helping-me/](http://www.bleepingcomputer.com/forums/t/182397/am-i-infected-what-do-i-do-how-do-i-get-help-who-is-helping-me/)


You do not need to do that.

You may also want to read this.
[http://www.bleepingcomputer.com/virus-removal/remove-ice-cyber-crime-center-ransomware](http://www.bleepingcomputer.com/virus-removal/remove-ice-cyber-crime-center-ransomware)

Going to give this a try.  I just registered there. On another note I am trying clamscan to see if that works.  It's scanning right now.  I just think wiping, reformatting and flashing the bios is just a novice way of dealing with the problem.  To my understanding, there are some viruses out there that can live through doing that.  I am just trying to figure out all the things I need to do in order to get it resolved *without* a reformat.

---

### Post by Jonathan_Wright on 2014-06-11
[Here]("http://www.bleepingcomputer.com/virus-removal/remove-homeland-security-ransomware") is the exact guide I am going to be following after searching their forums.  I will post the results of that soon.

The "Homeland Security Ransomware."

---

### Post by coffeecat on 2014-06-11
> **Jonathan_Wright said:**
> I have been on these boards for years.  I actually re-registered because it seems there is a master account we need to have to post on these boards anymore.

Although OT for this particular thread, just for your information. I don't know what you mean by master account, but if you want to get back into your previous forum account, start a thread in the [Resolution Centre]("http://ubuntuforums.org/forumdisplay.php?f=123") and one of us will help you. Please read this sticky first:

[http://ubuntuforums.org/showthread.php?t=2164369](http://ubuntuforums.org/showthread.php?t=2164369)

---

### Post by jon43 on 2014-06-11
Definitely need to nuke from outerspace and start again. 

You can't trust any system that's been pwned, and this system definitely has.

---

### Post by Jonathan_Wright on 2014-06-11
As an update I fixed my issue by using an ethernet cord to get the internet to work, and doing so made HitmanPro work.  It's always something simple isn't it?

After getting Hitman to work I installed malwarebyes and cleaned everything else.  After that I installed all the out of date drivers and updated windows and everything seems to be working swimmingly now.


> **jon43 said:**
> Definitely need to nuke from outerspace and start again. 

You can't trust any system that's been pwned, and this system definitely has.

Who says pwned anymore?  There isn't really ever a case where that needs to be done.

> **coffeecat said:**
> Although OT for this particular thread, just  for your information. I don't know what you mean by master account, but  if you want to get back into your previous forum account, start a thread  in the [Resolution Centre]("http://ubuntuforums.org/forumdisplay.php?f=123") and one of us will help you. Please read this sticky first:

[http://ubuntuforums.org/showthread.php?t=2164369](http://ubuntuforums.org/showthread.php?t=2164369)

I'll check that out.  In the past I had always used a ubuntu or linux live cd to remove windows viruses because it seemed to be the easiest way.  For some reason virses are so advanced now that I couldn't figure out why avast through ubuntu couldn't scan the files.  I still don't know.  The clamscan didn't work either.  I don't have any of the log files either to post so I don't think that's going to help me or anyone else really.

On another note, I ordered a couple laptops for my wife and I so we can use them for school.  I am looking forward to wiping that laptop and throwing ubuntu on there. :)

---

### Post by Chayak on 2014-06-11
> **Jonathan_Wright said:**
> 

Who says pwned anymore?  There isn't really ever a case where that needs to be done.



I wouldn't be so sure about that.  Is that computer used for anything sensitive such as banking and online shopping?  I have a few polymorphic malware samples that won't get a single detection on virustotal.  I use to reverse engineer malware for the government, then as a contractor, and then for a major telecommunications company.  If a system has been infected the experts will wipe and reinstall.  Then again we do tend to be a paranoid lot.  You get that way after seeing malware that changes itself in memory and has it's own independent network stack so none of it's traffic will show up on system tools.

---

### Post by Elfy on 2014-06-11
*Thread moved to **Other OS/Distro Support**.*

---

### Post by bashiergui on 2014-06-12
>  I just think wiping, reformatting and flashing the bios is just a novice way of dealing with the problem.No. The novice way is to think you can adequately clean it. Pros reimage. I would never trust that computer again until I backed up the files then reimaged.

---

### Post by mastablasta on 2014-06-12
you can download also bitdefeder rescue disk - you basically burn the iso on cd and then boot from cd (into Linux with XFCE environment), after that you can start the scan. it will download the latest virus definitions and then initiate the scan. perhaps it can clean the virus. i am not sure what happened with those filse. if they are really encrypted then...

[http://www.bitdefender.com/support/how-to-create-a-bitdefender-rescue-cd-627.html](http://www.bitdefender.com/support/how-to-create-a-bitdefender-rescue-cd-627.html)

it found more stuff than Avira.

---

### Post by WogBoy on 2014-06-12
> As an update I fixed my issue by using an ethernet cord to get the  internet to work, and doing so made HitmanPro work.  It's always  something simple isn't it?
I knew Hitman would work. An old solution for an old friend LOL. If I had a dollar for everytime that worked ......

**WARNING! YOUR PC IS NOT CLEAN YET**
 You still need to go to [http://www.bleepingcomputer.com/forums/](http://www.bleepingcomputer.com/forums/)  or  [http://www.malwareremoval.com/forum/](http://www.malwareremoval.com/forum/) and have some  logs looked at by an Expert ( no disrespect to the wonderfull hard working Admin Mods and Members on this site intended), Untill you are given the All clear by a member of UNITE ([**UNITE** - Unified Network of Instructors and Trained Eliminators]("http://uniteagainstmalware.com/"))
all you did was get rid of the screen that locked your pc.


> you can download also bitdefeder rescue disk - you basically burn the  iso on cd and then boot from cd (into Linux with XFCE environment),  after that you can start the scan. it will download the latest virus  definitions and then initiate the scan. perhaps it can clean the virus. i  am not sure what happened with those filse. if they are really  encrypted then...
There is a whole process for removing Malware from a Windows PC without causing damage To the OS  and quite frankly some antivirus systems just do not cut it, Bitdefender is OK, Same applies for spyware. Note Antivirus Software will not remove spyware or toolbars.  

Eg to remove malware I would use  [RKill]("http://www.bleepingcomputer.com/download/rkill/") first then run a malware/antivirus scanner on a running system  . Booting from Bitdefender Live CD is same thing as using Rkill as the malware processes are not running.. Nor is the OS with a Live CD or a Linux Live CD, And thats where the problems can start.  Use caution  when booting from a Live CD and deleting anything in Windows as it may make the OS unbootable.
>      **RKill** is a program that was developed at BleepingComputer.com  that attempts to terminate known malware processes so that your normal  security software can then run and clean your computer of infections.  When RKill runs it will kill malware processes and then removes  incorrect executable associations and fixes policies that stop us from  using certain tools. When finished it will display a log file that shows  the processes that were terminated while the program was running.
      As RKill only terminates a program's running process, and does not  delete any files, after running it you should not reboot your computer  as any malware processes that are configured to start automatically will  just be started again. Instead, after running RKill you should  immediately scan your computer using some sort of anti-malware or  anti-virus program so that the infections can be properly removed.

ESET Online Scanner is good to use With RKILL  [http://www.eset.com/us/online-scanner-popup/](http://www.eset.com/us/online-scanner-popup/)


>  if they are really  encrypted then.
They may not be recoverable, On the other hand it depends on the encryption, On bleeping computer contact [decrypterfixer]("http://www.bleepingcomputer.com/forums/u/834086/decrypterfixer/")
 he may be able to help.


> BleepingComputer.com was one of the first support sites to have reports of the CryptorBit, or HowDecrypt, ransomware. At the time, though, we were unable to help as this infection has been incredibly elusive and any supposed samples would not work. Recently, a member known as DecrypterFixer, has been able to recover some files that were supposedly encrypted by this malware. Due to our ability to now help users with this infection we have put together a guide that contains all known information about the CryptorBit infection.
Yes people actually ran and run this sort of stuff in VM or on " sacraficial" PC's picking it appart bit by bit, and then helping people for free.
[URL="http://www.bleepingcomputer.com/virus-removal/cryptorbit-ransomware-information"]http://www.bleepingcomputer.com/virus-removal/cryptorbit-ransomware-information

[/URL]
> No. The novice way is to think you can adequately clean it. Pros reimage.
No,  a real pro knows when to format and when its a waste of time. It depends on the infection, it's a case by case thing.

You dont need to "Nuke it from orbit " in all cases Ripley.

**EDIT**
I would like to invite Admin Mods and Members from the Unbuntu forum to pop over to [http://www.bleepingcomputer.com/forums/f/22/virus-trojan-spyware-and-malware-removal-logs/](http://www.bleepingcomputer.com/forums/f/22/virus-trojan-spyware-and-malware-removal-logs/) Or [http://www.malwareremoval.com/forum/viewforum.php?f=11&sid=94f0537300c5e4e558e377df92bb8402](http://www.malwareremoval.com/forum/viewforum.php?f=11&sid=94f0537300c5e4e558e377df92bb8402) and see some of the work done  with malware removal..

---

### Post by /ADM on 2014-06-12
Personally I would backup 'only' the documents folder (I would never fully backup as you could backup the virus/rootkit), flash the bios, throw out the HDD and do a reinstall on a fresh HDD or SSD and then scan again using a linux live cd, Knoppix is good for this.

But that is just me..  overly cautious.

---

### Post by WogBoy on 2014-06-12
> Personally I would backup 'only' the documents folder

Ever hear of PDF files And Other Microsoft office file's that are infected? Yes? If you must be "overly cautious" then those files are suspect too. Guess where most people store those files, Yes My Documents.

> then scan again using a linux live cd, Knoppix is good for this..


Guess you didnt see my reply as to why it may be a bad idea to use a Live Linux Cd of anything to "clean" windows? Without some guidance.  Because files could be deleted by a false positive rendering Windows unbootable.

That tutorial was made and tested by people who know what they are doing and is safe if followed 99% of the time(  not damage the OS) . This is a simple little bit of ransomware, If it was more complex the OP would have been told so and then given the apropriate advice.

The main reason I want the OP to go to a malware removal site is because that PC has been the victim of unsafe net usage and may have spyware on it EG toolbars and such, Only way to tell is to look at some logs, Then a Trained Windows Malware Removal Expert will advise the op on a course of action if any.
And to get some real practical advice on Securing Windows.

---

### Post by /ADM on 2014-06-12
> **WogBoy said:**
> Ever hear of PDF files And Other Microsoft office file's that are infected? Yes? If you must be "overly cautious" then those files are suspect too. Guess where most people store those files, Yes My Documents.


Guess you didnt see my reply as to why it may be a bad idea to use a Live Linux Cd of anything to "clean" windows? Without some guidance.  Because files could be deleted by a false positive rendering Windows unbootable.

That tutorial was made and tested by people who know what they are doing and is safe if followed 99% of the time for this type of infection.

Of course, but in this case it seems to be a boot issue not a general "a  viruses has infected my files".  Personally I would back them up in  this case, if it's a total system infection then I would throw them  away.  Base it on context here, not on every scenario that is irrelevent  to the OP's problem.

False positives happen but why anyone would blindly delete a bunch of files without inspecting them is beyond me.  Tutorials are also opinions, don't treat your posts like Gospel otherwise there is zero point for discussion.  You are not the only person who knows what they are doing.

Going to a malware removal site is good, but it is (IMO) far better to simply start again from scratch.  You can only clean so much, I wouldn't trust any 'ex-infected' computer unless they were completely nuked.

It's the difference of being safe and 'trying not to start from scratch'.

---

### Post by WogBoy on 2014-06-12
> Personally I would back them up in  this case, 
I totaly agree.

> False positives happen but why anyone would blindly delete a bunch of files without inspecting them is beyond me.
Because Novices do that sort of thing all the time, They also use tools like combo fix mess up their PC's then need help fixing it, I swear there are people out there that can't Do a system restore Change boot order in bios, And who download all sorts of "freeware" only to find they have some sort of infection, You help them clean up a week latter they are back with the something else. In linux speak They run as root ( admin without UAC) they run 2,3,and sometines 4 Antiviruses, And click on anything anyplace.


>  Base it on context here, not on every scenario that is irrelevent  to the OP's problem.
Correct as I said its a case by case thing. And as I said Warning! Your PC is not clean yet.
I am sorry if somebody was offended in any way by my coments.

---

### Post by /ADM on 2014-06-12
> **WogBoy said:**
> I totaly agree.


Because Novices do that sort of thing all the time, They also use tools like combo fix mess up their PC's then need help fixing it, I swear there are people out there that can't Do a system restore Change boot order in bios, And who download all sorts of "freeware" only to find they have some sort of infection, You help them clean up a week latter they are back with the same thing. In linux speak They run as root ( admin without UAC) they run 2,3,and sometines 4 Antiviruses, And click on anything anyplace.

I am sorry if somebody was offended in any way by my coments.

We are in agreement :P novices do indeed do some very strange things, some people do indeed to simply want to be taken to an expert and get it sorted out for them, though I always try to steer people to do these things themselves if they can, that way they are independent from the experts (and their charges).

The good thing about boards like this is we can all give advice and the OP can pick one.

---

### Post by WogBoy on 2014-06-12
At worst If the op needs to Nuke it from space at least the Op can recover things if needed first, Eg the Windows activation key that cant be recovered using linux or keys to anyother software that they paid for. As you know quite often people "misplace" these things if they actually bothered to record them. How much is a new copy of M$ office again. Or in my case when i used Microsoft Visual Studio Ultimate 2010 with MSDN.
> 
**From Microsoft**

Buy a Visual Studio with MSDN subscription online  from Microsoft for the fastest access to the software services, and  benefits your subscription provides. Select your location for the latest  pricing available through Microsoft in your region, which may not  reflect all applicable taxes.
         $13,299.00         new        
                $4,249.00         renewal       

[http://www.visualstudio.com/en-US/products/visual-studio-ultimate-with-MSDN-vs](http://www.visualstudio.com/en-US/products/visual-studio-ultimate-with-MSDN-vs)



Yes I did not record the Key and when disaster srtuck( HDD failed NO backups) M$ wanted me to pay up as I couldnt prove I paid for it in the first place. This was in 2010. It took 6 months statements from a bank showing the transaction and threats of legal action but 13 grand was 13 grand, Trouble was it cost me 6 grand in legal fees.

And I can show you posts where companys with 10's of employees that were hit by cryptolocker because the ceo opened a email attachment and encrypted the whole network and the IT department did not have backups under 12 months old, How much r&d was lost?
[Cryptolocker Hijack program             ]("http://www.bleepingcomputer.com/forums/t/506924/cryptolocker-hijack-program/")

---

### Post by Elfy on 2014-06-12
This has turned into a chat about security.

This is a Linux forum.

We offer a limited amount of support for Windows.

Thread Closed.

---

