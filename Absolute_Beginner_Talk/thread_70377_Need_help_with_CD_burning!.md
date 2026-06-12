---
title: "Need help with CD burning!"
date: 2005-09-29
forum: Absolute Beginner Talk
---

### Post by Alpha_Cluster on 2005-09-29
Im trying to burn a CD for Brezzy Live CD but it wont let me lower the burn speed and i know from experince that its burning to fast is there some way i can make it so that when i use the write to CD command on the .iso that i can change the burn speed down from max to say 12 or 16x

---

### Post by SilentCacophony on 2005-09-29
Which cd burning program, from what OS, are you using?

If you're working from Windows, you can use BurnCDCC from [here]("http://www.terabyteunlimited.com/utilities.html") to burn as slow as 4x.

---

### Post by Alpha_Cluster on 2005-09-30
No im running Ubuntu and im just using whatever program you getfrom right clicking on the iso and selecting write to a CD.

---

### Post by matthewv on 2005-09-30
try installing and/or using gnomebaker or k3b using synaptic

---

### Post by Perfect Storm on 2005-09-30
Or NeroLinux

Or with Nautilus CD burner (which you tried with): Go Application tab ---> System Tools ---> Configuration Editor

Apps ---> Nautilus-cd-burner 
Then change [default_speed] to 2 or 4 (whater you want). Just right click it and edit key.



.:=The AI Dude=:.

---

### Post by jeremy on 2005-09-30
NeroLinux is pretty lame, not nearly as good as K3b, and not free either!

---

### Post by Perfect Storm on 2005-09-30
[QUOTE=jeremy]NeroLinux is pretty lame, not nearly as good as K3b, and not free either![/QUOTE]

No, it's quite cool, if you own a license from nero 6 you get Nero linux for free, just type in your code.
Also thte good thing is you don't have to install KDE libs which I (and I know others) won't have on my machine.

---

### Post by wmcbrine on 2005-09-30
If you use the command-line program "cdrecord", you can specify the speed as an option. I don't know about the graphical UI; I'll check that later. (I'm typing this from Mac OS.)

Edit: Oops, AI had it up there in post #5.

---

### Post by Raj on 2005-09-30
Hi guys,

Total newbie and new to the forum. I did manage to Ubuntu running and have been "free" of windoze for a couple of weeks. This is a general question, but this post prompted me to ask...I installed K3B via synaptic as well as other programs, but icons for these app's dont appear anywhere. I am guessing that is because the apps are not either Ubuntu-centric or gnome-centric. Is this correct, as when I just installed gnomebaker, there it was. Having said this, couldn't find Noerlinux on synaptic...I do have a windows serial for it, so would be cool to try it out.

If this is the case, is there an easy way to have the apps icons appear in the menu's or create them manually, how much work is involved. I have looked on the starters guide and generally, but cant find the answer. Could someone point me in the right direction? Similarly in relation to speeding up the distro on my system..P3/800/128/80Gb.

Great distro, im hooked :)
Raj

---

### Post by 5-HT on 2005-09-30
[QUOTE=Raj] is there an easy way to have the apps icons appear in the menu's or create them manually, how much work is involved.[/QUOTE]
In terms of modifying the applications menu, there is a great program by called Smeg written by Amaranth which will allow that function. 

Though from what I've heard, one of its dependencies requires a newer version than that found in Hoary, resulting in at least one possible minor annoyance that the add/remove programs feature may be rendered inoperable (though synaptic/apt/aptitude are unaffected). 

Information on Smeg can be found [here]("http://ubuntuforums.org/showthread.php?t=38183").

I believe that Smeg will be installed by default in Breezy though.

Another option would be to simply create a shortcut to the program by right-clicking on the desktop and selecting "create launcher". Just fill in the name you'd like for it and the path to the program.

HTH

---

### Post by Raj on 2005-09-30
Cheers 5-HT,

I already thought about the shortcut option myself, but being from windows, this is where i am at a loss as to which file to point to, the directory it resides in etc etc. as for this i will probably give away the idea for now, as everything i NEED is there, just some nice apps which i thought i could add. but i think ill remove them. now, to figure out samba/talking to my windows laptop and gnome meeting with my logitech *sigh* ;)

thanks again

raj

---

### Post by patrick295767 on 2005-09-30
apt-get -f install xcdroast

ok, but how to make add files to burn ur data cd (regular stuff) ?
There is only add iso ??

thx

---

