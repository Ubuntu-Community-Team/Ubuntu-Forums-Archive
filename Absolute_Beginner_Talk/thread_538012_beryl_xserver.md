---
title: "beryl xserver"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by scorn_ik on 2007-08-29
I have just installed beryl.But after rebooting an error message shows me telling that

the xserver is not correctly configured so it is currently disabled.

Now how can i fix this?

My graphics card is built-in(128MB Intel 945 series )--> is that a problem?  

Please help me cause i am that good to continue my work in shell enviroment....

some more info about my graphics card-->

Section "Device"
	Identifier	"Intel Corporation 945G Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"

---

### Post by por100pre1 on 2007-08-29
Try reconfiguring xserver-xorg:

```
sudo dpkg-reconfigure xserver-xorg
```

and follow the instructions. When the screen goes balck again:

```
startx
```

---

### Post by scorn_ik on 2007-08-29
Thanks por100pre1 for your quick reply. But my problem haven't solved yet.

When i enter the command "dpkg-reconfigure xserver-xorg"  the following error message is shown: 

[I][B]Warning: Setting locale failed .Please check that your local setting.
Language = "en",
Lc-All=(unset),
LANG = "en-US.UTF-8" 
are supported and installed on your system.

beryl:warning: Falling back to the standard locale("C").
locale: Cannot set LC_ALL to the default locale: No such file or directory.
usr/sbin/dpkg-reconfigure: xserver-xorg is broken or not fully installed.
[/B][/I]

please help...:(

---

### Post by DM was on fire! on 2007-08-29
I unfortunately don't think there's anything you can do. :(
I've never had any luck reconfiguring Xserver, but...generally when it crashes, reconfigure works. D: The only thing I can say is, unfortunately, reinstall. :(

---

### Post by por100pre1 on 2007-08-29
Let's check your locale:

```
cd /usr/lib/locale
```

```
ls
```

and post the results...

---

### Post by por100pre1 on 2007-08-29
No answers, well, do [this]("https://help.ubuntu.com/community/LocaleConf"). Be sure to use **en_US.utf-8**. When finished. try reconfiguring xserver-xorg again.

---

### Post by scorn_ik on 2007-08-29
well it will take a liitle bit time for me to reply cause i have boot into linux and run the commands and handwritten it down and reboot to wnxp and post the result here!!!!!!

---

### Post by por100pre1 on 2007-08-29
> **scorn_ik said:**
> well it will take a liitle bit time for me to reply cause i have boot into linux and run the commands and handwritten it down and reboot to wnxp and post the result here!!!!!!

Ok, forget about posting the results, just read my previous post...

---

### Post by scorn_ik on 2007-08-29
[SIZE="3"]por100pre1,
i have gone to your given link, but didn't understand what to do exactly, as i am a noob after all.

Here is list of of things i did:

1. apt-get update   ------> it shows the following error:

GPG:Error:http:// debia.beryl-project.org etch Release : Public key is not available

2. apt-get install locales -----> As my main problem is to configuring the locales(may be).But it shows some errors and told me to correct this kind problem by --->" apt-get -f install". But when i run that command, it 
tries to dl some xserver.video...utils.. something something and it finished downloading it again shows the following error:

[I]"Warning: Setting locale failed .Please check that your local setting.
Language = "en",
Lc-All=(unset),
LANG = "en-US.UTF-8"
are supported and installed on your system."[/I]:(

and some dependency error like:

xserver-xorg: depends on xserver-xorg-video-all but it is not be installed :confused:

So this what summerizes my prob...now what can i do?
[/SIZE]

---

### Post by Crafty Kisses on 2007-08-29
> **scorn_ik said:**
> I have just installed beryl.But after rebooting an error message shows me telling that

the xserver is not correctly configured so it is currently disabled.

Now how can i fix this?

My graphics card is built-in(128MB Intel 945 series )--> is that a problem?  

Please help me cause i am that good to continue my work in shell enviroment....

some more info about my graphics card-->

Section "Device"
	Identifier	"Intel Corporation 945G Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"

Try reconfiguring your X server.

---

### Post by mysticmatrix on 2007-08-29
> **scorn_ik said:**
> [SIZE="2"]por100pre1,
i have gone to your given link, but didn't understand what to do exactly, as i am a noob after all.

Here is list of of things i did:

1. apt-get update   ------> it shows the following error:

GPG:Error:[COLOR="Red"]http:// debia.beryl-project.org etch[/COLOR] Release : Public key is not available

2. apt-get install locales -----> As my main problem is to configuring the locales(may be).But it shows some errors and told me to correct this kind problem by --->" apt-get -f install". But when i run that command, it 
tries to dl some xserver.video...utils.. something something and it finished downloading it again shows the following error:

[I]"Warning: Setting locale failed .Please check that your local setting.
Language = "en",
Lc-All=(unset),
LANG = "en-US.UTF-8"
are supported and installed on your system."[/I]:(

and some dependency error like:

xserver-xorg: depends on xserver-xorg-video-all but it is not be installed :confused:

So this what summerizes my prob...now what can i do?
[/SIZE]


You used a debian etch repository to install BERYL !!!!!

Why did you do so? That repository is of different Operating System type. The best guess that I can make is that the repositary updated your packages to a type not supported by Ubuntu...

My best advise would be to do a reinstall, and then use Add/Remove to install Beryl.

---

