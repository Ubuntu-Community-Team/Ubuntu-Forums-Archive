---
title: "help with conky"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by ITdrummer on 2007-06-26
Hello all,

I have been looking for an application that will run on my desktop and show me my system resources and other vital information.  I stumbled across conky.  Will this app run smoothly with ubuntu? If so, what config changes will be needed, and i hear something about flickering on screen?

I realize that there are a few threads already started on this topic, but the instructions given were vague to say the least.  Anyone know enough about this program to spell it out for a noob? (step-by-step would be great)
 
Thanks!

---

### Post by reset3x on 2007-06-26
> **ITdrummer said:**
> Hello all,

I have been looking for an application that will run on my desktop and show me my system resources and other vital information.  I stumbled across conky.  Will this app run smoothly with ubuntu? If so, what config changes will be needed, and i hear something about flickering on screen?

I realize that there are a few threads already started on this topic, but the instructions given were vague to say the least.  Anyone know enough about this program to spell it out for a noob? (step-by-step would be great)
 
Thanks!


See here... worked great for me... : [http://doc.gwos.org/index.php/Conky_1.4.2](http://doc.gwos.org/index.php/Conky_1.4.2)

---

### Post by Seisen on 2007-06-26
I have used it before also and it has worked fine. The only thing  I had to do was change some of the colors because of my background.

---

### Post by walkerk on 2007-06-26
This is a great how to for conky. It also address flickering.. 
[seldon77's conky thread]("http://ubuntuforums.org/showthread.php?t=205865&highlight=conky")

---

### Post by 5-HT on 2007-06-26
Conky will run nicely with Ubuntu. To eliminate flickering, have conky create its own window and use double buffering. Conky's documentation is quite thorough will answers all the questions you mentioned in your post. 


** Conky config settings (~/.conkyrc)**
For drawing conky in it's own window:
```
own_window 1
```For double buffering:
```
double_buffer 1
```**Xorg config settings (/etc/X11/xorg.conf)**  to enable double buffering:
Append```
 Load   "dbe" 
``` to the module section.

cheers,

---

### Post by shearn89 on 2007-06-26
I'd also recommend setting this in the config file:
```

own_window yes
own_window_type utility
own_window_hints undecorated,below,skip_taskbar,skip_pager

```

Which will make sure it is ONLY on the desktop (not a listed window in the pager).

---

### Post by ITdrummer on 2007-06-26
> **5-HT said:**
> Conky will run nicely with Ubuntu. To eliminate flickering, have conky create its own window and use double buffering. Conky's documentation is quite thorough will answers all the questions you mentioned in your post. 


** Conky config settings (~/.conkyrc)**
For drawing conky in it's own window:
```
own_window 1
```For double buffering:
```
double_buffer 1
```**Xorg config settings (/etc/X11/xorg.conf)**  to enable double buffering:
Append```
 Load   "dbe" 
``` to the module section.

cheers,

Do i need so say again...i am a noob, i have no idea what anything you said meant. I understand its code to be entered into the shell.  But other than hat, im clueless

---

### Post by ITdrummer on 2007-06-26
> **shearn89 said:**
> I'd also recommend setting this in the config file:
```

own_window yes
own_window_type utility
own_window_hints undecorated,below,skip_taskbar,skip_pager

```

Which will make sure it is ONLY on the desktop (not a listed window in the pager).

How do i set things in the config file? What config file?.........::noob::

---

### Post by Seisen on 2007-06-26
Follow this guide it is about the easiest way to do it.

[http://www.ubuntugeek.com/conky-a-light-weight-system-monitor-for-ubuntu-linux-systems.html](http://www.ubuntugeek.com/conky-a-light-weight-system-monitor-for-ubuntu-linux-systems.html)

---

### Post by ITdrummer on 2007-06-26
What is a universe repo? How do i enable it?

---

### Post by shearn89 on 2007-06-26
> How do i set things in the config file? What config file?.........::noob::
Assuming you've installed conky, open a terminal. Then type
```
sudo gedit .conkyrc
```
Then add/change
```

own_window yes
own_window_type utility
own_window_hints undecorated,below,skip_taskbar,skip_pager

```
and
```

double_buffer yes

```
then save (Ctrl-S) and exit (ctrl-q).

Then (still in terminal) type
```
sudo gedit /etc/X11/xorg.conf
```
and add
```
Load "dbe"
``` to the "Section Module"

About the universe repo: go "system -> administration -> synaptic package manager", then "settings -> repositories" and check the box saying "Community maintained...."

---

### Post by ITdrummer on 2007-06-26
thanks, thats what i needed to know. I will try as soon as i get home from work.

Thats what i mean by "step-by-step"  thanks again

---

### Post by 5-HT on 2007-06-26
> **ITdrummer said:**
> Do i need so say again...i am a noob, i have no idea what anything you said meant. I understand its code to be entered into the shell.  But other than hat, im clueless
Did you even read conky's documentation? I told you exactly what needed to be done and which files to enter. Everyone using GNU/Linux and Conky have been new to them at one time or another, but that doesn't give anyone the excuse not to first read the documentation and demand hand holding.

---

### Post by ITdrummer on 2007-06-26
> **5-HT said:**
> Did you even read conky's documentation? I told you exactly what needed to be done and which files to enter. Everyone using GNU/Linux and Conky have been new to them at one time or another, but that doesn't give anyone the excuse not to first read the documentation and demand hand holding.

Regardless of whether or not i read the documentation (which i did by the way), i thought i was doing the exact thing these forums were created for.....SEEKING HELP.  If you call what i did "demanding hand holding" then i guess thats what i am doing. I call it using all available resources.  Please dont be rude when someone asks a question.

---

### Post by bodhi.zazen on 2007-06-26
> **ITdrummer said:**
> Regardless of whether or not i read the documentation (which i did by the way), i thought i was doing the exact thing these forums were created for.....SEEKING HELP.  If you call what i did "demanding hand holding" then i guess thats what i am doing. I call it using all available resources.  Please dont be rude when someone asks a question.

I know the feeling ;)

> **5-HT said:**
> Did you even read conky's documentation? I told you exactly what needed to be done and which files to enter. Everyone using GNU/Linux and Conky have been new to them at one time or another, but that doesn't give anyone the excuse not to first read the documentation and demand hand holding.

I know this feeling too :twisted:

---

### Post by 5-HT on 2007-06-26
> **ITdrummer said:**
> Please dont be rude when someone asks a question. I wasn't trying to be rude, and I'm sorry if it came across like that.
 It's just that these are really high volume forums and the *vast* majority of questions asked have already been asked repeatedly *ad nauseum a*nd the answers are already given*. *
What that does is bury the post of people who have already searched as much as they could and still have a problem that they are unable to solve after trying everything they could find. I find this very unfair to those people.

Usually in posts, people will say: 1)what they've tried, 2)why it doesn't work, and 3)if anyone could point them in a different direction.
In my first post, I gave you everything you needed to know (If someone has installed an operating system completely new to them, I assume that they've at least read  how to edit a file prior to the installation)
Instead of saying "Do I have to repeat that I'm a noob", you could have said what you didn't understand about the directions I gave, the directions in other threads, or conky's official documentation. 

Anyways, hope you get it working.

---

### Post by ITdrummer on 2007-06-26
> **ITdrummer said:**
> 

I realize that there are a few threads already started on this topic, but the instructions given were vague to say the least.  Anyone know enough about this program to spell it out for a noob? (step-by-step would be great)
 
Thanks!

I had researched the topic and read the documentation, but as i said, the instructions were vague.  Yes i was able to install an OS, but it took me literally 3 weeks and even then when i got it working it was sheer luck!  I am just like those you mentioned who have already researched and are seeking others help.

---

### Post by ITdrummer on 2007-06-27
Its all good though. Sorry for being difficult.  All problems fixed! Thanks everyone

---

### Post by 5-HT on 2007-06-28
Glad it's working! :D

---

### Post by ITdrummer on 2007-07-10
Hello, im back.

Ok i got conky running (kinda) but there are a couple of issues im experiencing now.

Attached is the screenshot of what happend when i type 

```

conky

```
[ATTACH]37804[/ATTACH]

I edited my conkyrc.support.gz file to double buffer=yes and i made all the other necessary corrections to the script as described.

My questions are:

1) every conky screenshot ive seen has much more data that fills the entire height of the monitor.  Mine covers a half a best.  Is there data missing?  How do i get more data to show up?

