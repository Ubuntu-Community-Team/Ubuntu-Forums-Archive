---
title: "Why would a program get held back in an update?"
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by djsroknrol on 2006-08-02
Hello community;

It's been a while since I've had to post a question..I guess the search function has worked for me until now...Now I ask for your help again, and I know someone knows this one...

My updates came thru tonight, and it was an uneventful 25MB d/l, except for it skipped over totem. Why, I don't know, but I tried a dist-upgrade in terminal as instructed, and got this message attached...

I don't have a DVD on this box but do have all the good codecs installed without any updating conflicts. Anyone have an idea as to why it keeps skipping it?

---

### Post by orb9220 on 2006-08-03
Cannot read the term window. Why not copy and paste the text from term here so all can see.

Thanks.

---

### Post by Ptero-4 on 2006-08-03
This is the text in the terminal window.
```

bob@server:~$ sudo apt-get dist-upgrade
Password:
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  totem
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
bob@server:~$

```

---

### Post by orb9220 on 2006-08-03
Well to be honest I have never seen that before.

But an educated guess would be that they found something serious that would cause more problems maybe?

might get more info is to start a thread titled "The following packages have been kept back:"

That might trip someone's memory if it has happened before.

Sorry I couldn't be more help.

---

### Post by mcduck on 2006-08-03
If you want to find out the exact reason, open synaptic, search that package and mark it for upgrade. Synaptic will now tell you what's the issue.

Most likely installing that update would require removing some older package that is not needed any more or something like that.

---

### Post by Lunar_Lamp on 2006-08-03
I have the same issue.  It's because it wants to remove totem-xine.

---

### Post by djsroknrol on 2006-08-04
> **Lunar_Lamp said:**
> I have the same issue.  It's because it wants to remove totem-xine.

And I have totem-xine..how did you handle it?

---

### Post by milehigh on 2006-08-04
The same thing happened to me. I went ahead and marked totem for upgrade and let Synaptic remove totem-xine. Then I reinstalled totem-xine (without it I could play mpeg's but not wmv's).

Seems to be working fine now.

---

### Post by FizDev on 2006-08-04
Try rebooting... just to try :)

---

### Post by djsroknrol on 2006-08-04
> **FizDev said:**
> Try rebooting... just to try :)

I wish it was that simple FizDev. This server is rebooted daily..


And Milehigh:

>  	The same thing happened to me. I went ahead and marked totem for upgrade and let Synaptic remove totem-xine. Then I reinstalled totem-xine (without it I could play mpeg's but not wmv's).


I think this is the easiest and safe way of doing this..Thanks for that advice. I will post back the results later...dinner and all..;)

---

### Post by djsroknrol on 2006-08-04
And here's the latest...I uninstalled totem-xine..I marked totem for upgrade and Synaptic removed it..when I tried to reinstall it, I got this one...????

Any clues folks?

EDIT...news flash...totem-xine must be obsolete...everything is still working...good news....thanks for all the help...

---

### Post by stairwayoflight on 2006-08-04
er,

this doesn't seem to work for me in synaptic. ie. i have totem installed, and totem-gstreamer which installed as a dependency. now totem-xine is gone.

well i either try to mark totem-xine for installation, and it says totem and totem-gstreamer are to be removed, or if i just select totem-gstreamer for removal, it says totem will be removed as well.

it seems this won't work for me? i don't care whether i have xine or gstreamer as a backend, as long as video codecs, flac, and dvd playback all work.

i seem to remember the dpkg command can be used to force an install without dependencies fulfilled (when they are unavailable), i wonder what is the option to install a pkg without installing the dependencies (when they are available), there must be the option.

---

### Post by cstudent on 2006-08-04
Did you by chance do a dist-upgrade from Breezy to Dapper? I'm just curious. I had this totem problem show up today on a machine. Out of the six machines I have with ubuntu installed, this is the only one that gave the error. It is also the only machine I dist-upgraded. The rest I did clean installs on. I copied my sources.list from one of the other machines and did the usual apt-get update and upgrade and the error did not return. I don't know if that was the cure or just coincidence. Anyway, I am just curious about the dist-upgrade idea.

---

### Post by Metacarpal on 2006-08-05
Hey guys - ran into the same thing.  The issue? totem-xine is now obsolete.  totem-gstreamer now handles the totem-xine files.  I read that earlier.  Darned if I can find the info on it now, but I saw it around here somewhere...

---

