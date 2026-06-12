---
title: "This update is too stupid to be true!!!!!"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by Carlos Santiago on 2006-11-16
I was loving Ubuntu until today. I am still likeing it, but now the love has end. 

I am usint Ubuntu 6.06 (dapper) and I usually choose to perform the sugested updates.

However after the last update, it changes my keyboard map from PT to US default (both on GNOME and X)
Moreover, I had disable the click on the touchpad (I am using a laptop), and now it is on again.

It is too stupid to be true!!!!!

I would like to ask a few qustions:
 2) how can I fix the console keyboard. It was defined on install, so I didnt have to fix it. And I dont know how to.
 3) In which config file are the definitions of mousepad (I think it is the  /etc/X11/xorg.conf but I cant remember the option to add)
 3) And most of all, how can I prevent that next updates change my definitions

Thank you

---

### Post by Henry Rayker on 2006-11-16
I believe the keyboard can be reconfigured in the System > Administration > Keyboard. Additionally, I think you -COULD- do a 
sudo dpkg-reconfigure xserver-xorg 

That should ask you again which keyboard you want (but it WILL ask a bunch of other questions about things like your display and the like...If you don't know the correct answers, you may mess more up.

---

### Post by PilotJLR on 2006-11-16
> **Carlos Santiago said:**
> 

It is too stupid to be true!!!!!


Unless you are a developer, and fully understand what mistake was made, do you really think it's appropriate to make a statement such as this?

---

### Post by localuser on 2006-11-16
> **Carlos Santiago said:**
> 3) In which config file are the definitions of mousepad

If you have a synaptic touch pad, then there is a package called qsynaptics that you can install and execute.

---

### Post by Carlos Santiago on 2006-11-17
PilotJLR, an update shouldn't change your definitions, unless you explicit ask for it (with something like 'set to default').

Or do you think it would be reasonable if during an apache update, all your web pages are deleted and set to the Welcome To Apache Server page?

---

### Post by Carlos Santiago on 2006-11-17
Thank you all for your replies.

localuser: I found the solution in a forum (cant remember which) and I only need to change a config file. I think I will have to search for it again.

Henry Rayker: That procedure only changes the keyboard on X, but the keyboard on console is still using the US map. How can I change the keyboard map used by the console?
 
But my main question is still open: How can I avoid that future updates do not change my definitions?

---

### Post by localuser on 2006-11-17
> **Carlos Santiago said:**
> But my main question is still open: How can I avoid that future updates do not change my definitions?

Did you do a normal update or did you do an upgrade to 6.10?

My immediate thought is that since there isn't more noise on the forums regarding this, that perhaps you had a localized problem.  Mind you I didn't research this, but it seems to me that if a normal update was to reset everyone's configuration, that there would be much more traffic about it.

Is this the first update you've done?  Have you been doing regular updates and had this problem before?

---

### Post by Carlos Santiago on 2006-11-17
localuser, thank you for your reply

This was _not_ my first update, and I did it as I usually do: clicking on the top-right star, and then accepting the updates proposed.

Yesterday I also install wine, mozilla 1.5 for windows (to run over wine) and adobe flashplayer 9 (for windows) but that should not have anything to do with it.

I install Mozilla over Wine because I do not know other way to access sites that require flashplayer 9.

This keyboard and mouse reconfiguration appears after the reboot.

---

### Post by localuser on 2006-11-17
> **Carlos Santiago said:**
> Yesterday I also install wine, mozilla 1.5 for windows (to run over wine) and adobe flashplayer 9 (for windows) but that should not have anything to do with it.
...
This keyboard and mouse reconfiguration appears after the reboot.

It seems that you did a whole lot of things all at the same time as the normal Ubuntu update.  Since the problem happened after a reboot, could you have done something else since the previous reboot as well?

I agree that your installs *should* not have caused any problems, but then again, neither *should* the Ubuntu update have caused any problems.  So I guess the next question would be...

why immediately blame the Ubuntu update as "too stupid to be true" when its possible that it may have been something else.

---

### Post by Carlos Santiago on 2006-11-17
localuser, thx again.

My first thought was to blame the update, not the Ubuntu in general but this specific update.

However, I agree with your first post when you say that if a "normal update was to reset everyone's configuration, that there would be much more traffic about it."
Maybe it was something else, but I cant imagine what. 

In order to solve my present problem, do you know how to configure the keyboard map used by the console?

And what about the mouse?

Thankx again

Cheers,

Carlos

---

### Post by Obor on 2006-11-17
> **Carlos Santiago said:**
> I install Mozilla over Wine because I do not know other way to access sites that require flashplayer 9

There is a Flash Player 9 Beta for Linux out now. It worked for me on dapper and works fine on edgy too -  [Link]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_update_to_Flash_Player_9_Beta_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox")

---

### Post by jhenager on 2006-11-17
I had the same problem, but fixed it by adding this to my update.conf file:

stupidupdates=off

