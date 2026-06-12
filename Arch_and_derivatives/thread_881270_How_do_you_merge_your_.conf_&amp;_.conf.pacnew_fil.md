---
title: "How do you merge your .conf &amp; .conf.pacnew files?"
date: 2008-08-05
forum: Arch and derivatives
---

### Post by handy on 2008-08-05
Some background:  

Due to my no.1 machine being out of action for some weeks, I put the drive with the old version of Arch in my no.2 machine & updated it with a huge 500+ mb download, using yaourt -Syu.

This presented me with some config files that needed merging.  I did it the wrong way & caused some trouble in the system.

***Misfit138***'s tip as supplied on the Arch forum is as follows:

***vimdiff file.conf file.conf.pacnew ***

With recommendation to view the Vim wiki article for more info'.
___________

Personally I have no need to learn to use vim, though having it on my Arch system so I can use the above critically important command is thus far certainly important.

Which brings me to this question: 

What methods do you other Arch users use when you have to merge config' files after a pacman -Syu ?

I'm looking for the easiest most streamlined method, if it saves me from using vim, well then good, as I'm not a programmer & don't need the complexity involved in the use of either vim or emacs.

---

### Post by cardinals_fan on 2008-08-05
I love Vim and use it.  However, this experience shows the value behind an "update early, update often" philosophy.  When I run an update almost every day, the files rarely pile up like that.

---

### Post by kpkeerthi on 2008-08-06
I use [meld]("http://meld.sourceforge.net/") to see the differences and merge if need be

---

### Post by handy on 2008-08-06
> **cardinals_fan said:**
> I love Vim and use it.  However, this experience shows the value behind an "update early, update often" philosophy.  When I run an update almost every day, the files rarely pile up like that.

Yes I agree, I update Arch fortnightly at the latest on my main machine.  The Arch install that I used was my initial test install which uses one of the drives that I use via drive drawers, on my 2nd (testing) machine.  It was only bought into life because the iMac was away for warranty repair.  Fortunately, the situation has bought up a very important point regarding updating on Arch, about which I was ignorant.  I am grateful that I had this learning experience on machine no.2 & not my main box. ;-)

> **kpkeerthi said:**
> I use [meld]("http://meld.sourceforge.net/") to see the differences and merge if need be

Thank you so much ***kpkeerthi*** for bringing [***_Meld_***]("http://meld.sourceforge.net/") to my attention, I have not yet been able to install & test it, (as the Arch machine is still down).

Meld *looks* perfectly suited to the job! :-D  If it proves to be as good as it looks, I will update the iMac wiki entry to help new Arch users that come via that hardware route. 

***[Edit:]** There are instructions on this problem in the [**[I]_Arch Beginners Guide - Files_***]("http://wiki.archlinux.org/index.php/Beginners_Guide#Files")[/I]

---

### Post by handy on 2008-08-06
> **kpkeerthi said:**
> I use [meld]("http://meld.sourceforge.net/") to see the differences and merge if need be

I just attempted to install meld & found that it requires the Gnome desktop.

Unfortunately for me, (in this case anyway) I use Openbox.

---

### Post by kpkeerthi on 2008-08-07
It does seem to pull quite a lot of GNOME packages. But since I already use GNOME Desktop Environment, it didn't add anything unwanted for me. Sorry mate. :)

---

### Post by handy on 2008-08-07
> **kpkeerthi said:**
> It does seem to pull quite a lot of GNOME packages. But since I already use GNOME Desktop Environment, it didn't add anything unwanted for me. Sorry mate. :)

It does the job so beautifully that it tempts me to run the Gnome desktop as an option.

Thus far the jury is still out... :-)

---

### Post by Patogen on 2008-08-07
> **handy said:**
> ***Misfit138***'s tip as supplied on the Arch forum is as follows:

***vimdiff file.conf file.conf.pacnew ***


What methods do you other Arch users use when you have to merge config' files after a pacman -Syu ?


Yes. I use vimdiff now aswell. However you can just issue:

