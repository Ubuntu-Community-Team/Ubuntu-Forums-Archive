---
title: "wanna ajust gutsy with hammer"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by flipenzeeflop on 2008-01-08
Hi all,last year i made the jump to Linux.Feisty was GREAT...i had it configured and running super fast.It booted clean and quick.I was able to watch all forms of media within hours.I was the envy of my windows/slave friends.
   Since my update to Gutsy....thats a different story.It runs slower....simply CANT load some websites for reasons i dont understand.Almost no media works....flash is a NIGHTMARE and crashes the system.Real video etc are just a pipe dream it seems.I was able to configure Feisty pretty easy....i didnt even have to join.The info was easily avaialable.Not so with Gutsy....threads seem to give tons of differnt solutions....none work.

   So i am ready to ajust my system with a hammer......
all i want is the functionality that Feisty had....thats it.

   Isnt this supposed to be Linux that just works?
i cant be the only one who gives gutsy a HUGE thumbs down....

---

### Post by stump138 on 2008-01-08
well..this probably isn't the place for a rant, but if you can list some specific issues and try to give some details, some of us can maybe help you get sorted.

---

### Post by benrboone on 2008-01-08
have you tried a new install instead of an update.
I had problems with an update as well but when I did a clean install most of the problems went away

---

### Post by flipenzeeflop on 2008-01-08
well if anything besides slavish praise is a rant then i guess that was a rant.....otherwise i feel OK about the quite legit beefs i have with Gutsy


    this is a clean install....have done it twice

specific issues(same ones i point out above)

 flash simply doesnt work....youtube hardcrashes the system

 many websites simply dont load
  
 with Feisty there was a great communtiy spirit...issues were in stickies and even a dope like me was able to fix problems( some issues with Gutsy dont even seem to be considered bugs)

there  are dozens of solutions for the flash issue in VERY hard to follow threads...even a clean re install and manual install of flash doesnt work

 unable to figure out how to watch realvideo quicktime etc...

Perhpas i sound upset....i AM this feels like a microsoft product LMAO 2 steps forward 4 steps back

with feisty i felt positively evangelical about it i recomended it to everyone...Gutsy?
well i would recomend it to people i wanted to get a migrane

---

### Post by rune0077 on 2008-01-08
The latest version of Flash *just does not work* and Firefox does not install it correct. This is not a Gutsy problem, though, but a Flash problem I think (maybe a Firefox problem). If you're lucky, you can find an older version and install that - I never updated to the new version and mine still works like it's supposed to.

---

### Post by Ripfox on 2008-01-08
For the record, none of my computers run Gutsy...I run Feisty on all but one and it's this one. This one runs Hardy, which frankly runs better than Gutsy ever did. So in short I uninstalled it from everything b/c of endless problems. Just my experience.

Rip

---

### Post by caravel on 2008-01-08
Strange I have no problems myself.  Perhaps my expectations are too low?

I haven't installed flash as yet, as I hardly visit any flash sites (come to think of it I've yet to install the J2RE as well!).  I will have a go later and let you know how I get on. :)

---

### Post by flipenzeeflop on 2008-01-08
Thank you Rune and Ripfox...i was a bit perturbed to find my less than thrilled with Gutsy post to be deemed a rant...i assure you the hammer comment isnt far from the truth.

   so in plain simple english(i dont care who's fault it is) gutsy is broken?

    in other words unrealistic expectations like youtube or many flash sites etc WONT happen?
 
     Perhaps a downgrade back to Feisty?havent  they discontinued the all in one codec solution?Easyubuntu i think it was?



PS linux that just works...as far as gutsy anyways is a pretty cruel joke

---

### Post by hessiess on 2008-01-08
just dongrade, im still running feisty without problems

---

### Post by flipenzeeflop on 2008-01-08
ummmmm dont downgrade back to feisty because u are still running feisty without issues?

what the heck are you drinking?More to the point where can i get some?

---

### Post by philinux on 2008-01-08
Flash is easily sorted thanks to adobe.

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux)

Now I've even got full screen and progress bar.

---

### Post by flipenzeeflop on 2008-01-08
ok phil thx

please explain for a moron like me what to do...i have been to the same page u show...obviously i have done something wrong b4

---

### Post by philinux on 2008-01-08
Download the tar file to your desktop. Then

