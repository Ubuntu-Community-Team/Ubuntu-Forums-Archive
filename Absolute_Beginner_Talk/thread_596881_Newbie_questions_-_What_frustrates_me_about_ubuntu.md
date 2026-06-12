---
title: "Newbie questions - What frustrates me about ubuntu."
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by Stikky on 2007-10-30
Hey all.

I should probably start out by apologising because I am sure these questions have been raised before so if they have, I'm sorry, I did have a look around and couldnt find answers to most of them so I'm gonna ask them here and hope yuo all go easy on me cuz I'm a newbie :oops:

So the first OS I ever used was Windows 3.11 and then onto 95, 98, 2000 and eventually XP. Never made the leap to Vista because, well, my mum got it on a laptop and it drives me insane so yeah. Anyway! I have a pretty old laptop, it's a Sony VAIO, not sure of the model (it's at home, I'm at work) and it's about 4yrs old, I'd say. It was top of the line when it was new but now, not so much. From memory, I think it's a 1.8Ghz P4 and I'm not 100% sure on the RAM, maybe 512mb? I dunno. XP started to annoy me when I got a laptop, it is ALWAYS reminding me about stuff and the little popup thing in the bottom right hand corner never goes away so I decided to switch to Linux. Upon doing so, I encountered a few problems and I am hoping you guys can help... (Sorry for the essay, just thought I'd give some background :p)

1. The biggest problem for me may sound quite stupid to everyone else but this is the one I wanna fix the most.. When I turn my computer on, I get the VAIO sign, then it says "Starting up" or something and then the screen goes blank. For three whole minutes. Then, finally, the logon screen comes up and I can log in but I don't get any indication of what's going on, not even a pretty little boot screen that means nothing but assures me my computer is doing something!!?? Is this normal or is something wrong?? I really don't like it and it takes ages to set up. If I wanna do something quickly on my computer, I have to allow 5 minutes for it to boot up!! Annoying.

2. I can't figure out the programs. I get that I can install them through the Synaptic thing (is that what it's called?) and then I can see them in my applications but Ubuntu seems less than willing to use them. I installed VLC and I would like it to be my default player but I can't work out how! Any ideas? Also Azureus (spelling?) has screwed up, big time. I got it installed and opened but I downloaded a torrent file, couldnt work out how to get it to open with Azureus so I saved it on my desktop and opened it with Azureus and it said something about it not being a file and now it will not work at all, even after being reinstalled..

3. Where is everything?! I don't get the filesystem at all, is there any logic to it or will I have to just get used to that?

4. I don't like Pidgin, is there another messaging client I can use? Maybe one that lets me organise my MSN contacts into two groups: Online and Offline.

5. Command line confuses me, I thought this distribution was supposed to pretty much eliminate the terminal interaction but I still seem to have to use it and I just plain don't get it :(

That's all I can think of that I need help with (for now) but I have a few other things which were weird, thought I'd mention them, not that they can be fixed now..

1. The installation cleared my whole HD.. I had my HD partitioned already into two parts and one was empty (well, I had my videos on it but I moved them) and I couldnt just stick ubuntu on there? Why not?

2. I had to install it 4 times, in total, twice I got an error when installing (that's when I decided to format the whole HD) and twice I reinstalled it cuz it took so damn long to boot I thought it had not installed properly!! (Probably my fault)

3. The desktop effects that are supposed to be really cool and awesome are hard to find. Like REALLY hard. You get 3 options, they don't do much, and you have to install some other program (dont even know what, copied and pasted a command line thing from the net) to customise them, which was pretty disappointing.

I think that will do for now, that's a lot of text, I hope someone can be bothered reading it!! :p One more thing; that exposé program is cool, how it shows you all your desktops but I have got into the habit of using only one desktop, is there a program I can get (or an option I can enable) to get it to show all the programs in my current desktop? Like on a mac? That would be cool..

Thanks in advance guys, sorry for writing so much, I can't stop myself, you should hear me talk :p

Stikky

---

### Post by Crafty Kisses on 2007-10-30
Answer to your third question, the files usually are in ** /usr/bin**.

---

### Post by Stikky on 2007-10-30
> **Codename said:**
> Answer to your third question, the files usually are in ** /usr/bin**.

Thanks for your quick reply! Don't mean to sound like an idiot but what exactly does that mean? Is that the Linux equivalent of like **C:\** in Windows?? :oops:

---

### Post by Crafty Kisses on 2007-10-30
> **Stikky said:**
> Thanks for your quick reply! Don't mean to sound like an idiot but what exactly does that mean? Is that the Linux equivalent of like **C:\** in Windows?? :oops:

It's kind of like the Program Files for Ubuntu. :)

---

### Post by greenlegacy on 2007-10-30
Yet another answer to your third question--here is a graphical representation of [the linux file structure.]("http://bp3.blogger.com/_Vbsj-yhipTw/RvaiatPBPBI/AAAAAAAAABs/yjx3hPlEUNw/s1600-h/linux_file_structure.jpg")

As far as pidgin, you can hide your offline buddies by going to Buddies->Show then clicking the appropriate box.  Or if you want to sort your buddies into groups you can go to Buddies->Add Group, then you can click and drag them into the groups you want.

I know it may seem frustrating at first, but you will eventually get used to how things are done in linux.

---

### Post by Crafty Kisses on 2007-10-30
Answer to your fourth question, yes there are alternatives for example for MSN, there is aMSN, not sure about now, but there is still GAIM.

---

### Post by Nythain on 2007-10-30
1. is usually a grub resolution issue... can be fixed by adding teh appropriate vga=XXX to a certain line in your /boot/grub/menu.lst file... could probably get how by googling 'grub resolution' or 'ubuntu boot resolution' once you get the right vga value set, you should no longer have 'out of bounds' issues

2. im not sure how to help you here, i run kde and its menus are different, but somewhere there's a magical place that lets you set what programs get used to run certain files... maybe an ubuntu/gnome user can help with this one.

2b. with azureus and torrents... i believe you should be able to tell firefox (hopefully thats your browser, if nto im sure you can tell others also) to open a file with a certain program... azureus if installed via synaptic might be located in /usr/bin or just /bin... not sure, since i run rtorrent... but hey, its a point in the right direction

3. google 'linux file system' or 'linux file structure' or 'linux directory system/structure' and you will get a few good pages on explanations of where/how files are stored in a linux environment... usually brakes down like this

/ = root of teh system, consider it c:\ if you must
/bin = binaries... more importantly, system wide binaries... contains a large chuck of your systems 'executable' files
/boot = important files for booting teh system... grub is located here and is about the only thing you should ever have to mess with, if that even
/dev = not much help here... i never go there... nothing i need there
/etc = generally configuration files for installed programs and your operating system are located here... this is probably the most comon place i frequent outside of my home directory
/home = users home directories located here... consider it 'My Documents' or similar if you must... basically anything thats yours is here... and its the only place you have access to without root permissions
/initrid = see dev... once again, nothing i really need there
/lib = storage of libraries... sort of like dll files if you must... not the most use for average users, though if you get into things, there's a bit of stuff here that could require tweaking over time
/media and /mnt = mount points... for things like cdroms, floppies, other hard drives... you name it... if its not part of your base system, chances are ubuntu mounts it in one of these two places unless you tell it otherwise (google fstab for more info on mounting things)
/opt and /proc = once again, couldnt really explain it, because i dont go there
/root = root user's home folder so to say... not to important since root = bad
/sbin = more binaries and other things
halb halb halb... to much typing, i recomend the google approach

4. there are many other chat clients... i personally use a console ncurses based centericq... kde users get the joy of kopete, not sure how well it runs under gnome, though im sure its possible... google linux chat client and you will get a few

5. linux will always involve command line interaction... at the bare minimum it shouldnt confuse you to much, especiall if you come from 3.x windows, with its heavy reliance on DOS... easy to navigate, and manipulate really... you could google 'linux bash commands' to get a few good sites that list all the possibilities... but you dont have to interact that much with console shells in linux really... and what you do have to do, you can usually get copy/paste directions on these forums... though im against the copy/paste approach, you learn nothing, and there's a great chance for syntax failure... but it gets teh job done

on other issues

if you pay attention during installation you actually have great controll over formating/creating partitions and where to mount them... though a clean hard drive wipe is a great start for a new user

On multiple attempts at installation... for future reference, i would recomend downloaing a copy of the 'alternate install' iso, and burn at SLOWEST SPEED POSSIBLE... and get them via torrent if possible... all of those things can reduce errors during installation exponentially

desktop effects are over rated, after a month the flare of flaming windows fades and most users end up disabling most effects... but if you really want great 'desktop effects' you should get alittle more experience under your belt and look into compiz fusion

hope any or all of this helped, its the best i got right now... later

---

### Post by Crafty Kisses on 2007-10-30
Ubuntu takes time to get used to, so be patient. :KS

---

### Post by Stikky on 2007-10-30
Thanks guys! That aMSN program looks good, Codename, I will definately be giving that a try tonight. I can't get the whole groups thing, it just annoys me, I dunno why, I guess I am still stuck in my was from back when MSN only had the option to group by online/offline and I like that now. It's put my contacts in two groups called "Contacts" and "Individuals". Haha.

That picture was useful, greenlegacy, I should keep that somewhere I can see it :p It doesnt seem so complicated when you see it like that and now I know which files I shouldnt mess with!!

---

### Post by z-bot on 2007-10-30
> 1. The biggest problem for me may sound quite stupid to everyone else but this is the one I wanna fix the most.. When I turn my computer on, I get the VAIO sign, then it says "Starting up" or something and then the screen goes blank. For three whole minutes. Then, finally, the logon screen comes up and I can log in but I don't get any indication of what's going on, not even a pretty little boot screen that means nothing but assures me my computer is doing something!!?? Is this normal or is something wrong?? I really don't like it and it takes ages to set up. If I wanna do something quickly on my computer, I have to allow 5 minutes for it to boot up!! Annoying.

You can check what's actually happening on one of the terminals... Press CTRL + ALT + 'FN'    where 'FN' is one of your F1 through F6 keys. (you can try each one to find where the booting up is taking place.

> 2. I can't figure out the programs. I get that I can install them through the Synaptic thing (is that what it's called?) and then I can see them in my applications but Ubuntu seems less than willing to use them. I installed VLC and I would like it to be my default player but I can't work out how! Any ideas? Also Azureus (spelling?) has screwed up, big time. I got it installed and opened but I downloaded a torrent file, couldnt work out how to get it to open with Azureus so I saved it on my desktop and opened it with Azureus and it said something about it not being a file and now it will not work at all, even after being reinstalled..