vimdiff file.conf{,.pacnew} this will not always be shorter (and aswell we have tab complete if we want so writing stuff out isn't really an issue). I often use this feature of the shell, that you can issue things like as they were mathematical sets. For instance:

cp xorg.conf{,.bak} will copy xorg.conf to xorg.conf.bak, this is great for scripts aswell. I believe that it's worth to learn vim, the basic feature of it is good even when just editing small config files. It's a time saver.

---

### Post by K.Mandla on 2008-08-07
I sometimes 
```
cat file.conf.pacnew >> file.conf
```
and then hack away at it mercilessly.

And then stare in confusion when my system doesn't work, of course. :roll:

---

### Post by Barrucadu on 2008-08-08
I generally just mv the *.pacnew files over the previous files and edit in my changes - but only if I knew what exactly was changed.

---

### Post by Pogeymanz on 2008-08-09
I just open them in different windows and apply changes manually. Yeah, I'm a loser.

I am trying to learn how to use vim, though. So maybe that will change soon, and I'll be 1337.

---

### Post by rsambuca on 2008-08-10
> **Pogeymanz said:**
> I just open them in different windows and apply changes manually. Yeah, I'm a loser. Ditto.  Fellow loser here.
> **Pogeymanz said:**
> I am trying to learn how to use vim, though. So maybe that will change soon, and I'll be 1337.Nah, it doesn't seem to happen enough for me to bother with learning to use vi.  I am happy to be a loser :neutral:

---

### Post by handy on 2008-08-10
> **rsambuca said:**
> Ditto.  Fellow loser here.
Nah, it doesn't seem to happen enough for me to bother with learning to use vi.  I am happy to be a loser :neutral:

I expect I will end up going this way too.  At the very least I will be refreshing my memory of the .conf files which as I get older needs to be done more & more often!

I'm a loser too, of my memory... :lolflag:

---

### Post by handy on 2008-08-10
I have just completed a *yaourt -Syu*, it was a big one, nearing 300Mb download, (as previously mentioned my no.1 machine has been away for weeks on a warranty job).  

I had conflicts & about 8 .conf.pacnew files to look at, though not all required editing.  Overall it would have taken me (including download time) about 2 hours to get through it.

A more experienced Archer would have been quicker for sure.  It wasn't a great deal of fun (I am very tired at the moment which certainly doesn't help :-))

I contemplated installing meld, which would certainly make dealing with the .conf.pacnew files easier & quicker; but I don't really want to install Gnome...

Thinking I'll just try to do an -Syu every couple of days in the future & sudo the emelfm2 directory utility which has a built in editor, I can also call leafpad from the right menu when needed also.

---

### Post by Skarjoko on 2008-08-12
I also open them up in 2 different windows and just compare the two. 

However, the only time this happened was when a pacman update came out recently. I just had 1-2 extra repoes in my old conf that I copied over, so no real problems here.

---

### Post by MisfitI38 on 2008-08-19
Vimdiff ftw.
You must learn Vim; I wrote a pretty straightforward quickstart guide in the wiki that will learn it to you in minutes. ;)

---

### Post by RiceMonster on 2008-08-19
> **Pogeymanz said:**
> I just open them in different windows and apply changes manually. Yeah, I'm a loser.

I am trying to learn how to use vim, though. So maybe that will change soon, and I'll be 1337.

You can split the screen to edit both files or open them up in tabs in vim.

:tabedit /path/to/file/ for tabs
:sp /path/to/file for horizontal split
:vsp /path/to/file for vertical split

To switch through tabs, hit gt or type :tabn<0-9>. To switch between "tiled" files, use Ctrl-w + hjkl, and to move their location use Ctrl-w + HJKL. Vim's great once you learn it :).

---

### Post by handy on 2008-08-19
> **MisfitI38 said:**
> Vimdiff ftw.
You must learn Vim; I wrote a pretty straightforward quickstart guide in the wiki that will learn it to you in minutes. ;)

> **RiceMonster said:**
> You can split the screen to edit both files or open them up in tabs in vim.

