---
title: "Adding line to beginning of usr/bin/firefox"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by grj23 on 2006-11-14
Hi

So I recently installed ubuntu and it was going great until I installed Flash Macromedia.  Then Firefox would close on numerous websites.  So I discovered that this was a known bug ([https://launchpad.net/distros/ubuntu/+source/flashplugin-nonfree/+bug/62988](https://launchpad.net/distros/ubuntu/+source/flashplugin-nonfree/+bug/62988))
and the answer is to add
export XLIB_SKIP_ARGB_VISUALS=1
to the beginning of usr/bin/firefox

At least I think that was the best solution.  However, I couldn't do it.  I found the firefox file, but could only open it at read only.  Then I tried to switch user to the root user, but I wasn't allowed to for some reason.

Then I tried to install the beta version of macromedia, but couldn't find the directory to copy it into.  Then I tried to change the screen bits and couldn't find that.

](*,) 

It's so frustrating - I know my way around windows, but I guess I don't have a feel for this new operating system.  And it seems like I broke it so easily.  I couldn't even uninstall the flash mediaplayer.  One little click and hours down the drain!

So is there someone out there who can give me a step by step explanation that won't confuse me with endless options and deep geek speak?!

---

### Post by LLRNR on 2006-11-14
Hi. Well actually if you issue ls -il *firefox* somewhere in your /usr/bin folder, you'll notice it's written in blue - that means it's a link to the file in /lib/firefox/firefox. Try and see if you can fix it from there.

Ok, that's just a hunch...

---

### Post by Archmage on 2006-11-14
To edit the file you would need to enter:
```

ALT+F2
gsudo gedit [FILE+PATH]

```

But I would suggest using the second option and simply set your color deep at 24-bit.

---

### Post by Average Joe on 2006-11-14
I am not at a Ubuntu box right now, but what if you try:
> sudo u+w /usr/bin/firefox
Maybe the file is not writable by default.

Also, you can remove the flash plugin by typing:
> sudo apt-get remove flashplugin-nonfree

You can find more about it [here]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox").

---

### Post by grj23 on 2006-11-14
Okay, so how do I set my colour deep at 24-bit (whatever that means)?

---

### Post by LLRNR on 2006-11-14
In your /etc/X11/xorg.conf file, find the section called "Screen" and set DefaultDepth to 24. Here is a part of MY xorg.conf file, it's meant just as a guidance, PLEASE **DO NOT** COPY IT, it wouldn't suit your needs, just see where DefaultDepth gets and replace the number next to it with 24.

```
Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
        Monitor         "MCM 171V"
        **DefaultDepth    24**
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1152x864" "1152x768" "1024x768" "800x600"
        EndSubSection
        .............
EndSection
```

---

### Post by grj23 on 2006-11-14
Okay, that's helpful.  But it also opens as a read only.  How can I get past that?

---

### Post by LLRNR on 2006-11-14
Sorry for the delay ! You need of course to get root privileges to edit it, so in your place I'd just go for 

```
sudo nano /etc/X11/xorg.conf
```

sudo stands for "superuser do" (in Ubuntu you don't get a special root account, and all actions that require root privileges are acquired with sudo);type in your password; and nano just happens to be a text editor I like :) (Ctrl+O to save (=writeOut), then type enter, then type Ctrl+X to eXit); or you can just use gedit.

---

### Post by grj23 on 2006-11-14
Okay, that's very helpful.  Now all I need to know is where I type that bit of code?!  I'm sorry to be so dense - I know this must be really obvious, but I've really only used Ubuntu for 2 days!  This must be some kind of record for breaking it.

---

### Post by LLRNR on 2006-11-14
Look in one of my posts above. There is a "code" fragment taken from my xorg.conf file. **PLEASE DO NOT COPY/PASTE** it, it was meant just an example, so navigate through you xorg.conf file until you see *Section "Screen"*, then look right there for DefaultDepth and type in 24 if it's not already set as 24 bit color-depth.

Take care!

LLRNR

---

### Post by grj23 on 2006-11-14
Hi.  Sorry.  What I meant was the "sudo nano /etc/X11/xorg.conf". 

I can find the xorg.conf no problem, using places-computer-filesystem etc.  And I can find where I'm meant to change the number to 24.  I just couldn't actually change it because of the read only.  Am I supposed to be using some text based command line? If so how do I access it?

Thanks

---

### Post by dannyboy79 on 2006-11-14
if you're entering sudo and the command you should be able to edit and save the file? what happens when you do sudo -i, it should ask you for your password, enter it (even though it looks like you're not typing you still are) then hit enter after you entered your password. now you prompt should've changed from somehting like daniel@UBUNTU:~$ to root@UBUNTU:~#. NOW YOU CAN EDIT ANYTHING TO BE CAREFUL!!!! now at the command prompt, type in gedit /etc/X11/xorg.conf. the file should open, scroll down and find where you want to change the depth and change it. then don't forget to save the file and then close it. once you are finished doing what you needed to do logged in as root, at the command prompt, type in exit, and you'll be back to your user privalages and logged in as you. you can do this by simplly adding sudo at the begining of command to give you temporary root privalages but you keep telling us that the file is still read only so I figured I'd tell you something different so we don't sound like a broken record. good luck, anything along the way doesn't do as I described it and post back what happens or copy and paste the output of what happens. good luck and go get em tiger.

---

### Post by grj23 on 2006-11-14
Hi.  What I mean is how do I open the command prompt.  I don't know where to type the sudo bit.  I've literally been using Ubuntu for 2 days.  In windows you go start-run and type cmd. What do you do in Ubuntu to get to the place where you can do all these wonderful things?!  (Remember this is absolute beginner talk)

---

### Post by dannyboy79 on 2006-11-14
ah, ok, you can either hit ctrl-alt-f2 which will bring up a little box which is like doing a fast command, then you'd type in gksudo gedit /etc/X11/xorg.conf or you can open a terminal session by going to the main menu pull down and under accessories it should say terminal. good luck. i would suggest reading a ubuntu for dummies book or checkout the unofficial ubuntu starters guide here: [http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

---

### Post by grj23 on 2006-11-15
Thank you all very much.  You've been patient and helpful with this absolute beginner!  It's all working now.

G

---

