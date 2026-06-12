---
title: "Locked out of Ubuntu Edgy"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by Gek.uk on 2007-03-13
Hello there!  Just thought I had to post now, as I have been trying to use Ubuntu for over 6 months, as it is by far and away the best distribution of linux I have tried.  I have tried a huge cross section of distributions over the years, as my trade is assembling and repairing PCs and I despise the monopoly abuse of Microsoft.  I am also an information systems graduate, and I do respect the rigour that goes into linux.  Ubuntu is the best chance that linux has of going mainstream.

For more than 6 months I have been using Ubuntu on my old laptop, which had been relegated to torrent duties.  It is a Compaq Evo N1015v.  For those that (quite reasonably) don't know what that means it is an ATI chipset based machine with a AMD Athlon 1500 XP cpu and 384 MB of DDR RAM and a 20 GB hard disc.  Nothing fancy compared to my tower, but more than enough for Azureus.

Anyway, tonight I have just had to reinstall a 2 month old installation of Edgy Ubuntu (instead of reinstalling normal Edgy I am trying XUbuntu Edgy) purely because I was locked out due to the claim that the disc was full.  The disc was not full.  I had over 8 GB of free disc space, and the machine was only used for torrents.  I had noticed this to a milder degree with my last installation (yes, in 6 months I have had to install more than once) when it claimed that root was full, even though when trying my absolute hardest to find what was clogging it I could not.  I searched here, tried everything I could imagine to sort it and drew a blank.  

This is a major thing, as one of the reasons I use Azureus is it's cross platform nature and rich feature set.  The reason I am only using linux lightly (even though the only game I play is Unreal Engine based and would run well on linux) is that most of my customers only use PCs for surfing, email, accounts, word processing, photos and downloading.  However, this sort of nonsense, i.e. getting locked out of your own login due to there being no space (when I know damn well there is plenty of disc space left) is the sort of thing that just will not fly with  a normal user.  I'm not a normal user, I have been professionally building and fixing and trouble shooting Windows based PCs for over 9 years, and I have been utterly unable to sort this.  Any chances I had of sorting it vanished when I was locked out of my own laptop as explained earlier.

I am certainly not pro MS, I have to deal with their bad engineering every day and I really want to switch more fully to Ubuntu (or a variant, my XUbuntu install has finished now, and it does seem snappier on the old laptop than Edgy did) but issues like making it so hard to even view what files you have or hiding directories by prefacing them with a . is just daft.  I only even knew about that . preface thing while searching for reasons why Azureus was not running well.  I did not find the answer on here, but I did find that installing Sun's Java made Azureus behave like it did on the laptop when the laptop was running Windows.  I know Java has been closed source, but that is changing as we speak, soon it will be open source, and all I can say is thank god.

I use many open source utilities on Windows, such as FireFox and OpenOffice, and I use opensource where this is reasonable or possible, but surely something is wrong when you use a Ubuntu PC for only torrenting, have 8 GB of disc free, and get locked out of your own installation because the root is apparently full?  If I hadn't used this excellent program:

