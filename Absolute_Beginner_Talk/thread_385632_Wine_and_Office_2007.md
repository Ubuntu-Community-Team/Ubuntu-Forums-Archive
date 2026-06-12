---
title: "Wine and Office 2007"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by Shack_ on 2007-03-15
I'm trying to install Office 2007 on Ubuntu through Wine. I opened a command prompt and ran wine on the setup.exe file, but the following error occurred:

```
Fontconfig warning: "~/.fonts.conf", line 6: unknown element "boool"
Fontconfig error: "~/.fonts.conf", line 6: mismatched tag
libGL warning: 3D driver claims to not support visual 0x4b
Fontconfig warning: "~/.fonts.conf", line 6: unknown element "boool"
Fontconfig error: "~/.fonts.conf", line 6: mismatched tag
libGL warning: 3D driver claims to not support visual 0x4b
```

Then a windows popped up titled "Error." It read "Newer windows version needed."

What exactly does this mean? I would like to download the newest version of Wine, but my computer has no internet access, and the version on packages.ubuntu.com is not the most current release.

---

### Post by heimo on 2007-03-15
I probably shouldn't try to help using Wine, as I know pretty much nothing about it. But my hunch would be to run winecfg and change the version of Windows there, to XP or 2003.

---

### Post by Shack_ on 2007-03-15
That seemed to work, but now another window popped up that reads: 

A required D:\SmallBusinessr.WW\OSETUP.DLL cannot be loaded This may indicate that the file is missing or damaged.

I think the application is looking for a nonexistent directory. How do I trick the setup into locating the right file under Linux?

Or, maybe the .dll file isn't included with Wine. How can I get Wine to use the file?

---

### Post by MrKlean on 2007-03-15
I hate anything Microsoft lately.  Why not just use OpenOffice... no hassles and it's great for the average user ; ))

---

### Post by Shack_ on 2007-03-16
Begging your pardon, but I *like* Office, and the reason I want to do this is because I created a PowerPoint presentation in Office 2007. I saved it for 97-2003, but the images and effects don't show up properly on other computers. I want to use my laptop and bring in the presentation, but I don't want to have to install Windows on it. And certain effects don't show up in OpenOffice.org either. I would rather not have to scour the file looking for missing effects and reapply them using OpenOffice.org.

Not to sound rude, but I'd rather have someone give me an answer instead of commenting on whether or not they approve of my software decisions. Plus, you don't have to navigate endless file menus in Office 2007. It is *way* more user-friendly than OpenOffice.org.

---

### Post by MrKlean on 2007-03-16
Shack, my apologies.  I was offering a suggestion that I felt you may not have explored.  Also, at no point in time did I comment on your choice of software.  I did ask why not use it, which you answered.  My apologies for suggesting an alternative solution. I just don't comprehend why one would use a free OS and then pay several hundred dollars for an add-on.  But, it's not my business ; )  Enjoy Ubuntu ; )

---

### Post by heimo on 2007-03-16
Sorry, I'm unable to help any further (lack of knowledge and access to Office 2007). Hopefully someone else can give you a hand?

[This]("http://appdb.winehq.org/appview.php?iVersionId=4992&iTestingId=6830") might be related?

---

### Post by Belyel on 2007-03-16
You might look at software called "cross over office."  I know that it is designed to let you use MS office in linux, and it doesn't use wine (I think).  I haven't used it, and I don't know if it works with office 2007 or not, but I'm just throwing it out there.

---

### Post by tanpantsman on 2007-10-30
On a slightly different topic, i installed wine with the add/remove software utility, and I have no wincfg anywhere on my system.  I ran the command to no avail and i used a command line find to search the entire thing.  still nothing.  Should I just scrap this install and get it from apt-get instead?
There are really only a couple of reasons I want office 07 over open office.  Faster, looks snazzier, and it has onenote, which i am becoming rather fond of.

Any ideas?  Thanks a lot

Oh, this is a ubuntu 7.04 with gnome for normal use, KDE is installed, it's a desktop version that has added server functionality so it's a backup pc and a personal webserver.

-Tanpants

---

### Post by xueg0i on 2007-11-02
Use winecfg instead :) But I doubt wine is up to office 2007 yet.

---

### Post by Duck2006 on 2007-11-02
In the book,

Apress Beginning Ubuntu Linux From Novice to Professional Mar 2006

It shows you how to run office 2000 in wine, it may help you load the ver of office that you want to load.

---

### Post by Maestro23 on 2007-11-02
> **xueg0i said:**
> Use winecfg instead :) But I doubt wine is up to office 2007 yet.