Just kidding. Hope everything works out. You could always ask for your money back. :)
There is a saying that you get more flies with honey than vinegar and I bet it applies to developers and IT people as well.
Have a nicer day!

---

### Post by localuser on 2006-11-17
> **Carlos Santiago said:**
> In order to solve my present problem, do you know how to configure the keyboard map used by the console?

And what about the mouse?

When you say console do you mean the Terminal within Gnome?

Also, your original post stated a problem with the mousepad, are you having problems with your mouse or mousepad?

---

### Post by Carlos Santiago on 2006-11-17
Hi again  localuser.
Yes, I mean Terminal within Gnome when I said console.
And also my problem is with the mousepad (I dont use mouse). I want to turn off the ability of using the pad to make a click action. For that I just want to use the buttons. Sorry for the incorrection. Ty again.

jhenager, nice answer ;-) ..... lololol
Sorry if my words seem a bit acid (like vinegar), it was really **not** my intention. As I start saying, I am loving Ubuntu. 
In my friends I am known as an Ubuntu evangelizator (I dont know if the word exists in English, but u get the idea)
Congratulations for the excellent work!

Obor, thx for the tip, I will definitely try it!

---

### Post by localuser on 2006-11-17
> **Carlos Santiago said:**
> my problem is with the mousepad (I dont use mouse). I want to turn off the ability of using the pad to make a click action.

If your mousepad is Synaptic then you can use a package called qsynaptics.  You may want to try it out to see if it does what you need.

---

### Post by PilotJLR on 2006-11-17
> **Carlos Santiago said:**
> PilotJLR, an update shouldn't change your definitions, unless you explicit ask for it (with something like 'set to default').

Or do you think it would be reasonable if during an apache update, all your web pages are deleted and set to the Welcome To Apache Server page?

No, I agree with you.

It is NOT reasonable, however, to insult the developers as 'stupid' because you have experienced a unique problem with a package.

---

### Post by seshomaru samma on 2006-11-17
I often have a similar feeling to Carlos'
My Dapper is very stable and everything runs perfectly then update and Grub changes , update and no more Aiglx , update and Skype wont run. 
I do not understnd the specifc mechanism of Linux and I am sure the developers are doing a great work , but I found it much better to not update at all once I set the system to my liking. I will also not upgrade to Edgy .
At work I update the Windows machines because of security reasons but at home I see no reason to.
just my 2 cents.....

---

### Post by Carlos Santiago on 2006-11-17
PilotJLR, I think I already explain what I meant with the sentence "too stupid to be true". However, as you deserve my best considerations, I will try one more time.

The word "stupid" was concerning the procedure that changes my configuration. 

The update that reset all my configuration was "stupid", not the developers. I didnt mean to insult anyone. For me that was clear from the very first moment, but I apologize if my words were miss understood.

---

### Post by Carlos Santiago on 2006-11-17
Obor, in my Ubuntu evangelization I came across with a friend that wants to make alive bets on [www.bwin.com](www.bwin.com)
However, for this alive bets you need the flashplayer 9. Unfortunatly your tip, that I had already tried, do not work on this site. Anyway, thank you again for it. Do you still have a better solution then using wine?

localuser, the qsynaptics package seems great, however most options appears inactive (gray) and it ask me to do the following procedures:
"please install the synaptics touchpad driver"
"please enable X shared memory config in XF86Config"
I think I had synaptics touchpad driver installed, and I dont know how to enable the X shared memory. Thank you one more time for your kind reply ;-)

seshomaru, be wellcome to this thread. If fact there are some software procedures, most frequent in MS Windows, that are stupid. Weren't that stupid procedures of some MS Windows software that make us to give a try to Linux?

Thank you all

---

### Post by localuser on 2006-11-18
> **Carlos Santiago said:**
> "please enable X shared memory config in XF86Config"

Edit /etc/X11/xorg.conf

scroll down until you see the Synaptics Touchpad input device section and add the following line to that section:

Option "SHMConfig" "true"

As far as the keyboard mapping in Terminal:

$ sudo gconf-editor

Apps | gnome-terminal | global | active_encodings

Does it show "current" as a key value?  Try adding that and see what happens.

---

### Post by jsimmons on 2006-11-18
> **PilotJLR said:**
> Unless you are a developer, and fully understand what mistake was made, do you really think it's appropriate to make a statement such as this?

As a developer myself, I fully recognized how screwed up this is. An update should NOT change configuration settings without at least asking permission from the user first.  Is Ubuntu new at this "building an OS" thing?

---

### Post by localuser on 2006-11-18
> **jsimmons said:**
> As a developer myself, I fully recognized how screwed up this is. An update should NOT change configuration settings without at least asking permission from the user first.  Is Ubuntu new at this "building an OS" thing?

Read the full thread.  I think it was determined that the likely culprit for the config change may not have been the update at all.  The OP did a lot of different things before a reboot and only after the reboot did the config change.  More than likely it was something other than the update.

---

