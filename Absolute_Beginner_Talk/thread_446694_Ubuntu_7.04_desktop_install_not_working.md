---
title: "Ubuntu 7.04 desktop install not working"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by meegs on 2007-05-17
Hi...new to Linux...trying first evar install with very little linux knowledge etc....but have tried to do heaps of reading of documentatoin etc.

Ok so, have dl and burnt the live desktop CD

Re-booted my computer with CD and get to the first options page, when I hit the start/install thing it goes onto the black background and orange ubuntu and load bar page. From here the orange bar just bounces back and forth for a few seconds and then seems to give up and goes to some sort of a command line screen. Says stuff like:
Preparing Preliminary Keymap....OK
Restricted Drivers......OK
Starting Basic Netwoking........OK
Loading Hardware Drivers..................but on this one it just goes nuts and mad stuff scrolls out....but not always the same stuff (I have rebooted and tried this a few times eh!)

Please see the attached screen shots of these odd screens & error messages.

I really can't tell what would be causing this stuff, I followed the guides and defragged my hd, it has 60GB free, I have 512MB ram and my computer is about 3yrs old or so Compaq basic desktop.

I even did the whole check CD integrity thing and the memory test and they didn't come up with any errors

If anyone has any suggestions of what I might try or do to resolve this....plz help!

---

### Post by raja on 2007-05-17
I am not sure what the problem is, but you can try to install using the alternate install cd - often works when the live cd fails.

---

### Post by Terl on 2007-05-17
What are the pc specs that you are trying to install this to?

---

### Post by meegs on 2007-05-17
I'm not absolutely sure, but it's a Compaq with Pentium 4, I don't really know much more....

---

### Post by meegs on 2007-05-18
Ok so I am back at home now and have checked out the specs of the aforementioned pc.....


HPd220 Intel
Pentium 4 2.4GHz
512MB of RAM

I have also have a ATI Radeon 9250 graphics cad installed as well as a HD tv card

I have noticed in the other forums that some people have had problems with this type of graphics card, could it be this causing the problem?

I have only recently installed the graphics card and I used to just use the on-board graphics card....should I take the new card out? 

If I use the alternate cd to install will it solve the problem if it is the graphics card??

hope someone can help!

Meegs

---

### Post by Sef on 2007-05-19
Read this [sticky]("http://ubuntuforums.org/showthread.php?t=414194").

---

### Post by meegs on 2007-05-20
Hey, thanks for the suggestion of that sticky....

I have tried to follow it but I can't really quite get there....

I did the alternate disk install, which all seemed to go fine...

now I have rebooted into the Ubuntu OS and it has begun loading....and now stalled...the little orange bar is probably only 1/5 of the way accross....

any suggestions on how to overcome this?

Megan

---

### Post by southernman on 2007-05-20
Hi Megan - I think you'll have to adhere to the sticky Sef gave you. The basic differnce between the "live vs. alternate" cd is the minimum requirement of RAM your system must have.

Don't shoot me if this is incorrect advice... still learning *nix myself! ;)

---

### Post by meegs on 2007-05-20
well, yes, that's all good and well southernman....but I can't get into linux to follow the sticky....sooo I guess that's what my question actually is...

if I can't load ubuntu....how can I follow the sticky?

---

### Post by southernman on 2007-05-20
Ouch... so sowwwy! ;P

Give me a few. I'll have to search the forums for you so we can both learn how to drop into a console (DOS style) where you can run the commands given!

---

### Post by Bartender on 2007-05-20
just for the heck of it, try typing in "irqpoll" at that first options page.  I don't rememebr the details but you want to ask Ubuntu to load with irqpoll as a boot option.
I don't really think that'll solve your problem but easy to try
EDIT:  That's with the LiveCD.  If you already installed Linux from the alternate CD I don't know about that

---

### Post by southernman on 2007-05-20
Try this megan:

> When you boot into the box you are usually presented with a few options from GRUB. One of these options is to boot into "Recovery" mode or what is called "single user" mode. This will boot the kernel and drop you to just a plain root console. 

Excerpt taken from [this thread]("http://ubuntuforums.org/showthread.php?t=425229&highlight=drop+into+console"), the second post.

[edited] Then proceed with the sticky howto...

---

### Post by meegs on 2007-05-20
Ok well, just to be clear, I have already installed Ubuntu 7.04 using the Alternate disk.

The install went fine

I can boot into Windows XP, no problems

