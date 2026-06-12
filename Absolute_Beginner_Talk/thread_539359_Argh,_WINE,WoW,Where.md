---
title: "Argh, WINE,WoW,Where?"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by Kinuxx on 2007-08-31
Hi Guys (and Girls),

Finally managed to get the WoW installer from Blizzard Downloader!

It downloaded, terms and co came up, clicked accept, etc...

now updating ( expected )

downloaded update, installer got stuck on

 "Waiting for files to close."

i waited 5, then i googled it!

Red

   "1. Run winecfg
   2. Set the Windows version to NT 4.0. "

which I did no problem, then had to re start updater!

This is the problem...

I cannot find wow.exe, to get the updater again! i get the following error messages:

random@random-desktop:~$ wine wow.exe
wine: could not load L"c:\\windows\\system32\\wow.exe": Module not found
random@random-desktop:~$ wine wow
wine: could not load L"c:\\windows\\system32\\wow.exe": Module not found
random@random-desktop:~$ 

I then went onto read that above means I haven't give it a path to run?

I don't know what that means exactly. or how to do it?

This is what I did so far...

download trial installer, made /wine in home/user/ ...
right clicked installer- open with wine, MY Computer>>(C: )>>Programme Files
(this is where i downloaded it to!     Is this the correct place?
wow.exe launched automatically,
terms and cons, then update, updater froze...changed to NT 4

Now when I right click wow installer downloader again, WoW is now there below windows and programme files folders! (If this is any help!)

Please could someone give this noob some help?
Be much appreciated! :)

 ( Had to wait 2 whole nights for this to download :( )

Thanks

---

### Post by anewguy on 2007-08-31
I'll be honest and tell you I don't even know what WOW is, however, have used Applications/Accessories/Wine File and clicked the "C" drive then searched the folders to see what folder it got installed to?  Once you have that you just do  wine  fullpathtofile  , for example:  wind "c:\program files\something\something.exe".

I hope it helps in some way.:)

---

### Post by anewguy on 2007-08-31
Missed one other thing - it's possible if you downloaded/installed it first, then changed the Wine config to NT 4 that you have to reinstall it to the NT 4 instance.

---

### Post by Kheldin on 2007-08-31
I think I had this problem, and I only seemed to get it when I used the launcher instead of just running the wow.exe file. If it gets hung up like that again, try going to 'System -> Admin -> System Monitor' and make sure you kill off all wine processes. Try starting the game in wine using the wow.exe instead of the launcher. I start Wow  using the main executable and I've never had any issues.

Worth noting but do a search on this forum for 'wow' and you will find many helpful links. A few posts may be outdated, but the majority of them can help.

---

### Post by Kinuxx on 2007-08-31
Do you mean I have to re-install Wine again? And run :

" wine config " change it to NT 4.0 ( I originally changed it to XP )

then download the wow.exe installer again via the Blizzard Downloader?

Sorry, am a complete newbie!

Thanks

---

### Post by Kheldin on 2007-08-31
Oh yeah... if you can't find your wow.exe file, go to 'Places -> Search for Files' and search for wow.exe.

Once you find it, start it by typing the full path before wow.exe ... that is:

wine /full/path/to/wow/folder/wow.exe

obviously replacing the above with the full path of where yours is.

---

### Post by anewguy on 2007-08-31
I would first try the wine file browser to see if you can find it in the program files folder somewhere.  If you do find it, remember you have to use the full path for wine to find it, again:

wine  "c:\program files\something\something.exe"

If you have already run winecfg to get to NT 4, and if by saying "then had to re start the updater" means in installed or updated "WOW", then I assume you just need to add the full path to the "wine" command line.:)

---

### Post by Kinuxx on 2007-08-31
Hi Kheldin,

I just tried places>>search... but wow.exe doesnt seem to be found anywhere :confused:

What file do I need to search exactly? I have checked them all?

wow.exe is definetly here somewhere! As its there when I right click on the Blizzard Download installer!

