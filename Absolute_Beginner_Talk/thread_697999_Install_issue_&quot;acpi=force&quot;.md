---
title: "Install issue: &quot;acpi=force&quot;"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by doctorbighands on 2008-02-15
I'm trying to install Gutsy server edition on a legacy machine (550MHz CPU, 408MB RAM). When booting from the install CD, I get a message saying that the BIOS is too old or something, and that "acpi=force is required". I've tried rebooting, hitting F6, and adding acpi=force to the end of the boot string, but the message still appears. Any idea why adding what it wants isn't working?

---

### Post by amingv on 2008-02-15
It's just a reminder. It won't change either way.

In fact, I run a server on similar conditions and didn't edit the line. It should not mean any further problems.

---

### Post by kostkon on 2008-02-15
You could follow [this page from the Ubuntu Wiki on how to debug *ACPI*]("https://wiki.ubuntu.com/DebuggingACPI"). For a start, you could set *acpi=off*.

---

### Post by crf on 2008-02-15
You may edit your grub file:
/boot/grub/menu.lst 
copy the line you normally choose to boot, paste it to add a new line, and then add acpi=force to it.

example
```

title		Ubuntu hardy (development branch), kernel 2.6.24-8-386 with ACPI on
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-8-386 root=UUID=49a51b99-a881-45dd-b8ba-2bf3008b18ef ro quiet splash acpi=force
initrd		/boot/initrd.img-2.6.24-8-386

```

When you boot, you can then choose whether to start with acpi support enabled.
-------
Apparently, the reason why acpi defaults to off for computers with old bios is because they had limited functionality poorly implemented.
I use my computer without acpi, and it works well. suspend works when I press my computer's suspend button, as does shutdown. So what else do you need :D? If you have a laptop, you can also set linux to spin down the disk while in laptop mode using laptop_mode command and the config file in /etc/laptop-mode. 

I have a compaq armada m700.

If you want to, you could go to your computer manuafacturer's website and look for bios upgrades. Often there will be one. There is one for my computer, but the installer needs windows. <shrug>

---

