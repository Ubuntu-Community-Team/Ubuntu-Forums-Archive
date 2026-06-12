---
title: "How do u run windows IN ubuntu?"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by captain_conrad on 2008-04-12
hi. im the newest nubee to ubuntu and I have seen many many really awesome effects that it is capable of on youtube. one of them is running microsoft windows IN ubuntu in its own little window, and still having wobbly windows and bendy and stretchy windows being used on it.
How on earth do u enable those? what are the requirements
I have an Ecer extensa 7620, ATI radeon HD 2400 XT, 2gbram,intel centrino dual core 1.66, but the damn thing is locked on vista. I run vista or ubuntu (using super grub disk)
Have to use windows because I have to use autodesk autocad
any help will be appreciated
thanking you in advance
captain conrad

---

### Post by Inxsible on 2008-04-12
You can run Windows thru VMWare or VirtualBox. But I am not sure if you will get the compiz functionalities, as I have never used windows under Ubuntu.

Its worth a try tho :)

---

### Post by smartboyathome on 2008-04-12
You don't get the compiz effects with Windows, as it is technically running in a virtual machine, separate from Ubuntu. Virtualbox has that seemless feature, though, which lets you use Ubuntu and Windows apps seemlessly with each other.

---

### Post by Bölvaður on 2008-04-12
After installing Ubuntu you can go to Add/Remove and install Virtualbox with 2 clicks.
After that you make virtual harddisk drive in Virtualbox and then you have the annoying waiting while you are installing Windows on the Virtualbox.
But it is very simple to do :)

---

### Post by Inxsible on 2008-04-12
> **Bölvaður said:**
> ..... and then you have the annoying waiting while you are installing Windows on the Virtualbox.
LOL. Annoying is right !!!

---

### Post by atomkarinca on 2008-04-12
I guess op is talking about Wine. It's not Windows IN Ubuntu but you can run some of the Windows softwares through it. You can see some of those [here]("http://appdb.winehq.org").

---

### Post by Inxsible on 2008-04-12
> **atomkarinca said:**
> I guess op is talking about Wine.

Maybe, maybe not !! :confused:

---

### Post by HermanAB on 2008-04-12
I can second Virtualbox.  It is very easy to install and works well with Windwos XP.

