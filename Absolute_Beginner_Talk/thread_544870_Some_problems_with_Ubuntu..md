---
title: "Some problems with Ubuntu."
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by T4K3Z0U on 2007-09-06
As you may have read yesterday, I am a total beginner when it comes to Ubuntu. I now finally have it installed but have come across a problem or 2.

Problem #1 I want to install Mozilla Thunderbird. I searched for help on this forum and one suggestion in someone else's thread was to go into the add/remove option and do it there some how. The problem....... I do not have an Add/Remove button/option, I find that rather disturbing.

So next I read I could do it from Ubuntuzilla. I went to download it from there and got asked for my password, after entering it, I got this message. {failed to run gdebi-gtk '--non-interactive' '/tmp/ubuntuzilla-4.4.0-0ubuntu1-i386.deb' as user root} {The underlying authorization mechanism (sudo) does not allow you to run this program. Contact system administrator.

WTH does all that mean? and I thought I was the system administrator no?

I saved my windows version of TB to disk and tried to install the .EXE file that way, but it wouldn't let me.

Problem #2 In the version of Firefox that came with Ubuntu, there is no options tab, I can't change the home page or clear cookies and so on.

Problem #3 The appears to be no, AV on my system while using Ubuntu, which is a concern for me.

Problem #4 Everytime I try to install some software, I.E skype, real player and so on, I don't get any install option Per Se, just all the folders. As stated above I am a beginner and I have relied on Windows my whole life of computers. It may be crap but at least it was relatively user friendly.

and

Problem #5 when ever I'm typing something like this, the cursor moves to a different point and stuffs up my text. If I move the cursor to a different part of the screen, It will end up opening a hidden window or something. That is very frustrating.


Sorry to B**ch like this everyone. I know all good things take time and all, but since the installation took me like 4 days to get done and now I'm running into these problems it is a little disheartening.
I really do appreciate your help, and thank you all in advance for any advice you may have.

---

### Post by thelocust on 2007-09-06
I'll try my best

1: You need automatix2 it's a program that installs a bunch of really essential programs.

2: The options tab is now the preferences tad under edit.

3: Again automatix2 you can install all of your codecs (assuming you mean audio/video)

4: The file system is different than window which is better for a few reasons but thats a little much to get into.

5: No Idea.

I'm working on some links for ya hang in there.

---

### Post by sumguy231 on 2007-09-06
1.) It should be at the bottom of the Applications menu. If not, you can use Synaptic to install it (Applications -> System -> Synaptic I think, but I don't use Ubuntu)

#1 part two - I don't know why it wouldn't let you use sudo, but I'm pretty sure you can just double-click on the .deb file to launch the installer. Also, the Windows version won't work unless you install Wine, and I advise against that because it won't work as well as running the Linux version.

2.) Tools -> Options is Edit -> Preferences in Linux
3.) You don't need an antivirus since there are about 0 Linux viruses actually "in the wild". There are some antivirus applications which are mostly for networked computers/servers to prevent accidentally spreading Windows viruses. This is still probably not something you need.
4.) It's easier if you just install all of those things from your package manager, synaptic.  Synaptic lets you download and install about 20,000 software packages (if you enable all software services). Some programs like skype will offer .deb downloads which you can just double-click to install. Think of .deb as the equivalent of self-extracting .exe installers on windows. What you were doing is downloading the generic Linux versions, which are usually source files you have to compile. Which is unnecessary 99% of the time.
5.) I actually don't know. Is it only in Firefox, or other things? What kind of keyboard do you have?

