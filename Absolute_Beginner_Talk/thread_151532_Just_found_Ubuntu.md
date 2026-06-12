---
title: "Just found Ubuntu"
date: 2006-03-28
forum: Absolute Beginner Talk
---

### Post by Flanker35M on 2006-03-28
S!

 Just a brief intro of myself and a hello to the community. I recently switched to a dual boot system with both WinXP and Ubuntu 5.10 Breezy. So far so good, even there has been some moments of disbelief :-k  I am an average computer user, oriented more into gaming than applications and tweaking.

 What pushed me into Ubuntu was the fact I am getting bored on WinXP even it still serves as a game platform for me. Want to try something new and linux itself is very interesting and also offers quite a lot more when looking more into it.

 So..now to the point. Installation went fine, system works nicely and no serious glitches so far. Only problem seems to be the tendency of GDM getting messed up if updating the kernel, for example. I tried to use the SMP-kernel for my dual core AMD, but ended up with gnome not starting and I am stuck in command line ](*,) 

 So, I have read some tips & tricks and will try them before re-installing 5.10 again and starting with the tips and settings I've read about here. Trying to keep the installation as clean as possible and all that. I just would like to ask a few questions for opinions from you more advanced users. Thank you in advance. System is included below for reference.

1) 32-bit or 64-bit Ubuntu if I plan to try switching for linux as primary gaming platform?

2) WINE or Cedega for "porting" games? I mainly play EVE Online and a few others.

3) Most recommended utilities to ensure virus free surfing with a decent firewall on top of that? Other utilities also welcome, like mvoie playback and occasional music listening.

4) Gnome or KDE? What are their differences? Might have been asked a gazillion times already..

 Thank you for any information, I really like to get things rolling with Ubuntu :mrgreen: 


 System reference:

 AMD64 X2 4200+
 Asus A8N-SLI Deluxe mobo (v.1016 BIOS)
 2 x 1Gb DDR400 RAM (dual channel mode)
 MSI nVidia 7800GT 256Mb PCIe
 Maxtor 37Gb 10000rpm S-ATA HDD (15Gb to linux)
 Samsung 160Gb 7200rpm S-ATA HDD (WinXP+games)

---

### Post by Teroedni on 2006-03-28
IMHO



1. For games i think you need 32 bit. 

2.I would say wine since i dont like Cedega

3.Hmm Virus:D You gotta work hard if you ever gonna get infected with Virus or Adware on Linux, Really Hard;)

As for Firewall. Many use a Program like Firestarter

4.;O
Thats its a really difficult question. Both Gnome And Kde is very Good
Its like debating between Mercedes and Bmw or [Insert favourite car here;)]

I myself use Gnome for the moment.... Still Kde is good as well


And welcome ^__^

---

### Post by Darkriser on 2006-03-28
Agree with Teroedni.

2) WINE is free and many games are unsupported, Cedega is much better but it's payware. look at their homepages if your favourite game is supported.

3) well, by default you already HAVE firewall on your ubuntu. it's called IPTABLES (see [https://wiki.ubuntu.com/Security](https://wiki.ubuntu.com/Security) or type man iptables in console). so you should be safe without any additional software. Firestarter is a great choice for easy iptables maintenance (just clicking instead of writing commands in console), plus it delivers some more features (like dynamic firewalling, etc.)

4) Gnome or KDE? Exactly like the post above - these are only different ways to use ubuntu. try installing both and find your favourite. I personally use gnome, but the only argument i have is - i simply like it ;)

---

### Post by mrgnash on 2006-03-28
1. Definitely go with the 32 bit. I struggled for a long time with Breezy 64 and it was one endless series of frustrations.

2. Don't count on either Wine or Cedega for games. In my experience, Windows games rarely work well, if at all on Linux.

