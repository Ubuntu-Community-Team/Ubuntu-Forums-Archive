---
title: "PowerMAC G5 dual 2.0 no boot after install!"
date: 2005-03-26
forum: Apple PPC Users
---

### Post by CashMAN on 2005-03-26
When i boot from the hoary array 7 cd and succesfully install Ubuntu i get an error when i reboot my comp and start ubuntu! I hangs right after it says Starting Ubuntu...

I get an error something like this: 

Starting Ubuntu...
Pivot_root : no such file or directory
/sbin/init: 420 : cannot open dev/console: no such file or directory
Kernel Panic - not syncyng atempted to kill init!

After that i yust hear the fans speed up!

A also tried Kubuntu.... The same problem! Array 1 of Ubuntu and array 6 gave me the same errors...

---

### Post by DJ_Max on 2005-03-27
What install did you chose? "install-power4"?

---

### Post by Brian McConnell on 2005-03-28
[QUOTE=CashMAN]i yust hear the fans speed up![/QUOTE]
Stan Boreson fan? ah, forget it.
Anyhoo,

Your yaboot.conf file was probably not configured properly. You'll want to boot to the live cd and make the necessary corrections. Sorry I can't tell you exactly how, but I know it's not too difficult. Try to search the ubuntu wiki.
In addition to making sure you installed using the "install-power4" option, make sure any external devices like printers and hard drives, especially hard drives, are turned off at first boot. I've installed Ubuntu a few times on my dual 1.8ghz G5 and although I usually have my external hard drives turned on during install, I've always had a kernel panic at first boot if I don't make sure to turn them off before that first boot.
Hope that helps.

---

### Post by CashMAN on 2005-03-28
i used the Install-power4 option...  LiveCD doesn't wor either... it boots but then i get a black screen...

---

