---
title: "help needed!!!"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by Robbey on 2007-12-16
ok I installed compiz, although when I run it I get this error-

robert@Roberts-Computer:~$ compiz --replace
Fatal: Compiz can't be ran using VESA or VGA divers.
robert@Roberts-Computer:~$ 




When I press Alt+F2 to run and press enter nothing happens

My graphics card is geforce 8500 gt

---

### Post by dpar on 2007-12-16
Did you install the restricted drivers for the video card?

---

### Post by Robbey on 2007-12-16
> **dpar said:**
> Did you install the restricted drivers for the video card?

I dont think so..Lol can you tell me how I do

---

### Post by Robbey on 2007-12-16
I dont think so..Lol can you tell me how I do

---

### Post by aysiu on 2007-12-16
> **Robbey said:**
> I dont think so..Lol can you tell me how I do
[http://www.psychocats.net/ubuntu/nvidia](http://www.psychocats.net/ubuntu/nvidia)

The instructions demonstrate Nvidia, but I think ATI is the same principle.

---

### Post by Robbey on 2007-12-16
When I go driver many it says 'your hardware doesnt need any restricted drivers" ??

---

### Post by Robbey on 2007-12-16
Little help??I really need done by tonite

---

### Post by jken146 on 2007-12-16
What is "driver many"?  Just go to the Restricted Frivers Manager and install the restricted driver for your card.

---

### Post by Robbey on 2007-12-16
When I go to restricted driver manager, It explains-
"Your hardware does not need any restricte drivers"

How can I change that

---

### Post by jken146 on 2007-12-16
Try to install the driver anyway.  ```
sudo aptitude install nvidia-glx-new nvidia-settings
sudo nvidia-xconfig
```

---

### Post by Robbey on 2007-12-16
I ran those to commands. I got tons of errors in terminal >>

---

### Post by jken146 on 2007-12-16
Could you post those errors please?

---

### Post by Robbey on 2007-12-16
First 1-
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be installed:
  nvidia-settings 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/762kB of archives. After unpacking 1823kB will be used.
Writing extended state information... Done
(Reading database ... 113517 files and directories currently installed.)
Unpacking nvidia-settings (from .../nvidia-settings_1.0+20060516-3ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/nvidia-settings_1.0+20060516-3ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/bin/nvidia-settings', which is also in package nvidia-glx-new
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-settings_1.0+20060516-3ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:




Second 1-
robert@Roberts-Computer:~$ sudo nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

robert@Roberts-Computer:~$

---

### Post by PmDematagoda on 2007-12-16
Nvidia-settings is included in the Nvidia-glx-new package as well, so do not install Nvidia-settings in addition to Nvidia-glx-new.

---

### Post by jken146 on 2007-12-17
Sorry about that!  Anyway, did that sort your problem out?

---

### Post by Robbey on 2007-12-17
Could you please go on or add my msn-
[email]lil_shifty_greek69@hotmail.com[/email]

I rahter instant chat

---

### Post by jken146 on 2007-12-17
Sorry, I don't have an msn account.  More people will be able to help you on the forums, and your solution will be available for other people to see in the future.

---

### Post by Robbey on 2007-12-17
> **jken146 said:**
> Sorry, I don't have an msn account.  More people will be able to help you on the forums, and your solution will be available for other people to see in the future.

Oh Ok so what do i need to do? do you know? thanks in advance

---

### Post by jken146 on 2007-12-17
Well, having installed the nvidia restricted driver, can you run compiz?

---

### Post by Robbey on 2007-12-17
> **jken146 said:**
> Well, having installed the nvidia restricted driver, can you run compiz?

No It didn't install the nvidia driver. I showed you the errors...little help?

---

### Post by Ripfox on 2007-12-17
No it just didn't install nvidia-settings b/c it was included in the first package.

---

### Post by jken146 on 2007-12-17
> **PmDematagoda said:**
> Nvidia-settings is included in the Nvidia-glx-new package as well, so do not install Nvidia-settings in addition to Nvidia-glx-new.

My initial advice was a bit wrong (sorry once again!), so try to install the driver again - this time the commands should be ```
sudo aptitude install nvidia-glx-new
sudo nvidia-xconfig
```

Then you have to reboot for the change to take effect.

---

### Post by jken146 on 2007-12-17
> **ripfox said:**
> No it just didn't install nvidia-settings b/c it was included in the first package.

Yeah.

---

### Post by aktiwers on 2007-12-17
Then start by installing them manually..  just follow these few steps.

Goto:
[http://www.nvidia.com/object/linux_display_ia32_100.14.19.html](http://www.nvidia.com/object/linux_display_ia32_100.14.19.html)
and download the [NVIDIA-Linux-x86-100.14.19-pkg1.run]("http://us.download.nvidia.com/XFree86/Linux-x86/100.14.19/NVIDIA-Linux-x86-100.14.19-pkg1.run") to your desktop.

When done right-click on the file and pick "properties" and go to the "permission" tab. There enable "allow executing  file as program"

Hit "ok".

Hit CTRL+ALT+F1
Log in
 type:
```
cd Desktop
``````
sudo /etc/init.d/gdm stop
```And then
```
sudo ./NVIDIA-Linux-x86-100.14.19-pkg1.run
```when done.. type:
```
sudo reboot
```

Now the newest driver should be installed.

---

### Post by jrusso2 on 2007-12-17
Maybe I missed it but I didn't see the OP saying what kind of video card he has?  Does he even have an Nvidia card?

How can he run restricted driver if he doesn't have an nvidia card?

---

### Post by Robbey on 2007-12-17
I have nvidia 8500 gt 512mb

---

### Post by Ripfox on 2007-12-17
> **Robbey said:**
>  geforce 8500 gt

there

---

### Post by Robbey on 2007-12-17
ok whats the command to run compiz
when i go 
'compiz --fushion'

In terminal I get this 
robert@Roberts-Computer:~$ compiz --fushion
There is already the metacity win manager running, you should use the --replace option to override it
robert@Roberts-Computer:~$


Oh and Btw Im pretty sure the Nvidia drivers are installed now. Before the Ubuntu login came I got a quick NVIDIA logo :)

---

### Post by jken146 on 2007-12-17
[quote=Robbey]ok whats the command to run compiz[/quote]
```
compiz --replace
```

What exactly do you want to do with compiz-fusion?  If it's the rotating cube and all that jazz then you'll need to install ccsm, like this: ```
sudo aptitude install compizconfig-settings-manager
```  Then you'll be able to set up all the pretty effects by going to Preferences > Advanced Desktop Settings.

---

### Post by dpar on 2007-12-17
The command is > compiz --replace

---

### Post by Robbey on 2007-12-17
uhhh I ran compiz replace. The application bar and stuff is all like smudged and ubuntu is lagging :o

Edit: Ok How do I actually use the stuff.
Im in CompizConfig Setting manager, what do i do?

EDIT:NVM WORKS THANK YOU SO MUCH GUYS I LOVE YOU MUCH APPRECIATED!!!!!!!!!!!!!!!!

---

### Post by jken146 on 2007-12-17
Can you post the output of that command please?

And could you tell us what your overall aim is, i.e. what you are trying to achieve in the end?

---

### Post by jken146 on 2007-12-17
OK, I saw your edit.  Just play with the plugins in ccsm.  Most of them are fairly self-explanatory.  Look around on these forums too, there's bound to be tons of advice on compiz.

---

### Post by Robbey on 2007-12-17
> **jken146 said:**
> Can you post the output of that command please?

And could you tell us what your overall aim is, i.e. what you are trying to achieve in the end?

It worked. Compiz is working fine TY so much for your help. Just 1 last thing, I downloaded a theme from gnome-look.org. I have 'ermerald theme manager' installed already so i imported it to there. Although when I double click to use the theme nothing happens Lol

---

### Post by jken146 on 2007-12-17
Sorry, I have no experience of emerald themes.  Try searching the forums and google, and good luck.

---

### Post by Robbey on 2007-12-17
> **jken146 said:**
> Sorry, I have no experience of emerald themes.  Try searching the forums and google, and good luck.

Do you know any other theme programs that you are familiar with?

---