:tabedit /path/to/file/ for tabs
:sp /path/to/file for horizontal split
:vsp /path/to/file for vertical split

To switch through tabs, hit gt or type :tabn<0-9>. To switch between "tiled" files, use Ctrl-w + hjkl, and to move their location use Ctrl-w + HJKL. Vim's great once you learn it :).

:lolflag:  Ok, Ok, I will check out your Quickstart MisfitI38, thanks for both your post & the effort in manufacturing the guide.

---

### Post by rsambuca on 2008-08-19
> **MisfitI38 said:**
> Vimdiff ftw.
You must learn Vim; I wrote a pretty straightforward quickstart guide in the wiki that will learn it to you in minutes. ;)

If I have to learn how to use vim in order to use Arch, I think I will go back to Ubuntu :)

---

### Post by handy on 2008-08-19
> **rsambuca said:**
> If I have to learn how to use vim in order to use Arch, I think I will go back to Ubuntu :)

I know you are tongue in cheek but I'll reply anyway:  

You don't have to go anywhere near vim to use Arch.

When the occasional .pacnew comes up use 2 editor windows/tabs.

I consider this to be the toughest part of using Arch, & it really isn't that tough once you understand that it is important not to ignore the .pacnew situation.

---

### Post by fwojciec on 2008-08-19
Git version of yaourt allows automatic merging pacnew files with -C switch.  It requires enabling AutoSaveBackupFile option in yaourtrc.  Also, it will not work immediately, since yaourt apparently needs to store two versions of each config file before it can make intelligent decisions on how to merge.  I just enabled this yesterday, so I haven't actually seen it work yet, but it looks like a very cool feature, if it indeed works like I imagine it might.

---

### Post by rsambuca on 2008-08-19
> **handy said:**
> I know you are tongue in cheek but I'll reply anyway:  

You don't have to go anywhere near vim to use Arch.

When the occasional .pacnew comes up use 2 editor windows/tabs.

I consider this to be the toughest part of using Arch, & it really isn't that tough once you understand that it is important not to ignore the .pacnew situation.

Yeah, I just opened both in different windows of gedit.

---

### Post by handy on 2008-08-20
> **fwojciec said:**
> Git version of yaourt allows automatic merging pacnew files with -C switch.  It requires enabling AutoSaveBackupFile option in yaourtrc.  Also, it will not work immediately, since yaourt apparently needs to store two versions of each config file before it can make intelligent decisions on how to merge.  I just enabled this yesterday, so I haven't actually seen it work yet, but it looks like a very cool feature, if it indeed works like I imagine it might.

Please keep us updated on this?

---

### Post by FakeOutdoorsman on 2008-08-22
I often use colordiff to quickly look at the differences, make a backup, and then edit the original.  [colordiff]("http://aur.archlinux.org/packages.php?O=0&L=0&C=0&K=colordiff&SeB=nd&SB=n&SO=a&PP=25&do_Search=Go") is available in AUR.  Here's an easy way to make a backup:
```
cp /etc/rc.conf{,.bak}
```
This will create the file /etc/rc.conf.bak.

I used to use Meld extensively when I used Gnome and Ubuntu but not anymore unfortunately due to it's Gnomependencies.

---

### Post by handy on 2008-08-23
> **FakeOutdoorsman said:**
> I often use colordiff to quickly look at the differences, make a backup, and then edit the original.  [colordiff]("http://aur.archlinux.org/packages.php?O=0&L=0&C=0&K=colordiff&SeB=nd&SB=n&SO=a&PP=25&do_Search=Go") is available in AUR.  Here's an easy way to make a backup:
```
cp /etc/rc.conf{,.bak}
```
This will create the file /etc/rc.conf.bak.

I used to use Meld extensively when I used Gnome and Ubuntu but not anymore unfortunately due to it's Gnomependencies.

Thanks, I'll have a look at colordiff.

---

### Post by fwojciec on 2008-08-23
> **handy said:**
> Please keep us updated on this?

