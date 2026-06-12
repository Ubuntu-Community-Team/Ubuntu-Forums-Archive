---
title: "Macbook Pro 8,3 with Cosmic"
date: 2019-03-16
forum: Apple Hardware Users
---

### Post by dieselnutjob on 2019-03-16
I successfully got Ubuntu installed on my old 8,3.
Firstly, there are no instructions on [https://wiki.ubuntu.com/MactelSupportTeam](https://wiki.ubuntu.com/MactelSupportTeam) for this combination.  I thought that I could write something but I have neither the permissions or enough posts to do anything about it.
For the benefit of others this is how I did it.

1. My DVD drive wasn't working so I bought a caddy and put a second drive in it.  So I have OSX on the normal drive and Ubuntu on the other.  I can use the Option key when I hear the boot up noise to choose which one.

2. I used the ubuntu server ISO image

3. As it boots I hit the E key to edit the boot up options.
I changed
```
set gfxpayload=keep
```
to
```
set gfxpayload=text
```

I changed
```
linux /casper/vmlinuz boot=casper quiet ---
```
to
```
linux /casper/vmlinuz boot=casper adeon.modeset=0 i915.modeset=1 i915.lvds_channel_mode=2 ---
```

Hit F10 to boot

4. After installation I connected to Ethernet and rebooted

5. When ubuntu comes up you can't see the screen, so I found the IP address of the Macbook in my routers DHCP table and ssh into it.

6. Edit  /etc/grub.d/10_linux
add these lines
```
echo "    outb 0x728 1" | sed "s/^/$submenu_indentation/"
echo "    outb 0x710 2" | sed "s/^/$submenu_indentation/"
echo "    outb 0x740 2" | sed "s/^/$submenu_indentation/"
echo "    outb 0x750 0" | sed "s/^/$submenu_indentation/"

```before the line that says echo "        insmod gzio" | sed "s/^/$submenu_indentation/"

These lines disable the GPU so from now on only the HD3000 graphics built into the processor will work (which is what I want)

run 
```
update-grub
reboot
```


7.  Install the GUI that you like, in my case that's 
```
[COLOR=#333333][FONT=monospace]apt-get update[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]apt-get upgrade[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]apt-get install lxqt xinit[/FONT][/COLOR]
```
But most people will probably prefer a more conventional window manager than LXQT,  but I really like it.

to get wifi working
```
apt-get install firmware-b43-installer
```

I still need to tune my installation.  Problems still to solve
Can't adjust baclight brightness.
Keyboard doesn't illuminate
Can't right click on the mouse pad.

Anyway I think that there are solutions to all of these things; I just need to google and experiment

---

### Post by dieselnutjob on 2019-03-24
wifi is only working on 2.4 GHz.  5 GHz doesn't work.  Does anyone have a solution?

---