Doesn't look like much progress has been made with Office 2007 under Wine.
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=31](http://appdb.winehq.org/objectManager.php?sClass=application&iId=31)

---

### Post by markharding557 on 2007-11-02
> **Shack_ said:**
> I'm trying to install Office 2007 on Ubuntu through Wine. I opened a command prompt and ran wine on the setup.exe file, but the following error occurred:

```
Fontconfig warning: "~/.fonts.conf", line 6: unknown element "boool"
Fontconfig error: "~/.fonts.conf", line 6: mismatched tag
libGL warning: 3D driver claims to not support visual 0x4b
Fontconfig warning: "~/.fonts.conf", line 6: unknown element "boool"
Fontconfig error: "~/.fonts.conf", line 6: mismatched tag
libGL warning: 3D driver claims to not support visual 0x4b
```

Then a windows popped up titled "Error." It read "Newer windows version needed."

What exactly does this mean? I would like to download the newest version of Wine, but my computer has no internet access, and the version on packages.ubuntu.com is not the most current release.

just checked wine application database on the wine site and it seems that 2007 does not work well however 2003 is much better and 2000 is a little better still but none are 100% 

also another option is to run windows in vm ie virtualbox

---

### Post by Exonimus on 2007-11-02
I can give you a little more information about using office on wine. As a linux newbie(just a few weeks) I also really wanted to be able to run office. First solution I came across was wine. Office 2000 worked perfectly for me. I'm not sure about XP, but it seems to run ok. Office 2003 however, was a different story. Since II create a lot of powerpoint presentations, there's some stuff I use a lot that is in office 2003 and later, but not in xp and earlier. I tried to install office 2003, and after a lot of hassle, it worked. That is, I could get it to run, but it crashed as soon as I tried to open certain menu's, load more than one picture, etc. The latter turned out to be because I had insufficient ram. I added a bit and that solved a lot of the crashes. I still couldn't add effects properly. That's the  reason I created a virtual machine. With windows xp on it, sadly. However, there are some more apps I really need. I can also add it seems to run a lot faster on a vritual machine with less RAM. I currently assigned 192mb to it and it runs perfectly(you might want to assign a bit more, though). I installed office 2003 on the virtual machine without any problems(obviously) and I now run office from there. I've got my main folders shared, so getting files on my regular pc is not a problem. I'm certain this will work with office 2007 as well. Also, you might want to consider a program called Virtualbox(I think it was mentioned earlier) because it also has an option called 'seamless integration' which comes in quite handy. It looks something like this:
[http://img211.imageshack.us/img211/9073/schermafdrukfp4.png](http://img211.imageshack.us/img211/9073/schermafdrukfp4.png)

(on a side note, I still have to find a way to hide the annoying 'windows xp snapshot 1' bar on my regular task bar) and yes, my regular taskbar is also blackish. I just love that color :P The seamless mode is in not way perfect yet, but it's quite good. You can also get the seamless desktop a different(and, if I might add, the hard way) by doing it almost manually. you can view more info about that here:[http://ubuntuforums.org/showthread.php?t=433359](http://ubuntuforums.org/showthread.php?t=433359)

edit: and yes, I do still have powerpoiint 2000 installed on my regular linux :P sorry if that confused you. My family seems to like it better somehow :S

edit: I can also tell you that I couldn't run office 2003 with crossover office properly. Gave me the same error as wine(something about the app not being installed for the current user, this can be solved by downgrading wine and upgrading it again later on. Not sure if that can be done with cxoffice though)  Also, it was crossover office I used to install office 2000 with. No hassle, and kind of easy. It should work properly on wine, though

and you DO need a valid XP license to install xp on a virtual machine. I hope you have that laying around somewhere. That's the biggest disadvantage of it. For the rest, every possible app. works with a virtual machine, except for heavy grapihc apps like games. Some old games might. Actually, I've something about all openGL games running properly. there's some sort of project that can get the graphics card to work for the VM. or something. I don't have much knowledge in that area :P I do know that with that project, the games will run on 87% of the detail on which they would run on your regular pc. I read that in an article somewhere, I'll see if I can find it

---

### Post by scales on 2007-11-05
little link i found that helped me get office 2003 working great under ubuntu 7.10

[http://thesorcerer.wordpress.com/2007/10/07/guide-how-to-install-microsoft-office-2003-in-linux/](http://thesorcerer.wordpress.com/2007/10/07/guide-how-to-install-microsoft-office-2003-in-linux/)

---

### Post by ratatosk13 on 2007-11-05
I would suggest running WinXP using VMware server and installing Office 2007 that way. I've used VirtualBox and VMware for running virtual PCs and have had the best performance with VMware. Anyway, I'm running Office 2k3 on VMware server in Gutsy and have had no problems. Good luck!

---

### Post by Delvien on 2007-11-05
Try using Winecfg and setting it to Windows Vista and hit apply (first tab)

---

### Post by FinalBoy on 2008-02-01
[http://wine-review.blogspot.com/2008/01/microsoft-office-2007-install-on-linux.html](http://wine-review.blogspot.com/2008/01/microsoft-office-2007-install-on-linux.html)

---

### Post by yaknowwat on 2008-02-02
[http://www2.ashampoo.com/webcache/html/1/product_2_0238__.htm](http://www2.ashampoo.com/webcache/html/1/product_2_0238__.htm)

Ashampoo Office runs quite nice under wine as it is based off SoftMaker Office and i have found it to work quite nicely feels better than MS Office 2003 and is loads faster.
I'll be honest OpenOffice with powerpoints isn't that great. (try and set an image as a background)


[http://www.softmaker.com/english/sitemap_en.htm](http://www.softmaker.com/english/sitemap_en.htm)

Then there is SoftMaker Office also very fast
they have a 2008 version though at the moment only for windows
though they have a 2006 version for other operating system.


You can try the trial versions i think they have that.

---

### Post by SomeGuyDude on 2008-02-02
> **FinalBoy said:**
> [http://wine-review.blogspot.com/2008/01/microsoft-office-2007-install-on-linux.html](http://wine-review.blogspot.com/2008/01/microsoft-office-2007-install-on-linux.html)

Um... I can't read what the hell he did. I saw "wine --" and then a bunch of fuzzy characters. What happened?

---

### Post by FinalBoy on 2008-02-04
> **SomeGuyDude said:**
> Um... I can't read what the hell he did. I saw "wine --" and then a bunch of fuzzy characters. What happened?


try this url:
[http://anonymouse.org/cgi-bin/anon-www.cgi/http://wine-review.blogspot.com/2008/01/microsoft-office-2007-install-on-linux.html](http://anonymouse.org/cgi-bin/anon-www.cgi/http://wine-review.blogspot.com/2008/01/microsoft-office-2007-install-on-linux.html)

---

### Post by mehd36 on 2008-03-02
There is no information in this video, he just wrote "wine --version" to see his wine version (0.9.53)

---

### Post by Siller on 2008-03-06
I am looking for a possible alternative solution to my problem and I am not the "average" user. Seems that if we don't implement  a database with web front end then I will have to Wine Office if I can. I don't like it at all but might have to use it.

Problem: If I save a shared Excel sheet with Open Office it locks it, takes control and they have to re-open and share it again.

So either Open Office needs to share the work space for multiple users, I get Office 2007 running on Wine or we implement a job tracking database.

(The bosses will be hard to budge toward the last and I don't see Open Office fixing this problem fast.)

If someone knows how, please would you post a step-by-step as this is my first week on Linux

---

### Post by h2gofast on 2008-03-13
[http://wine-review.blogspot.com/2008/01/running-ms-office-2003-under-linux-with.html](http://wine-review.blogspot.com/2008/01/running-ms-office-2003-under-linux-with.html)



Would office 2003 work for you

---

### Post by biotux on 2008-03-17
> **FinalBoy said:**
> [http://wine-review.blogspot.com/2008/01/microsoft-office-2007-install-on-linux.html](http://wine-review.blogspot.com/2008/01/microsoft-office-2007-install-on-linux.html)

I believe that this movie is a fake. The guy doesn't want to publish a howto which makes me very suspicious. 
He most likely is using Qemu or VirtualBox (Seamless mode) but not wine.

---

### Post by simpleboy on 2008-03-27
Here is a good tutorial on installing office 2007 in Ubuntu [http://goodbutbad.blogspot.com/2008/03/install-m-office-2007-in-ubuntu.html](http://goodbutbad.blogspot.com/2008/03/install-m-office-2007-in-ubuntu.html)

---

### Post by sayantandas on 2008-03-28
> **simpleboy said:**
> Here is a good tutorial on installing office 2007 in Ubuntu [http://goodbutbad.blogspot.com/2008/03/install-m-office-2007-in-ubuntu.html](http://goodbutbad.blogspot.com/2008/03/install-m-office-2007-in-ubuntu.html)

hi, thanks 4 d url . i followed the instructions and ms office enterprise 2007 installed without a glitch.
but while running it, i get the following error

fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Microsoft Office\\Office12\\winword.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Microsoft Office\\Office12\\winword.exe" failed, status c0000135

---

