---
title: "Driver Installation for the Linux Impaired"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by reedness on 2007-04-17
Wow, I am so glad that I never have to purchase another Microsoft product again.  Anyway, here's my issue.  I've been able to install things from the add/remove programs feature and from the Synaptic Package Manager.  Those are quite easy.  I have also used the terminal which is possible for me when I view the forums and just copy and paste what I see here.  I've kind of paid attention to what the commands sort of actually do, but I am still new and don't really quite get it.  I've read some tutorials and stuff and there is a lot to understand.

Ok, so I want to install my WinTV PVR USB 2 and I read some threads here that take me to other sites, and I got this driver from this guy's site, I think his name is Bill Isely.  I've downloaded the driver which has been just sitting on my desktop for a few days now.  It is a tarball.  I've read pages and pages of how to install the damn thing, I've read the "readme" files when I open the thing and every thing I've read assumes that one knows how to install this stuff.  It's talking about firmware and all kinds of stuff that I just don't quite get.  I will soon, but I am not there yet.  I need your help.

Also, I think Myth TV is having problems because when I install other things from synaptic, it will give me errors regarding Myth TV so I uninstalled Myth TV.  IvTV was one of the things I installed that gave me an error.  Anyway, I guess what I am hoping for here is plain instructions and better yet, code to copy and paste to get this thing working.  :D 

Your help is very much appreciated.  Thanks again!!!

---

### Post by SOULRiDER on 2007-04-17
Im guessing that the tarball has to be compiled, check out thsi guide on compiling, you can apply it to everythign you download :)

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

It would be a good idea to post the tarball too so we can try and give you further help. 


I dont know if you had seen this before, but theres  a page int he wiki on how to get MythTV working, check it out. 

[https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

---

### Post by reedness on 2007-04-17
I got the driver here.  [http://www.isely.net/pvrusb2/download.html](http://www.isely.net/pvrusb2/download.html)  The top one.  It's supposed to be the newest.  Thanks for your help.  I have to run, but I'll be back tonight to check out what you posted.  Thank you!  :)

---

### Post by reedness on 2007-04-18
I've been reading all kinds of instructions that were in those links.  I found some stuff that I liked in the repositories and I selected what I wanted.  It gave me what looked like commands to type.  I kept getting "bash" something about not recognizing deb command.

Anyway, I followed the instructions on the tar -jxvf file.bz2 command AFTER I figured out to switch to the desktop directory.  All it did was put an identical folder (to the tarball) on my desktop.  Now that link you gave me is talking about configure, make, and reading the readme that came with my driver.  The readme says to make it close to the kernel.  All I'm thinking is Colonel Sanders.  *Sigh.  :(   I really want to get this.  I need more time I guess.  I don't ever want to go back to Windows, so I'm not giving up!!!

Wait, here's the kernels   :popcorn:    LOL.  I need help...  :)

---

### Post by Bachstelze on 2007-04-18
You could try this :

```
cd
sudo apt-get install build-essential linux-headers-$(uname -r)
wget http://www.isely.net/downloads/pvrusb2-mci-20070407.tar.bz2
tar xjvf pvrusb2-mci-20070407.tar.bz2
cd pvrusb2-mci-20070407/driver
make
sudo make install
```

This should compile and install the driver. Can't help you further for now since I'm at school but I'll see what I can do whel I'll be back home.

---

### Post by reedness on 2007-04-18
SWEET!  Thanks a lot.  I can't really check right now since I am at work, but you can sure bet that it'll be the first thing I do when I get home!  :)

---

### Post by reedness on 2007-04-18
I think the driver for the TV Tuner was installed.  It seemed like it worked, but I can't get MythTV to work.  I followed the instructions and I had a feeling something wouldn't work.  I went to the OpenBox session, and it just sits there with a blank blue screen.  Those commands all set it up for the Gnome Desktop.  I use KDE.  I installed Kubuntu cuz I like it better.  I almost think I could change the commands in the script to match KDE.  Like switch KDE for GDM, but I don't know what to put where it says gnome in the one script.  Probably KDE, but I don't know.  AHHHHHHHHH!  I think I'll just format tomorrow night or maybe this weekend after Feisty is ready.

---

### Post by Temis on 2007-05-02
[QUOTE=HymnToLife;2472649]You could try this :

```
cd
sudo apt-get install build-essential linux-headers-$(uname -r)
wget http://www.isely.net/downloads/pvrusb2-mci-20070407.tar.bz2
tar xjvf pvrusb2-mci-20070407.tar.bz2
cd pvrusb2-mci-20070407/driver
make
sudo make install
```

Hi, I did this and the end result  in terminal was:
name@name-desktop:~/pvrusb2-mci-20070407/dr
I think I still  have to run the script  fwextract.pl. its on my desktop. But I have no clue how to go about it.
Any hint appreciated.

---

### Post by sailor2001 on 2007-05-02
> **reedness said:**
> I think the driver for the TV Tuner was installed.  It seemed like it worked, but I can't get MythTV to work.  I followed the instructions and I had a feeling something wouldn't work.  I went to the OpenBox session, and it just sits there with a blank blue screen.  Those commands all set it up for the Gnome Desktop.  I use KDE.  I installed Kubuntu cuz I like it better.  I almost think I could change the commands in the script to match KDE.  Like switch KDE for GDM, but I don't know what to put where it says gnome in the one script.  Probably KDE, but I don't know.  AHHHHHHHHH!  I think I'll just format tomorrow night or maybe this weekend after Feisty is ready.

you don't have to reformat..... in synaptics find gnome and install all it's pkgs...now you will have KDE and gnome on your pc... ctrl/alt + backspace will end your session and as it restarts, you have an option of what session you want to go into,  KDE or gnome.....

---

### Post by reedness on 2007-05-02
I have formatted since then, numerous times.  I just feel weird about having things install that don't end up working, then I have all this leftover stuff and I want to know exactly how to do something and blah blah blah.  That's what my head does to me LOL.

Anyway, I posted another thread last night about my computer and I am going to format once more.  I love Linux, but am wondering if I am using the right distro for me.  I just started using it like 4 weeks ago, have formatted countless times.  I am not giving up.  I think I'm going to take a linux class or something.  Read the next paragraph to find out why I am foramatting again.

I just installed Kubuntu Desktop from the Synaptic Package Manager, (was using Gnome and Ubuntu until now) and I now cannot shut down or reboot my computer correctly. All it does is go the shutdown screen with the Kubuntu logo and the status bar stays black and then the screen will flicker, and it stays at a standstill again for like 10 seconds, flickers again, then sits there for 10 seconds, etc... until I hold the power button. The last time I did it my wallpaper wasn't saved. Any suggestions? By the way, I am using Feisty 64-bit if that helps. It was working fine until now. Do I need to uninstall GDM or Ubuntu-desktop or what?

---

