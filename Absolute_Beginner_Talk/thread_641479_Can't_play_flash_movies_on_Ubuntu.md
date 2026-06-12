---
title: "Can't play flash movies on Ubuntu"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by jaymel on 2007-12-15
Last night I installed Ubuntu for the first time :guitar: and I'm excited!  Now, I'm learning all the things that need to be done to get it running smoothly.  

I was emailed a link to a Flip camera video (I think it's flash) and when I clicked the link through the email it brought me to the video site, which told me I needed plugins.  I installed Gnash but it still won't play.  

Any suggestions?  I also went to [www.kidrobotlovesyogabbagabba.com](www.kidrobotlovesyogabbagabba.com) (they rock.. lol) and the video doesn't play there, either.  Any suggestions?

Also, I'm not getting sound after tweaking the
System --> Preferences --> Sound
and changed the Sound Events, Music and Movies, and Audio Conferencing to Multichannel Playback

Any ideas on these two issues?  Thanks! :)

---

### Post by SunnyRabbiera on 2007-12-15
well first I must ask do you use a amd 64 based system?

---

### Post by jaymel on 2007-12-15
I know I sound ignorant... but here goes... 

I don't know :(

I have a regular PC with Pentium 4 processor.  It's a Dell.  I hope that answers.  Is this an AMD 64 based system?

Sorry.... and stop laughing at me!  :lolflag:

---

### Post by CCNA_student on 2007-12-15
Gnash SWF stinks. Download Adobe's flash player from adobe.com. Just follow the insturctions on the web site and you should be fine. 

    Sin Cere

---

### Post by SunnyRabbiera on 2007-12-15
No, its a intel one, I just asked as flash has issues with AMD.
anyhow gnash is really just a open source version of flash 7 so you may need a more recent version of flash.
anyhow to get regular flash installed you need to use extra repositories, the one I used to get it running is by using the "multiverse" repos...
do you know how to use synaptic?
I can give you a step by step guide if you need it

> **CCNA_student said:**
> Gnash SWF stinks. Download Adobe's flash player from adobe.com. Just follow the insturctions on the web site and you should be fine. 

    Sin Cere

this might not be best as i heard there are issues by doing this

---

### Post by salamaza on 2007-12-15
you should have installed the flash plugin its works better than gnash in many situation as its 100% compatible with flash (gnash still not fully compatile).., uninstall it from syntapic or add/remove programs, acsess the page one more time and install flash.

---

### Post by CCNA_student on 2007-12-15
When I tried installing Adobe flash player from Synaptic(or Adept) I looked at the terminal output as the installer was downloading flash player and I kept getting a bad MD5 checksum so I had to install Adobe flash player manually. That is why I would suggest going to Adobe's website and installing Adobe yourself. It is very simple, the website tell you how. Make sure you download the tar.bz file.

    Sin Cere

---

### Post by SunnyRabbiera on 2007-12-15
> **CCNA_student said:**
> When I tried installing Adobe flash player from Synaptic(or Adept) I looked at the terminal output as the installer was downloading flash player and I kept getting a bad MD5 checksum so I had to install Adobe flash player manually. That is why I would suggest going to Adobe's website and installing Adobe yourself. It is very simple, the website tell you how. Make sure you download the tar.bz file.

    Sin Cere

this also does happen, but he should try it through synaptic first before trying it via adobe.

---

### Post by daradib on 2007-12-15
[http://ubuntuforums.org/showthread.php?t=636397](http://ubuntuforums.org/showthread.php?t=636397)

---

### Post by mscir on 2007-12-31
Thanks for the clear instructions. I removed Gnash and installed the Adobe player and instead of a blank spot on the page I'm now watching flash movies, your instructions worked perfectly for me. 

Cheers,
Mike

---

### Post by daradib on 2008-01-02
Glad to hear that. Happy Ubuntuing and a happy late New Year! Cheers!

---

### Post by bindatype on 2008-01-02
Do this in a terminal
```

$ sudo apt-get install flashplugin-nonfree

```

iff you use xubuntu7.10 you'll discover a problem...it is a known issue and the workaround (for now) is

```

$ wget http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb
$ sudo dpkg -i flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb
```]

---

