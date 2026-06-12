---
title: "Nvidia-settings"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by tomcat1965 on 2006-12-07
After successfully installing the new nvidia driver and Beryl when I run nvidia-settings I get the new settings control panel but the left pane with settings is blank apart from the "nvidia settings" title.
I had the same thing happen after installing Beryl with the previous 8xxx driver. Before I had options like adjust digital vibrance,colour,hue,saturation etc......is this just a Beryl side effect or a bug?

---

### Post by BLTicklemonster on 2006-12-07
I never see that. did you do that nvidia-config or whatever it was you were supposed to do after the installation? (that is not the right command, btw)

how do you open nvidia-settings? do you launch it from the tool bar, or open it with a terminal?

---

### Post by useResa on 2006-12-07
I believe that what is meant is the tool that is available via Applications --> System Tools --> NVIDIA X Server Settings

See attachment

---

### Post by BLTicklemonster on 2006-12-07
Yeah, I love it! First time around, I didn't have it, so I installed it 

```
sudo aptitude install nvidia-settings
```


and had to run it


```
sudo nvidia-settings
```

but it's there this time around. :)

---

### Post by tomcat1965 on 2006-12-07
This is the screenshot of what I get at the moment. If I run apt-get install nvidia-settings I get a message saying nvidia glx is to be removed as it's broken. Via synaptic it is not listed as broken. If Beryl works I can't believe it is broken although Beryl runs really smooth I get 440 fps in glxgears which sounds very low,although the processor is an ancient AMD Turion. 900MHZ I think.

---

### Post by useResa on 2006-12-08
> **tomcat1965 said:**
> After successfully installing the new nvidia driver and Beryl.
Which Nvidia driver did you install exactly.
Personally I run the latest Nvidia Beta driver (which I obtained from [here]("http://www.nzone.com/object/nzone_downloads_linux_display_x86_1.0-9742.html")) and Beryl and as you could see from the screenshot in my previous post I have no problem running Nvidia Settings.

Isn't it an option to re-install nvidia-glx?

---

### Post by tomcat1965 on 2006-12-08
I tried to install from there originally but just got an error message all the time that the file couldn't be opened.:confused:

---

### Post by useResa on 2006-12-08
You have to save the **NVIDIA-Linux-x86-1.0-9742-pkg1.run** file (using right mouse button and selecting "Save Link as ...") to your computer.
Next follow the instructions as described in Method 2 on [this page]("https://help.ubuntu.com/community/Latest_Nvidia_Dapper").

Hope this will help you .

---

### Post by tomcat1965 on 2006-12-08
I downloaded the latest driver to my home directory(after I read the "if you're reading this then you should have right clicked bit... LOL)
Ctrl Alt F1 .....logged in......then found the installer telling me my card's not supported!!( MX 440) I read it was on the forum....I have the nvidia-glx driver installed so guess I'll have to stay with that.
If I type sudo apt-get install nvidia-settings I get the message nvidia-glx will be removed...not that I'm bothered about the control panel just would be nice if it worked.
Many thanks for your input much appreciated:)

---

### Post by useResa on 2006-12-08
Sorry to hear your card is not supported.
Glad that I could be of somewhat assistance.

---