Edit: I hate to discredit someone else, but** I highly advise against using Automatix**. It has been known to be a potential source of problems and is completely unnecessary as everything it does can be done almost as easily a different way. For example, the mentioned audio codecs, dvd support, and more can be easily installed by these directions:
[https://wiki.ubuntu.com/RestrictedFormats?highlight=%28formats%29%7C%28restricted%29](https://wiki.ubuntu.com/RestrictedFormats?highlight=%28formats%29%7C%28restricted%29)

---

### Post by rsambuca on 2007-09-06
> **T4K3Z0U said:**
> As you may have read yesterday, I am a total beginner when it comes to Ubuntu. I now finally have it installed but have come across a problem or 2.

Problem #1 I want to install Mozilla Thunderbird. I searched for help on this forum and one suggestion in someone else's thread was to go into the add/remove option and do it there some how. The problem....... I do not have an Add/Remove button/option, I find that rather disturbing.

So next I read I could do it from Ubuntuzilla. I went to download it from there and got asked for my password, after entering it, I got this message. {failed to run gdebi-gtk '--non-interactive' '/tmp/ubuntuzilla-4.4.0-0ubuntu1-i386.deb' as user root} {The underlying authorization mechanism (sudo) does not allow you to run this program. Contact system administrator.

WTH does all that mean? and I thought I was the system administrator no?

I saved my windows version of TB to disk and tried to install the .EXE file that way, but it wouldn't let me.

Problem #2 In the version of Firefox that came with Ubuntu, there is no options tab, I can't change the home page or clear cookies and so on.

Problem #3 The appears to be no, AV on my system while using Ubuntu, which is a concern for me.

Problem #4 Everytime I try to install some software, I.E skype, real player and so on, I don't get any install option Per Se, just all the folders. As stated above I am a beginner and I have relied on Windows my whole life of computers. It may be crap but at least it was relatively user friendly.

and

Problem #5 when ever I'm typing something like this, the cursor moves to a different point and stuffs up my text. If I move the cursor to a different part of the screen, It will end up opening a hidden window or something. That is very frustrating.


Sorry to B**ch like this everyone. I know all good things take time and all, but since the installation took me like 4 days to get done and now I'm running into these problems it is a little disheartening.
I really do appreciate your help, and thank you all in advance for any advice you may have.

1. Go to the top menu bar.  Press "Applications", at the bottom of the menu that opens it says Add/Remove...

2. In FF, go to Edit, Preferences.  Same as in the Windows version.

3. Please elaborate so we can help you.

4.  I am not quite sure what you mean here.

5. That is very strange behaviour!

---

### Post by T4K3Z0U on 2007-09-06
> **thelocust said:**
> I'll try my best

1: You need automatix2 it's a program that installs a bunch of really essential programs.

2: The options tab is now the preferences tad under edit.

3: Again automatix2 you can install all of your codecs (assuming you mean audio/video)

4: The file system is different than window which is better for a few reasons but thats a little much to get into.

5: No Idea.

I'm working on some links for ya hang in there.

Thank you kindly.

I just came across problem #6, but I guess automatix is an important program.

I just went to use the update manager and it told me there are 119 updates available. Again entered my password and then got this message. {Failed to run /usr/sbin/synaptic '--hide-main-window' '--non-interactive' '--parent-window-id' '39845891' '--progress-str' 'Please wait, this can take some time.' '--finish-str' 'Update is complete' '--set-selections-file' '/tmp/tmpT_jmY9' as user root.} {The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.}

I am almost in tears.

---

### Post by thelocust on 2007-09-06
Here's instruction for [automatix2.]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#Automatix2") I'm assuming your running Feisty. Use the alternate method enter the commands in to terminal and you should be fine. Let me know if you have any questions.

---

### Post by thegreenblob on 2007-09-06
> Problem #1 I want to install Mozilla Thunderbird. I searched for help on this forum and one suggestion in someone else's thread was to go into the add/remove option and do it there some how. The problem....... I do not have an Add/Remove button/option, I find that rather disturbing.

You can install it with the terminal. Applications>Accessories>Terminal.

And do the command "sudo apt-get install mozilla-thunderbird".

> Problem #2 In the version of Firefox that came with Ubuntu, there is no options tab, I can't change the home page or clear cookies and so on.

In firefox go to Edit>Preferences.

> Problem #3 The appears to be no, AV on my system while using Ubuntu, which is a concern for me.

You don't need one.

> Problem #4 Everytime I try to install some software, I.E skype, real player and so on, I don't get any install option Per Se, just all the folders. As stated above I am a beginner and I have relied on Windows my whole life of computers. It may be crap but at least it was relatively user friendly.

Maybe automatix or easyubuntu can help? [http://www.getautomatix.com/](http://www.getautomatix.com/) [http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)

> Problem #5 when ever I'm typing something like this, the cursor moves to a different point and stuffs up my text. If I move the cursor to a different part of the screen, It will end up opening a hidden window or something. That is very frustrating.

Not sure on this one. Sorry.

Hope this helps.

---

### Post by rsambuca on 2007-09-06
T4...  What version of ubuntu did you install?  You are having some issues with sudo that clearly are not normal.  Also, I would suggest not using Automatix as it can cause upgrade problems later on.

---

### Post by thelocust on 2007-09-06
Your having some funky problems. First restart and I have a feeling that in the process of installing automatix2 you might fix that last one.

---

### Post by T4K3Z0U on 2007-09-06
[QUOTE=rsambuca;3323142]1. Go to the top menu bar.  Press "Applications", at the bottom of the menu that opens it says Add/Remove...

It did when I was using Ubuntu from boot CD. Now that Ubuntu is installed, there is no Add/Remove option under Applications, places or system. I checked dozens of times.

---

### Post by sumguy231 on 2007-09-06
I highly recommend reading this article on Automatix before installing it, this guy knows what he's talking about:
[http://mjg59.livejournal.com/77440.html](http://mjg59.livejournal.com/77440.html)

---

### Post by Beggar on 2007-09-06
as stated previously ask any advanced ubuntu user and they will tell you **AUTOMATIX IS BAD**. Now, the first step to getting this all worked out, try running 

sudo apt-get update
sudo apt-get install ubuntu-desktop

This will check to make sure that you have all of the most basic programs installed. Please let us know what the results are.

---

### Post by overdrank on 2007-09-06
> **thelocust said:**
> Your having some funky problems. First restart and I have a feeling that in the process of installing automatix2 you might fix that last one.

To Automatix and EasyUbuntu users, please read the official announcement.
[http://ubuntuforums.org/announcement.php?f=13](http://ubuntuforums.org/announcement.php?f=13)

---

### Post by sumguy231 on 2007-09-06
Also, Add/Remove should be at the bottom of 'Applications'. Maybe I missed it, what version of Ubuntu are you using exactly?

Edit: I think Automatix is bad, but I guess we should tone it down to avoid turning this into an Automatix flamefest.

---

### Post by T4K3Z0U on 2007-09-06
> **thegreenblob said:**
> You can install it with the terminal. Applications>Accessories>Terminal.

And do the command "sudo apt-get install mozilla-thunderbird".




Doesn't do anything. Asks for password, I entered it and pressed enter. It dropped 1 line asking for the command again.

---

### Post by markp1989 on 2007-09-06
> **T4K3Z0U said:**
> As you may have read yesterday, I am a total beginner when it comes to Ubuntu. I now finally have it installed but have come across a problem or 2.

Problem #1 I want to install Mozilla Thunderbird. I searched for help on this forum and one suggestion in someone else's thread was to go into the add/remove option and do it there some how. The problem....... I do not have an Add/Remove button/option, I find that rather disturbing.

So next I read I could do it from Ubuntuzilla. I went to download it from there and got asked for my password, after entering it, I got this message. {failed to run gdebi-gtk '--non-interactive' '/tmp/ubuntuzilla-4.4.0-0ubuntu1-i386.deb' as user root} {The underlying authorization mechanism (sudo) does not allow you to run this program. Contact system administrator.

WTH does all that mean? and I thought I was the system administrator no?

I saved my windows version of TB to disk and tried to install the .EXE file that way, but it wouldn't let me.

Problem #2 In the version of Firefox that came with Ubuntu, there is no options tab, I can't change the home page or clear cookies and so on.

Problem #3 The appears to be no, AV on my system while using Ubuntu, which is a concern for me.

Problem #4 Everytime I try to install some software, I.E skype, real player and so on, I don't get any install option Per Se, just all the folders. As stated above I am a beginner and I have relied on Windows my whole life of computers. It may be crap but at least it was relatively user friendly.

and

Problem #5 when ever I'm typing something like this, the cursor moves to a different point and stuffs up my text. If I move the cursor to a different part of the screen, It will end up opening a hidden window or something. That is very frustrating.


Sorry to B**ch like this everyone. I know all good things take time and all, but since the installation took me like 4 days to get done and now I'm running into these problems it is a little disheartening.
I really do appreciate your help, and thank you all in advance for any advice you may have.

with number 5, are you using a laptop, cause i had the same problem on my laptop, wt was happening is that as i was typing, i was tapping the touch pad, and clicking somewhere else in the text

---

### Post by sumguy231 on 2007-09-06
It sounds like you have serious issues if you can't use sudo. Have you done anything to the user accounts? Also, I hate to sound like a broken record but what version of Ubuntu are you using?

---

### Post by T4K3Z0U on 2007-09-06
> **Beggar said:**
> as stated previously ask any advanced ubuntu user and they will tell you **AUTOMATIX IS BAD**. Now, the first step to getting this all worked out, try running 

sudo apt-get update
sudo apt-get install ubuntu-desktop

This will check to make sure that you have all of the most basic programs installed. Please let us know what the results are.

Nothing happens. I take it I am supposed to enter it the way you wrote it and hit enter? if so it just keeps dropping down with the same command line.

> **sumguy231 said:**
> Also, Add/Remove should be at the bottom of 'Applications'. Maybe I missed it, what version of Ubuntu are you using exactly?

Edit: I think Automatix is bad, but I guess we should tone it down to avoid turning this into an Automatix flamefest.

Nope no Add/remove function available.
Version if I recall correctly is Feisty valid til '08 for desktop.

---

### Post by rsambuca on 2007-09-06
There appears to be something wrong with your basic installation.  Could you try booting the liveCD that you used and run the CD check?  If it checks out to be fine you might consider re-installing.

---

### Post by T4K3Z0U on 2007-09-06
> **markp1989 said:**
> with number 5, are you using a laptop, cause i had the same problem on my laptop, wt was happening is that as i was typing, i was tapping the touch pad, and clicking somewhere else in the text

Yes laptop. I didn't think I have my hand close enough to the mouse pad but maybe I do. Never happened in Windows.

> **sumguy231 said:**
> It sounds like you have serious issues if you can't use sudo. Have you done anything to the user accounts? Also, I hate to sound like a broken record but what version of Ubuntu are you using?

Not as far as I know. I just followed the install instructions and then went immediately to install TB.

Sorry I am real slow at typing as such and as soon as I finish 1 reply theres a dozen new ones :)
Feisty desktop.

---

### Post by T4K3Z0U on 2007-09-06
> **rsambuca said:**
> There appears to be something wrong with your basic installation.  Could you try booting the liveCD that you used and run the CD check?  If it checks out to be fine you might consider re-installing.

I did the cd check before installing it. I had to actually download three times and I burned it 5 times before it finally worked the 6th time. The 6th time being I figured Magic ISO must be the problem and it was. Once I installed Infra recorder it burned and worked like a charm.

---

### Post by thelocust on 2007-09-06
> **Beggar said:**
> as stated previously ask any advanced ubuntu user and they will tell you **AUTOMATIX IS BAD**. Now, the first step to getting this all worked out, try running 

sudo apt-get update
sudo apt-get install ubuntu-desktop

This will check to make sure that you have all of the most basic programs installed. Please let us know what the results are.
My bad, didn't mean to point you in the wrong direction. I'll have to look in to this.

---

### Post by Beggar on 2007-09-06
"Nothing happens. I take it I am supposed to enter it the way you wrote it and hit enter? if so it just keeps dropping down with the same command line."

can you please post exactly what you entered, and the output you received?

---

### Post by markp1989 on 2007-09-06
> Yes laptop. I didn't think I have my hand close enough to the mouse pad but maybe I do. Never happened in Windows.

yer it never happened in windows with me, on my laptop in windows there was a way to disable the touchpad whilst typing, so maybe the same on yours, i wish there could be a similar feature in ubuntu

---

### Post by T4K3Z0U on 2007-09-06
> **Beggar said:**
> "Nothing happens. I take it I am supposed to enter it the way you wrote it and hit enter? if so it just keeps dropping down with the same command line."

can you please post exactly what you entered, and the output you received?

I entered exactly what you posted:

sudo apt-get update

sudo apt-get install ubuntu-desktop.

No output was recieved, just the initial command line. xxx@xxx:~$

> **markp1989 said:**
> yer it never happened in windows with me, on my laptop in windows there was a way to disable the touchpad whilst typing, so maybe the same on yours, i wish there could be a similar feature in ubuntu

Oh yea, I have a button above the touch pad to disable it. I should just put batteries in my mouse and use that, coz often the touch pad is time consuming.

---

### Post by T4K3Z0U on 2007-09-06
Just to clarify, in FF under tools there is no Edit, preferences or options tab.

All there is, is, web search, downloads, add-ons, error console, page info and clear private data.


I am thinking I have D/L'd some screwed up version of Ubuntu!!???



ETA: "Sorry, posted a little early, I found it :oops:

---

### Post by Billy_McBong on 2007-09-06
> **T4K3Z0U said:**
> Just to clarify, in FF under tools there is no Edit, preferences or options tab.

All there is, is, web search, downloads, add-ons, error console, page info and clear private data.

[COLOR="Blue"]no edit isnt under the tools menu, it is its own menu to the left of tools
EDIT: o you found it
and you have some really weird problems sounds like something went wrong when you burned the CD or when you installed[/COLOR]

---

### Post by nanotube on 2007-09-06
you seem to have some problem with the basic system setup (with the sudo not working...)

boot into safe mode, and see what the content of your /etc/sudoers file is
also, when you are logged in as regular user, what is the output of command
```
id
```

---

### Post by rsambuca on 2007-09-06
Hey T4, I think the errors (or actually the lack of response in the terminal) is a cause for concern.  Most problems in linux can be fixed without reinstallation, but a bad initial installation can be pretty tough.  I suggest re-installing.

---

### Post by T4K3Z0U on 2007-09-06
> **nanotube said:**
> 
also, when you are logged in as regular user, what is the output of command
```
id
```

Um this is embarrassing, Can you put that into layman terms for me?


Just going to boot into safe mode now.

---

### Post by T4K3Z0U on 2007-09-06
> **T4K3Z0U said:**
> 
Just going to boot into safe mode now.

Scratch that.

Ok I don't know what Linux is or anything about it so I am always thinking Windows.
I just restarted my pc thinking it would give me a safe mode option but it didn't.

Is there another way I don't know about. Should I just cut my losses and re-install Ubuntu??

---

### Post by sumguy231 on 2007-09-06
To boot into recovery mode, you need to press Esc to get to the boot menu when it's doing the "1...2...3.." countdown. Then select the "recovery mode" option. When it's done booting, run id from the terminal you'll be at.
> 
Is there another way I don't know about. Should I just cut my losses and re-install Ubuntu??
At this point, I think this might be more worthwhile. If you're familiar with md5sums, you should use it to verify the .iso file you're installing from. If you don't know what that means, just try downloading it again.

---

### Post by T4K3Z0U on 2007-09-06
> **sumguy231 said:**
> 

At this point, I think this might be more worthwhile. If you're familiar with md5sums, you should use it to verify the .iso file you're installing from. If you don't know what that means, just try downloading it again.

I'm not familiar with md5sums, but I did D/L that software and used it accurately. The first 2x I D/L'd Ubuntu the sums didn't match, third time lucky., Then I did the CD test. I believe these problems have occurred during the install.

---

### Post by T4K3Z0U on 2007-09-06
I just rebooted in recovery  mode. Typed id and this is the result.

uid=0 (root)
gid=0 (root)

---

### Post by bigboy_pdb on 2007-09-07
> **T4K3Z0U said:**
> 
I did the cd check before installing it. I had to actually download three times and I burned it 5 times before it finally worked the 6th time. The 6th time being I figured Magic ISO must be the problem and it was. Once I installed Infra recorder it burned and worked like a charm.


You're having some very strange problems. I think it might be a good idea to burn a new CD using a different system from the one that you first burned them with. You should use some good quality CDs as well. I'd recommend getting CD-RWs because they're reusable and you save money (but I use them more for environmental reasons). I use TDK CD-RWs and they've worked well (even on older machines). Also, check the md5sums for the new CD (and there's an option in the boot menu where you can do a CD scan or check or something like that).

You should also check your RAM using memtest on the Ubuntu CD.

After doing those two things (successfully) you should re-install Ubuntu. If you're still getting problems, we can rule out a few things that might be causing trouble.

---

### Post by sumguy231 on 2007-09-07
> The first 2x I D/L'd Ubuntu the sums didn't match, third time lucky., Then I did the CD test. 
Ok, just double-checking. I think you might as well just try a reinstall anyway.

If you still want to try fixing it, what does /etc/sudoers look like? You can view it with less /etc/sudoers.

---

### Post by T4K3Z0U on 2007-09-07
> **sumguy231 said:**
> 

If you still want to try fixing it, what does /etc/sudoers look like? You can view it with less /etc/sudoers.

Yeah..... I'm just going to reinstall it because that code....... I have no idea what I am supposed to do with it.

---

### Post by nanotube on 2007-09-07
> **T4K3Z0U said:**
> Yeah..... I'm just going to reinstall it because that code....... I have no idea what I am supposed to do with it.

heh ok... well generally when someone gives you some "code" to type, you are supposed to open up a terminal, and type or paste in the command. so, for example, to see the content of the /etc/sudoers file, you can open up a terminal (applications> accessories>terminal), and type in
```
more /etc/sudoers
```

since the sudoers file is not world-readable, you would normally do it with sudo, like this:
```
sudo more /etc/sudoers
```

but since your sudo is messed up, you have to do it from the recovery mode. 

also, when i asked you to give me the output of command "id", same explanation applies - but i asked you to do it from your regular user, not from recovery mode. 

but anyway... if you don't have anything of value in this install, you might be better off just reinstalling. :)

---

### Post by bigboy_pdb on 2007-09-07
Compare the code that you got from using "md5sum" on the ISO to the ones on the following page:
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

If they match then the ISO image shouldn't have any flaws, meaning you don't have to download the ISO again from the Ubuntu website. However, just because you have a properly downloaded version of the ISO doesn't mean that it burned to the CD correctly. If you tried it multiple times and it failed then there could be a chance that there were still problems burning the CD the time that it appeared to work.

---

### Post by T4K3Z0U on 2007-09-07
> **bigboy_pdb said:**
> Compare the code that you got from using "md5sum" on the ISO to the ones on the following page:
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

If they match then the ISO image shouldn't have any flaws, meaning you don't have to download the ISO again from the Ubuntu website. However, just because you have a properly downloaded version of the ISO doesn't mean that it burned to the CD correctly. If you tried it multiple times and it failed then there could be a chance that there were still problems burning the CD the time that it appeared to work.

As previously mentioned, I checked the md5sums and I did the cd check before trying to install Ubuntu. The other burning problems were from trying to use Magic ISO. As I also said, I decided to use Infra recorder and thats what gave me a good bootable cd.

I am just about finished reinstalling Ubuntu now. Fingers crossed it works this time.

Also I decided to delete my third partition, so now I will just have 2.

---

### Post by T4K3Z0U on 2007-09-07
OK I've just reinstalled it, everything looks a bit better. 

But..... as it was restarting without the cd, it said something about a check being forced and when it got to about 70% it said{died with exit, something, 3} it then rebooted and worked okish. Now I shall check all those things in the terminal.

Oh yea, the add remove button is now there.

---

### Post by T4K3Z0U on 2007-09-07
> **nanotube said:**
> heh ok... well generally when someone gives you some "code" to type, you are supposed to open up a terminal, and type or paste in the command. so, for example, to see the content of the /etc/sudoers file, you can open up a terminal (applications> accessories>terminal), and type in
```
more /etc/sudoers
```

since the sudoers file is not world-readable, you would normally do it with sudo, like this:
```
sudo more /etc/sudoers
```

but since your sudo is messed up, you have to do it from the recovery mode. 

also, when i asked you to give me the output of command "id", same explanation applies - but i asked you to do it from your regular user, not from recovery mode. 

but anyway... if you don't have anything of value in this install, you might be better off just reinstalling. :)

OK I just entered those and heres the screen shot.

[IMG]http://i33.photobucket.com/albums/d51/kiwi_samurai/Screenshot-t4k3z0uTAKEZOU.png[/IMG]

---

### Post by sumguy231 on 2007-09-07
Edit: never mind, I misread the screnshot. It's 1 a.m. here and I should go to bed anyway. Disregard and read below post.

Also, while this post is here I should mention that less is way better than more. more won't even let you scroll up.

---

### Post by bigboy_pdb on 2007-09-07
You entered it incorrectly. You wrote a space where the second forward slash should be. It should read:
sudo more /etc/sudoers

---

### Post by T4K3Z0U on 2007-09-07
OK, I'm not good at quoting so here are all the screen shots of the code input into terminal.

Just as a side note, I wasn't getting anything like this before the reinstall. You will also see another problem I may have encountered.

[IMG]http://i33.photobucket.com/albums/d51/kiwi_samurai/Screenshot-t4k3z0uTAKEZOU-1.png[/IMG]

The next to screen shots are displaying the results that used up a lot of room.

[IMG]http://i33.photobucket.com/albums/d51/kiwi_samurai/Screenshot-t4k3z0uTAKEZOU-2.png[/IMG]
[IMG]http://i33.photobucket.com/albums/d51/kiwi_samurai/Screenshot-t4k3z0uTAKEZOU-3.png[/IMG]

And now the rest are what I was told to do.

[IMG]http://i33.photobucket.com/albums/d51/kiwi_samurai/Screenshot-t4k3z0uTAKEZOU-4.png[/IMG]
[IMG]http://i33.photobucket.com/albums/d51/kiwi_samurai/Screenshot-t4k3z0uTAKEZOU-5.png[/IMG]

I hope you can understand this coz I certainly can't. :oops:

Thanks again everyone.

---

### Post by T4K3Z0U on 2007-09-07
> **bigboy_pdb said:**
> You entered it incorrectly. You wrote a space where the second forward slash should be. It should read:
sudo more /etc/sudoers

OMG, this is exactly what I mean when I say I am a beginner. 
This is real confusing stuff, but quite interesting too.

Heres the new SS.

[IMG]http://i33.photobucket.com/albums/d51/kiwi_samurai/Screenshot-t4k3z0uTAKEZOU-6.png[/IMG]

---

### Post by sumguy231 on 2007-09-07
Your /etc/sudoers is ok, and sudo is working fine. That's great. Now, the error you're getting trying to install things: Make sure you're not trying to run two package managers at once, two instances of apt-get, apt-get and synaptic, you get the point. If you're not sure if any are running, try doing 'ps -u t4k3z0u' at the terminal to list all your processes.

---

### Post by T4K3Z0U on 2007-09-07
> **sumguy231 said:**
> Your /etc/sudoers is ok, and sudo is working fine. That's great. Now, the error you're getting trying to install things: Make sure you're not trying to run two package managers at once, two instances of apt-get, apt-get and synaptic, you get the point. If you're not sure if any are running, try doing 'ps -u t4k3z0u' at the terminal to list all your processes.

Oh that may have happened coz Ubuntu was doing the software update successfully yesterday.

---

