---
title: "[INTEL MBP GEN2] disabling Ubuntu Hardy Touchpad..."
date: 2008-05-14
forum: Apple Hardware Users
---

### Post by ThatGuyThere on 2008-05-14
I would like to disable my mbp's touchpad. It causes me nothing but grief whenever i try to type, as my hand continually swipes it, switching to some part of the text that i did NOT want to be typing in. Alternatively, disabling the touch=click or lowering sensitivity options would also be welcomed. Thanks!

---

### Post by tchorix on 2008-05-14
Hi ThatGuyThere,

I have a MPB GEN1. And this is what it worked for me: *System->Preferences->Mouse*, and then go to the Touchpad tab, where you can enable or disable it (under General). After doing that I was able to open *System->Pereferences->Touchpad*, where there is a tab "Tapping". That is the one you want to disable. For having the Touchpad option, you will need to install gsynaptics

```
sudo install gsynaptics
```

I hope it helps
cheers
Tchorix

---

### Post by Brightbelt on 2008-05-14
Just as an alternative, you can also install gsynaptics in the Synaptic Package Center. 

I think it's accessable through the System/Administration menu. Once there, do a search for 'gsynaptics' and mark for install and you're there.

---

### Post by ThatGuyThere on 2008-05-14
> **tchorix said:**
> Hi ThatGuyThere,

I have a MPB GEN1. And this is what it worked for me: *System->Preferences->Mouse*, and then go to the Touchpad tab, where you can enable or disable it (under General). After doing that I was able to open *System->Pereferences->Touchpad*, where there is a tab "Tapping". That is the one you want to disable. For having the Touchpad option, you will need to install gsynaptics

```
sudo install gsynaptics
```

I hope it helps
cheers
Tchorix
I have already tried sudo apt-get install gsynaptics, and it tells me that it is already installed. There is no 'general' tab whenever i go to my mouse preferences. I do have a synaptics touchpad option in my preferences, but when i click it, it gives me this:
```

GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics

```

Where is that file usually located?

---

### Post by Rog-Mahal on 2008-05-14
It's found in /etc/X11/xorg.conf

---

### Post by ThatGuyThere on 2008-05-14
I've found the file, but i don't know where and what to type in :(

---

### Post by cyberdork33 on 2008-05-14
[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)

---

### Post by ThatGuyThere on 2008-05-14
> **cyberdork33 said:**
> [https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)

I followed the touchpad instructions, pasted in, saved, logged out, logged in, but i get an error. Had to go to a failsafe terminal session, and open firefox... Is this a known error, or did i mess up somewhere along the line...?

---

### Post by issih on 2008-05-14
The little program you want is syndaemon, which you almost certainly already have installed...this blocks touchpad events when the keyboard is in use. For simple use, "syndaemon -d" will do, but type "syndaemon --help" to get an idea of the syntax if you want to be more specialised. I just launch it at startup by adding the command to the current session (System->Preferences->Sessions)

---

### Post by cyberdork33 on 2008-05-14
> **ThatGuyThere said:**
> I followed the touchpad instructions, pasted in, saved, logged out, logged in, but i get an error. Had to go to a failsafe terminal session, and open firefox... Is this a known error, or did i mess up somewhere along the line...?
I referenced it because it shows how to put the option you are asking about in the file. You should not just copy and paste. add only the options you need/want and tune it.

> **issih said:**
> The little program you want is syndaemon, which you almost certainly already have installed...this blocks touchpad events when the keyboard is in use. For simple use, "syndaemon -d" will do, but type "syndaemon --help" to get an idea of the syntax if you want to be more specialised. I just launch it at startup by adding the command to the current session (System->Preferences->Sessions)
I think that still relies on the above option being set.

---

### Post by issih on 2008-05-14
As for your error, you have probably made a mistake in editing your xorg.conf file in some way... It is always a good idea to save your current version of that file before messing with it, as an error can leave you unable to log into the desktop, as you just found. It is worth checking the /etc/X11 directory to see if there is a file named "xorg.conf~" (note the ~) as linux often makes automatic backup copies with a tilda on the end. If you have a backup of the previously functional version, just copy it over the borked one and reboot X (ctrl alt backspace).

If you haven't got a backup file, you are going to have to reconfigure X from scratch..

Run "sudo dpkg-reconfigure -phigh xserver-xorg", then reapply any changes you have made

Hope that is helpful

---

### Post by ThatGuyThere on 2008-05-14
> **issih said:**
> As for your error, you have probably made a mistake in editing your xorg.conf file in some way... It is always a good idea to save your current version of that file before messing with it, as an error can leave you unable to log into the desktop, as you just found. It is worth checking the /etc/X11 directory to see if there is a file named "xorg.conf~" (note the ~) as linux often makes automatic backup copies with a tilda on the end. If you have a backup of the previously functional version, just copy it over the borked one and reboot X (ctrl alt backspace).

If you haven't got a backup file, you are going to have to reconfigure X from scratch..

Run "sudo dpkg-reconfigure -phigh xserver-xorg", then reapply any changes you have made

Hope that is helpful
I ran that command, and xorg.conf seems to be back to it's normal state. However, i don't know what you mean by reapplying changes, and i still cannot login to any sessions :/ Would it be easier to simply make a new account,move all of my stuff from my borked account there, and simply start anew? I have not made anything that is hard to configure and wouldn't take more than 15 mins to my main account currently... Plus, thanks to this thread, i seem to know what to do know :P

---

### Post by issih on 2008-05-15
Probably worth a whirl to make a new user account, if it fixes the problem then you can get on with using your computer rather than trouble shooting it...If things are still playing up we'll know you have a deeper issue than just user settings being screwy

good luck

---

