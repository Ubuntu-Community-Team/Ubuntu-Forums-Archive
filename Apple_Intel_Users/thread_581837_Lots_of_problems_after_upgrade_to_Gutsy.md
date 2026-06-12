---
title: "Lots of problems after upgrade to Gutsy"
date: 2007-10-19
forum: Apple Intel Users
---

### Post by PaulFXH on 2007-10-19
I upgraded Ubuntu to Gutsy on my MacBook (C2D, 2.16 GHz) today and, other than taking quite a bit longer than anticipated (overloaded server), the install seemed to go fine.
Strangely, the one problem I anticipated (wireless connection) went perfectly smoothly and wireless has worked perfectly once I had installed the madwifi drivers.
However, there are quite a few other problems where I would welcome some advice:

1) No desktop-effects
This doesn't appear in System menu and if I try to install desktop-effects using Synaptic, I get this message:
> desktop-effects:

Package desktop-effects has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list

2) Similarly, can't install Emerald themes. I get this message when trying to install from Synaptic:
> emerald-themes:
 Depends: emerald but it is not going to be installed

3) All open windows are missing Minimize/Quit buttons

4) Open windows cannot be moved

Everything seems to point to some major confusion or error in the area of Desktop-Effects. However, I very much doubt if this is a Mac-related problem.
Nevertheless, perhaps somebody here knows how I might fix this.

Thanks
Paul

---

### Post by neonide on 2007-10-19
yeah, i have a 1st gen macbook, upgraded today as well. tons of errors during install

the result: gnome doesnt fully load, i'm eff'd

solution: i dont want to troubleshoot, so right now i'm booted into knoppix, samba'ing my /home dir to another computer, as well as downloading the actual install CD(which i assume will install fine)

---

### Post by cyberdork33 on 2007-10-19
> **PaulFXH said:**
> 1) No desktop-effects
This doesn't appear in System menu It is now located under 'appearance'

> 2) Similarly, can't install Emerald themes. I actually think I have got this error before. I use a custom theme I have at home so I haven't encountered it recently. can you verify that emerald is installed?
```
sudo apt-get install emerald
```> 3) All open windows are missing Minimize/Quit buttons

4) Open windows cannot be movedYou window borders are likely missing because your window decorator is not loading up (emerald). You can remove the emerald line from your session so that you use the default decorator.

> Everything seems to point to some major confusion or error in the area of Desktop-Effects. However, I very much doubt if this is a Mac-related problem.
Nevertheless, perhaps somebody here knows how I might fix this.nope not Mac related.

---

### Post by PaulFXH on 2007-10-19
> It is now located under 'appearance'
Yes, I had found this However it doesn' help me greatly. If I go to Visual Effects and select something other than "none" (e.g Extra), the dialog box immediately becomes grayed out. However, no noticeable visual effects are evident. Then after about 40-50 seconds, the checked radio button becomes unchecked, the "None" button becomes checked and the dialog box is "ungrayed" and becomes usable again.
So, this is very wierd.
Nevertheless, this fiddling around in the Appearance box does actually bring back the missing Minimize/Quit buttons on all windows. Plus, windows now get noticeable borders.

> can you verify that emerald is installed?
Emerald is NOT installed. Trying to install through either Synaptic or a terminal gives rise to complaints about unresolved dependencies and installation is not possible. In a terminal, the last message is as follows:
> The following packages have unmet dependencies:
  emerald: Depends: libemeraldengine0 but it is not going to be installed
           Depends: libwnck18 (>= 2.15.90) but it is not installable
E: Broken packages


> You window borders are likely missing because your window decorator is not loading up (emerald). You can remove the emerald line from your session so that you use the default decorator.
As I mentioned above, the borders and buttons are retrievable but Emerald just is not available.

> nope not Mac related.
I therefore have to conclude that this was just a bad install. This may have arisen because the network download took about three hours with the download rate varying from 220 KB/s to as low as 4000 B/s. And this variation continued through the whole download. Seems the server was very busy at the time.
I think I'm gonna download the CD and do a clean-install. All my important stuff is in my Home directory so I won't lose that.
Thanks for your help

---

### Post by phonky on 2007-10-19
> 

Quote:
It is now located under 'appearance'



You also will want to install compiz-settings-manager:

```
sudo apt-get install compiz-settings-manager
```

Then you will be able to set the different settings for cube, etc. in 
System-Preferences-Advanced Desktop Effect Settings.

> If I go to Visual Effects and select something other than "none" (e.g Extra), the dialog box immediately becomes grayed out. However, no noticeable visual effects are evident. Then after about 40-50 seconds, the checked radio button becomes unchecked, the "None" button becomes checked and the dialog box is "ungrayed" and becomes usable again.
So, this is very wierd.
This looks weird indeed though, can't help you on that

---

### Post by PaulFXH on 2007-10-19
OK, I've finally managed to get the desktop effects working in Gutsy thanks to this [thread.]("http://ubuntuforums.org/showthread.php?t=581643")
The key link is [here]("http://kevin.vanzonneveld.net/techblog/article/upgrade_to_ubuntu_gutsy_with_compizfusion/") which recommends taking out all (or almost all) third party repositories, uninstalling the installed Compiz-Fusion and then installing the Gutsy version of CF.
Worked very nicely for me.