Not sure what the problem(s) is(are) here.  Just right click the file, go to properties, then go to the "Open With" tab, then add/remove/select the program with which you want to open the file.

> 
3. Where is everything?! I don't get the filesystem at all, is there any logic to it or will I have to just get used to that?


I found this to be a problem as well, don't know if it's fixed under the newest release.  The fix I did was to add a file browser shortcut to one of the panels (as the file browser app is not under applications). This is straight forward.

> 
4. I don't like Pidgin, is there another messaging client I can use? Maybe one that lets me organise my MSN contacts into two groups: Online and Offline.

aMSN.

> 5. Command line confuses me, I thought this distribution was supposed to pretty much eliminate the terminal interaction but I still seem to have to use it and I just plain don't get it

You really do not have to use the terminal at all if you know what you are doing.  If you ask us how to do the equivalent of a terminal "process" using the GUI tools, we'll be happy to help you.

> 1. The installation cleared my whole HD.. I had my HD partitioned already into two parts and one was empty (well, I had my videos on it but I moved them) and I couldnt just stick ubuntu on there? Why not?

Probably because the format of the disk was not for linux (maybe it was partitioned under windoze(?) )

> 2. I had to install it 4 times, in total, twice I got an error when installing (that's when I decided to format the whole HD) and twice I reinstalled it cuz it took so damn long to boot I thought it had not installed properly!! (Probably my fault)
Probably wrong format's fault :)

> 3. The desktop effects that are supposed to be really cool and awesome are hard to find. Like REALLY hard. You get 3 options, they don't do much, and you have to install some other program (dont even know what, copied and pasted a command line thing from the net) to customise them, which was pretty disappointing.

Again, everything that commands do can be achieved by GUI (almost).  The effects are awesome indeed.  Though to get them to work, your video card must be properly configured.  The effects are super easy to get going, the video card might be a bit of a challenge.

> 
I think that will do for now, that's a lot of text, I hope someone can be bothered reading it!! One more thing; that exposé program is cool, how it shows you all your desktops but I have got into the habit of using only one desktop, is there a program I can get (or an option I can enable) to get it to show all the programs in my current desktop? Like on a mac? That would be cool..

Don't know what you mean here...

Cheers,
z-bot

---

### Post by Maestro23 on 2007-10-30
> **Codename said:**
> Ubuntu takes time to get used too, so be patient. :KS

Yep.:)

---

### Post by Stikky on 2007-10-30
> **z-bot said:**
> You can check what's actually happening on one of the terminals... Press CTRL + ALT + 'FN'    where 'FN' is one of your F1 through F6 keys. (you can try each one to find where the booting up is taking place.

Thanks, I'll try that but I might try that "grub" thing Nythain was talking about cuz I like the little boot screens that look like it's doing something..

> Not sure what the problem(s) is(are) here.  Just right click the file, go to properties, then go to the "Open With" tab, then add/remove/select the program with which you want to open the file.

Well the problem is that I can't figure out where the problems are stored!! Like I said, I am so used to the Windows file system that if it's not a .exe file in C:\Program Files\Azureus then I have no hope of finding it!!

> You really do not have to use the terminal at all if you know what you are doing.  If you ask us how to do the equivalent of a terminal "process" using the GUI tools, we'll be happy to help you.

Thanks for the offer, I suppose I was just a little disappointed that I thought this was supposed to be a competitor for like OSX and XP but I have been using XP for ever and never had to use the command line, really.. I was only a kid when I used 3.x so I have forgotten most (read:all) of the DOS commands my dad used to do! Haha.

> Again, everything that commands do can be achieved by GUI (almost).  The effects are awesome indeed.  Though to get them to work, your video card must be properly configured.  The effects are super easy to get going, the video card might be a bit of a challenge.

Yeah, my video card is not working, I'm sure. I'm already sick of most of the visual effects (mainly cuz I couldnt get them to work) but Wobbly Windows is pretty damn cool. Also, as to what I am refering to, I mean this:

[IMG]http://media.arstechnica.com/reviews/os/pretty-vista.media/expose_screenshot.jpg[/IMG]

You press a button in OSX (my friend showed me on his Macbook) and it opens all your minimised windows and shows you them on the screen so you can select one which it then maximises! It's really useful and ubuntu kind of does it but only with the desktops, as far as I can work out..

Thanks again for all your quick replies and help, everyone! I heard the Linux community was helpful but I wasnt expecting such a great response so thanks!! :)

---

### Post by Crafty Kisses on 2007-10-30
> **Stikky said:**
> Thanks, I'll try that but I might try that "grub" thing Nythain was talking about cuz I like the little boot screens that look like it's doing something..



Well the problem is that I can't figure out where the problems are stored!! Like I said, I am so used to the Windows file system that if it's not a .exe file in C:\Program Files\Azureus then I have no hope of finding it!!



Thanks for the offer, I suppose I was just a little disappointed that I thought this was supposed to be a competitor for like OSX and XP but I have been using XP for ever and never had to use the command line, really.. I was only a kid when I used 3.x so I have forgotten most (read:all) of the DOS commands my dad used to do! Haha.

Yeah, my video card is not working, I'm sure. I'm already sick of most of the visual effects (mainly cuz I couldnt get them to work) but Wobbly Windows is pretty damn cool. Also, as to what I am refering to, I mean this:

[IMG]http://media.arstechnica.com/reviews/os/pretty-vista.media/expose_screenshot.jpg[/IMG]

You press a button in OSX (my friend showed me on his Macbook) and it opens all your minimised windows and shows you them on the screen so you can select one which it then maximises! It's really useful and ubuntu kind of does it but only with the desktops, as far as I can work out..

