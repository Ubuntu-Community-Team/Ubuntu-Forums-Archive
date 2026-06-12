---
title: "change boot splash"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by Jaxilian on 2006-08-25
I need to change the boot splash, usplash or whatever it's called. I am looking for a simple way...no rocket science novels please.

Can anyone point me in the right direction? I searched for howtos, but everyone was different from the other and all seemed like rocket science to me. ](*,)

---

### Post by ciscosurfer on 2006-08-25
There isn't "an easy way" of doing this.  Search the forums again and follow the directions.

---

### Post by Senshi on 2006-08-25
[Check out this site.]("http://www.freesoftwaremagazine.com/articles/change_ubuntu_look?page=0%2C1")

This site will go through step-by-step showing you how to change the wallpaper, login screen, icons, or splash screen using Art Manager.

---

### Post by ciscosurfer on 2006-08-25
> **Senshi said:**
> [Check out this site.]("http://www.freesoftwaremagazine.com/articles/change_ubuntu_look?page=0%2C1")

This site will go through step-by-step showing you how to change the wallpaper, login screen, icons, or splash screen using Art Manager.
Well I'll be...that's fantastic...KDE has something similar if I recall.  Nice post Senshi!

---

### Post by Jaxilian on 2006-08-25
> **Senshi said:**
> [Check out this site.]("http://www.freesoftwaremagazine.com/articles/change_ubuntu_look?page=0%2C1")

This site will go through step-by-step showing you how to change the wallpaper, login screen, icons, or splash screen using Art Manager.

I couldn't find any info about changing the boot splash on that link. :confused:

---

### Post by ciscosurfer on 2006-08-25
> **flodis said:**
> I couldn't find any info about changing the boot splash on that link. :confused:

You still need to follow the forums guides on how to accomplish that...the other link describes an easy program that allows you to modify your GDM splash, themes, icons, etc.  Not the bootsplash.

---

### Post by Jaxilian on 2006-08-25
> **ciscosurfer said:**
> You still need to follow the forums guides on how to accomplish that...the other link describes an easy program that allows you to modify your GDM splash, themes, icons, etc.  Not the bootsplash.

I looked for several weeks for a website that describes how to change the boot splash, but havent found one.
My guess when I have searched this intensive is that it can't be done by a human.
same goes for remastering the ubuntu CD, should be able to be done by 1 program and not 5 million commands.

I am loosing faith in Ubuntu :confused:

I just want to change that ubuntu splash for a more personal one..one simple picture..gaah how hard can it be???

---

