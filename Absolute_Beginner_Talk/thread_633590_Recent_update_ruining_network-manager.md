---
title: "Recent update ruining network-manager"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by jwalker on 2007-12-06
Hi all

In the spirit of ubuntu, I thought I might tell you about how an update on Tuesday caused me some trouble. 

It was a fairly big update and included some Open Office stuff, but when it applied the changes it hit a snag applying changes to the network manager. It hung my machine, killed my network connection and I was forced to reboot. Do not want. 

The next day there was a smaller group of updates, no network-manager but once again the same behaviour occured. Goodbye network and a locked up machine. 

I'm not sure what it was about but I surely do get pissed off when a approved and advertised update wrecks my ****. That is an understatement. In any case no major harm was done, after a reboot the network manager was back. 

After the second time I thought I'd do some investigation. 

sudo dpkg --configure -a

will sort this issue out. I don't know what this command does, but it worked for me. Can anybody shed any light on this?

For the record I use a Dell D620 notebook that has had no changes made to it since I installed Gutsy.

Hope not too many other people have this issue, from looking around it seems I am one of the few. The error message you will see is along the lines of 'dpkg: error processing network-manager (--configure): subprocess post-installation script returned error exit status 2'

lol kthxbye!

---

### Post by OffAxis on 2007-12-06
```
sudo dpkg --configure package  -a 
```
              Reconfigure an unpacked package. If -a or --pending is given instead of package, all unpacked but unconfigured packages are configured.

(from the man page)



you can also check out the log file if you're having issues
[B] /var/log/dpkg.log
[/B]

---

### Post by jwalker on 2007-12-08
Cheers mate nice one. Nice to see no one else is having this issue. 

Also nice to see how busy this place is, show's the disto's popularity! WAR Ubuntu.

---

### Post by jimmj43 on 2007-12-08
^Spoke too soon^

It was around midweek when I too decided to D/L updates and hit a snag right off the bat. I closed it out and tried again only to get the same result. I don't recall exactly what the error message was. I decided to put off the updates until later.

tsk, tsk, tsk.... Shame on me.

I began encountering spooky glitches. Somehow Firefox had altered the icons up top - the "minimize", "maximize" and "close icons had seemingly been shoved inward a couple of inches. Likewise, the Firefox icon had also been shoved inward. It was an annoyance and I went looking for a fix from Firefox. Fail. Then I tried to C/P something into the text editor. But when I clicked on the (also moved inward) "minimize" icon I learned later when I tried to open the text editor that it had VANISHED! Huh?? And I hadn't even been drinking!!
Firefox was on the receiving end of a blue streak from me.

I continued for several days limping along like that, then decided to try the updates again. Oddly, there were 100+ when I'd tried them mid week, but only ~20 when I tried again today! HUH?? So I did the only thing a reasonable person would do: I made a drink and set about trying a few other distros, only to finally decide to reinstall Feisty. BINGO! Things are now back to "normal", but I'll admit I'm reluctant to D/L any more updates until more light is shed on this issue.

---

