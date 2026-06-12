---
title: "Can't remove package..and can't install anything either. :("
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by CheeseEatingBulldog on 2006-09-22
I was trying to get compiz/xgl to work but that seems to have backfired.

Now, I have a broken apt-get, when I try anything be that via terminal, synaptic or update notifier I get

apt-get remove csm
Reading package lists... Done
Building dependency tree... Done
E: The package csm needs to be reinstalled, but I can't find an archive for it.

But try as I may I cannot remove this package, how to I get rid of it? I can't install /deinstall anything at the moment.

---

### Post by wieman01 on 2006-09-22
There is a thread full of attempt to resolve a similar problem. It's tough but the guy eventually managed to resolve despite the fact that he could not tell how he did it at the end of the day:

[http://www.ubuntuforums.org/showthread.php?t=252762]("http://www.ubuntuforums.org/showthread.php?t=252762")

But look for yourself. Hope it helps.

---

### Post by CheeseEatingBulldog on 2006-09-22
Actually I thought it was solved but it still gives the same error, my synaptic is broken and I can't install anything!

---

### Post by wieman01 on 2006-09-22
This is a though one and I have not seen anybody with a straight answer to be frank. But this thread is a start.

---

### Post by CheeseEatingBulldog on 2006-09-22
So far I have tried 

-the deborphan method, couldn't see csm package.

-sudo dpkg -r remove-reinstreq csm
dpkg - warning: ignoring request to remove remove-reinstreq which isn't installed.
dpkg: error processing csm (--remove):
 [B]Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.[/B]
Errors were encountered while processing:
 csm

-all tries in [http://www.ubuntuforums.org/showthread.php?t=252762](http://www.ubuntuforums.org/showthread.php?t=252762)

-banging my head against keyboard

I guess alien-ing an RPM package isn't the brightest idea on the block.

---

### Post by wieman01 on 2006-09-22
> **CheeseEatingBulldog said:**
> 
-banging my head against keyboard

I guess alien-ing an RPM package isn't the brightest idea on the block.
Hey, I have not said every mentioned solution is the good one... Hahaha! ;-)

---

### Post by CheeseEatingBulldog on 2006-09-22
I thought I would try all that he did anyway...just in case his phantom sollution happend to me as well....alas.

I have a linux wizZard coming over in a while, if he can solve it I will put the sollution up here.

It is pretty weird though.....

---

### Post by wieman01 on 2006-09-22
It is and as you can see we could not resolve it despite our joint efforts. Finally the guy was able to resolve the issue but don't ask me how he did it.

---

### Post by CheeseEatingBulldog on 2006-09-22
I fixed it, albeit a butchering.

I found [http://forum.linspire.com/viewtopic.php?t=236072&sid=4c57c957064d633b853d12d05f72ff72](http://forum.linspire.com/viewtopic.php?t=236072&sid=4c57c957064d633b853d12d05f72ff72)

And followed the suggestion to 

"Then I went to my /var/lib/dpkg/status file and backed it up (called it status-bak) and removed the "paragraph" or section on the mfc driver which I tried to install (I did a search and then deleted it).
I then ran CNR and tried a update and it worked!!!!!" 

Which does indeed work, so if you bugger your apt, then edit its status file. :)

---

### Post by saphil on 2006-10-02
This is the sort of heavy-handed bludgeoning style I appreciate.  I have tried all the suggestions in the internet and these forums with zero effect.  Now I am testing your solution.  I am doing this with courier-authdaemon which is apparently a piece of a mailserver that I didn't know I had installed on my fileserver.  

Since I was in the middle of a dapper --> edgy dist-upgrade, with 1/3 of the operating system yet to upgrade.  It feels important to get the whole operation done.  My test machine's dist-upgrade worked like a charm, but the fileserver has been a production server for a couple of years, so there are a lot of other programs that have to be considered.

Thanks, 

Wolf

Now I just wonder what this fix might break...  That is not very optimistic, is it?

---

