---
title: "Ubuntu Viruses?"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by mrphud on 2008-01-26
Hello

I am aware that everyone says there are no viruses for ubuntu but ever since I played with azureus I can no longer utilize my grub because my keyboard doesn't work at startup. However, this is a recent issue because it always used to, I am seriously considering reinstalling my ubuntu system. Any suggestions advice before I spend an extra hour?

---

### Post by Darkhack on 2008-01-26
What does this have to do with Ubuntu Viruses?  You should properly label your subject line to recieve the best help.  This is an issue with GRUB.  Azureus could not have caused it because that's a userspace application and GRUB runs before the kernel even does.  It sounds like an Ubuntu update broke something.  I'd file a bug report and say whether you are using a PS/2 or USB keyboard.

---

### Post by mrphud on 2008-01-26
I believed this to be with viruses because I have seen similar behavior on windows machines. You are probably right about the bug report so how do I file one?

Thanks

---

### Post by CasperRed on 2008-01-26
I've never done it, but I trust the information located here:

[http://ubuntuforums.org/showthread.php?t=284595](http://ubuntuforums.org/showthread.php?t=284595)

Best of luck.

---

### Post by gvartser on 2008-01-26
> **mrphud said:**
> I believed this to be with viruses because I have seen similar behavior on windows machines. You are probably right about the bug report so how do I file one?

Thanks

the slightly difference is that when it comes to windows you can almost be sure that the cause is a virus. With Ubuntu & other linux flavors on the other hand, 

Darhack's:

> What does this have to do with Ubuntu Viruses? You should properly label your subject line to recieve the best help. This is an issue with GRUB. Azureus could not have caused it because that's a userspace application and GRUB runs before the kernel even does. It sounds like an Ubuntu update broke something. I'd file a bug report and say whether you are using a PS/2 or USB keyboard.

is most likely the case.

If you find it interresteing there are a cuple of threads about viruses on linux:

Here are a few:

[http://www.counterpunch.org/~blinux/list-archive/blinux-list/1997/msg00184.html](http://www.counterpunch.org/~blinux/list-archive/blinux-list/1997/msg00184.html)

[http://math-www.uni-paderborn.de/~axel/bliss/](http://math-www.uni-paderborn.de/~axel/bliss/)

[http://www.linuxportalen.se/node/8999](http://www.linuxportalen.se/node/8999)

Best regz,
/g

---

### Post by mikewhatever on 2008-01-26
> **mrphud said:**
> Hello

I am aware that everyone says there are no viruses for ubuntu but ever since I played with azureus I can no longer utilize my grub because my keyboard doesn't work at startup. However, this is a recent issue because it always used to, I am seriously considering reinstalling my ubuntu system. Any suggestions advice before I spend an extra hour?

It is highly unlikely to get a virus on a standard Ubuntu installation, however, you've mentioned Azureus which is based on Java, which is a different story. If you think it is a virus, go ahead and install one of the scanners like Avast or AVG.
[http://www.google.co.il/search?q=ubuntu+avast&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.co.il/search?q=ubuntu+avast&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)
[http://www.google.co.il/search?q=ubuntu+avg&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.co.il/search?q=ubuntu+avg&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)
I'd also advise a rootkit scanner like chkrootkit and rkhunter, and run them from terminal with 'sudo preffix'.
> sudo aptitude install chkrootkit
sudo aptitude installrkhunter

In case nothing turns up, try searching for keyboard troubleshooting. It's not unknown, that USB keyboards have settings to configure in the BIOS, for example. Lastly, reinstall if you have to, it's not a big deal.

---

### Post by stalkingwolf on 2008-01-26
Here is my experience.  My Wife ( a computer challenged person) has used Ubuntu since 6.04 with never a virus or spyware. Her sister ( a computer moron) used ubuntu for several months problem free( she crashed xp daily.)  My landlord has run Ubuntu for months with no problems.  I have Ubuntu on at least 3
machines and have only had issues with win only applications. (the resort I work at has a provider whos website is only viewable from inet exploder, I have heard that they have just filed bankruptcy).

So I doubt it is a virus issue.  might it be that you need new batteries in your keyboard?

---

### Post by Kilz on 2008-01-26
> **mikewhatever said:**
> It is highly unlikely to get a virus on a standard Ubuntu installation, however, you've mentioned Azureus which is based on Java, which is a different story. If you think it is a virus, go ahead and install one of the scanners like Avast or AVG.
[http://www.google.co.il/search?q=ubuntu+avast&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.co.il/search?q=ubuntu+avast&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)
[http://www.google.co.il/search?q=ubuntu+avg&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.co.il/search?q=ubuntu+avg&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)
I'd also advise a rootkit scanner like chkrootkit and rkhunter, and run them from terminal with 'sudo preffix'.


In case nothing turns up, try searching for keyboard troubleshooting. It's not unknown, that USB keyboards have settings to configure in the BIOS, for example. Lastly, reinstall if you have to, it's not a big deal.

The avast and avg are anti virus. But I believe they dont scan for linux viruses because none exist. Instead they look for windows viruses that you could pickup and accidentally pass on to friends who run windows.

---

### Post by mdsmedia on 2008-01-26
> **gvartser said:**
> the slightly difference is that when it comes to windows you can almost be sure that the cause is a virus. With Ubuntu & other linux flavors on the other hand, 
While Windows is more likely to attract viruses it's not really fair to say "you can almost be sure it's a virus". It could be the same thing that's causing the problem in Linux....in fact more than likely.

> **stalkingwolf said:**
> Here is my experience.  My Wife ( a computer challenged person) has used Ubuntu since 6.04 with never a virus or spyware. Her sister ( a computer moron) used ubuntu for several months problem free( she crashed xp daily.)  My landlord has run Ubuntu for months with no problems.  I have Ubuntu on at least 3
machines and have only had issues with win only applications. (the resort I work at has a provider whos website is only viewable from inet exploder, I have heard that they have just filed bankruptcy).

So I doubt it is a virus issue.  might it be that you need new batteries in your keyboard?I agree, but doubt that it has much to do with their bankruptcy :). BTW, it's 6.06...Dapper Drake...6.04 doesn't exist.

> **Kilz said:**
> The avast and avg are anti virus. But I believe they dont scan for linux viruses because none exist. Instead they look for windows viruses that you could pickup and accidentally pass on to friends who run windows.True. Anti-Virus programs are reactive. When a virus is found the anti-virus can then look for its signature. Until then anti-virus won't stop anything. Since there are no known viruses for Linux, anti-virus is only useful for ensuring you don't pass on windows viruses to windows users.

---

### Post by mikewhatever on 2008-01-26
Well, how about viruses for java? Besides, the OP claims it's a virus, so an AV would not hurt in this particular case, even for reassurance purpose only.

---

### Post by arsenic23 on 2008-01-26
Have you tried a different keyboard ?

---