3. Firestarter if you want a firewall (not something that I've bothered with, personally) and there's no need for antivirus software unless you need to scan attachments you're sending to Windows users or something. For music playback, Amarok is by far the best, and I've found VLC to be the most reliable movie player -- plus it comes with all the codecs you need. 

4. Out of the two? KDE - better apps, better interface, better experience. But I prefer Xfce or Fluxbox myself -- or if you want to be really daring, give Enlightenment DR17 a go.

---

### Post by meborc on 2006-03-28
3. since you are dual-booting i seriously suggest you use anti-virus, to protect your lesser-brother (read: wind-that-blows-through-the-window)... meaning, you will probably never get a virus that will affect your ubuntu OS, but when copying files between ubuntu-xp it is possible to transfer the viruses there and kill the beast (what is acctually a 'kuollut peura' anywayz)

clamav (installable from apt-get/synaptic) or avg with a port to linux are the ones preffered... oh, there is a how-to to those and to f-prot as well under tips and trick section of ubuntuforums... have fun ;)

---

### Post by Perfect Storm on 2006-03-28
1) Diffently 32-bit at the current state. Hopefully that will change in the near future if you want to game on linux.

2) I've good experience cedega pay version. Easy to use (point'n'click), but it really come down which games we're talking about. Very populare games are supported, better if you check the transgaming gamelist (4 or 5 stars). But you can run both wine and cedega on the same machine. Also if you want to play dosgames there's dosbox. There's dozens of other application to try when it comes to getting diffrent OS games to work on linux. You might also check ubuntu gamelist (in my signature), it's not complete and I'll updating it countinuously.

3) As stated by others, virus' aren't a problem on linux. There's some few but as long you aren't logged in as root you shouldn't be in trouble. Check the security forum for more information, debates etc. I've written some howto's on installing two ant-virus applications which have gui-interface. [F-prot antivirus]("http://ubuntuforums.org/showthread.php?t=88357") which I can recommend espcially for dual-booters and then [avg anti-virus]("http://ubuntuforums.org/showthread.php?t=136064").

4) It's really about taste in the end. Myself I like Gnome it's clean and simple though costumizable without being a ûber-decorated christmas tree. Check the gallery: [http://ubuntuforums.org/gallery/](http://ubuntuforums.org/gallery/) . The best advise is to try both or if you want to try something lighter go for a wm (xfce, Enlightenment, openbox etc. etc. etc.) Plenty to choose from. 

and welcome to the forum :)

best regards
A.I. Dude

---

### Post by RRS on 2006-03-28
[QUOTE=mrgnash]1. Definitely go with the 32 bit. [/QUOTE]

Agreed. Reinstalled 64 bit three times on my AMD machine and was never able to get X (the GUI interface) properly confiquered.

Switched to 32 bit and installation recognized monitor, etc. and almost everything was configured automatically.

For your video card you may still need to manually install the driver using nsdwrapper, can probably find instructions/procedure in other postings if necc.

Welcome aboard.

---

### Post by belikralj on 2006-03-28
Everything I would say has been said. I just want to add

NICE SETUP!!!!

You have a beast there that Ubuntu will make the most of.

---

### Post by Vulpus on 2006-03-28
[QUOTE=Flanker35M]S!
1) 32-bit or 64-bit Ubuntu if I plan to try switching for linux as primary gaming platform? [/quote]

Definately 32-bit, any 64-bit Linux distro I have tried has not been worth the hassle.  I have also found that 64-bit distros seem to have a particular problem with SATA drives.  

> 2) WINE or Cedega for "porting" games? I mainly play EVE Online and a few others.
My addiction to civilization IV is the one reason i still use XP.

> 3) Most recommended utilities to ensure virus free surfing with a decent firewall on top of that? Other utilities also welcome, like mvoie playback and occasional music listening.
I don't bother with virus protection on Linux but ensure I keep it up to date on windows.
The latest version of Kaffeine does the job for me for movies and for music playback you need the one and only **amaroK**


