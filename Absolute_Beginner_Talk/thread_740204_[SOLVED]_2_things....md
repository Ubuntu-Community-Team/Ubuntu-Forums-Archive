---
title: "[SOLVED] 2 things..."
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by manicmailman on 2008-03-30
1) which flash player version do i download for gnome-ubuntu 7.10?
    .tar.gz
    .rpm
    YUM

2) i have no sound... i know its a common problem.. i have a:
    SoundBlaster X-fi Xtreme Audio

thanks..

---

### Post by Michael.Godawski on 2008-03-30
usually tar

but use this terminal command to install the flash-plugin 
It is easier

```
sudo apt-get install flashplugin-nonfree -y
```

---

### Post by kbless7 on 2008-03-30
download the tar.gz file. If they have a .deb then download that instead, being that ubuntu is debian linux.

---

### Post by jjgauthi on 2008-03-30
[HERE]("http://ubuntuforums.org/showthread.php?t=739233") is a link to a post concerning the RTL8185 wireless network issue, I think no matter what card you use the steps listed in here would be great to help you solve your networking issue.

If you could post any success or non-success you have we can try and work it out for you

---

### Post by NullHead on 2008-03-30
> **manicmailman said:**
> 1) which flash player version do i download for gnome-ubuntu 7.10?
    .tar.gz
    .rpm
    YUM

2) i have no sound... i know its a common problem.. i have a:
    SoundBlaster X-fi Xtreme Audio

thanks..

Try using this guide [http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg21618.html](http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg21618.html) Note I have not tested it myself.

---

### Post by manicmailman on 2008-03-30
thanks for the terminal code.. i actually did download the tar file first, but didnt know what to do with it... so i used the code and it worked... 

as for the sound... any ideas.. are there drivers around for the x-fi?... 

and im not sure about the network thing.. im not wireless, so i have no problems... it was a flash issue and a sound issue... no network stuff... thanks anyway!

i previously had an audigy and had trouble with sound... i am just so lost when it comes to fixing it... any help would be great!... 

soundblaster x-fi

thanks again..

---

### Post by NullHead on 2008-03-30
For x-fi [http://ubuntuforums.org/showpost.php?p=4617849&postcount=5](http://ubuntuforums.org/showpost.php?p=4617849&postcount=5)

---

### Post by manicmailman on 2008-03-30
ok well this is probably a dumb question... (referring to the link).. but what do i actually type in the terminal?... do i type the "$$" as well or ignore them... 
as well, there was some discussion about 'mistakes'.... could a 'vet' please check out the link and let me know what i need to do/type in terminal?  i really am paranoid about messing ubuntu up (as you can tell)...

---

### Post by Tatty on 2008-03-30
> **manicmailman said:**
> ok well this is probably a dumb question... (referring to the link).. but what do i actually type in the terminal?... do i type the "$$" as well or ignore them... 
as well, there was some discussion about 'mistakes'.... could a 'vet' please check out the link and let me know what i need to do/type in terminal?  i really am paranoid about messing ubuntu up (as you can tell)...

ignore all the $

type the rest,  line by line.

You might want to use Checkinstall instead of "make install" on the final command... [https://help.ubuntu.com/community/CheckInstall?highlight=%28check%29%7C%28install%29]("https://help.ubuntu.com/community/CheckInstall?highlight=%28check%29%7C%28install%29")

---

### Post by Samurai Penguin on 2008-03-30
I have a SoundBlaster Audigy1 card and here's what did it for me:

Setting up Sound:

Volume Control > File > Change Device > select Audigy 1 [SB0090] (Alsa mixing)

Volume Control > Switches Tab > uncheck Audigy Analog/Digital Output Jack

---

### Post by NullHead on 2008-03-30
> **manicmailman said:**
> ok well this is probably a dumb question... (referring to the link).. but what do i actually type in the terminal?... do i type the "$$" as well or ignore them... 
as well, there was some discussion about 'mistakes'.... could a 'vet' please check out the link and let me know what i need to do/type in terminal?  i really am paranoid about messing ubuntu up (as you can tell)...

> **Tatty said:**
> ignore all the $

type the rest,  line by line.

You might want to use Checkinstall instead of "make install" on the final command... [https://help.ubuntu.com/community/CheckInstall?highlight=%28check%29%7C%28install%29]("https://help.ubuntu.com/community/CheckInstall?highlight=%28check%29%7C%28install%29")

what he said [CENTER]/\ 
                      |[/CENTER]
 Also you might want to do ```
sudo apt-get install build-dep alsa-base
``` before attempting the instructions.

---

