---
title: "Help please! Adding application error."
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by Pasty-Flawss on 2008-04-15
Hi,

I wasn't sure which topic this should go in so i just posted it here.

I have this error adding and removing applications. When i run add/remove application program it says these applications are out of date would you like to refresh them? and when i click on the refresh button it says downloading package information 7/8. I wait for ages then it stops and comes up with an error message saying Could not download all repository indexes.

I've tryed useing synaptic package manager and even the terminal one. Neither have worked.

What i want is to download wine (the emulator to run windows EXE Files etc.) but i can't because of this bug. Please help.

Thanks in advance :).

---

### Post by bumanie on 2008-04-15
You probably have not enabled the software sources. Go to System --> Administration --> Software Sources and check the first four boxes, uncheck (or leave as is) the source code and cd-rom boxes. Then go to third party software and check any boxes that are in there. Things should work better after you have done this.

---

### Post by joshrobinson on 2008-04-15
when you run it in terminal, does it say what repo fails? if you added a custom repo in, that it cant connect to, it would cause this error

---

### Post by Pasty-Flawss on 2008-04-15
Thanks for the reply. :). Now when i open add/remove applications and refresh it says downloading 7 out of 13. (before it was 7 out of 8). I am still stuck on 7. Anyone else have any ideas?

---

### Post by Pasty-Flawss on 2008-04-15
when you run it in terminal, does it say what repo fails? if you added a custom repo in, that it cant connect to, it would cause this error

Sorry i am a noob. What do you mean by repo fails? can you tell me what commands to enter into terminal etc.? thanks

---

### Post by joshrobinson on 2008-04-15
> **Pasty-Flawss said:**
> 

Sorry i am a noob. What do you mean by repo fails? can you tell me what commands to enter into terminal etc.? thanks

could you run this in a terminal, and post the output

```
sudo apt-get update
```

also if you want to quote someone, click the quote button in the bottom right corner of that persons post :)

---

### Post by bumanie on 2008-04-15
May be you have to update your/etc/apt/sources.list Follow this guide
[http://www.psychocats.net/ubuntu/sources.php](http://www.psychocats.net/ubuntu/sources.php)
> sudo apt-get update to ensure everything is updated

---

### Post by Pasty-Flawss on 2008-04-15
> **joshrobinson said:**
> could you run this in a terminal, and post the output

```
sudo apt-get update
```

also if you want to quote someone, click the quote button in the bottom right corner of that persons post :)

