---
title: "Can't find programs?  How-To Enable Sources"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by spiderbatdad on 2008-02-10
I see a lot of new Gutsy users unable to find packages or getting error messages related to: E: Couldn't find package 

By default Gutsy enables the universe and multiverse packages. If, however, the user installed Gutsy without having a working internet connection, the sources get commented out. 

The simplest method is to navigate to System>>Administration>>Software Sources. Enter password, and check each window. Unchecking CD as a source in the lower window is often preferred to stop Ubuntu from asking you to insert the CD when installing software distributed on the CD as optional.
Additionally you can enable Canonical sources under the Third-Party Software tab. And you can control updates under the Updates tab. This post has another intent though. To help new users discover the command line and file system, and open a graphical text editor with root permissions to edit a root file.

This post is intended to help others, in searching the forum, find out how to enable their sources list.
First open a terminal window by navigating to Applications>>Accessories>>Terminal

Now open the /etc/apt/sources.list with a text editor in administrative mode:```
gksu gedit /etc/apt/sources.list


NOTE: KDE and Xubuntu use text editors other than gedit.
 sudo mousepad works in Xubuntu and
 sudo kate for KDE.
```

Now edit the file by removing the # marks at the beginning of lines containing download locations. This is called uncommenting. Make the file look similar to the example below. Generally, the sources to be uncommented will be preceded by the line: "# Line commented out by installer because it failed to verify." Note: Do not uncomment that line itself. Instead uncomment the line below it: deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted, for example.


```
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Alpha i386 (20071129.3)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
# Line commented out by installer because it failed to verify:
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
# Line commented out by installer because it failed to verify:
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
# Line commented out by installer because it failed to verify:
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe
# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
# Line commented out by installer because it failed to verify:
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
# Line commented out by installer because it failed to verify:
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
# Line commented out by installer because it failed to verify:
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu hardy-security main restricted
# Line commented out by installer because it failed to verify:
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu hardy-security universe
# Line commented out by installer because it failed to verify:
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
# Line commented out by installer because it failed to verify:
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
```


Save the file by clicking the floppy disk image near the top of the window, and close.

Now update synaptic package manager by running, in the terminal:

```
sudo apt-get update
```

Congratulations and welcome to Ubuntu Linux

---

### Post by JoshuaRL on 2008-02-10
Nice.

+1

---

### Post by Crashmaxx on 2008-02-10
There is an easier way to do this. Just go to System>Administration>Synaptic Package Manager and select Settings>Repositories.

Under the "Ubuntu Software" tab, just check the sources you want. In this case, make sure Universe and Multiverse are selected. Then click "Close" and "Reload", that's it.

Now all the apps will show up in Synaptic Package Manager, Add/Remove, and when you use apt-get.

---

### Post by spiderbatdad on 2008-02-10
:popcorn:

---

### Post by ahuman on 2008-02-20
> **Crashmaxx said:**
> There is an easier way to do this. Just go to System>Administration>Synaptic Package Manager and select Settings>Repositories.

Under the "Ubuntu Software" tab, just check the sources you want. In this case, make sure Universe and Multiverse are selected. Then click "Close" and "Reload", that's it.

Now all the apps will show up in Synaptic Package Manager, Add/Remove, and when you use apt-get.
[B][COLOR="Purple"]Would any of you tell me what you believe Crashmaxx meant by "reload"? Does it mean "Apply" or  "Restart computer"?

Also: Please tell me if this screenshot would indicate that Ubuntu-Restricted-Extras have been successfully/perfectly installed:[/COLOR][/B]

[img]http://img54.imageshack.us/img54/2811/screenshotsynapticpackazs7.png[/img]

---

### Post by spiderbatdad on 2008-02-20
:popcorn:

---

### Post by ahuman on 2008-02-20
**Since when did this become a non-discussion forum? :confused:**

---

### Post by spiderbatdad on 2008-02-20
:popcorn:

---

### Post by Crashmaxx on 2008-02-21
> **ahuman said:**
> [B][COLOR="Purple"]Would any of you tell me what you believe Crashmaxx meant by "reload"? Does it mean "Apply" or  "Restart computer"?

Also: Please tell me if this screenshot would indicate that Ubuntu-Restricted-Extras have been successfully/perfectly installed:[/COLOR][/B]


The "Reload" button is in the screenshot you posted. I've circled it for you. You don't need to restart anything, and "Apply" installs the packages you've selected. Hope that makes it clearer.
[img]http://ubuntuforums.org/attachment.php?attachmentid=60348&stc=1&d=1203640145[/img]

---

### Post by himagain on 2008-03-11
Hi folks,

In my never-ending quest to make Linux intelligible to the other 92% of the world, (ME!) I find the greatest stumbling block after all these years is still the same:
Needlessly confusing the refugees (trying to escape M$) with cryptic and dare I say it - archaic advice - to use the deadly black screen. 
Linux and the world has moved on tremendously since I was attacked in the earliest Linux forums for daring to suggest that a GUI was a good thing for evolution.
Most things are accessible today via familiar and friendlier GUI's (for the very young or new black-screeners, it means a graphical(or good)) user interface. 

There are a couple of well-meaning posts in this very column that precisely show what I mean:
1. A long very confusing (has to be) and DANGEROUS habit of accepting black-screen-of-death advice to do something that a very simple program does extremely well ( within the limits of typically poor Linux user docs) SYNAPTIC.

It is also well to note that for 90% of refugees, the Kubuntu interface is much more familiar - and dare I say saner in a real user world than Gnome.  I would advise any new user to start with Kubuntu as KDE is just like THAT one. 

