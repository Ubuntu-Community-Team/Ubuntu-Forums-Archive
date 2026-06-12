---
title: "UBUNTU GDM doesn't load"
date: 2006-01-20
forum: Absolute Beginner Talk
---

### Post by mishranurag on 2006-01-20
Hi,  I am using UBUNTU 5.10 with latest Kernel. Yesterday I fixed the resolution issue of my computer, where I forced the computer to use the 1280 x 1024 resolution and none other. The system worked fine until today morning when I shut it down. When I restart it now, I can see only the CLI on a black background. Has it happened to anybody before? Can anybody guide me regarding that? or direct me to better forum or HowTo. I would appreciate any help regarding the matter.  Thank You Anurag

---

### Post by dueY on 2006-01-20
Try ```
sudo /etc/init.d/gmd start
``` to start up GNOME.  If that doesn't work you can ```
sudo nano /etc/X11/xorg.conf
``` to edit your X configuration or ```
sudo dpkg-reconfigure xserver-xorg
``` to reconfigure X.

---

### Post by mishranurag on 2006-01-20
I tried the first and the last command, and it didn't help. I haven't tried the second command. What do I need to do after typing the second command. i am a newbie so I don't understand the intricate details of linux, so please explain me. Thanks in advance Anurag   [quote=dueY]Try ```
sudo /etc/init.d/gmd start
``` to start up GNOME.  If that doesn't work you can ```
sudo nano /etc/X11/xorg.conf
``` to edit your X configuration or ```
sudo dpkg-reconfigure xserver-xorg
``` to reconfigure X.[/quote]

---

### Post by dueY on 2006-01-20
Does your xorg.conf have the option of 1280x1024 in it?
```
Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV41 [GeForce 6800]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
```

Like that?

---

### Post by racecat on 2006-01-20
I don't mean to butt in. but I noticed a possible syntax error in your first suggestion, dueY.

Shouldn't```
sudo /etc/init.d/gmd start
```read```
sudo /etc/init.d/gdm start
```I don't mean to second guess anyone, but it kind of glared at me.

Good luck,
Bill

---

### Post by dueY on 2006-01-20
[QUOTE=racecat]I don't mean to butt in. but I noticed a possible syntax error in your first suggestion, dueY.

Shouldn't```
sudo /etc/init.d/gmd start
```read```
sudo /etc/init.d/gdm start
```I don't mean to second guess anyone, but it kind of glared at me.

Good luck,
Bill[/QUOTE]

Racecat is very correct.  It was a typo.

---

### Post by Mustard on 2006-01-20
[QUOTE=mishranurag]I tried the first and the last command, and it didn't help. I haven't tried the second command. What do I need to do after typing the second command. i am a newbie so I don't understand the intricate details of linux, so please explain me. Thanks in advance Anurag[/QUOTE]

One thing that you should learn to do when telling people about your problems is to be more elaborate in your explanations.  In the instance above, you should have described what error messages you received when you ran those commands.  The more detail you give, the easier it is for others to know what is happening.  A descriptions of 'it didn't help' is not enough for people to work with.

I would try looking in your logs for errors.  You can find the logs in the /var/log/ directory.  To get there you type this in console...

```
cd /var/log/
```

Once there you want to look at the Xorg.0.log.  You can display this using this command...

```
cat Xorg.0.log
```

Look through the log for errors messages that might have some relevance to your display problems.  Post the error messages in here, so that others can try to work out what the problem might be.

---

### Post by mishranurag on 2006-01-22
I am sorry for not giving explicit details of my problem. Actually my right hand is broke and I generally avoid too much typing.

Anyways, apart from fixing the resolution issue about which I explained earlier, I also updated the Kernel and some KDE vulnerabilities as was issued by UBUNTU.  When I started my computer, the UBUNTU would appear to load everything and instead of graphical login screen, it showed me a blank screen with CLI. I tried to reboot my comp with older kernel and again it was the same. I tried the  
sudo dpkg-reconfigure xserver-xorg 
and it would lead me to the whole process of setting up screen but bring back to the CLI. I tried  
sudo /etc/init/d/gdm restart 
the box responded with sopping GNome display Manager and Starting GNome Display manager, but again showed me the blank screen with CLI.  With due frustration and forum not working I used s
udo apt-get install ubuntu-desktop 
and the computer responded with ubuntu-desktop already installed and 0 upgraded. Then I tried  
sudo apt-get install kubuntu-desktop 
It installed everything and it gave me a graphical login screen and I could login to my computer with lot more softwares (k stuff) to confuse with. I am right now on my UBUNTU again but with Kubunutu login screen.   Currently I have no problem but I want to remove KUBUNTU, since I don need it. I want to know what caused the problem and how can I fix it.  

Thank You for all the help I can get. 
Anurag  

PS: The file Xorg.0.log is very big. Should I paste its output here?

---

### Post by mishranurag on 2006-01-24
No replies yet ?? :(

---

### Post by mishranurag on 2006-02-01
Hi!
Today I tried to load login screen setup from Gnome, but couldn't. Is it due to the problems which I encountered in past weeks?? Can it be fixed??
Anurag

---

