---
title: "Easy way to install ALSA v1.0.15?"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by aberadam on 2008-03-13
Last shot at getting sound to work properly... headphone problem... is there an easy way to install alsa 0.15?  

I've tried following the site's instructions and it's a nightmare.

---

### Post by rcsdnj on 2008-03-13
I did this on Gutsy, because my audio card's loopback ((HDA with sigmatel STAC9271D codec) wasn't working. I was advised to enable the Backports repository, then install linux-backports-modules (which contains the v1.0.15 ALSA), and it worked fine. Good luck.

---

### Post by Nepherte on 2008-03-13
If you have an intel sound card: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by stchman on 2008-03-13
> **aberadam said:**
> Last shot at getting sound to work properly... headphone problem... is there an easy way to install alsa 0.15?  

I've tried following the site's instructions and it's a nightmare.

I have a script that installs ALSA.

[http://www.stchman.com/alsa_update.html](http://www.stchman.com/alsa_update.html)

I too hated all teh typed commands so I automated the process.  The script installs 1.0.15 for Intel ICH7.  If you want another type of sound card you can modify the

```
sudo ./configure --with-cards=hda-intel
```

Line to reflect another card.

---

### Post by aberadam on 2008-03-14
Thanks a lot everyone, I've tried everything apart from stchman's script and [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) (just can't follow all that, especially since I want 0.15 not 0.14 and am using Gutsy) with no luck. 

Could you tell me in easy steps how to modify and implement the script?  I really don't know what I'm doing with Linux.  I got it into the /home folder but then it wouldn't run, but even then I'm not sure I modified the line correctly.

Here's the info from alsamixer: 

 Card: HDA Intel                                                              &#9474;
Chip: Realtek ALC861-VD

---

### Post by stchman on 2008-03-14
> **aberadam said:**
> Thanks a lot everyone, I've tried everything apart from stchman's script and [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) (just can't follow all that, especially since I want 0.15 not 0.14 and am using Gutsy) with no luck. 

Could you tell me in easy steps how to modify and implement the script?  I really don't know what I'm doing with Linux.  I got it into the /home folder but then it wouldn't run, but even then I'm not sure I modified the line correctly.

Here's the info from alsamixer: 

 Card: HDA Intel                                                              &#9474;
Chip: Realtek ALC861-VD

If it is an HDA Intel then use the script as it is.

---

### Post by aberadam on 2008-03-14
Apologies for being a pain... but how do I run the script? 

Change the permission of the script to make it executable.  To make the script executable type the following in a terminal:
        chmod 755 ~/alsa_setup.sh
        This command assumes you downloaded the script in your /home folder
- Run the script as root

I can get it into home by using some nautilus auto root thing I have, but the rest I'm not so sure of.  

If 0.15 gives me the headphone jack sense option then I don't need to install Vista!

---

### Post by aberadam on 2008-03-14
Oh hang on, by /home you mean /home/usr, I think.

---

### Post by stchman on 2008-03-14
> **aberadam said:**
> Oh hang on, by /home you mean /home/usr, I think.

I will make it easy for you.

Enter each parameter in a terminal.

```

cd ~
wget http://www.stchman.com/tools/alsa/alsa_setup.sh
chmod 755 ~/alsa_setup.sh
sudo ~/alsa_setup.sh
rm ~/alsa_setup.sh

```

First line changes to the users home folder.
Second line gets the script from my website.
Third line changes the script permission to executable.
Fourth line executes the script with root privelages.
Fifth line removes the script as it is no longer needed.

Hope this helps.

---

### Post by aberadam on 2008-03-14
I got it running!  Let's see if it fixes my sound...

---

### Post by aberadam on 2008-03-14
OK, I ran the script the first time and nothing happened, the second time and no sound, all muted.  Alsamixer is still showing as version 0.14

Looks like sound's gone.  

Thanks for all your help anyway.

---

