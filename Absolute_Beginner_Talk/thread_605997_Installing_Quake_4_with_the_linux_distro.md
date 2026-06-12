---
title: "Installing Quake 4 with the linux distro"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by Dapman01 on 2007-11-07
I was wondering if anyone can give me instructions on installing Quake 4 with the Linux distro patch.  I would like to get it step-by-step but i'll take what I can get
thanks

---

### Post by Dapman01 on 2007-11-07
bump

---

### Post by Dapman01 on 2007-11-07
Hi,
I was wondering if someone could get me started on getting native Quake 4 running, I have the package downloaded, but don't know what to do with it.

---

### Post by taurus on 2007-11-07
You probably should ask that question in the Gaming & Leisure section because that's where gamers are hanging out.  In fact, I bet you can find an answer to your question if you look in there.

---

### Post by Dapman01 on 2007-11-07
I have a thread in the Game and leisure section and I'm got getting any help

---

### Post by MrFSL on 2007-11-07
On the rare occasion when you feel that you MUST cross post it would be considerate if you included a link to  your original post.

---

### Post by Maestro23 on 2007-11-07
> **Dapman01 said:**
> I have a thread in the Game and leisure section and I'm got getting any help

Is it a .run file? In a terminal (after you navigate to the directory you downloaded the file to):

> sudo chmod + x filename.run  

./filename.run

