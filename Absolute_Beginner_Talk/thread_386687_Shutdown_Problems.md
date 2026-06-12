---
title: "Shutdown Problems"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by OldGrey on 2007-03-17
Hi,

I did a clean install of 6.10 this am on a dual boot with Windows XP. All went well except when I shutdown just as I thought it was actually going to shutdown the screen went blank and I got rows of text like:

"2577.5066 58] - k8: failing targ, change pending bitset". 

The bit before ] changed on each line otherwise each line is the same. They kept coming and once the screen was full they still keep coming. After what seemed an eternity and the lines kept on coming I got bored and switched off, which it did straight away. Can anyone tell me:

1 Apart from the annoyance factor will this hurt the programe / machine?
2 Is there a fix?

By the way I have tried rebooting and shuting down again with the same result. However Windows not affected.

OldGrey

---

### Post by apjone on 2007-03-17
look at dmesg  . there should be something in there

---

### Post by OldGrey on 2007-03-17
Hi

Tried dmesg and it was all in there. What do I do now delete the lot?

---

### Post by apjone on 2007-03-18
just had a quick look around net, may be a acpi problem. in a terminal run
```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bk
sudo gedit /boot/grub/menu.lst

```

find the current kernel you are using and add

```

acpi=off noapic

```
 to the end of the line. eg
```

kernel /boot/vmlinuz-2.6.18-3-amd64 root=/dev/sda1 ro acpi=off noapic

```

this may fix the problem. I am not 100 % though

---

### Post by OldGrey on 2007-03-18
Thanks for the reply. Excuse my ignorance, I am very new to these things, how do I find my current kernel?

---

### Post by apjone on 2007-03-18
> **OldGrey said:**
> Thanks for the reply. Excuse my ignorance, I am very new to these things, how do I find my current kernel?

if in a terminal you type
```

uname -a
Linux ichigo[COLOR="Red"] 2.6.17-11[/COLOR]-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686 GNU/Linux

```

then look in menu.lst for the number in red and put **acpi=off noapic** after that in /boot/grub/menu.lst  eg
```

title           Ubuntu, kernel 2.6.17-11-generic
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/hda2 ro quiet splash acpi=off noapic

```

that should do it

---

### Post by OldGrey on 2007-03-19
Hi again

Sorry to be a pain, but menu.lst doesn't seem to be recognised. Am I missing something?

---

### Post by apjone on 2007-03-19
```

sudo gedit /boot/grub/menu.lst

```

---

### Post by OldGrey on 2007-03-19
Thanks for your patience,

Good news, the penny drooped and I inserted the text as suggested (I have double checked). Bad news, it did not work.

---

### Post by apjone on 2007-03-19
ahh, sorry , I have no other idea's sorry

---

### Post by OldGrey on 2007-03-19
Your efforts are appreciated anyway.

Thanks

OldGrey

---