---

### Post by cyberdork33 on 2007-10-19
> **PaulFXH said:**
> Yes, I had found this However it doesn' help me greatly. If I go to Visual Effects and select something other than "none" (e.g Extra), the dialog box immediately becomes grayed out. However, no noticeable visual effects are evident. Then after about 40-50 seconds, the checked radio button becomes unchecked, the "None" button becomes checked and the dialog box is "ungrayed" and becomes usable again.
So, this is very wierd.compiz-fusion is just crashing / unable to start. What machine are you on? If you have ATI, did you install XGL?

---

### Post by PaulFXH on 2007-10-19
Well, I have an Intel 945GM card but everything is working fine now -- see my previous post.

---

### Post by cyberdork33 on 2007-10-19
> **PaulFXH said:**
> Well, I have an Intel 945GM card but everything is working fine now -- see my previous post.
yes sorry, posted near the same time. Glad you got it working.

---

### Post by omax on 2007-10-20
tjopp.

Ill add one of my major problems to this thread instead of starting a new one.

I have a problem with Grub. After the upgrade it worked allright. Had to make some minor changes and bla bla.

And since then I rebooted like 3 times, and now on boot when I go to grub it shows:

GRUB _

And thats it, the "_" is just flashing and nothing else is happening. What may be the problem?

:)


EDIT: SOLVED

I ran Windows Installer disk and selected to repair using cmd
Simply enter FIXMBR and Windows takes over the MBR bootloader
I had installed grub on linux partition before, so it worked like a charm.

Now there is another minor problem:

sudo apt-get install

```

..................
Setting up acpid (1.0.4-5ubuntu8) ...
 * Loading ACPI modules...                                               [ OK ] 
 * Starting ACPI services...                                                    invoke-rc.d: initscript acpid, action "start" failed.
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of acpi-support:
 acpi-support depends on acpid (>= 1.0.4-1ubuntu4); however:
  Package acpid is not configured yet.
dpkg: error processing acpi-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of powermanagement-interface:
 powermanagement-interface depends on acpi-support (>= 0.17); however:
  Package acpi-support is not configured yet.
dpkg: error processing powermanagement-interface (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xubuntu-desktop:
 xubuntu-desktop depends on acpi-support; however:
  Package acpi-support is not configured yet.
 xubuntu-desktop depends on acpid; however:
  Package acpid is not configured yet.
 xubuntu-desktop depends on powermanagement-interface; however:
  Package powermanagement-interface is not configured yet.
dpkg: error processing xubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 acpid
 acpi-support
 powermanagement-interface
 xubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Why is this? ^^

---

### Post by cyberdork33 on 2007-10-21
> **omax said:**
> tjopp.

Ill add one of my major problems to this thread instead of starting a new one.

I have a problem with Grub. After the upgrade it worked allright. Had to make some minor changes and bla bla.

And since then I rebooted like 3 times, and now on boot when I go to grub it shows:

GRUB _

And thats it, the "_" is just flashing and nothing else is happening. What may be the problem?

:)


EDIT: SOLVED

I ran Windows Installer disk and selected to repair using cmd
Simply enter FIXMBR and Windows takes over the MBR bootloader
I had installed grub on linux partition before, so it worked like a charm.

Now there is another minor problem:

sudo apt-get install

```

..................
Setting up acpid (1.0.4-5ubuntu8) ...
 * Loading ACPI modules...                                               [ OK ] 
 * Starting ACPI services...                                                    invoke-rc.d: initscript acpid, action "start" failed.
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of acpi-support:
 acpi-support depends on acpid (>= 1.0.4-1ubuntu4); however:
  Package acpid is not configured yet.
dpkg: error processing acpi-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of powermanagement-interface:
 powermanagement-interface depends on acpi-support (>= 0.17); however:
  Package acpi-support is not configured yet.
dpkg: error processing powermanagement-interface (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xubuntu-desktop:
 xubuntu-desktop depends on acpi-support; however:
  Package acpi-support is not configured yet.
 xubuntu-desktop depends on acpid; however:
  Package acpid is not configured yet.
 xubuntu-desktop depends on powermanagement-interface; however:
  Package powermanagement-interface is not configured yet.
dpkg: error processing xubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 acpid
 acpi-support
 powermanagement-interface
 xubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)

```Why is this? ^^
You really need to create new threads for new problems.

This is probably not Mac specific, so while I may not be able to help, there are others (in various parts of the forum) that probably can.

---

### Post by madscientist032 on 2007-10-21
I just upgraded to Gusty two days ago (through the update manager from Fiesty) and everything's fine, except the aftermath of the login screen. After I log in, I get a black screen and I only see the mouse cursor and I hear the welcome music playing. After about 10 seconds my desktop is displayed.  That's the only problem so far. I haven't tried to suspend or hibernate yet due to the issues I had in fiesty.

Any help to fix the black screen would be greatly appreciated.

---