[http://www.sentex.net/~mwandel/ftpdmin/](http://www.sentex.net/~mwandel/ftpdmin/)

as I'll admit Samba seemed a nightmare (don't laugh, I wonder why more leet Linux folks didn't think of just using FTP to transfer between platforms) to move downloaded data off to my windows tower, I might have lost quite a lot of data for no hardware fault and no user error.  

Please don't take this the wrong way, I am yearning for the time I don't have to deal with a £75 windows tax when I build a normal office machine where all the parts for the box only cost £225 retail.  But if Ubuntu can't handle a few months worth of torrenting without locking the user out, and even before this point, I have done disk analyser, found root was full yet I had 8-10 GB free on the disc, it's just not going to work with Joe Punter.  I've searched here a lot and tried everything to locate what was clogging the drive to no result.  

I really hope some of you excellent guys here will reply, because I haven't given up, I just need help and have not been able to find it here after months of silently trying to help myself.

Respect to all the guys that build Ubuntu and help out here.  If you want a superb game that runs quite happily on Linux using the Unreal Tournament 2004 engine, please check out the game I volunteer my free time to help (I run the public forum, beta test and write news for it) my name on there is also Gek, so feel free to drop by the forums if you have any problems.  As you can tell I'm no linux specialist, but we do have a quite a few lads there that use linux, and one of the key team guys uses mac and linux.  

[www.to-crossfire.net](www.to-crossfire.net)

It runs on Linux, Windows and Mac.  Our end is free, but as it is a modification, you do need a legit copy of Unreal Tournament 2004 to run it (only costs £5).  You won't be disappointed, the quality of our unpaid volunteer team puts a lot of "pro" game developers to shame.  For example, our game eats Counterstrike for breakfast.  :D  If you want a superior, semi realistic online shooter you could do a lot worse than check us out.  :)

Thanks, I really hope someone can help me with the few problems I have been having with Ubuntu.

---

### Post by lamalex on 2007-03-13
Samba is used for MUCH more than just file sharing. FTP file sharing will now allow for 1/3 of what samba can do.

as for your game eating cs for breakfast, sorry but nothing can ever touch CS 1.5.

---

### Post by Gek.uk on 2007-03-13
I'm well aware that Samba does more than just share files, but that is what the vast majority of people with a home network may want to do.  How about actually trying to help rather than attempting to be leet?  I just posted the quick and easy solution I had found that was not mentioned here at all, and incidentally uses a free and easy program.  

If you reckon the online shooter world stopped with CS 1.5, you're even more deluded than the chimps that think it ended with CS 1.6.  

Does your much loved CS run natively on linux?  No, it doesn't.  Whereas the game I help out with runs on linux, and even the previous version (to which my team makes the sequel) ran natively on linux too.  So go back to Philly mate if you just like to spam and not help.

By your post count in the short time you have been here, you do look like a bit of a spammer.  :(

---

### Post by Gek.uk on 2007-03-14
Bump!  Can anyone help me with this please?  :)

---

### Post by Gek.uk on 2007-03-29
Waited a couple of weeks now, can anyone help, please?  :(

---

### Post by Gek.uk on 2007-04-06
Ok, I installed the Xubuntu Feisty beta over 7 days ago, and I have been very happy with it.  But despite just using it for surfing with Firefox and torrenting with Azureus, I have yet again been locked out of my own installation.  This same thing happened with Ubuntu Edgy.  The exact error code when I try and login is this:

"GDM could not write to your authorization file.  This could mean that you are out of disk space or that your home directory could not be opened for writing.  In any case, it is not possible to log in.  Please contact your system administrator."

Could someone please tell me how I can fix this and prevent it from happening again, as I have at least 9 GB free.  Everything is stock, azureus installs where it defaults to and I tell torrents to save in the torrents folder in the the Azureus folder.  

Please show that you folks want to help, as I have been waiting over a month for some help, and the only person that has appeared is a useless spammer.  :(

---

### Post by Maestro23 on 2007-04-06
Just skimmed thru your situation.  I don't use Azurues anymore, but it seems that there was an option in it to pre-allocated the storage for torrents before they where complete.  Do you have this option enabled and do you have alot of torrents that are not complete? 

Again, I could be wrong its been a long time since I used Az. .I have just stumbled upon your thread and trying to help.

*Can you run and post output of:

> ls -la /home

---

### Post by Gek.uk on 2007-04-06
Hey, thanks so much for you help.  Please read my last post though, I can't login into XUbuntu (I've had this exact same thing with Ubuntu as well), I get the error message I posted above.  I have only 1 torrent that is not complete.  I can press Ctrl and F1 to get a terminal, but I can't do much from there.  Running your commmand doesn't seem to provide useful info:

[IMG]http://i26.photobucket.com/albums/c121/coastaluk/100_0407.jpg[/IMG]

I don't even know how to get to my azureus folder from here and try and delete some stuff.  :(

It's not good that it should be possible to be locked out of your PC this easily.  :(

I just want to get back into my Xubuntu installation. After I can get back in, I can worry about stopping this happening again.  It's bloody annoying, though.  This should not happen when you have over 9 GB free.  If someone could just tell me how to get to my Azureus folder via the terminal (it is in the default install location) I could at least try and delete some stuff.  I'm extra annoyed as there is over 7 GB of data that I really don't want to lose.

My main problem is not Azureus, but: how do I get into my Xubuntu installation when I have this error:

"GDM could not write to your authorization file. This could mean that you are out of disk space or that your home directory could not be opened for writing. In any case, it is not possible to log in. Please contact your system administrator."

---

### Post by Maestro23 on 2007-04-06
Where is the azureus folder?  /home?

** Hey man, check this thread: [http://ubuntuforums.org/showthread.php?t=395193&highlight=GDM+could+to+your+authorization+file](http://ubuntuforums.org/showthread.php?t=395193&highlight=GDM+could+to+your+authorization+file).

---

### Post by Gek.uk on 2007-04-06
Yeah, I've found my way to the Azureus folder by using ls -a (I frigging hate the way this OS hides stuff from you by default) but now I can't delete a file using the rm command.  I'm typing the file name in exactly as ls shows it but it's claiming it can't see the file.  Does Linux handle filenames with spaces differently to windows?    

Thanks for that link, I will try it, but I'm not confident.  

Trying now.  :)

Well, your link did not help, but deleting a large (4.5 GB) file in the \azureus\torrents folder did the trick.  Why do you think this happened though?  How can I avoid this problem in future?  It's caused me to reinstall ubuntu over 4 times now, and it undermines my trust, as how can I recommend this OS to my customers, if it will lock them out of their own machine for torrenting, when they have plenty of space left?  Either way Maestro, thank you so much for your help, it's much appreciated.  :)

The only way I could delete the file in the end was to type:

rm *.iso

That worked, would have been a nightmare if there had been more than 1 iso in the folder though.

Thanks again Maestro, I'm grateful for your help.  :)

---

### Post by Maestro23 on 2007-04-06
> **Gek.uk said:**
> Yeah, I've found my way to the Azureus folder by using ls -a (I frigging hate the way this OS hides stuff from you by default) but now I can't delete a file using the rm command.  I'm typing the file name in exactly as ls shows it but it's claiming it can't see the file.  Does Linux handle filenames with spaces differently to windows?    

Thanks for that link, I will try it, but I'm not confident.  

Trying now.  :)

Yeah, try enclosing the filename in quotes.  Ex: "my filename"

Where is the Az directory?  If it's anywhere besides /home, you need "sudo" in front of your command.

---

