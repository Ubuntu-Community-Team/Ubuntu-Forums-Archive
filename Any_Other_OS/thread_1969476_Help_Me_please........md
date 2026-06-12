---
title: "Help Me please......."
date: 2012-04-30
forum: Any Other OS
---

### Post by abnordude on 2012-04-30
I had debian as my OS....
I wanted to try arch linux....
With a few difficulties and with a lot of wasted time, I finally got arch linux on my PC.....
But when the computer booted, it displayed only arch linux as an option and not debian...
Then I used grub4dos from lucid puppy and got debian as an option...
But now when I tried arch linux....I get this error....Also, the caps lock light keeps on blinking....

Help me...I've wasted considerable time installing arch linux...I dont want to reinstall again....Help me fix this.......

---

### Post by Antman on 2012-04-30
> **abnordude said:**
> I had debian as my OS....
I wanted to try arch linux....
With a few difficulties and with a lot of wasted time, I finally got arch linux on my PC.....
But when the computer booted, it displayed only arch linux as an option and not debian...
Then I used grub4dos from lucid puppy and got debian as an option...
But now when I tried arch linux....I get this error....Also, the caps lock light keeps on blinking....

Help me...I've wasted considerable time installing arch linux...I dont want to reinstall again....Help me fix this.......

You'll get quicker Arch help here: [https://bbs.archlinux.org/]("https://bbs.archlinux.org/")

Also, just a quick tip: If you want to try a preconfigured Arch Linux distro, check out [Bridge Linux]("http://millertechnologies.net/"). The creator has several iso's with various DE's (KDE, GNOME, etc) already setup.

---

### Post by mips on 2012-04-30
Are you using lilo, grub or grub2?

I think Debian uses Grub2 by default so maybe look at installing grub2 in Arch [https://wiki.archlinux.org/index.php/GRUB2](https://wiki.archlinux.org/index.php/GRUB2)

---

### Post by abnordude on 2012-05-04
I found out the solution...

It was rather a simple one....

I just did a 'sudo update-grub' from debian, and it detected arch....

Thanks everyone for the help....

---

### Post by ratcheer on 2012-05-04
That's exactly what I do. I am so happy that the Arch installer allows me to easily skip the bootloader phase. As soon as I finish Installing Arch, I just boot into Ubuntu, run update-grub, and then everything works exactly as it should.

Tim

---