Well, here is the first update -- I found this wiki page on the French Arch Linux page.  It's in French, but it should give the idea of how the system works even if one doesn't speak that language:
[http://wiki.archlinux.fr/howto:archlinux:gerer_pacsave_pacnew]("http://wiki.archlinux.fr/howto:archlinux:gerer_pacsave_pacnew")

There is also some explanation of the mechanism in this thread (see the posts by wain, the author or yaourt):
[http://bbs.archlinux.org/viewtopic.php?id=53532]("http://bbs.archlinux.org/viewtopic.php?id=53532")

I'm still waiting to collect enough pacnew/pacsave files to see this in action myself...

---

### Post by dijxtra on 2008-08-27
> **handy said:**
> I consider this to be the toughest part of using Arch, & it really isn't that tough once you understand that it is important not to ignore the .pacnew situation.
Damn :-D After my pacman -Syu few minutes ago everything works fine so I decided to go with "if it works don't repair it" philosophy, but I guess you changed my mind :-D So, this is what I got:

# ls *new*
group.pacnew gshadow.pacnew pacman.conf.pacnew passwd.pacnew shadow.pacnew

I suppose I have to update all of them?

As I see, preferred technique is to use vimdiff. Now, my religion (Church of Emacs) forbids me from using vim, so are any True Believers here to advise me how to do this most painlessly using Emacs? :-)

---

### Post by Barrucadu on 2008-08-27
Open the original, and the pacnew file in Emacs, compare them and incorporate any changes. Usually, not many changes are needed. Good to see another believer on here :)

---

### Post by dijxtra on 2008-08-27
> **Barrucadu said:**
> Open the original, and the pacnew file in Emacs, compare them and incorporate any changes. Usually, not many changes are needed. Good to see another believer on here :)

Just did that. I suppose I messed up with pacman.conf because now I get a bunch of Transient resolver errors when I try to pacman -Syu. Lessons learned: 1. first backup pacman.conf and pacman.cont.pacnew before doing edits; 2. don't ******' delete those two before testing pacman. D'oh.

So, I suppose my pacman.conf is messed up now (although I can't see the difference, in fact I swear I just added

```

# kde 4 - for kdemod4 packages >= KDE 4.1.0
[kdemod-core]
Server = http://kdemod.iskrembilen.com/repo/core/i686

```

to the end of the file).

Anyway, this is full history: 
* installed Arch from CD
* did pacman -Syu, pacman found newer version of itself
* did pacman -S pacman
* did pacman -Syu successfully
* read this forum thread
* updated pacman.conf (I just used pacman.conf.pacnew and added those [kdemod] stuff at the end)
* pacman -Syu failed with "Transient resolver error"s

Any ideas what to do? Can I just steal somebody else's pacman.conf (since I didn't do any special edits to it)?

---

