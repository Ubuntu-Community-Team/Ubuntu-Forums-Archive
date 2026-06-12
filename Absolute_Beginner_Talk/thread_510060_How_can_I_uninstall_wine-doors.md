---
title: "How can I uninstall wine-doors?"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by Jareth on 2007-07-26
I installed wine-doors with the .deb package. It installed okay but it doesn't do anything for me, all it seems to have done is install aload of other things I didn't even ask for like a link in my applications to half life 2 (wtf?) and somthing called autokeys?

So I want rid now as I can't afford the space to just leave it on there.
Can anyone suggest how to completely remove everything it has done since installing?

Ta for now!

---

### Post by mcduck on 2007-07-26
> **Jareth said:**
> I installed wine-doors with the .deb package. It installed okay but it doesn't do anything for me, all it seems to have done is install aload of other things I didn't even ask for like a link in my applications to half life 2 (wtf?) and somthing called autokeys?

So I want rid now as I can't afford the space to just leave it on there.
Can anyone suggest how to completely remove everything it has done since installing?

Ta for now!

Just search for it in Synaptic and then remove it. Or run 'sudo apt-get --purge remove wine-doors'. Then you can get rid of all extra packages it installed by either taking a look into 'auto-removaböe' section in Synaptic or by running 'sudo apt-get autoremove'.

Everything you install from .deb packages will show in Synaptic and can also be removed with it.

---

### Post by dreaswar on 2007-07-29
hey i face teh same problem..
even after i have unistalled the winnedoors form synaptic the application it has installed like Autokeys and Quicktime do not go away form teh menu. 

i tried the sudo command for autoremove but nothing happened. it just said 0 programs to be removed. 

i searched in synaptic for autoremovable section ... didnt find any such section ..

i tried uninstall button on the menu for quicktime.. it went through the "un installation " but he menu and the programs stil remained. 

however by following the synaptic i could sucessfully remove the wine doors program .. but not the programs it has intalled. ...

any idea...

my disc space is low and i really want to salvage as much space as possible. i can do very well without quicktime ..as i had just installed it on a test basis to see how this wine doors worked. 

please help..

---

### Post by livingtarget on 2007-07-29
Easy tip to save space? 

Clean out all the packages apt downloads. If you install a lot, you may want to clean this cache.
sudo apt-get clean

It doesn't look like wine-doors would actually use a lot of space. If you feel annoyed by the items in the menu, either find them in the menu editor (right-click on the menu and press edit) and either hide them (untick them) or remove them all together.

If you want to remove the .desktop file directly you can do: 
sudo rm -i /usr/share/applications/wine-door.desktop

.desktop file generate menu icons btw. If there's any on the desktop just remove them.

You know where it installs wine? That's most likely the source of your problems. Browse to /home/your_user_name/.wine/drive_c/ this is the default drive wine uses to store everything. Just remove it and you should get more space available. It is hidden by default (all dot files are), just press ctrl+h to toggle them in nautilus.

Other great utility to see where your space is going is the Disk Usage Analyser in Applications -> Accessories. Just scan your home folder and it will show you what is eating up space. ;)

---

### Post by dreaswar on 2007-07-30
thanks a lot for the advice 

i tried out what you said.

1) deleted the quicltime folder in /wine/c_drive/programs

    that saved some 70mb.

2) i deleted the short cut in menu bar for quicktime and autokeys.

3) used the disk analyser to find out what is taking up space. 

   ./wine had a folder called installer which was taking about 130MB of space.

   found that the cache folder  in /var/cache/apt is taking up 680MB. 

   i found a whole list of packages here. is this what get deleted when you clear the cache with         the command?

do i need to back up this file ... wil i need them again.?

The reason i am worried about space is that i am running ubuntu through Wubi and had allocated 5GB of virtual disk space during installation . i have an internal hard disk of 18 Gb and an external USb hard of 120 Gb in two 60 Gb partitions. The internal hard disk has a free space of 3.9Gb after installation of ubuntu.

After ubuntu installation i had updated the OS nad installed varous small programs which could have taken up space. I am not abe to find out how much of the virtual disk space is being used up by ubuntu and how it is being split among the various folders. The disk analyser while being a very good program , gives only the percentage of disk space used by that folder.. 

for eg. i have an external hard drive which is 60Gb and has 2 GB free space. but the anlyser calculates the total hard disk space external and internal and says that it is using up 40%. which is not true. 

so, more questions....

is there any way in which i could find out the free space on my virtual disks ?

which folders do i monitor in ubuntu to know whether this is getting filled?

right now i seem to be having 680 mB free space in /bin and /usr folders and have 70Mb free in /home folder( which has only 7mb occupied. )

is that good enough?

and ofcourse is it safe to delete the cache under /var/cache/apt ?

thanks so much..

---

### Post by forestpixie on 2007-07-30
as far the apt cache goes - you can clear it and then as you apt-get install it'll just start filling up again so I don't think that'll be a probelm - it hasn't caused me any 

I don't use virtual disks so can't hellp with that 

I believe that your 70mb /home will only fill with what you actually put there yourself - but I could be wrong.

---

