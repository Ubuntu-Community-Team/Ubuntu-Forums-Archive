---
title: "Boot splash screen disappeared"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by Bobtheknight on 2006-12-10
Hey everyone,

I've always wanted to change the boot-up splash screen when the kernel load everything (like network, screen, buses) but after a lot of tries I failed.  Now that entire part disappeared and I get blank screen until the load desktop splash screen (with the icons appearing in a row), then my compy revived itself :D.

So now I don't want to mess with the splash anymore, instead I miss the good old linux command-line kernel boot.  If anyone can help me get back to that it'd be awesome.  This is a feature I noticed in red-hat, centos, but not ubuntu.

Loading Network.......................................................[OK]
Loading bus x and y ..................................................[OK]
Loading keyboard......................................................[OK]
Loading mouse.........................................................[OK]
Loading sound......................................................[Failed]
Loading other stuff...................................................[OK]

^-- The screen I was refering to by "command-line kernel boot" looks something like that.

Thanks in advance.

---

### Post by Ecthelion on 2006-12-12
You have to remove the 'quiet' option in the grub menu to get those messages to show up:

```
sudo gedit /boot/grub/menu.lst
```
Scroll down to the menu entries and remove 'quiet' two times in the menu entry that gets booted by default.

Normally you should see the messages the next time you boot up...

I hope this helps!

---

### Post by nixclusive on 2006-12-12
remove the keyword 'splash' in the kernel command line in /boot/grub/menu.lst . Here's an example:

```
kernel          /vmlinuz-2.6.15-23-386 root=/dev/hdc9 quiet
```

@Ecthelion: the quiet keyword controls the general kernel verbosity on the terminal AFAIK. thanx.

---

### Post by Bobtheknight on 2006-12-12
I removed both quiet and ro splash.  Now I have a basic command line bootup.  Which makes me feel a lot more secure about the boot-process than a blank screen.

The splash did come back a while ago for unknown reasons (maybe I rebooted enough times :P)  But it doesn't show up properly anyway.

Thanks for all the help.

I saw once someone (a mod possibly) tagging my thread as [resolved] after my problem is solved. Is that something I can do myself?

---

### Post by bodhi.zazen on 2006-12-12
Yes.

Edit your first post and one of the tic box options is "resolved"

---