### Post by fwojciec on 2008-08-27
Here's the default pacman.conf:
[http://repos.archlinux.org/viewvc.cgi/pacman/repos/core-i686/pacman.conf?revision=8131&view=markup]("http://repos.archlinux.org/viewvc.cgi/pacman/repos/core-i686/pacman.conf?revision=8131&view=markup")

And here's pacman.d/mirrorlist as well, in case you need it:
[http://repos.archlinux.org/viewvc.cgi/pacman/repos/core-i686/mirrorlist?revision=8131&view=markup]("http://repos.archlinux.org/viewvc.cgi/pacman/repos/core-i686/mirrorlist?revision=8131&view=markup")

---

### Post by dijxtra on 2008-08-27
OK, next obvious thing is that I might not have a working Internet connection. And, that is right assumption. After pacman -Syu my Internet connection went bananas. wget says: Temporary failure in name resolution. Any ideas what happened here or how to determine what happened?

---

### Post by fwojciec on 2008-08-27
What do ifconfig/iwconfig tell you?  Is the network interface working correctly?  Did you try connecting to different addresses?

---

### Post by dijxtra on 2008-08-27
> **fwojciec said:**
> What do ifconfig/iwconfig tell you?  Is the network interface working correctly?  Did you try connecting to different addresses?
I must say that using Arch really is exciting experience (and I'm not being ironical): no way I could learn this much about GNU/Linux by just using Ubuntu.

Anyway, ifconfig shows me only lo, no eth0 present. I should have remembered to look there immediately, sorry. I tried  to figure out what is racing over the screen while booting, and earliest error I could read was:
FATAL: Could not load /lib/modules/2.6.25-ARCH/modules.dep: No such file or directory
Which is logical because in /lib/modules/ I only have 2.6.26-ARCH.

It seems like pacman -Syu really messed up my system...

---

### Post by Barrucadu on 2008-08-27
If you installed a kernel update, you'll need to reboot for things to  work properly :)

---

### Post by dijxtra on 2008-08-27
> **Barrucadu said:**
> If you installed a kernel update, you'll need to reboot for things to  work properly :)
Yup. Rebooted a few times.

---

### Post by dijxtra on 2008-08-27
OK, I did depmod which created /lib/modules/2.6.25-ARCH/modules.dep, but now I get:
FATAL: Module mii not found.
FATAL: Module pcnet32 not found.

I suppose that creating 2.6.25-ARCH was not the way to go, but I had to try it ;-)

Sooooo, is there a way to tell arch to use 2.6.26 kernel and see if 2.6.25-ARCH is useful?

BTW, I enabeled bootlogd (put BOOTLOGD_ENABLED = Yes in /etc/default/bootlogd) but there's no /var/log/boot file. :-(

---

### Post by fwojciec on 2008-08-27
Try something like this:
Run "ls /var/cache/pacman/pkg/kernel26*"
That should give you the list of kernel packages in pacman's cache.  Reinstall the latest version with pacman -U [full path to the package file] (on my system it would be pacman -U /var/cache/pacman/pkg/kernel26-2.6.26.2-1-x86_64.pkg.tar.gz).  As you're installing keep an eye on the messages -- mkinitcpio should report "SUCCESS!" twice, after generating the regular and the fallback images.
Reboot and see if the card works.

---

### Post by dijxtra on 2008-08-27
> **fwojciec said:**
> Try something like this:
Run "ls /var/cache/pacman/pkg/kernel26*"
That should give you the list of kernel packages in pacman's cache.  Reinstall the latest version with pacman -U [full path to the package file] (on my system it would be pacman -U /var/cache/pacman/pkg/kernel26-2.6.26.2-1-x86_64.pkg.tar.gz).
Already did that, nothing changes. Arch again searches for /lib/modules/2.6.25-ARCH/.

> **fwojciec said:**
> As you're installing keep an eye on the messages -- mkinitcpio should report "SUCCESS!" twice, after generating the regular and the fallback images.
Reboot and see if the card works.
I did the pacman -U thing again, this time I logged the output. And, there are two SUCCESSes, yes. There, it says:
==> Running command: /sbin/mkinitcpio -k 2.6.26-ARCH -c /etc/mkinitcpio.conf -g /boot/kernel26.img
[...]
:: Generating image '/boot/kernel26.img'...SUCCESS

Then I reboot and I get "FATAL: Could not load /lib/modules/2.6.25-ARCH/modules.dep: No such file or directory" (I removed /lib/modules/2.6.25-ARCH/). Go figure.

I ran out of ideas :-(

---

### Post by fwojciec on 2008-08-27
The problem probably has something to do with the fact that you're installing kernel 2.6.26 and the boot is looking for files in kernel 2.6.25 directory.  I don't know why this is happening, something must be mis-configured somewhere, this isn't the default behavior.

EDIT:  oops, I didn't realize that you already knew that...  Try making a thread about this on Arch forums, maybe someone there will know.

---

### Post by dijxtra on 2008-08-28
> **fwojciec said:**
> Try making a thread about this on Arch forums, maybe someone there will know.
Just did that: [http://bbs.archlinux.org/viewtopic.php?pid=412738#p412738](http://bbs.archlinux.org/viewtopic.php?pid=412738#p412738)

Thanks everybody for trying to help!

---

