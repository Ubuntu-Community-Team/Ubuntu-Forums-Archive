---
title: "Boot up Windows instead of Ubuntu by default"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by MiThRaZoR on 2006-09-04
When I turn on my computer, I want it to boot straight into Windows. Currently it shows a list of 3 for Ubuntu and at the end is Windows XP. It's highlighted on Ubuntu so after three seconds (I made it do that) it boots into Ubuntu.

Now, I don't want it to boot into Ubuntu like that. Imagine the exact same scene I painted, except with Ubuntu being highlighted, I want Windows XP to be highlighted. So after three seconds if I don't press a button, it'll boot into that.

Understand me?

Now, I've clicked on start then right clicked on 'My Computer' then went to 'Properties'. Went on 'Advanced' tab then under the 'Start Up and Recovery' I clicked on 'Settings'. But on the drop down menu it doesn't show Ubuntu. It just has it on Windows but it still doesn't boot right into Windows.

PS: I have it dual booted.

---

### Post by calvinthomas on 2006-09-04
[http://www.ubuntuforums.org/showthread.php?t=250822](http://www.ubuntuforums.org/showthread.php?t=250822)

HTH

Calv

---

### Post by nickpaton on 2006-09-04
There's a very useful little GUI app GrubEd:

[http://www.ubuntuforums.org/showthread.php?p=1339536]("http://www.ubuntuforums.org/showthread.php?p=1339536")

---

### Post by MiThRaZoR on 2006-09-04
I think I'll stay safe and try to install GrubED.

Question is, how do I install it? It's on my desktop. I extracted it. I double click to install it and tried the terminal, and run. But nothing pops up.

---

### Post by halitech on 2006-09-04
Looks like you need to open a terminal and type

sudo ./install 

then put in your password and follow the prompts from there

---

### Post by MiThRaZoR on 2006-09-04
It says this:
> kudafi@kudafi-desktop:~$ sudo ./install
sudo: ./install: command not found
kudafi@kudafi-desktop:~$


It can't be found. Do I need to do something else?

---

### Post by orb9220 on 2006-09-04
Is the package on your desktop otherwise you have to give the path to the package.

---

### Post by tuxcantfly on 2006-09-04
sudo gedit /boot/grub/menu.lst

find this line:
default         0

change it into
default         3

---

### Post by MiThRaZoR on 2006-09-04
> **orb9220 said:**
> Is the package on your desktop otherwise you have to give the path to the package.

The folder is. But even when I take all the contents out of it and put it on the desktop. It still says the same thing.

---

### Post by nickpaton on 2006-09-05
> **MiThRaZoR said:**
> I think I'll stay safe and try to install GrubED.

Question is, how do I install it? It's on my desktop. I extracted it. I double click to install it and tried the terminal, and run. But nothing pops up.

In the link to the GrubEd HOWTO look in post 7 from Tomosaur:

> Right click, 'Create Launcher'. Name it whatever you like. I just use 'GrubEd'. In the 'command' bit, just type 'sudo sh /home/nick/GrubEd.sh', set the drop down box to 'Application', and click the box which says 'Run in terminal'. Set your icon to whatever, and click ok. Then I just dragged my newly created launcher onto my top Gnome Panel. Left click, and when the terminal pops up, just enter your password normally. Once you exit the script, the terminal will automatically close.

Before then make sure that you have installed it properly to your Home folder & not onto the Desktop, again as detailed in the post.  
Note that Tomo has shown how it is then openened using my Home folder as an example.

---

### Post by omns on 2006-09-05
.

---

### Post by Tomosaur on 2006-09-06
If you still want to install GrubEd, here is how:
Download and unzip the file.
Open up a terminal.
Cd to the directory you extracted the files to.
Type 'sudo ./install'

This should install GrubEd properly, and you can launch it using the provided launcher or just by typing 'gksdo GrubEd' in the terminal.

But yes, it is quicker to just edit menu.lst by hand if you know what to change.

---

### Post by MiThRaZoR on 2006-09-06
> **Tomosaur said:**
> If you still want to install GrubEd, here is how:
Download and unzip the file.
Open up a terminal.
**Cd to the directory you extracted the files to.**
Type 'sudo ./install'

This should install GrubEd properly, and you can launch it using the provided launcher or just by typing 'gksdo GrubEd' in the terminal.

But yes, it is quicker to just edit menu.lst by hand if you know what to change.

OH!! I'm still new to Ubuntu so I'm still learning. Kinda hard. But I hope I get used to it. Don't want to use Windows. While it does feel nice just to go back every now and then.

---

### Post by xpod on 2006-09-06
>  While it does feel nice just to go back every now and then.

ARHHHH...Your kidding surely.I just had to go through one of the maddest re-installs of Xp you could possibly imagine...just to shut the wife up!

As much as i felt good at my overcoming my xp issue after all that time it still riles me that i had to even put it back on the pc....(she who must be obeyed dont do sudo!!)......

I only used windows for a few months and THIS is much more fun.
I just wish i had installed it that very first week when i first
read about it........4 months wasted on virus`s,missing dll`s.
slipstreamed cd`s and wga`s bulls**T baloons....

---

### Post by nickpaton on 2006-09-08
> **xpod said:**
> ARHHHH...Your kidding surely.I just had to go through one of the maddest re-installs of Xp you could possibly imagine...just to shut the wife up!

Kept you out of mischief and has given the rest of us a good laugh[IMG]http://www.kolobok.wrg.ru/smiles/rpg/jester.gif[/IMG]

---

### Post by &#12465;&#12452;&#12488; on 2006-09-08
In my opinion, it must be better to move the Windows option to the top. Say, if you install another kernel, then default 3 might just become booting Ubuntu with another kernel.

Put the Windows option on the top, right before the line
### BEGIN AUTOMAGIC KERNELS LIST

That way, it'll always stay in the same spot, and you'll not need to edit the default options at all.

I don't use and have never installed Windows on my computer, as filthy things have nothing to do on my computer, and would certainly never make it default instead of Ubuntu! BUT this method is certainly effective for making static content... you know, static.

---

### Post by MiThRaZoR on 2006-09-08
> **xpod said:**
> ARHHHH...Your kidding surely.I just had to go through one of the maddest re-installs of Xp you could possibly imagine...just to shut the wife up!

As much as i felt good at my overcoming my xp issue after all that time it still riles me that i had to even put it back on the pc....(she who must be obeyed dont do sudo!!)......

I only used windows for a few months and THIS is much more fun.
I just wish i had installed it that very first week when i first
read about it........4 months wasted on virus`s,missing dll`s.
slipstreamed cd`s and wga`s bulls**T baloons....

Lol, I had the same problem. It's just that going back to something familiar is kinda nice sometimes. I don't have to worry about viruses since I use FireFox and Avast!. But I like Ubuntu better.

> In my opinion, it must be better to move the Windows option to the top. Say, if you install another kernel, then default 3 might just become booting Ubuntu with another kernel.

Put the Windows option on the top, right before the line
### BEGIN AUTOMAGIC KERNELS LIST

That way, it'll always stay in the same spot, and you'll not need to edit the default options at all.

I don't use and have never installed Windows on my computer, as filthy things have nothing to do on my computer, and would certainly never make it default instead of Ubuntu! BUT this method is certainly effective for making static content... you know, static.
That's exactly what I wanted. Cause I installed it and the updated it and that's when I had 6 things to do with Linux. So I had to put it to "6" instead of 3. So thanks for that advice.

---

### Post by hartunnoo on 2006-10-22
How do you know that windows # is on #3?? any hints for it?

---