2)When i run:  conky    
in the terminal, the display (as in the attached picture)  stops everytime after it says "writing to single buffer" What does this freezing mean?  Does the command need to stay like this to make the app work?

3) After it is all said and done with, where should my conky files be located?  I have a config file "conkyrc.support.gz" located in my /usr/share/doc/conky/examples  directory.  Should there be another configuration file elsewhere?

4) and lastly (sorry so long),  While writing this post i relized i didnt edit the xorg.conf file  to  :  Load "DBE"  
Will this have caused my problems?

Thanks in advance and i would appreciate any help given.

---

### Post by silent1643 on 2007-07-10
not sure on some of your questions, but this is what i did to install conky, works fine

[http://www.littleubuntu.com/blog/?p=10](http://www.littleubuntu.com/blog/?p=10)

---

### Post by ITdrummer on 2007-07-10
ok, let say that i want to completely erase what ive done and start over.  In windows i would just go to "add/remove programs"  and remove, and if it wasnt displayed in the list i would go to c:/program files/..... and delete the folder that it is located in.

I realize that there is an add/remove option in ubuntu, will this completely remove the conky folder with the config file and leave no trace of conky ever being installed?

I am not giving up just yet, im just preparing myself for what i might have to do.

---

### Post by silent1643 on 2007-07-10
how did you install it in the first place?
check your synaptic package manager and search for conky - from there you can install or remove it 

i wouldn't think you would need to remove then install, just install from synaptic and follow my guide above

---

### Post by alphane on 2007-07-10
Do a search on the forums for the "conky setup and config".

In there you will see *plenty* of conky setups that you can rip (and learn from) to your hearts content.  You can't really screw up your conky install bad enough to demand uninstalling, you simply need to get a good .conkyrc file copied back into your home directory.

As for what you said here:

> ...i've edited my conkyrc.support.gz file...

I'm not quite sure what you've been editing?  I've always edited my .conkyrc file to implement changes using the following terminal command:

```
sudo gedit /home/USERNAME/.conkyrc
```

---

### Post by ITdrummer on 2007-07-10
I installed with 
```

sudo apt-get install conky

```
because i heard that, although possible, installing ubuntu from synaptic is kinda risky.  Not for everyone of course, but with the luck ive been having the past month, it would have made my computer explode, so i went the safe route.

> i wouldn't think you would need to remove then install, just install from synaptic and follow my guide above

It is already installed. I figured it might be best if i completely removed the app & files and started over.

---

### Post by Seisen on 2007-07-10
Do you want me to vnc into your computer and help you setup conky? You sound like your gettting frustrated.

---

### Post by silent1643 on 2007-07-10
why am i getting confused by this thread? :confused:

---

### Post by ITdrummer on 2007-07-10
> **Seisen said:**
> Do you want me to vnc into your computer and help you setup conky? You sound like your gettting frustrated.



That sounds great but i am at work.  You busy after 5:30 CST?  

Im not really frustrated, like i said i used windows for a while, im used to uninstalling and re-installing programs.... :twisted:

it was kind of fun last night while i was editing the config file.  Im new to linux so this is practice for me getting used to the terminal and file system.  

As you can see by the screenshot, i got it to display on the background, there are just a few little tweeks i think i need.  But i did so many things last night that i think it would be best to just start over.

---

### Post by ITdrummer on 2007-07-10
> **silent1643 said:**
> why am i getting confused by this thread? :confused:
i dunno why are you?  I dont think my questions are all that confusing. :)

