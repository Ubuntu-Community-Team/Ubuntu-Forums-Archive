---
title: "Paranoid Win XP User running Ubuntu/Kubuntu on VirtualBox"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by NewConvert on 2007-06-14
I am a new-convert-to-linux running Kubuntu 7.04 as guest OS on Win XP ( host OS) using VirtualBox. My question : Do I need an antivirus program &/or firewall on the guest i.e. Kubuntu ? If not, why - and what would happen if a windows virus finds its way into the Kubuntu guest ? I am assuming that the answers to the above apply to Ubuntu 7.04 running as guest ; if they are different, please give me directions.

---

### Post by NfF on 2007-06-14
nope...windows xp and kubuntu are complete different OS
dont worry, linux has fewer viruses compared to windows.
remember windows -$(Fly):-though easy to use
linux-$(Save!:) hard to use,install blah blah

---

### Post by HotShotDJ on 2007-06-14
> **NfF said:**
> linux-$(Save!:) hard to use,install blah blah
Ex-CUZE-me???  Kubuntu / Ubuntu is not harder to use than Windows and it is EASIER to install on Linux-certified hardware than Windows is on Windows-certified hardware.

---

### Post by lazyart on 2007-06-14
I would guess is possible that a virus could damage the files that make up the virtual machine, but it wouldn't put a virus into the guest OS.

---

### Post by starcraft.man on 2007-06-14
> **NewConvert said:**
> I am a new-convert-to-linux running Kubuntu 7.04 as guest OS on Win XP ( host OS) using VirtualBox. My question : Do I need an antivirus program &/or firewall on the guest i.e. Kubuntu ? If not, why 

No to the AV and Ubuntu has an OS integrated firewall called IPtables, it is very powerful. Reason why, [see here...]("http://www.psychocats.net/ubuntu/security") 

> and what would happen if a windows virus finds its way into the Kubuntu guest ?

99.9% of the time, absolutely nothing. Most windows viruses attack specific APIs or protocols in Windows, and thus it wouldn't understand Linux, it would sit there sad and confused with nothing to attack. Some viruses are of course cross platform and target actual applications like the recent OO scare with badbunny but those are very hard to get. IMO they aren't prevalent or a threat.

The exception is of course running a program in something like WINE, it is designed specifically to run Windows applications in a layer. It is very possible to get a Virus working in that because they go out of their way to create a layer that runs Windows API/protocols/other Windows things to get windows programs working in Linux, thus Viruses would recognize it.

In any case, the VM is isolated from the Host so any infection of either won't go into or out of it.

> -  I am assuming that the answers to the above apply to Ubuntu 7.04 running as guest ; if they are different, please give me directions.

There is no difference, they are just two different desktop environments.

I find it numerous that your a paranoid XP user worried about infecting the Linux Guest, I'd be more concerned about your Host OS :p. Unlike a vanilla and unpatched copy of XP, you won't get infected in under 5 minutes with blaster.

---

### Post by NewConvert on 2007-06-14
Thanks , for the assurance.  but regarding :
 > In any case, the *VM is isolated from the Hos*t so any infection of either won't go into or out of it.

Why , how is this possible ? (You can see that I *am * a new convert)

---

### Post by starcraft.man on 2007-06-14
> **NewConvert said:**
> Thanks , for the assurance.  but regarding :
 
Why , how is this possible ? (You can see that I *am * a new convert)
[URL="http://en.wikipedia.org/wiki/Virtual_machine"]
Here is the wiki on Virtual Machines.[/URL]

Virtual machines (like Virtual Box) have several functions, first and foremost of all is to create a complete virtual operating machine that is capable of running almost any OS. This is ensured by emulating the most generic of hardware that has the greatest range of support. VMs aren't just that though, they are completely self contained and Isolated systems of operation, this has been done since the beginning I believe and for good reason. They are isolated from the host to prevent any actions inside from affecting the host, this is the reason say if you were running Windows in Virtual Box and it crashed or BSoDed, you wouldn't crash your host machine.

Developpers and testers find this essential, able to crash an OS doing a specific change and then bring it back online with not time at all (and with a snapshot feature like Virtual Box have, they can even restore it to before the change without having to reinstall). This is simply the nature of all VMs, you need not do anything extra to Virtual Box to garner this protection. They are very powerful applications IMO, I use Virtual Box almost daily to run different distros/Windows.

---

### Post by NewConvert on 2007-06-14
Thanks, my mind is at peace, at least till I am on Kubuntu !

---

