---
title: "Auto-Notify in Thunderbird mail?"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by discmaster on 2007-05-14
I set Thunderbird mail up once before, (2 separate accts.) & it would "Auto-Notify" of new mail with a small pop up window, & maybe a "sound" (I don't remember).

I can't seem to find a way to do it now. Is it in "settings", or do I need to install something else?

---

### Post by scrooge_74 on 2007-05-14
i got around that installing an xubuntu package for mail notify then I configure it to check on my mail

---

### Post by eltorodeoro on 2007-05-14
as far as i know, tbird 2.0 does it automatically.

---

### Post by discmaster on 2007-05-14
I installed this from Synaptic & I was just looking at it again, & I have the 1.5 vers. I guess I need to update...

---

### Post by vtel57 on 2007-05-14
T-bird --> Edit --> Preferences --> General --> When New Messages Arrive --> Advanced.

---

### Post by scrooge_74 on 2007-05-14
> **vtel57 said:**
> T-bird --> Edit --> Preferences --> General --> When New Messages Arrive --> Advanced.

That means you have to have Thunderbird running all the time?

---

### Post by discmaster on 2007-05-14
> T-bird --> Edit --> Preferences --> General --> When New Messages Arrive --> Advanced. Hmm...now that is odd; mine are already checked by default.

BTW, what is the terminal command for downloading Thunderbird 2.0?

---

### Post by scrooge_74 on 2007-05-14
sudo apt-get install mozilla-thunderbird

---

### Post by discmaster on 2007-05-14
> sudo apt-get install mozilla-thunderbird

Thanks - It tells me I already have the latest vers., but when I click Help>About, it says:

> version 1.5.0.10 (20070403) Isn't 2.0 the latest?

---

### Post by vtel57 on 2007-05-14
> **scrooge_74 said:**
> That means you have to have Thunderbird running all the time?

That's correct. My T-bird runs all the time in Work Space #4. It's set to check all my email accounts every 15 minutes. I use the audio alert. Works well. I use it this way in all my distros. :)

---

### Post by vtel57 on 2007-05-14
> **discmaster said:**
> Thanks - It tells me I already have the latest vers., but when I click Help>About, it says:

 Isn't 2.0 the latest?

v2.0 is probably NOT in the repos yet, nor will you see it there for a while. You can manually install T-bird 2.0 from a download at Mozilla.

---

### Post by discmaster on 2007-05-14
> That's correct. My T-bird runs all the time in Work Space #4. It's set to check all my email accounts every 15 minutes. I use the audio alert. Works well. I use it this way in all my distros. Mine must be broken...:confused: 

Both of those boxes are checked, but it doesn't give me either alert; in fact, when I click on "preview sound", I hear nothing. (& yes, I can hear other sounds, audio files are working).

Any ideas?

---

### Post by discmaster on 2007-05-14
> You can manually install T-bird 2.0 from a download at MozillaI did download it, how do I install from the desktop file that I have there? You have to understand I am a complete newb.!

---

### Post by evilc on 2007-05-14
> **discmaster said:**
> I did download it, how do I install from the desktop file that I have there? You have to understand I am a complete newb.!

Open TB tar file and extract the TB folder to file sytem/ opt folder, then on panel add to panel select(on top) custom application.. name - thunderbird, browse to opt folder select thunderbird.. click "no icon" again browse to opt folder.. TB... icons pick tb-icon finish. You should have TB icon on task bar which will start thunderbird.

---

### Post by discmaster on 2007-05-14
> Open TB tar file and extract the TB folder to file sytem/ opt folder

Extraction not performed

You don't have the right permissions to extract archives in the folder "/opt"

what do I do?

---

### Post by vtel57 on 2007-05-14
> **discmaster said:**
> Mine must be broken...:confused: 

Both of those boxes are checked, but it doesn't give me either alert; in fact, when I click on "preview sound", I hear nothing. (& yes, I can hear other sounds, audio files are working).

Any ideas?

