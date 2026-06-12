---
title: "Help with Beryl &amp; nvidia-settings"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by SinxarKnights on 2007-01-22
I am using Dapper Drake (6.06 LTS)

Since I never get an answer in any other forums I figure I should ask about this here. I installed Beryl and it works great. I am using a GeForce 5200FX and wanted to tweak my card a bit. I had the nvidia-glx driver installed but now when I type:
```
nvidia-settings
```

I get this error message:

```
joey@joey-desktop:~$ nvidia-settings

ERROR: NV-CONTROL extension not found on this Display.


ERROR: Unable to determine number of NVIDIA GPUs on ':0.0'.


ERROR: Unable to determine number of NVIDIA Frame Lock Devices on ':0.0'.
```

Is there a way to access my graphics cards settings with Beryl installed, or did I screw up my install.

I tried to reinstall nvidia-glx but no change. Also you cannot have nvidia-glx and nvidia-settings installed at the same time. But you can use nvidia-settings with just nvidia-glx (im assumming its built in?). I'm thinking I need to reinstall nvidia-kernel-common but I will hold off on this until i get some feedback.

---

### Post by ComplexNumber on 2007-01-22
although i'm not 100% certain, it may be because you haven't yet configured your xorg.conf file. see [this]("http://www.ubuntuforums.org/showthread.php?t=339426") thread because i later go into detail about how to modify that file (see post 12).

---

### Post by SinxarKnights on 2007-01-22
I have edited the crap out of that file already. But I did find out what it was.

I have another question now. When I boot into ubuntu. When I open a window the title bar and border will flash constantly. I read at the beryl forums that it is usually caused by 2 of the same manager running. So thinking about that, when the borders are flashing, I "quit" the Beryl Manager and it works fine (stops flashing). Anyone have a clue to what to do? I am stumped! I have been unable to find a fix for this.

---

### Post by ComplexNumber on 2007-01-22
>  But I did find out what it was.to help others in the same position, would you mind stating what it was that was giving you the initial problem?

---

### Post by SinxarKnights on 2007-01-22
Well I can't find the orginal post that solved the problem. But it just said something along the lines of there is no direct render support with nvidia so the control panel won't work with beryl. But I really need to fix the flashing window borders. Anyone have any luck getting that fixed?

---

