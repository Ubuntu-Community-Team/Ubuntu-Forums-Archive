---
title: "Aterm keyboard layout problem? [locales!]"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by MrGreen on 2007-05-03
Hi,

I normally use Aterm terminal but under ubuntu keyboard layout is wrong everything works ok in Xterm

My .Xdefaults

```

aterm*foreground: white
aterm*background: black
aterm*transparent: true
aterm*shading: 90
aterm*saveLines: 3000
aterm*tintingType: true
aterm*tinting: #c0c0c0
aterm*fading: 50
aterm*transpscrollbar: true 
aterm*scrollBar: off
aterm*pointerColorBackground: black
aterm*loginShell: false 
aterm*title: Terminal 
aterm*font:*-*-fixed-medium-r-normal--*-140-*-*-*-*-iso8859-1
aterm*boldFont:*-*-fixed-bold-r-normal--*-*-140-*-*-*-*-iso8859-1

```

Can anyone tell me if there is anything wrong with above?

Thanks

MrG

---

### Post by hencke on 2007-05-03
I have no idea about aterm, but my layout problems have been related to two things:

1) xorg.conf
Type:
gedit /etc/X11/xorg.conf
See:
-> Section "InputDevice"
-> Option "XkbLayout" "xx"
Check that xx refers to your locale.

2) Gnome preferences
Go to:
System -> Preferences -> Keyboard -> Layouts
Check that your locale layout has been selected.

It could be that Xterm uses xorg.conf layout and aterm uses the gnome layout (the one in preferences).

Do you have the layout problem ONLY in aterm, or is it also in for example gedit or OpenOffice as well?

---

### Post by MrGreen on 2007-05-03
Well there is no entry in xorg.conf :confused: so maybe thats the problem ...

keyboard layout in gnome is correct

thanks for your help

MrG

---

