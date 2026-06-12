---
title: "Graphical Bootloader?"
date: 2008-11-23
forum: Art &amp; Design
---

### Post by Tindytim on 2008-11-23
I've seen some graphical bootloaders. But most of them seem to be just adding to graphics to what GRUB already does. As someone who not only uses multiple Operating Systems at a time, I find that grub gets pretty cluttered, pretty fast, with all the options for various operating systems.

I made this little mock-up as what I would see as more useful.
[IMG]http://img384.imageshack.us/img384/3086/conceptzy8.png[/IMG]
I just threw in some placeholders.

Thoughts?
I know it increases boot time by a few seconds. But I usually have to scroll through a list depending on what I want to boot.

---

### Post by lyceum on 2008-11-24
I really like this idea a lot! You should submit it on Launchpad. I really think the black-and-white we have now looks really bad, espeashally when compared to SuSE's. I hate that I have to scroll through so many different versions of the same OS to get to the one I want (I am triple booted). 

The only catch is that where would these pics come from? The would need to be added to the install CD, or grabbed from the internet. I really can't see an install CD having more than 10 or so by default. This means there will need to be a GUI to operate it, another program to add to the live CD. 

There would need to be a way to add new icons and I would like to see a way to change the background, so it is not black. Also, it would be a good idea to have the program change the order (which program is at the top of the list to start by default). If you could do all that, it would be awesome!

:popcorn:

:guitar:

---

### Post by lukjad on 2008-11-24
I've seen examples of what you are suggesting. I think that it would be a nice option, perhaps even a default. I would, however most likely turn it off. ;)

---

### Post by Tindytim on 2008-11-24
> **lyceum said:**
> I really like this idea a lot! You should submit it on Launchpad. I really think the black-and-white we have now looks really bad, espeashally when compared to SuSE's. I hate that I have to scroll through so many different versions of the same OS to get to the one I want (I am triple booted).
I know the feeling. I've had 5 OSes installed at once on multiple occasions. I currently have 4.

