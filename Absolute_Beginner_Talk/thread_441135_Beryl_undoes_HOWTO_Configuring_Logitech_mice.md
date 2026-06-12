---
title: "Beryl undoes HOWTO: Configuring Logitech mice?"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by timzak on 2007-05-12
I'm using Logitech MX700

I previously went through the Configuring Logitech Mice HOWTO to configure my side buttons to work as forward and back in both Firefox and Nautilus.  It worked GREAT (btw, I'm using Feisty; the HOWTO is written for 6.06 but worked fine in 7.04 the first time).  Then the following happened:

1) I hosed my xorg.conf file when changing video driver versions.  I got this fixed through the console with the help of member Pigsflew.

2) I installed Beryl (it's configured properly and working great).

At some point during event 1 and 2 above, my side mouse buttons stopped working.  I'm not sure when.

I went through the HOWTO again, exactly (copying and pasting to avoid mistakes).  It does not work now.  My system does not boot into Gnome now (DOS-like text stuff with a blue screen telling me my mouse is not configured properly).  I was able to get myself out of this by restoring my xorg.conf backup file (an accomplishment in itself for a newbie) and I tried a 2nd time with a second event number (checked in advance to be unused) and I got the same error again.  I got myself out again by restoring the backup xorg.conf file, I rechecked the mouse section in xorg.conf and it looks good compared to the HOWTO. 

So why can't I get the side buttons working this time?  Did Beryl do something to the mouse configuration?  Did my video driver crash do something?  Or am I just missing something?

Thanks.

---

### Post by timzak on 2007-05-12
Can anyone help me?

---

### Post by timzak on 2007-05-13
Please help.  I rephrased some things to help clarify.

Thanks.

---

### Post by johnc4510 on 2007-05-13
timzak, please post this part of your xorg.conf file:

Section "InputDevice"
    Identifier     "Configured Mouse"

Please also post the contents of this file:

gedit ~/.xbindkeysrc

I will then try to help you out.

---

### Post by timzak on 2007-05-13
```
Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection
```

Notice this is nothing like the HOWTO for configuring Logitech mice.  I'm not sure what changed it to what you see above, but originally, I had it set up:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"evdev"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/event9" #this should be that underlined name from 19-local.rules
EndSection
```

which worked great until sometime between #1 and #2 in my opening post.

And for your second request:

```
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:6
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  m:0x0 + b:7
"~/.click/click 4"
  m:0x0 + b:9
"~/.click/click 5"
  m:0x0 + b:10
```

Thanks for the reply.

---

### Post by johnc4510 on 2007-05-13
well, your xorg.conf is much different than mine.  But my mouse is an LX7. Which has 7 buttons. Not sure how many yours has. Here if my xorg.conf for the mouse. It should get you to the point of booting up, although the button mapping maybe slightly different. Just type in a terminal: sudo gedit /etc/X11/xorg.conf. Then copy and paste the below conf and replace what is in yours with what is in mine. Then save and close. Note is this does not work, you will have to restore your backup xorg.conf file.  Please post results back here.

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Buttons" "7"
    Option         "ButtonMapping"   "1 2 3 6 7"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "false"
    Option         "Resolution 100"
EndSection

---

### Post by timzak on 2007-05-13
Hi, here is the result when replacing that section of xorg.conf with your code:

Failed to start X server (blue screen with text only)

"data incomplete in file xorg.conf.  undefined InputDevice "Mouse0" referenced by ServerLayout "Layout0

I restored the original xorg.conf file and am back here.

Any ideas?

Thanks.

---

### Post by timzak on 2007-05-15
Still unresolved...any help?

---

### Post by jkeyes0 on 2007-05-15
In your InputDevice section of your xorg.conf file, change the "Identifier" from "Configured Mouse" to "Mouse0" and reboot.

---

### Post by Stoffer on 2007-06-17
I have the same problem.  The issue is with Berly, although I can't guarantee what you did prior to that didn't do anything either.

And the solution of changing "Configured Mouse" to "Mouse0" crashed my xserver.  

So... still no solution...

---

### Post by timzak on 2007-06-17
This is an old thread, and I'm sorry to say I never posted back my solution.  So here it is (better late than never):

First, at one point I saved my xorg.conf file from within nvidia-settings.  I found that when you do this, it replaces your mouse config section with its own generic one.  This is how my mouse modifications disappeared.

Second, in the section "ServerLayout", the nvidia-settings changes your mouse input device identifier to "Mouse0", which in my case didn't match my mouse sections identifier of "Configured Mouse".  Whatever you have your mouse identified as in the mouse section has to match the description in the ServerLayout section.

Also, if you're trying to find the ServerLayout section, it defaults to the end of the xorg.conf file.  The nvidia-settings version moves it to the beginning of the file.  

If you want to save your settings via nvidia-settings, I recommend saving it to a different filename, like xorg.conf-nvidia, then copy and paste the appropriate sections from this file to your actual xorg.conf file.  This way you don't lose any mouse configuration settings you make.

Hope this helps.

---

