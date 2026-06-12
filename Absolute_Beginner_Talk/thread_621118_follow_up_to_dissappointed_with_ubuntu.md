---
title: "follow up to dissappointed with ubuntu"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by nestor5 on 2007-11-23
I had earlier posted about my failed attempts to install ubuntu, and I thank everybody who took the time to contribute their wisdom and experience. As suggested, I downloaded the text based installer, and succeeded in getting ubuntu installed on the hard drive (that was quite simple, actually) even though the actual install took over an hour to complete (what is the installer doing all that time?).
 Anyhow, I am submitting this post from Firefox, running under the new installation of ubuntu. I still have serious reservations about having ubuntu as a primary operating system, because of two frustrating experiences I am having: firstly, I downloaded and installed the wine emulator: whenever I open the terminal, and type winecfg to create the fake c drive to be used by windows apps, the machine trundles for a few seconds, and then locks up solidly: the mouse pointer freezes and even ctrl alt backspace elicits no response: I have no other option but to hit the reset button.
 To add insult to injury, wine is not even listed among the installed and installable packages, so I do not even have the option of removing and reinstalling it! My second peeve is I have read that Windows codecs can be used by the multimedia packages in ubuntu. Recognizing this, I hooked up my hard drive, with windows 98se installed, which has codecs for virtually everything under the sun, and I was hoping that when a multimedia application went hunting for codecs, it would search all mass storage devices that were connected first, before attempting to search online.I seem to have overestimated ubuntu's intelligence, because when I tried to play an mp3, kaffeine simply searched the list of available packges , and reccomended the wrong set of codecs (gstream). 
  At first I went along with its selection, and installed the gstream codecs et al. No go.
Not a sound out of the player, even though it went into visualizer mode and  was playing to all intents and purposes.These two experiences have left me very frustrated and dissappointed, and I am seriously considering downloading Freespire, or Linuxpcos, which have the ability to play multimedia files right out of the box: even Puppy Linux, whic is the undisputed champ among the lighter distros, can handle multimedia without requireing any additional add ons!

---

### Post by philinux on 2007-11-23
Get rid of the downloaded version then install from synaptic it works a treat.

Menus set up correctly everything just brill.

To sort out your problems please make a single post for each single problem that way everything will get sorted quickly and sanely

---

### Post by siciliancasanova on 2007-11-23
There is a reason why Ubuntu doesn't play MP3's out of the box.  It's made very clear all over the place Ubuntu's practices in regards to this.

Ubuntu is also not responsible for WINE's interaction with the operating system.

It's not Microsoft's fault if after installing the 100 dvds to play the sims, they somehow aren't working.  That's EA's problem.

Now I'm not suggesting that people here won't help you with your WINE issues.  However, the operating system doesn't mold to WINE, the application must fit the mold of the operating system.

---

### Post by mikewhatever on 2007-11-23
To address your multimidea problem, first, Linux can't use Windows codecs or any other software natively. Gstreemer codecs work very well in my case (should I now say Ubuntu is perfect?). Are you sure you sound settings, volume in particular are all right? Remember, Ubuntu was not made for you and you alone. If installing codecs is such an issue that you are ready to switch a distro, try Linux-Mint.

---

### Post by jken146 on 2007-11-23
> whenever I open the terminal, and type winecfg to create the fake c drive to be used by windows apps, the machine trundles for a few seconds, and then locks up solidly: the mouse pointer freezes and even ctrl alt backspace elicits no response: I have no other option but to hit the reset button.[/QUTOE]
Once you have installed wine your fake C drive should already exist (.wine in your home directory, it is a hidden file)

[QUOTE] To add insult to injury, wine is not even listed among the installed and installable packages, so I do not even have the option of removing and reinstalling it!
Yes it is.  Wine is in the universe repository.  If you haven't got this enabled, go to System > Administration > Software Sources and tick the box for "Community maintained open source software (Universe)".
Then you can go to Applications > Add/Remove and, making sure you have "All Available Applications" selected in the menu at the top right, do a search for wine and install the package.  Or alternatively, open up a terminal and type
```
sudo apt-get install wine
```

[QUOTE=siciliancasanova]
There is a reason why Ubuntu doesn't play MP3's out of the box. It's made very clear all over the place Ubuntu's practices in regards to this.[/QUOTE]
Ubuntu does not by default include any proprietary packages.  You can, of course, install them if you wish.


Do not be so quick to judge Ubuntu.  Learn how to use it first.  If you can't do that then perhaps Ubuntu isn't for you.  Good luck anyway.

---

