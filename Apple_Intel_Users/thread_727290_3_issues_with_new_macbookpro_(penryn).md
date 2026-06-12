---
title: "3 issues with new macbookpro (penryn)"
date: 2008-03-17
forum: Apple Intel Users
---

### Post by amonsul on 2008-03-17
Hi!

So, im got my MacbookPro with Penryn

But now i have a couple of problems. I will list you my 3 most important:

1) No Wifi
I have tested this solution but no way
[https://help.ubuntu.com/community/Macbook_Air#head-146f51398e2debca46f8962a0c51dc0eee7a4ba7](https://help.ubuntu.com/community/Macbook_Air#head-146f51398e2debca46f8962a0c51dc0eee7a4ba7)

2) Without mouse how can i make a right click?

3) I have a fat32 partition, but only ubuntu can access to it.... and from mac no way!


Could someone help me?
Thanks!

---

### Post by cyberdork33 on 2008-03-17
Use the windows driver from the restore dvd with ndiswrapper for WiFi.

The touchpad is still very limited as it is completely new hardware.

No idea why your FAT32 partition is not showing up in OS X.

---

### Post by DrAma999 on 2008-03-17
For doing the right click you can use the touchpad and the keyboard... take a look at this tutorial, the most of tips are good also for owr new MBP [https://wiki.ubuntu.com/MacBookPro](https://wiki.ubuntu.com/MacBookPro)
Unfortunately i wasn't able to make the airport works with a wpa encrypted lan.
Ciao

---

### Post by amonsul on 2008-03-18
The Problem with the FAT32 Partition that in OSX the partition is only readable and not writeable! How can i change this?

Bye

---

### Post by amonsul on 2008-03-18
1) How can i checkup if the broadcom driver is recognized?

2) still no solution?

3) I have reformatted the fat32 disk in OSX, and now it works. I dont know why but ok it works :)

---

### Post by amonsul on 2008-03-18
EHM, Im using hardy! Maybe this explains some issues :(

Ciao

---

### Post by cyberdork33 on 2008-03-18
> **amonsul said:**
> EHM, Im using hardy! Maybe this explains some issues I have heard that there are some other people having problems with ndiswrapper in hardy. I would file a bug report and hopefully it will get fixed.

You could also try compiling the latest version of ndiswrapper:
[http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)

---

### Post by amonsul on 2008-03-19
Another day without wireless.

I have tried to do following things
1) use bcmwl5.inf from Broadcam 
...it doesnt work so i had to remove all installed drivers and...
2) use bcmwl6.inf from the Mac OSX original CD
...it doesnt work so i had to remove all installed drivers and...
3) to use ndisgtk GUI to install the drivers

Nothing.....
So what can i do?

---

### Post by cyberdork33 on 2008-03-19
> **amonsul said:**
> Another day without wireless.

I have tried to do following things
1) use bcmwl5.inf from Broadcam 
...it doesnt work so i had to remove all installed drivers and...
2) use bcmwl6.inf from the Mac OSX original CD
...it doesnt work so i had to remove all installed drivers and...
3) to use ndisgtk GUI to install the drivers

Nothing.....
So what can i do?ok, you have to understand that there is not one file out there named bcmwl5.inf. Each one is different for specific hardware.

The driver from the restore dvd that came with your machine is the only driver that is known to work. If you are still having problems, it is likely a bug in Hardy. The best thing you can do if give detailed information about the problem in a bug report and hope for a fix.

---