When I try and boot into Ubuntu....it starts loading and then the orange bar stalls and nothin happens for a long time!

So, I suspected it had something to do with the ATI Radeon graphics card I currently have installed and hence my goal was to install using alternate cd, boot into ubuntu and apply the sticky reccommended by Sef.

Unfortunately for me....I can't seem to get into ubuntu to do this. 

At this point....I'm really not sure what to do...

I only recently go this ATI Radeon graphics card, and previously used the on-board intel motherboard one....am beginning to wonder if it will be easier to just take out the offending graphics card and see if things work better.

Also...could it be something other than graphics card???

Megan

---

### Post by meegs on 2007-05-20
Steve,

tried the recovery mode boot and as soon as it starts "loading hardward drivers" it goes into a bit of tail spin and spits out a whole bunch of text and then stalls

.....still not in.... :(

---

### Post by Parmenion on 2007-05-20
In my opinion, your best bet is to take out the offending card and let Ubuntu load naturally. Then go according to the sticky and install the drivers. Afterwhich, put the card back in and test.

---

### Post by southernman on 2007-05-20
> it goes into a bit of tail spin and spits out a whole bunch of text **and then stalls**

Ok. When it stalls, what is the last line of text?

---

### Post by Bartender on 2007-05-20
meegs -
Definitely.  Go back to the Winodws side and uninstall the Radeon.  I had one of those stupid 9200's and it gave me fits in Linux.
When you pull the card your motherboard may automatically go back to the onboard, but you better check BIOS settings to make sure it's going to onboard first.
Then try Linux side again.
If you want to add a vid card stick to Nvidia.  I put an ASUS V9400 in mine to replace the ATI 9200 and no problems.

---

### Post by southernman on 2007-05-20
> **Parmenion said:**
> In my opinion, your best bet is to take out the offending card and let Ubuntu load naturally. Then go according to the sticky and install the drivers. Afterwhich, put the card back in and test.
I started to suggest this, but would have prefaced it with: Does your system (motherboard) have an onboard video?

It would be where your IO shield is... eg. serial, usb, ethernet ports are.

---

### Post by meegs on 2007-05-20
ok well, surprise!! I'm stuck again!

I can't figure out how to get rid of the old card and get it working from the onboard stuff...

I uninstalled the software for radeon card in windows

When I go to the bios it won't let me pick anything except PCI/Internal VGA and there doesn't seem to be an option for Internal as priority....

Soo then when I just take out the PCI card and re-boot....I don't get nothin and I have to put it back in and re-boot.

oh and if I leave the PCI card in and reboot, things seem ok except that when I boot into windows I have to plug the monitor into the onboard card!!!

any advice..?

---

### Post by southernman on 2007-05-20
> oh and if I leave the PCI card in and reboot, things seem okYou mean in ubuntu, right? If that's what ya mean, you'll be able to get into a terminal window and proceed with the howto given ya. At the end, instead of rebooting, do a *shutdown now *command and reinstall your ATI card.

Of course you'll have to reinstall the drivers in winders also. Plug your monitor back into the onboard slot, reinstall drivers and you should be good to go.

> when I boot into windows I have to plug the monitor into the onboard card!!!
Surely your aware this is because you uninstalled the drivers for your ATI card

---

### Post by meegs on 2007-05-20
Hey, 

Sorted out some stuff....

I got my onboard graphics card to work (my bios had some weird settings I had to sort out). So I then loaded ubuntu and it was sweet except X wouldn't work, so y'know I just loaded into command line, which...y'know is ok for now, so I typed in all the stuff it told me to in the sticky....

except at the end when it says...

Configure /etc/X11/xorg.conf    <<<do I need to type this bit?
Code:
     sudo aticonfig --initial
     sudo aticonfig --overlay-type=Xv <<<<do I just type the X or do I put the number of my ATI card in??

---

### Post by southernman on 2007-05-20
Nice job, Megan!

Only enter (type or c&p) the commands that Mike wrapped in the quote tags:
> sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

No - to the last question you asked.

I'll wait and see how this comes out before hitting the rack... :)

---

### Post by meegs on 2007-05-20
I have now re-done the sticky instructions....

word for word, it all seemed to work ok....

but I still can't get ubuntu to work....my original problem hasn't changed at all

---

### Post by southernman on 2007-05-20
Daurn Megan... I can't hold out any longer! Have to get some sleep.

Sorry I couldn't help ya more... someone will.

I'll check back on ya later, after checking for holes in my eyelids for a while!

---