---

### Post by Seisen on 2007-07-10
> **ITdrummer said:**
> That sounds great but i am at work.  You busy after 5:30 CST?  

Im not really frustrated, like i said i used windows for a while, im used to uninstalling and re-installing programs.... :twisted:

it was kind of fun last night while i was editing the config file.  Im new to linux so this is practice for me getting used to the terminal and file system.  

As you can see by the screenshot, i got it to display on the background, there are just a few little tweeks i think i need.  But i did so many things last night that i think it would be best to just start over.

Thats fine, I will send you a pm when I am on here.

---

### Post by ITdrummer on 2007-07-10
will i need to download any software before you can do that?  Any terminal software?

---

### Post by Seisen on 2007-07-10
just make sure that  you have x11vnc installed.

---

### Post by ITdrummer on 2007-07-10
unless it comes pre-installed with the OS i havent done that yet.  Can i find that through synaptic?

---

### Post by Seisen on 2007-07-10
You should be able to search for it and find it.

---

### Post by ITdrummer on 2007-07-11
Ok, so last night i entered:
 ```

Load   "dbe"

```
 into the glxinfo.conf  Section "Module" and i think i majorly screwed something up.

After i did that, nothing happened, so i restarted my machine hoping that the changes would take effect after a clean reboot, but what do i see.....UBUNTU   B.S.O.D!!  ha ha  
But seriously, Grub loaded, i chose Ubuntu, and it started to load Ubuntu.  It sat there for a few minutes (normal) but then wouldnt go anywhere.

So i tried again and this time i pressed alt+F2 after grub so i can see where it was hanging up.  It got all the way to loading GNOME and when it got to x-window i got a blue screen (i dont remember the message exactly) telling me that something in my Section "Module" in glxconf.info was misconfigured and it wouldnt let me load Ubuntu.  I think i  put the:
```
Load   "dbe"
```
in the wrong place and it screwed up somethin aweful.  Can someone help me?

---

### Post by ITdrummer on 2007-07-11
bump

---

### Post by Seisen on 2007-07-11
You need to add it to your xorg.conf file instead of the glxinfo.conf file

---

### Post by ITdrummer on 2007-07-11
so how do i fix that?  I cant seem to boot into Ubuntu.  I get a blue screen with an error (bsod?)lol

---

### Post by Seisen on 2007-07-11
Can you boot into recovery mode?

---

### Post by ITdrummer on 2007-07-11
Now that i think about it, i DID enter 
```

Load  "dbe"

```
 into xorg.conf because i went into the section labeled "Modules"

---

### Post by ITdrummer on 2007-07-11
bump...help

---