### Post by eitan on 2008-03-20
i have a macbook pro fourth generation.  the wifi didn't work out of the box.
i followed the instructions at [http://ndiswrapper.sf.net/](http://ndiswrapper.sf.net/)
which i thought were excellent.

this worked, almost:  i had to manuall rmmod ssb and reload the ndiswrapper
module to make it work, because ssb was conflicting.

i was able to resolve this by editing /etc/modprobe.d/blacklist.

i added this line:
blacklist ssb

and also had to comment this line:
#blacklist bcm43xx

if i recall correctly.

---

### Post by eitan on 2008-03-20
i'm also running a macbook pro 4,1 with hardy.

is your fn key working?  that's my main problem right now.

..besides x crashing when i try to touch openoffice.
oh.. and x crashing when i try to tweak the keyboard layout.

---

### Post by cyberdork33 on 2008-03-20
you want to keep bcm43xx blacklisted. There is no reason for it.

---

### Post by eitan on 2008-03-21
it seems that not blacklisting bcm43xx has the pleasant
side effect of not loading ssb, which solves my wifi problem
by letting ndiswrapper load without any conflicts.

i don't know why, but blacklisting ssb directly had no effect.

i know basically nothing about the linux kernel.  and i don't
really have countless hours to try and figure this out.
i've already skimmed through a bunch of conversations
on ubuntuforums and read parts of the ubuntu wiki and
read the documentation on ndiswrapper.

so what choice do i have?  for some reason i like ubuntu
and the final release of hardy is around the corner.  so installing
it now made sense to me.

anyhow, wifi is working for me just fine now.  my big problem
is that i have no home/end/pgup/pgdown/delete and other keys.
this really hurts.  and the other two problems i mentioned:
how certain specific activities will just kill x.  i have presentations
i need to put together and i can't touch openoffice because it
clobbers x instantaneously/repeatedly/reliably.

same with fiddling with the keyboard layouts in gnome.  that's a total
mistery to me. what's the point of specifying what keyboard you have
(i specified apple->macbook pro) if it does nothing?  plus, isn't the
keyboard layout already specified in xorg.cong anyway?  so which
wins?
the macbook pro's keyboard layout hasn't changed in like five years.
and yet it can't detect my fn key..  :confused:  totally confused.

anyways, thanks for the advice.. :-)


/ eitan

---

### Post by amonsul on 2008-03-21
OOOK!
Wifi is now working! But dont ask me how i have done it! :)


WHat surely helps is following:

> 
i added this line:
blacklist ssb

and also had to comment this line:
#blacklist bcm43xx

and to use the bcmwl5 and not the bcmwl6 driver!


Could someone write a wiki for the new macbookPros? We have to put togheter some information....


So what doesnt work now?
pommed doesnt help me and yeah FN key doesnt work!

I have pommed 1.16 installed, but it doesnt work.

