---
title: "I'm so close. Someone please help (Ubuntu on Wallstreet Powerbook)"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by ScooterDMan on 2007-02-18
I have been fighting to get Ubuntu up and running on this Old World Powerbook G3 Wallstreet I have inherited.

I have followed all the steps from the various guides on the Net, and now I am really close and need help.

I have arrived at a screen which starts loading all sorts of scripts or commands. Eventually it finishes and asks me for my login and password. I give it, and then it gives me this:
```

~$
```

From here, I have no idea what to do. I am dying to get this machine going.

Another tidbit that seems important: when the system is booting and running those scripts and commands, one message that pops out to me as possibly problematic is:

```
"filesystem type 'usbfs' is not supported"
```

Not sure what any of this means. It's all new to me.

---

### Post by taurus on 2007-02-18
See if you have a desktop version or a server version.  What happens if you enter this command at the prompt?

```
startx
```

---

### Post by ScooterDMan on 2007-02-18
it says, "Command not found."

Although, I distinctly remember choosing "Install Ubuntu Desktop" during the intallation.

I am using the Ubuntu 6.10 Alt PPC iso.

---

### Post by taurus on 2007-02-18
Is it connected to the net?  You now need to install Gnome desktop on it.

```
sudo aptitude update
sudo aptitude install ubuntu-desktop
sudo /etc/init.d/gdm start
```

---

### Post by ScooterDMan on 2007-02-18
things are happening! I'll let you know if this works... (Thanks for the help)

---

### Post by BarfBag on 2007-02-18
If all else fails, here are two suggestions.

Perhaps your CD burner skipped as it was burning the .ISO to the disk.  To check this, boot the CD and select the "Check Disk for Errors" option.  This isn't always accurate, so if you get desperate enough, try burning another CD.

The G3 is a PowerPC processor.  Make sure that you have the PPC version of Ubuntu.

---

### Post by ScooterDMan on 2007-02-19
So close!

When I get to this part

```
sudo /etc/init.d/gdm start
```

It says "command not found."

Now what? Everything seemed to be going so well...

---

### Post by ScooterDMan on 2007-02-19
anyone? i'm right there...

---

### Post by ScooterDMan on 2007-02-19
Going to bed — again defeated by this old laptop. If anyone can help, I'm still all ears.

---

### Post by pismo on 2007-02-19
Why dont you try Xubuntu lets face it the old Wallstreet is going to wonder what hit it trying to run 6.10 i ran 6.10 on a DP 450 1.5 gig of ram it craped me of so much i went and bought 3.6 mhz PC to run it I am not knocking Macs as I have 3 of them that i still use every day but in my humble opion i think the Pc runs general version of  linux better

---

### Post by ScooterDMan on 2007-02-19
> **pismo said:**
> Why dont you try Xubuntu lets face it the old Wallstreet is going to wonder what hit it trying to run 6.10 i ran 6.10 on a DP 450 1.5 gig of ram it craped me of so much i went and bought 3.6 mhz PC to run it I am not knocking Macs as I have 3 of them that i still use every day but in my humble opion i think the Pc runs general version of  linux better

That's fine. I have the Xubuntu CD. Does this mean I have completely redo the install, though? Or is there anyway I can modify what I've done already?

---

### Post by Brendantb on 2007-02-19
Hi, 

You will have to start again, I'm afraid. There is a way to remove a Gnome Desktop, and replace it with an Xfce one, but it almost as much bother as reinstalling, and I don't know if you are far enough advanced in your first install anyway. 

How much ram do you have in your powerbook?

---

### Post by ScooterDMan on 2007-02-19
I have 128 MB of RAM. I am going to start over, so any guidance you could offer would be great.

---

### Post by taurus on 2007-02-19
Before you decide to start over, maybe try this first.

[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

---

### Post by ScooterDMan on 2007-02-19
Well, I already reformatted so I can start over. I am just not sure what to do at this point. I have tried Ubuntu 5.10, 6.10 and Xubuntu 6.10.

I just want to run Firefox. There's gotta be an easier way...

---

### Post by Brendantb on 2007-02-19
The installation should be more straightforward with Xubuntu, and 128 mb ram. 

I see from the specs for you machine that you can increase the ram to 512, with the right dimms, though these might well be expensive now. 

The biggest problem will probably be the video ram, at 4mb, but people have had OSX running on these old laptops, so its definitely worth a try.

---

### Post by ScooterDMan on 2007-02-19
Do you think I can follow [these same instructions ]("http://gonz.wordpress.com/2006/03/22/installing-ubuntu-510-breezy-badger-on-an-old-world-powerbook-g3-wallstreet/")for installing Xubuntu?

---

### Post by Brendantb on 2007-02-19
Hi, 

That is quite a road you have walked! I am glad I didn't buy an old mac to try linux on, after all. 

In one of the links to that article I saw this point: 

"Reboot your system and Xubuntu should start; older versions of Ubuntu may require you to login at the text prompt and start Xubuntu with startxfce4 or xserver. If you are using Xubuntu on a fully installed system, Xubuntu or XFCE will be an session option on login."

This might be your problem...

---