### Post by daradib on 2008-01-02
> **bindatype said:**
> Do this in a terminal
```

$ sudo apt-get install flashplugin-nonfree

```

iff you use xubuntu7.10 you'll discover a problem...it is a known issue and the workaround (for now) is

```

$ wget http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb
$ sudo dpkg -i flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb
```]

This issue affects all *buntu distributions (using the Ubuntu repository). More information here: [http://ubuntuforums.org/showthread.php?t=636397](http://ubuntuforums.org/showthread.php?t=636397)

---

### Post by alexzzz on 2008-01-03
I had the same problem and did exactly what you said but still have problems. I can not see any flash file. "Gnash" isn't working correct for me and "flashplugin-nonfr" although installed isn't working.

Any suggestions?

---

### Post by daradib on 2008-01-04
> **alexzzz said:**
> I had the same problem and did exactly what you said but still have problems. I can not see any flash file. "Gnash" isn't working correct for me and "flashplugin-nonfr" although installed isn't working.

Any suggestions?

In Firefox, go to the address ```
about:plugins
```
Is flash listed? You can reply [here]("http://ubuntuforums.org/showthread.php?t=636397") as there are other people who may be able to help.

---

### Post by LowSky on 2008-01-04
i just manually install flash fro the .tar.gz file from their website. its very easy. just download it to your desktop then open terminal and type these commands

```
 cd /home/###/Desktop/ ( ### is you user name) 
```

```
 tar xvfz install_flash_player_9_linux.tar.gz
```

```
 cd install_flash_player_9_linux/ 
```

```
 sudo ./flashplayer-installer 
```


You will be asked a few questions:
it looks like this [COLOR="red"](anything in red is the answer you should use)[/COLOR]

Adobe Flash Player 9 for Linux

Adobe Flash Player 9 will be installed on this machine.

You are running the Adobe Flash Player installer as the "root" user.
Adobe Flash Player 9 will be installed system-wide.

Support is available at [http://www.adobe.com/support/flashplayer/](http://www.adobe.com/support/flashplayer/)

To install Adobe Flash Player 9 now, press ENTER.

To cancel the installation at any time, press Control-C. <-- <ENTER> 

NOTE: Please exit any browsers you may have running.

Press ENTER to continue... <-- <ENTER> 

Please enter the installation path of the Mozilla, SeaMonkey,
or Firefox browser (i.e., /usr/lib/mozilla): [COLOR="Red"] /usr/lib/firefox[/COLOR]

dir= /usr/lib/firefox


----------- Install Action Summary -----------

Adobe Flash Player 9 will be installed in the following directory:

Browser installation directory = /usr/lib/firefox

Proceed with the installation? (y/n/q): [COLOR="Red"]y [/COLOR]

Installation complete.


Perform another installation? (y/n): [COLOR="red"]n[/COLOR]

Please log out of this session and log in for the changes to take effect.


The Adobe Flash Player installation is complete.

Close the terminal afterwards and log out of your current desktop session, then log in again.

---

### Post by daradib on 2008-01-04
The problem with that method is that it is not "clean" with the package management. More importantly, however, it will cause problems when Flash is changed/upgraded in Ubuntu. WIth the package fix, it is very easy to uninstall, etc.

But the package is only an install and uninstall script for the file downloaded off Adobe (same as your instructions).

---

### Post by alexzzz on 2008-01-04
> **daradib said:**
> The problem with that method is that it is not "clean" with the package management. More importantly, however, it will cause problems when Flash is changed/upgraded in Ubuntu. WIth the package fix, it is very easy to uninstall, etc.

But the package is only an install and uninstall script for the file downloaded off Adobe (same as your instructions).

Problem solved. Thanks for the help!

---

### Post by CJ_Hudson on 2008-06-12
I couldn't get the package fix to work but the previous instructions work just fine. Just have to go out and purchase some Adobe software now so I don't feel guilty using their Player for free!
As far as their photo packages go, I heard Abode Lightroom is good (not for photo editing, though.)

---

### Post by CJ_Hudson on 2008-06-12
Yep. 
Updates work.
I now have intermittently crashing browser trouble from previous botched attempts (main thread, "Multimedia..." etc.)
Any clues on how to check if I have corrupted the 'kernal' (again)? And if so, how to put it right???
Cheers in advance.
Mogbug

---