Thanks again for all your quick replies and help, everyone! I heard the Linux community was helpful but I wasnt expecting such a great response so thanks!! :)
That's pretty cool. :)

---

### Post by devilears on 2007-10-30
1. Try these links for your VIAO:
[http://www.google.co.za/search?q=Sony+VAIO%2Bubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.co.za/search?q=Sony+VAIO%2Bubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)

2. Cant help you there.

3. [http://www.ee.surrey.ac.uk/Teaching/Unix/](http://www.ee.surrey.ac.uk/Teaching/Unix/) and [http://www.tuxfiles.org/](http://www.tuxfiles.org/)

4. GAIM works well but personally i use gmail's built-in client.

5. command line? what did you need it for? most probably there is a GUI for what you want to do. anyway, here are some references: [http://www.unixguide.net/linux/linuxshortcuts.shtml](http://www.unixguide.net/linux/linuxshortcuts.shtml)  and [http://linux.about.com/library/cmd/blcmdl_1x.htm](http://linux.about.com/library/cmd/blcmdl_1x.htm) and [http://www.linuxcommand.org/learning_the_shell.php](http://www.linuxcommand.org/learning_the_shell.php)

6. Ubunto cleared your HD? I suspect that during the install, you probably left the "use entire disk" option ticked...

7. Being a fresh Windows convertee, i would suggest starting off with KDE instead of Gnome as it more closely mimics Windows. in other words load Kubuntu instead of Ubuntu.

6.

---

### Post by katch22 on 2007-10-30
> **Stikky said:**
> 
 XP started to annoy me when I got a laptop, it is ALWAYS reminding me about stuff and the little popup thing in the bottom right hand corner never goes away so I decided to switch to Linux. 

I'm really sorry if this is offensive, but if you weren't able to figure out how to get XP to stop always reminding you about stuff and how to get rid of the "popup thing in the bottom right hand corner" maybe Linux is not the best choice for you.

> 
3. Where is everything?! I don't get the filesystem at all, is there any logic to it or will I have to just get used to that?

There is a lot of logic to it and it is very easy to find out all about it, all it takes is a quick search and you will numerous guides online to how the linux file system is organized.

> 
4. I don't like Pidgin, is there another messaging client I can use? Maybe one that lets me organise my MSN contacts into two groups: Online and Offline.

You can organize your messenger contacts within Pidgin, just play with the settings.

> 
5. Command line confuses me, I thought this distribution was supposed to pretty much eliminate the terminal interaction but I still seem to have to use it and I just plain don't get it

Command will always be present in linux based os. This is a very good thing because it gives you complete control. There is a lot to learn and it takes a little practice but it's really quite fun and well worth the effort.


Again, I'm sorry if this message is rude and makes me sound like an *******. However, it just seems to me that there is so much time wasted in the forums by people who refuse to put forth the littlest bit of effort. Just experiment and search these forums thoroughly and if you don't find what you want here then search the web. If you still haven't found answer to your question, *then* post a message.

---

### Post by Stikky on 2007-10-30
> **katch22 said:**
> I'm really sorry if this is offensive, but if you weren't able to figure out how to get XP to stop always reminding you about stuff and how to get rid of the "popup thing in the bottom right hand corner" maybe Linux is not the best choice for you.

I'm not sure what you're getting at here, are you suggesting that Linux is not for me because I don't like Windows? I didnt like Windows, so I switched to another OS. Of course, I was exaggeating a little about the little popups in the right hand corner and I'm sure you can stop them but they were so unnecessary. Every time i logged onto my computer, it would tell me the status of my battery, that there were new updates to install, I had unused icons on my desktop, my firewall was off, my virus definitions needed updating, my wireless network was available, my wireless network was connected, my wireless network was disconnected, there were multiple wireless networks and it didnt know which one it wanted, unused icons were being hidden, blah blah blah, I just got sick of it! I didnt need to be reminded a million times a second what my computer was doing, I am physically capable of checking.

> There is a lot of logic to it and it is very easy to find out all about it, all it takes is a quick search and you will numerous guides online to how the linux file system is organized.

Yes, I am aware of that now but I'm sure you can see, as someone who has never used Linux before (really) and has always been used to the Windows file system, it's less than intuitive, especially since nothing is what it says it is.. /bin is not where I put my rubbish, /etc could be ANYTHING and /lib is pretty general too so don't act like I'm an idiot cuz I didnt understand it immediately, if you'd used that file system for 10+ yrs then you'd have trouble adjusting to the C:\ stuff in Windows which is like second nature to me.

> You can organize your messenger contacts within Pidgin, just play with the settings.

I have played with the settings, I just want Online/Offline, that's all, none of this groups and tricky stuff, just online contacts, offline contacts.. Pidgin can't do that, apparently, but people have pointed me towards aMSN which I wil download tonight.

> Command will always be present in linux based os. This is a very good thing because it gives you complete control. There is a lot to learn and it takes a little practice but it's really quite fun and well worth the effort.

Well maybe I will have to get used to it then but it was my understanding that *this* distribution is supposed to be a user friendly GUI Vista/XP/OSX competitor and, as such, should have minimum command line interaction.. I've said it before and I'll no doubt say it again, there are a hundred thousand Linux distributions for the guy with a degree in computer science, I thought Ubuntu was supposed to be the one for us regular people who just wanna use their computers!

> Again, I'm sorry if this message is rude and makes me sound like an *******. However, it just seems to me that there is so much time wasted in the forums by people who refuse to put forth the littlest bit of effort. Just experiment and search these forums thoroughly and if you don't find what you want here then search the web. If you still haven't found answer to your question, *then* post a message.

It's ok, I'm sorry if *this* post made me sound like an "*******" but I felt a compulsion to defend myself. I have googled most of these problems, especially the boot screen one, with no real success at all, I still dont know what to do about that. I'm not sure how much effort you want me to put in but since the forum is called "Absoloute Beginner Talk" perhaps you should expect a few stupid questions?

---

### Post by hyper_ch on 2007-10-30
> **Stikky said:**
> Well the problem is that I can't figure out where the problems are stored!! Like I said, I am so used to the Windows file system that if it's not a .exe file in C:\Program Files\Azureus then I have no hope of finding it!!
Programs installed are normally just called by there program name... no need to "find" as it is in the normal search paths. So if you want to run azureus, then open a terminal, enter "azureus", press enter and it will run... same goes for selecting the "Open With"... you don't have to browse to the binary file, you just enter it's name (ok, VLC is a bit different, the name of the binary there isn't just vlc....)


> **Stikky said:**
> Thanks for the offer, I suppose I was just a little disappointed that I thought this was supposed to be a competitor for like OSX and XP but I have been using XP for ever and never had to use the command line, really.. I was only a kid when I used 3.x so I have forgotten most (read:all) of the DOS commands my dad used to do! Haha.
You've heard about that exciting new Windows Vista feature called "POWER SHELL"? So much for the "shell is not needed"-attitude... once you get the hang of the shell you'll do a lot in it as it is just a lot more efficient. Linux gives you the tools and options to use the operating system at maximum efficiency ;) and it is a competitor. Only because M$ has made you think shell is not needed doesn't mean it's actually true (why else would they introduce the power shell as exciting new feature?)

> **Stikky said:**
> Yeah, my video card is not working, I'm sure. I'm already sick of most of the visual effects (mainly cuz I couldnt get them to work) but Wobbly Windows is pretty damn cool. Also, as to what I am refering to, I mean this:
Open Synaptic, search for "compiz" and install the compiz settings manager. Once done, you'll have a new entry in your system preferences. There you can activate the more advanced effects.

---

### Post by justsomedude on 2007-10-30
> Yeah, my video card is not working, I'm sure. I'm already sick of most of the visual effects (mainly cuz I couldnt get them to work) but Wobbly Windows is pretty damn cool. Also, as to what I am refering to, I mean this:

You press a button in OSX (my friend showed me on his Macbook) and it opens all your minimised windows and shows you them on the screen so you can select one which it then maximises! It's really useful and ubuntu kind of does it but only with the desktops, as far as I can work out..

[IMG]http://i20.tinypic.com/2ik5rb5.jpg[/IMG]

Install CCSM. Enable Scale. Enable Scale Addons if you wish.

---

### Post by hyper_ch on 2007-10-30
> **Stikky said:**
> I'm not sure what you're getting at here, are you suggesting that Linux is not for me because I don't like Windows? 
I guess he suggested that but Linux is for everyone who is not afraid to think and learn ;)

> **Stikky said:**
> Yes, I am aware of that now but I'm sure you can see, as someone who has never used Linux before (really) and has always been used to the Windows file system, it's less than intuitive, especially since nothing is what it says it is.. 
I disagree... why is it less intuitive? Since you said you had Win95 so you have 12 years of experience and learning... that doesn't make windows more intuitive... you just know your way around because you learned so much over time ;)

> **Stikky said:**
> Well maybe I will have to get used to it then but it was my understanding that *this* distribution is supposed to be a user friendly GUI Vista/XP/OSX competitor and, as such, should have minimum command line interaction.. 
User-friendlyness and familiarity are two different things. This distro is very user friendly and it is a competitor to Vista/XP/OSX... just if you refuse to learn or are afraid of new approaches then it's not for you. Have a read here:  [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by Stikky on 2007-10-30
> **justsomedude said:**
> Install CCSM. Enable Scale. Enable Scale Addons if you wish.

Thanks, I'll give that a go.

> **hyper_ch said:**
> I disagree... why is it less intuitive? Since you said you had Win95 so you have 12 years of experience and learning... that doesn't make windows more intuitive... you just know your way around because you learned so much over time ;)

I should probably have phrased that better, let me explain what I meant.. I didnt mean the Linux file system is crap or less intuitive than the Windows system, I'm sure it is intuitive, I was just saying that it *seems* unintuitive to me. I seem to struggle a lot with new file systems, I just don't get them, probably because I have been using Windows for ever so yeah, I wasnt knocking the file system, I was explaining that I don't really undertand it yet. Like you said, if I'd been using it for 12 or more years, it would be second nature, I havent spent enough time with it to learn it yet..

> User-friendlyness and familiarity are two different things. This distro is very user friendly and it is a competitor to Vista/XP/OSX...

Yeah, I know that they're different but that's not to say they arent related. Windows is very user friendly to me in the sense that I can open up an XP computer and I know what I'm doing straight away. I know how to install stuff, I know how to find files and all that kinda stuff. Linux, I'm sure, would be just as easy if I'd been using that from the begining but I havent, and neither have most people. I think Ubuntu's target market is peolpe switching from XP more than anything so I think they should be trying to make it easy for them, that's all.. Just my opinion..

---

### Post by CaptainInsaneO on 2007-10-30
You needn't worry about not understanding Ubuntu (or Linux in general). I come from the same background as you - I've been using Windows since 95 and just recently made the switch to Ubuntu earlier this year and already I feel more comfortable in Linux than windows.

I haven't booted windows in months!

Welcome to the community. :)

---

### Post by carlosjuero on 2007-10-30
Yep - Linux has a learning curve; Those of us who have been with Windows since forever have a slightly different learning curve - namely, we have to get out of the mindset that everything has to be 'dumbed down' to the lowest denominator (no offense intended - its just how MS has made their OS's). The file system structure is a heck of a different beast, but in the long run it ends up being intuitive (everything has its place.. literally. Whereas in Windows things would end up all over the place :/) - some of the Linux file system items can have direct parallels drawn to Windows (at least those with the NTFS system - if you ever watch a Windows NT/2k/XP/Vista machine boot in safe mode you will see things like \Device\Hardisk(0)\System Volume\etc etc - it is like NTFS is trying to use a pseudo *nix backend :)).

The command line, while not 100% necessary with newer linux distros, actually allows for alot more flexibility and control over the operating system - I mean, could you recompile your video drivers in Windows for better performance? (just an example, the newer Linux video drivers are suprisingly mature compared to a year ago). I started out with Tandy DOS myself (On my honkin Tandy 1000HX with 640k RAM and 2 3.5" LD Floppie drives!) and learned the DOS command line in and out before moving up to Windows 3.1 - I used the command line consistantly all the way up to Windows XP.

Don't worry OP - you will get the hang of it and wonder why you ever used the MS operating systems in the first place :)

---

### Post by katch22 on 2007-10-30
> **Stikky said:**
> 
It's ok, I'm sorry if *this* post made me sound like an "*******" but I felt a compulsion to defend myself. I have googled most of these problems, especially the boot screen one, with no real success at all, I still dont know what to do about that. I'm not sure how much effort you want me to put in but since the forum is called "Absoloute Beginner Talk" perhaps you should expect a few stupid questions?

It doesn't really make you sound like an *******, and you definitely have every right to defend yourself. I was a little tipsy when I made my post and didn't take the fact that this is "Absoloute Beginner Talk" into consideration, so again I apologize. :)

---

### Post by Stikky on 2007-10-30
Rightyo, I'm back again!! I don't have internet at my new place yet so I can only post at work, which is less than ideal but oh well, what can ya do? :p

Just thought I'd update, in case anyone is wondering where I got with my few issues.. The boot screen one, I havent fixed that yet, it's still blank for some reason and I couldnt find a decent tutorial on how to do the "grub" thing mentioned before but if I'm honest, I didnt look very hard cuz I was busy! I did, however, try pressing "Ctrl+Alt+F1" and it came up with what it was doing instead of a blank page which was pretty cool, can I make it do that by default? Also, instead of taking 3 minutes to load, it took like 1 minute, which is much more acceptable! Anyone know why that might be?

Obviously, with no internet, I didnt get a chance to do much else but I thought this was quite an interesting development.. I also used the comand line a little bit (I know, I know, I was stubbourn but if I dont try new things I'll never learn) and it's not THAT complicated.. I managed to work out a few things, my memory sucks though so I can't remember what the commands mean.. I'll get there.

The file system is kind of making sense to me now, too, but I still can't remember where the program files are (I installed a couple of programs and then couldnt find them, where do they go by default?) but I kind of managed to work it out. I was using a live cd for something and I managed to find my desktop and work out that it was like "/mnt/hda1/home/....." etc but again, I can't remember what all the files mean :p

Anyway, that's the status at the moment, just thought I'd update in case anyone's interested. If anyone could shed some light on why my computer would boot so much quicker when I pressed "Ctrl + Alt + F1"? That was weird.

Thanks guys!

P.s. katch22, no worries mate, sorry I kinda snapped back at you a little :)

---

### Post by nutunbuntu on 2007-10-30
Wow this sounds like a mirror of my OS life for the past few days.... Thought I had partitioned for both XP and ubuntu and wound up with ubuntu only..

Used Windows back to 3.1 and even have some machine and gray?? background.. I think that is what it was called...

The OS @ work is SUSE, so I thought I would delve into the Linux world @ home, but didn't think I would be thrust into it being the only OS I had... That being said, I'm for the Penguin and all for dumping M$... Just have to figure it all out... And I will...

Will try to do some searching b4 I ask my normal dumb @ss questions...

---

### Post by hyper_ch on 2007-10-31
You don't have to remember where program files go. You just run them by entering the program's name in the command line terminal (if it's a terminal based one).

e.g. top / htop are programs that let you see what processes are running, how much cpu/ram the use etc....
top is installed by default, htop isn't. For installing htop you can use the cli
```

sudo apt-get install htop

```

And then you run htop by entering in the cli:
```

htop

```

You can then exit it by pressing "q"

If it's a graphical program like firefox you just start it with the command "firefox"

---

### Post by Jaco Du Toit on 2007-10-31
Regarding the boot issue where the screen is blank, I think it might be related to the splash screen being turned on and perhaps not compatible with your hardware. To test this theory you can turn it off by editing a file located at:
/boot/grub/menu.lst

To edit this file from the Desktop, press ALT-F2
This should bring up the linux equivalent of the RUN command in windows.
Enter the following command:

gksudo gedit /boot/grub/menu.lst

It should prompt you for your password (because you are editing a privileged file) and then bring up a text editor with the file loaded.
Now search for a line containing the word defoptions=
Should look something like this:

# defoptions=quiet splash

change it to
# defoptions=quiet nosplash

If you have other options listed there, retain them. Basically just change the word splash to nosplash. 

Anyways, after doing that, save the file
Then open terminal (Click Applications->Accessories->Terminal) and enter:
sudo update-grub

I assume you could do the above command with ALT-F2 and gksudo update-grub but I like to see some output. ;-)

Finally, restart to test new boot configuration.

Hope it helps.

---

### Post by macogw on 2007-10-31
> **Stikky said:**
> 
Yes, I am aware of that now but I'm sure you can see, as someone who has never used Linux before (really) and has always been used to the Windows file system, it's less than intuitive, especially since nothing is what it says it is.. /bin is not where I put my rubbish, /etc could be ANYTHING and /lib is pretty general too so don't act like I'm an idiot cuz I didnt understand it immediately, if you'd used that file system for 10+ yrs then you'd have trouble adjusting to the C:\ stuff in Windows which is like second nature to me.

bin is short for **bin**aries
lib is short for **lib**raries
etc is for assorted configuration files
usr is for **us**e**r**space (as in, not the things the very deep down parts of the OS need to keep running) programs
dev is short for **dev**ices
tmp is short for **t**e**mp**orary files
opt is for **opt**ional extra programs
any path with "local" in it is for locally-compiled programs
var is for **var**iably-sized log files
mnt is for **m**ou**nt**ed partitions/drives
srv is for if you're running a **s**e**rv**er
proc is for **proc**ess information for the deep down parts of the OS

Oh, to find out what a command does and what its options are, use "man <command>" so if you want to know how apt-get can be used, run "man apt-get"

---

### Post by diom on 2007-10-31
Hey Stikky.

Was the same as you about 6 months ago. Ubuntu is well worth it. Different systems are like different languages, the more exposure to different ones that you get, the more adaptable you beome. 

As for the long boot up time and lack of the progress bar, I had that problem too, but I followed the solution as posted here by Jaco Du Toit and now it works and the boot up time is much improved.

---

### Post by acl123 on 2007-10-31
> **macogw said:**
> bin is short for **bin**aries
lib is short for **lib**raries
etc is for assorted configuration files
usr is for **us**e**r**space (as in, not the things the very deep down parts of the OS need to keep running) programs
dev is short for **dev**ices
tmp is short for **t**e**mp**orary files
opt is for **opt**ional extra programs
any path with "local" in it is for locally-compiled programs
var is for **var**iably-sized log files
mnt is for **m**ou**nt**ed partitions/drives
srv is for if you're running a **s**e**rv**er
proc is for **proc**ess information for the deep down parts of the OS



I thought I would expand this post and hopefully make it a bit simpler for newbies, because beginners probably won't understand a lot of the terms like 'binaries' or 'locally-compiled'.
I'm a relative newbie at linux, although I have lots of Windows experience, but I still feel uncomfortable around a lot of these sort of words.
Please let me know if any of the following is wrong.


binaries = programs (in Windows these are .exe files). Fundamental linux programs like *grep* and *ls* end up in /bin... the majority of other programs end up in /usr/bin or /usr/games, or sometimes /usr/local/bin

libraries = libraries of code that programs share amongst each other. Unless you are a programmer you don't have to worry about these - just watch them get magically updated.

devices = computer hardware

host = a computer on a network... although if you're computer isn't on a network it might still be considered a host... so you can basically think host = computer

local = On your computer. If you are on a network, other computers are "remote". On a network, some folders, such as /usr, could actually be "remotely" located. In that case the difference between /usr and /usr/local would be important. If you're not on a network then the distinction is not very important.

var = files that are modified by programs (and therefore vary in size a lot), particularly log files. For example, open up /var/games and you'll probably see a list of .scores file which are high score lists for games.


Out of all the directories, the once I find myself dealing with the most are -
* my home directory (obviously)
* /media,  because that's where cdroms and hard drives are
* /usr/bin and /usr/games, because that's where most of my programs end up
* /etc, because that's where I configure various things

---

### Post by ByteJuggler on 2007-10-31
> **Stikky said:**
> 
Yes, I am aware of that now but I'm sure you can see, as someone who has never used Linux before (really) and has always been used to the Windows file system, it's less than intuitive, especially since nothing is what it says it is.. /bin is not where I put my rubbish, /etc could be ANYTHING and /lib is pretty general too so don't act like I'm an idiot cuz I didnt understand it immediately, if you'd used that file system for 10+ yrs then you'd have trouble adjusting to the C:\ stuff in Windows which is like second nature to me.

Edit: Sorry had posted this before reading the whole thread, so I guess this post is redundant... Ignore etc as appropriate!

OK, hope this helps:

"bin" stands for "binaries" meaning user program binaries.  You can always expect programs to be located in a "bin" folder, it has nothing to do with a paper/recycle/waste-bin.  It's loosely analogous to "Program Files" in Windows

"lib" stands for "libraries", it is where (shared) program libraries are stored.  It's loosely analogous to "Windows\System32"  (Aside, I think "lib"/"libraries" are rather more descriptive than "Windows\System32"...)

"etc" stands for "et-cetera", and is conventionally the dumping ground for system wide configuration files, as well as a few other things that don't fit anywhere else.  It's roughly analogous to the Windows System registry.

"sbin" stands for "System binaries", meaning programs that are not normally useful to users, but are useful to system administrators/system administration.  You typically won't find the "sbin" folders on the search path of end-users but will find it on the path for root/administrator users.

"dev" stands for "devices".  Windows has no filesystem counterpart.  Inside "/dev" the Ubuntu system represents a whole load of devices as files.

"proc" stands for "process(es)"  Windows has no fileystem counterpart.  Here the Ubuntu system represents process and kernel related items as files.  You can for example access a processes command line by going into the directory corresponding to its process id and opening the file named "cmdline".

"tmp" stands for "temporary" and is meant for temporary files. Windows has over the years had many/several equivalents. They  C:\Windows\Temp and C:\Documents and Settings\<username>\Local Settings\Temp

"home" stands for... home!  It is meant for all user data and home folders.  The Windows equivalent is "C:\Documents and Setting" (or "c:\users" under Vista.) 

"opt" stands for "optional" Typically you'd install/place programs here that are manually installed and not part of the "official" system (e.g. stuff that doesn't install via Synaptic or whatever.)

In the end, you should ideally always try to keep your user data in your home folder (/home/<username>) and not anywhere else.  

Hope that helps!  :KS

---

### Post by The Tronyx on 2007-10-31
This might shed some light on a few of your frustrations.  Just give it time.  As you can see, the community here is excellent and always willing to help as long as people are willing to help themselves.

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by oldos2er on 2007-10-31
> **macogw said:**
> 
usr is for **us**e**r**space (as in, not the things the very deep down parts of the OS need to keep running) programs


 usr = unix system resources

---

### Post by Keith_Burton on 2007-10-31
Hi Stikky, and welcome to the Linux world.

Here's the deal with people always posting command-line instructions to solve problems: It's more accurate and far less typing for us. As an example, assume you needed to be told how to install a particular package (program). I can type:
[INDENT]sudo apt-get install packagename[/INDENT]
Or, I can spend a whole paragraph explaining how to start Synaptic, search for the package, now click here to mark it to be installed, click somewhere else to actually start the install, and so on. And then, half the time it'll turn out you were using Kubuntu, Xubuntu, or one of the others, and they use different programs to install packages so it all has to be done over again.

The two examples do exactly the same thing. In fact, Synaptic ends up actually invoking a hidden command-line and running that exact same command to do the real work of installing. Most Linux graphical programs are like that. They're a pretty cover, but underneath they just run the same command-line programs the old-timers have always run.

But just because we do it that way here doesn't mean you have to. Except for troubleshooting problems with us here, everything you need to do can be done without the command line.  Well, there are doubtless a couple of exceptions to that, but people here will help when that time comes. 

As for all the differences in how the filesystem is organized and how tasks are done between Linux and Windows, well that's on-purpose. Ubuntu isn't designed to be "like Windows". Linux is designed from a different perspective...one we consider superior to Windows' design. That means it's going to take several months to get comfortable with it, but the first couple of weeks are the hardest. It would be the same if you switched to a Mac, an IBM mainframe, or a Palm-based handheld. And I'm speaking from personal experience.

You're off to a great start. I hope you stick around :)

---

### Post by PudUK on 2007-10-31
I've found the best thing to do with ubuntu when stuck is walk away and calm down.

I was quite happy with dos, and i first used windows 3.0, but it did seem simple and fairly intuitive. Linux by comparison just isn't - like you i still don't really get it properly.

If you hit a problem and don't get an answer, i've found coming back to the problem 3 months later and googling again usually turns up an answer. I am hoping in 3 months someone will get to the bottom of the aMSN webcam problems with Zyxel Prestige routers - for instance.

Incidentally, i've tried Fedora, Suse and Ubuntu in 2 forms. Ubuntu is definitely the best version of Linux i've tried.

Sorry, this doesn't assist with any of your problems - but happy to share the pain.

---

### Post by averagebeatboy on 2007-10-31
Lord knows I can relate with what your post states.  I can never remember (to this day) though Windows being more intuitive than Ubuntu.  I am using "Gutsy Ribbon 7.10.

I was younger than and saw those little Window hiccups (especially my favorite "Winsock" that they still have the "nerve" to be using Winsock for Windows communications).  As if that isn't bad enough they are still using DOS as the underlying pinning for their operating syytems -- they ought to be drummed out of the business ...laughing.  As for Windows still using DOS if you do not believe me remove DOS from any version of Windows.  I promise you Windows will not run. 

I think I am going through the same learning curve with Ubuntu, but with a major difference:  I have a little more patience and a maturity that you get with getting older.  I now know for instance that a little legal pad and pen are my best friends.  Instead of running around like a dog chasing its tail ... I write down ANY and ALL commands that I feel may be of use to me now and in the future.  Doing this has helped to relieve my frustration levels in learning Ubuntu, to say -- 20%.  I now even know how to get Root in a terminal and closing Root when I shut the terminal.  I don't feel like going through my notes but it is something like su sudo or sudo su one or the other.  It is a great command for doing a lot of things.

Another example is that pesky "changing permissions" command.  Now that I wrote it down, use it so often, I was forced to memorize it or keep looking at my notes.  The command I use is to become root in terminal (see the command above) and in a terminal type without the quotation marks "chown -R <my name> /file/file you may have to reload what directories you are changing the permissions for but it works like a charm and like the root command above once the Terminal is closed so is the command.  That way, unlike countless times before I cannot damage anything in Ubuntu and go through reinstalling.

All-in all, if you do take notes it will make your life with Ubuntu so much easier and a pleasurable experience instead of a hair-raising one.  I hope this helps you and anyone else using Ubuntu and suffering from frustration.

I wish you the best with Ubuntu and if you take my advice you will find that what I am writing about really does work and Ubuntu becomes a very pleasurable experience.

Cheers,

Averagebeatboy

---

### Post by Bigbird999 on 2007-11-01
Sticky 
Total newb (4 days)!!  Same frustrations including black screen slow boot.   I fixed it by doing this
1) Change the resolution in /etc/usplash.conf to 1024x768
2) Add vga=791 to the kernel line in /boot/grub/menu.lst
3) sudo update-initramfs -u -k `uname -r`
as per the following thread
[http://ubuntuforums.org/showthread.php?p=3569987#post3569987](http://ubuntuforums.org/showthread.php?p=3569987#post3569987)

Plus i am a command line/terminalphobe!

Which led to one of my greatest frustrations so far which was that the that the ** '** marks around uname-r are not apostrophes, but are really back ticks **`** on the tilde key ~ at the upper left of your keyboard.  Didn't even know it was there.  
This led to my next great break through which was that you don't have to type all this arcane code into the terminal.  I only found this tip in one post 
Select the line of code in the post like
sudo update-initramfs -u -k `uname -r`
open terminal
move the cursor onto the terminal window
center click (on a 3 button mouse)  or simultaneous left right click on a 2 button and the code is magically pasted into the terminal 
hit enter and it runs the command.
No typing errors, no mistaking ' for`, no missed spaces or extra spaces, missed upper case errors.  It just works!  I am sure that all of this is in the manual, but I never found it.  
> Here's the deal with people always posting command-line instructions to solve problems: It's more accurate and far less typing for us. As an example, assume you needed to be told how to install a particular package (program). I can type:

    sudo apt-get install packagename

Or, I can spend a whole paragraph explaining how to start Synaptic, search for the package, now click here to mark it to be installed, click somewhere else to actually start the install, and so on. And then, half the time it'll turn out you were using Kubuntu, Xubuntu, or one of the others, and they use different programs to install packages so it all has to be done over again.

Thanks for this great explanation of why terminal is so useful.  

BB

---

### Post by Stikky on 2007-11-06
> **Bigbird999 said:**
> Sticky 
Total newb (4 days)!!  Same frustrations including black screen slow boot.   I fixed it by doing this
1) Change the resolution in /etc/usplash.conf to 1024x768
2) Add vga=791 to the kernel line in /boot/grub/menu.lst
3) sudo update-initramfs -u -k `uname -r`
as per the following thread
[http://ubuntuforums.org/showthread.php?p=3569987#post3569987](http://ubuntuforums.org/showthread.php?p=3569987#post3569987)

Thanks for that, I want to give that a try.. Unfortunately, I had problems with.. Well.. All the steps! :p (Yeah, I'm useless)

1) I found this file, changed the res, no problems, until I come to save. Aparently I don't have permission. How do I get permission? It's my computer, can't I do what I want with it?!
2) I don't want to stuff anything up so I didnt do this one but i did look at the file and there are lots of lines with the word "kernel" in them, I didnt know which one to add "vga=791" to
3) I assume, since thats an update command that you need to do the first two before running this so I didnt do this one either..

