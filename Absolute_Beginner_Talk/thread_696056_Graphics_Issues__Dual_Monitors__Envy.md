---
title: "Graphics Issues | Dual Monitors | Envy"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by reeksy on 2008-02-13
Hi

Porting to Linux has been brilliant! Everything’s gone smoothly and I have a complete development environment with CVS. Problem is; I went one step too far!

I've always used dual monitors with Windows. Since moving to Linux I haven’t bothered with my secondary monitor as I knew Linux dual monitor support wasn’t as idiot proof as Windows dual monitor support; so I left it alone!

I decided this evening to get my two LCD widescreens working together with Linux. I followed [this]("http://www.lockergnome.com/linux/2007/06/18/dual-monitors-with-ubuntu/") tutorial using [Envy]("http://www.albertomilone.com/nvidia_scripts1.html"). After successfully installing Envy and rebooting, I then fired-up Envy and ran through the wizard. After the wizard completed I was prompted to reboot; which I did. This is when things went wrong. Now, when I boot up, the screen displays a funny pixilated gradient with the occasional flickering. I can’t even see any text! The system is working correctly in the background as I can still login (albeit blindly). But as I get the constant funny pixilated gradient; I can’t see what I’m doing!

My first action was to boot in safe mode and run:

```

sudo dpkg-reconfigure xserver-xorg

```

I then went through the motions of reconfiguring the xserver via DOS like prompts, but to no avail! I’m still in the same situation!

I’ve no idea where to go from here!

Can anyone suggest any ideas?

Kind regards
Jon

---

### Post by PinkFloyd102489 on 2008-02-13
You never said what type of graphics card you have.


If you have an Nvidia, get nvida-settings from the repos.
```

sudo apt-get install nvidia-settings

```

Now configure your monitors with this. Remember, it's only for Nvidia cards.

---

### Post by reeksy on 2008-02-14
Sorry!

Yes it's NVIDIA. I have an NVIDIA GeForce 7600 GS.

I've managed to restore the Ubuntu build by booting up in recovery mode and:

```

envy --uninstall-all

```

However, now I'm back to my original state; I'd still like to get my dual monitors working! I've run the following:

```

sudo apt-get install nvidia-setting

```

.. but how do i access the Nvidia-settings app? Is there a tutorial on this?

Regards.

---

### Post by warrior24 on 2008-02-14
I believe its under system tools

---

### Post by reeksy on 2008-02-14
I can't see it. And

```

# whereis nvidia-settings

```

doesn't return anything!

---

### Post by warrior24 on 2008-02-14
try looking in synaptic to see if there is another part to it.

---