I had the exact same problem in Mepis. [HERE](http://www.linuxquestions.org/questions/showthread.php?p=2718183#post2718183)'s how I fixed it.

---

### Post by discmaster on 2007-05-14
Sorry vtel, but here again, just a wee bit over my head... :(


At this point I am trying to update to 2.0, but I am fighting that one all the way to the bank too, since I don't understand the whole permissions thing. I read a thread on here dated from '05, tried  but it didn't work...

---

### Post by vtel57 on 2007-05-14
Ooops! My apologies, my friend. We all have to start somewhere. One day, you'll be the one helping out the new folks. ;)

[HERE](http://tuxicity.wordpress.com/2007/01/24/install-native-mozilla-thunderbird-20-beta-2-on-ubuntu/)'s a decent tutorial on installing T-bird in Ubuntu. Just follow the instructions.

About the sound problem... If your other system sounds are working fine, then the problem I had in Mepis may also be your problem. Mepis had installed the incorrect libesd library files on my system. I need to correct that. You can check to see what libesd is installed on your Ubuntu system by going to Synaptic and using the search feature. Search for "libesd". If you see that libesd0 is installed instead of libesd-alsa, you can just install libesd-alsa while you're there. It should be in that list also. 

This may or may not be your problem with sounds in TB. I can't really tell from the info we've discussed so far.

Luck!

~Eric

---

### Post by evilc on 2007-05-14
> **discmaster said:**
> Sorry vtel, but here again, just a wee bit over my head... :(


At this point I am trying to update to 2.0, but I am fighting that one all the way to the bank too, since I don't understand the whole permissions thing. I read a thread on here dated from '05, tried  but it didn't work...
No problem. easy way :)

Open the tar file save the extract to where you can find it easy then open nautilus in admin rights ie sudo nautilus (terminal mode) find TB r/click copy then open opt folder paste.

---

### Post by discmaster on 2007-05-14
Quick question - Am I gonna lose my messages in this process? If so, how to back them up?

---

### Post by vtel57 on 2007-05-14
Ummm... maybe/maybe not. Just to protect yourself, though, you can copy and save the entire .mozilla-thunderbird directory in /home/<your username>. You need to have Nautilus displaying hidden files to see it: Nautilus --> View --> Show hidden files. Just RIGHT click on .mozilla-thunderbird and COPY it to somewhere safe. 

Once you install TB 2.0 and run it once, a new .mozilla-thunderbird directory will be made. PASTE your old one over into the /home/<your username> directory. It will warn you that a directory by that name already exists. Just overwrite ALL.

However, you may not need to do any of this. The new installation of TB should use the existing directory.

Having fun yet? ;)

---

### Post by expatCM on 2007-05-14
Are you asking for notification when messages are downloaded by Thunderbird (so Thunderbird is running all the time) or are you asking for notification when messages arrive on an ISP's mail server prior to downloading so that you can filter out the spam?

If it is the later .....  you may want to think about Mailwasher.  I have the Windows version running under Wine and it works well but there is also a Linux version available.  An icon flashes in the system tray when new messages are received.  Sound is supported but I have forgotten what is the trigger.
[http://mailwasher.net/](http://mailwasher.net/)

---

### Post by discmaster on 2007-05-14
>  	Are you asking for notification when messages are downloaded by Thunderbird (so Thunderbird is running all the time) or are you asking for notification when messages arrive on an ISP's mail server prior to downloading so that you can filter out the spam?

I usually keep my mail pgm. open all the time, as vtel said he does. I was wondering; if I keep it open on another side of the cube, I guess I will still get the notify sound, but what about the pop-up window?

---

### Post by scrooge_74 on 2007-05-15
> **vtel57 said:**
> Ummm... maybe/maybe not. Just to protect yourself, though, you can copy and save the entire .mozilla-thunderbird directory in /home/<your username>. You need to have Nautilus displaying hidden files to see it: Nautilus --> View --> Show hidden files. Just RIGHT click on .mozilla-thunderbird and COPY it to somewhere safe. 

Once you install TB 2.0 and run it once, a new .mozilla-thunderbird directory will be made. PASTE your old one over into the /home/<your username> directory. It will warn you that a directory by that name already exists. Just overwrite ALL.

However, you may not need to do any of this. The new installation of TB should use the existing directory.

Having fun yet? ;)

It does, infact my thunderbird folders come from the time I was using Sarge, then Dapper, later Edgy (which I upgraded to Feisty)

---

### Post by vtel57 on 2007-05-15
I thought so, too. I just wanted to give him the option to back-up his .moz-tb directory, just in case. ;)

---

### Post by discmaster on 2007-05-15
Got it working, (mostly) thanks to all for putting up with such a newb!!!

I have 2 accts., and only acct. 1 is giving me the pop-up notification.  2nd. acct.,  when receiving  mail, will pop up, but it says "acct 1 has 0 messages".  ???

Most be an account setting that is set wrong somewhere, but I cant' seem to find it. Where to look? I believe I went thru everything/preferences/properties/server settings...


Also, I am still not getting any sound notify; I will refer back to the earlier posts to try to remedy the problem. Not a necessity, but would be nice, since it is offered...

---

### Post by vtel57 on 2007-05-15
Keep bangin' away at it. You'll figure it out. :)

---

### Post by discmaster on 2007-05-15
My progress thus far;

libesd-alsa is installed, I checked synaptic. Notify sound still wouldn't play. I reinstalled it anyway. Then, downloaded a "chime" wav. file, selected it as "custom" , & now it does play...on the first message I receive, along with the pop up. All messages after that just come thru with no notify. (pop up or chime)

& still...
>  

I have 2 accts., and only acct. 1 is giving me the pop-up notification. 2nd. acct., when receiving mail, will pop up, but it says "acct 1 has 0 messages". ???

If anyone has a solution, it would sure save some time! I don't mind looking & researching a problem if I know where to look, but spending 3 hrs. to set this thing up???? :lolflag: 

Yes, I am leaving T-bird open, minimized...

---

### Post by vtel57 on 2007-05-15
You're making progress... ;)

---

### Post by discmaster on 2007-05-15
> You're making progress... 3 + hrs. to set up email is progress? :( 

:lolflag:

---

### Post by vtel57 on 2007-05-15
HAHA! Wait till you get it all set up the way you want and then use the rm -R command in terminal and delete some critical component of the system and have to reinstall and customize everything again. Then do that two or three more times. It's a learning experience.

;)

---

### Post by discmaster on 2007-05-16
> HAHA! Wait till you get it all set up the way you want and then use the rm -R command in terminal and delete some critical component of the system and have to reinstall and customize everything again. Then do that two or three more times. It's a learning experience.

While I don't understand all that, (m -R command) I can appreciate it; coming from a windows environment, I have hosed a perfectly well functioning system more than once, including using a nasty partitioning tool, lol!

BTW, the mail is working "mostly" right. Notify works, "mostly" I gave up fooling with it anymore & am just letting it do its' thing! :D

At least I am receiving the mail & it is going to the correct folders, & that is the most important part, I guess.

---

### Post by vtel57 on 2007-05-16
Yeah. Sometimes, you just have to step away from it for a bit. A week or so from now, you'll be trolling some forum and you'll see a solution for your exact same problem. Sometimes, it just falls in your lap when you're not even looking for it.

Have FUN with it! :)

---