So could someone let me know how I should be doing this? Haha, sounds stupid, I know, but I am still pretty new so I apologise for the newbie questions... :oops:

---

### Post by Peter09 on 2007-11-06
HI,
welcome.... I'm a three month newbie to Ubuntu. 

To get super user permissions to write your file you start the command line with sudo.

eg

> sudo gedit "a_file_you_wish_to_ edit."

(note that gedit is another text editor).

it will ask you for a password and then carry on.

This is a great strength of Linux, and why there are no viruses, in general you operate at a user level and only go  to root when needed.

---

### Post by Peter09 on 2007-11-06
Note that my understanding is that you need to set the resolution in the usplash file to the same resolution as your screen - although I stand to be corrected on that one as I have not needed to do it.

---

### Post by Stikky on 2007-11-06
Thanks Peter! I will give that a try now..

> **Peter09 said:**
> This is a great strength of Linux, and why there are no viruses, in general you operate at a user level and only go  to root when needed.

Is that why they do it? It frustrates me sometimes but I suppose it makes sense when you think about it.. I mean, the vast majority of things I do on my computer dont require me to have root access so I guess it makes sense to get root access only when you need it.. I'm pretty new, too, so these things take a while for me to grasp, sometimes I think Ubuntu is just being difficult but I guess there's a purpose to everything!