you can try it adding this lines in your sourceslist
deb [http://ppa.launchpad.net/mactel-support/ubuntu](http://ppa.launchpad.net/mactel-support/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/mactel-support/ubuntu](http://ppa.launchpad.net/mactel-support/ubuntu) hardy main

Ciao

---

### Post by dabeeeenster on 2008-03-21
Could someone possibly write a mini-howto to explain what they did to get the wifi working from a vanilla install?

---

### Post by cyberdork33 on 2008-03-21
> **eitan said:**
> it seems that not blacklisting bcm43xx has the pleasant
side effect of not loading ssb, which solves my wifi problem
by letting ndiswrapper load without any conflicts.

i don't know why, but blacklisting ssb directly had no effect.Interesting, and if it works, then it works. so I guess that is ok. It is likely setup to have bcm43xx (which is another broadcom driver) block ssb when it loads because it causes issues, and a similar thing needs to be done for ndiswrapper likely. Here are some instructions that someone else is using, as well as a link to the bug report about it:
[http://ubuntuforums.org/showpost.php?p=4540521&postcount=62](http://ubuntuforums.org/showpost.php?p=4540521&postcount=62)

There is also apparently a more permanent fix shown here (minus the part about using the Dell driver):
[http://ubuntuforums.org/showpost.php?p=4557950&postcount=72](http://ubuntuforums.org/showpost.php?p=4557950&postcount=72)

> so what choice do i have?  for some reason i like ubuntu
and the final release of hardy is around the corner.  so installing
it now made sense to me.

anyhow, wifi is working for me just fine now.  my big problem
is that i have no home/end/pgup/pgdown/delete and other keys.
this really hurts.  and the other two problems i mentioned:
how certain specific activities will just kill x.  i have presentations
i need to put together and i can't touch openoffice because it
clobbers x instantaneously/repeatedly/reliably. The beta looks very good. Still some issues with bluetooth. Delete is Fn+Backspace, and Home, End, etc, is some Fn-combo with the arrow keys. Some people are having issues with the Fn keys completely not working. Are you this is not your issue? I haven't experienced any of the OO.org issues you are talking about. are you sure you are up to date? I was having major issues with my last install (even after completely updating) until I reinstalled from the latest beta release, so you might try that unless you just want to stick it out until final.

> same with fiddling with the keyboard layouts in gnome.  that's a total
mistery to me. what's the point of specifying what keyboard you have
(i specified apple->macbook pro) if it does nothing?  plus, isn't the
keyboard layout already specified in xorg.cong anyway?  so which
wins?
the macbook pro's keyboard layout hasn't changed in like five years.
and yet it can't detect my fn key..  :confused:  totally confused.Apple keyboards pretty much send unique keycodes so there is not really a need to change your keyboard, but I remember it being helpful for some people on portables as it changed how the F1, F2, etc keys worked or something... either way it doesn't matter... X and gnome are two different things, the gnome settings apply, well, in gnome, and will likely override what is in Xorg, but you can run other window managers or desktop environments that rely on Xorg's keyboard layout.

> **amonsul said:**
> Could someone write a wiki for the new macbookPros? We have to put togheter some information.... You seem to know what needs to be changed to make it work, so why do you not make the edits to the wiki?


If pommed is not working then uninstall it. I just compiled the raw source for the PPA, you can go to the pommed site and try to get some more information.

You should check if your keyboard bug is reported and add your information to it..
[https://bugs.edge.launchpad.net/ubuntu/+bugs?field.searchtext=Fn+key&orderby=-datecreated](https://bugs.edge.launchpad.net/ubuntu/+bugs?field.searchtext=Fn+key&orderby=-datecreated)

If you can't find something that sounds like your bug then report a new one:
[https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)

Issues like this will not get fixed unless you tell the devs that something is wrong.

---

### Post by amonsul on 2008-03-22
uhhhhhhhhh!
After one update Wifi doesnt work anymore! I can see the wireless network but i cant make the login!

There is a big need for a HOW-TO for macbbokpro penryn that can solve the problem for ever!
:(


ciao

---

### Post by cyberdork33 on 2008-03-22
> **amonsul said:**
> There is a big need for a HOW-TO for macbbokpro penryn that can solve the problem for ever!
There is a need for a lot of how-tos. Complaining won't make it happen faster.

I don't know why you are having so many issues. If you can see networks, then your card is working.

---

### Post by eitan on 2008-03-24
> The beta looks very good. Still some issues with bluetooth. Delete is Fn+Backspace, and Home, End, etc, is some Fn-combo with the arrow keys. Some people are having issues with the Fn keys completely not working. Are you this is not your issue?

yes, my issue is that the fn key completely does not work.

> I haven't experienced any of the OO.org issues you are talking about. are you sure you are up to date?
that's what apt-get tells me.  i do apt-get update and apt-get upgrade daily.

> I was having major issues with my last install (even after completely updating) until I reinstalled from the latest beta release, so you might try that unless you just want to stick it out until final.

i think your suggestion to reinstall using the beta release is a great idea.
any advice on the best way to go about this?  backup my home dir,
nuke the partition and reinstall from scratch?  is there a shortcut?  perhaps
instructing the current distribution to magically "upgrade" to the beta cd?

thanks,
/ eitan

---

### Post by cyberdork33 on 2008-03-24
> **eitan said:**
> i think your suggestion to reinstall using the beta release is a great idea.
any advice on the best way to go about this?  backup my home dir,
nuke the partition and reinstall from scratch?  is there a shortcut?  perhaps
instructing the current distribution to magically "upgrade" to the beta cd?basically upgrading is what you want to avoid. just backup the files you want to keep, then start the installer, using the manual method to specify the existing partitions to use (and be sure to tell it to reformat them)

The Fn key thing is a big issue, and it is not something that is easily fixed. Follow the bug reports and contribute where you can and hopefully it will get fixed.

---

### Post by eitan on 2008-03-25
> **cyberdork33 said:**
> basically upgrading is what you want to avoid. just backup the files you want to keep, then start the installer, using the manual method to specify the existing partitions to use (and be sure to tell it to reformat them)

i was afraid of this.

> The Fn key thing is a big issue, and it is not something that is easily fixed. Follow the bug reports and contribute where you can and hopefully it will get fixed.

i think i'm going to wait until the next linux image update and if things don't
get better, i will likely then proceed with a reinstall.

thanks,
/ eitan

---

### Post by eitan on 2008-03-25
i looked into this issue some more.
came across this link:
  [http://gentoo-wiki.com/HARDWARE_Apple_MacBook#Apple_Keyboard](http://gentoo-wiki.com/HARDWARE_Apple_MacBook#Apple_Keyboard)
where the author states that he had to recompile the kernel
with a revision to hid-quirks.c to correct the device id for
the apple internal keyboard... to make the fn key work.
i have verified that running xev and pressing the fn key
echos nothing (pretty much every other key on my keyboard
is detected).

the correct device id on my system (macbook pro fourth gen)
appears to be 0x0230 whereas the source file says 0x021b
for the constant USB_DEVICE_ID_APPLE_GEYSER4_ISO

i'm surprised this kind of information can't be specified 
without requiring the recompilation of the kernel.

/ eitan

---

### Post by cyberdork33 on 2008-03-25
I thought there was already a bug report on the keyboard IDs, and that it was fixed, but I cannot find it now. That gentoo document is old though, but if you can get a fix from it more power to you.

Ok here it is. It may need another patching though for newer keyboards...
[https://bugs.edge.launchpad.net/ubuntu/+source/linux-meta/+bug/162083](https://bugs.edge.launchpad.net/ubuntu/+source/linux-meta/+bug/162083)

---

### Post by eitan on 2008-03-25
the bug report on keyboard id's doesn't include the fourth generation
macbook pros.

i verified my theory.  i just compiled a custom kernel with the revised
device id for the fn key and it worked.

the problem with the new kernel is that for some reason the nvidia
restricted-driver is not loaded / doesn't show up.  so it uses a generic
display driver with a low resolution.  not sure how to address that.
i noticed the mactel repository also publishes its own restricted drivers
module and synaptic complains when i ask to install it.

anywho.. thanks for the help.

/ eitan

---

### Post by cyberdork33 on 2008-03-26
> **eitan said:**
> the bug report on keyboard id's doesn't include the fourth generation
macbook pros.

i verified my theory.  i just compiled a custom kernel with the revised
device id for the fn key and it worked.

the problem with the new kernel is that for some reason the nvidia
restricted-driver is not loaded / doesn't show up.  so it uses a generic
display driver with a low resolution.  not sure how to address that.
i noticed the mactel repository also publishes its own restricted drivers
module and synaptic complains when i ask to install it.

anywho.. thanks for the help.

/ eitanThe nvidia driver is compiled against a specific kernel so if you compile your own kernel, then you have to compile the nvidia driver. The mactel PPA has a couple of pseudo-packages to work around that issue since the modules in the normal repo are technically compatible (same kernel version).

If you can post a patch then Seq can update the mactel kernel to include your changes. I would also either add to the existing bug report or create a new one with the fix instructions so that this can get implemented in the Main Ubuntu kernel.

---

### Post by eitan on 2008-03-26
> **cyberdork33 said:**
> The nvidia driver is compiled against a specific kernel so if you compile your own kernel, then you have to compile the nvidia driver. The mactel PPA has a couple of pseudo-packages to work around that issue since the modules in the normal repo are technically compatible (same kernel version).

thanks, i'll take a look..

> If you can post a patch then Seq can update the mactel kernel to include your changes. I would also either add to the existing bug report or create a new one with the fix instructions so that this can get implemented in the Main Ubuntu kernel.

done:
[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/207127](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/207127)

thanks,
/ eitan

---

### Post by Neffscape on 2008-03-27
I have a dream: an installable metapackage to make possible for every "human" to automatically install and configure things on apple hardware. Why is it so hard to install ubuntu on Apple Hardware? In my opinion this would be feaseable, also because Apple computers are distributed in very standard configurations worldwide and they are not so frequently updated...

---

### Post by cyberdork33 on 2008-03-27
> **Neffscape said:**
> I have a dream: an installable metapackage to make possible for every "human" to automatically install and configure things on apple hardware. Why is it so hard to install ubuntu on Apple Hardware? In my opinion this would be feaseable, also because Apple computers are distributed in very standard configurations worldwide and they are not so frequently updated...
We are working on something like that... See the mactel-support ppa and launchpad team.

There are two big issues though.

1. Apple continually updates hardware with fresh, new hardware all the time... this makes it very difficult to keep up with the changes, especially when...
2. those changes include new, before unseen, proprietary hardware with closed drivers that CANNOT be included in Linux because the licensing is incompatible.

---

### Post by shiver on 2008-04-14
I compiled a custom kernel with the change suggested in the bug report mentioned above to get the fn key working. Today when I booted Ubuntu for the second time with the fixed kernel, the key just stopped working again. I double checked that I'm running the correct kernel but now it seems as if I had never done anything. By the way, has anyone got sound working? The mixer shows all sliders it should and they're not muted, but nothing comes out.

---

### Post by eitan on 2008-04-14
sound works fine for me, using the santarosa instructions.
i am still running the standard kernel until i take the time
to find a good set of instructions for compiling a kernel
along with all the modules i need (restricted modules,
etc..)

/ eitan

---

