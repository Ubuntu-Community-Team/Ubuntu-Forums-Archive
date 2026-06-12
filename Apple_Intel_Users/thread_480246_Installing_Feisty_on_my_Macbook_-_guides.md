---
title: "Installing Feisty on my Macbook - guides?"
date: 2007-06-21
forum: Apple Intel Users
---

### Post by aktiwers on 2007-06-21
Okay so now its time to make my Macbook 100% Ubuntu. 

Is there any guide or howto install it on a normal Macbook(not PRO) ?

I basically want it to work and also make sure that the Duo Core works correct.. can anyone point me in the right direction? 

This is pretty much the one I got:
[http://www.apple.com/macbook/specs.html](http://www.apple.com/macbook/specs.html)
(the small one)

---

### Post by kzm. on 2007-06-21
i just installed feisty 7.04 64bit yesterday again and can give you my tomboy notes (more or less the same like the [help]("https://help.ubuntu.com/community/MacBook")):

Install Notes MacBook 
Computer: c2d 2.16 
Ubuntu: feisty 7.04 64bit

1) wifi
    sudo apt-get install gcc g++ libc6-dev linux-headers-2.6.20-16-generic build-essential debhelper
    tip: uname -r > kernel versio
    wget [http://snapshots.madwifi.org/madwifi-hal-0.9.30.13-current.tar.gz](http://snapshots.madwifi.org/madwifi-hal-0.9.30.13-current.tar.gz)
    tar -zxvf madwifi-hal-0.9.30.13-current.tar.gz
    cd madwifi <tab>
    make
    sudo make install
    sudo make clean
    reboot

2) screen resolution
    sudo apt-get install 915resolution
    restart xserver

3) function key
    sudo apt-get install sysfsutils
    sudo gedit /etc/sysfs.conf
    add: module/hid/parameters/pb_fnmode = 2
    reboot
    test: volume |  fn+volume

4) backlight
    sudo gedit /usr/share/hal/fdi/policy/10osvendor/10-macbook-backlight.fdi 
    line 6 change "Apple Computer, Inc" to "Apple Inc."

5) keys
    to get right/middle mouse button to keys:
    sudo mkdir /bin/scripts
    sudo gedit /bin/scripts/keys_mouse_mac_fix
    add:
    #makes lower enter key right click.
    xmodmap -e 'keycode 108 = Pointer_Button3'
    #makes right apple key middle click.
    xmodmap -e 'keycode 116 = Pointer_Button2'
    
    sudo nautilus
    go /bin/scripts/ select keys_mouse_mac_fix set under permission "executable"
    go System > Preferences > Session 
    add "mac mouse fix" : /bin/scripts/keys_mouse_mac_fix

6) mouse (works: scroll right side, right mouse three-finger-tap)
    block tapping while typing:
    System > Preferences > Sessions
    add: syndaemon -t -d
    sudo apt-get install gsynaptics

7) isight
    sudo modprobe -r uvcvideo
    sudo mv /lib/modules/$(uname -r)/kernel/ubuntu/media/usbvideo/uvcvideo.ko /lib/modules/$(uname -r)/kernel/ubuntu/media/usbvideo/uvcvideo.ko.original
    sudo apt-get install libusb-0.1-4 libusb-dev linux-headers-$(uname -r)
    wget [http://files.i-nz.net/projects/linux-kernel/isight/uvcvideo-isight.tar.gz](http://files.i-nz.net/projects/linux-kernel/isight/uvcvideo-isight.tar.gz)
    tar -xzvf uvcvideo-isight.tar.gz
    cd against-revision-100
    sudo make
    sudo make install
    sudo modprobe uvcvideo
    sudo apt-get install libusb-0.1-4 libusb-dev linux-headers-$(uname -r)
    wget [http://people.freedesktop.org/~rbultje/linux-uvc-0.1.0-b.tar.gz](http://people.freedesktop.org/~rbultje/linux-uvc-0.1.0-b.tar.gz)
    tar zxf linux-uvc-0.1.0-b.tar.gz
    cd linux-uvc-0.1.0-b
    sudo make
    sudo make install
    sudo mkdir /mnt/mac
    sudo mount -t hfsplus /dev/sda2 /mnt/mac/
    sudo ./extract /mnt/mac/System/Library/Extensions/IOUSBFamily.kext/Contents/PlugIns/AppleUSBVideoSupport.kext/Contents/MacOS/AppleUSBVideoSupport
    sudo modprobe uvcvideo

    test: gst-launch-0.10 v4l2src ! video/x-raw-yuv,format=\(fourcc\)UYVY,width=640,height=480 ! ffmpegcolorspace ! ximagesink

8) mount osx
    sudo mkdir /mnt/mac
    sudo mount -t hfsplus /dev/sda2 /mnt/mac/

9) fan speed
     get: sudo cat /sys/devices/platform/applesmc/fan0_actual_speed
            sudo cat /sys/devices/platform/applesmc/fan0_maximum_speed
     set:  sudo gedit /etc/rc.local:
                echo 3000 > /sys/devices/platform/applesmc/fan0_minimum_speed
             sudo gedit /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux (on a line by itself BEFORE the final "exit" statement)
                echo 3000 > /sys/devices/platform/applesmc/fan0_minimum_speed 

