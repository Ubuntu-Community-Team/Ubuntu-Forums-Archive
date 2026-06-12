---
title: "Ventrilo isn't Installing. Help please."
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by Catewilliams on 2006-08-28
Hi, I just recently uninstalled Ubuntu so I could partition Ubuntu and Windows XP, Something happend and Windows didn't install correctly, but I didn't care much, I can still use Linux.

When I first had Ubuntu, Ventrilo installed and ran fine when I used Wine. Then, when I uninstalled, I can't re-install it.

What happens is, it'll ask me to install and it says it does, but all that pops up is a 'ventrilo.ink' docuement, and I can't run it. Ventrilo doesn't seem to actually install. I've tried uninstalling it, but it doesn't even un-install.

I've tried using various tutorials, but it keeps installing 'ventrilo.ink'. ](*,) 

If you could tell me how to actually install it, or, what the problem is, I'd be very thankful. Thank you!

**Edit: Also, anytime I try to navigate to the install directory, I can't even find Ventrilo.exe, it keeps saying it doesnt exist. Either Ventrilo just isn't installing, or I'm not doing something right.. :-k **

---

### Post by judgejudy on 2006-08-28
sry i cant help new to linux but maybe you can help me got vent running with wine but cant get it to work with my sound](*,) no input no output i have a audguy sound card ubuntu works with it music ect..:confused:

---

### Post by Toxicity999 on 2006-08-28
Well wine doesn't have propper Windows Shortcut support, navigate to the actual install directory and run the exe manually... assuming I understood you. (To the O.P.)

To the secondary...


Run winecfg see if all your sound options are set correctly. Maybe read up at appdb.winehq.org

---

### Post by Catewilliams on 2006-08-28
> **Toxicity999 said:**
> Well wine doesn't have propper Windows Shortcut support, navigate to the actual install directory and run the exe manually... assuming I understood you. (To the O.P.)

To the secondary...


Run winecfg see if all your sound options are set correctly. Maybe read up at appdb.winehq.org


I tried that, but it said it couldn't find Ventrilo.exe. It keeps installing a .ink docuement that I can't open.

Also, before I re-installed Ubuntu, it was putting the Icons on my desktop. Now it's putting .ink docuements.

---

### Post by Toxicity999 on 2006-08-29
weird where did you get your wine download the winehq site? I know the Linking supposidly works, never has for me with any of the versions. Try uninstalling wine removing .wine then install again run winecfg and go from there. Might of just been by chance it didn't work. Otherwise you must of done something different the first time... Though it's odd it doesn't actually extract the files from the installer... Does Vent have an archive manual install version? Then you could just do your thing with that, cut out the issue at its source.

---

### Post by Catewilliams on 2006-08-29
> **Toxicity999 said:**
> weird where did you get your wine download the winehq site? I know the Linking supposidly works, never has for me with any of the versions. Try uninstalling wine removing .wine then install again run winecfg and go from there. Might of just been by chance it didn't work. Otherwise you must of done something different the first time... Though it's odd it doesn't actually extract the files from the installer... Does Vent have an archive manual install version? Then you could just do your thing with that, cut out the issue at its source.


Thank you for the advice... ^^;

I did all of the above, and it keeps telling me Ventrilo is installed, besides the fact I can't find it anywhere on my system.

Also, I didn't find manual install version, it might be out there, but I can't find it. Ventrilo seems to keep installing 'doc', I try to open them but they won't go. 

So, whenever I try to install Ventrilo now, it asks me if I want to 'Repair, Modify, or Remove' Ventrilo. **Even** if I try to Remove, it says it installs it. Same with the others, it keeps installing .Doc files, that don't even show up.

I feel like such a n00b, I thought I had it figured out. I apprently didn't. :-#

---

### Post by Toxicity999 on 2006-08-29
It is really weird though... I'll never understand why people that Code for Windows create all these fancy annoying installers to me deleting a selfcontained directory the way it's organized anyway would be much simpler than navigating an ugly add/remove prog and clicking next 30 times haha. You said you've tried removing and installing wine a few times right? throughout that did you ever delete the .wine directory in your home? that's where all the goodies are like files that might keep telling the installer to give up as it's already there. Deleting .wine of course is the easy way if you want to go all out tech on it it skim the wine reg riles remove anything refering to the Vent installer and any temp files that may still be there.

