---
title: "Asus G73S Screen Resolution Limited to  800x600"
date: 2011-09-04
forum: Asus Ubuntu Support (CLOSED)
---

### Post by dano2 on 2011-09-04
I just installed Ubuntu 10.04.3 after 11.04 kept freezing up on me. Now the screen resolution only allows for 800x600 or 640x480. I have a Nvidia geoforce graphics card. 

I have windows 7 installed as well which displays at 1980x1080 with no problem. 

"glxijnfo | grep -i render" returns
Yes
Software Rasterizer

After running "updatedb" xorg.conf is still nowhere to be found on my system. 

Tried "nvidia-xconfig" and it doesn't exist.

I'm at a loss. Is this ubuntu version not compatible with my system? Should I only be trying to run a 64 bit OS? I've followed other solutions found at this forum like this one ([http://ubuntuforums.org/showthread.php?t=1829771](http://ubuntuforums.org/showthread.php?t=1829771) ) but nothing has changed anything.
Any suggestions?

---

### Post by realzippy on 2011-09-04
Welcome to UF !

Did you install the nvidia graphics driver offered in
System=>Administration=>AdditionalDrivers?

---

### Post by dano2 on 2011-09-04
> **realzippy said:**
> Welcome to UF !

Did you install the nvidia graphics driver offered in
System=>Administration=>AdditionalDrivers?

The closest I could find is System=>Administration=>Hardware Drivers
which just returns "No proprietary drivers are in use on this system"

nvidia-current-modaliases is installed but I still don't see any drivers.


[PHP]uname -a
Linux mylap 2.6.32-33-generic #72-Ubuntu SMP Fri Jul 29 21:08:37 UTC 2011 i686 GNU/Linux
[/PHP]

---

### Post by Vakman on 2011-09-04
Please post the output of:
```
fglrxinfo
```

Disregard this, for AMD/ATi only. Clearly, I can't remember things.

---

### Post by dano2 on 2011-09-04
> **Thisislaw said:**
> Please post the output of:
```
fglrxinfo
```

I didn't have that. So, after a little research I ran
sudo apt-get install xorg-driver-fglrx

and then "fglrxinfo" just returned
Segmentation fault

Could the way I installed over a reformatted partition be contributing to the problem? Everything else seems fine except the resolution.

---

### Post by Vakman on 2011-09-05
> **dano2 said:**
> I didn't have that. So, after a little research I ran
sudo apt-get install xorg-driver-fglrx

and then "fglrxinfo" just returned
Segmentation fault

Could the way I installed over a reformatted partition be contributing to the problem? Everything else seems fine except the resolution.

You didn't have it because the drivers are not installed or not install correctly.
To your second question, no.

Let's get these drivers installed.
If you are running the x86 version of Ubuntu, download the drivers here: [http://www.nvidia.com/object/linux-display-ia32-280.13-driver.html](http://www.nvidia.com/object/linux-display-ia32-280.13-driver.html)
If you are running the x64 version of Ubuntu, download the drivers here:
[http://www.nvidia.com/object/linux-display-amd64-280.13-driver.html](http://www.nvidia.com/object/linux-display-amd64-280.13-driver.html)
If you do not know which version you are running, open terminal and enter:
```
uname -m
``` and then show me the output.

Now, to install the drivers.
There is an excellent tutorial here: [http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html)
Follow it to a tee, let me know when you have that finished or if you need any help with it. Also, let me know if it worked.

---

### Post by realzippy on 2011-09-05
```
fglrxinfo
```

..is for ATI cards only...
......................................................
I would suggest to check which graphics card OP runs,before
installing nvidia-drivers manually,since there might be a reason
why jockey (Additional drivers GUI ) doesn't offer those..

run

```
lspci |grep VGA
```

...if you are running the free nvidia driver due to a very old nvidia graphics card,the resolution
(normally) could be changed by xrandr..

---

### Post by dano2 on 2011-09-05
> **Thisislaw said:**
> You didn't have it because the drivers are not installed or not install correctly.
To your second question, no.

Let's get these drivers installed.
If you are running the x86 version of Ubuntu, download the drivers here: [http://www.nvidia.com/object/linux-display-ia32-280.13-driver.html](http://www.nvidia.com/object/linux-display-ia32-280.13-driver.html)
If you are running the x64 version of Ubuntu, download the drivers here:
[http://www.nvidia.com/object/linux-display-amd64-280.13-driver.html](http://www.nvidia.com/object/linux-display-amd64-280.13-driver.html)
If you do not know which version you are running, open terminal and enter:
```
uname -m
``` and then show me the output.

Now, to install the drivers.
There is an excellent tutorial here: [http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html)
Follow it to a tee, let me know when you have that finished or if you need any help with it. Also, let me know if it worked.

Okay, I didn't get an error message popup to reach the terminal. But I did control+alt+F1 . I'm getting an error message that I need to turn off X server?? As I understand, to do this I need to run " /sbin/init 3" but my root account is disabled. sudo doesn't seem to make a difference as I keep getting the "x server" error.


Realzippy:
lspci |grep VGA
01:00.0 VGA compatible controller: nVidia Corporation Device 0dd1 (rev a1)

---

### Post by Vakman on 2011-09-05
> **realzippy said:**
> ```
fglrxinfo
```

..is for ATI cards only...
......................................................
I would suggest to check which graphics card OP runs,before
installing nvidia-drivers manually,since there might be a reason
why jockey (Additional drivers GUI ) doesn't offer those..

run

```
lspci |grep VGA
```

...if you are running the free nvidia driver due to a very old nvidia graphics card,the resolution
(normally) could be changed by xrandr..

Haha, of course. I forgot. Ah well, no harm done. Clearly I am tired and have been dealing with AMD/ATi cards for to long.
We know what card he runs, ASUS G73S runs the GTX 460m, no?
I wouldn't consider this an older graphics card at all. Higher end gaming laptop, in my opinion anyhow.

---

### Post by Vakman on 2011-09-05
> **dano2 said:**
> Okay, I didn't get an error message popup to reach the terminal. But I did control+alt+F1 . I'm getting an error message that I need to turn off X server?? As I understand, to do this I need to run " /sbin/init 3" but my root account is disabled. sudo doesn't seem to make a difference as I keep getting the "x server" error.


Realzippy:
lspci |grep VGA
01:00.0 VGA compatible controller: nVidia Corporation Device 0dd1 (rev a1)

When you are installing it, it will want you to turn off the XServer. To do this, run: ```
sudo /etc/init.d/gdm stop
``` Before you install the drivers. So after that, continue running as you were with:
```
sudo sh NVIDIA-Linux-x86_64-195.36.24-pkg2.run
```

---

### Post by realzippy on 2011-09-05
So you have a nVidia 460M...
Suggest to add the xswat repo to get the 280.13 nvidia driver to your sources,so a driver might appear in "Hardware Drivers",maybe the default nvidia driver in Lucid's jockey is too old for your card.
Run:

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
```

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

..then again have a look in Hardare Drivers.
If now  a driver has appeared,install it.

---

### Post by realzippy on 2011-09-05
@Thisislaw

...would suggest to wait with downloading driver from nvidia,it should be last choice due to disadvantages (kernel updates).
Don't get me wrong,I am not saying that your resolution does not work...but in newer Ubuntu versions jockey offers driver for 460M,so
maybe xswat will fix that.

---

### Post by Vakman on 2011-09-05
> **realzippy said:**
> So you have a nVidia 460M...
Suggest to add the xswat repo to get the 280.13 nvidia driver to your sources,so a driver might appear in "Hardware Drivers",maybe the default nvidia driver in Lucid's jockey is too old for your card.
Run:

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
```

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

..then again have a look in Hardare Drivers.
If now  a driver has appeared,install it.

This is certainly easier than installing them manually, I never thought of this. You should do this if you have not already finished.

---

### Post by Vakman on 2011-09-05
> **realzippy said:**
> @Thisislaw

...would suggest to wait with downloading driver from nvidia,it should be last choice due to disadvantages (kernel updates).
Don't get me wrong,I am not saying that your resolution does not work...

Mmhmm, makes sense. I agree.
OP, you already have it downloaded, so unless you are already finished, add the repository and continue with his steps.

---

### Post by dano2 on 2011-09-05
> **Thisislaw said:**
> When you are installing it, it will want you to turn off the XServer. To do this, run: ```
sudo /etc/init.d/gdm stop
``` Before you install the drivers. So after that, continue running as you were with:
```
sudo sh NVIDIA-Linux-x86_64-195.36.24-pkg2.run
```

Well this seemed to fix the resolution issue. Are you guys suggesting I should still backtrack and follow realzippy's steps or just leave well enough alone at this point? The Hardware Drivers list is still empty.

Also, should I now restart x server, which I assume is
sudo /etc/init.d/gdm restart

Currently showing:
[PHP]
glxinfo | grep -i render
direct rendering: Yes
OpenGL renderer string: GeForce GTX 460M/PCI/SSE2
    GL_NV_conditional_render, GL_NV_copy_depth_to_color, GL_NV_copy_image, 
    GL_NV_parameter_buffer_object2, GL_NV_path_rendering, 
    GL_NVX_conditional_render, GL_NVX_gpu_memory_info, GL_OES_depth24, 
    GL_OES_fbo_render_mipmap, GL_OES_get_program_binary, GL_OES_mapbuffer, 
[/PHP]Please let me know and I'll mark this as "Solved". Thanks a lot for the help.

---

### Post by realzippy on 2011-09-05
Restart Xserver?

Confused,since you already have done this when resolution issue got fixed,
or how did you notice that it got fixed?

Adding xswat:

It won't hurt if you would.If a driver would appear then in hardware drivers GUI,you could reinstall it.
The disadvantage of your manual install is that you have to repeat it
every time there is a kernel update.

Btw,which nvidia driver version did you install ?

---

### Post by dummy910 on 2011-09-05
> **dano2 said:**
> I just installed Ubuntu 10.04.3 after 11.04 kept freezing up on me. Now the screen resolution only allows for 800x600 or 640x480. I have a Nvidia geoforce graphics card. 

.......... After running &quot;updatedb&quot; xorg.conf is still nowhere to be found on my system. 

........

I have the same laptop(AsusG73), difference being an ATI 5850 VideoCard installed with max resolution of 1600x900, and the default 11.04 install created NO xorg,conf(been this way in Ubuntu going back to 9.10 or 10.04 I believe) as the system will not need it. 

I now have an xorg.conf file now after the Restricted-Drivers(jockey-gtk) detected and installed the proper drivers it saw fit for my card.

The following entries are my entire xorg.conf file on my AsusG73 >  

Section &quot;Screen&quot; 

Identifier &quot;Default Screen&quot;

DefaultDepth 24

EndSection

Section &quot;Module&quot;

Load &quot;glx&quot;

EndSectionNotice, no other settings for resolution, keyboard, mice etc... and this laptop boots into its max resolution every time.

---

### Post by dano2 on 2011-09-05
> **realzippy said:**
> Restart Xserver?

Confused,since you already have done this when resolution issue got fixed,
or how did you notice that it got fixed?

Adding xswat:

It won't hurt if you would.If a driver would appear then in hardware drivers GUI,you could reinstall it.
The disadvantage of your manual install is that you have to repeat it
every time there is a kernel update.

Btw,which nvidia driver version did you install ?


[http://www.nvidia.com/object/linux-display-ia32-280.13-driver.html](http://www.nvidia.com/object/linux-display-ia32-280.13-driver.html)

---

### Post by realzippy on 2011-09-06
Same as in xswat...

---

### Post by dano2 on 2011-09-06
Thanks everyone for their assistance. The screen resolution issue is resolved for now. Unfortunately, my original problem with ubuntu 11.04 completely freezing up at random times is happening in this 10.04 version as well.

I don't see where I can mark this resolution issue as officially resolved.

---

### Post by Vakman on 2011-09-06
Under thread tools, scroll to the top and you will see "Thread Tools" near the right of the page.
Also, yes, each time there is a kernel update, you would need to manually repeat my process.
With the process given by realzippy, it would be much easier.

Ubuntu randomly freezing?

---

### Post by dano2 on 2011-09-06
> **Thisislaw said:**
> This is certainly easier than installing them manually, I never thought of this. You should do this if you have not already finished.

I was going to leave well enough alone, but since my system is still randomly freezing on me ([http://ubuntuforums.org/showthread.php?t=1839665](http://ubuntuforums.org/showthread.php?t=1839665)), I want to go ahead and try this realzippy's way. I ran the xswat, update, upgrade commands successfully, but still nothing shows up in Hardware Drivers. Do I need to uninstall the driver I manually installed first? I don't see any uninstall instructions. 

realzippy, I've never restarted Xserver. I just stopped it, manually installed the driver, then rebooted and the resolution was fixed. I'm not sure whether I should be dwelling on Xserver, since I'm not real clear on its function.

---

### Post by realzippy on 2011-09-06
> **dano2 said:**
> ...but still nothing shows up in Hardware Drivers.
...this is really strange.Please open Synaptic Package Manager.
On the left click on "*sections*",scroll down to
*Miscellaneous -Text based (restricted)*,click it.Is there no
*nvidia-current* offered on the right side?
If,I wonder why jockey doesn't know.
If not,hit *Settings => Repositories*,and mark the checkbox for
*Proprietary drivers for devices* and (generally useful)
*Software restricted blah...*
Then hit apply in the main window.Now there has to be a driver...
> **dano2 said:**
> 
Do I need to uninstall the driver I manually installed first? I don't see any uninstall instructions. 
No,this has nothing to do with jockey (HardwaredriversGUI).
If jockey at last would offer a driver,then
yes,you had to uninstall manually installed driver first,same procedure as installing,just type
--uninstall at the end when starting .run file:
```
sudo NVIDIA-linux-280.whatever.run --uninstall
```
> **dano2 said:**
> 
...never restarted Xserver. I just stopped it.... then rebooted  
Stopping Xserver+reboot also is a X restart  ;-)

---

### Post by dano2 on 2011-09-07
I followed all the instructions and still do not see anything in the hardware drivers list (screenshot).
[http://www.freeimagehosting.net/0713e](http://www.freeimagehosting.net/0713e)


As you can see, nvidia-current is in the right panel. The settings boxes were already checked. I don't see an "apply" button in any window.

---

### Post by Vakman on 2011-09-07
> **realzippy said:**
> ...this is really strange.Please open Synaptic Package Manager.
I wonder why jockey doesn't know.
If not,hit *Settings => Repositories*,and mark the checkbox for
*Proprietary drivers for devices* and (generally useful)
*Software restricted blah...*
Then hit apply in the main window.Now there has to be a driver...


In my experience, Hardware Drivers/Jockey often doesn't have the drivers for newer cards. However, his card is not overly new and it should know and I have never thought to add that repo like you said.
On the plus side, at least the manual way will fix his issue but like you said, he'll have to do that again next kernel update. Not sure if he is fine with that.
Though I am sure you'll figure this out if there is a way.

---

### Post by realzippy on 2011-09-07
> **dano2 said:**
> I followed all the instructions and still do not see anything in the hardware drivers list (screenshot).
[http://www.freeimagehosting.net/0713e](http://www.freeimagehosting.net/0713e)
I give up.
Last desperate shot would be to reinstall jockey:

```
sudo apt-get install --reinstall jockey-gtk
```

If jockey still is empty,then you could install nvidia-current
in synaptic.Right click it,mark for install.Then you will see
the "apply" button in the top bar,which you had to hit.
(it is greyed out unless you mark something to install).
Remember to uninstall the manually installed nvidia-driver as described a few posts earlier  (--uninstall option) 
and to reboot before installing via synaptic.

---

### Post by dano2 on 2011-09-08
> **realzippy said:**
> I give up.
Last desperate shot would be to reinstall jockey:

```
sudo apt-get install --reinstall jockey-gtk
```

If jockey still is empty,then you could install nvidia-current
in synaptic.Right click it,mark for install.Then you will see
the "apply" button in the top bar,which you had to hit.
(it is greyed out unless you mark something to install).
Remember to uninstall the manually installed nvidia-driver as described a few posts earlier  (--uninstall option) 
and to reboot before installing via synaptic.

Marking as Solved either way for now. Thanks again for everyone's time.

---

### Post by Vakman on 2011-09-09
> **dano2 said:**
> Marking as Solved either way for now. Thanks again for everyone's time.

Not a problem.

---