tar.gz installation

   1. Click the "Download .tar.gz" link. A dialog box will appear asking you where to save the file.
   2. Save the .tar.gz file to your desktop and wait for the file to download completely.
   3. Unpackage the file. A directory called install_flash_player_9_linux will be created.
   4. In terminal, navigate to this directory and type ./flashplayer-installer to run the installer. Click Enter. The installer will instruct you to shut down your browser(s).
   5. Once the installation is complete, the plug-in will be installed in your Mozilla browser. To verify, launch Mozilla and choose Help > About Plug-ins from the browser menu.

For item 4 In the terminal type.

cd /Desktop/install_flash_player_9_linux

Cut and paste the command.

Then type

./flashplayer-installer

Follow the instructions. By the way I uninstalled the gutsy version of flash first

---

### Post by rune0077 on 2008-01-08
You should note that this won't work if you're using a 64bit version of Gutsy.

---

### Post by philinux on 2008-01-08
> **rune0077 said:**
> You should note that this won't work if you're using a 64bit version of Gutsy.

Whats the fix for 64 bit I'm buying a new pc soon.

---

### Post by rune0077 on 2008-01-08
Oh gosh, I wasn't prepared for that question. It's been a while since I installed flash, but I actually think I used the guide from Psychocats: [http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash) - even if I didn't, it should work.

Edit: actually, the link from there just links to a thread here on the forum: [http://ubuntuforums.org/showthread.php?t=202537](http://ubuntuforums.org/showthread.php?t=202537)

---

### Post by benrboone on 2008-01-08
there is a fix for the 64 bit version of flash as well 
take a look at this forum

[http://ubuntuforums.org/showthread.php?t=636397](http://ubuntuforums.org/showthread.php?t=636397)
the package you want for amd64 is  flashplugin-nonfree_9.0.115.0ubuntu0.7.10_amd64.deb

I've used three different times to fix my friends computers

This will give you some warning about a package in the repositories that is better just ignore it and in stall it anyways

ps like stated above the problem lies with adobe changing the file which results in a new checksum this causes the flash to fell to install although it report success in the gui.  The terminal output however does show failure

---

### Post by 4partee on 2008-01-08
Boy, you got that title right.  I 'upgraded' to Gutsy and I wished I had not.  

I re-installed 7.04.

Gutsy should have been named DULL DELL.

John

---

### Post by benrboone on 2008-01-08
I happen to like gusty quite well
had a few problems such as flash but over all works very well

---

### Post by caravel on 2008-01-08
I've just installed flashplayer from the link posted above and it was easy enough.  The hardest part, and even that's easy, is entering the path to Firefox which was /usr/lib/firefox and it's working first time,  Youtube also works btw.  It was easy enough so I thought I'd install Opera and try installing flash player for that by re running the installer as well but that wasn't as simple.  Java was easy enough to get working as well.

-Edit: still no lock with flash player 9 and Opera.  I've made links to the plugins but it still simply doesn't work.

---

### Post by jordanmthomas on 2008-01-08
I realize this isn't really adding much to the thread, but I was VERY disappointed with gutsy.  I haven't used Ubuntu as my primary system in quite some time, but since I help here I usually try out all the new releases and most of the time have an install on another partition.  

I am sure I could have made it run fast, but why waste my time doing this when other distros are fast by nature?  There's nothing stopping you from using another distro or from going back to feisty.  Personally, I don't like using old software and always run unstable, so going to feisty wouldn't be a good thing for me, but pergaps I am just a bit of a masochist.  :)

You seem like you only have three problems, which isn't too many.  To play videos just use mplayer-plugin after installing ubuntu-restricted-extras (or whatever it's called...it's at least a similar name) and people have already suggested how to fix flash.  All that's left is the speed issue, which isn't a bug per se, it's just that Ubuntu has taken on the role of "everything works without you needing to do anything" so it has a bunch of stuff you likely don't need / won't ever use running.  I'm sure you CAN make Ubuntu fast, but in the end you'll just end up with Debian, so there's not too much value in trying to make Ubuntu faster.

Sorry for rambling.

---

### Post by pw2buz on 2008-01-24
Flipenzeeflop,

I do not consider your post about hammer adjustments a rant.

Definitions of rant:
# harangue: a loud bombastic declamation expressed with strong emotion
# bombast: pompous or pretentious talk or writing
# talk in a noisy, excited, or declamatory manner 

Your post expressed frustration with Ubuntu 7.10, which is seen by many as
an imperfect distro (see, that's polite writing!).  I've had much frustration from
7.04 until I received two very helpful posts from Mandrill and yourpalal, and posted
what some might consider rants.

You may find that persistence is a quality you develop from working with Linux.

Pw2buz

---

