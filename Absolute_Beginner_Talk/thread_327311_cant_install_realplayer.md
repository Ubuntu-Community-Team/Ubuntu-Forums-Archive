---
title: "cant install realplayer"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by tordan on 2006-12-29
When I try to open the bin file that I downloaded from the Realplayer website it says:

Cannot open /home/tordan/Desktop/RealPlayer10GOLD.bin: No application suitable for automatic installation is available for handling this kind of file.

Great spirits of the Ubuntu, what should I do?

---

### Post by califman831 on 2006-12-29
I'm a newbie too, but it shows up in my synaptic as realplay.  You could try checking  some of the unmarked  repositories.

---

### Post by tordan on 2006-12-29
I be even more newbie than thou.
What do you mean? These are updates, codecs, or something else?

---

### Post by Perfect Storm on 2006-12-29
```
sudo nano /etc/apt/sources.list
```

add the following;

[b]## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.)
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main
[/b]

save and exit (ctrl + o | ctrl +x)


```
sudo aptitude update
sudo aptitude install realplay
```

---

### Post by tordan on 2006-12-29
got it installed now, but when I try to open streaming video from Democracy Now I cant get it to use the Realplay program. It goes to and Mplayer page and fails miserably. I changed the actions of the files in preferences on firefox, but it continues to not work. What now?

---

### Post by obsidion on 2006-12-29
> **tordan said:**
> got it installed now, but when I try to open streaming video from Democracy Now I cant get it to use the Realplay program. It goes to and Mplayer page and fails miserably. I changed the actions of the files in preferences on firefox, but it continues to not work. What now?


  Symlink the real player plugins into your firefox/plugin directory and remove the mplayer rm ones.
ie open a terminal cd to your /usr/lib/firefox/plugin directory.
Once there ls to see what is in it.
sudo rm the files mplayerplug-in-rm.so and mplayplug-in-rm.xpt
If they are there. There should be a couple of nphelix files, if not then you haven't
installed the real plugins what you need to do is sudo ln -s /realplayerdirectory/mozilla/nphelix.xpt
and reapeat for nphelix.so

Mine is in /usr/local/RealPlayer so I would substitute that for realplayerdirectory

---

### Post by tordan on 2006-12-29
Sounds really cool, but what did you ask me to do? I need uber newdie talk.

---

### Post by tordan on 2006-12-29
That was "newbie." Damn dyslexic fingers.

---

### Post by obsidion on 2006-12-29
> **tordan said:**
> That was "newbie." Damn dyslexic fingers.


  OPen a terminal ie run a console.

You will be in your home directory. 
Ok you need to answer some questions about how you finally managed to install Realplayer, did you do a system wide install ie did you sudo ./Realetc to install it or did you just install it in your home directory.

Or did you install it from the commercial repos as suggested by Art

In that case the real player plugins should already be in /usr/lb/mozilla/plugins and possibly in the firefox directory as well.

Type aboutplugins in the address bar of fiirefox put a : between about and plugins, I typed it like that as I haven't figured out how to make it not show a smilie due to the : and the p being next to each other

That will tell you what plugins you have installed. Maybe you have both the mplayer and the realplayer ones and they are not playing nice with each other.

---

### Post by tordan on 2006-12-29
I used Synaptic Package Manager.

I'm checking the plugins...

---

### Post by tordan on 2006-12-29
Yes, both are running. how do I drop the mplayer from this particular usage (streaming media)?

---

### Post by Perfect Storm on 2006-12-29
uninstall mozilla-mplayer-plugin

---

### Post by obsidion on 2006-12-29
> **Artificial Intelligence said:**
> uninstall mozilla-mplayer-plugin


 That will also take out the other media types, not just the real media ones.

Open a consol

type cd /usr/lib/firefox/plugins enter

Once there type ls enter, this will list the plugins available

now type sudo rm mplayerplug-in-rm.so enter
it will ask you for a password, type in your normal one assuming you are the first or only user
now type sudo rm mplayerplug-in-rm.xpt enter.

Now ls again to make sure they are gone and lastly cd~ enter to get back to your home directory.

Close firefox down and then open it again and recheck the plugins to make sure only one set of real media plugins are activated. Hopefully it will now call realplayer and work for you

---

### Post by tordan on 2006-12-29
Now its opening in Totem and will play. But all my audio and video applications have lost sound. Odd. Maybe unrelated. 
I'm fine watching it in totem, but the sound thing is a new hurdle.

