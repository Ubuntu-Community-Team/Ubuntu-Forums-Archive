---
title: "[SOLVED] installing adobe flash player in feisty 7.04 (64-bit)"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by jake16424 on 2007-08-12
i have the file downloaded i extracted and i followed the instructions, but how do i navigate to a file from the terminal? O_O how does that work? cause, i can't figure it out, i need to get to install_flash_player_9_linux 

there, its in its own directory, i tried what i thought would make it work, but it didn't , ,now i need help, those who help will get :popcorn:

---

### Post by benerivo on 2007-08-12
Firstly, if you're using Firefox then it will install flash automatically now. Just try going to a flash site such as youtube and trying to play a video.

To navigate to a file in any terminal, use the cd command. For example the command ```
cd /home/ME/pics
``` would take to me my pics folder. Or you may drag a file icon in to the terminal window and you might be presented with some options (such as cd).

---

### Post by jake16424 on 2007-08-12
> **benerivo said:**
> Firstly, if you're using Firefox then it will install flash automatically now. Just try going to a flash site such as youtube and trying to play a video.

To navigate to a file in any terminal, use the cd command. For example the command ```
cd /home/ME/pics
``` would take to me my pics folder. Or you may drag a file icon in to the terminal window and you might be presented with some options (such as cd).

sweet thankyou, im going to try to get to the installer with that, then follow there instructions on there site for the install, :KS

---

### Post by benx009 on 2007-08-12
> **jake16424 said:**
> i have the file downloaded i extracted and i followed the instructions, but how do i navigate to a file from the terminal? O_O how does that work? cause, i can't figure it out, i need to get to install_flash_player_9_linux 

there, its in its own directory, i tried what i thought would make it work, but it didn't , ,now i need help, those who help will get :popcorn:

what i always do to install flash is just go to a website that needs flash to run (like youtube) and wait for firefox to say "additional plugins are required to display this page"  (or something like that) then i just click "install missing plugins" and proceed with installing flash that way.

---

### Post by jake16424 on 2007-08-12
> **benx009 said:**
> what i always do to install flash is just go to a website that needs flash to run (like youtube) and wait for firefox to say "additional plugins are required to display this page"  (or something like that) then i just click "install missing plugins" and proceed with installing flash that way.

just went to the video page of myspace,, nothing popped up that said additional plugins required, it just says where the video should be, that i need to install the latest version of macromedia flash player:confused:

---

### Post by Arisna on 2007-08-12
Some websites don't trigger the Flash installation prompt.  If you want to go this route, I suggest searching the Internet for "flash games" or similar and poking around until you get the prompt you want to see.

---

### Post by jake16424 on 2007-08-12
> **Arisna said:**
> Some websites don't trigger the Flash installation prompt.  If you want to go this route, I suggest searching the Internet for "flash games" or similar and poking around until you get the prompt you want to see.

did what you said, got a page to say i need to install missing plugins,, then it said no sutable plugins found, >=(

i have the installer on my desk top, i just need to know how to install the thing,, pleaaaseeee????

---

### Post by benerivo on 2007-08-12
You can install flash using synaptic from the main menu (this method is not only the easiest but also keeps your version of flash updated).
or...
If you have downloaded to your desktop, then extract this compressed archive, and then in any terminal type the full directory path it has extracted to, such as  ```
cd /home/MYNAME/desktop/flash-installer
``` then type```
./flashplayerinstaller
``` or whatever it calls the file in the new folder. It should then automatically run an installation program.

---

### Post by jake16424 on 2007-08-12
> **benerivo said:**
> You can install flash using synaptic from the main menu (this method is not only the easiest but also keeps your version of flash updated).
or...
If you have downloaded to your desktop, then extract this compressed archive, and then in any terminal type the full directory path it has extracted to, such as  ```
cd /home/MYNAME/desktop/flash-installer
``` then type```
./flashplayerinstaller
``` or whatever it calls the file in the new folder. It should then automatically run an installation program.

as i am unformiluar with the file system, is there a way i can find the directory where my file is?:confused:

---

### Post by jake16424 on 2007-08-12
jake@jake-desktop:~$ cd /jake/desktop/install_flash_player_9_linux
bash: cd: /jake/desktop/install_flash_player_9_linux: No such file or directory
jake@jake-desktop:~$ 

i tried and thast all i got =(

---

### Post by benerivo on 2007-08-12
close but no cigar - i know the feeling

try this...

```
cd /home/jake/Desktop/install_flash_player_9_linux
```

then

```
./flashplayer-installer
```

---

### Post by eapache on 2007-08-12
/home/username/Desktop

is the path to your desktop (caps are important)

---

### Post by jake16424 on 2007-08-12
> **benerivo said:**
> close but no cigar - i know the feeling

try this...

```
cd /home/jake/Desktop/install_flash_player_9_linux
```

then

```
./flashplayer-installer
```

grrr



ERROR: Your architecture, \'x86_64\', is not supported by the
       Adobe Flash Player installer.

jake@jake-desktop:~/Desktop/install_flash_player_9_linux$ 	](*,)	](*,)




ahh, where do i find one that is X86_64bit supportave? O_O](*,)](*,)](*,)](*,)](*,)

