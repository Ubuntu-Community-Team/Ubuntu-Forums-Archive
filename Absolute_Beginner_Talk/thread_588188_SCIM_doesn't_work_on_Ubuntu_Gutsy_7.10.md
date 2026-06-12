---
title: "SCIM doesn't work on Ubuntu Gutsy 7.10"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by TWO on 2007-10-23
I recently updated from Feisty to Gutsy and had SCIM working fine for enabling Japanese text input. 

Since I've updated, I can't get the program to appear on the panel, nor am I even able to get it to appear when I am in programs such as Open Office or on the Internet.

It's a little frustrating as I already have another problem since I updated to Gutsy.

I have already tried reinstalling it and installing various repositories, but to no avail

I am pretty much out of ideas for now.

Any suggestions would be greatly appreciated. I have been using Ubuntu for a few months now but if you have any instructions please explain the full commands as I am not an advanced user.  


:confused:

---

### Post by jenhsun on 2007-10-24
Check it out this bug
[https://bugs.launchpad.net/ubuntu/+bug/153233](https://bugs.launchpad.net/ubuntu/+bug/153233)

After I enable the complex input to fireup SCIM, keyboard freeze for input.
This problem only in Gutsy 32 and 64 bits only.

FYI

---

### Post by jenhsun on 2007-10-24
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/153233](https://bugs.launchpad.net/ubuntu/+bug/153233) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Check it out this bug
[https://bugs.launchpad.net/ubuntu/+bug/153233](https://bugs.launchpad.net/ubuntu/+bug/153233)

After I enable the complex input to fireup SCIM, keyboard freeze for input.
This problem only in Gutsy 32 and 64 bits only.

FYI

Sorry for the spam post...

---

### Post by jenhsun on 2007-10-28
About anything related on SCIM, Problem solved.

Please take a look at this bug report
[https://bugs.launchpad.net/ubuntu/+bug/34282](https://bugs.launchpad.net/ubuntu/+bug/34282)

And the most important is the document in your
/usr/share/doc/scim/README.Debian.gz

---

### Post by chang47 on 2007-10-30
You can try this solution [http://ubuntuforums.org/showthread.php?t=594743&highlight=scim](http://ubuntuforums.org/showthread.php?t=594743&highlight=scim)

---

### Post by Michal77 on 2007-10-31
HI,

I have used method from: [https://bugs.launchpad.net/ubuntu/+bug/34282](https://bugs.launchpad.net/ubuntu/+bug/34282)
and it works for me here is small HowTo:

```
sudo apt-get install scim-bridge
sudo gedit /etc/X11/xinit/xinput.d/scim
```

them find and change 

```
GTK_IM_MODULE=xim 
```

into 
```

GTK_IM_MODULE="scim-bridge"

```

Restart system. SCIM should works fine with all applications. Maybe you will need start SCIM manually by

```
SCIM -d
```

---

### Post by TWO on 2007-10-31
I have since returned to Ubuntu Feisty Fawn, as I was experiencing sound card issues as well. The SCIM works fine on this distro, so I think I'll remain on this one until the other issue is solved, but I'll take your suggestions for when I do decide to upgrade!

Thanks!

---

### Post by jenhsun on 2007-10-31
> **Michal77 said:**
> HI,

I have used method from: [https://bugs.launchpad.net/ubuntu/+bug/34282](https://bugs.launchpad.net/ubuntu/+bug/34282)
and it works for me here is small HowTo:

```
sudo apt-get install scim-bridge
sudo gedit /etc/X11/xinit/xinput.d/scim
```

them find and change 

```
GTK_IM_MODULE=xim 
```

into 
```

GTK_IM_MODULE="scim-bridge"

```

Restart system. SCIM should works fine with all applications. Maybe you will need start SCIM manually by

```
SCIM -d
```

It works, thanks man.
This solution doesn't exist in SCIM document. I think people should know about it.
This problem looked like exist in Realplayer too. (Xim and GTk...)

---

### Post by cablop on 2007-12-04
GTK_IM_MODULE="scim-bridge"

Solution just works for gnome applications, the guide says you need to set

QT_IM_MODULE="scim-bridge"

for KDE apps too, but it's useless if you use accents in your documents á becomes ´a and ã becomes ~a when you try to input them.

So, for the poeple using Feisty instead of Gutsy, keep in Feisty for more time or find a way to downgrade SCIM in Gutsy to Feisty version... could it be possible?

I'll try, cause Gutsy works well with my widescreen monitor, and feisty... i have to hack or xorg conf or SCIM conf... i prefer to hack SCIM conf.

---

### Post by ryukent on 2008-02-02
I'd give up on SCIM if I were you. The XIM interface hasn't been properly patched yet. Even if you get it working, you'll still be unable to input into many apps, specifically non QT or GTK ones. Go for UIM, it's more stable and compatible.

---

### Post by cablop on 2008-02-22
but it is not supposed that UIM is just for japanese input?

I need chinese input, there's a better alternative? I think i'll start a thread just to ask that question

---

### Post by ryukent on 2008-02-23
UIM does chinese too!!! Just do a search for the package. I think it's uim-pinyin or something like that.

---

