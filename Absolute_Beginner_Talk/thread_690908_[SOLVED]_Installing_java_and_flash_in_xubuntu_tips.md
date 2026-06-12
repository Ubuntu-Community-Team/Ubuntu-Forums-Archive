---
title: "[SOLVED] Installing java and flash in xubuntu tips please"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by Indy452 on 2008-02-07
Any good advice for me when installing Java and flash player? I need jave to run frostwire and I need flash for videos and youtube. I 'm running xbuntu 7.10.

I'm not trained in synaptic yet so if you can advise me in the install that would be much appreciated.

Also I need a media player. The Totem doesn't play my mp3's.

Thanks, Neal

---

### Post by spiderbatdad on 2008-02-07
download the flashplayer here:[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)
get the tar.gz...the instructions are just below it. Couldn't be simpler to install...a five year old could do it.```
sudo apt-get install ubuntu-restricted-extras
```for the rest.

---

### Post by cwbar_1 on 2008-02-07
[https://help.ubuntu.com/community/#head-5ba01a2a950ca4281bc039ebd2ab3da97af09732](https://help.ubuntu.com/community/#head-5ba01a2a950ca4281bc039ebd2ab3da97af09732)
Follow the instructions for Multimedia. 

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
 This will also take you to very good instructions on Java!
I would suggest reading the entire "Community" based support pages.  Great information!

Good luck!

---

### Post by spiderbatdad on 2008-02-07
ps use the flashplayer above...not the one in synaptic.

---

### Post by santiagoward2000 on 2008-02-08
> **Indy452 said:**
> Any good advice for me when installing Java and flash player? I need jave to run frostwire and I need flash for videos and youtube. I 'm running xbuntu 7.10.

I'm not trained in synaptic yet so if you can advise me in the install that would be much appreciated.

Also I need a media player. The Totem doesn't play my mp3's.

Thanks, Neal

Hi Indy!
Java isn't that hard to get working. Just look for it in **Add/Remove...**. I've installed **Sun Java 6 Console** and **Sun Java 6 Web Start** and FrostWire is working perfectly.
About Totem, as you are using Xubuntu, you probably have **totem-xine** (if you haven't change it). Then, to play your mp3 you need to install **libxine-ffmpeg**. To install it, look for it in Synaptic, or open a Terminal and type: ```
sudo apt-get install libxine-ffmpeg
```
Cheers!

---

### Post by Indy452 on 2008-02-08
> **spiderbatdad said:**
> download the flashplayer here:[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)
get the tar.gz...the instructions are just below it. Couldn't be simpler to install...a five year old could do it.```
sudo apt-get install ubuntu-restricted-extras
```for the rest.

I used the code in terminal and after it retrieved quite a bit of stuff its asking to configure mstt core fonts (ok)

Should I press enter?

Neal

---

### Post by jan quark on 2008-02-08
yes and run for cover

---

### Post by kesman on 2008-02-08
> **jan quark said:**
> yes and run for cover

haha =D

---

### Post by Indy452 on 2008-02-08
> **jan quark said:**
> yes and run for cover

Thanks, I've done it.  Now its kinda stuck there on configuring sun java6-bin it has an ok at the bottom of about a half a mile of disclaimer stuff but the enter does not work can I just go to file-close window or is it doing something?

Is it installed then? I know, ridiculusly simple questions I'm sure but I'm learning as I go. I learn best by doing rather than a bunch of reading about then doing.

Thanks for the help folks. 

Neal

---

### Post by santiagoward2000 on 2008-02-08
> **Indy452 said:**
> Thanks, I've done it.  Now its kinda stuck there on configuring sun java6-bin it has an ok at the bottom of about a half a mile of disclaimer stuff but the enter does not work

Hi!
To accept there, just press your keyboard's rigt key until you get to the **OK** button.
Cheers!

---

### Post by Indy452 on 2008-02-08
> **santiagoward2000 said:**
> Hi!
To accept there, just press your keyboard's rigt key until you get to the **OK** button.
Cheers!


Thanks Santiagoward2000,  that worked, now I can use frostwire Yeah!  Now I just need to get some Flash for vids.

Any takers?

I've downloaded it but I'm not sure how to get her out of the archive manager. Any tips for that?

Thanks, Neal

(by it I mean flash)

---

### Post by forrestcupp on 2008-02-08
Well, the way I like to do it is in Synaptic.  Open up Synaptic and go to Settings->Repositories.  In that window, click the Updates tab and check the boxes that say 'Pre-released updates (gutsy-proposed)' and 'Unsupported updates (gutsy-backports)'.  Then click 'Close' and press the 'Reload' button.  With those checked, Synaptic will have a more recent package of Flash that works.  Then you can do a search for flashplugin-nonfree, click the box and choose 'Mark for Installation' and click the 'Apply' button.

If you use the Syaptic/apt-get method, it will always be automatically updated for you.  You just need to enable your proposed and backports updates.

---

### Post by santiagoward2000 on 2008-02-08
> **Indy452 said:**
> Thanks Santiagoward2000,  that worked, now I can use frostwire Yeah!

You're welcome! :KS

> **Indy452 said:**
> Now I just need to get some Flash for vids.

Any takers?

I've downloaded it but I'm not sure how to get her out of the archive manager. Any tips for that?

Thanks, Neal

(by it I mean flash)

> **forrestcupp said:**
> Well, the way I like to do it is in Synaptic.  Open up Synaptic and go to Settings->Repositories.  In that window, click the Updates tab and check the boxes that say 'Pre-released updates (gutsy-proposed)' and 'Unsupported updates (gutsy-backports)'.  Then click 'Close' and press the 'Reload' button.  With those checked, Synaptic will have a more recent package of Flash that works.  Then you can do a search for flashplugin-nonfree, click the box and choose 'Mark for Installation' and click the 'Apply' button.

If you use the Syaptic/apt-get method, it will always be automatically updated for you.  You just need to enable your proposed and backports updates.

About the Flash in the repositories, I got a MD5mismatch error, even when I'd checked the 'Pre-released updates (gutsy-proposed)' and 'Unsupported updates (gutsy-backports)' boxes. I had to change the **/var/lib/dpkg/info/flashplugin-nonfree.postinst** file.
I used this guide for it: [http://ubuntuforums.org/showthread.php?t=637684&highlight=flash+mismatch+gedit]("http://ubuntuforums.org/showthread.php?t=637684&highlight=flash+mismatch+gedit")
I know it's in Spanish, so I'll try to translate it here:

1) Open a terminal and type: **sudo apt-get install flashplugin-nonfree**

2) **sudo gedit /var/lib/dpkg/info/flashplugin-nonfree.postinst**

3) On that file, search for this:
```
# verify MD5 checksum of (copied or downloaded) tarball
rm -rf install_flash_player_9_linux/
echo "821cc72359a937caef85bb4cc74ef5cd install_flash_player_9_linux.tar.gz"| md5sum -c > /dev/null 2>&1 \
|| fp_exit_with_error "md5sum mismatch install_flash_player_9_linux.tar.gz"