I remember typing this command i think it was earlier today and i got a more accurate message but i typed it in this time and it timed out or something.

Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_NZ
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_NZ
Err [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg                             
  Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg                                
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
42% [Connecting to archive.canonical.com (1.0.0.0)] [Connecting to archive.ubun

---

### Post by rockerphil on 2008-04-15
i've had this same problem. here's what you want to do. open up Synaptic Package Manger. click on the tab that says "Settings" up at the top then click "repositories" in the drop down and make sure ALL the boxes are checked then click "ok" once the Repository window closes click "refresh" then close out synaptic and then run this code
sudo apt-get install wine
that should do the trick

---

### Post by Pasty-Flawss on 2008-04-15
I think this may be a problem with my connection with ubuntu because i cant refresh any other things. it always gets stuck on downloading file number 7 out of X. :S I'm connected to the internet fine though.

---

### Post by joshrobinson on 2008-04-15
> **Pasty-Flawss said:**
> I think this may be a problem with my connection with ubuntu because i cant refresh any other things. it always gets stuck on downloading file number 7 out of X. :S I'm connected to the internet fine though.

yeah it seems like it, i just did an update to check to see if anything was down, and archive.ubuntu loaded fine for me
im not sure why it wont work for you

---

### Post by Pasty-Flawss on 2008-04-15
i tried running  add/remove applications again then i clicked on reload then it gave me a different error message:

E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory

---

### Post by joshrobinson on 2008-04-15
> **Pasty-Flawss said:**
> i tried running  add/remove applications again then i clicked on reload then it gave me a different error message:

E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory

do you have synaptic or update manager open? make sure to close them before trying to use add remove programs

---

### Post by 3rdalbum on 2008-04-15
Try going into System > Administration > Software Sources and change it from "Download from Main Server" to a different server. There should be one listed underneath for your country, or you can go to the bottom entry and choose one from anywhere in the world.

Reload your package list again, and then you'll be able to install Wine.

---

### Post by Pasty-Flawss on 2008-04-15
> **rockerphil said:**
> i've had this same problem. here's what you want to do. open up Synaptic Package Manger. click on the tab that says "Settings" up at the top then click "repositories" in the drop down and make sure ALL the boxes are checked then click "ok" once the Repository window closes click "refresh" then close out synaptic and then run this code
sudo apt-get install wine
that should do the trick

When i type in "Sudo apt-get install wine" it comes up with the following:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package wine

---

### Post by joshrobinson on 2008-04-15
> **Pasty-Flawss said:**
> When i type in "Sudo apt-get install wine" it comes up with the following:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package wine

it cant find wine because the repo's wont update correctly
try what 3rdalbum posted

---

### Post by Pasty-Flawss on 2008-04-15
I tryed what 3rdalbum posted. It's still stuck on 7th file. I think the problem maybe because when i first loaded ubuntu i couldn't get internet to work then i looked up troubleshoot and it said:
IPv6 Not Supported

   1.

      IPv6 is supported by default in Ubuntu and can sometimes cause problems.
   2.

      To disable it, open a Terminal (Applications &#8594; Accessories &#8594; Terminal) and type the command: gksudo gedit /etc/modprobe.d/aliases.
   3.

      Find the line alias net-pf-10 ipv6 and change it to read alias net-pf-10 off.
   4.

      Reboot Ubuntu.

I did this and internet works. however ubuntu still might not be pickingup my connection?.. Only reason i can't think it's not working

---

### Post by bumanie on 2008-04-15
Sometimes servers are down due to the need for maintenance etc. Often they will work in a day or two. As suggested before find a server closer to your home system --> Administration --> Software Sources, click on the 'download from and choose other. A scan will commence that choose the best/closest server for your location.

---

### Post by Pasty-Flawss on 2008-04-15
Now its stuck on file 1 of 28. If i click Show progress of single files it comes up with 8 different file name things and all there status is failed. Oh well thanks for the help guys

---

### Post by Pasty-Flawss on 2008-04-15
yes i think it has nothing to do with add/remove application program i think its to do with my connection because i can not connect to pidgin instant messenger and other programs that are installed on my computer

---

### Post by bumanie on 2008-04-15
The ipv6 and aliases should've worked, but how I got gutsy to connect to the internet was by disabling ipv6 in firefox. Try opening firefox and type about:config in the address bar and in the filter type ipv6. On the line that appears, right click on it and then left click on toggle to change the value to true. you may like to try that because if it doesn't work, you can go through the process again and change the toggle value back to false.

---

### Post by Pasty-Flawss on 2008-04-15
still no luck. But i did some more research and came across someone who had same error message as me the guy who helped him said this : 

sudo gedit /etc/apt/sources.list
Will allow you to examine and manually edit the sources.list file (look at the line 26 that is reported as a problem).

Do a forum search for a default sources.list for your version, you may want to replace it if it is too far gone.

i typed in sudo ... and i got this:

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports universe main multiverse restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

the only other post was from the guy who posted the topic saying worked like a charm.. any ideas?

EDIT: i repasted the source list cause i didnt paste all of it accidently

---

### Post by bumanie on 2008-04-15
I don't know where that sources list has come from, that's why I suggested the one from psychocats - they are a trusted source of linux/ubuntu information. It is up to you which one you use. I have found the psychocats list adequate, bu the one you've posted, at a glance looks OK too. Use whichever one you prefer and then change to a local server as I suggested earlier. I'm in Australia, and since changing to a local server, I've had less hassles with updating. As far as everything goes with some things not updating, don't stress as long as most things update and see if the others do in a day or two. Sometimes you may be missing a public key which gets added to the authentication under software sources. A google search should come up with something that will help if you read which keys are missing.

---

### Post by Pasty-Flawss on 2008-04-15
ok, will try that. But not just some aren't refreshing i cant get ANY to refresh because it freezes while its refreshing.

---