Above seems to be the only way to run wine! (that's if it actually is and not just the Installer? 

I can't seem to find the fake (C: ) neither!

Could you be more specific please?

Thanks

---

### Post by anewguy on 2007-08-31
Also, if you don't want to use wine file, then click on "Places" on the top bar, select "Home Folder" and click on it.  When the File  Browser comes up, click on "View" and click "Show Hidden Files".  You will now see a ".wine" folder listed.  Click on that, then go to the "drive_c" folder and search through there until you find your file.  Once you have found it you know the path, but I would be sure to quote the filepathfilename string because otherwise you have to put a backslash in front of each space.  Also, I think (haven't done it for a while) that the wine command requires the path in Windows format.:)

---

### Post by Kinuxx on 2007-08-31
> **anewguy said:**
> I would first try the wine file browser to see if you can find it in the program files folder somewhere.  If you do find it, remember you have to use the full path for wine to find it, again:

wine  "c:\program files\something\something.exe"

If you have already run winecfg to get to NT 4, and if by saying "then had to re start the updater" means in installed or updated "WOW", then I assume you just need to add the full path to the "wine" command line.:)


Hi,

Sorry, I only installed wine a few days ago, and i'm not exactly sure what you mean?

Could you be able to be more specific please?

I don't know how to launch the wine file browser?

I enter "wine" in the command line and get this message

"Usage: wine PROGRAM [ARGUMENTS...]   Run the specified program
       wine --help                   Display this help and exit
       wine --version "

I had previously installed wine on my 2nd install (now my 6th :lolflag: )

That time Wine was tabbed on Applications above add/remove...

This time, its not there :confused:

So how do I open the wine file browser again?

Thanks

---

### Post by anewguy on 2007-08-31
> **Kinuxx said:**
> Hi Kheldin,

I just tried places>>search... but wow.exe doesnt seem to be found anywhere :confused:

What file do I need to search exactly? I have checked them all?

wow.exe is definetly here somewhere! As its there when I right click on the Blizzard Download installer!

Above seems to be the only way to run wine! (that's if it actually is and not just the Installer? 

I can't seem to find the fake (C: ) neither!

Could you be more specific please?

Thanks

As I mentioned in my last post, the folder of ".wine" is a hidden file on your home folder.  The path to your "c" drive in WINE is ".wine/drive_c".

---

### Post by Kheldin on 2007-08-31
Sorry.. under the 'Places -> Search for files' , after you type in wow.exe to search for, make sure to set the 'look in folder' to 'File System' so that it will search your entire hard drive instead of just your home folder.

---

### Post by anewguy on 2007-08-31
> **Kinuxx said:**
> Hi,

Sorry, I only installed wine a few days ago, and i'm not exactly sure what you mean?

Could you be able to be more specific please?

I don't know how to launch the wine file browser?

I enter "wine" in the command line and get this message

"Usage: wine PROGRAM [ARGUMENTS...]   Run the specified program
       wine --help                   Display this help and exit
       wine --version "

I had previously installed wine on my 2nd install (now my 6th :lolflag: )

That time Wine was tabbed on Applications above add/remove...

This time, its not there :confused:

So how do I open the wine file browser again?

Thanks
  Okay, let's try this:

open a terminal window so you have the command line

type:

cd /wine/drive_c

pwd   <-- does this show you are in the drive_c folder?

ls -al   this will list all of the files/folders at the root level of drive_c

one of these will probably be Program Files

cd "Program Files"

ls -al  <--- post the output back here and we'll go from there:)

---

### Post by Kinuxx on 2007-08-31
> **anewguy said:**
> Also, if you don't want to use wine file, then click on "Places" on the top bar, select "Home Folder" and click on it.  When the File  Browser comes up, click on "View" and click "Show Hidden Files".  You will now see a ".wine" folder listed.  Click on that, then go to the "drive_c" folder and search through there until you find your file.  Once you have found it you know the path, but I would be sure to quote the filepathfilename string because otherwise you have to put a backslash in front of each space.  Also, I think (haven't done it for a while) that the wine command requires the path in Windows format.:)

:)

Now that I have clicked show hidden files (learn something new everyday :) )

I am able to now find wow.exe. :)

However, when you mention