---

### Post by obsidion on 2006-12-29
> **tordan said:**
> Now its opening in Totem and will play. But all my audio and video applications have lost sound. Odd. Maybe unrelated. 
I'm fine watching it in totem, but the sound thing is a new hurdle.


  Talk about conflicts, you installed the realplayer the totem and the mplayer plugins, you need to uninstall the mplayer and the totem ones and then do the about plugins thingie again. Then choose what you want to use for media viewing, mplayer or totem or real player. Personally I mostly use a combination of realplay and aviplay.

---

### Post by tordan on 2006-12-29
Now I got the sound but the volume is real low, even w/ volume up in amarok, main, and pre-amp.

---

### Post by obsidion on 2006-12-29
> **tordan said:**
> Now I got the sound but the volume is real low, even w/ volume up in amarok, main, and pre-amp.


  What has amorok got to do with anything, you are jumping all over the place and making helping you rather difficult. First it was how to install a realplayer bin, then it was mplayer, then totem and now amorok that is giving you problems yet you never tell us fully what you are actually doing or trying to achieve.

---

### Post by tordan on 2006-12-29
Many apologies. I am just trying to get the media thing figured out and every time I add something new or try something that is suggested, I seem to move a little backwards. Let me start all over again.

Realplayer is now installed and will open when I engage it from the applications menu. I am not given an option to select it when I open the online media.
. 
Around the same time I installed Realplayer and possibly related, I lost the sound on all my media players (amarok is what I was using to play music at the time).

I am now trying to get the sound working so that I can further configure the Realplayer to play the online media later.

What should I address first?

---

### Post by hakimaki on 2006-12-29
I've had great luck with automatix, it installed real player without a problem and works great.

---

### Post by tordan on 2006-12-29
Oh my gosh. At the behest of a friend I moved the audio cord to the on board sound card (which had always been disabled) and I have plenty of sound now. That takes care of that. Sorry to waste your time with that problem. I'm not sure where the problem was coming from, but I don't need to use the SB sound card anyway. The on board sound device will work fine.

Back to getting realplayer to work with my online media.

Its loaded (via package manager) but only accessible from the Applications menu, not when accessing from the media source itself.

---

### Post by obsidion on 2006-12-29
> **tordan said:**
> Oh my gosh. At the behest of a friend I moved the audio cord to the on board sound card (which had always been disabled) and I have plenty of sound now. That takes care of that. Sorry to waste your time with that problem. I'm not sure where the problem was coming from, but I don't need to use the SB sound card anyway. The on board sound device will work fine.

  I have never managed to get my onboard sound card working properly, not that I have tried lately, I bought a nice 5.1 pci card a while ago and it has alwways worked fine. No worries about the time wasting, just that it is easier to work on one problem at a time rather than jumping all over the place.


Back to getting realplayer to work with my online media.

Its loaded (via package manager) but only accessible from the Applications menu, not when accessing from the media source itself.

 
  OK I would uninstall the other plugins if any, ie totem-plugins and the mplayer ones, whatever they are called on your system, use synaptic and the search option for ease of use.
  You might be able to get in to call realplay and use it as a standalone app rather than as an embedded app in firefox if you want to do it that way. Rather than the bit I have described below, when firefox gets to a stream or file that it doesn't recognise it asks what you want to open it with, you might be able to chose realplay it should be in the /usr/bin directory. 
 Then I would do the about plugins enquirey again and see where you are at. Then let us know what you have installed there and we will go from there. It seems like you are getting some form of conflict. If the nphelix plugins from realplayer are not installed then it is going to require some command line use, hopefully that is not too scarey. You just have to be careful to get it right.

---

### Post by Xonos on 2006-12-29
I didnt like mplayer too much..

---

### Post by tordan on 2006-12-29
Uninstall/reinstall, got it working. 
Yer awesome. Peace.

---

### Post by obsidion on 2006-12-29
> **tordan said:**
> Uninstall/reinstall, got it working. 
Yer awesome. Peace.  

  Be interesting to know what caused the hassles, rather than using the Microsoft method of uninstalling and reinstalling. However glad you got it going, linux can be a steep learning curve but it is very satisfying when you do get something going that has been a hassle for you. I recently decided to sit down and work out how to get lm-sensors working with ksensors, was a great thrill to finally have cpu temp and fan speed displayed on the task bar :)

---