So can anyone tell me which line specifically to edit in /boot/grub/menu.lst??

---

### Post by Stikky on 2007-11-06
> **Peter09 said:**
> Note that my understanding is that you need to set the resolution in the usplash file to the same resolution as your screen - although I stand to be corrected on that one as I have not needed to do it.

Oh, didn't see this post! Sorry!

I checked the usplash file and the res is 1280x1024 which is higher than my little lappie can handle so I think this might be one of the problems.. It can do 1024x768, though, so that's what I'm gonna change it to..

---

### Post by Stikky on 2007-11-06
> **Stikky said:**
> So can anyone tell me which line specifically to edit in /boot/grub/menu.lst??

Come on, anyone???

---

### Post by dhobbs on 2007-11-06
If you have a problem with the resolution then you should just change the usplash.conf file to the correct resolution.
```
sudo gedit /etc/usplash.conf
```
If you set the resolution correctly then when you boot up the computer grub won't fail at displaying the pretty artwork which will speed the boot process up.

As for the grub menu.  That's a dangerous file to mess with if you don't know what's going on.  First try the different resolution to see if that fixes the boot splash screen.  If there's still a problem then reply here and we'll see what we can do.

---

### Post by Stikky on 2007-11-06
> **dhobbs said:**
> If you have a problem with the resolution then you should just change the usplash.conf file to the correct resolution.
```
sudo gedit /etc/usplash.conf
```
If you set the resolution correctly then when you boot up the computer grub won't fail at displaying the pretty artwork which will speed the boot process up.

