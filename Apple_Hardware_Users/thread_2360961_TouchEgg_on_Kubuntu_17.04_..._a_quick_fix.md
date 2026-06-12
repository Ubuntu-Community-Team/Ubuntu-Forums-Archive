---
title: "TouchEgg on Kubuntu 17.04 ... a quick fix"
date: 2017-05-10
forum: Apple Hardware Users
---

### Post by MikeBraxner on 2017-05-10
Just relaying some information .... Due to a change in [xserver-xorg-input-synaptics 1.9.0-1ubuntu1]("https://www.mail-archive.com/desktop-packages@lists.launchpad.net/msg484116.html"), ***touchegg***  won't work out of the box under ***Kubuntu 17.04***. 

As a temporary workaround ( see [here]("https://askubuntu.com/questions/905159/touchegg-trackpad-gestures-stopped-working-after-upgrading-to-17-04") and [here]("https://github.com/iberianpig/xSwipe#install-older-version-synaptics-driver-that-is-compatible-with-xswipe")), revert  to an older version of the synaptics driver, e.g. ...
```
sudo apt install -y git build-essential libevdev-dev autoconf  automake libmtdev-dev xorg-dev xutils-dev libtool
sudo apt remove -y xserver-xorg-input-libinput
sudo apt remove -y xserver-xorg-input-synaptics
git clone https://github.com/Chosko/xserver-xorg-input-synaptics.git
cd xserver-xorg-input-synaptics
./autogen.sh
./configure --exec_prefix=/usr
make
sudo make install
```

... and ensure /etc/X11/xorg.conf.d/60-synaptics.conf contains ...
```
Section "InputClass"
    Identifier      "evdev touchpad catchall"
    Driver          "synaptics"
    MatchDevicePath "/dev/input/event*"
    MatchIsTouchpad "on"
    Option          "Protocol" "event"
    Option          "SHMConfig" "on"
EndSection
```

After a reboot, touchegg works just fine ... assuming you've installed  it.

---