Please note that these are constructive comments, not destructive and meant to help usher in a new world without a Borg .... :-)

Peace!

---

### Post by spiderbatdad on 2008-03-11
> **himagain said:**
> Hi folks,

In my never-ending quest to make Linux intelligible to the other 92% of the world, (ME!) I find the greatest stumbling block after all these years is still the same:
Needlessly confusing the refugees (trying to escape M$) with cryptic and dare I say it - archaic advice - to use the deadly black screen. 
Linux and the world has moved on tremendously since I was attacked in the earliest Linux forums for daring to suggest that a GUI was a good thing for evolution.
Most things are accessible today via familiar and friendlier GUI's (for the very young or new black-screeners, it means a graphical(or good)) user interface. 

There are a couple of well-meaning posts in this very column that precisely show what I mean:
1. A long very confusing (has to be) and DANGEROUS habit of accepting black-screen-of-death advice to do something that a very simple program does extremely well ( within the limits of typically poor Linux user docs) SYNAPTIC.

It is also well to note that for 90% of refugees, the Kubuntu interface is much more familiar - and dare I say saner in a real user world than Gnome.  I would advise any new user to start with Kubuntu as KDE is just like THAT one. 

Please note that these are constructive comments, not destructive and meant to help usher in a new world without a Borg .... :-)

Peace!

Thank you for this useful post. You have inspired me to update the original post with a simple GUI method of enabling software sources by navigating to System>>Administration>>Software Sources. 
However, the outlined CLI method is an excellent way for a newcomer to become acquainted with the CLI and learn how to enable a graphical text editor with "ROOT" privileges. Inevitably, linux users should desire to learn something about the "black screen of death" just as a car owner should know how to change a tire ( and yes you might break a nail ). Try fixing something when the Windows registry is fouled...ha.

And I completely disagree that KDE is a more user friendly interface than Gnome...and synpatic in KDE is twice as confusing as it is in Gnome.

---

### Post by spiderbatdad on 2008-03-11
OP edited to include GUI method.

---

### Post by himagain on 2008-03-12
Hi there Spiderbatdad,

Actually, my point wasn't  against further learning - especially for emergency repairs, but  to push-start an auto is not a good inducement to initially buy it. :-)
The three main points involved here are:
1. 99.9995% of users will never, ever confront the BSOD (black screen of danger).  As I keep explaining to people, almost nobody in the world ever actually installs Windoze. Just as I would never bother changing my oil.
 
It is miraculous that U-Kubuntu seems to work at all, so many times outta the box in the hands of the average  refugee. 

2. But there is great danger in the BSOD - especially from the criminally insane Cyber-dolts who deliberately set out to total people's systems as a joke - as funny as setting kittens on fire.

3. Also from simple transcription errors.
   
The  key point missed by most willing helpers out in the Cyberbog is a simple one:
92% of those potential users only use a computer to do things with as a tool. A tool to do a specific set of tasks and just as with the auto, have no interest at all in how a hypoid differential or auto gearbox works, only in using it to get from A 2 B.
They aren't like you! :-) 
BUT, we are mostly very thankful that you are out there offering assistance.
BTW- I didn't know there was any difference in the Synaptic program interface  between the Gnome and K, will go look. 

Cheers,

Himagain

---

### Post by spiderbatdad on 2008-03-12
I guess my point, in response would be, I agree with a great deal of what you said. We hope with each new release things improve in the area of user friendly interfaces and out-of-the-box functionality. 

Ubuntu is a free alternative to Windows. It offers relatively virus free computing, some really flashy toys (like compiz-fusion), some control over one's computer and a community. Developers are open to suggestions. In this example, it would be useful if the system ran a check during boot-time network configuration to check if sources were enabled, and if not, offer a dialog when the desktop loads.

Anyone who uses Windows knows it is riddled with problems of it's own, and after a brief time, you have to pay for support...and take it to the mechanic when it fails. My folks recently bought a new Dell...well, the McAfee (whatever) ran out in like 6mos. They had to renew the subscription to the tune of a couple hundred dollars. What a joke. Every time they start the thing, it seems like half a dozen dialogs open to do one thing or another, or renew a subscription to Corel Photo or whatever. It never stops demanding more money. Where are all the great features it should have? Oh, you have to buy those separately. It is also not as if a first-time windows users fires up the computer and knows how to resize photos, configure a firewall, or even cut & paste text in a word processing program (if he can find it). There is a learning curve.

I'm so grateful for this software. That's why I try to help refugees, though I don't know much; but I'm learning. The more those of us that are here learn, the more likely we are to be able to contribute to further development.

---

### Post by kushykush on 2008-03-25
Totally agree with HimAgain.   Linux could have dominated the OS world had it been given to people in formats they could easily understand.  Which is what Microsoft has exploited.  The Linux world has come a long way.  Ubuntu distributions are an example.  However, there are still things that unnecessarily confuse new users like me who are not interested in learning any kind of code.

For example, I still do not understand why I cannot add drivers into my OS from my CD/DVD disks.  

Printers is another example.  I have a new Brother MFC 9440cn printer.  But it is more than just a printer. As the name (MFC - Multi functional center) suggests it does scanning, faxing, and copying besides printing.  Brother website does seem to have a Linux driver for the complete suite.  But the CUPS website does not have this driver.  The driver they have is for MFC 9420, which works as far as printing goes but I cannot use other functions.  

I have no idea how to  have this Printer (Suite) drivers added to CUPS.  And I still do not understand why to we have to go to CUPS to add printer drivers??

Could someone tell me how I can have this driver for Brother MFC 9440cn added to the list on CUPS?:confused:

---