"but I would be sure to quote the filepathfilename string because otherwise you have to put a backslash in front of each space."

how/where do i get the filepathfilenamefrom, could you give me an example please as to what it may be, and also how i would add that file? :)

Cheers! :) :)

---

### Post by Kinuxx on 2007-08-31
> **anewguy said:**
> Okay, let's try this:

open a terminal window so you have the command line

type:

cd /wine/drive_c

pwd   <-- does this show you are in the drive_c folder?

ls -al   this will list all of the files/folders at the root level of drive_c

one of these will probably be Program Files

cd "Program Files"

ls -al  <--- post the output back here and we'll go from there:)



chiron@chiron-desktop:~$ cd /wine/drive_c
bash: cd: /wine/drive_c: No such file or directory

---

### Post by anewguy on 2007-08-31
> **Kinuxx said:**
> :)

Now that I have clicked show hidden files (learn something new everyday :) )

I am able to now find wow.exe. :)

However, when you mention

"but I would be sure to quote the filepathfilename string because otherwise you have to put a backslash in front of each space."

how/where do i get the filepathfilenamefrom, could you give me an example please as to what it may be, and also how i would add that file? :)

Cheers! :) :)

I will make an assumption here, so you may need to adjust that to fit your actual path.  I'm going to assume that WOW is installed in the WOW folder within Program Files and that the name of the executable is WOW.exe.  If so:

in a terminal window type:

wine "c:\Program Files\WOW\WOW.exe"  and press enter

Let me know what happens.:)

---

### Post by anewguy on 2007-08-31
> **Kinuxx said:**
> chiron@chiron-desktop:~$ cd /wine/drive_c
bash: cd: /wine/drive_c: No such file or directory

you forgot the "." before "wine"  - it should be "cd /.wine/drive_c"  - you can copy everything within the quotes and paste it to the command line if you want.

If I missed the "." when I entered the cd command in the post, sorry about that!:)

---

### Post by anewguy on 2007-08-31
Going out for a quick smoke - hang on a minute and I'll be right back.  BTW - don't worry about this all being new - there's no need to apologize!  I'm relatively new here myself, but have learned just enough to sometimes be of help.  Everyone starts new and has to learn - everyone on the forums has been down that same road.  So, just hang in there, things will start to click more and more as time goes by, and the next thing you know you'll be answering some questions, too!:)

---

### Post by Kinuxx on 2007-08-31
> **anewguy said:**
> I will make an assumption here, so you may need to adjust that to fit your actual path.  I'm going to assume that WOW is installed in the WOW folder within Program Files and that the name of the executable is WOW.exe.  If so:

in a terminal window type:

wine "c:\Program Files\WOW\WOW.exe"  and press enter

Let me know what happens.:)


chiron@chiron-desktop:~$ cd wine c:\Programe Files\WOW\WOW.exe
chiron@chiron-desktop:~/wine$ ls
WoW-enGB-Installer-downloader.exe


I also tried

chiron@chiron-desktop:~$ cd /.wine/drive_c/World_of_Warcraft/WoW.exe
bash: cd: /.wine/drive_c/World_of_Warcraft/WoW.exe: No such file or directory
chiron@chiron-desktop:~$ 

Which is what it looks like from the file browser.


Sorry...

chiron@chiron-desktop:~$ wine c:\Program Files\WOW\WOW.exe
wine: cannot find 'c:Program'
chiron@chiron-desktop:~$

---

### Post by anewguy on 2007-08-31
Well let's try this again.  Copy the below (highlight, right click and copy) then paste into the command line and press enter.  

wine c:\WoW-enGB-Installer-downloader.exe

That should start the downloader.  This I assume will install it somewhere in the Program Files tree, so post back after it starts downloading so I know the download started, ok?:)

---

### Post by anewguy on 2007-08-31
I probably should have had you try this first, but I don't see it in the output of the "ls" you did on your Program Files folder:

cd /.wine/drive_c/World_of_Warcraft  <---Don't add "/WoW.exe" to this - you just want to change you working folder, and you can't do that to an exe.


Please let me know what the result of this is.:)

