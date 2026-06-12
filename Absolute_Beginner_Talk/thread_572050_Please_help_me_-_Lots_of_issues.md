---
title: "Please help me - Lots of issues"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by HackCoders on 2007-10-10
Wow I've been sitting on my computer literally all day trying to work this thing.

I've read so many articles on that grub error 21, all lead to the /boot/grub folder which I do not have for some reason, even via terminal it says file cannot be found..

So, I decided to do a fixmbr/boot via windows cd, and the piece of !@$# re-installed windows without formatting, because I had pressed enter at the main menu, then the R key..I didn't realize that..It should have at least asked for confirmation!, Luckily I made a backup of the registry..It's a .reg file though, so when I import it, it will probably tell me most of the things are in use and I cannot import at this time and what not :(

Ok so anyway, I've been trying to figure out this grub thing pretty much ALL day, all the files that the articles mention, I do not have in the system files!, no grub files, no config files..So I will get back into XP and delete the partition, then I will create new partition and start from there.

I had this error earlier today the first time I tried, so I didn't re-create the partition, I just did something to empty it then re-installed or something like that, I'm not sure, that would probably be why the grub files do not exist.

Anyway, off to the other computer, I must continue reinstalling windows, I have setup files for ALL my programs so backing up registry is no issue at all I guess, just kinda annoying I pressed the wrong key.

Also one other question, I have a crappy ATi X300 card, pretty old but I need drivers..or should I just leave it as stock in ubuntu?

My onboard sound works, I have a Netgear wireless card, where can I find drivers for them? Also what are the best codec packs? I have lots of movies and anime.

Also, is it possible to get viruses on linux? only reason I got it was to get rid of viruses...


Thanks for reading my long post, I hope someone decides to help me :)

This forum has really nice theme/formatting/mods

---

### Post by winsur8 on 2007-10-10
have you tried lilo?

---

### Post by rubbsdecvik on 2007-10-10
ok... well I can help with some of the less technical issues.  First... some of these things might need to go into separate threads.  It will help a lot for us.  That way you can get many people focusing on one problem instead of a few focusing on lots (trust me that's how it works... learned that the hard way).

I'm not sure about the partitions... I'm not sure about how vista works, so I'm gonna let someone else tell you about that.

Linux in general is very good about drivers.  You shouldn't need to get any drivers for your hardware, especially if it's been on the market for a while. Ubuntu should set up your graphics card and audio card just fine automatically.

as far as getting viruses on Linux... theoretically it is possible, but almost not really, and here is why: 
1) Linux doesn't have a big enough market share yet to really be targeted with desktop related viruses and spyware
2) (biggest reason) Since Linux is open source, there are thousands of pairs of eyes looking over the code and finding and fixing vulnerabilities.  Where it could take Windows 6 months to make a patch, Linux will have one in 6 hours.  This means that it's effectively a waste of time to create a virus for Linux.

I hope that helps somewhat for you.

---

### Post by swisscow on 2007-10-10
Can't help with Grub but I have the X300 as well. Just installed Gutsy (kubuntu) and it was a breeze setting up the fglrx drivers with that  - used the restricted drivers manager after the install and loading all updates - much easier than before.

I am also led  to believe that ATI will be issuing some MUCH improved drivers for their series of cards later on this month, supposedly good enough to run compiz etc without XGL. I'll believe it when I see it.

---

### Post by rubbsdecvik on 2007-10-10
PS... sorry missed a whole line.  

Your wireless card should be able to work... Mine is a belkin and it works fine.  If it doesn't work... post on here, and people will help you out.

Codex are pretty easy to figure out.  All you should have to do is try to double click on the file, and Ubuntu will ask you if you want to install the codec. You say yes, and away it goes to go get what you need.  

Hope that helps!

---

### Post by phidia on 2007-10-10
There are a lot of different questions there for sure...I'm not sure why there is/was no grub directory under /boot on your install. Did the install complete sucessfully? What version of ubuntu are you trying to install, and have you made sure the cd you burned is ok? You can check the cd before you install from the boot menu.  So after you make sure your cd is ok then you should be able to proceed with the installation. 
Briefly addressing your other questions: an ATI card could be made to work for 3D Acel you will want to look at the multimedia & video forum.
Wireless cards setup (usually through ndiswrapper) are covered in the networking and wireless section movie codecs would be covered in that section too.
Finally viri are possible in linux but relatively rare so far-also many say the damage they can do on a linux system is limited.

