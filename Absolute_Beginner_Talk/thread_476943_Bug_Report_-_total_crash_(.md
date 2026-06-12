---
title: "Bug Report - total crash :("
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by U5tabil on 2007-06-17
Hello.

It seems like my ubuntu has in some way "crashed"

Just to get it from the beginning. I tried to extract a .ISO file but it failed, and crashed my pc. So when i try to start it again i get a stupid "bug report" stuff in my face i press cancel and a new one gets up. This has happend before on a smaler number of files but this time it was 251 files in that ISO. So i thought i just could press cancel 251 times, but no. The system crashes every 11 cancel or save for that matter. And i tried to do this 251times... But the "bug report" still comes up. Making my pc not working. I cant do anything :( How can i fix this? How can i get rid of this?

Please help :(

---

### Post by jrusso2 on 2007-06-17
I don't even understand why your extracting an ISO.  I just burn them as ISO image files.

---

### Post by U5tabil on 2007-06-17
> **jrusso2 said:**
> I don't even understand why your extracting an ISO.  I just burn them as ISO image files.
Well the .ISO file was 6.9GB and i dont have any DVD disc around... So i thought i could extract it but no...

Do you know how to fix this? Just make that **** disappear?

---

### Post by U5tabil on 2007-06-18
Nobody knows what i need to do? :(

---

### Post by wormser on 2007-06-18
You can just mount the iso.  I have done this a few times and it works great.

The first thing is to create a mount point for the iso.

```
sudo mkdir /media/myiso
```

Next we mount it.

```
sudo mount -t iso9660 filename /media/myiso -o loop
```

Now you should have an icon on the Desktop.  That example assumes you are in the directory the file is in.  You can always specify the whole path instead /home/username/Desktop/myiso.

To unmount it use the umount command.

```
sudo umount /media/myiso
```

BTW, that is a big iso.  What is it?

---

### Post by hardyn on 2007-06-18
two layers of a commerical DVD.

---

### Post by U5tabil on 2007-06-18
It's a movie. Thats why its so big.
But that don't help me get rid of that bug report! I CAN'T USE THE PC UNLESS I GET RID OF THAT! :(
How can i get rid of that ******* ****?

---

### Post by U5tabil on 2007-06-18
No one that knows how to fix this? My PC is totaly usless if i cant fix this :(

---

### Post by MrKlean on 2007-06-18
It looks like you need a dual layer dvd and writer.. 
But, you should be able to get rid of the error with a reboot ..

---

### Post by U5tabil on 2007-06-18
> **MrKlean said:**
> It looks like you need a dual layer dvd and writer.. 
But, you should be able to get rid of the error with a reboot ..

Well now i dont even care about the .iso file i just want the pc up and running again.
And a reboot doesn't help :(

---

### Post by jvc26 on 2007-06-18
Can you not find the running processes via system monitor or top and kill them?

System -> Administration -> System Monitor
Or:
Applications -> Accessories -> Terminal
```

top

```
Then kill the PIDs which are causing you trouble?
Il

---

### Post by podfish on 2007-06-18
So, when is the machine crashing in the boot process?  what specific error messages are you receiving?

Can you tell us, step by step, where you are in the process and what you've tried to do, what programs you're trying to use, and what beeps and bloops the machine is giving you?

Also, can you tell us what media you used to install ubuntu?  was is the 64-bit or the 32-bit?

Thanks!

---

### Post by U5tabil on 2007-06-18
I am using the Ubuntu dapper i think its the 6.06 version on a 32bits....

The problem is that when i log in the bug report pups up (tried to kill it in the system panel or whatever) and when that pops up it stops the rest from starting, the system bars aint complet. So i can't use anything... and i tried to cancel it several times but it doesnt go away, after canceling 11 times (every time even after reboot) the system bars disapears.

---

### Post by U5tabil on 2007-06-18
Il try to post some pictures here now. now you can see what i mean. And it aint going away. As you can see on the last picture the panels goes dark and i need to ctrl+alt+backspace to start over again. but the same thing happens every time. Even after a complete reboot...

And now i need to sit on this crappy windows... The only way was that i manage to take a screenshot of this placing the files over on my portable hard drive and then over here.

---

### Post by U5tabil on 2007-06-18
No one knows this problem? :o

---

### Post by vexorian on 2007-06-18
It is very odd.

Do you have a swap partition? It could be that the extracting made your hardware full and now there's no ram and is issueing that bug, either way if the files that you were extracting from the ISO are still in the filesystem, you shall try joining from recovery mode / live cd and removing those files.

If that doesn't work then you can just use recovery mode / live cd to save your documents and do a clean reinstall, I am sorry but this problem is very strange.

--- 

wow wow wo, stop, Tried checking the details screenshot, it is certainly related to memory, vm size is 0? Try removing what you extracted that's for sure.

---

### Post by wormser on 2007-06-18
It looks like the bug report tool has that bug in its list to send off.  Try removing the bug report tool.

System> Administration> Synaptic Package Manager
Click the search button and search for bug-buddy - I think that is the right name
Remove bug-buddy
Then reboot

Hopefully that will solve it.  If you want the bug reporting tool then reinstall it after everything is working.

Now you can follow [my directions]("http://ubuntuforums.org/showpost.php?p=2865858&postcount=5") from the post earlier to mount the iso to view it.

---

### Post by podfish on 2007-06-18
also, it looks like gnome-panel is freaking out on you, based on the bug-buddy output.  My guess is that you have some applet installed that's segfaulting or doing some other nastiness.  Did you install a new applet recently?  Like that system monitor one that is showing 4 pieces of activity in your lower left-hand corner?

What's that red cd lookin' thing next to your system menu?  Is that nero?

Anyhow, uninstall all your applets through the gnome-panel menu, reinstall them one by one to see which is causing the problem, and see if that resolves your situation.  Then mount your iso, like the other dude said, and see what happens.

Good luck!

---

### Post by U5tabil on 2007-06-19
well the control bar isn't accessable and deliting the files didn't do it. so i hope that the live cd and a recovery boot will help, and removing the bug-buddy will help....

---

### Post by U5tabil on 2007-06-19
well removing bug buddy just made the problems bigger. Now it "cancels" it by itself, making the crash come faster... It seems like a total reinstall is needed... and then i need to try installing my ATI X1950PRO card... Should i start the install with the card in or should i install it with the Nvidia card and then install ATI card?

---

### Post by U5tabil on 2007-06-20
Ok THIS is strange!

As you all know the system crashes an that bug buddy showed up every time when i started. 
And when that happened i couldn't use anything. So i came up with an idea since i was last time surfing on the net finding a phone number that i needed really much but couldn't get any more. 
So when the system started i pushed the terminal icon that i have in the down left corner many times. Then i started the Firefox from there. And HEY now everything works as it should, no error or crashing!

What the hell happened? I really don't know what has happened. But now thing works and i don't need to do a reinstall!

---

