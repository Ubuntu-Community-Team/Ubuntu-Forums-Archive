---
title: "Blacklist Problem"
date: 2005-10-09
forum: Absolute Beginner Talk
---

### Post by element3260 on 2005-10-09
What is the best way to add things to the blacklist file? i cant really navigate that well through a command prompt and i need to add two lines for Ubuntu to boot properly (sound card problems). I'v searched through the forums and even the absolute begginers seem to know how to edit there blacklist. Any help would be greatly appreciated.

---

### Post by mlomker on 2005-10-09
This from a terminal should open it for you:

```

gksudo gedit /etc/hotplug/blacklist

```

---

### Post by element3260 on 2005-10-09
but how do i access the terminal if i can't boot up?

---

### Post by mlomker on 2005-10-09
> but how do i access the terminal if i can't boot up?

Where in your post did you mention that?  Perhaps you could provide more details here...

---

### Post by element3260 on 2005-10-10
sorry i thought i mentioned that... any way the boot up hangs when it reaches "detecting hotplug" and i ran debug and it stops at my sound card drivers. so i need a way to add these two lines into the file. Once again any help is greatly appreciated

---

### Post by mlomker on 2005-10-10
>  Once again any help is greatly appreciated

Assuming that you've already installed the system to your hard disk then you'd probably have to boot up to a liveCD (I like [Knoppix]("http://www.knoppix.net/get.php")) in order to edit the file, since you can't boot to a prompt yet.

---

### Post by element3260 on 2005-10-10
yea thanks il try that. also, if i was to take the sound card out, and then reinstall ubuntu without it detecting it, would it be able to boot?

---

### Post by mlomker on 2005-10-10
> would it be able to boot?

I don't know if the sound card is your issue...that was your speculation.  My approach when dealing with problems like this is to unplug and pull out everything that isn't necessary for the machine to boot.  If it still doesn't work then I update the BIOS and tinker with the settings...if that doesn't work then I find the big hammer...  :cool:

---

### Post by benplaut on 2005-10-10
when it starts hanging, try Ctrl+C... it *should* cancel the process and continue booting

---