---

### Post by Kinuxx on 2007-08-31
I was able to load the 2.1.0 patch from the hidden folders by right clicking on it and using wine...
the patch was successfully updated!

Then it automatically started wow.exe again...

it said need another patch please restart , yeah sure why not...

small patch 1.7 MB or something...

now I'm getting the same error as I was for the first 2.1.0 patch when trying to install it

" Waiting for files to close. "

:lolflag:

WoW, i've never met a game that has made me want to cry before! :lolflag:

Ok, well maybe Final Fantasy 8  :)


I just run winecfg again, to check whether it returned to Win XP,  but it is still NT 4.0

---

### Post by anewguy on 2007-08-31
Well,  you remember how I said I was not expert?:)  You've reached the end of knowledge here.  I would suggest you search the forum for WoW or World of Warcraft.  Or make another post using "World of Warcraft install problems" and re-post your error in that.  It might attract some forum users who have already gone through that on World of Warcraft.:)

Sorry I can't be anymore help - I know how to use Wine but I don't know squat of WoW and therefore can't duplicate your error to try to find a solution.:)

Good luck, and do me a favor and send me a private message on the forum when you get further on this so I can review what was needed - I like to learn!:)

---

### Post by Kinuxx on 2007-08-31
> **anewguy said:**
> Well,  you remember how I said I was not expert?:)  You've reached the end of knowledge here.  I would suggest you search the forum for WoW or World of Warcraft.  Or make another post using "World of Warcraft install problems" and re-post your error in that.  It might attract some forum users who have already gone through that on World of Warcraft.:)

Sorry I can't be anymore help - I know how to use Wine but I don't know squat of WoW and therefore can't duplicate your error to try to find a solution.:)

Good luck, and do me a favor and send me a private message on the forum when you get further on this so I can review what was needed - I like to learn!:)



Thank You very much for your time and help! :)

I must add though (before am off to do some errands):

3rd patch needed...

same message on install again "waiting to close files"

tried right clicking the 3rd patch and got a message saying you do not need this patch as you have a new version:lolflag:

This is crazy! lol!

All for a game! 

Thanks again for your help! Wouldnt of found out about the hidden files without you mentioning it! :)

And will do on the pm! :)

---

### Post by anewguy on 2007-08-31
You may want to talk with guy who made this post:

[http://ubuntuforums.org/showthread.php?t=539243]("http://ubuntuforums.org/showthread.php?t=539243")

:)

---

### Post by Kheldin on 2007-08-31
When you get the 'Waiting for files to close' thing, it's just not closing or exiting properly, wine that is.

Try going to System -> Administration -> System Monitor

and look under the processes tab for anything with wine. I had this exact problem during patching, what basically was happening to me was the patcher wasn't closing wine, and manually killing wine seemed to do the trick.

Since there were many patches and I got sick of it, I eventually searched the forums here and found a site that has all the stand-alone patches for wow. It's at
[http://www.wowwiki.com/Patch_mirrors]("http://www.wowwiki.com/Patch_mirrors")
and it works great, you won't get the 'Waiting ...' error with them as they are simply the stand-alone .exe files.

I believe why you get that error is related to the wow laucher.

---

### Post by anewguy on 2007-08-31
> **Kheldin said:**
> When you get the 'Waiting for files to close' thing, it's just not closing or exiting properly, wine that is.

Try going to System -> Administration -> System Monitor

and look under the processes tab for anything with wine. I had this exact problem during patching, what basically was happening to me was the patcher wasn't closing wine, and manually killing wine seemed to do the trick.

Since there were many patches and I got sick of it, I eventually searched the forums here and found a site that has all the stand-alone patches for wow. It's at
[http://www.wowwiki.com/Patch_mirrors]("http://www.wowwiki.com/Patch_mirrors")
and it works great, you won't get the 'Waiting ...' error with them as they are simply the stand-alone .exe files.

I believe why you get that error is related to the wow laucher.

Thanks for a fix!  I'll keep this in mind and point people to your post if I see it come again.

BTW - there were quite a few entries about this on the games forum.

Thanks again!:)

---