### Post by ciscosurfer on 2006-08-25
[http://ubuntuforums.org/showthread.php?t=82835](http://ubuntuforums.org/showthread.php?t=82835) or [https://help.ubuntu.com/community/USplashCustomizationHowto](https://help.ubuntu.com/community/USplashCustomizationHowto)

---

### Post by Jaxilian on 2006-08-25
> **ciscosurfer said:**
> [http://ubuntuforums.org/showthread.php?t=82835](http://ubuntuforums.org/showthread.php?t=82835) or [https://help.ubuntu.com/community/USplashCustomizationHowto](https://help.ubuntu.com/community/USplashCustomizationHowto)

I looked at that one before. Too messy written! I give up! I have to tell the computer manufacturer that I was gonna help to get lost. :-({|=

---

### Post by ciscosurfer on 2006-08-25
The second link I provided you was written with the least amount of steps involved.  This is the only way (I know of) to get a new USplash up and running.  It's not so hard, just copy and paste! (but read the instructions as well) :D

---

### Post by Jaxilian on 2006-08-25
> **ciscosurfer said:**
> The second link I provided you was written with the least amount of steps involved.  This is the only way (I know of) to get a new USplash up and running.  It's not so hard, just copy and paste! (but read the instructions as well) :D

didnt work. I just got red error and it booted anyway. Had to restore it back

When I run the command:

gcc -Os -g -I/usr/include/bogl -fPIC -c usplash-artwork.c -o usplash-artwork.o

I get a lot of these: 

usplash-artwork.c:3161: varning: stort heltal implicit trunkerat till unsigned typ

I tried the howto 4 times now and same every time. It doesnt show any new splash, in fact it doesn't show any splash....just red error that swishes by very fast so I can't read it.

The howto needs more clarification about the steps to take.

---

### Post by ciscosurfer on 2006-08-25
You need to create or convert your own picture first...whatever you want your usplash to look like.  I'm not sure how else to help you, the tutorial on the pages I've provided seem to work for me.  Try reading through the threads to see if some people are having the same problems as you.  Try this page again -- remember, you need to start out with PNG image files...try using the ones provided at this link, and read through this thread as well: [http://ubuntuforums.org/showthread.php?t=82835&highlight=usplash](http://ubuntuforums.org/showthread.php?t=82835&highlight=usplash)

---

### Post by Jaxilian on 2006-08-26
> **ciscosurfer said:**
> You need to create or convert your own picture first...whatever you want your usplash to look like.  I'm not sure how else to help you, the tutorial on the pages I've provided seem to work for me.  Try reading through the threads to see if some people are having the same problems as you.  Try this page again -- remember, you need to start out with PNG image files...try using the ones provided at this link, and read through this thread as well: [http://ubuntuforums.org/showthread.php?t=82835&highlight=usplash](http://ubuntuforums.org/showthread.php?t=82835&highlight=usplash)

I tried with a PNG file and it didnt work. Can someone please provide info on what picture format to use? and what program to create them with cause GIMP aint working so good on that. :confused:

during the boot with the new splash I get this error:

setting up per-VC font - FAIL


I have no clue what that means

---

### Post by Tomosaur on 2006-08-26
You need to use very specific palette colours to create your own splash. The GIMP will allow you to create a custom palette no problem, but editing a palette to be USplash compatible is a bit more tricky. You can't just use any old picture, a USplash has very specific elements, which is why it requires a specific palette. You can, of course, edit a picture to be USplash compatible, it's just kinda difficult with the tools available.

---

### Post by Jaxilian on 2006-08-26
> **Tomosaur said:**
> You need to use very specific palette colours to create your own splash. The GIMP will allow you to create a custom palette no problem, but editing a palette to be USplash compatible is a bit more tricky. You can't just use any old picture, a USplash has very specific elements, which is why it requires a specific palette. You can, of course, edit a picture to be USplash compatible, it's just kinda difficult with the tools available.

What palette do I need?

---

### Post by mejy on 2006-08-26
> **flodis said:**
> What palette do I need?

Can you be a bit more specific about why you need your bootsplash changing?  If you'd like an easier method, perhaps you'd like to try [this?]("http://www.ubuntuforums.org/showthread.php?t=216597&highlight=splashy") (It's not actually changing the bootsplash, it's replacing usplash itself).

---

### Post by fakie_flip on 2006-08-26
Doesn't gnome-look.org give any directions since it has splash screens? I could be wrong. You can always try asking the people on there for advice especially the creaters of splash screens.

---

### Post by fakie_flip on 2006-08-26
Ask specific questions about instructions that you do not understand in order to get the best help following them.

---

### Post by Tomosaur on 2006-08-26
The palette (I think) needs to be 16 colours of your choosing, but the index of the specific colours does mean something. I can't remember the exact meaning, but just imagine that colour 0 is the loading bar, colour 1 is your text colour, colour 3 is your fail colour etc etc. There's a table with the info you need lying around somewhere.

---

### Post by adverseyaw on 2006-08-26
The palette does need to be a specific order.  Here is the link to ubuntu's [HOWTO]("https://help.ubuntu.com/community/USplashCustomizationHowto").  Read that first.  Making sure that your png image is compatible (I would recommend 640x230 or some similar size for VGA in boot screen). Then when you are sure, use the script at bottom to configure it... do it like this...
```

mv make-usplash.sh.txt make-usplash
sudo chmod +x make-usplash
sudo make-usplash <your_png image>

```
And that will do it.
Pay no attention to the line...
**Searching for splash image ... none found, skipping**

> **SilentCacophony said:**
> [COLOR="Red"][INDENT]* EDIT * - Please note that the output of the last step may include the message "splash image... none found, skipping...", which does not affect usplash in any way. It is a function of the /sbin/update-grub script which is executed while reconfiguring the linux-image package, and only displays if you've never previously set up the optional grub splash image, which would display before usplash would, and is an entirely separate splash image meant for the grub menu alone.[/INDENT][/COLOR]

Let me know of any errors you get, if any.  I will try to help you through them.

AdverseYaw

---

### Post by ciscosurfer on 2006-08-26
> **ciscosurfer said:**
> [http://ubuntuforums.org/showthread.php?t=82835](http://ubuntuforums.org/showthread.php?t=82835) or [https://help.ubuntu.com/community/USplashCustomizationHowto](https://help.ubuntu.com/community/USplashCustomizationHowto)

@flodis

The links I have provided for you explain in explicit detail exatcly how to change and/or create a new USplash.  You need to *read through* *the entire* thread and then follow the wiki in order to do it.  Others have had your similar problems, too.  Please be patient and understand that we are trying to help you.  I've pointed you to the thread and wiki that are important (with subsequent links on the thread that are helpful as well).  Rather than reposting the intructions, please try reading what others have already written on this subject.  :D  

Know also that the wiki will work for you if you are using Dapper...the original thread instructions will work if you're using anything before Dapper.  We are beginning to repeat ourselves and it doesn't seem like you are following through on reading the links provided :(.  If you don't like the instructions for USplash customization, than you can try gfxboot (search on the forums) as well as splashy (again, within this thread or search on the forums).  You can also use your original usplash by simply adding the proper vga= line to end your kernel.  If you need more help, then you can also try the #ubuntu channel on IRC.

EDIT: after further thought, I think "splashy" might be the best way for you to go...you don't need to patch your kernel, it's highly customizable, and very easy to install.  If you encounter trouble with splashy, [then this link]("http://www.ubuntuforums.org/showthread.php?t=239291&highlight=splashy") should help.  Bear in mind, no solution is perfect and works differently for everyone.  Splashy has it's own issues, too. Try 'er out! ;)

EDIT: on even further thought, splashy is quite buggy right now.  I'd pass on it.  Try the seregeti splash (I use this one and enjoy it immensely)

---

### Post by Jaxilian on 2006-08-26
> **ciscosurfer said:**
> @flodis

The links I have provided for you explain in explicit detail exatcly how to change and/or create a new USplash.  You need to *read through* *the entire* thread and then follow the wiki in order to do it.  Others have had your similar problems, too.  Please be patient and understand that we are trying to help you.  I've pointed you to the thread and wiki that are important (with subsequent links on the thread that are helpful as well).  Rather than reposting the intructions, please try reading what others have already written on this subject.  :D  

Know also that the wiki will work for you if you are using Dapper...the original thread instructions will work if you're using anything before Dapper.  We are beginning to repeat ourselves and it doesn't seem like you are following through on reading the links provided :(.  If you don't like the instructions for USplash customization, than you can try gfxboot (search on the forums) as well as splashy (again, within this thread or search on the forums).  You can also use your original usplash by simply adding the proper vga= line to end your kernel.  If you need more help, then you can also try the #ubuntu channel on IRC.

EDIT: after further thought, I think "splashy" might be the best way for you to go...you don't need to patch your kernel, it's highly customizable, and very easy to install.  If you encounter trouble with splashy, [then this link]("http://www.ubuntuforums.org/showthread.php?t=239291&highlight=splashy") should help.  Bear in mind, no solution is perfect and works differently for everyone.  Splashy has it's own issues, too. Try 'er out! ;)

EDIT: on even further thought, splashy is quite buggy right now.  I'd pass on it.  Try the seregeti splash (I use this one and enjoy it immensely)

it works now! yay! I had to take another existing splash image and modify it to make it work. It didn't have the correct colors but at least I have my splash now. Thanks man! :-\"  =D>

---

### Post by Jaxilian on 2006-08-26
> **mejy said:**
> Can you be a bit more specific about why you need your bootsplash changing?  If you'd like an easier method, perhaps you'd like to try [this?]("http://www.ubuntuforums.org/showthread.php?t=216597&highlight=splashy") (It's not actually changing the bootsplash, it's replacing usplash itself).

I needed to change it cause I got a computer manufacturer interested in Ubuntu. Splash is now changed and I got all other parts changed now....just need to remaster it or make a ghost image of it somehow. Not ghost since it costs money...anyone know a good program on linux to make "ghost" images??

---

### Post by fakie_flip on 2006-08-26
Do you mean like Norton Ghost copies of your partitions? Try dd.

---

### Post by Jaxilian on 2006-08-26
> **fakie_flip said:**
> Do you mean like Norton Ghost copies of your partitions? Try dd.

I mean so I can boot with the CD/DVD that has an exact cpoy of my full HD and restore it with a simple command. I used to do that with ghost all the time when I was running Windows.

Can it be done in Ubuntu linux? :-\"

Also do any know why changing the usplash made the boot time longer by like 8 seconds?

---

### Post by ciscosurfer on 2006-08-26
> **flodis said:**
> I mean so I can boot with the CD/DVD that has an exact cpoy of my full HD and restore it with a simple command. I used to do that with ghost all the time when I was running Windows.

Can it be done in Ubuntu linux? :-\"

Also do any know why changing the usplash made the boot time longer by like 8 seconds?

flodis,
I'm glad to hear you got it working!  As far as longer boot time, perhaps you are using a larger image (higher KB, perhpas a even a little over a MB).  Try making the image size (cropping the image, and making sure on a 16 color palette are chosen should do the trick).

In terms of a program like Ghost, I agree with a previous poster who suggested using 'dd'.  Check it in a terminal by issuing```
man dd
```Good Luck!

---

### Post by Jaxilian on 2006-08-27
> **ciscosurfer said:**
> flodis,
I'm glad to hear you got it working!  As far as longer boot time, perhaps you are using a larger image (higher KB, perhpas a even a little over a MB).  Try making the image size (cropping the image, and making sure on a 16 color palette are chosen should do the trick).

In terms of a program like Ghost, I agree with a previous poster who suggested using 'dd'.  Check it in a terminal by issuing```
man dd
```Good Luck!
 

Can I use compression on the PNG file or does it have to stay uncompressed?

---