### Post by djsroknrol on 2006-08-05
I did a dist-upgrade to Dapper if it helps...but I haven't found anything different so far with it functioning different...I do have another stupid issue I'm about to post on that's unrelated to this one...and again, I think it has to do with an upgrade unfortunately...:(

EDIT: I'm wondering if it's possible to get it back somehow by altering the sources.list file?...anyone have any idea which source list totem-xine came from originally?

---

### Post by fourfats on 2006-08-05
did you use automatix or easyubuntu or the ubuntu starter guide to install stuff when you first installed ubuntu.  cuz i believe they all use/suggest totem-zine

i have the same problem but i just ignore the message for now, may try to have it install totem-gstreamer and then use automatix to install totem-xine again. i didnt dist-upgrade from breezy but rather did a clean install.

---

### Post by djsroknrol on 2006-08-05
> **fourfats said:**
> did you use automatix or easyubuntu or the ubuntu starter guide to install stuff when you first installed ubuntu.  cuz i believe they all use/suggest totem-zine

i have the same problem but i just ignore the message for now, may try to have it install totem-gstreamer and then use automatix to install totem-xine again. i didnt dist-upgrade from breezy but rather did a clean install.

I did a dist-upgrade to Dapper RC1 from a Breezy install CD..been updating ever since without incident till now...I was using Automatix till the upgrade and found it didn't work in Dapper (before the new Automatix came out), and never reinstalled it. Is totem-xine available on the Dapper version of Automatix?

---

### Post by stairwayoflight on 2006-08-05
well,

the above methods didn't work for me, at least in synaptic, though i suppose i could have tried aptitude or apt-get on the ol' xterm.

what did work was [automatix]("http://ubuntuforums.org/showthread.php?t=190025").

kudos to arnieboy and the team.

---

### Post by VirtuAlex on 2006-08-05
> **Metacarpal said:**
> Hey guys - ran into the same thing.  The issue? totem-xine is now obsolete.  totem-gstreamer now handles the totem-xine files.  I read that earlier.  Darned if I can find the info on it now, but I saw it around here somewhere...
Can anybody confirm that totem-gstreamer really handles all these formats which were available only in totem-xine?

---

### Post by Metacarpal on 2006-08-05
> **VirtuAlex said:**
> Can anybody confirm that totem-gstreamer really handles all these formats which were available only in totem-xine?

Found it!  Go into Synaptic and look at the description for Totem.  First line under Features:

> * Play any xine supported file

The new Totem has it covered.  Totem-xine is now redundant.

---

### Post by VirtuAlex on 2006-08-05
> **Metacarpal said:**
> Found it!  Go into Synaptic and look at the description for Totem.
The new Totem has it covered.  Totem-xine is now redundant.
I mean did you check it? Cause people report having problems:
[http://ubuntuforums.org/showthread.php?t=229618]("http://ubuntuforums.org/showthread.php?t=229618")
[http://ubuntuforums.org/showthread.php?t=230002]("http://ubuntuforums.org/showthread.php?t=230002")

---

### Post by Metacarpal on 2006-08-05
Okay, I see what you mean.  Oddly enough, I can play DVDs in my (updated) Totem without Totem-Xine.  I just don't have access to the menus, but I don't know if I ever had that with Totem.  I usually just use Gxine anyway.

---

### Post by stairwayoflight on 2006-08-06
mine is working now, i just used automatix to install dvd &  win32 codecs. it installed "totem" and "totem-xine".

however, the description of "totem" is as follows:

```
A simple media player for the Gnome desktop (dummy package)
Its features :
 .
    * Play any xine supported file
...
```

doesn't "dummy package" mean it is empty, only has dependencies? so it pulls totem-xine in as a dependency, and thats where the program is. afaik you're not going to get a working totem with only the "totem" package.

---

### Post by trent dillman on 2006-08-15
...

---

### Post by chattanoga on 2006-08-22
I have had the same problem for a couple of weeks (2-3). 
totem is held back when updating.

I did as mcduck suggested:
Marked Totem for upgrade
Synaptic suggested that totem-Xine be removed and totem-gstreamer installed, and voilà.
The updating problem is gone.

Can anyone explain why?

---

### Post by Metacarpal on 2006-08-22
I think it was a matter of the totem and totem-gstreamer updates being released before the totem-xine update was released.  As a result, the required package lists for totem and totem-xine didn't match anymore, and it b0rked.  Once the updated totem-xine package appeared in the repositories, the dependancies matched and it worked again.

---