As for the grub menu.  That's a dangerous file to mess with if you don't know what's going on.  First try the different resolution to see if that fixes the boot splash screen.  If there's still a problem then reply here and we'll see what we can do.

OK, I just tried that, I changed the resolution in that file and nothing happened.. I rebooted and same blank screen.. Any more suggestions??

---

### Post by dhobbs on 2007-11-06
Did it boot fast or was it still incredibly slow?

Also did you follow the suggestion about changing "splash" to "nosplash" in the grub file from an earlier post?  If you did that tells grub to not show the splash screen.

---

### Post by dhobbs on 2007-11-06
As a side note:  if we end up diving into the simplistic world that is the grub bootloader, here is a link that will hopefully help ease the pain.
[http://technical-itch.co.uk/2006/12/01/understanding-grub/](http://technical-itch.co.uk/2006/12/01/understanding-grub/)

---

### Post by Bigbird999 on 2007-11-06
It is a 3 step process, did you do all 3?  Also look here
[http://ubuntuforums.org/showthread.php?t=579684&page=2&highlight=splash+screen](http://ubuntuforums.org/showthread.php?t=579684&page=2&highlight=splash+screen)

BB

---

### Post by Stikky on 2007-11-06
Hey so I did the "sudo update" command thing and it worked! :D I get the pretty boot screen now!! Well, it's just a black background with a status bar and the logo.. Awesome! Thanks guys!

---

### Post by dhobbs on 2007-11-06
That's good to hear.  Is there anything else that's still bothering you?

---

### Post by Stikky on 2007-11-06
> **dhobbs said:**
> That's good to hear.  Is there anything else that's still bothering you?

Thanks dhobbs, I think I'm alright at the moment, actually, but I will be sure to bring up more questions once I have them, which I no doubt will!! :p

Haha, thanks again for all your help!!

---

### Post by crf on 2007-11-06
--
**Command reference**
One good book to buy is linux in a nutshell. An [older copy](http://www.abebooks.com/servlet/SearchResults?sts=t&tn=linux+in+a+nutshell&x=0&y=0) may be good, since the new one, last time I looked, is now really large, and uncomfortable to hold.

It explains many of the commands you can use on the terminal. You can use it as a reference, or you can read a little bit each day, to get familiar with some commands.

---
**Where are things**
In Linux, programs store their user-specific settings and files in the user's home directory, under directory names starting with a period (.). You can see these files in from the command line by choosing ls -a or ls -al . You can see them in "places" file browser by going to view menu --> show hidden file.

In a terminal window, you can display the contents of files by using the more command. 

You can edit files on the command line using vi, but unless that is necessary, try using the command gedit, which open the file in a gedit window (it's more intuitive: I think a reference is needed to work vi properly). 

---
**Booting up**
Linux can take a while to boot up and to shut down. One option is to use suspend. When your computer is suspended, it will consume little power (more than if it were off of course), and the disk drive should shut off (so it shouldn't make noise). Resuming from the suspended state doesn't take long, and putting the computer into suspension also doesn't take long (perhaps less than shutting it down). 

--
**installing programs**
You may use synaptic to install programs. But first try, from the ubuntu menu, add-remove applications, and from the pull down menu, choose to show supported applications. These are the apps that are "officially supported", and so would presumably have gone through some quality control. For instance, I'd expect any of those apps to add entries in the applications menu that actually work.

To see what programs you can run, look in the /usr/bin or /usr/games directory, and the /bin directory, the /usr/sbin directory is for the superuser only programs.

--
**becoming superuser**
on the command line, type sudo -s, after which all commands you enter will be as superuser, until you quit the shell with quit. You won't often need to do it, so use it sparingly. Just preceding commands with sudo usually is enough (sometimes it isn't, or is inconvenient).

---
little bits that might be interesting -->

I just installed linux myself :-) . The following commands and files might be useful.

parted --> this is a partition editor. But it is useful to display info or error messages about your partitions.

/etc/fstab --> this file contains information about how linux will boot your partitions. I had to edit it, but don't mess it up.

/var/log/fsck/ --> logs of the file system checker program.

mount --> shows info about mounted partitions.

sudo vol_id /dev/*a partition your want info for*

------
Sometimes things will take a long time to boot up if something is just a little bit wrong with your filesystem.

---

### Post by hogwartsnigel on 2007-11-07
Guys,
A short post to say thank you and thank you again. I am a well established WinDOSE user too and have install 3 distros onto 3 of my 6 pcs in the last fortnight. @ dual boots and this old laptop exclusively running free spire.
It is AMAZING:)
The community feel is real, I am a command line phobic and haven´t had to use it except to establish a boot loader link to sort out a boot issue see my other post.
This thread has inspired and informed me so much more than I could have hoped.

I am running Ubuntu (fave) 7.1 dual booted on an AMD 64 machine, Sabayon (Very Pretty) on a dell P4 2.8ghz and freespire on this dinosaur compaq armada.  The other 3 will follow soon and my kids will be word processing, emailing,browsing at home so as to break the M$ excrement feeding.

I am in it for the cause more than the free beer but love both. I own 6 xp liscenses and am happy to ditch them, the time is right.

MY ISSUE is how to mount my NTFS hard drives and my 2 USB hard drives to read data for Ubuntu....the learning keeps on.

Thanks a million guys

N igel

---

### Post by Metalslave on 2007-11-07
> **Nythain said:**
> if you pay attention during installation you actually have great controll over formating/creating partitions and where to mount them... though a clean hard drive wipe is a great start for a new user

Perhaps, but I *did* pay attention, but appearantly still missed it and ended up with a wiped harddrive. Wiping the harddrive is a pretty big deal and I think there should be at least a couple of warning signs to click through before it happens. Also, the formatting options need to be made a lot clearer to the point where it's impossible to miss them

---

### Post by hyper_ch on 2007-11-07
Why should there be a couple of warnings? One is enough - people should try to read what's actually written on the screen and comprehend... and if they don't comprehend, inquire what that means before proceeding...

---

### Post by Stikky on 2007-11-07
> **Metalslave said:**
> Perhaps, but I *did* pay attention, but appearantly still missed it and ended up with a wiped harddrive. Wiping the harddrive is a pretty big deal and I think there should be at least a couple of warning signs to click through before it happens. Also, the formatting options need to be made a lot clearer to the point where it's impossible to miss them

I feel your pain, metalslave, I lost quite a lot of data from my computer.. I knew it was gonna wipe the HD but by that time, it was too late, there were no other options, it had already screwed up my partitions and my computer wasnt even booting to xp and since the live CD doesnt support NTFS, I couldnt even back up stuff.. None of it was really that important, I guess, but still..

I dont think there needs to be more warnings, I think there needs to be an option in the installer to use your *existing* partitions.. XP lets me do it (I know, I know, people dont like to compare but XP really wins this round..) when I install.. With Ubuntu, I was gonna have to split my partition into 2 and have 3 partitions on the same drive. Why is it so hard for it to use my existing partition??

> **hyper_ch said:**
> Why should there be a couple of warnings? One is enough - people should try to read what's actually written on the screen and comprehend... and if they don't comprehend, inquire what that means before proceeding...

I agree with you, yes, one warning should be enough.. But it's not. As much as we don't like to admit it, people are stupid.. Not calling anyone here stupid but if you're gonna make a Linux distro for the average person, you have to remember that the average person won't read everything on the screen.. It's no use saying "Well, if you'd read through the output in command prompt, you would have SEEN that it was going to wipe /dev/hda1 which you should have known was your hard drive" when the person who's in control of the computer doesnt even know what the command line does..

Die hard Linux fans have been pedaling Linux for years and it's getting towards the point where it's useable for the average Joe (or Jane) but it's still got a way to go.. You can see from this forum alone (the absoloute beginer talk one) that Linux isn't quite there yet. Half the posts on the first page are "I can't stand it, how do I go back?!" and "Gutsy wiped my HD" and stuff like that. I know it's different from Windows but the transition is not really made any easier by the lack of documentation...

Having said that, of course, there is the community which I have nothing but good things to say about. These have to be some of the most helpful people I have ever encountered (on the internet, especially!) and they are always more than happy to sort out a problem or provide a link if you're willing to help yourself. The problem is that a lot of people don't want to help themselves, they want someone else to do it for them..

Just my two cents :)

---

### Post by hyper_ch on 2007-11-08
> **Stikky said:**
> and since the live CD doesnt support NTFS, I couldnt even back up stuff.
The live CD does support ntfs RO...

> **Stikky said:**
> I dont think there needs to be more warnings, I think there needs to be an option in the installer to use your *existing* partitions.. XP lets me do it (I know, I know, people dont like to compare but XP really wins this round..) when I install.. With Ubuntu, I was gonna have to split my partition into 2 and have 3 partitions on the same drive. Why is it so hard for it to use my existing partition??
It is not ;) why not manually set them... the problem is Windoze installs itself only onto 1 partition. In linux however you can already upon installation fracture your system installs into many, many partitions. Linux offers you more choice... furthermore windows only lets you install one system... in linux, as you know from dual booting and with grub, you can have 2,3,4, ... systems installed at the same time. How is the partitioner going to find out which existing one you want to use?

> **Stikky said:**
> I agree with you, yes, one warning should be enough.. But it's not. As much as we don't like to admit it, people are stupid.. Not calling anyone here stupid but if you're gonna make a Linux distro for the average person, you have to remember that the average person won't read everything on the screen.. 
The average user doesn't install an OS but uses the one that's delivered with the machine he buys.

> **Stikky said:**
> Die hard Linux fans have been pedaling Linux for years and it's getting towards the point where it's useable for the average Joe (or Jane) but it's still got a way to go.. You can see from this forum alone (the absoloute beginer talk one) that Linux isn't quite there yet. Half the posts on the first page are "I can't stand it, how do I go back?!" and "Gutsy wiped my HD" and stuff like that. I know it's different from Windows but the transition is not really made any easier by the lack of documentation...
What do you expect from a support forum? People one "whine" when something go wrong. Hardly ever it's acknowledged when everything goes right. It is expected to be going right so no use to applaud there en masse on forum, is there? I'd love to see those people install windows... I bet they will also wipe their harddisks...

---

### Post by airtonix on 2007-11-10
> Yeah, I know that they're different but that's not to say they arent related. Windows is very user friendly to me in the sense that I can open up an XP computer and I know what I'm doing straight away.you just described familiarity. not user-friendly

THe whole point of ubuntu and linux is to empower people, windows will never do that becuase it is a tool aimed at corporations who deploy it to those thousands and thousands of cubilce workstations.

windows = labour-slave-tool
linux = dev/tech/empowered-persons-tool

now think about it, you wouldnt want you slaves to learn about freedom or (kek) even dare to desire it.

This is the feeling told to me by business-owners that I offered to replace their windows netowrk with ubuntu.

also, if you want to start doing things like triplicts of a warning screen so mentally deficient people will go " ohhh a third warning screen, maybe something is wroooong"....you enter the realms of diminishing usefulness....windows is well down this path. as is modern democracy

---

### Post by quinnten83 on 2007-11-10
> **greenlegacy said:**
> Yet another answer to your third question--here is a graphical representation of [the linux file structure.]("http://bp3.blogger.com/_Vbsj-yhipTw/RvaiatPBPBI/AAAAAAAAABs/yjx3hPlEUNw/s1600-h/linux_file_structure.jpg")

As far as pidgin, you can hide your offline buddies by going to Buddies->Show then clicking the appropriate box.  Or if you want to sort your buddies into groups you can go to Buddies->Add Group, then you can click and drag them into the groups you want.

I know it may seem frustrating at first, but you will eventually get used to how things are done in linux.

probably allready suggested elsewhere, but if it is MSN you want, try aMSN in the repos.
has most features except winks and sound when using webcam.

---

### Post by quinnten83 on 2007-11-10
> **Stikky said:**
> Thanks, I'll try that but I might try that "grub" thing Nythain was talking about cuz I like the little boot screens that look like it's doing something..



Well the problem is that I can't figure out where the problems are stored!! Like I said, I am so used to the Windows file system that if it's not a .exe file in C:\Program Files\Azureus then I have no hope of finding it!!



Thanks for the offer, I suppose I was just a little disappointed that I thought this was supposed to be a competitor for like OSX and XP but I have been using XP for ever and never had to use the command line, really.. I was only a kid when I used 3.x so I have forgotten most (read:all) of the DOS commands my dad used to do! Haha.



Yeah, my video card is not working, I'm sure. I'm already sick of most of the visual effects (mainly cuz I couldnt get them to work) but Wobbly Windows is pretty damn cool. Also, as to what I am refering to, I mean this:

[IMG]http://media.arstechnica.com/reviews/os/pretty-vista.media/expose_screenshot.jpg[/IMG]

You press a button in OSX (my friend showed me on his Macbook) and it opens all your minimised windows and shows you them on the screen so you can select one which it then maximises! It's really useful and ubuntu kind of does it but only with the desktops, as far as I can work out..

Thanks again for all your quick replies and help, everyone! I heard the Linux community was helpful but I wasnt expecting such a great response so thanks!! :)

The forums are one of the strengths of the Ubuntu operating system.
I know Beryl used to have this option, but for the love of me I don't know how to do that in compiz-fusion. have you installed compiz-config cofiguration manager? It wil allow you to tweak and configure (mind you i dunno what half of the options in there do).

---

### Post by Bachstelze on 2007-11-10
Now everyone (especially the two of you who recieved an infraction) please calm down or this thread will be closed and/or jailed, since nothing interesting came out of it anyway.

---

### Post by Stikky on 2007-11-11
> **HymnToLife said:**
> Now everyone (especially the two of you who recieved an infraction) please calm down or this thread will be closed and/or jailed, since nothing interesting came out of it anyway.

Sorry, maybe I missed something but who needs to calm down? I thought everyone was just having a discussion, I didnt think anyone was getting nasty, were they?

---

### Post by airtonix on 2007-11-17
el oh el....calm down...i'm as saguine as can be...I think you need thicker skin hymntolife

For that expose type feature your after, it's already been mentioned what it is.

again: it is the 'Tile & Scale' plugin

You may also want the expo plugin, which does a similar thing for the workspaces, as opposed to waht the tile & scale plugin does for the application windows.

I highly suggest anyone search for help on the [https://help.ubuntu.com/community/](https://help.ubuntu.com/community/) site, before even bothering to ask here.

---

### Post by Stikky on 2007-11-20
> **airtonix said:**
> For that expose type feature your after, it's already been mentioned what it is.

again: it is the 'Tile & Scale' plugin

You may also want the expo plugin, which does a similar thing for the workspaces, as opposed to waht the tile & scale plugin does for the application windows.

Yeah, thanks, I have it working now..

If anyone is still reading this thread, maybe someone could tell me how I get it to tile and scale ALL windows, even the ones I have minimised? It doesnt appear to be possible, even though there seems to be an option for it (which I have enabled, still no luck) so if I'm donig something wrong or there's some setting I can change? That would be cool..

What I want it to do it just unminimise everything on the taskbar and tile and scale, not just the un-minimized windows..

Thanks again in advance.

---

### Post by ByteJuggler on 2007-11-26
Came across this today, thought I'd post it for reference:

[http://www.pathname.com/fhs/2.2/](http://www.pathname.com/fhs/2.2/)

It's some official documentation describing the Linux filesystem layout and is rather more complete than the comments posted in this thread.

---

### Post by linuxlizard on 2007-11-26
> You press a button in OSX (my friend showed me on his Macbook) and it opens all your minimised windows and shows you them on the screen so you can select one which it then maximises! It's really useful and ubuntu kind of does it but only with the desktops, as far as I can work out..

Compiz advanced settings will let you set this up just fine on ubuntu.

On mine, I just slide my mouse to the upper right hand corner of the screen and every window on all desktops appear for me to select from. I forgot the name of this feature, but if you search the forums or google compiz tweaks you will find how to do it. That's how I learned.

---

