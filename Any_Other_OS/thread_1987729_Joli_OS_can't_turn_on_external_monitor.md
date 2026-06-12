---
title: "Joli OS: can't turn on external monitor"
date: 2012-05-26
forum: Any Other OS
---

### Post by Count Hankey on 2012-05-26
Hi everyone,

Yesterday I installed Joli OS on my laptop, in dualboot with Windows 7. Everything works fine, except my external monitor. This is disabled. I know I can turn it on in the NVidia Control Panel, but when I try to save I get the message that I can't save it to the xorg.conf-file. Below I will discribe step by step what I tried to turn my external monitor on, using screenshots.

First of all I click on 'Monitor' on the dashbord. Then I get this message.
[IMG]http://img138.imageshack.us/img138/5170/60226812.jpg[/IMG]

When I press 'no', I get this screen. When I press 'detect monitors' nothing happens.
[IMG]http://img51.imageshack.us/img51/8493/45956161.jpg[/IMG]

When I press 'yes', the NVidia Control Panel opens. As you can see my external monitor HKC is disabled.
[IMG]http://img171.imageshack.us/img171/4593/63372397.jpg[/IMG]

I can turn it on. I choose for 'Twinview'. Choosing 'Seperate X screen' caused me big problems in Linux Mint, so I choose for 'Twinview'
[IMG]http://img37.imageshack.us/img37/2947/53859688.jpg[/IMG]

When I try to save the changes. This message comes up
[IMG]http://img444.imageshack.us/img444/1193/52115949.jpg[/IMG]

The only thing I can do is clicking 'OK'. So I did.
[IMG]http://img706.imageshack.us/img706/4571/99692121.jpg[/IMG]

When I click save this error comes up
[IMG]http://img43.imageshack.us/img43/3550/45990866.jpg[/IMG]

So nothing is saved and I still can't use my external monitor. Maybe it is interesting, so I enclosed my xorg.conf-file too. This is it.
[IMG]http://img715.imageshack.us/img715/9999/88212628.jpg[/IMG]

Could anyone help me, please? Big thanks in advance!

---

### Post by bruno9779 on 2012-05-26
Try running the nvidia tool from command line with "sudo".

```
sudo nvidia-settings
```

---

### Post by Count Hankey on 2012-05-27
Big thanks, bruno9779! It works! :)

Do you, or anyone else, know how I can manually add an other resolution? I prefer 1024x600, but I can only choose 1280x800 or a 4:3 ratio resolution.

Thanks in advance!

Edit: what I actually want, is my primary laptop screen 1024x600 and my external monitor 1280x720. The 1280x720 is already done.

---

### Post by bruno9779 on 2012-05-28
What Nvidia driver do you have installed?

The default one, the one from ppa or the one from Nvidia website?

I advise you to add x-swat ppa to keep the drivers updated:

```
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current
```

After reboot you should have the correct resolution options for your monitor.

---

### Post by Count Hankey on 2012-05-28
I didn't install anything manually, so I think I use the default drivers. I will try the code you posted, thanks! :)

---

### Post by Count Hankey on 2012-05-28
I opened a terminal and paste the code you posted, but still I cant choose 1024x600 as my resolution. In Windows I can choose it whitout problems, so it must be supported... Is there a way to add it manually?

Thanks in advance! :)

---

### Post by Count Hankey on 2012-06-02
Hi, could anyone tell me how I can remove the NVidia Driver from Joli OS, please? It was installed by default.

But finnaly I know how I can add a costum resolution in Linux. I did in Linux Mint and Easypeasy, both based on Ubuntu, like Joli OS. But in Linux Mint and Easypeasy the only way to do it, was without the NVidia driver. Not a problem, because in these OS you could easily remove it. But in Joli OS I can't find a way to remove the NVidia driver. So hopefully could anyone help me, please? Thanks in advance! :)

btw, I used [this site]("http://ubuntuforums.org/showthread.php?t=1295831") to add the 1024x600 resolution to Linux Mint and Easypeasy. In Joli OS it doesn't work, because it conflicts with the NVidia driver I guess.

---

