---
title: "[SOLVED] Fn Key"
date: 2008-03-11
forum: Apple Intel Users
---

### Post by bozzochet on 2008-03-11
Hello to all!

I have Kubuntu 7.10 on my MacBook SantaRosa. From yesterday I'm not able to use my Fn key as I've been till this moment.
If I use "xev" I don't see any difference pushing "Key" or "Key+Fn". Seems like if this key (Fn) was broken.
Obviously under MacOsX it continues to works and if I use "xev" (by X11 under MacOsX) I see the difference (for example the "backslash" if pushed with "fn" became Delete).
I tried ti reconfigure xorg but nothing to do...
Any idea?!:(
Thanks

---

### Post by eitan on 2008-03-11
my query is somewhat related to this so i'm posting to the same thread.

i have a 4th generation macbook pro (4,1).  running hardy.

fn key does not work.

which means delete key, pgup/pgdown, home/end
are pretty much dead.  also, fn in combination with the function keys
for volume control, contrast, etc.. does not work either (i have
pommed v1.16 installed from the mactel support repository).

thanks,
/ eitan

---

### Post by bozzochet on 2008-03-12
You can try to change the behavour of fn key editing /etc/pommed.conf changing "fnmode". You can change the usage of F1,F2,ecc keys bringing to working like in MacOsX (You have to push Fn+KEY to make F1,F2,ecc.. but only KEY to change volume, for example)
 Obviously that if "Fn" doesn't work (as for me), after this change you can change brightness, volume, ecc... but cannot use F1,F2,ecc...
I'm saying it only to "test" if pommed is working correcly
Then we HAVE to find the problem!!!

---

### Post by bozzochet on 2008-03-12
Ooops!
After I posted to you I tried myself if pommed was really working and the problem was (ONLY) in Fn key... Pommed isn't working also changing fn behaviour!
I disinstalled it but Fn didn't began to work...

I have no idea!!!:confused::(

---

### Post by bozzochet on 2008-03-12
Sorry...

Pommed is working! Is working only the CD-ejecting but is working (killing pommed the Eject key doesn't work). The other keys don't work but they are all related to Fn (maybe also in the MacOsX-behaviour) so for now isn't this the problem...
I'm trying to change also the kernel but I'm not understanding the problem...
If you're more lucky let me now...

---

### Post by bozzochet on 2008-03-12
I don't know if was related but since I have this problem I have also problem with Ksynaptics (I use Kubuntu) and with Setting->Keyboard&Mouse->Touchpad:

```
Shared Memory is not accessible.
Please add the option 'SHMConfig ''on''' into the touch pad section of /etc/X11/xorg.conf
```

even if I have this option enabled on my xorg.conf...

](*,):cry::sad:

---

### Post by eitan on 2008-03-12
my experience is the same as yours.  only the eject button works.
fnmode tweaking does nothing.  the issue is not with pommed 
but with the fn key not working.

thanks, / eitan

---

### Post by bozzochet on 2008-03-12
But until sunday it was working correcly, since Xmas!!!! And I think to have not change anything!!!!

---

### Post by eitan on 2008-03-12
that's interesting.  for me this is a brand new installation
of hardy heron on brand new hardware (macbook pro 4,1).
so i anticipated issues.  i'm surprised to hear you're having
the same issues running gutsy on an mbp3.

/ eitan

---

### Post by bozzochet on 2008-03-12
Yes I have MB 3.1 (MacBook, NOT MacBookPro!!!) with Gutsy 7.10. the only thing in common is that in the last days (but I'm speaking of 15 last days) I "tried" the hardy kernel (2.6.24), and I didn't notice nnthing of strange; But now I disintalled it and I "come back" to 2.6.22 (I continued to use it for all the period, only sometimes I tried the other kernel for trying to use the "appleIR", that now I'm not able to use on 2.6.22, and to load wireless driver, working on 2.6.22, with ndiswrapper but without success on 2.6.24) and from sunday on evening I have this problem...
:(

---

### Post by eitan on 2008-03-12
fyi:  i just tested the package "mactel-support-fnmode-fix"
but it made no difference.  i suspect perhaps the next
kernel update might fix this issue.  we need to check
the hardy bug database if this is a known issue to the
dev team.

/ eitan

---

### Post by eitan on 2008-03-12
ok, it looks like this is well known issue.
here's the bug:

[https://bugs.launchpad.net/mactel-support/+bug/162083](https://bugs.launchpad.net/mactel-support/+bug/162083)

the last note states that the 2.6.24-12.21 version of the kernel
fixes this issue.  the latest one in the repositories (the one
i'm running is -12.20.  i'll post an upate after the next kernel
update comes down and let you know whether this issue
is fixed.

/ eitan

---

### Post by bozzochet on 2008-03-12
Yes, I also tested, with no difference also for me...
I hope in the kernel update but the problem is that for me it WAS WORKING until sunday!!!
It WORKED before and NOW doesn't work, it's strange!!! If it never had worked I would think that was only the kernel "old", but isnt' so...

---

### Post by eitan on 2008-03-13
well, i just took a linux-image update this morning.
my previous version was 2.6.24-12-generic (version 20)
the new version is 2.6.24-12-generic (version 22)
which supposedly fixes the bug i linked to in a previous
posting to this thread.

the update makes no difference in terms of the fn key functioning.
again this is with a macbookpro gen4 (4,1) and hardy heron.

i'm thinking about switching to the mactel kernel.
any advice on whether or not to do that? does that
break anything else?

thanks,
/ eitan

---

### Post by bozzochet on 2008-03-13
A problem shouldn't be, I'm using mactel kernel (2.6.22) and is ok (it's fixing some problems of complete freezing that I have with "normal" kernel). Now I try the 2.6.24 kernel, but now I have yet the 2.6.22 because with the new kernel I'm not able to use the wireless card. I have no native support for it and in new kernel I don't find "ndiswrapper" module that I'm currently using with my actual kernel. Are you able to make the wireless working?!

---

### Post by eitan on 2008-03-13
with respect to wireless, whether i have it working;  the answer is 
both yes and no.

it's working but i have to manually do this each time i boot up:

sudo modprobe -r ssb
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper

only then does iwconfig actually show me wlan0.

the problem is that the ssb module is conflicting.

so i installed ndiswrapper and used the instructions from that project's
web pages on sourceforge.

i had to copy a .exe file out of the mac dvd (under bootcamp)
and extract an inf file that i then instructed ndiswrapper to load.
that all worked.

i tried specifying ssb in the blacklist file which didn't work.
i then read somewhere else that it had to be specified
in here instead for ubuntu:
 /etc/default/linux-restricted-modules-common

and that didn't work either.  at that point i decided to take
a break.

/ eitan

---

### Post by bozzochet on 2008-03-13
Yes the part of .ini file I had also to do and now (kernel 2.6.22) is working correclty...

The part of ssb module to remove I don't know but on 2.6.22 I have no this module...

Instead of making manually at boot time you can put the 3 command in /etc/rc.local, isn't it?!

The problem for me is that with 2.6.24 I have no ndiswrapper module to `modprobe', now I'm installing the 2.6.24-12(22) and I try again...

In few minutes I say if the Fn key is working for me and If it'a all ok...

---

### Post by eitan on 2008-03-13
> Instead of making manually at boot time you can put the 3 command in /etc/rc.local, isn't it?!

that's true.  but i think i'd rather figure out how to properly prevent a module
from autoloading on boot.  i just need a little time.

>The problem for me is that with 2.6.24 I have no ndiswrapper module to 
> `modprobe', now I'm installing the 2.6.24-12(22) and I try again...

right.  my understanding is that it's really easy if you use hardy
and the hardy repositories, but not so easy if you're using gutsy.

> In few minutes I say if the Fn key is working for me and If it'a all ok...

looking forward to finding out if it worked for you.
thanks,
/ eitan

---

### Post by bozzochet on 2008-03-13
>>The problem for me is that with 2.6.24 I have no ndiswrapper module to
>> `modprobe', now I'm installing the 2.6.24-12(22) and I try again...

>right. my understanding is that it's really easy if you use hardy
>and the hardy repositories, but not so easy if you're using gutsy.

I use hardy repo only to install kernel and all related packages (including linux-ubuntu-modules, linux-backport-modules, linux-restricted-modules, ecc...) so I have (or better `had', because for the new istallation of kernel i have no yet finished) the modules, but no the ndiswrapper module...

---

### Post by bozzochet on 2008-03-14
](*,), ](*,) and ](*,)...

Now I'm not able to install the new kernel (I made it easily till 5-6 days ago) because stupid problems `module_init_tools` that wants to overwrite some old file changing their name and this is return an error. For avoiding it I tried to manually remove any of those files and the installation in this way proceed. But restarting the system the new kernel doesn't work (the first time even the old, infact I had to manually restore the removed file) because he doesn't find for example /sbin/modprobe (one of the removed file that the other kernel however see correctly) and then it can find the root file system,  by passing the root=UUID=XXXXX and not even by passing root=/dev/sdaX...
Now I'm with no ideas beside of waiting to update complety to hardy, for which I'd like to wait the official release...

---

### Post by bozzochet on 2008-03-14
I tried to remove some `stuff': compiz, avant, emerald and all the packages from hardy.

Now my Fn Key IS WORKING!!!!! And at the same time I resolved the problems on Synaptic Touchpad.

Now, unfortunately, I CANNOT OPEN MORE THAN 1 GRAPHICAL APPLICATION!!!!

When I try to open the second (by command line) I have:

```
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
```

And now I have always this problem but I had this, only with compiz, also in the last days...

Now I try to post of this particular problem on the forum....

---

### Post by eitan on 2008-03-15
hi bozzochet,

  glad to hear the fn key problem is resolved for you.
  i'm running nothing but hardy so i don't think your
  solution applies to me.  i'm not running emerald
  or avant, just compiz.  running a different window
  manager (metacity) has no effect on the functioning
  of the fn key.

  i'm fairly certain from the list of patches on the launchpad
  that i cited a few entries ago that this problem requires
  a patch to the latest kernel.  perhaps it works with 
  third generation macbook pro's, but definitely not with
  generation 4,1.

  i could try to substitute my kernel image with the one
  from the mactel support, but i'm a little hesitant to do that,
  and i'd rather see the patches applied to the main repository
  kernel of course.

thanks, / eitan

---

### Post by bozzochet on 2008-03-15
...It WORKED, after the next reboot all returned as before, with no Fn working AND no Synaptic Touchpad (ksynaptics or gsynaptics) working (I'm quite sure that the two problem are related).

The mactel kernel is quite sure (also for a not apple hardware) and for the hardy kernel (2.6.24) I think you can install it beside the standard kernel, infact you have the 2.6.24-XX-generic, the 2.6.24-XX-server, 2.6.24-XX-xen, ecc... and the 2.6.24-XX-mactel, so if you have problem with it you can easily reboot with the other one...

Now I'm resolving my problem with "Xlib" and then I try something to resolv the Fn problem...

Thanks to you, too...
Matteo

---

### Post by bozzochet on 2008-03-16
Sorry, only a question:

Is your gSynaptics (or kSynaptics) working?! I can use my trackpad in a `dummy' mode but now (since the same period from which the Fn problem began) I cannot use all the spcial features given by synaptics module...
I'm quite sure that the 2 problems are related...

Thanks,
Bye

---

### Post by bozzochet on 2008-03-18
:)----All it's ok!!!:)

I solved all the problems!
1) The Xlib problem was in a corrupted kmsmserver in ~/.kde/share/config/ and the solution was simply to remove it before starting kde and it was re-created correctly. But surely this problem was not related to the others.

2)The Fn key now is working using the kernel from Mactel (2.6.22-14.51) because not the 14.52 (gutsy-security) and not the 14.46 (gutsy) make this key working correctly.

3)The trackpad not recognized correctly form X and Synaptics is also a kernel related problem and infact now is working good!

Bye

---

### Post by eitan on 2008-03-18
glad to hear your problem is solved!

to answer your previous question, i have no issues with the 
trackpad on my end.  i can use it like a one-button mouse.  i almost never
use the trackpad.

with hardy i think i'm stuck and sticking with 2.6.24 kernel.
i do hope a fix for the fn key issue is coming up (again, running
hardy heron, on a macbook pro 4,1).
it really sucks not having a pgup/pgdown/delete/home/end key.
not to mention the pommed stuff:  volume control, contrast, etc..

thanks,
/ eitan

---

### Post by bozzochet on 2008-03-18
For the trackpad for me was frustating because if I had to use my computer without an external mouse I was not able to right-click. With Touchpad Synaptics working fine I can do a two finger click (for example) for making right click.

If you have not the possibility to try the mactel kernel I cannot uggest ot use xmodmap. With xmodmap, for example I made the left-apple key be "Insert" and right-apple key "Right-Click" but you can make any key you want using for example also F1,F2,F3 you don't use usually, also using combination like Shift+KEY, Alt+KEY, AltGr+KEY. Obviously in this way you cannot use however the special keys from pommed but the `damage', till a bug-fix, is only an half-damage...

I hope you resolve your problem in few days...
Matteo

---

### Post by pierrelux on 2008-04-10
I don't quite like having to recompile the kernel for this only key... I remapped some of the function keys in System -> Keyboard Shortcuts. For example, «Volume Up» is activated with «CTRL+F12»

But still, I'd prefer having the fn key to work... I might do it when I'm gonna have enough things to change in the kernel.

---

### Post by bozzochet on 2008-04-10
Sorry, I didn't understand you question (if there's one...) cause my poor english...
I didn't recompile kernel, I use the Mactel kernel from semi-official repository (repo on PPA Launchpad from Canonical)...

---

### Post by cyberdork33 on 2008-04-10
it is not official at all... it was made by the community.

---

### Post by bozzochet on 2008-04-11
Yes, infact I use the term semi-official!!
Is not, neither, a package made by a person who made this package at "home" and putted it on his personal site; it's  package that is on ppa!!!

---

### Post by cyberdork33 on 2008-04-11
> **bozzochet said:**
> Yes, infact I use the term semi-official!!
Is not, neither, a package made by a person who made this package at "home" and putted it on his personal site; it's  package that is on ppa!!!yes, but anyone with a launchpad account can have a ppa now (including user-created teams)

---

### Post by bozzochet on 2008-04-11
Yes, ok...
But however the mactel kernel is a good "product" and solve some problems with my MacBook, including the Fn key.
Anyone can try the generic kernel of mactel, installing also the server one (official); of something goes wrong you can boot with the server one and come back to official generic...

---

