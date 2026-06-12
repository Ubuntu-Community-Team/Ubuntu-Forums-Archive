---
title: "I don't know what to do."
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by illusionz on 2007-10-01
My Linux experiences haven't been that good.

I've tried Knoppix and Debian and all that. Then I've tried SuSe, and most recently I've installed Kubuntu.

I tried using Automatix to install things like Skype and whatnot, and I couldn't figure out why it wouldn't work.


Does anyone suggest anything I should try different this time?

I guess I didn't give it enough time and troubleshooting if I didn't get things working.

---

### Post by jfinkels on 2007-10-01
> **illusionz said:**
> My Linux experiences haven't been that good.

I've tried Knoppix and Debian and all that. Then I've tried SuSe, and most recently I've installed Kubuntu.

I tried using Automatix to install things like Skype and whatnot, and I couldn't figure out why it wouldn't work.


Does anyone suggest anything I should try different this time?

I guess I didn't give it enough time and troubleshooting if I didn't get things working.

Your patience is admirable! Keep it up, friend.

My suggestion is to NOT use Automatix (also, to use Ekiga, not Skype [https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype) ). Read the link in my signature if you need help on installing software. In general, the software you need to install will only be one short command away! For example, to install the flash plugin for firefox, simply type in the terminal:```
sudo aptitude install flashplugin-nonfree
```
Installing software this way makes it easier on you because you know how and where your software is installed.

In general, if a program fails to open for you, you should try to open it in a terminal, as you will get some sort of error message or, if the developers were nice, some sort of descriptive message on why the program fails. For example, to open "kate" from the terminal, type:```
kate
```

---

### Post by FranMichaels on 2007-10-01
> **illusionz said:**
> My Linux experiences haven't been that good.

I've tried Knoppix and Debian and all that. Then I've tried SuSe, and most recently I've installed Kubuntu.

I tried using Automatix to install things like Skype and whatnot, and I couldn't figure out why it wouldn't work.


Does anyone suggest anything I should try different this time?

I guess I didn't give it enough time and troubleshooting if I didn't get things working.

Do not blame yourself! It is the software that needs improvement. :) Don't use automatix as the other poster mentioned, as for skype (which is proprietary, so no one can fix issues but their company...), this forum has loads of how-tos. 

Anyway, I'm a Gnome lover, so I'd suggest trying plain old Ubuntu (I would wait a while actually, since Gutsy Gibbon, Ubuntu 7.10 will be out October 18th...) Has a lot of nice improvements I promise.

Don't give up. People on this forum are so friendly, someone will help you for sure.:KS

---

### Post by illusionz on 2007-10-01
> **jfinkels said:**
>  (also, to use Ekiga, not Skype [https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype) ).

Would that work with Skype?





I did Kubuntu because I was familiar with the Kde interface more then Gnome.

I dunno if I want to wait till the new version comes out, since I feel like playing around some more with it.


Thanks guys.

---

### Post by Scunizi on 2007-10-01
For Skype use this link.

