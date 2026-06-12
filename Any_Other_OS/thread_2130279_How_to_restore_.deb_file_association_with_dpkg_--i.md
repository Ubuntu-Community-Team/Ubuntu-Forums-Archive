---
title: "How to restore .deb file association with dpkg --install"
date: 2013-03-28
forum: Any Other OS
---

### Post by rozbojnik rumcajs on 2013-03-28
I had installed Ark and Software Center. After that I tried 2 install some '.deb' package by clicking on it. It turned out that instead of an automatic installer just had two options to choose, namely Soft Center or Ark (used 'dolphin' browser). Tried to solve by uninstalling the both, but after it, happened that there is no any association. DOES ANYBODY KNOW HOW TO RESTORE THE DEFAULT ASSOCIATION OF '.deb' FILES? ( 'RAW' situation in that matter as just after have installed the system )  P.S.    I am not interested to have fun with possessing and discovering some sys , would like to have a stable main system 4 others like windows (virtual machine to do heavy calculations, etc. ). Expect that the chosen SYS must be stable should not to surprise me with such complications or give by itself some simple solutions in such a matter. In fact am using kali 1.0 (debian wheezy), but had heard that it is almost similar to ubuntu that is build on debian in generall. Also use a kubuntu ditribution to test. Looking forward to having a smart advise, also 4 future potential similar problems.

---

### Post by stinkeye on 2013-03-29
Too rambling to understand properly.
Is it **gdebi** you want?

---

### Post by rozbojnik rumcajs on 2013-03-29
I do not know if it is 'gdebi', maybe I made mistake writting dpkg.
  Whatever it be just would like to have situation that if I click a file with '.deb'  extension it runs  and automatically be installed.
Just like to restore the state  of "association" of the '.deb' as was at the beginning.

---

### Post by Cheesemill on 2013-03-29
The default application handler for .deb files with Kali is gpk-install-local-file.

---

### Post by rozbojnik rumcajs on 2013-03-29
Ok, great, understood, but how to make it happen to associate gpk-install-local-file with .deb.
In 'System settings' there is a tool, 'file associations' but gives just the only opportunity to choose between components that are present within the main menu.

---

### Post by oldos2er on 2013-03-29
Moved to Other OS/Distro Talk.

---

### Post by stinkeye on 2013-03-29
Here on ubuntu I can associate .debs with gpk-install-local-file using the **~/.local/share/applications/mimeapps.list** file.

eg I searched in the file for deb and changed [COLOR="#FF0000"]this section[/COLOR]...
```
[Default Applications]
application/x-deb=[COLOR="#FF0000"]gpk-install-local-file.desktop[/COLOR]
audio/x-vorbis+ogg=rhythmbox.desktop
audio/3gpp=totem.desktop
audio/ac3=smplayer.desktop
audio/AMR=totem.desktop
audio/AMR-WB=totem.desktop

```

---

### Post by rozbojnik rumcajs on 2013-03-29
Ok I found solution by myself 'via' application of 'Synaptic Package Manager'; It turned out that some bug application;
 maybe a of the previously mentioned had uninstalled gdebi.

I applied SPM, thanks  				 				 					 						 	[**[COLOR=#000000]Cheesemill[/COLOR]**]("http://ubuntuforums.org/member.php?u=559258") advise found 'dgedi-kde' package, and installed it.
Then I updated priority in the order list of associated applications 4 gdebi was third on the list.
I set gdebi as the first to be 'called'.
And at last it is restored.
My comment:
I am a windows user but have never ever faced a situation, except of forcefully removal of half of a system, that '.msi' association is replaced for example by a 'call' rar app instead.
Even if such a potential situation occurrs, in windows it is easy to undo it, or somehow cope with it without deep studies.
Thus looks like it is a real weakness of linux, if U install or make a thing everything is upside down.

P.S.
By the way [**[COLOR=#C61919][B]oldos2er**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=338320"), I am in the right place 4 ubuntu is modified debian as well as kali, all apps and commands I took from that forum works great in kali. Have also ubuntu installed.
( I have 7 HDDs, each with own OS: windows vista, windows 7, windows xp, ubuntu, kubuntu, kali and fedora )
In my opinion if the base stands the same debian 4 all distributions such as ubuntu, kali, kubuntu, etc., it means that indeed it's the right place 2 get a smart advise.
Of course there are some 'little' differences beetween them but in general the same solutions work great in all.   
4 example the found there solution by using synaptic is extracted from ubuntu forum and its advertisement in youtube, and it works in kali ( wheezy ).

---

### Post by rozbojnik rumcajs on 2013-03-29
[**[COLOR=#000000]stinkeye,[/COLOR]**]("http://ubuntuforums.org/member.php?u=684510") thanks am jotting it down 4 future.

---

### Post by oldos2er on 2013-03-30
> **rozbojnik rumcajs said:**
> By the way [**[COLOR=#C61919][B]oldos2er**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=338320"), I am in the right place 4 ubuntu is modified debian as well as kali, all apps and commands I took from that forum works great in kali. Have also ubuntu installed.


Sorry, but ubuntuforums.org only supports the *buntus, not derivatives of Ubuntu nor distros from which it's derived. Debian has its own support forums [here]("http://forums.debian.net").

---