> **lyceum said:**
> The only catch is that where would these pics come from? The would need to be added to the install CD, or grabbed from the internet. I really can't see an install CD having more than 10 or so by default. This means there will need to be a GUI to operate it, another program to add to the live CD.
My thought would be, a few broad images the apply to some more well known OSes (like a generic Windows logo for all Windows OSes, and a Generic apple logo for any Mac OS versions, and then a few of the other big distros). If it was unrecognizable, you would get text in the image area. Or if there were duplicates you would get a small text overlay on the images (say I had Windows XP and Vista, I would get a 4 different colored squares for each, but with the name of each on top of the image, wouldn't be pretty, but it would get initially sufficient).

A utility could then be used to define some coloring options, and what logos to use (maybe from some sort of repository?).

I made this image in Inkscape, so everything is vector (changing basic colors wouldn't be difficult, and once all the settings were as desired a raster could be rendered).

> **lyceum said:**
> There would need to be a way to add new icons and I would like to see a way to change the background, so it is not black. Also, it would be a good idea to have the program change the order (which program is at the top of the list to start by default). If you could do all that, it would be awesome!
Now I want to drop all coding projects I have no to do this. But I have no experience in this. I may look into making a graphical front-end for GRUB, and what that would entail.

---

### Post by smartboyathome on 2008-11-24
> **Tindytim said:**
> [QUOTE=lyceum;6241201]The only catch is that where would these pics come from? The would need to be added to the install CD, or grabbed from the internet. I really can't see an install CD having more than 10 or so by default. This means there will need to be a GUI to operate it, another program to add to the live CD.

My thought would be, a few broad images the apply to some more well known OSes (like a generic Windows logo for all Windows OSes, and a Generic apple logo for any Mac OS versions, and then a few of the other big distros). If it was unrecognizable, you would get text in the image area. Or if there were duplicates you would get a small text overlay on the images (say I had Windows XP and Vista, I would get a 4 different colored squares for each, but with the name of each on top of the image, wouldn't be pretty, but it would get initially sufficient).

A utility could then be used to define some coloring options, and what logos to use (maybe from some sort of repository?).

I made this image in Inkscape, so everything is vector (changing basic colors wouldn't be difficult, and once all the settings were as desired a raster could be rendered).[/QUOTE]

I was thinking distros could provide their own, using a shared boot partition. Other grub folders could also be looked for on the hard drive so that their images could be added. For other Operating Systems (especially ones which don't include GRUB), the distro could apply icons they include on the install CD if none were available already by other installs. A generic icon could be applied for unrecognized ones.

---

### Post by lyceum on 2008-11-25
> **Tindytim said:**
> I know the feeling. I've had 5 OSes installed at once on multiple occasions. I currently have 4.


My thought would be, a few broad images the apply to some more well known OSes (like a generic Windows logo for all Windows OSes, and a Generic apple logo for any Mac OS versions, and then a few of the other big distros). If it was unrecognizable, you would get text in the image area. Or if there were duplicates you would get a small text overlay on the images (say I had Windows XP and Vista, I would get a 4 different colored squares for each, but with the name of each on top of the image, wouldn't be pretty, but it would get initially sufficient).

A utility could then be used to define some coloring options, and what logos to use (maybe from some sort of repository?).

I made this image in Inkscape, so everything is vector (changing basic colors wouldn't be difficult, and once all the settings were as desired a raster could be rendered).


Now I want to drop all coding projects I have no to do this. But I have no experience in this. I may look into making a graphical front-end for GRUB, and what that would entail.

I assumes the name would pop up as text above or below the image. If the name is there the image could just be a penguin for Linux, the devil for FreeBSD, etc... then theh user could replace it. 

As for the the distros making their own, I think he fans would do it, as I fear some one not think this a prioraty. Obviously, those that use it would create their own icon for it.

Let me know if you need any help with art, ideas or testing. I cannot code though, sorry. If I were you I would put something up on Sourceforge and ask for help. I would also sign up for different distro forums and rease awareness and try to get help there.

---

### Post by Thr33finger on 2009-05-01
Just wanted to follow up and see if there has een any progress with this? I was told by a friend that he saw someone do this sort of thing already. It was more basic(less OS options). He moved away and I have not been able to conact him. It took me forever but i finally found the picture He was refering to.

[http://www.2shared.com/file/5580556/8bb25969/linux-windows2preview.html](http://www.2shared.com/file/5580556/8bb25969/linux-windows2preview.html)

Just using the left and right arrow keys to move from windows to linux. Simple but looks cool.

---

### Post by Tindytim on 2009-05-01
Nope, GRUB 2 is coming, and it's going to have a graphical interface appearently. Depending on how that GUI works, I may attempt to learn a bit about coding for a bootloader. But I don't see the point in working on something that will be out of date very soon.

---

### Post by hessiess on 2009-05-01
Boot loaders run before the operating system is booted, which means that they have to use the lagency 16 bit BIOS features to draw there interface with the 800*600 resolution limit, or implement there own graphics system. Newer systems like the Linux BIOS or EFI are far more feasible bases on which to implement graphical boot loaders.

---

### Post by Sewje on 2009-05-01
There is such bootloader out in the wild believe it or not.

If you've been following the osx86 scene, recently such bootloader has been made and it is currently in RC,
But it does exactly what you are looking for!

[http://chameleon.osx86.hu/articles/chameleon-20rc1-is-out](http://chameleon.osx86.hu/articles/chameleon-20rc1-is-out)

---

### Post by pietjanjaap on 2009-05-02
> **Tindytim said:**
> I find that grub gets pretty cluttered, pretty fast, with all the options for various operating systems.

But I usually have to scroll through a list depending on what I want to boot.

With startup-manager you can decrease the kernels you see on boot(grub).

---

### Post by Niva on 2009-05-03
Let me say that I really like the screen above.

However, I find that images like this would baffle newcomes w/o the use of their mouse.  You'd still be restricted to using just the keyboard to make a selection during bootup and it will make things complicated.

I do agree with the sentiment though.  Ubuntu's grub is not taylored in any way like SUSE's and just plain looks ugly.  

Also Grub gets cluttered very fast.  

If I recall SUSE also has a graphical utility to manage grub within YaST which I found pretty nice when I used it a few years ago.  Not sure if Ubuntu has such an application, but it allowed a user to go in and manage the boot options w/o needing to text-edit the menu.lst file within grub.

If we can concentrate on giving users a graphical option to select/edit boot options any time a new kernel header is added it would really be optimal.

---

### Post by damis648 on 2009-05-03
Chameleon boots linux? It never used to... Right now I have the following setup:

Grub:
Ubuntu
Windows
OS X -----> Chameleon -----> OS X
                      |
                       -----> Windows
I only use the GRUB windows option, however.

In any case, the new chameleon looks great. Not likely to be implemented into Ubuntu, however.

---

### Post by Orlsend on 2009-05-04
Man something like this would sure help my mom, she really scared on anything that looks like  a command line.

---

### Post by damis648 on 2009-05-04
> **Orlsend said:**
> Man something like this would sure help my mom, she really scared on anything that looks like  a command line.

Most people are. :(

---

### Post by Tindytim on 2009-05-04
> **damis648 said:**
> Most people are. :(
I certainly hope you aren't talking about Ubuntu users.

---

### Post by lyceum on 2009-05-04
> **Tindytim said:**
> I certainly hope you aren't talking about Ubuntu users.

One would imagine that Linux for human Beings would mean that Ubuntu is for people that fear the command line ;)

---

### Post by Tindytim on 2009-05-04
> **lyceum said:**
> One would imagine that Linux for human Beings would mean that Ubuntu is for people that fear the command line ;)

Why would they imagine that? What does fear of the command line have to do with being human? I don't fear the command line and I'm human.

---

### Post by Niva on 2009-06-07
LOL, there are humans who fear the command line just like there are humans who fear linux (because they tried it when you can only use the command line.)

Ideally everything will move away from the command line, but it would be available for those who like using it.

---