> 4) Gnome or KDE? What are their differences? Might have been asked a gazillion times already..

I think some desktops work better with certain distros.  Overall i prefer KDE but for some reason Gnome seems to suit Ubuntu better.  I have tried KDE on Ubuntu and it just doesnt feel right.  considering the spec of your PC I don't think there is any point in using Xfce, unless you like the minimalist look?

---

### Post by mrgnash on 2006-03-28
> I think some desktops work better with certain distros. Overall i prefer KDE but for some reason Gnome seems to suit Ubuntu better. I have tried KDE on Ubuntu and it just doesnt feel right. considering the spec of your PC I don't think there is any point in using Xfce, unless you like the minimalist look?

That's not quite true... My machine is also pretty fast (for a laptop anyway) but I prefer the way Xfce handles theming (for some reason, I could never get the icon themes to work properly under Gnome - so they'd end up looking inconsistent and ugly, particularly in the menus), the right-click application menu being present right from the get-go, the Xfce panel and the Thunar file manager. It's also the only desktop window manager with native comopositing support. 

And as for KDE, if it doesn't feel right for you under Ubuntu in comparison to other distros such as Debian, why not try and reverting it back to the default profiles? eg:

```
sudo rm -r /usr/share/kubuntu-default-settings/kde-profile/default/share/apps/konqueror
sudo cp /usr/share/apps/konqueror/konqueror-orig.rc /usr/share/apps/konqueror/konqueror.rc
```

---

### Post by Flanker35M on 2006-03-28
S!

 Thank you for the replies and the welcome. I even hooked up a few guys from work that have been fiddling with linux before and after talking to them I am more convinced to learn more :D With time I might even learn something :p 

 About WinXP and linux, I have no interaction between them in any way. That is why the question about how to for gaming. There are only very few games I play and for those that will definitely not run under Ubuntu will stay on the WinXP HDD. I've read that EVE Online players have made it work under linux, that would be a blast :mrgreen: So my main concern is in EVE.

 I will download both Ubuntu and Kubuntu 32-bit then and try out to see which one will be the final choice. So far I have liked gnome, but better test and then make the choice. Now I must head off to How-To section to see if I can switch the desktops on the fly without re-install..yes..I am a n00b and too long since fiddling with command lines :-k 

 Once again thank you for the tips, very much appreciated. Gonna lurk around to see more, something will stick in the small part of brains that are left ;)

---

### Post by digimatic on 2006-03-28
[QUOTE=Vulpus]Definately 32-bit, any 64-bit Linux distro I have tried has not been worth the hassle.  I have also found that 64-bit distros seem to have a particular problem with SATA drives.  
[/QUOTE]

I wouldn't go quite that far...Certainly I'd say as a newcommer to Linux go with the 32bit version until you understand the system better. Otherwise runing 32bit only apps (most games except say UT2004) can sometimes be a bit of a challenge.

But 64bit does work well. The only remaining gripes I really have is that 64bit lags slightly on package availability and you can't have flash on Firefox (without installing the 32bit version of Firefox..which is a pain)

Also I'd say go with Gnome initially. KDE is more familiar to Windows users..but kubuntu has always seemed a bit more buggy than the Gnome release.

---

### Post by meborc on 2006-03-28
[QUOTE=Flanker35M] I will download both Ubuntu and Kubuntu 32-bit then and try out to see which one will be the final choice. So far I have liked gnome, but better test and then make the choice. Now I must head off to How-To section to see if I can switch the desktops on the fly without re-install..yes..I am a n00b and too long since fiddling with command lines :-k 
QUOTE]

you can install both gnome and kde on the same system, so you can switch between them from your log in screen...

if you installed ubuntu (gnome), then to install kde, the simplest is to type:
[B]
sudo apt-get install kubuntu-desktop[/B]

which will then install all the packages that are related tu kubuntu meta-package... i guess it is hard to explain all at once, but there is a lot of threads concerning gnome/kde under absolute beginner talk... just use the advanced search to locate them

