---
title: "Installing Refit without OSX(need bless)"
date: 2007-12-06
forum: Apple Intel Users
---

### Post by tehkain on 2007-12-06
Hello my fellow free software users. So I am having issues with EFI, I have been booting up traditionally for a while now but the boot time is bugging me. I know this has to do with cycling the GUID and then finally the MBR. So to avoid this I decided to use Refit(again). The issue I cannot (and kinda dont want to) install OS X again to 'bless' the refit setup(which I did manually) with 
```

sudo bless --mount /efi --setBoot --file /efi/efi/refit/refit.efi --labelfile /efi/efi/refit/refit.vollabel

```
So I tried to mount the efi partition using the OS X install CD and bless it from there but of course it does not allow me. So any suggestions? Essentially all I can do now is buy an expensive external drive to install OSX on. Hopefully some of you are more informed then I.

---

### Post by tehkain on 2007-12-06
How small can I make a OSX install? Any chance I can get it below 2gb and onto a usb stick?

---

### Post by cyberdork33 on 2007-12-06
> **tehkain said:**
> How small can I make a OSX install? Any chance I can get it below 2gb and onto a usb stick?

I don't know with versions now, but I have an install of OSX on a G3 iBook that I converted to a digital picture frame that is about that big on a CF card. I just chose to install the base system

---

### Post by chunderbunny on 2007-12-07
Last time I tried to install OSX on a minimal partition the installer wouldn't let me install on anything less than 8GB. 

Searching around the Internet, there doesn't seem to be an equivalent of the OSX "bless" command for Linux, which worries me a little. Is the bless command only needed for Apple's implementation of EFI?

---

### Post by Levo75 on 2007-12-11
> **tehkain said:**
> Hello my fellow free software users. So I am having issues with EFI, I have been booting up traditionally for a while now but the boot time is bugging me. I know this has to do with cycling the GUID and then finally the MBR. So to avoid this I decided to use Refit(again). The issue I cannot (and kinda dont want to) install OS X again to 'bless' the refit setup(which I did manually) with 
```

sudo bless --mount /efi --setBoot --file /efi/efi/refit/refit.efi --labelfile /efi/efi/refit/refit.vollabel

```
So I tried to mount the efi partition using the OS X install CD and bless it from there but of course it does not allow me. So any suggestions? Essentially all I can do now is buy an expensive external drive to install OSX on. Hopefully some of you are more informed then I.

This command doesn't seem to work for me.

Can anyone help me install rEFIt? The boot time is really annoying me.

---

### Post by cyberdork33 on 2007-12-11
> **Levo75 said:**
> This command doesn't seem to work for me.

Can anyone help me install rEFIt? The boot time is really annoying me.

You have to use it in OSX... bless is an OSX command.

---