---

### Post by HackCoders on 2007-10-10
Ahh I see thanks for that

Very happy right now, somehow XP restored without deleting ANYTHING at all :D..

As for the one thing at a time, lets focus on the Error 21 thing please, that's the only thing I need right now..I'm about to create a new partition then do a full re-install of ubuntu.

What boot thing should I select, /usr, /boot, / or what?, I think I chose / last time.

winsur I haven't tried lilo, I don't know much at all about linux, just got my package in the mail today and thats why I've been wanting to install it, most of the computer-savvy people I know use linux :)

Still, so happy that it didn't delete any of my things or anything, thats great, it usually re-installs XP without formatting, but does a whole clean install and keeps the files I had under seperate folders and what not..

Thanks for the fast replies.

Lol a few replies while I type mine, I love this place ^_^


Edit: I ordered the 64bit from ubuntu, I think 2 of them, both disc's are fine.

I'll be back later, I'm about to go back and create a partition for ubuntu and try again

Before I go, which mounting point should I select? and should I make a 2GB linuxswap partition as well? (Don't know what that is).

---

### Post by rubbsdecvik on 2007-10-10
If you want to focus on just the grub issue I would suggest starting a new thread and title it something like grub error 21.  That will attract people who know what to do.

I know I don't know exactly what is going on, so that why it would probably be beneficial to start another thread.

Just a suggestion... if someone here already knows what to do, have at it!

---

### Post by HackCoders on 2007-10-10
OK I'll create a new thread, I'll re-write the specific issue..

I hope it's not against the rules or anything?

---

### Post by rubbsdecvik on 2007-10-10
as far as new partitions go do this instead:

erase all your partitions (except your windows one of course)

start the installer...and tell it to use the larges continuous free space.   It will set up the partitions for you!

---

### Post by HackCoders on 2007-10-10
Really? Last time I did that it deleted windows =\

Or I think I must of selected the one under it, doesn't it ask how much % to use? or did I do the wrong option.

Are you sure the continous space won't remove windows? Also, umm, will it take all the available space on the HDD?

---

### Post by phidia on 2007-10-10
you need to be very specific with what happens and with what your hadware setup is.
Error 21 is a disc/hard drive not found problem.
The thread [here]("http://ubuntuforums.org/showthread.php?t=62717") might help.

---

### Post by HackCoders on 2007-10-10
OK well I made a new thread.

As for this one, I got error 21 because as it stated, the files were not there. It was as if GRUB was not installed on my system at all, I don't know how setup did that, I guess I made an error when re-creating the partition or something, I did some weird things :S

---

### Post by rubbsdecvik on 2007-10-10
If you are careful not to delete any NTFS file systems, and you use the continuous free space, it should not delete your windows, nor take up all of your hard drive space.  The continuous free space just means the space that isn't being used bye some other partition.

If you delete the partitions that have / or /usr/ or /var/ or /home/ etc... you will be effectively deleting any Linux partition.  This will not touch your windows partition side.  

If you then use the continuous space option, you won't have to worry about grub... because it will do it all for you.

it won't take up the free space left over on your windows partition.  It will only use the "non partitioned" space that is left on your HD.

---

### Post by HackCoders on 2007-10-10
Oh I see what you mean, OK I'll give that a go in a few minutes :)

Thanks for all the help guys

---

### Post by rubbsdecvik on 2007-10-10
no problem... that is why we are here!

Don't worry I had similar questions when I first started.

---

### Post by HackCoders on 2007-10-10
yay I just searched for my wireless card and someone posted a little tutorial to get it working :)

---

### Post by rubbsdecvik on 2007-10-10
Good to hear... 

I knew there had to be something out there.  It's a fairly common piece of hardware.  

Let us know how the reinstall goes.

I think I'm heading to bed here (1am my time), but if anything others will help, or I can check up on you in the morning.

---

### Post by HackCoders on 2007-10-10
OK, I'm about to go ahead with the re-install

Thanks a lot for all the help :)

---

### Post by Martje_001 on 2007-10-10
For grub:
Boot up live-cd --> go to terminal:

sudo grub
> find /boot/grub/stage1
> root (hdx,x)
> setup (hdx)

hdx,x is what you get returned from 'find'. If find cannot find anything you have to do the partition 'work' yourself (firts hard disk = 0, first partition on harddisk = 0)

---

