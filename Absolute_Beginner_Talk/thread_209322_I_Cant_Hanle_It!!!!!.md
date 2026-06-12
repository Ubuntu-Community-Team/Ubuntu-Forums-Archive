---
title: "I Cant Hanle It!!!!!"
date: 2006-07-05
forum: Absolute Beginner Talk
---

### Post by IrishGangsta on 2006-07-05
All i am trying to do is use Frostwire

I downloaded it but it wont open
And i cant find Java sun package
I tried turning things to multiverse but it just confused the hell out of me

I couldnt be any more confused right now

All i want to do is install java sun i guess 

BUT I WANT TO MAKE FROSTWIRE WORK!!!!!

If anyone can explain this to me in simplified terms 

like Ubuntu for IDIOTS!!!

i would greatly appreciate it

thank you

---

### Post by Wyrm_1972 on 2006-07-05
Be lazy... use Automatix

[http://ubuntuforums.org/showthread.php?t=138405&highlight=automatix](http://ubuntuforums.org/showthread.php?t=138405&highlight=automatix)

Will do both of those things for you...

---

### Post by Kilz on 2006-07-05
[QUOTE=Wyrm_1972]Be lazy... use Automatix

[http://ubuntuforums.org/showthread.php?t=138405&highlight=automatix](http://ubuntuforums.org/showthread.php?t=138405&highlight=automatix)

Will do both of those things for you...[/QUOTE]
I have helped a few people fix java installed by automatrix over the last few days. They get an sun-java5-doc: subprocess post-installation error that pops up whenever they use synaptic after using automatrix to install java 
```
sudo apt-get install j2re1.4
```
Will install java with little problems if multiverse is enabled.

---

### Post by Wyrm_1972 on 2006-07-05
Automatix can cause some headaches... true... but it is easy!

Look at this thread too... [http://www.ubuntuforums.org/showthread.php?t=185758](http://www.ubuntuforums.org/showthread.php?t=185758)

I use it to base my sources.list on. Lets me get most things I want and or need. Easy cut and paste job too...

---

### Post by Kilz on 2006-07-05
[QUOTE=Wyrm_1972]Automatix can cause some headaches... true... but it is easy!

Look at this thread too... [http://www.ubuntuforums.org/showthread.php?t=185758](http://www.ubuntuforums.org/showthread.php?t=185758)

I use it to base my sources.list on. Lets me get most things I want and or need. Easy cut and paste job too...[/QUOTE]
Seems to me one line to install whats needed without errors is a lot more easy than installing something to install something else with errors.

[I would also recommend the orignal poster to read this page.]("http://linux.oneandoneis2.org/LNW.htm")

---

### Post by IrishGangsta on 2006-07-05
im so confused
i think im gonna give up on linux
I am currently reading this page the Kilz suggested i read
It seems that it may help me
Thank you

---

### Post by _simon_ on 2006-07-05
don't give up! If what people are saying is going over your head then just ask to have it explained as simply as possible in steps and then keep a note of what worked for you for future reference :)

---

### Post by r4ik on 2006-07-05
Changing OS isnt a walk through the park hang in there and keep on trying.
Nobody steps on a bicycle without fallin of the first time.
Just hop on it again and keep trying.
When it doesnt work and you have a question just ask, if it still doesnt ask agian and again.
And remember you are NOT an idiot because you cant make things work the first time.

Good luck and have a nice day !

---

### Post by Wyrm_1972 on 2006-07-05
[QUOTE=Kilz]Seems to me one line to install whats needed without errors is a lot more easy than installing something to install something else with errors.
[/QUOTE]

True. However I have happily used Automatix several times without trouble. I would recommend it for a beginner trying to get up and running and enjoying their new OS sooner.

Linux has a sharp learning curve. I would like people to give it a go before giving up too early.

---

### Post by cjm5229 on 2006-07-05
I just used Automatix yesterday to put Java and Frostwire into my wifes computer, it worked just fine. I have used it many times over the last year without a problem. Easy Ubuntu will also help if you don't want to use Automatix. If you edit your sources list for synaptec with the instructions you were given above, you will find 99% of the apps you need for just about anything you will ever want to do.  Once you learn how to use it, you will wonder why Windows can't do it that way. Just take your time and read these forums, check out the howto section. The information is there just browse through it learn.

---

### Post by Kilz on 2006-07-05
I, ummmm, think automatrix is nice. But it installs a lot, on a lot of diffrent systems. There are ocsionaly errors [like here]("http://www.ubuntuforums.org/showthread.php?t=208407"), [and here]("http://www.ubuntuforums.org/showthread.php?t=209080"). I just noticed it had to do with installing java with automatrix.
IMHO its always best to just install whats needed. Especialy if its one or 2 things. Synaptic/apt isnt that hard. Pasting in a command isnt that hard.

[quote=IrishGangsta]  	im so confused
i think im gonna give up on linux
I am currently reading this page the Kilz suggested i read
It seems that it may help me
Thank you[/quote] When I was relatively new I had similar problems understanding why things are so different. Don't give up, but realize, Linux is different, that's why most people want to try it in the first place. I was asked to read the page, and I saved it because it helped me.

---

### Post by Winblowz on 2006-07-05
Why not just do 
```
sudo apt-get install sun-java5-jre
```
???:cool: 

Anyways, I guess it doesn't matter. If you have java installed, then thats great:p  

I do however think we as a community should stop recommending Automatix to everyone when a problem arises. Everytime somebody doesn't know how to install a program, we say "just install Automatix...it will do everything for you." It's my opinion that we shouldn't go that route. If we do, then nobody will learn how to fix simple problems or install a program. I do understand that programs like Automatix are supposed to help linux beginners, and thats great, but we can help them learn linux in other ways. We can teach them how to open the terminal, and how to do things from there. That way, they will eventually know their way around and what they're doing. 

Sorry I got onto a rant, I just couldn't hold in my feelings any longer:-) 


Winblowz

---

### Post by Kilz on 2006-07-05
[QUOTE=Winblowz]Why not just do 
```
sudo apt-get install sun-java5-jre
```
???:cool: 

Anyways, I guess it doesn't matter. If you have java installed, then thats great:p  

I do however think we as a community should stop recommending Automatix to everyone when a problem arises. Everytime somebody doesn't know how to install a program, we say "just install Automatix...it will do everything for you." It's my opinion that we shouldn't go that route. If we do, then nobody will learn how to fix simple problems or install a program. I do understand that programs like Automatix are supposed to help linux beginners, and thats great, but we can help them learn linux in other ways. We can teach them how to open the terminal, and how to do things from there. That way, they will eventually know their way around and what they're doing. 

Sorry I got onto a rant, I just couldn't hold in my feelings any longer:-) 


Winblowz[/QUOTE]

I agree. Automatrix is nice, but it doesn't give the user any knowledge. The old saying, give a man a fish, feed him for a day, teach a man to fish, feed him for a lifetime applies here. If people want to use automatrix or other psetup rograms that's up to them. Especially for the hard to install, hard to find programs, or they know how to install things but want it setup fast its probably best. It was probably its original goal. But it has grown into a install everything a newbie could want program, even if the program is easy to find or install.
But the thing is it cant install everything a newbie could want because each person is different. So the new person has to learn how to install applications eventually. Because odds are there is something not included they want. Learning how to use synaptic isn't that hard. For single applications we may be better off helping them install it without automatrix so they know how to get other things it doesn't include installed.

---

### Post by cjm5229 on 2006-07-06
[quote=Kilz]I agree. Automatrix is nice, but it doesn't give the user any knowledge. The old saying, give a man a fish, feed him for a day, teach a man to fish, feed him for a lifetime applies here. If people want to use automatrix or other psetup rograms that's up to them. Especially for the hard to install, hard to find programs, or they know how to install things but want it setup fast its probably best. It was probably its original goal. But it has grown into a install everything a newbie could want program, even if the program is easy to find or install.
But the thing is it cant install everything a newbie could want because each person is different. So the new person has to learn how to install applications eventually. Because odds are there is something not included they want. Learning how to use synaptic isn't that hard. For single applications we may be better off helping them install it without automatrix so they know how to get other things it doesn't include installed.[/quote]

I agree. However,  If he gives up because something doesn't work, then you don't have anybody to teach.   If they get everything set up and working without a lot of hassles, then they will get interested in staying around and learning how it works. If you try to teach a man how to fish and give him a pole with no line or hooks, how long will he keep fishing? While we argue amongst ourselves the merits of Automatix, another New User is gone. Automatix, Easy Ubuntu, and Bumps all work. Automatix is updated constantly. arnieboy and mstlyevil, are doing a fantastic job of correcting bugs and maintaining Automatix. For the beginner, Automatix will give him a computer that works, then he can take the time to learn the other methods of installing apps in Ubuntu. 
I just installed Windows Vista on my computer, It took two hours to install, and I spent all last week hunting for software, (antivirus, anti-adware, anti-spyware, etc. couldn't get drivers for my scanner, the Windows software that came with it wouldn't load.  Windows is defininitely not ready for the desktop! :wink: A,B,and E are just tools, lets not argue about which tool is right for the job, lets give them the tools and let them use what they want.

---

### Post by IrishGangsta on 2006-07-06
Alrite i wont give up 
lol
i guess i could learn this linux thing eventually
But it sure looks tuff
I just dont understand how to use Automatix

---

### Post by cjm5229 on 2006-07-06
Here, [http://www.ubuntuforums.org/showthread.php?t=190025]("http://www.ubuntuforums.org/showthread.php?t=190025")
just follow the directions in this thread it will install Automatix, then all you have to do is start Automatix from Applications<System tools in your toolbar. after it goes through the intro and credits, you will get a list of Apps to choose from. Install what you want by checking the boxes. You will be able to go back to it at anytime to install more Apps. If you have any questions you can ask for help in the Automatix thread, someone should help quickly. After your setup and working the way you want, check out  Add/Remove Apps, in Applications be sure to check the boxes for unsupported software and commercial software. Also, in Ubuntuforums there is a section in "Other Support Options" for Repositories. Read that, it will help you set up your repositories correctly, so that you will be able to find just about any software you will need in Synaptic. Then here is some more good reading, [http://ubuntuguide.org/wiki/Dapper ]("http://http://ubuntuguide.org/wiki/Dapper")
When you are done with that you will be here answering questions instead of asking them:wink: Good Luck and Happy Ubunutuing.

---

