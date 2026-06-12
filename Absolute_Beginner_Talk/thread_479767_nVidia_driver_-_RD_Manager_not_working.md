---
title: "nVidia driver - RD Manager not working"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by doubleplus on 2007-06-20
I'm a rank beginner with Linux.  I was in the market for a laptop (my first) and I'd been meaning to give Linux a whirl, so I got one of the Ubuntu Inspiron E1505s.  I've been grinding through online tutorials and podcasts and such for a month or so now, but I can't figure out how to do something, that something being:

The laptop comes with a 256MB NVIDIA GeForce Go 7300 card.  I get the laptop and open up Restricted Drivers Manager and it tells me "NVIDIA accelerated graphic driver.... Not in use"  I check the box.  A pop-up gives me the option to Cancel, or Enable Driver.  I click to Enable Driver.  I'm returned to the RD Manager which still has an unchecked box and "Not in use."

I thought maybe the system couldn't see the card.  I looked under System > Hardware Information and didn't see anything.  Then I Googled all of this and landed here: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)  So I typed "lspci | grep -i nvidia" into the terminal and got

01:00.0 VGA compatible controller: nVidia Corporation Quadro NVS 110M / GeForce Go 7300 (rev a1)

So I guess the card is there, but the RD Manager won't enable the driver.  Is there some fancy command line kung fu I should be doing?

Sorry for the length; I didn't want to leave anything out.  Thanks in advance!

---

### Post by Happy_Man on 2007-06-20
You could forcefully make the computer install it... which may, in retrospect, be easier. This, of course, depends on your being connected to the internet. For that matter, so does the GUI method, because it's downloading the driver. From the terminal (applications --> Accessories --> Terminal), type:
```
sudo apt-get install nvidia-glx-new
```

Enter your password, don't mind that nothing shows up, and press enter. You should be good.

---

### Post by doubleplus on 2007-06-20
> **Happy_Man said:**
> You could forcefully make the computer install it... which may, in retrospect, be easier. This, of course, depends on your being connected to the internet. For that matter, so does the GUI method, because it's downloading the driver. From the terminal (applications --> Accessories --> Terminal), type:
```
sudo apt-get install nvidia-glx-new
```

Enter your password, don't mind that nothing shows up, and press enter. You should be good.

Thank you for the advice.  I did what you suggested, and the driver downloaded, and I went to RDM and enabled it.  I was told I would need to restart my system to have the changes take effect, and then.................

I got an error screen saying something about my X Windows and my devices not being configured properly.  The detail screen mentioned a var.log.Xorg.0.log file, then dumped me into terminal mode.  I located that log file and at the bottom it said, essentially: "Failed to initialize the NVIDIA kernel module! Ensure there is a supported NVIDIA GPU, and that the NVIDIA device files have been created properly."  And it told me to read a README that I couldn't locate.

As of now, I'm stuck in Terminal, I don't know how to get back to GUI, and I'm not quite sure what "device files" I should be creating or editing.  Welcome to Linux! :)

Any help would be appreciated.  Thanks,

dp

---

### Post by Happy_Man on 2007-06-20
Um-humm..... perhaps I specified the wrong type of driver. You see, there are three; nvidia-glx-old, nvidia-glx, and nvidia-glx-new. I gave you the new one, because your card sounded new. At least, I hope it is. Anyway, when you get to your terminal, try this command ```
sudo dpkg-reconfigure xserver-xorg
``` That will give you.... stuff. Keep hitting the defaults until you get to a screen with a list of drivers. Scroll to choose "vesa", spacebar to select, keep going until you finish and it dumps you back to a prompt. Then type ```
/etc/init.d/gdm start
``` Hopefully, a login screen will appear. Then we can work some more.

---