I also use Cross Over from Codeweavers for certain Windows applications.  Wine is Free, but Cross Over is so much better, that it is worth the expense [http://www.codeweavers.com](http://www.codeweavers.com)

Cross Over is so good, I'm using it in a military project.

Cheers,

Herman

---

### Post by shivam.seth on 2008-04-12
WINE is a really good application which provides Windows like API for certain applications to work. It does not support AutoCAD so I think its useless for you.

VirtualBox and VmWare are applications which can allow you to create a virtual drive and then install Windows on it as you would install it normally on your disk. You can install any Windows software over that virtual drive including AutoCad also (I haven't tried it but i think it should work well too...).

You won't get Compiz like desktop effects in your Windows installation in Ubuntu because VirtualBox and other similar softwares just provide a virtual drive but what is running on these virtual drive is your Windows which does not support any such effects.

Using VirtualBox etc., you can definitely work on Windows within Ubuntu but the application will run really slow in it.....n huge softwares like AutoCAD might respond even slower. So you can try VirtualBox but may be its better for you to dual boot Windows along with Ubuntu so as to use AutoCAD. 

You can also try open-source CAD applications for Linux such as QCAD but don't expect it to be as good as AutoCAD because its not a commercial software.

---

### Post by captain_conrad on 2008-04-12
wow thank u guys SO much!
my silly laptop is locked on vista. Windows are clearly taking the whole world domination thing to a whole new level, locking laptops onto vista. I had an absolute NIGHTMARE trying to install XP... (and failed)
SO im currently doing dual boot with vista and Ubuntu. And im using autocad because iim an autocad student. So it's all mickey mouse 2d stuff right now, the hectic 3d stuff only starts next year.

So Is it possible to have vista on its own partition, ubuntu on its own partition, and windows XP on a virtual drive inside this virtualbox thing (btw what is that and where can i get it?) inside ubuntu, WITH autocad2008 running in Xp in virtualbox in ubuntu? that will seriously rock my world to the max!

oh and what about Autocad REVIT 2008? we're getting that for free from my college, its a 3d architecture program for buildings, and the vids i've seen about it are pretty hectic. Will that run in XP in virtualbox in ubuntu?

---

### Post by Inxsible on 2008-04-12
> **captain_conrad said:**
> .

So Is it possible to have vista on its own partition, ubuntu on its own partition, and windows XP on a virtual drive inside this virtualbox thing (btw what is that and where can i get it?) inside ubuntu, WITH autocad2008 running in Xp in virtualbox in ubuntu? that will seriously rock my world to the max!

 Yes you can have vista, ubuntu and xp running on different partitions.

Using Autocad under Virtualbox will be very slow as mentioned before. You would be better off, having a triple boot of Vista, ubuntu and xp

---

### Post by captain_conrad on 2008-04-12
triple boot won't work because this stupid laptop is somehow locked on vista, in the same way that u would lock a phone on vodacom or lock it on mtn, etc. windows are really trying to be like pinky and the brain now

so can i have the dual boot with vista and ubuntu, and then this virtualbox virtual drive thingie with XP "inside" ubuntu?

and what is virtualbox and where can i get it? I found vmware on that list thingie but no virtualbox

---

### Post by Inxsible on 2008-04-12
> **captain_conrad said:**
> triple boot won't work because this stupid laptop is somehow locked on vista, in the same way that u would lock a phone on vodacom or lock it on mtn, etc. windows are really trying to be like pinky and the brain now

so can i have the dual boot with vista and ubuntu, and then this virtualbox virtual drive thingie with XP "inside" ubuntu?

and what is virtualbox and where can i get it? I found vmware on that list thingie but no virtualbox```
sudo aptitude install virtualbox
``` should do it, provided you have universe and multiverse enabled.

---

### Post by captain_conrad on 2008-04-12
can i have the dual boot with vista and ubuntu, and then this virtualbox virtual drive thingie with windows XP "inside" ubuntu?




I tried typing that into the terminal but it says this:


Couldn't find any package whose name or description matched "virtualbox"



but hang on. Im on internet on a desktop, with the laptop with the ubuntu next to me. No internet on the laptop. (Yet...)

---

### Post by captain_conrad on 2008-04-12
whats universe and multiverse?

---

### Post by Inxsible on 2008-04-12
> **captain_conrad said:**
> can i have the dual boot with vista and ubuntu, and then this virtualbox virtual drive thingie with windows XP "inside" ubuntu?




I tried typing that into the terminal but it says this:


Couldn't find any package whose name or description matched "virtualbox"



but hang on. Im on internet on a desktop, with the laptop with the ubuntu next to me. No internet on the laptop. (Yet...)
So you ran the command on a Windows box ?
You need to execute the command on the ubuntu machine and yes you need to have an internet connection.

---

### Post by Inxsible on 2008-04-12
> **captain_conrad said:**
> whats universe and multiverse?Universe and Multiverse are additional repositories which has software in it.

You can enable them by going to System>>Administration>>Software Sources. On the Ubuntu Software tab, check mark all the 4 boxes and then hit Close and then Reload.

Of course you will need the internet to do this too.

---

### Post by Oldsoldier2003 on 2008-04-12
> **smartboyathome said:**
> You don't get the compiz effects with Windows, as it is technically running in a virtual machine, separate from Ubuntu. Virtualbox has that seemless feature, though, which lets you use Ubuntu and Windows apps seemlessly with each other.

VirtualBox Seamless mode is what finally prompted me to trash my windows partition and give complete control to Ubuntu. Viva VMs!

---

### Post by captain_conrad on 2008-04-12
hahahahahahahaha no luckily im not that dumb, of course i typed the command into the ubuntu terminal on the ubuntu machine.

whats inuverse and multiverse?

---

### Post by Inxsible on 2008-04-12
> **captain_conrad said:**
> hahahahahahahaha no luckily im not that dumb, of course i typed the command into the ubuntu terminal on the ubuntu machine.

whats inuverse and multiverse?I am sorry man !!

It was just that you mentioned you are on a desktop and ubuntu is on the laptop.

I explained universe and multiverse in my earlier post

---

### Post by Oldsoldier2003 on 2008-04-12
> **captain_conrad said:**
> hahahahahahahaha no luckily im not that dumb, of course i typed the command into the ubuntu terminal on the ubuntu machine.

whats inuverse and multiverse?

Universe and Multiverse are repos where you can get additional software that is not directly maintained as part of the default Ubuntu Installation. You can add the repos by going to System>Adminstration >Software Sources and enabling them on the first tab

---

### Post by the8thstar on 2008-04-12
I have used VirtualBox with XP. It works very well, and given your current configuration, speed shouldn't be a problem.

I would like to slip one word of warning though: at this point in time, neither VirtualBox or VMWare Server/Player support 3D 'hungry' applications. This means that you can't hope to run games on your XP install within Ubuntu. The results can be disastrous, trust me.

Now, check if Autocad has specific hardware/software requirements before you install it. 

Other applications using low level graphics, such as MS Office run smoothly.

---

### Post by shivam.seth on 2008-04-12
Being a totally new user, I think you deserve a better explanation for multiverse and universe repositories and here it comes....

In Ubuntu, you can install any compatible software directly from internet. You don't have to search for it yourself. Ubuntu maintains something called repositories for all its softwares. Repositories, as the name suggests, are locations where all the software is stored or linked to. Multiverse and Universe are the names of two such Ubuntu repositories. Medibuntu is another such repository.

You can use your **synaptic package manager** or use the command **apt-get** to install any of the available softwares onto your computer automatically. The only condition here is that these repositories which are the software sources for your requested software, are disabled by default and you need to enable them.


For enabling these repositories, either you can check against these rep. in the synaptic package source list as explained in previous posts or if you want to do it on command line then you can open a **terminal** and type 

```
[COLOR="SeaGreen"]sudo gedit /etc/apt/sources.list[/COLOR]
```

A file named sources.list will open for editing. You can read the comments in the file to know what it is. 

**[COLOR="DarkOrange"]#[/COLOR]** is used for commenting in this file. So you need to remove **[COLOR="DarkOrange"]#[/COLOR]** before the address of the rep. you want to enable. Remove **[COLOR="DarkOrange"]#[/COLOR]** against the multiverse and universe repositories. Save the file and exit.

Then goto synaptic package and search for your software and install it.

---

### Post by captain_conrad on 2008-05-09
ok wow this is all quite a bit to take in
anyways
I have just recently installed the new ubuntu hardy 804 version and all is ok except my compizfusion won't work! man its like taking two steps forward and one step back

last time with the old gutsy gibbon ubuntu 7.10, when i right click on the desktop and select change desktop background, and then go to visual effects tab, it would not let me select anything other than "NO effects".

Now, it will select custom and all the other options, but then it comes with some message about compiz package not being able to work

what now?

---

### Post by Afkpuz on 2008-05-09
Simple talk:

**To run a single windows program within ubuntu:**
 you need to use a program called wine.  Goto Applications>Add/Remove and search for wine.  Install it.
Then, find the .exe file and right click on it.  Select "open with..." and choose wine.  If wine is able, it will try to run the program.  Alternately, you can run wine from the command line with
```
wine filename
```



**To run the entire windows operating within ubuntu:**
You'll need to use some sort of virtual environment, like VMware or Virtual box.  Virtualbox is found in the repositories.  You'll also need a copy of windows.  So, using virtual box, you would first set up virtual box by create a virtual partition, tell it which CD drive to use, etc.  then, turn on virtual box and install XP within it like you would install on a clean system.  It basically emulates a blank computer for XP to install.  Then, when you start virtualbox, XP will boot up within windows.  If you need specific help here, I'd be glad to give it.

---

### Post by Tburg on 2008-05-09
*_So Is it possible to have vista on its own partition, ubuntu on its own partition, and windows XP on a virtual drive inside this virtualbox thing (btw what is that and where can i get it?) inside ubuntu, WITH autocad2008 running in Xp in virtualbox in ubuntu? that will seriously rock my world to the max!_*


You should be able to create partitions with Partition Magic.
Give it a shot and see.

---

### Post by lswest on 2008-05-09
also, virtualbox can be found here: [http://virtualbox.org/](http://virtualbox.org/) (ironically) :P (the Open Source Edition without USB support is available from the repos though)

---

### Post by captain_conrad on 2008-05-10
u guys rock! im gonna go try all this out and I will report back asap

---

### Post by Afkpuz on 2008-05-14
virtualbox is also found in the repositories.  To install, open a terminal and paste this is in

```
sudo apt-get install virtualbox
```

Then, you'll find an icon in the Applications>System Tools

---