---

### Post by jake16424 on 2007-08-12
grrr



ERROR: Your architecture, \'x86_64\', is not supported by the
Adobe Flash Player installer.

jake@jake-desktop:~/Desktop/install_flash_player_9_linux$




ahh, where do i find one that is X86_64bit supportave? O_O

---

### Post by jake16424 on 2007-08-12
i need someone to hlep me with a macromedia installation. only if you have a few moments, to help me out. IM me, as its faster, and i will in return post it in my previous post of macro install, so that others may get help

IM name, is [email]Jacob16424@yahoo.com[/email]

---

### Post by eapache on 2007-08-12
I don't think flash runs on 64 bit FF. Try this post [here]("http://ubuntuforums.org/showthread.php?t=425672") .

---

### Post by jake16424 on 2007-08-12
> **eapache said:**
> I don't think flash runs on 64 bit FF. Try this post [here]("http://ubuntuforums.org/showthread.php?t=425672") .

i downloaded it, it didnt do anyhting, it unzipped, and then it sat there like a bump on a log, i clicked it,, and poked it with my mouse, and nothing said "RUN IN TERMINAL"

O_o

---

### Post by aysiu on 2007-08-12
Assuming you have it downloaded and extracted to your desktop, paste these commands into the terminal: ```
cd ~/Desktop/nsplugin\ wrapper\ install
chmod +x nspw\ install
./nspw\ install
``` Please **paste** the commands in. Do not retype them.

---

### Post by jake16424 on 2007-08-12
> **aysiu said:**
> Assuming you have it downloaded and extracted to your desktop, paste these commands into the terminal: ```
cd ~/Desktop/nsplugin\ wrapper\ install
chmod +x nspw\ install
./nspw\ install
``` Please **paste** the commands in. Do not retype them.

jake@jake-desktop:~$ jake@jake-desktop:~$ cd ~/Desktop/nsplugin\ wrapper\ install
bash: jake@jake-desktop:~$: command not found
jake@jake-desktop:~$ bash: cd: /home/jake/Desktop/nsplugin wrapper install: No such file or directory
bash: bash:: command not found
jake@jake-desktop:~$ jake@jake-desktop:~$ 
bash: jake@jake-desktop:~$: command not found
jake@jake-desktop:~$ 
jake@jake-desktop:~$ 


thats what i got O_o, no clue what it means, beside it didnt find what it needed to.. :(

---

### Post by misfitpierce on 2007-08-12
nspluginwrapper gets flash working within 64 bit firefox... There is an autoscript somewhere on these boards search it

---

### Post by jake16424 on 2007-08-12
> **misfitpierce said:**
> nspluginwrapper gets flash working within 64 bit firefox... There is an autoscript somewhere on these boards search it

what's auto script?

---

### Post by aysiu on 2007-08-12
```
jake@jake-desktop:~$ jake@jake-desktop:~$ 
``` There's something seriously wrong here, and I think that should be addressed before you try installing Flash.

Why does this appear twice? Why does bash think your username is a command? This is weird.

---

### Post by jake16424 on 2007-08-12
idk, i just ran it again..

this is what i got this time

jake@jake-desktop:~$ cd ~/Desktop/nsplugin\ wrapper\ install
bash: cd: /home/jake/Desktop/nsplugin wrapper install: No such file or directory
jake@jake-desktop:~$ 


i feel utterly useless when it comes to commands,,, i dont know,, how there supposed to look,, im a windows user,, X_X... i feel like roadkill,

---

### Post by aysiu on 2007-08-12
Well, we're resorting to the command-line only because double-clicking the script did nothing. This is what *ordinarily* happens:
1. Download the file.
2. Double-click it.
3. Click the extract button.
4. See the new folder (which is supposed to be called *nsplugin wrapper install*
5. Double-click the *nspw install* file
6. A prompt will ask if you want to run it in the terminal. Click *Run in Terminal*
7. Watch the script execute

For some reason, you are not getting the *Run in Terminal*
Based on the *No such file or directory* output above, it appears you don't even have an *nsplugin wrapper install* folder.

Are you sure you unzipped the .tar.gz file to your desktop?

---

### Post by jake16424 on 2007-08-12
just started typing random "what i thought was a file location" and things started installing,, i scrolled up to what it was that started installing and it was the flash plugin :D whheeeee,,, haha,, im lucky,, :guitar:

---

### Post by aysiu on 2007-08-12
Awesome!

So it works?

---

### Post by jake16424 on 2007-08-12
YES AT LONG LAST,,, but i still don't have audio cause i cant get my drivers to work,, ><,,, haha,, one thing after another,, hehe,,, owell.... yes it plays videos now,, from web-based interfaces,, thank you all. =D:popcorn::KS

---

### Post by aysiu on 2007-08-12
That's wonderful. Unfortunately, I won't be much help with the new audio thread you create.

---

### Post by jake16424 on 2007-08-12
> **aysiu said:**
> That's wonderful. Unfortunately, I won't be much help with the new audio thread you create.

haha,, no worries,, thank you much for the help =D

keep on helping your doing a good job,, haha..:guitar:

---

