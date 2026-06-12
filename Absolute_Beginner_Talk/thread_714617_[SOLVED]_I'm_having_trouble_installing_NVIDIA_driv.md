---
title: "[SOLVED] I'm having trouble installing NVIDIA drivers."
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by infernohit on 2008-03-04
I don't exactly know how to install it. I tried typing sudo sh NVIDIA-Linux-x86-169.12-pkg1.run in recovery mode but nothing happens. Am I doing it right? I tried doing it through terminal and it gives me this error:

ERROR: nvidia-installer must be run as root

---

### Post by kpkeerthi on 2008-03-04
See the instructions [here]("https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia")
I suggest you install using restricted drivers manager unless you have nvidia 8800 card

---

### Post by infernohit on 2008-03-04
I have an 8800GT 512MB.

---

### Post by kpkeerthi on 2008-03-04
Install [envy]("http://albertomilone.com/nvidia_scripts1.html"). No hassles. Just works.

---

### Post by infernohit on 2008-03-04
I'm new to Linux... I'm still getting the hang of it.

I downloaded EnvyNG but I have trouble installing it.

I saved the file to my desktop, then extracted it there.

Then I get a folder with the following files in them: control.tar.gz, data.tar.gz, and debian-binary. I tried going to Envy's FAQ but it's really confusing to me.

Whenever I try step 2 to installing it, it says file not found.

---

### Post by gtdaqua on 2008-03-04
see [this]("http://ubuntuforums.org/showthread.php?t=596875") post. This should simply work.

---

### Post by kpkeerthi on 2008-03-04
> **infernohit said:**
> I'm new to Linux... I'm still getting the hang of it.

I downloaded EnvyNG but I have trouble installing it.

I saved the file to my desktop, then extracted it there.

Then I get a folder with the following files in them: control.tar.gz, data.tar.gz, and debian-binary. I tried going to Envy's FAQ but it's really confusing to me.

Whenever I try step 2 to installing it, it says file not found.

Enable Universe and Multiverse repositories from System -> Admin -> Software Sources.

You don't have to extract it. Just double-click the deb file to launch the installer to install envy.

Open a terminal and type ```
sudo envy -t
```

---

### Post by sanddgroper on 2008-03-04
Hi
Why dont people just use synaptic to install the nvidia drivers
am I missing something.?

Cheers
Sandy

---

### Post by infernohit on 2008-03-04
> **kpkeerthi said:**
> Enable Universe and Multiverse repositories from System -> Admin -> Software Sources.

You don't have to extract it. Just double-click the deb file to launch the installer to install envy.

Open a terminal and type ```
sudo envy -t
```

When I double-click it I get this error: Dependency is not satisfiable: python central

When I type sudo envy -t in the terminal, it says command not found.

---

### Post by Gepetto on 2008-03-04
> **infernohit said:**
> I'm new to Linux... I'm still getting the hang of it.

I downloaded EnvyNG but I have trouble installing it.

I saved the file to my desktop, then extracted it there.

Then I get a folder with the following files in them: control.tar.gz, data.tar.gz, and debian-binary. I tried going to Envy's FAQ but it's really confusing to me.

Whenever I try step 2 to installing it, it says file not found.

EnvyNG is for 8.04. If you're running 7.10 or earlier, you should get Envy Legacy. When you download it, it should just be a .deb file which you should just be able to double click and run. After it's installed, run it from Applications/System Tools.

---

### Post by Tatty on 2008-03-04
I would not use Envy if you can help it.  I am not knocking the software, it is fantastic by all accounts, but there can be some issues with using it, particularly when it comes to upgrading your system.

I would reccomend installing the driver the "standard" way first, and use envy if that doesnt work.

1. What video card do you have?  
2.Have you tried checking the restricted drivers manager to see if you can install the drivers from there?

3.If you really want to use the drivers from the nvidia site try this:

```
sudo ./NVIDIA-Linux-x86-169.12-pkg1.run
```  - making sure of course that you have set the file to be an executable, have the correct file name, and you are in the correct directory.

---

### Post by infernohit on 2008-03-04
Thanks, I didn't know there was a newer version.

---

### Post by infernohit on 2008-03-04
I try running EnvyNG but it says EnvyNG does not recognize my card as compatible with any drivers.

---

### Post by infernohit on 2008-03-05
I installed the NVidia drivers manually through EnvyNG, and when I rebooted my comp, it started in low-graphics mode. What went wrong?

---

### Post by infernohit on 2008-03-05
Gah. When in low-graphics mode it told me to pick my graphics card and monitor. I picked a different model of the Acer than mine because mine wasn't listed there. So now in xorg.conf it lists the monitor that's not mine. How can I undo that?

---

### Post by sanddgroper on 2008-03-05
Hi
What nvidia card do you have maybe you need to use one of the other
drivers.

Cheers
Sandy

---

### Post by infernohit on 2008-03-05
> **sanddgroper said:**
> Hi
What nvidia card do you have maybe you need to use one of the other
drivers.

Cheers
Sandy

I have an 8800 GT 512MB.

---

### Post by sanddgroper on 2008-03-05
Hi
Ok maybe not but if your stuck maybe if you search the ubuntu forums for nvidia 8800 cards you
may find a solution I know there have been a lot of posts on these cards.
Have you tried installing the nvidia drivers using the synaptic packet manager.
I find it the best way but I have an old graphics card.

Cheers
Sandy

---

### Post by PmDematagoda on 2008-03-05
I think your problem is mainly with conflicting modules:-

1) Open a modules file for editing using:-
```
sudo gedit /etc/default/linux-restricted-modules-common
```

2) Edit the DISABLED_MODULES line to make it look like this:-
```
DISABLED_MODULES="nv nvidia_new"
```

3) Reconfigure your X-Server using:-
```
sudo dpkg-reconfigure xserver-xorg
```
and select the appropriate options. After that is done restart Ubuntu with:-
```
sudo restart
```

See if your problem is then solved.

---

### Post by infernohit on 2008-03-05
> **sanddgroper said:**
> Hi
Ok maybe not but if your stuck maybe if you search the ubuntu forums for nvidia 8800 cards you
may find a solution I know there have been a lot of posts on these cards.
Have you tried installing the nvidia drivers using the synaptic packet manager.
I find it the best way but I have an old graphics card.

Cheers
Sandy

Yeah, I couldn't find the drivers through that.

PmDematagoda: Thanks a lot. The settings are back to normal.

---

### Post by infernohit on 2008-03-06
I've looked at other topics and I haven't solved my problem yet.

EnvyNG doesn't install the drivers and I try everything in terminal and it just doesn't want to install them. :(

---

### Post by PmDematagoda on 2008-03-06
What errors does EnvyNG put up?

---

### Post by sanddgroper on 2008-03-06
Hi
To get the drivers through synaptic you need to go
System->synaptic->settings->repositories and select everything
under the Ubuntu Software heading.Then select reload on the main
synaptic page then look for nvidia packages.

Cheers
Sandy

---

### Post by infernohit on 2008-03-06
> **sanddgroper said:**
> Hi
To get the drivers through synaptic you need to go
System->synaptic->settings->repositories and select everything
under the Ubuntu Software heading.Then select reload on the main
synaptic page then look for nvidia packages.

Cheers
Sandy

Thanks. I think I got it now, but I'm not sure. Where can I check which drivers I have installed to be sure they're updated?

---

### Post by sanddgroper on 2008-03-06
Hi
In synaptic were you installed the drivers from.The square in front of the
drivers you installed will be green and if they need updating the square will
have a yellow star in it

Cheers
Sandy

---