# unpacking and checking the plugin
tar xzf install_flash_player_9_linux.tar.gz || fp_exit_with_error "cannot unpack plugin"
echo "be5a2f9032f8fc8bccbbf5d96c5028f9 install_flash_player_9_linux/libflashplayer.so"| md5sum -c > /dev/null 2>&1 \
|| fp_exit_with_error "plugin changed, not trusted"
echo "a81fd3b03b8c6d6e5a14298110718d3f install_flash_player_9_linux/flashplayer.xpt"| md5sum -c > /dev/null 2>&1 \
|| fp_exit_with_error "plugin changed, not trusted"
```

and replace it for this:
```
 # verify MD5 checksum of (copied or downloaded) tarball
rm -rf install_flash_player_9_linux/
echo "93b7c48eaa492237b807a3ae1de65cf9  install_flash_player_9_linux.tar.gz"| md5sum -c > /dev/null 2>&1 \
|| fp_exit_with_error "md5sum mismatch install_flash_player_9_linux.tar.gz"

# unpacking and checking the plugin
tar xzf install_flash_player_9_linux.tar.gz || fp_exit_with_error "cannot unpack plugin"
#echo "a81fd3b03b8c6d6e5a14298110718d3f  install_flash_player_9_linux/flashplayer.xpt"| md5sum -c > /dev/$
#echo "13ce705df5d47422a9192b29827544e8  install_flash_player_9_linux/libflashplayer.so"| md5sum -c > /de$
#|| fp_exit_with_error "plugin changed, not trusted"
```

4) **sudo dpkg-reconfigure flashplugin-nonfree**

This did it for me. Tell us if it works!
Thanks jotix for the original guide!
Cheers!

---

### Post by Indy452 on 2008-02-08
> **forrestcupp said:**
> Well, the way I like to do it is in Synaptic.  Open up Synaptic and go to Settings->Repositories.  In that window, click the Updates tab and check the boxes that say 'Pre-released updates (gutsy-proposed)' and 'Unsupported updates (gutsy-backports)'.  Then click 'Close' and press the 'Reload' button.  With those checked, Synaptic will have a more recent package of Flash that works.  Then you can do a search for flashplugin-nonfree, click the box and choose 'Mark for Installation' and click the 'Apply' button.

If you use the Syaptic/apt-get method, it will always be automatically updated for you.  You just need to enable your proposed and backports updates.



This is the method I chose and now I'm good to go,  thanks for the help forrestcupp. I can watch all the youtube videos I want now.
No problem at all. I think I'm gonna really like this xubuntu stuff. Now on to the next issue, camera...


Neal

---

### Post by santiagoward2000 on 2008-02-08
> **Indy452 said:**
> This is the method I chose and now I'm good to go,  thanks for the help forrestcupp. I can watch all the youtube videos I want now.
No problem at all. I think I'm gonna really like this xubuntu stuff. Now on to the next issue, camera...


Neal

That's good to hear! I hope you enjoy Xubuntu as much as I do! :KS
What's the issue with the camera?

---

### Post by Indy452 on 2008-02-08
> **santiagoward2000 said:**
> That's good to hear! I hope you enjoy Xubuntu as much as I do! :KS
What's the issue with the camera?



Wellll since you asked, xubuntu is not recognizing it for some reason. I have a Canon powershot A630. I would like to be able to download pictures from camera to wherever they go in xubuntu and then be able to upload them onto photobucket.  Simple enough right?

I'm not sure where to start, maybe here...[http://ubuntuforums.org/showthread.php?t=684283](http://ubuntuforums.org/showthread.php?t=684283)

Thank you, Neal

---

