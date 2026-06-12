---
title: "mail and resolution issue"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by ceezax on 2007-03-17
hi there 

i have tried all the last night to change my screen resolution and i asked for help here

and users here told me to use dpkg-reconfigure xorg.xconf and i changed it then 

after restarting my ubuntu i found that my X can't start telling me that my screen can't 

handle 24 depth ??

so i just recovered the xorg.xonf form xorg.xconf.save and my X starts but with the 

same resolution , so till now i can't change my resolution :(  ??

i don't know till now may be it's due to my video card don't have the correct driver ?? 

i really don't know what to do ?? 

2-the same problem with my audio card which is correctly defined and i have the 

audio tab available up , but till now i don't have sound ????

3-the third thing i just want to use evolution mail , so i want to use my hotmail 

account so it asks me for the server type which i don't know ??

and under the configuration tab it asks me for the server ??? 

so please can't any body tell me how to configure the evolution mail for my hotmail 

account ??

---

### Post by mrmonday on 2007-03-17
1. What graphics card do you use?

2. What sound card do you use?

3. To use a hotmail account, with any email program you must be using the paid for service. Are you?

---

### Post by ceezax on 2007-03-17
what do u mean by paid ?? can u explain more ??

more over that i just got this pc of my friend and i don't know the make of the video 

or the audio card

---

### Post by ceezax on 2007-03-17
by the way , i need to write something in arabic but i can't do that ?? 

i went to the layout tab and added the arabic but i still don't know how to write

in arabic or how to switch between english and arabic

---

### Post by Kateikyoushi on 2007-03-17
Copy the following 2 commands to terminal, Applications > Acessories > terminal and post their output here. then we know what video adapter and soundcard do you use.

```
lspci | grep VGA
lspci | grep audio
```

Hotmail can be reached only through the webpage unless you pay for it.

---

### Post by ceezax on 2007-03-17
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)


01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]

what about the arabic layout ?

---

### Post by mrmonday on 2007-03-17
There are 3 different types of hotmail account:

[LIST]
[*]The free account
[*]A plus account
[*]A premium account
[/LIST]

The second two, you pay a yearly subscription fee. If you signed up for a free account, you can't download your email. If you use a paid for account, ( if you can download your mail in windows), I will look to see if I can find out how to for you.

I will look now for how to find your graphics card/ sound card make.

---

### Post by mrmonday on 2007-03-17
What resolution are you using?

What resolution are you meant to be using?

How are you trying to change your resolution?

---

### Post by Kateikyoushi on 2007-03-17
To solve the video problem try the following.

[CODE]sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo nano /etc/X11/xorg.conf[/QUOTE]
This creates a backup of your xorg.configuration and opens it for editing.

Then look for a line
> DefaultDepth    24

Change the 24 to 16 then CTRL+X to exit Y to save the changes, and CTRL+ALT+Backspace to restart X.

---

### Post by ceezax on 2007-03-17
hi there

i opened xorg.conf and it's default depth already 16  ??? i just want to edit the resolution

---

### Post by ceezax on 2007-03-17
why i still have no reply ??????? any expertise here ?????????????////

---

### Post by Kateikyoushi on 2007-03-17
Show us your xorg.conf

```
cat /etc/X11/xorg.conf
```

---

### Post by ceezax on 2007-03-17
Section "Screen"
        Identifier      "Default Screen"
        Device          "S3 Inc. VT8375 [ProSavage8 KM266/KL266]"
        Monitor         "Generic Monitor"
        DefaultDepth    16
        SubSection "Display"
        SubSection "Display"
                Depth           1
                Modes           "4095x4095" "960x960" "960x720" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "4095x4095" "960x960" "960x720" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "4095x4095" "960x960" "960x720" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "4095x4095" "960x960" "960x720" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "4095x4095" "960x960" "960x720" "800x600" "640x480"
        EndSubSection
        SubSection "Display"

---

### Post by mrmonday on 2007-03-18
What resolution are you mant to be using? The ones you have seem quite odd? If you don't know what size is your screen, is it LCD?

---

