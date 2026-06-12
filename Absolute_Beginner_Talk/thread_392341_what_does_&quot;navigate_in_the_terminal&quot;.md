---
title: "what does &quot;navigate in the terminal&quot;"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by sameoldude on 2007-03-24
hey, first time to post. i'm liking ubuntu, but there's this thing: i tried to install flash player with the instructions from 
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

there's a part that says:
"#3 Unpackage the file. A directory called install_flash_player_9_linux will be created.
 #4  In terminal, navigate to this directory and type ./flashplayer-installer to run the installer. Click Enter. The installer will instruct you to shut down your browser(s)."

how do i navigate in the terminal, what do they mean?

thanks

---

### Post by Waappu on 2007-03-24
Hi

It means change directory to that dir where you unpack files e.g.```
cd ~/install_flash_player_9_linux
```

---

### Post by Outrunner on 2007-03-24
[http://www.linuxcommand.org/learning_the_shell.php](http://www.linuxcommand.org/learning_the_shell.php) Go to the second chapter (2. Navigation) to learn about moving through files/directories in the terminal.

---

### Post by sameoldude on 2007-03-24
thanks, dudes. i came to the right place to ask.

---

### Post by mlnease on 2007-11-09
Dear Waappu,

Thanks for your response.

The expression 'It means change directory to that dir where you unpack files e.g.' is a little advanced for this 'Absolute Beginner'.  The code 'cd ~/install_flash_player_9_linux' per se copied into the Terminal didn't take me anywhere (though in fact I WAS trying to install flash-player-nine and had followed the previous instructions).

 I don't know e.g. what 'that dir where you unpack files' means.  I don't know how to find a directory in Terminal.  I do know what 'directory' means but am completely unfamiliar with Linux conventions.  I think this is to be expected of Ubuntu users, especially 'Absolute Beginners'?

Thanks again and in advance for your help.

mn

---

### Post by SunnyRabbiera on 2007-11-09
this is why I just do it the easy way... wait till it is in the repo's :D
and it is, flash is available if you know how to look

---

### Post by Maestro23 on 2007-11-09
> **mlnease said:**
> Dear Waappu,

Thanks for your response.

The expression 'It means change directory to that dir where you unpack files e.g.' is a little advanced for this 'Absolute Beginner'.  The code 'cd ~/install_flash_player_9_linux' per se copied into the Terminal didn't take me anywhere (though in fact I WAS trying to install flash-player-nine and had followed the previous instructions).

 I don't know e.g. what 'that dir where you unpack files' means.  I don't know how to find a directory in Terminal.  I do know what 'directory' means but am completely unfamiliar with Linux conventions.  I think this is to be expected of Ubuntu users, especially 'Absolute Beginners'?

Thanks again and in advance for your help.

mn

I agree with Sunny or you can start trying to grasp the concept of the terminal.  The following link will help.

Using the Terminal:  [https://help.ubuntu.com/community/UsingTheTerminal?action=show&redirect=HowToUseTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal?action=show&redirect=HowToUseTheTerminal)

---

### Post by Pumalite on 2007-11-09
Tutorials:

[http://www.linux-tutorial.info/index.php](http://www.linux-tutorial.info/index.php)
[http://www.linux.org/lessons/beginner/toc.html](http://www.linux.org/lessons/beginner/toc.html)
[http://howtoforge.com/taxonomy_menu/1/1/50](http://howtoforge.com/taxonomy_menu/1/1/50)
[http://www.littleigloo.org/tutorial.php3](http://www.littleigloo.org/tutorial.php3)
[http://www.ubuntugeek.com/tag/ubuntu-hacks/](http://www.ubuntugeek.com/tag/ubuntu-hacks/)

---

### Post by mlnease on 2007-11-09
Thanks, Sunny, guess I don't know how to look, being an 'Absolute Beginner'.

---

### Post by mlnease on 2007-11-09
Thanks, Maestro, I've been trying to 'grasp the concept of the terminal' for some time, using 'apt-get', 'gedit' and so on.  I'm afraid this doesn't address my original question, though.  Are these responses meant to be a kind of 'hazing' for non-hackers?  Just curious.

mn

---

### Post by SunnyRabbiera on 2007-11-09
the thing to understand is unlike windows you dont have to look all over heck and creation for new apps, there is a program for you called synaptic package manager that will take care of a great deal of apps for you.
with synaptic you are dealing with one of the largest repositories linux has to offer.
granted there are still programs ubuntu does not have but with any luck with your favorites windows apps you can find alternatives to them.
Of course there is wine too, that can allow you to possibly install your favorite windows applications on linux, but it will NOT work on every app or make it work the way it does in windows.
learn your system, there are plenty of guides out there for you.

---

### Post by Pumalite on 2007-11-09
Later on you can run Windows virtually in Ubuntu through Virtualbox(need 1 GB of RAM though)

---

### Post by Toadmund on 2007-11-09
If your downloaded file is downloaded to your desktop,
'cd Desktop' (without the ' ' ) will bring you to that directory.
Now you can input the command as they say.

Try this in terminal:
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by sisco311 on 2007-11-09
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
[http://ubuntuguide.org/wiki/Main_Page](http://ubuntuguide.org/wiki/Main_Page)

---

