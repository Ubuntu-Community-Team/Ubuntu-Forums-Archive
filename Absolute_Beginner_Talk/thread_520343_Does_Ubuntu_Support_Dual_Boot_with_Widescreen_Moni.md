---
title: "Does Ubuntu Support Dual Boot with Widescreen Monitor?"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by jenson on 2007-08-08
Hi guys,

I'm planning to dual boot Ubuntu with my current Windows XP on my Toshiba Satellite M30 with 15" Wide Screen monitor.

I would like to know whether Ubuntu support Widescreen Display? Also, how am I going to install Ubuntu on my current notebook computer/laptop? I intend to create another partition using Partition Magic or any better software you can offer (if they are free and nice), and to install Ubuntu on the second partition?

Sorry I'm quite new in Linux as well as Ubuntu, please pardon me if I make a stupid question.

I tried installing clean Fedora before as well as dual boot with XP, it installed properly but when everything is done and I boot into Linux, the screen is totally blank and nothing appear with the hard disk loading something. I try to search around various Linux forums, but unable to find any solution to it.

Thus, until I found Ubuntu, I still have this question in my mind, I don't want to risk installing it if it does not support widescreen display.

Thanks.

Regards,
Jenson

---

### Post by Mr. Svinlesha on 2007-08-08
The short answer is no, although you're screen won't go black.  You just won't 1440x900 as an option for screen size.  You have to manually configure your xorg.conf file in order to to make it work.  A bit tricky the first time you do it, but once you know how, it takes about 10 minutes.

Here's a walk-through:


1)  Make a backup of your xorg.conf file.  VERY IMPORTANT!

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

2)  Edit the file: I prefer the following command to the “nano” one:

gksudo gedit /etc/X11/xorg.conf

3)  You should navigate down to the “Monitor Section” and add the following lines:

HorizSync	30-81  (xx-xx)
VertRefresh	56-75  (xx-xx)

where xx – xx are the values for your specific monitor.  These values can be easily found by Googling your monitor's name. (30-81 and 56-75 are the values for my monitor.  Yours will be different, probably).

When you're done, at this point, xorg.conf should look something like this:


Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 28-64
VertRefresh 43-60
EndSection

 
4) Now, the next bit is a little tricky.  You should have xorg.conf open in gedit.  Open a new terminal and type in:

gtf horizontalresolution verticalresolution refreshrate

Where “horizontalresolution” is, in this case, 1440, “verticalresolution” is 900, and, for my monitor at any rate, “refreshrate” is 60.  In other words, the command here would be “gtf 1440 900 60.”  When you hit enter Ubuntu will generate a “modeline” for you.  Copy and paste it into the xorg.conf Section "Monitor" under “Vertrefresh” and above “EndSection.”


5)  Navigate down to “Section Screen.”  You may have several such sections – I did.  (This is the step I missed, by the way, that was so simple.)  It should look something like this:


Section "Screen"
    Identifier    "Default Screen"
    Device        "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Monitor        "CM752ET"
    DefaultDepth    16
    SubSection "Display":
        Depth        16
        Modes      "1280x1024" "1024x768"
    EndSubSection
EndSection


On the “modes” line, add your desired resolution in quotations (“1440x900”).  Just to make sure I added that line to every “Section Screen” in my xorg.conf file, in front of the "1280x1024" entry.

6)  Save gedit.  Close all open programs.  Hit Ctrl-Alt-Backspace.  Ubuntu restarts.

That *should* do the trick.  If it doesn't, let me know and I'll add a couple more steps.

:)


You can find a helpful walkthrough here:

[http://ubuntuforums.org/showpost.php?p=129379&postcount=21](http://ubuntuforums.org/showpost.php?p=129379&postcount=21)


Finally: if the screen is too narrow, don't forget to use the monitor's auto-adjust function.

---

### Post by jenson on 2007-08-08
Hi Mr. Svinlesha,

First of all, thanks for replying to my thread.

It's really a lot of steps there! OMG, imagine a newbie like me have to try to do this all together. I'm using a Toshiba Satellite M30 series notebook/laptop. I would be able to look for the xx - xx figures too on Google? I will try that.

I'm going to try it later at home to make Ubuntu the second OS on my laptop. I've long waited for a stable and nice Linux to be installed. Due to my work, I still need to do some work on Windows, but the rest of the time I think I would be using happily with Linux once I get used to everything with Ubuntu =)

