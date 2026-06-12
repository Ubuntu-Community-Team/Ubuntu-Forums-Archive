---
title: "Add/Remove, Synaptic Package Manager and Update Manager are not working [Resolved]"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by Avinevo on 2007-01-01
Happy New Year, friends! :)

I'm pretty new for the Ubuntu usergroup and for this community as well. I downloaded Ubuntu 6.10 desktop edition (Edgy) ISO about 14 or 15hrs ago.  After burning it on a CD ROM, when I tried to install Ubuntu, the installation process kept hanging. I realized that 128MB RAM won't let me install Ubuntu on my system. Then I downloaded the Alternate version ISO, burned it on a CD ROM, installed Ubuntu successfully in the first try.

Now, when I was done with the installation process, I tried to run the Update Manager to install all the possible security updates. I tried many times but it didn't work. I launched Network Tools and tried to ping few sites. Everything went well. Pings were successful. But whenever I tried to check whois of any domain, it wasn't working at all. I launched Firefox, and no websites were opening. I checked Networking configuration and DHCP was set for automatic detection. Still the problems started to make me a bit sad even about Ubuntu Linux distro but I didn't stop trying. 

I booted my system in Windows Server 2003 mode, searched in Google for similar Ubuntu problems and fortunately, I found the IPv6 related article @ Official Ubuntu documentation site. I rebooted my system, logged into Ubuntu, tried disabling IPv6, rebooted Ubuntu, disabled IPv6 in my Mozilla Firefox browser, tried to visit Google and voila! It worked well. I was happy thinking that everything is working fine now as far as Networking is concerned. But all my expectations started to appear false when I tried to run the Update Manager once again. It didn't work. I tried to run Gaim IM client, it wasn't able to connect to the net either. I launched Firefox, searched for the possible help in Google, found a few similar problems, applied them and finally, Internet was fully functional on my system. 8) 

Third time, I launched the Update Manager, got 80 security updates listed in the window, downloaded and installed the updates, rebooted Ubuntu, tried to install a few softwares using the Add/Remove option, and damn! It popped up a window showing a major error:
----------------------------------------------------------------------------------------------------------------------------------
[B]
ERROR: [/B]
**[COLOR="Red"](-)[/COLOR]** **Failed to check for installed and available applications.**
This is a major failure of your software management system. Check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information: 'sudo apt-get update'.
----------------------------------------------------------------------------------------------------------------------------------


Launched the Synaptic Package Manager, it showed the same error. Tried to launch the Update Manager, it kept crashing just after launching it. The interesting thing is that the Add/Remove system was working fine before installing the security updates. Internet is still working fine because I am writing this post using Firefox @ Ubuntu. Gaim is also working just fine. Could you please help me in solving this problem? Any help is pretty much appreciated. Thanks in advance for that. 

And yes... When I tried to run apt-get in terminal, it showed an error message. **[COLOR="Red"]The error message was:[/COLOR]** 'Error: Opening the cache (E: Malformed line 6 in source list /etc/apt/sources.list (dist parse), E: The list of sources could not be read.)' 


One more thing that I remember is... after installing the security updates and before the reboot, I had launched the Add/Remove application, it wasn't showing any error at that time. :-?  

Somebody please help me! I'm a complete Linux newbie (not even 24hrs old for Linux). I've been concentrating in solving these problems since past 16hrs+ in a row and it's 4:16 AM in India. I won't go to bed before solving this problem. 

Thanks for your time!

Regards,
Avinevo

---

### Post by AgenT on 2007-01-01
Post your complete /etc/apt/sources.list file here. Just remember to enclose it in code tags.

---

### Post by Avinevo on 2007-01-01
> **AgenT said:**
> Post your complete /etc/apt/sources.list file here. Just remember to enclose it in code tags.

Thanks for the reply! :)

Here is the complete /etc/apt/sources.list file:

```

# 
# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ edgy main restricted #Added by software-properties


deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy

deb http://in.archive.ubuntu.com/ubuntu/ edgy main restricted multiverse
deb-src http://in.archive.ubuntu.com/ubuntu/ edgy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://in.archive.ubuntu.com/ubuntu/ edgy-updates main restricted multiverse
deb-src http://in.archive.ubuntu.com/ubuntu/ edgy-updates restricted main multiverse universe #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://in.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://in.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://in.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu edgy-security main restricted multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security restricted main multiverse universe #Added by software-properties
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe

```

---

### Post by MrJackdaw on 2007-01-01
I've just solved a similar faliure by removing the line

deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy

James

---

### Post by AgenT on 2007-01-01
To quote your error:
> The error message was: 'Error: Opening the cache (E: Malformed **line 6** in source list /etc/apt/sources.list (dist parse), E: The list of sources could not be read.)'Line 6 is:
```
 deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy
```Just replace that line with:
```
 # deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy
```(just add a # in front to comment it out - that is, to disable it)

Now in a terminal, run:
```
sudo apt-get update
```That should fix it.

---

### Post by Avinevo on 2007-01-01
Thanks a lot, MrJackdaw and AgentT!! :) I just edited the /etc/apt/sources.list file, saved it, ran apt-get and everything worked fine in the terminal. I hope everything works fine even in X. 

Thank you once again for your time!

Regards,
Avinevo

---

### Post by snacker on 2007-01-06
[http://www.ubuntuforums.org/showpost.php?p=1977346&postcount=4]("http://www.ubuntuforums.org/showpost.php?p=1977346&postcount=4")

---