[http://www.skype.com/download/skype/linux/](http://www.skype.com/download/skype/linux/)

Pick the version for Feisty Fawn and download it to your Desktop then double click it.  It should start to load then ask for your password.. at least in gnome it works in that order..  It's that easy.

---

### Post by Faud on 2007-10-01
> **illusionz said:**
> My Linux experiences haven't been that good.

I've tried Knoppix and Debian and all that. Then I've tried SuSe, and most recently I've installed Kubuntu.

I tried using Automatix to install things like Skype and whatnot, and I couldn't figure out why it wouldn't work.


Does anyone suggest anything I should try different this time?

I guess I didn't give it enough time and troubleshooting if I didn't get things working.

Is Skype your only problem ? What other things are you trying to install in Linxu and how are you trying to install them ? Are you using Automatix for everything ?
Everyone on the forums are great. If you list a specific thing then we can get started helping you through it.

---

### Post by illusionz on 2007-10-02
Well, I tried automatix, and when it didn't work, it kinda got me off on the wrong foot.

Then I tried to run stuff in wine. I'm pretty sure games like Unreal Tournament 2k4 won't run in Linux.

So until I can figure out how to play that, I doubt I'd stay on Linux.

---

### Post by hyper_ch on 2007-10-02
Medibuntu has Skype and my advice is not use Automatix.

[http://medibuntu.sos-sts.com/repository.php](http://medibuntu.sos-sts.com/repository.php)

---

### Post by metalpancake on 2007-10-02
maybe your problem has something to do with the fact that the Automatix server is down at the moment. I know I have this problem whenever I try to use it:(

---

### Post by Scunizi on 2007-10-02
If unreal tournament is the only thing holding you back.. DON'T WORRY..  :popcorn: UT2004 will run natively on Linux.. I run it on my Dapper System.. In fact, there are lots of threads on this forum on how to install (without wine) and fix issues that might appear.  

By the way, the game runs great on linux.

---

### Post by illusionz on 2007-10-02
Well, thats not the only thing.

I would have to look into installing uTorrent too, but I'm sure that wouldn't be much hard.


My other gripe was how I couldn't get NTFS to read/write, and get my two monitors to work. Thats ultimately why I switched back.


Really, other then graphical, is there any differences between kubuntu and ubuntu? Like od things run better on gnome versus Kde?


I guess I could find this somewhere on the internet myself, but its easier to ask people direct questions.

---

### Post by steve.horsley on 2007-10-02
> **illusionz said:**
> 
Then I tried to run stuff in wine. I'm pretty sure games like Unreal Tournament 2k4 won't run in Linux.

UT2004 runs natively in Linux, and I have spent much more of my life playing that than I should have done. That said, I prefer the original UT and have wasted even more of my life there.

---

### Post by Scunizi on 2007-10-02
There are lots of torrent applications available to suit your needs there.  As for dual monitor, it does work, and work well.  However, it's easier to start with one monitor on install then add the second.  Either way you're going to have to tweek /etc/X11/xorg.conf (the text file that tells the system about video hardware) or use a gui if it's available for your card... Nvidia works smoother in setting it up than Ati.  

Feisty has NTFS read/write capability but you have to install the right driver.  The new Gutsy coming out later this month may have a more intutive interface to get it working.. The other way to share data between the two systems is to create a partition formatted with vFat or Ext3 for transferring stuff.  There is a driver for windows to allow read/write capability to Ext3 as well.

As for the graphical interfaces, I like both.  I seem to be more productive in Gnome (ubuntu) vs KDE (Kubuntu).  I'm sure once I get use to KDE more I'll like that as much.  They are different some in how to tweek them and the nomenclature or acronyms (read vernacular) is different between the two when discussing certain things.  The good thing is that programs from one will run on the other.  The bad thing is if you're running Ubuntu (gnome) and want to run a KDE program inside of it, when you install it, it often pulls lots of dependancies with it.  That can be a factor of you're running on a small HD.  Otherwise, you can actually install one of them, then install the other on top.  When logging in you can "change Sessions" to pic the interface you want.  Pretty cool!

---

### Post by illusionz on 2007-10-02
Couple more things:

1. I saw that you could wave your window around, and it would wobble, and like there was a cube you could change desktops with. What was that called? I couldn't get that to install either.


2. Last time, I downloaded the 64bit version. There was some stuff that didn't work with it back then (I don't remember when I last had Feisty though). Could that be why Skype didn't work? Should I just go 32bit?

---

### Post by Scunizi on 2007-10-02
Yep.. being new at linux go for the 32 bit.  The cube thing is "compiz / Beryl".  It will only work if your video card is setup propertly with the opengl driver.  Nvidia drivers and Ati are listed in Synaptic.  But there is an "Activate Effects" button someplace in the Feisty menus.  I run Dapper 6.06 which is older and doesn't have that easy setup feature.  Remember that the fancy cube thing is in Alpha and can be somewhat unstable at times.  That means, some programs won't like it or it won't like some programs.  UT2004 typically likes to start in full screen mode, you might have to change that to startup windowed instead to get compiz/beryl to like it.

---

### Post by illusionz on 2007-10-02
Ah, it was called Xgl. It only runs on Kde, right?

---

### Post by Scunizi on 2007-10-02
no.. it runs on gnome and kde... xgl is just a part of what's needed for compiz/beryl

---

### Post by illusionz on 2007-10-02
Oh, alright, thanks.

One last thing before I install it again, Any major difference between Ext2 and 3?

---

### Post by Lord Illidan on 2007-10-02
I know one of the major differences lies in the fact that ext3 uses journaling, while ext2 either does not, or else doesn't do it well.
In case you're not sure what journaling is, supposed you're copying a file.
Then, suppose midway through the copy, your computer shuts off. A filesystem
with journaling would leave a copy of the file in tact before it would move
it completely. One without would leave you with not only a corrupt file, but also sometimes a corrupt directory.

---

### Post by voided3 on 2007-10-02
Use ext3 for your main file system. The only difference is that ext3 is journaled and ext2 is not. Journaling is considered to be a good thing to have as it increases the integrity of the file system since it logs changes made to it, so if the power were to go out while you were in the middle of something, for example, it would be less likely to be corrupted on the next boot.

---

### Post by voided3 on 2007-10-02
Lord Illidan beat me to it!

---

### Post by steve.horsley on 2007-10-02
Wobbly windows and other neat effects come with compiz. In Feisty, this needs enabling, in Gutsy it's enabled by default. Either way, you need 3D graphics acceleration. With ATI or Nvidia this involves installing proprietary drivers, but I installed Feisty on a PC with intel graphics last week and the wobbly windows worked out of the box, really slick. One up to intel, and I can't wait for them to come out with high performance cards that have OSS drivers.

---

### Post by illusionz on 2007-10-02
Well, I got everything setup right.

I dunno how I screwed up installing Skype, because it was easy.

But I wanted to install Pidgin, instead of Gaim. I uninstalled Gaim, and installed Pidgin. I didn't find it in the Internet section in Applications, so I opened it up with Terminal.

Is there a way I can get it to be under the internet section?



Also, I have a USB Headset and USB Speakers. I want to only use the headset for Skype, and the speakers for everything else. How could I do that?

---

### Post by jfinkels on 2007-10-02
> **illusionz said:**
> 
Is there a way I can get it to be under the internet section?

To edit the menu entries, open the Alacarte Menu Editor under "System > Preferences > Main Menu", or just open the program 'alacarte' using the terminal or the "Run Application..." dialog (press <Alt>+<F2>).

I'm glad you're giving us another chance! I think some of your problems stem from being accustomed to the "Windows way" of doing things. Linux is about freedom of choice, and there are countless ways of solving problems.

As for torrents, if you feel comfortable with the terminal (it's easy!), use 'rtorrent' (here's a howto: [http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/](http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/) ). As for GUI torrent clients, I prefer Transmission (download from here [http://transmission.m0k.org/](http://transmission.m0k.org/) ).

And as always, if you have any questions about anything, or if you think to yourself "there should be a better way to do this...", there is! Just come to the forums! And read and learn from sites like those to which I have linked in my signature.

---

### Post by illusionz on 2007-10-02
Gee, Thanks. This has to be the nicest forums I've been on in a while.

If I have any more questions, I'll just ask.

---

### Post by jfinkels on 2007-10-02
From [http://www.ubuntu.com/products/whatisubuntu](http://www.ubuntu.com/products/whatisubuntu) :
> 
**What does Ubuntu mean?**

Ubuntu is an African word meaning 'Humanity to others', or 'I am what I am because of who we all are'. The Ubuntu distribution brings the spirit of Ubuntu to the software world.


We're all in this together!

---

### Post by gordonh on 2007-10-02
> **steve.horsley said:**
> Wobbly windows and other neat effects come with compiz. In Feisty, this needs enabling, in Gutsy it's enabled by default. Either way, you need 3D graphics acceleration. With ATI or Nvidia this involves installing proprietary drivers, but I installed Feisty on a PC with intel graphics last week and the wobbly windows worked out of the box, really slick. One up to intel, and I can't wait for them to come out with high performance cards that have OSS drivers.

I'd have to add a caveat here.

The wobbly windows stuff in  Feisty is enabled in system>preferences>desktop effects.  It gives some sort of warning before it's enabled, but I'm the sort of bloke who answers "yes" to these sort of dialogues and lives with the results.

It stuffed up so many areas that I can't remember them all.  The only way I could get rid of it was by deleting the configuration files (I can't remember where they are, but I lost all my Evolution info as well)

I was minutes away from a complete reinstall when I found that solution.

BTW I'm IT literate and Ubuntu noob and these forums are excellent.

95% of the time I can find an answer to any question and the remaining 5% the excellent forum members will happily help.

Good work everyone

---

### Post by illusionz on 2007-10-02
I wanted to grab some themes. So there was this .deb installer. I clicked on it, it opened package installer. I installed it, it says it was finished, but where do I go from there?

( [http://cdn0.esnips.com/nsdoc/a2a539da-34b2-4f1b-a515-00e3c94232f0/?cdn=-699&action=forceDL](http://cdn0.esnips.com/nsdoc/a2a539da-34b2-4f1b-a515-00e3c94232f0/?cdn=-699&action=forceDL) )

---

### Post by Scunizi on 2007-10-03
Also don't forget the great resource of people on IRC.  Install Xchat from synaptic.  You'll want to go to the server list, scroll down to "freenode.net" and click edit.  Change it from irc.freenode.net (as the server) to chat.freenode.net using port 8001.  This will avoid the headache of getting banned until you make that change.  Once connected to the server there are lots of channels to join and "talk" on.

/join #ubuntu
/join #ubuntu-effects (for compiz stuff -  ie eyecandy)
/join #ubuntu-server
/join #kubuntu

Lots of nice people, usually, and fast answers to questions.. They might ask more questions than you think are neccessary but typically you'll get somewhere.

Rock-On!  :guitar:

---

### Post by chameleonkid on 2007-10-03
Although alot of people will tell you to use a torrent client native to linux, having done so I keep coming back to utorrent. For some reason it just destroys any competition provided by ktorrent or any other client. I run utorrent perfectly fine through wine, and achieve the same speeds as I did in windows. Wine, while not an emulator, is your friend.

---

### Post by jfinkels on 2007-10-03
> **illusionz said:**
> I wanted to grab some themes. So there was this .deb installer. I clicked on it, it opened package installer. I installed it, it says it was finished, but where do I go from there?

( [http://cdn0.esnips.com/nsdoc/a2a539da-34b2-4f1b-a515-00e3c94232f0/?cdn=-699&action=forceDL](http://cdn0.esnips.com/nsdoc/a2a539da-34b2-4f1b-a515-00e3c94232f0/?cdn=-699&action=forceDL) )

For future reference, make a new thread for each problem you are having, it allows people to see your problems more easily at a glance and it keeps problems simply sorted so that others can easily find answers to similar problems.

As for themes, you generally go to "System > Preferences > Theme" to manage your themes.

As for the .deb package, you can find out the contents of a .deb file by entering the command:```
dpkg -c *packagename*.deb
``` where *packagename*.deb is the name of the package.

---

### Post by illusionz on 2007-10-03
You know how many questions I've asked in here?

I just didn't want to makea  bunch of threads and clutter up everything.

---

### Post by jfinkels on 2007-10-04
> **illusionz said:**
> You know how many questions I've asked in here?

I just didn't want to makea  bunch of threads and clutter up everything.

Well, in MOST cases, it's best to make a new thread, because people view titles and say "Hey, I know how to answer that question".

In addition, you may follow to a certain extent the "Wikipedia is not paper" rule ([http://en.wikipedia.org/wiki/WP:NOTPAPER#Wikipedia_is_not_a_paper_encyclopedia](http://en.wikipedia.org/wiki/WP:NOTPAPER#Wikipedia_is_not_a_paper_encyclopedia)). This says, essentially, that since this forum is a digitized repository of information, you shouldn't be afraid to add to it.

---

### Post by illusionz on 2007-10-04
I guess. Just other forums I've been on just isn't as nice as this one, so they flame you for making new topics over and over.

Thanks for your help.

---