But, I will try your guide later, but no promise I can follow all the way through. LOL

Those steps look complicated to me >.<"

I will have a tough time and good start to learn using command line once again :lolflag:

Thanks again Mr. Svinlesha!

Regards,
Jenson

---

### Post by Mr. Svinlesha on 2007-08-08
Don't worry.  Just take your time and do them step for step.  You might miss something the first time, but be sure to back up xorg.conf and you'll be fine.

Good luck!

---

### Post by domzo on 2007-08-08
Xorg config is pretty specific to your setup but you may not have to actually manually edit your xorg.conf file.

I am using a Dell widescreen monitor, and in my "installation notes" I have written:

Widescreeen support:
Install: xorg-driver-fglrx
Reconfigure xconf using: sudo dpkg-reconfigure xserver-xorg
when this runs select the fglrx driver and select 1680*1050 as one of the supported resolutions. (use spacebar to toggle select)

This is what worked for my setup, but it can be applied generally.
i.e. find the right driver (google helps), then reconfigure to use this driver.
Again though take a backup of your xorg.conf file before you do anything.

And if it breaks, cp the backup over the edited file and try again:
sudo cp /etc/X11/xorg.conf_backup  /etc/X11/xorg.conf

Editing xorg.conf by hand is a thankless task and to be avoided if possible!!

---

### Post by jenson on 2007-08-08
> **Mr. Svinlesha said:**
> Don't worry.  Just take your time and do them step for step.  You might miss something the first time, but be sure to back up xorg.conf and you'll be fine.

Good luck!

Ok, I will try that. The backup is as simple what we do like copying it to another location, as simple as that? Sorry, I think I shouldn't ask this :-#](*,)

---

### Post by jenson on 2007-08-08
> **domzo said:**
> Xorg config is pretty specific to your setup but you may not have to actually manually edit your xorg.conf file.

I am using a Dell widescreen monitor, and in my "installation notes" I have written:

Widescreeen support:
Install: xorg-driver-fglrx
Reconfigure xconf using: sudo dpkg-reconfigure xserver-xorg
when this runs select the fglrx driver and select 1680*1050 as one of the supported resolutions. (use spacebar to toggle select)

This is what worked for my setup, but it can be applied generally.
i.e. find the right driver (google helps), then reconfigure to use this driver.
Again though take a backup of your xorg.conf file before you do anything.

And if it breaks, cp the backup over the edited file and try again:
sudo cp /etc/X11/xorg.conf_backup  /etc/X11/xorg.conf

Editing xorg.conf by hand is a thankless task and to be avoided if possible!!

Hi domzo,

So do you mean Ubuntu does come with some preset resolution support for certain type of widescreen display?

Regards,
Jenson

---

### Post by jenson on 2007-08-08
hmm. by the way guys, if the OS selection screen give me errors, does that means I would have lost of all my data and I have to reformat everything and start all over again? >.<" I would hate that to happen on me -.-"

---

### Post by domzo on 2007-08-08
> **jenson said:**
> Hi domzo,

So do you mean Ubuntu does come with some preset resolution support for certain type of widescreen display?

Regards,
Jenson

Hi,

Well it certainly has the fglrx driver in the 'restricted' repositories which you can enable through synaptic or adept.  If you have an ATI graphics card in your machine it might be worth trying this.


As to your other question, I'm not sure what errors you mean. If you have messed around with xorg.conf and now the display won't work, just use the command line to copy the backup you made over the messed up file as mentioned earlier

Breaking the X display won't lose you data though no.

hope that helps.

---

### Post by jenson on 2007-08-08
> **domzo said:**
> Hi,

Well it certainly has the fglrx driver in the 'restricted' repositories which you can enable through synaptic or adept.  If you have an ATI graphics card in your machine it might be worth trying this.


As to your other question, I'm not sure what errors you mean. If you have messed around with xorg.conf and now the display won't work, just use the command line to copy the backup you made over the messed up file as mentioned earlier

Breaking the X display won't lose you data though no.

hope that helps.

Hi Domzo,

Thanks for the reply, so does that means i would not need to worry about changing xorg.conf file is my screen resolution is available during the setup? Btw, can I choose a lower resolution during installation, and only when the installation finish I go and modify the xorg.conf or following your steps?

Thanks.

Regards,
Jenson

---

### Post by Mr. Svinlesha on 2007-08-08
**jensen**:

Sorry I wasn't clearer about that earlier.  The Ubuntu set-up does include some widescreen settings.  It *doesn't* include the setting 1440x900.  That particular setting is for some reason the only one my monitor can use without an extensive blurring effect.

*If* you need 1440x900 pixels on your screen, you'll probably have to go through the steps I outlined above.  If not, there are other settings that might work:1280x800, for example, and 1280x760.

During set-up Ubuntu starts with a default screen resolution.  It works fine, but things look a bit fat on widescreen.  After you've installed, go to System (upper left corner of the screen)> Preferences > Screen resolution.  From there you can set your desired resolution (if it's available).

---

### Post by haricharan on 2007-08-08
> **jenson said:**
> Ok, I will try that. The backup is as simple what we do like copying it to another location, as simple as that? Sorry, I think I shouldn't ask this :-#](*,)

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.original
```

---

### Post by jenson on 2007-08-09
> **Mr. Svinlesha said:**
> **jensen**:

Sorry I wasn't clearer about that earlier.  The Ubuntu set-up does include some widescreen settings.  It *doesn't* include the setting 1440x900.  That particular setting is for some reason the only one my monitor can use without an extensive blurring effect.

*If* you need 1440x900 pixels on your screen, you'll probably have to go through the steps I outlined above.  If not, there are other settings that might work:1280x800, for example, and 1280x760.

During set-up Ubuntu starts with a default screen resolution.  It works fine, but things look a bit fat on widescreen.  After you've installed, go to System (upper left corner of the screen)> Preferences > Screen resolution.  From there you can set your desired resolution (if it's available).

Hi Mr. Svinlesha,

I have successfully installed Linux on my laptop, and yes, it installed nicely with my 1280 x 800 screen resolution. But I have problem installing application. I think I have to learn from scratch to be a better Ubuntu Linux user =) I like it a lot, it's a very cool OS to have.

Regards,
Jenson

---

### Post by jenson on 2007-08-09
> **haricharan said:**
> ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.original
```

Hi haricharan,

Thanks for the command, a newbie like me needs it a lot, I learnt a bit of Unix commands during my college time but I have long forgotten most of them. But I never learnt how to install program in Unix, thus I'm having problem in installing programs.

I think I need to search for tutorials like from beginner to intermediate user for Linux  >.<"

Regards,
Jenson

---

### Post by haricharan on 2007-08-10
you are welcome....everyone is a newbie...just in diff stages..so dont worry!!...you shud be fine....

---

### Post by jenson on 2007-08-12
> **haricharan said:**
> you are welcome....everyone is a newbie...just in diff stages..so dont worry!!...you shud be fine....

So far I'm alright, hehe. Thanks to the helps from you guys. however, I do have some problems to uninstall the Java runtime environment that i have manually installed previously and unable to configure it successfully as a plugin to Mozilla Firefox, now I don't know how to unisntall it.

When I first get it installed, I can't configure as the system replied me with Permission denied, means I can't configure the plugin part after the successful installation. I've manage to install another copy of Jre1.6.0_02 though but the old one remains on my Desktop still. I don't know how to get rid of that extra copy.

When I do **su** in my Terminal window, I entered in my password, but they told me that the system failed to authenticate root user.

Hmmm..

Regards,
Jenson

---

### Post by haricharan on 2007-08-16
you **don't** have to type **su **and type the command in the next line

use **sudo <command>.... **it wud automatically ask u for ur password....

---

### Post by Arthur Archnix on 2007-08-16
I'm not sure if I've missed it, but in general widescreen is well supported. To know how to set-up yours you need to know your graphics card. Posting the output of lspci will determine what commands you need to run in order to get your resolution up to snuff.

---

### Post by Paul133 on 2007-08-16
When you said "widescreen", did you mean 1280x800? That's supported and can be detected. 1440x900 is not automatically detected. As for installing programs, use Synaptic, which can be found in System -> Administration -> Synaptic Package Manager.

---

### Post by jenson on 2007-08-17
Thanks for the replies, Arthur and Paul.

Yes it is 1200x800 and it supported it pretty well and I don't need to take any action to configure it too. Now it's the wireless connection that I have yet to try, I would give it a try at a later time and see whether I can get a driver to get it working if it's found not working =)

Thanks for all the great replies and helps given.

I really love this community/forum =)  Feel great to be part of the family.  :guitar:

Regards,
Jenson

---

