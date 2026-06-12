---
title: "Live CD won't boot."
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by tll_2k on 2007-05-29
I just installed ubuntu on my new Gateway desktop, and on my wife's HP laptop. I really wanted to use my old computer for it, since windows had a really bad spyware or something, making it impossible to use while connected to the internet. So, I tried to restore defaults, destroying everything on the drive and reinstalling windows, but it didn't install all the way or something. So, I now want to make that machine a Linux only box.

My old computer has a Pentuim 4, so I should also use the x86 disk, right? It has 512 ram, so that shouldn't be a problem. I has onboard video and an nVidea GeForce 5500 or something. Could that be the problem? I tried the Live CD, and it let me choose between booting ubuntu, memory test, and all of that, but when I choose boot ubuntu, it shows some lines of numbers on the bottom of the screen and doesn't do anything. Should I use the alternative CD or is there a way to make the live CD work?

Thanks in advance!
Tyler

---

### Post by Kobalt on 2007-05-29
Your computer has everything to run Ubuntu just fine. The LiveCD sometimes needs boot options in order to work. You can try this way : at the LiveCD boot screen press F6 and add at the end of the line, after a space, the following : > noapic nolapic
Then press Enter to boot.

If it still doesn't work then you should try the Alternate CD. If you need help on how to install Ubuntu with the Alternate CD see [this]("http://users.bigpond.net.au/hermanzone/").

---

### Post by floke on 2007-05-29
You should also check the disc (menu option) to make sure that it burned correctly.
Sometimes you get a bad burn that can screw things up.

---

### Post by ashijit007 on 2007-05-29
By 'trying out the Live cd', if you mean to 

Just try out Ubuntu without actually installing it:
When your computer detects a CD in the CD drive, it may display a message while it's starting up, like "Press ENTER to boot from the CD" -- in which case, do what it says. You should see some text scrolling up the screen, followed by the "Ubuntu" logo instead of the usual Windows logo, and after about 5 minutes, you should see the Ubuntu desktop. Did you wait for sufficient time? Since you are using the operating system from the cd, it will be visibly slower and only very basic tasks can be performed.

If you want to install Ubuntu onto the hard drive, once the Live CD has booted into gnome, just click the install icon on the desktop. The basic difference between the alternate and the live cd is that the latter gives the option of trying out Ubuntu without actually installing it onto the hard drive. Also check your cd for errors (one of the options). It may not have been burnt properly.

Hope that helps!:)

---

### Post by tll_2k on 2007-05-30
> **Kobalt said:**
> Your computer has everything to run Ubuntu just fine. The LiveCD sometimes needs boot options in order to work. You can try this way : at the LiveCD boot screen press F6 and add at the end of the line, after a space, the following : 
Then press Enter to boot.


O.k. I Tried this and My screen has a blinking cursor in the top left corner and this on the bottom of the screen:

```
Int 14: CR2 df800000  err 00000000  EIP c020c384  CS 00000060  flags 00010007
Stack: c00f8050 c03f129b c0371d8c 00000002 c00f8059 000f8050 00000000 00000000
```

So just try the alternative CD? Or is there something else I can try? I know the CD is good, because I installed ubuntu from it onto my wife's laptop a day or two ago.

Also, sorry for the delay, I had to go to work and I couldn't log in there...

---

