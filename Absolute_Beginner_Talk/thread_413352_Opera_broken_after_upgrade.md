---
title: "Opera broken after upgrade"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by roylond on 2007-04-19
I followed the automatic upgrade from the notification on the panel, it was X11 lib and since then I cannot launch Opera. How can I fix the problem ?
Thanks

---

### Post by meborc on 2007-04-19
i don't remember how i fixed the problem... probably i removed opera... went to opera's homepage and downloaded the debian for edgy (there was no package for feisty for obvious reasons) installed it... and all was well :)

---

### Post by dakhan on 2007-04-19
It is enough to upgrade Opera to 9.20.

Canonical Commercial repository is recommended - insert following line into /etc/apt/sources.list:
<code>
deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) feisty-commercial main
<code>
(If you are still on Edgy replace feisty with edgy.)

EDIT:
In fact at the moment the package is only in the edgy-commercial. Sorry for misleading - I have kept both and did not check...

---

### Post by meborc on 2007-04-19
ahh... should have remembered that :)

---

### Post by roylond on 2007-04-19
HI Again 
I have tried both solutions its still broken though. Any other thoughts as I miss my Opera.

---

### Post by brazzmonkey on 2007-04-19
i noticed i haven't been able to upgrade to latest opera, because of dependencies issues :
```
opera:
  Depends: libc6 (>=2.5-0ubuntu1) but 2.4-1ubuntu12.3 is to be installed
  Depends: libgcc1 (>=1:4.1.2) but 1:4.1.1-13ubuntu5 is to be installed
  Depends: libqt3-mt (>=3:3.3.8really3.3.7) but 3:3.3.6-3ubuntu3.1 is to be installed
  Depends: libstdc++6 (>=4.1.2) but 4.1.1-13ubuntu5 is to be installed
```
so i suppose you'd rather wait or downgrade.

---

### Post by roylond on 2007-04-19
Problem is I only used Ubuntu a short while and it is still a learning curve for me so when the upgarde manager appears saying there is an upgrade I just let it do it without knowing what the upgrade is. This morning it was to x11 lib but I don't know what x11 lib is or does.
It is since then that Opera won't launch. 
How can I remove the update and return the system to the state it was before the update ?
Would that work ?

Thanks

---

### Post by Sunflower1970 on 2007-04-19
I had problems with Opera too. I uninstalled the version I had when I upgraded from Edgy to Feisty, (Went to Synaptic searched for Opera and marked it for complete removal) then went to the Opera homepage and downloaded version 9.2. It worked again with no problems.

---

### Post by rillip on 2007-04-19
I haven't gone to Fiesty, so I can't provide a specific answer to your issue.  However, x11 is (oversimplifying a lot here), the internal guts that make running guis possible.  I ran the update today and am posting for Opera just fine, so I don't believe it's specific to this update.

---

### Post by roylond on 2007-04-19
It seems odd that Opera was running ok before the upgrade and not after. I just assumed that it was something to do with the upgrade. I've removed Opera and reinstalled it and it still doesn't launch. Where do I go from here?

---

### Post by Ambimom on 2007-04-19
Me too!  Realplayer didn't work anymore either but I found a solution.

1.  remove opera using synaptic (don't complete removal or you'll lose your settings)
2. go to [http://www.opera.com/download/](http://www.opera.com/download/) and download latest version
3. install

voila....it's back and realplayer works again too (at least for me)

Good luck trying this.  I hope it works for you too!

---

### Post by roylond on 2007-04-19
Thanks Gang I've got my Opera back again and running. Ubuntu and the Ubuntu community is great Thanks alot for your help=D>

---

### Post by Ambimom on 2007-04-19
> **kenmiles said:**
> 1. remove opera using synaptic (don't complete removal or you'll lose your settings)
2. go to [http://www.opera.com/download/](http://www.opera.com/download/) and download latest version
3. install

voila....it's back and realplayer works again too (at least for me)

Good luck trying this. I hope it works for you too!

Thanks, worked a treat.
Kenneth.

This didn't work?

---

### Post by roylond on 2007-04-19
> **Ambimom said:**
> This didn't work?

Not the first time I did it. So I used Synaptic a second time to remove Opera, then went to the Opera site downloaded the 9.20 from there and installed it and then it worked. The queer thing is that I was already using 9.20 version before the system upgrade this morning. I don't know enough about Ubuntu to know where to look to find out what happened.
But all is back working again.

---

### Post by Brian Smith on 2007-04-20
One more instance here of Opera broken after an update, that was successfully rectified by removing it in Synaptic then running the installer downloaed from Opera's website.
Thanks, this community is very good!

---

### Post by lippe on 2007-04-23
Thx!

Opera working again!

---

### Post by konungursvia on 2007-05-01
I have the same problem, but the solution of removing and re-installing doesn't work for me. Can I use the edgy one instead, in dapper, and try that?

---

### Post by konungursvia on 2007-05-02
Or are there other ideas this fantastic community of geniuses knows about?

---

### Post by chek2fire on 2007-05-03
i have the same problem two weeks now :(

edit:after the last update i think they fix the problem :)

---

### Post by hornett on 2007-05-15
> **chek2fire said:**
> i have the same problem two weeks now :(

edit:after the last update i think they fix the problem :)

Hmm, not here sadly:

```

retro@hive-linux:~$ sudo apt-get update && sudo apt-get install opera
Get:1 http://gb.archive.ubuntu.com edgy Release.gpg [191B]
Ign http://gb.archive.ubuntu.com edgy/main Translation-en_US                   
Get:2 http://archive.ubuntu.com edgy-backports Release.gpg [191B]              

...
    
Fetched 388B in 19s (20B/s)                                                                                                    

...

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  opera: Depends: libc6 (>= 2.5-0ubuntu1) but 2.4-1ubuntu12.3 is to be installed
         Depends: libgcc1 (>= 1:4.1.2) but 1:4.1.1-13ubuntu5 is to be installed
         Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but 3:3.3.6-3ubuntu3.1 is to be installed
         Depends: libstdc++6 (>= 4.1.2) but 4.1.1-13ubuntu5 is to be installed
E: Broken packages
retro@hive-linux:~
```

---