and one more caution - if you install kubuntu-desktop, your gnome menu will have some kde applications and vice versa, meaning, that you can use the apps both, in gnome and kde, but also you will have a scrambled menu... it can be fixed though and there are alse threads about how to do it

hope you enjoi ubuntu and remember... the truth is in ubuntuforums

---

### Post by Flanker35M on 2006-03-28
S!

 Seems I have to do some serious forum searching ;) I would need 2 machines..one for browsing forums etc. and the other being setup for linux :D Could check from the other how to and simultaneously do it on the other..Thank you again for answers.

---

### Post by meborc on 2006-03-28
well... to help you with your searching - [http://www.ubuntuforums.org/search.php?searchid=4549085](http://www.ubuntuforums.org/search.php?searchid=4549085)

:mrgreen: the ubuntuforum advanced search is the only help i have ever needed!

---

### Post by Vulpus on 2006-03-28
[QUOTE=mrgnash]That's not quite true... My machine is also pretty fast (for a laptop anyway) but I prefer the way Xfce handles theming... [/quote]

Fair point, but i think that Xfce and the like are SO different from Windows that they are probably off-putting to a newbie.  However, my statement that there is no point in trying them was a bit sweeping.  

i have tried different options with KDE in Ubuntu but always go back to Gnome.  But with SUSE (and Mandriva) I much prefer KDE.

---

### Post by Flanker35M on 2006-03-28
S!

 Will try that out, thank you! I am trying to save this existing installation, even though a new installation takes only 15min or so. Now off to tweak..

---

### Post by Vulpus on 2006-04-01
[QUOTE=mrgnash]That's not quite true... My machine is also pretty fast (for a laptop anyway) but I prefer the way Xfce handles theming (for some reason, I could never get the icon themes to work properly under Gnome - so they'd end up looking inconsistent and ugly, particularly in the menus), the right-click application menu being present right from the get-go, the Xfce panel and the Thunar file manager. It's also the only desktop window manager with native comopositing support. 
[/QUOTE]

I take back what i said about XFCE!  I have just installed Zenwalk ([http://distrowatch.com/table.php?distribution=zenwalk](http://distrowatch.com/table.php?distribution=zenwalk)) on an old Celeron PC.  Zenwalk 2.2 comes with the latest version of XFCE (4.3.0) and I must say I am VERY impressed.  I would recommend anyone to try this version of XFCE.

---

### Post by BoneKracker on 2006-04-01
Gnome vs KDE advice is worthless.  As was said above, it's like cars - it all depends on your personal requirements and tastes.

Anbody who voices a strong opinion that one is better than the other in general is wrong and simply casting flame-bait.

---

### Post by BoneKracker on 2006-04-01
Just one other thought on "Gnome or KDE":

I've put Ubuntu on three machines:
[LIST]
[*]Athlon64 4400+ on A8NSLI-P (similar to your rig) (amd64, booting from RAID0)
[*]A basic Pentium 4 (Dell) (686)
[*]An old PowerPC (Apple G4) (ppc32)
[/LIST]

If I were you I would start off with the default Ubuntu (Gnome) because it still has a lot more users (about four times as many, if I recall correctly).  While I found that both the Ubuntu and Kubuntu sub-communities have adequate participation and documentation to point the way past routine issues, I found that more help was available to resolve platform- and component-specific issues when I was installing Gnome.  For example, I saw a post that had gone unanswered for two weeks in the Kubuntu AMD64 forum from a user who had a simple problem (turned out to be a corrupted download).  Likewise with ppc.  Incidentally, I tried KDE, Gnome and Xfce on each machine.

So, my recommendation is that you get yourself up and running, stable, with your favorite apps, and familiar with the command line (if you are new to Linux in general) -- and THEN by all means try out KDE, which really is a wonderful window manager (and try Xfce too), then YOU decide.

---