*Also here is a Quake 4 for lInux FAQ page: [http://zerowing.idsoftware.com/linux/quake4/](http://zerowing.idsoftware.com/linux/quake4/)

---

### Post by Dapman01 on 2007-11-11
When trying to install the linux quake 4 patch (1.4.2) after I enter the intallation path, it gives me the error 
No write permission to /usr/local.games/quake4
can anyone help me

---

### Post by eldragon on 2007-11-11
run it with sudo.......that location is read only for regular users..

---

### Post by carlosjuero on 2007-11-11
> **eldragon said:**
> run it with sudo.......that location is read only for regular users..
That or change the install location to your home folder.

---

### Post by Dapman01 on 2007-11-11
No matter what I type in it says no write permission

---

### Post by Sockerdrickan on 2007-11-11
sudo sh thefile
start it like that, it should work

---

### Post by Dapman01 on 2007-11-11
patrick@patrick-desktop:~$ sudo sh quake4_linux_1.4.2.x86.run
[sudo] password for patrick:
sh: Can't open quake4_linux_1.4.2.x86.run
patrick@patrick-desktop:~$ 

that is what I get

---

### Post by Dapman01 on 2007-11-11
am I suppose to put the file in a special place...I have it on my desk top

---

### Post by Dapman01 on 2007-11-11
I was wondering if someone coult tell me how to log in a root
I'm still trying to get quake to work, but it isn't.
I understand that it is dangerous, but I really want this game to work
gksudo thunar doesn't work so this is kind of a last resort

---

### Post by Maestro23 on 2007-11-11
> **Dapman01 said:**
> I was wondering if someone coult tell me how to log in a root
I'm still trying to get quake to work, but it isn't.
I understand that it is dangerous, but I really want this game to work
gksudo thunar doesn't work so this is kind of a last resort

Is this the file: quake4-linux-1.4.2.x86.run

I believe I showed you this before.

> sudo chmod +x quake4-linux-1.4.2.x86.run

./quake4-linux-1.4.2.x86.run

---

### Post by Dapman01 on 2007-11-11
yea, that is the file, and I did what you said, but it still gives me the same error
Am I suppose to have the file in a special place,I currently have it on the desk top

---

### Post by Paul820 on 2007-11-11
What is the error? Did you cd to the desktop so it can find the file?
> cd ~/Desktop

---

### Post by Maestro23 on 2007-11-11
> **Dapman01 said:**
> yea, that is the file, and I did what you said, but it still gives me the same error
Am I suppose to have the file in a special place,I currently have it on the desk top

If the file is on your Desktop:

> cd ~/Desktop

ls (lists contents of the Desktop directory, shoulde see your file)


Then run the commands I provided.

Hey Paul820, we meet agian. :smile:

---

### Post by Sockerdrickan on 2007-11-11
chmod +x quake4_linux_1.4.2.x86.run

---

### Post by Dapman01 on 2007-11-11
thank you for your help btw
I did what you said and this is what happened

patrick@patrick-desktop:~$ cd ~/Desktop
patrick@patrick-desktop:~/Desktop$ ls
Desktop                                 Fedora-8-Live-i686.iso
doom3-linux-1.3.1.1304.x86.run          Fedora-8-Live-KDE-i686
doom3-linux-1.3.1.1304.x86.run.torrent  quake4-linux-1.3-sdk.x86.run
patrick@patrick-desktop:~/Desktop$ sudo chmod +x quake4-linux-1.4.2.x86.run
chmod: cannot access `quake4-linux-1.4.2.x86.run': No such file or directory
patrick@patrick-desktop:~/Desktop$ ./quake4-linux-1.4.2.x86.run
bash: ./quake4-linux-1.4.2.x86.run: No such file or directory
patrick@patrick-desktop:~/Desktop$ ls
Desktop                                 Fedora-8-Live-i686.iso
doom3-linux-1.3.1.1304.x86.run          Fedora-8-Live-KDE-i686
doom3-linux-1.3.1.1304.x86.run.torrent  quake4-linux-1.3-sdk.x86.run
patrick@patrick-desktop:~/Desktop$ quake4-linux-1.3-sdk.x86.run
bash: quake4-linux-1.3-sdk.x86.run: command not found
patrick@patrick-desktop:~/Desktop$

---

### Post by Dapman01 on 2007-11-11
sorry, for the last post, I forgot I moved the install file
but I'm still having the same problem though

---

### Post by Maestro23 on 2007-11-11
> **Dapman01 said:**
> thank you for your help btw
I did what you said and this is what happened

patrick@patrick-desktop:~$ cd ~/Desktop
patrick@patrick-desktop:~/Desktop$ ls
Desktop                                 Fedora-8-Live-i686.iso
doom3-linux-1.3.1.1304.x86.run          Fedora-8-Live-KDE-i686
doom3-linux-1.3.1.1304.x86.run.torrent  quake4-linux-1.3-sdk.x86.run
patrick@patrick-desktop:~/Desktop$ sudo chmod +x quake4-linux-1.4.2.x86.run
chmod: cannot access `quake4-linux-1.4.2.x86.run': No such file or directory
patrick@patrick-desktop:~/Desktop$ ./quake4-linux-1.4.2.x86.run
bash: ./quake4-linux-1.4.2.x86.run: No such file or directory
patrick@patrick-desktop:~/Desktop$ ls
Desktop                                 Fedora-8-Live-i686.iso
doom3-linux-1.3.1.1304.x86.run          Fedora-8-Live-KDE-i686
doom3-linux-1.3.1.1304.x86.run.torrent  quake4-linux-1.3-sdk.x86.run
patrick@patrick-desktop:~/Desktop$ quake4-linux-1.3-sdk.x86.run
bash: quake4-linux-1.3-sdk.x86.run: command not found
patrick@patrick-desktop:~/Desktop$

Why did you download the SDK (Software Developers Kit) for Quake 4?  Are you going to be developing additonal mods for Quake?  I don't see the actual game file like I posted in my original post.  No wonder the command is not working.

---

### Post by Dapman01 on 2007-11-11
oh yea, and for the record (for paul) this is becuse I'm trying to install quake 4 on ubuntu, while the packeage starts after I select the install path I get the error
Failed permissions
No write permission to /usr/local/games/quake4

---

### Post by Dapman01 on 2007-11-11
> **Maestro23 said:**
> Why did you download the SDK (Software Developers Kit) for Quake 4?  Are you going to be developing additonal mods for Quake?  I don't see the actual game file like I posted in my original post.  No wonder the command is not working.

I'm just trying to get quake installed for playing
Did I install the wrong thing, if so can you point me to where to download the right thing

Sorry if that is the case

---

### Post by NightCrawler03X on 2007-11-11
There truly is no need to log in as root :P

At your terminal, type:
```

mkdir ~/quake4
mkdir ~/quake4/q4base

```

Insert the CD to the Windows version of your quake4 disc. In it should be a folder named "q4base", containing a bunch of .PK1, .PK2, etc files, copy all of them to ~/quake4/q4base directory

At you terminal, do the following:
```

mv quake4-linux-1.4.2.x86.run ~/quake4
cd ~/quake4
chmod 755 quake4-linux-1.4.2.x86.run
./quake4-linux-1.4.2.x86.run

```

Follow the onscreen instructions. Make sure you tell it to install to ~/quake4
(~ means /home/your-user-name)

After that, type
```

quake4

```

When typing "quake4", you might find that sound doesn't work.
If so, do the following:
```

sudo killall esd
sudo -i
echo "quake4.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
exit

```
NOTE - You need to do this every time you log out/in or shutdown/powerup, because the changes made by these commands are only temporary. There is currently no permanent fix.

You will also most likely find it to be in Spanish. If English is a requirement:
```

gedit ~/.quake4/q4base/Quake4Config.cfg

```
You may not have gedit, if not, just replace "gedit" with the name of any text editor you have.

Search for a string that says 
> 
seta sys_lang

if after that it says "spanish", replace it with "english". Save the file, and you will see quake4 in english whenever you run it.

Adiós

---

### Post by Dapman01 on 2007-11-11
Ok, so I put the file back on my desktop did what you said

patrick@patrick-desktop:~$ cd ~/Desktop
patrick@patrick-desktop:~/Desktop$ ls
Desktop                                 Fedora-8-Live-i686.iso
doom3-linux-1.3.1.1304.x86.run          Fedora-8-Live-KDE-i686
doom3-linux-1.3.1.1304.x86.run.torrent  quake4-linux-1.4.2.x86.run
patrick@patrick-desktop:~/Desktop$ sudo chmod +x quake4-linux-1.4.2.x86.run
patrick@patrick-desktop:~/Desktop$ 
patrick@patrick-desktop:~/Desktop$ ./quake4-linux-1.4.2.x86.run

and I'm still having the same permissions problems
Do you think rebooting into admin would help?
I am willing to risk it

---

### Post by magicman5421 on 2007-11-11
why would you need to reboot into admin? isn't sudo and the like enough for you?

---

### Post by Tyke91 on 2007-11-11
on ubuntu, you *can* log into the root account after enabling it, but it is not necessary at all. 

do you see the "sudo" command in front of many of codes we are giving you? this (plus the password) gives you the full powers of the administrator for the command.

---

### Post by Dapman01 on 2007-11-11
> **NightCrawler03X said:**
> There truly is no need to log in as root :P

At your terminal, type:
```

mkdir ~/quake4
mkdir ~/quake3/q4base

```

Insert the CD to the Windows version of your quake4 disc. In it should be a folder named "q4base", containing a bunch of .PK1, .PK2, etc files, copy all of them to ~/quake4/q4base directory

At you terminal, do the following:
```

mv quake4-linux-1.4.2.x86.run ~/quake4
cd ~/quake4
chmod 755 quake4-linux-1.4.2.x86.run
./quake4-linux-1.4.2.x86.run

```

Follow the onscreen instructions. Make sure you tell it to install to ~/quake4
(~ means /home/your-user-name)

After that, type
```

quake4

```

When typing "quake4", you might find that sound doesn't work.
If so, do the following:
```

sudo killall esd
sudo -i
echo "quake4.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
exit

```
NOTE - You need to do this every time you log out/in or shutdown/powerup, because the changes made by these commands are only temporary. There is currently no permanent fix.

You will also most likely find it to be in Spanish. If English is a requirement:
```

gedit ~/.quake4/q4base/Quake4Config.cfg

```
You may not have gedit, if not, just replace "gedit" with the name of any text editor you have.

Search for a string that says 

if after that it says "spanish", replace it with "english". Save the file, and you will see quake4 in english whenever you run it.

Adiós

patrick@patrick-desktop:~$ mkdir ~/quake4
patrick@patrick-desktop:~$ mkdir ~/quake3/q4base
mkdir: cannot create directory `/home/patrick/quake3/q4base': No such file or directory
patrick@patrick-desktop:~$ mkdir ~/quake3/q4base
mkdir: cannot create directory `/home/patrick/quake3/q4base': No such file or directory
patrick@patrick-desktop:~$ 

is this normal

---

### Post by Maestro23 on 2007-11-11
> **Dapman01 said:**
> Ok, so I put the file back on my desktop did what you said

patrick@patrick-desktop:~$ cd ~/Desktop
patrick@patrick-desktop:~/Desktop$ ls
Desktop                                 Fedora-8-Live-i686.iso
doom3-linux-1.3.1.1304.x86.run          Fedora-8-Live-KDE-i686
doom3-linux-1.3.1.1304.x86.run.torrent  quake4-linux-1.4.2.x86.run
patrick@patrick-desktop:~/Desktop$ sudo chmod +x quake4-linux-1.4.2.x86.run
patrick@patrick-desktop:~/Desktop$ 
patrick@patrick-desktop:~/Desktop$ ./quake4-linux-1.4.2.x86.run

and I'm still having the same permissions problems
Do you think rebooting into admin would help?
I am willing to risk it

Just download the quake file to my /home/username 

This is what I done:

sudo chmod +x quake4-linux-1.4.2.x86.run

./quake4-linux-1.4.2.x86.run

Took me directly to the Insallation screen.

---

### Post by Dapman01 on 2007-11-11
I can get that far.  it's when I get to the install path when I start having the troubles

---

### Post by Maestro23 on 2007-11-11
> **Dapman01 said:**
> I can get that far.  it's when I get to the install path when I start having the troubles

Sorry man, I read the Install notes a little closer, you need:

> A licensed copy of Quake 4 retail for Windows(r) is required.
You will copy the assets files from it and use the CD key.

Do you have that?

---

### Post by Dapman01 on 2007-11-11
Ok, did what nightcrawler said and it's now working 
Thanks everyone for your help

---

### Post by carlosjuero on 2007-11-11
you tend to have to tell the prompt where the file is; if it is in the current folder then add a './' to the command in front of the file name. Ex:
```

sudo sh ./quake4_linux_1.4.2.x86.run

```

What I did was change its permissions to be executable (you can do it like Tux0r says, or just right click the file, select Properties, and then in the Permissions tab make sure that the Allow Execution box is fully checked [click once if it has a single straight line through it]). Then just open the file, if it says someting about being an executable text file select 'Run' - specify somewhere you have write permissions to (at least to test) for the installation.

---

### Post by NightCrawler03X on 2007-11-11
DAPMAN - I've edited my post, there were some contextual errors that were teh reason for your problems based on the fact that you were following my instructions.
Follow them again, precisely.

> **Dapman01 said:**
> patrick@patrick-desktop:~$ mkdir ~/quake4
patrick@patrick-desktop:~$ mkdir ~/quake3/q4base
mkdir: cannot create directory `/home/patrick/quake3/q4base': No such file or directory
patrick@patrick-desktop:~$ mkdir ~/quake3/q4base
mkdir: cannot create directory `/home/patrick/quake3/q4base': No such file or directory
patrick@patrick-desktop:~$ 

is this normal
where it says "mkdir ~/quake3/q3base", that was a typo.
In this post of mine, look where after ~/ it says "quake3". THAT is the typo, it's meant to be "quake4"

so:
```

mkdir ~/quake4/q4base
NOT mkdir ~/quake3/q4base

```

(I made these typos because I originally thought you wanted to know how to install quake3, then when realizing that you wanted to install quake4, I quickly edited my post, but alas, I accidentally forgot some parts I needed to edit, sorry if this caused any confusion)

You don't need root permissions because following my instructions, you will be installing quake4 to your /home/user directory.

---

### Post by Dapman01 on 2007-11-12
So, what do I need to type into a fresh terminal in order for it to run

---

### Post by NightCrawler03X on 2007-11-12
You need to do what I've said in my first post in this thread.

---

### Post by Dapman01 on 2007-11-12
No, I have it installed I just need the run command
I was playing it by going home/quake4 and clicking quake4.x86 and it was working fine
but than I enabled anti-aliasing and now that way just doens't work.  I'll double click and nothing happens.  Nothing happens with right click open either

---

### Post by Dapman01 on 2007-11-12
I installed and ran quake 4 fine so I went to the options menu and enabled anti-aliasing.  THe problem is that now Quake 4 won't run anymore.  Does anyone know what I can do

---

### Post by luisromangz on 2007-11-12
You can try looking for a quake4 in your home folder (it will probably be a hidden folder, starting with .), and there should be a config file. You could try modifiying it, or delete the folder and let Quake IV recreate its config.

---

### Post by NightCrawler03X on 2007-11-13
Sorry, but I'm afraid I don't know how to help you.

The file I told you to edit to get it playing in english, try opening that in a text editor and finding something that says anti-aliasing or something, and try disabling it.

---

### Post by stchman on 2007-11-13
> **Dapman01 said:**
> I was wondering if someone coult tell me how to log in a root
I'm still trying to get quake to work, but it isn't.
I understand that it is dangerous, but I really want this game to work
gksudo thunar doesn't work so this is kind of a last resort

In Ubuntu you cannot log in as root.  If you type root as the username the password changes every time the PC boot up.

Now you can run apps as root with a sudo in front but it is dangerous.  I especially recommend NOT using sudo with Firefox.

Linux is very secure but when you use sudo for web apps it can be very insecure.

---

