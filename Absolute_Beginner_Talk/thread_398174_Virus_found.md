---
title: "Virus found"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by metalaxesucks on 2007-03-31
Hello folks
I was scanning with Avast antispyware on my Ubuntu 6.06 desktop and found this virus, the thing is Avast couldn't fix it. So I took a screen shot of it to show you what I'm talking about. 

[http://www2.hawaii.edu/~hurtadoj/avast.png](http://www2.hawaii.edu/~hurtadoj/avast.png)

As you can see I found the file that needs to be deleted (pagefile.sys), but I'm afraid if I delete it manually I might screw up something.

Also, after about 40 minutes or so of scanning my Avast just closed, just like you would close it with the X in the upper right hand corner. And when I relaunched it it said "Deleted state lock file /home/username/.avast/lockfile-username"

Help me out please someone

Be gentle I'm not a pro at Linux yet.

---

### Post by yabbadabbadont on 2007-03-31
pagefile.sys is your Windows swap file...

---

### Post by metalaxesucks on 2007-03-31
Does that mean that there is a Virus on my Windows side?

Here is something I read up on the Windows Swap File:
Windows swap file is a large hidden file located in the root of your boot drive used for keeping your virtual memory. It is only a temporary file, but Windows does not delete it from your disk upon shut down,..It is strongly recommended that you clean it.

Can I clean out the pagefile.sys or Windows Swap File as suggested above?

---

### Post by beercz on 2007-03-31
The swapfile is what Windows uses to temporarily store data from your computer's memory whilst it is running.  Windows uses a chunk of your hard disk space as extra working memory when Windows is running.

I would leave it alone if I were you.

---

### Post by Zzl1xndd on 2007-03-31
It does look like its on your windows side.

---

### Post by wj32 on 2007-03-31
If Windows is hibernated right now, DON'T DELETE IT. If it's not, and it's cleanly shut down, you can delete it.

---

### Post by metalaxesucks on 2007-03-31
When referring to the pagefile.sys aka Windows swap file

Mr/Ms beercz says:
"I would leave it alone if I were you."
Mr/Ms wj32 says "If Windows is hibernated right now, DON'T DELETE IT. If it's not, and it's cleanly shut down, you can delete it."

Anymore opinions/suggestions?

---

### Post by orb9220 on 2007-03-31
Also do a scan in windows. Why was the pagefile shown to be infected?

Just to be safe boot up in windows and scan for viriuses.

---

### Post by arron on 2007-03-31
If this was a virus i think it would say so.  How far along did the scan go?  Im guessing its spitting out the error because it cant write to your ntfs partition.  If this is the first thing that comes up when u scan, check if you can write to the drive, if not have a look on here how to enable it.

If it was a virus though, im sure a virus alert would pop up.

---

### Post by wj32 on 2007-03-31
The page file (or swap) is used to swap out pages from memory if there is not enough RAM or if the pages are not used very often. Pages are basically chunks of memory. In your case it is "infected" because some memory from a virus program *has* been swapped out and the virus scanner finds it in your pagefile.

---

### Post by arron on 2007-03-31
wj32: im not sure if its a virus, its a error not virus alert saying it cant rename or move the file.  Viruses running do that, but not while running linux scanning another partition.  I really think it may be his write permissions.

---

### Post by arron on 2007-03-31
Crap... Sorry after looking further, your right. It is a virus!  I missed that part.  Sorry, you guys are right.

Now im very sure you need write permission on your ntfs drive, do a search on here for it.  ntfs 3g i think its called.

---

### Post by wj32 on 2007-03-31
It is a virus. It says in the screenshot.

---

### Post by wj32 on 2007-03-31
Hah, you posted when I was posting "It is a virus."

---

### Post by wj32 on 2007-03-31
Yes, don't delete your pagefile while Windows is running! :)

---

### Post by arron on 2007-03-31
My bad.....  I know RTFS right? :-P

Here is a link on how to mount your ntfs drive with read/write permissions, this will get you on the go.

[http://ubuntuforums.org/showthread.php?t=217009&](http://ubuntuforums.org/showthread.php?t=217009&)

---

### Post by Gina on 2007-03-31
You could turn off pagefile and reboot Windows.  Then shut Windows down an boot up Linux and test again.  The Windows pagefile will not exist now.  If you want the Windows pagefile you can turn it back on in Windows.  Depends how much memory you have and how many apps you run at the same time and the memory required.

I would still run a virus check in Windows before turning off the pagefile though - there could be other bits of virus around.

---

### Post by STREETURCHINE on 2007-03-31
oops double post

---

### Post by STREETURCHINE on 2007-03-31
go into windows and do the scan ,it is on your windows side as suggested before boot to windows and run the scan,you can then dig it out manually,if your virus protection cant dig it out .

in windows it is better to run the scans in safe mode,but not as adminastrator,

---

### Post by WeAreNotAlone on 2007-03-31
Hello guys (and gals),

First post here..

On the XP Windows virus in the PAGEFILE.SYS file...

What I'd do is to go to My Computer icon>system properties>Advanced>first section Performance, click the Settings button.. Then click the ADVANCED tab... look towards the bottom, Virtual Memory, click the CHANGE button..

At that point you will see all the paging files on whatever hard discs you may have...
You can select NO PAGING file... and then reboot... Upon reboot check in root directory (C:\pagefile.sys) and then DELETE it...  Reboot and then re-enable the pagefile...

PS: Viruses hide in the System Restore file... 
(it's a file that tracks changes to your system, enables you to go-back to a previous time, like say before you installed /deleted something and it screwed up your system.)
Viruses like to hide in the restore file,,,, as they are "restored...

Standard procedure for most viruses to be SURE they haven't hidden away  in the System Restore file is to dis-able System Restore (My Computer icon>system properties>System Restore..) Then reboot into SAFE MODE and do your virus scan from there... then reboot into normal mode, re-enable system restore once you have confirmed the virus has been removed. (might want to run a second scan with OS in normal mode).

.

---

### Post by Nolander on 2007-03-31
plz tell me im right,

im pritty sore some one once sed u cant get viruses on linux.

nolander

---

### Post by Lucifiel on 2007-03-31
I'd run the following anti-spyware as well as scan with another anti-virus program. This is 'cos many virus also attempt to infect your antivirus program and also 'cos many viruses also install other forms of viruses, etc.. I also suggest you go to castlecorps and post in their forums for help. 

Anti-spyware programs:

1.AVG Anti-spyware 7.5(don't really need)
2.Bazooka Scanner
3.CMShredder
4.eTrust Internet Security Suite = AVG??
5.Lavasoft Ad-Aware SE Personal
6.Spybot - Search and Destroy
7.SpywareBlaster
8.Trojan Hunter

---

### Post by NicoleM on 2007-03-31
> **Nolander said:**
> plz tell me im right,

im pritty sore some one once sed u cant get viruses on linux.

nolander

it is possible but it's highly uncommon and unlikely.  if you pay close attention to the eventual discovery of this thread, the virus is in his windows partition...he was simply running a scan from linux when he happened to find it.

even though viruses and such are unlikely in linux that doesn't mean you still shouldn't take some precautions.  even a simple software firewall goes a long way in helping along with watching the sites you go to and now downloading things from strangers, etc.  if you use common sense you'll be fine probably 90% of the time

---

### Post by metalaxesucks on 2007-04-01
> **WeAreNotAlone said:**
> Hello guys (and gals),

First post here..

On the XP Windows virus in the PAGEFILE.SYS file...

What I'd do is to go to My Computer icon>system properties>Advanced>first section Performance, click the Settings button.. Then click the ADVANCED tab... look towards the bottom, Virtual Memory, click the CHANGE button..

At that point you will see all the paging files on whatever hard discs you may have...
You can select NO PAGING file... and then reboot... Upon reboot check in root directory (C:\pagefile.sys) and then DELETE it...  Reboot and then re-enable the pagefile...

PS: Viruses hide in the System Restore file... 
(it's a file that tracks changes to your system, enables you to go-back to a previous time, like say before you installed /deleted something and it screwed up your system.)
Viruses like to hide in the restore file,,,, as they are "restored...

Standard procedure for most viruses to be SURE they haven't hidden away  in the System Restore file is to dis-able System Restore (My Computer icon>system properties>System Restore..) Then reboot into SAFE MODE and do your virus scan from there... then reboot into normal mode, re-enable system restore once you have confirmed the virus has been removed. (might want to run a second scan with OS in normal mode).

.

Thanks everybody for the suggestions. I ended up turning off the pagefile in Windows, deleting the folder, and leaving it off because turning it back on led Avast to tag it as infected with a virus. As long as my PC side runs Ok with out it I'll leave it off.
One  thing that I find intersting is that I scanned with AOL's Kaspersky antvirus in safe mode as well as spyware doctor, Adaware, spybot search and destroy, windows defender, cw shredder, hijack's this ADS Spy, superantispyware and I also have SpywareBlaster and not one of these scanners found the virus. The only way I found out about this virus was to scan with Avast from the Linux side and then I had to manually delete it from the window's side, because after all it was in the window's side.
Thanks everybody
I followed your directions Mr WeAreNotAlone and they worked fine

---

### Post by OrangeCrate on 2007-04-01
I've posted this thread on the avast! Linux forum...

---

### Post by OrangeCrate on 2007-04-01
Follow-up on previous post ( ^)...

> **metalaxesucks said:**
> 
I was scanning with Avast antispyware on my Ubuntu 6.06 desktop and found this virus, the thing is Avast couldn't fix it... 

...Help me out please someone


A discussion regarding your problem has been started on the avast! forums. It's Sunday, and there are many time zones involved, so responses will be slow to start, but keep your eyes on this thread for help:

[http://forum.avast.com/index.php?topic=27473.0](http://forum.avast.com/index.php?topic=27473.0)

---

### Post by Patrick K on 2007-04-01
Here is Wikipedia's list of Linux viruses (probably not complete)
[http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses](http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses)
I guess we can feel a bit short changed, nowhere near the amount available for Windows :).

---

### Post by hornett on 2007-04-01
Were there any other infected files listed?

Given that the contents of the pagefile will be almost random chunks of executable code and data, it could just be a false positive.

Personally I would now scan the whole Windows partition from Windows & Linux; using as many scanners as possible. If nothing had turned up at that point, I'd exclude that file from the scan and go my merry way.


Edit: On the subject of 'Linux' viruses/virii/whatever, I personally would be more wary of running packages from unofficial repositories such as those posted commonly in the HowTo section of this forum...

There is simply no way of knowing that somebody hasn't added a couple of lines of code before uploading that allow root access to your machine (or do anything else for that matter!). 

The Xorg 7.2 packages posted recently are a great example - the codebase is huge enough to make hiding an exploit easy, Xorg generally runs as root, and it has a perfect way to record every keystroke you make ready to be uploaded later and grep'd by the attacker for passwords and credit card numbers.

---

### Post by metalaxesucks on 2007-04-01
There were no other files infected.
Now that I understand what page file is, and after I scanned with plenty of other scanners on the windows side and after they came up negative, I agree that it could have been a false positive, however I already turned page file off and deleted the folder so what's done is done. I'll probably turn it back on later, but for now my windows is running fine.

I know Avast is not in the repositories of Ubuntu, but I also know that they are a reputable outfit and I know that there scanner is very easy to use, so I downloaded it form their official website. I also tried ClamAV with the GUI and it still was a little bit confusing.
You have to forgive me, but I'm a windows user still trying to learn Ubuntu.

I also use Swiftfox which is not in the repositories of Ubuntu, but after reading all the positive posts here I feel its a trustworthy program.

---

