---
title: "MacBookPro6,2 LCD brightness control"
date: 2010-05-06
forum: Apple Hardware Users
---

### Post by bfroemel on 2010-05-06
Either wait for the updated packages (maintainers are already contacted) or use those for now.

Enjoy!

---

### Post by stefanwa on 2010-05-06
Thanks!

---

### Post by abel_bcn on 2010-05-06
I don't think it's working for me. Is rebooting necessary? I'll try later anyways.

---

### Post by abel_bcn on 2010-05-06
Rebooting was indeed necessary. Works flawlessly now :)

---

### Post by bfroemel on 2010-05-06
yes, either reboot or install the mbp-nvidia-bl-dkms first and ensure that the module is loaded:
```

sudo rmmod mbp_nvidia_bl           # just in case a previous version was installed
sudo modprobe mbp_nvidia_bl

```

The module must be loaded. Then install pommed - it is started automatically.

If it works - you're good. If not you may follow this short debug session:

Can you control the backlight by setting brightness manually with:

```

echo 3 | sudo tee /sys/class/backlight/mbp_backlight/brightness
echo 15 | sudo tee /sys/class/backlight/mbp_backlight/brightness

```

?


In case this doesn't work, please post dmesg after the module insertion.
In case it does work, but the F1 and F2 keys do not work: first make sure that mouseemu is not installed (interferes with pommed) - then try to restart pommed
```

sudo /etc/init.d/pommed restart
[code]

And if you still don't get any control, please post the output of:
[code]
sudo /etc/init.d/pommed stop
sudo pommed -d

```

and press F1/F2 a few times.

You can quit the debug run by pressing [Ctrl]-[c].

---

### Post by bfroemel on 2010-05-06
> Rebooting was indeed necessary. Works flawlessly now

Ah - well, great! :)

---

### Post by kosumi68 on 2010-05-06
> **bfroemel said:**
> yes, either reboot or install the mbp-nvidia-bl-dkms first and ensure that the module is loaded:
```

sudo echo 3 > /sys/class/backlight/mbp_backlight/brightness
sudo echo 15 > /sys/class/backlight/mbp_backlight/brightness

```


Actually, the file redirect is done with user creds, not for sudo (this is an oldie :-)):

```

echo 3 | sudo tee /sys/class/backlight/mbp_backlight/brightness

```

etc will work.

---

### Post by abel_bcn on 2010-05-06
> **bfroemel said:**
> Ah - well, great! :)

Thanks for the info anyways. I'm looking forward to customize some power management stuff.

---

### Post by rabidcentipede on 2010-05-07
it's working for me, but I seem to be having a problem with the keyboard backlight controls. I hit F5 to turn down the kb light, and it works as expected. However, once it gets to the "lowest" light setting, if I hit it again, instead of turning off completely, the keyboard lights go back up to full brightness. 

Is there any way to fix this? Thanks!

---

### Post by lael on 2010-05-09
> **bfroemel said:**
> Either wait for the updated packages (maintainers are already contacted) or use those for now.

Enjoy!

Where did you get the source to rebuild mbp-nvidia-bl-dkms? 
Do you know where I can find the repo to mbp-nvidia-bl-dkms and nvidia-bl-dkms ?

I have a MacBookPro6,1 and I'm trying to get my backlight to work

---

### Post by bfroemel on 2010-05-09
```
 
sudo add-apt-repository ppa:mactel-support && apt-get update
sudo apt-get source mbp-nvidia-bl-dkms 
```

---

### Post by macsrok on 2010-05-11
SOLVED PLEASE IGNORE

Hi,

I need help. I've followed all the instructions and I can't get pommed to start. I've installed the updated mbp-nvidia-bl-dkms and when I try to install pommed I get the following error message: " Starting Apple laptops hotkeys events handler: invoke-rc.d: action "start" failed.

Any advice?

Thanks in advance.

---

### Post by Simonmoush on 2010-05-11
> **bfroemel said:**
> Either wait for the updated packages (maintainers are already contacted) or use those for now.

Enjoy!

How do i open these?

---

### Post by majortom67 on 2010-08-10
Very useful post. Unfortunately everytime I restart I need to reinstall nvidia drivers and pommed otherwise nothing works.
(MB Pro 6,2).
Majortom

---

### Post by math- on 2010-08-24
> **rabidcentipede said:**
> it's working for me, but I seem to be having a problem with the keyboard backlight controls. I hit F5 to turn down the kb light, and it works as expected. However, once it gets to the "lowest" light setting, if I hit it again, instead of turning off completely, the keyboard lights go back up to full brightness. 

Is there any way to fix this? Thanks!


Hi,

I have the same problem. Did you find an issue  please?

---

### Post by Vathanak on 2012-04-19
all settings seem to return back to default after restarting such as screen brightness.

---

### Post by oldos2er on 2012-04-20
Old thread closed.

---

