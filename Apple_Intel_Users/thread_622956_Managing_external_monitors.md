---
title: "Managing external monitors"
date: 2007-11-25
forum: Apple Intel Users
---

### Post by karl_kashofer on 2007-11-25
Hi all !

I have a macbook C2D and use a mini-DVI to VGA connector to connect to a beamer at work. 
I would like to share how that works using xrandr

When X boots it determines what size is the biggest connected screen and defines the intel drivers framebuffer for the largest square needed. So if you just boot your laptop it will be 1280x1280.
The screens in Xorg just provide a view on that square, in the normal case a 1280x800 view on the top part of it. You can run xrandr to see: 
[INDENT]karl@karl-laptop:~$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1280 x 1280
VGA disconnected (normal left inverted right)
LVDS connected 1280x800+0+0 (normal left inverted right) 286mm x 179mm
   1280x800       59.9*+   60.0
   1280x768       60.0
   1024x768       60.0
   800x600        60.3
   640x480        59.9
TMDS-1 disconnected (normal left inverted right)
TV disconnected (normal left inverted right)
karl@karl-laptop:~$
[/INDENT]

This means we have a square of 1280x1280 and look at the top 800 lines of it. "LVDS connected 1280x800+0+0" means our laptop monitor looks at 1280x800 with no (0x0) offset.

Now if we want to use any other setup than just external or internal we need to expand our view with a Virtual line in xorg. If you connect the external monitor on boot it will become default, so you get the framebuffer size from the external monitor and it becomes the default monitor so you have no picture on the internal screen.

So for most setups we can add "Virtual 2960 1824" into the screen section of xorg.conf.

Now the framebuffer will be 2960x1824 and will fit my 1680 wide flatscreen and the 1280 wide laptop screen next to each other.

I then use this script to switch monitor configurations:
[INDENT]if  xrandr | grep -q "VGA disconnected"
then
echo No external monitor detected, press enter for exit.
read tmp
exit 1
fi

echo "Please select:"
echo "Only internal              ... 1"
echo "Only external              ... 2"
echo "Mirroring                  ... 3"
echo "Desktop expansion to left  ... 4"
echo "Desktop expansion to right ... 5"

read selection

case "$selection" in

   1)
    xrandr --output LVDS --auto --output TMDS-1 --auto --output VGA --off --output TV --off ;;
   2)
    xrandr --output LVDS --off --output TMDS-1 --off --output VGA --auto --output TV --off;;
   3)
    xrandr --addmode VGA 1280x800
    xrandr --fb 1280x800
    xrandr --output LVDS --auto --output TMDS-1 --off --output VGA --same-as LVDS --mode 1280x800 --output TV --off ;;
   4)
#    xrandr --addmode VGA 1280x800
    xrandr --output LVDS --auto --output TMDS-1 --off --output VGA --auto --left-of LVDS --output TV --off
#    xrandr --output LVDS --pos 1680x250
    ;;
   5)
    xrandr --output LVDS --auto --output TMDS-1 --off --output VGA --auto --right-of LVDS --output TV --off ;;
   *)
    echo "Wrong input. Exiting."
esac
[/INDENT]

This works fine as long as the framebuffer is large enough. Unfortunately with the intel driver you cant change the framebuffer size once X has started.

I have recently found one limitation though:
The kde screensaver euphoria gets really slow and CPU goes really high if the framebuffer is that large. It seems to me that the screensaver is expanded over the whole framebuffer not just the active screen. 
Would anyone know how to fix this ?

Hope this works for you,
Cheers,
Karl

---

