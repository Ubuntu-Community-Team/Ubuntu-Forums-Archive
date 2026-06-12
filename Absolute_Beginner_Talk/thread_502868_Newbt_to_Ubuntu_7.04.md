---
title: "Newbt to Ubuntu 7.04"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by stefcep on 2007-07-17
Hello All.  I've Ubuntu &.04 installed for about 1 week ago from an iso on a mag cover cd.  I installed it alongside my Windows XPPro system. A few queries:

1. When i select to boot into ubuntu i get an error message which tells me to try to boot with noapic.  i worked out how to do this and I can boot into ubuntu no worries.  Is there something negative about booting this way.  If not how do i make the nopaic option permanent so i don't have to keep editing everytime i boot?

2.  i have downloaded several programs both by synaptic and automatix  For some software  an icon appears in Applications menu but for others i can't work out where the installed software has been put eg the emulators in cross-platform in synaptic.  How can i therefore find out in which directory the executables have been installed? Actually this raises a broader issue about how software is installed in this distro: automating installation via synaptic or automatix might mean less user input from the user but i would prefer feedback from the installer as to where its going to put stuff, and preferably a choice.

---

### Post by Outrunner on 2007-07-17
About the first question, I have a faint idea about how you may go about doing that, but I'm not sure if it's entirely correct so I'll leave it to someone else.

Second Q, I don't think it's a good idea to change where things are installed, the default is the best. And also, there will applications that don't put any shortcuts in the menus, as you've noticed, so you can either make a link to it in the menu or start them via the terminal. You've mentioned emulator, so I assume you installed wine? If so, you can run an .exe file by typing in the terminal
```

wine /path/to/file.exe
```

Yes, wine is generally used in the CLI, but if you want you can start

```
winefile
```

, for a... not very good looking Explorer-type window in which you can open .exe files.

---

### Post by stefcep on 2007-07-17
I am actually emulating old computers and video game systems ie apple II, sega, amiga.  I downloaded these files using synaptic but i don't know what directories they have been put in.

---

### Post by Outrunner on 2007-07-17
Ohh,that. Well, you can simply type the name of the emulator in the terminal and see if a graphical interface appears. If not, and the emulator(s) are CLI only, it should display some information(author, copyright, options, arguments, etc.). If you tell me what you installed, I'll see what information I can find.

---

### Post by 3rdalbum on 2007-07-17
Sometimes the name of the package isn't actually the name of the executable. Amazingly enough, I can't find a link to this tip, but it's quite well-known, so I'll have to be the first to put this topic online :-) I'm going to do a screencast of it :-)

Let's say you install the program "Gmanedit". It doesn't put a link in the menu. So you'd go to Synaptic Package Manager, find Gmanedit again, and right-click it. Select Properties from the contextual menu. Now go to the Installed Files tab. You will see a list of files and folders that the program has created as part of its installation. Any files that are inside /bin/ or /usr/bin, or inside any file path that includes a "/bin/", are executables. So you can type just those names inside the terminal, or add those commands to the menu or to launchers, to run them.

---

### Post by stefcep on 2007-07-17
ok thank you. 
Any ideas on how to make my startup options permanent (Part 1 of my post)

---

### Post by meierfra on 2007-07-17
With respect to question1 : You need to edit the  file /boot/grub/menu.lst. Since your computer will not boot if you mess up this file, you need to back it up first:

Open a terminal (Applications->Accessories>Terminal)

Type 

```
cd /boot/grub 
```

to change to the folder /boot/grub


Type

```
sudo cp  menu.lst menu.lst.backup
```

to backup the file.

Type 
```
sudo gedit menu.lst
```
 
to open the file. Scroll down until you find something like

> title		Ubuntu, kernel 2.6.20-16
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-16root=UUID=a6af4a0e-dd38-4b40-985d-e1e2f76fc5a3 ro noquiet 

initrd		/boot/initrd.img-2.6.20-16 quiet
savedefault

Add   noapic   at the end of  the line  

> kernel		/boot/vmlinuz-2.6.20-16root=UUID=a6af4a0e-dd38-4b40-985d-e1e2f76fc5a3 ro noquiet  

(and don't change anything else) so that it looks like 

>  kernel		/boot/vmlinuz-2.6.20-16root=UUID=a6af4a0e-dd38-4b40-985d-e1e2f76fc5a3 ro noquiet noapic

Save the file and the next boot-up should work automatically

---

### Post by meierfra on 2007-07-17
I fixed  the path for menu.lst in the previous post. It's correct now.

---

### Post by stefcep on 2007-07-18
Thank you.  On my system the "noquiet" and "splash" were  also there.  Any idea what these might do, as I notice you had "quiet" and "splash" were there.

BTW I think its great that there are users like yourselves willing to help in this way.  I was afraid most Linux users were too arrogant to help newcomers.

---

### Post by meierfra on 2007-07-18
About the boot up options:

"noquiet" has the effect that all kinds of messages will be displayed during boot up, telling you what the computer is doing at the time. 

"splash" is used to display an image during boot up, but you need to  install an image first. I have never done that, but here are two links which explain how to do it:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_display_Splash_Image_for_GRUB_menu_on_boot-up]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_display_Splash_Image_for_GRUB_menu_on_boot-up")

[http://users.bigpond.net.au/hermanzone/p15.htm]("http://users.bigpond.net.au/hermanzone/p15.htm")

I know that lots of people have to use "noapic" to be able to boot. But I don't really understand  what is does.

---

### Post by dptxp on 2007-07-18
> **stefcep said:**
> 
BTW I think its great that there are users like yourselves willing to help in this way.  I was afraid most Linux users were too arrogant to help newcomers.

Ubuntu is loved more for its forum support than the OS.

---