10) monitor cpu heat
      cd ~/mactel-linux/trunk/tools/temperature
      sudo modprobe msr
      sudo ./coretemp

11) flash
      wget [http://home.comcast.net/~ubuntume/nsplugin-wrapper-install-0-1.1.tar.gz](http://home.comcast.net/~ubuntume/nsplugin-wrapper-install-0-1.1.tar.gz)
      unzip
      ./nspw install

12) compiz
      sudo apt-get install gnome-compiz-manager

13) java 6
       i dunno yet

---

### Post by kzm. on 2007-06-21
and if you run refit (which is easy to set up) to boot a hint:
on osx: sudo pico /efi/refit/refit.conf 
uncomment: "legacyfirst"

---

### Post by kzm. on 2007-06-21
and another tip. wireless dropps off once in a while (dissapears) repeat those steps:

cd madwifi <tab>
make
sudo make install
reboot


and it'll be back

---

### Post by aktiwers on 2007-06-21
Wow thanks guys! I will try it out.. I will let you know if I hit any problems :)

---

### Post by 11xzeginx11 on 2007-06-25
OK....Can you tell me how to do all that with no internet connection.

---

### Post by 11xzeginx11 on 2007-06-25
you guys make it sound sooo easy. i've been up all night just tring to get the wifi working. When i plug in my cable modem, i can see packets leaving my macbook, but when i fire up firefox or do an apt-get, i get a connection error. And i know there is a connection. Also, i installed madwifi, and i just get errors...i might just stick with OSX.

---

### Post by kzm. on 2007-06-25
you should do the first installs with ethernet. i had some troubels the first time with the madwifi too. it looked like total random to me. but if you follow the steps above and do reboot afterwards it should work.. at least in a dualboot situation.

if you still remain having problems do an advance searched on this forum and/or follow the original posts on the help section of this forum (the link i talk about above).

but of course you also can just stick to osx... not knowing what you are missing :D

---

### Post by ivesjd on 2007-06-25
Like kzm said above. Installing fiesty with ethernet pluged in helps alot. It configures it to work automaticly that way.

---

### Post by ronocdh on 2007-06-25
> **11xzeginx11 said:**
> you guys make it sound sooo easy. i've been up all night just tring to get the wifi working. When i plug in my cable modem, i can see packets leaving my macbook, but when i fire up firefox or do an apt-get, i get a connection error. And i know there is a connection. Also, i installed madwifi, and i just get errors...i might just stick with OSX.
I don't know why you got two replies chastising you to use ethernet when you clearly are (unless you have some mythical faery dust cable modem with a FireWire 1600 connection--which, I must admit, would be totally badass, and I want one for myself). Anyway, as the guys above have said, DHCP-enabled ethernet *should* work out of the box. Have you tried placing a router between your modem and computer? The router might play more nicely with your system.

---

### Post by kzm. on 2007-06-26
and once you have your ehternet working (you can use static ip also through going to system > administration > network: select your ehternet card, go properties.. rest should be abovious).
if the madwifi doesnt work, try it again.. reboot.. be patient. it didnt worked with me first neither, but eventually did. now once in a while its gone and i reinstall it...

---

### Post by aktiwers on 2007-06-26
I followed all the advices here and it went great! :)
Thanks!

Now all I need to do is to get:
1) Touchpad working when using 2 fingers (is this possible yet?)
2) Get my cam to work ( I used the guide here on the forum, but without luck :( )
3) Get the program Cheese (for the webcam) to work.. It doesnt seam to compile right? 

Number 3 is not really that importent.. cant post the errors im getting as im not on the Mac right now.. but if this not enough info, then I will post them tomorrow or so :)

Thanks again!

---

### Post by ivesjd on 2007-06-26
> **aktiwers said:**
> I followed all the advices here and it went great! :)
Thanks!

Now all I need to do is to get:
1) Touchpad working when using 2 fingers (is this possible yet?)
2) Get my cam to work ( I used the guide here on the forum, but without luck :( )
3) Get the program Cheese (for the webcam) to work.. It doesnt seam to compile right? 

Number 3 is not really that importent.. cant post the errors im getting as im not on the Mac right now.. but if this not enough info, then I will post them tomorrow or so :)

Thanks again!

Cheese is very very early in devolpment. I posted it up here before I realized the project was start on april 21! But I someone has gotten it to compile. But didnt have video. I have not gotten it to compile. Hopefully soon.

---

