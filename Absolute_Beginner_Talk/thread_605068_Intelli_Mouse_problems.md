---
title: "Intelli Mouse problems"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by limptwiglet on 2007-11-06
Hello all,

I have an Intelli mouse and have been trying to get the extra buttons to work fully and followed this guide:

[http://dotnet.org.za/matt/pages/39097.aspx](http://dotnet.org.za/matt/pages/39097.aspx)

But after restarting my scroll wheel now takes me back in my browser history and it no longer works as expect in other applications.

My xorg.conf file looks like this.

```

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
        Option          "Buttons"       "7"
        Option          "ButtonMapping" "1 2 3 4 5 6 7"
EndSection

```

Can anyone help me? I'm sorry to ask a question that I so simple.

Thanks for any help.

---

### Post by daimaru on 2007-11-07
try this guide [http://ubuntuguide.org/wiki/Ubuntu:Feisty#Activate_side-mouse-buttons_in_FireFox]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#Activate_side-mouse-buttons_in_FireFox")
do the "Install & Configure IMWheel" stuff. you may have to change a few things in your xorg.conf file. mine now says:

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ExplorerPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Buttons" 	"7"
        Option		"ButtonMapping" "1 2 3 6 7"
EndSection

and it works fine just change the  button mapping and zaxis stuff until you get it right ;:) sorry was trial and error for me too, but now everything works

---

