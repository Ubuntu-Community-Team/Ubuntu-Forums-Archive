---
title: "[SOLVED] NVIDIA accelerated graphics driver (help please)"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by jeramiahx on 2007-08-30
[SIZE="3"]
I tried to run desktop effects and I get this: [/SIZE]

[IMG]http://i18.photobucket.com/albums/b134/richardwild/Screenshot-restricted-manager.png[/IMG]

I enabled the driver and when I restart my computer it goes through the splash load up screen and then goes blank and I can't do anything.....

I am running off of the cd right now..... What can I do to get things back to normal?


Video card nvidia 6800xt

---

### Post by splintercellguy on 2007-08-30
You could try downloading Envy to your Ubuntu partition and running it from Recovery Mode: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Hobo Joe on 2007-08-30
Well, first you should install. :)

That alone could fix your entire problem!

---

### Post by splintercellguy on 2007-08-30
I think he did, but he's running from CD for recovery purposes.

---

### Post by w4ett on 2007-08-30
From the command line type:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will give you the interface to modify the driver and resolutions. Controls are UP and DOWN cursor keys move the cursor and scrolls through available options, the space selects options, and <enter> confirms selections.

Select "nv" as the driver and press <enter>, then at the next screen you can enable any addttional resolutions that you want to use.....then use the cursor keys to highlight {OK} and <spacebar> to select the resolutions and press <enter> to save the selections as prompted, then type:

```
startx
```

This will get you to a GUI desktop. then go to:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Install envy and then from the terminal type:

```
sudo envy -t
```

This will run the installation script from the terminal....follow the instructions to remove the old attempted driver installation and then install the correct Nvidia proprietary driver.

Good Luck

---

### Post by splintercellguy on 2007-08-30
I suppose the OP could just download it in the LiveCD session to his Ubuntu partition and run it from command-line in Recovery Mode.

---

### Post by jeramiahx on 2007-08-30
w4ett........... I did what you did and my whole computer went haywire. I changed my video card to my old one and everything you told me to do worked. I guess I have a messed up video card.......... Thanks for the help!!!!!!!!!

---