---

### Post by Catewilliams on 2006-08-30
> **Toxicity999 said:**
> It is really weird though... I'll never understand why people that Code for Windows create all these fancy annoying installers to me deleting a selfcontained directory the way it's organized anyway would be much simpler than navigating an ugly add/remove prog and clicking next 30 times haha. You said you've tried removing and installing wine a few times right? throughout that did you ever delete the .wine directory in your home? that's where all the goodies are like files that might keep telling the installer to give up as it's already there. Deleting .wine of course is the easy way if you want to go all out tech on it it skim the wine reg riles remove anything refering to the Vent installer and any temp files that may still be there.


Yeah. Instead of asking me if I want to install, it asks me if I want to Repair, Remove, Modify. I can post a screen shot if you need it.

I'll try removing the .wine directory, see if that'll help. You are being such a help, thanks!

---

### Post by Catewilliams on 2006-08-30
This is quite intresting, there is no wine directory in my home directory. :/ This makes me a little wary that it wasn't installed correctly.

---

### Post by Toxicity999 on 2006-08-30
well you can try 
sudo apt-get remove wine --purge
then install the deb from the winehq site then use winecfg which should create all the fakedirs and such. Hopwfully all of that will purge the old failed install attempts. What it seems to be doing is just reading it was already installed for some reason like I said. If it's all too much trouble you might want to just try cedega Vent works pretty well through that as well.

---

### Post by Catewilliams on 2006-08-30
```
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/ellie', starting in the Windows directory.
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/', starting in the Windows directory.
```

Thats what I get when I try to run winecfg. 
I'm going to assume thats the reason nothing was working properly, because there doesn't seem to be anything else wrong. 

Also, when I right clicked on the ventrilo install exe file, and tried to open it up with Wine, it wouldn't budge. 

D: I'm sorry if I'm just being incompetent, but this really does tickle me as odd.


EDIT:

```
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\ ellie\\Desktop"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\ ellie\\Desktop"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\ ellie\\Desktop"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\ ellie\\My Documents"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\ ellie\\My Pictures"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\ ellie\\My Music"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\ ellie\\My Video"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\ ellie\\Desktop"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\ ellie\\Desktop"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\ ellie\\Desktop"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\ ellie\\My Documents"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\ ellie\\My Pictures"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\ ellie\\My Music"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\ ellie\\My Video"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\ ellie\\Desktop"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\ ellie\\Desktop"'.

```

When I try to make the proper drives in Winecfg, thats what comes up in the terminal. Any help? ](*,)

---

### Post by Toxicity999 on 2006-08-30
No it is odd... it seems like Wine doesn't have the access to create files in your own directory... just for answers sake try sudo winecfg and see if that tosses the same error output. This would create a wine directory in the root home area which though it could be a security threat if you werent careful might allow you to just run this for now. I still don't understand why Wine seems to refuse to make files and folders in a director you own... Through all this did you actually try to fully purge and reinstall wine like I said? (Long term I wouldn't recommend always sudoing for wine I was just curious to see if it gave the same error output.)

---

### Post by Catewilliams on 2006-08-30
> **Toxicity999 said:**
> No it is odd... it seems like Wine doesn't have the access to create files in your own directory... just for answers sake try sudo winecfg and see if that tosses the same error output. This would create a wine directory in the root home area which though it could be a security threat if you werent careful might allow you to just run this for now. I still don't understand why Wine seems to refuse to make files and folders in a director you own... Through all this did you actually try to fully purge and reinstall wine like I said? (Long term I wouldn't recommend always sudoing for wine I was just curious to see if it gave the same error output.)


1. I did purge and reinstall like you said, twice, actually. Before the first purge, when I made this thread, it wasn't coming up with that error. 

2. sudo winecfg came up with the same thing, and even when I made specified drivers for C, and opened it up in winecfg (not sudo) it told me there wern't any C drivers. D:

---

