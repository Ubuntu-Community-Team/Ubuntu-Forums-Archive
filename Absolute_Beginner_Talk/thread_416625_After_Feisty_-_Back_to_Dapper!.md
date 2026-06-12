---
title: "After Feisty - Back to Dapper!"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by hinne on 2007-04-21
Just wondering if others had this experience -- I had everything working on Dapper in October last year. Especially Xgl/Compiz/Beryl and WPA wireless on a Compaq Presario V2000 laptop and it worked like a charm.

In October 2006 I upgraded (through a fresh install) to Edgy and have not been able to get Compiz/Beryl to work since then even though I tried a number of times with a fresh machine etc. 

With an upgrade to Feisty the Wireless broke as well. I use WPA and while the card authenticates with my access point (Dlink 504T), it does not show as 'authorised' and does not get an IP address from the DHCP server. The 'desktop effects' don't work either.

Some browsing of these forums and the launchpad bugs shows me I am not alone in this experience.

I have today rebuilt the laptop on Dapper and got everything working again in a couple of hours. The only thing I really don't like about Dapper is the bootup screen, but I can live with that.

Nevertheless I am puzzled that in my experience the newer releases progessively seem to break functionality I had fairly painlessly on Dapper...

I'm not exactly a newbie either. Been a linux only user since about 1998...

EDIT: The wireles card shows as 'authenticated' but not as 'authorised'.

---

### Post by AusIV4 on 2007-04-21
Right after Edgy came out, I upgraded, then went back to Dapper. About a month later, I found that Edgy was satisfactory for all but one of my machines, so I upgraded.

Yesterday I tried upgrading one machine as a test, to see about the state of feisty. 
[LIST]
[*]Sound didn't work. 
[*]Wireless worked, but it often quit working after hibernate or suspend. (neither of which worked without some tweaking)
[*]It hangs for 30 seconds at a time - supposedly this can be solved by putting a CD in the drive, but it hasn't worked for me.
[*]The VPN client I use, Kvpnc, hasn't been working properly, which means I can't log on to my campus wireless network.
[*] Beryl, for whatever reason, was downgraded from 0.2.0 to 0.2.0 RC3. These may be the same version, but it seems unprofessional having an RC when a later release has been available for quite a while.[/LIST]
Since I had backed up my root partition, and I keep my home folder on another partition, it was very easy to revert to my edgy install. I'll give it a few weeks, and once the majority of my problems have been fixed, I'll boot back to my feisty partition and see how it does, then consider putting it on my other computers, but for the time being I need it to be reliable.

---

### Post by RustyWyatt on 2007-04-21
Howdy AusIV4,

I am a relatively new Ubuntu user who was very happy with 6.10 until I tried to install Vertualbox.  Now my system is very broken.  I will wait until the dust settle on 7.x before installing it (I'm running on a WinXP partition until then;( ). 

Your statement below really interest me as a future way for my to minimize the impact of having a major system failure.

Could you please expand your comments below so a newbie can duplicate your set up?

All information GREATLY appreciated!

Thanks,
Tom

"...Since I had backed up my root partition, and I keep my home folder on another partition, it was very easy to revert to my edgy install. I'll give it a few weeks, and once the majority of my problems have been fixed, I'll boot back to my feisty partition and see how it does, then consider putting it on my other computers, but for the time being I need it to be reliable...."

---

### Post by hinne on 2007-04-21
Linux doesn't have C: or D: drives like windows. The root partition is the '/' partition, the home partition is under '/home'. What you can do when you install Linux is to define different 'mount points' for these partitions and then you can reformat only the one where you want the new operating system to go. I commonly have a '/' parition and '/home' on different mount points. When I install a new version I just go into the manual partitioning and tell it not to reformat '/home'. Have a play with the installer on a machine and go into the manual mode-then you can see what I mean.

---

### Post by loserboy on 2007-04-21
dapper is the LTS version right now, as far as I know edgy and feisty are meant to be the latest and greatest so this sort of thing is to be expected till the next LTS version comes out.

---

### Post by kittyhawk63 on 2007-04-21
> **loserboy said:**
> dapper is the LTS version right now, as far as I know edgy and feisty are meant to be the latest and greatest so this sort of thing is to be expected till the next LTS version comes out.

loserboy,
Feisty is a LTS.

Later Edit: I must have heard wrong. Sorry. I checked it out, and you are soooooo right!

---

### Post by oilchangeguy on 2007-04-21
> **kittyhawk63 said:**
> loserboy,
Feisty is a LTS.
uh, NO! the next LTS will NOT be available until 2009!

---

### Post by Nightmist on 2007-04-21
> **hinne said:**
> Linux doesn't have C: or D: drives like windows. The root partition is the '/' partition, the home partition is under '/home'. What you can do when you install Linux is to define different 'mount points' for these partitions and then you can reformat only the one where you want the new operating system to go. I commonly have a '/' parition and '/home' on different mount points. When I install a new version I just go into the manual partitioning and tell it not to reformat '/home'. Have a play with the installer on a machine and go into the manual mode-then you can see what I mean.

Is it a simple procedure to split a current Linux installation into / and /home on two partitions instead of the one they are sharing now?

---

### Post by bulldog on 2007-04-21
> **kittyhawk63 said:**
> loserboy,
Feisty is a LTS.

I think you're not well  informed about that.
Feisty isn't a LTS release like Dapper is.

it's just like loserboy stated,a new release with the latest greatest applications,no more no less :)

---

### Post by halitech on 2007-04-21
> **oilchangeguy said:**
> uh, NO! the next LTS will NOT be available until 2009!

2009 is even a guess at this point. from what I've heard, LTS versions are decided upon not by date, but by how stable the system is and if they've done everything they aimed to do. If they have done that, then a LTS version will be released and given 3/5 years support instead of the normal 18 months. The projected date for the next one is 2009 (would make sense to have 1 before Dapper drops support) but could be late 2008, early 2009, might not happen again ever.Will have to see how things go.

---

### Post by hinne on 2007-04-21
> **Nightmist said:**
> Is it a simple procedure to split a current Linux installation into / and /home on two partitions instead of the one they are sharing now?

That depends -- if you still have an unpartitioned section on the disk it can be done, if you don't then it needs a reinstall.

If you still have an unpartiitoned section on your current disk google qtparted and that will let you do it. Maybe you need to boot from a live CD to do this.

---

### Post by Cat.Food on 2007-04-21
I'm pretty new to GNU/Linux as well as Ubuntu.  I've been playing around with Dapper for the past few weeks and had it working pretty well.  My hardware is pretty old, so after trying compiz and beryl and seeing how they worked on my old GeForce 3, I removed them.  They look really cool, but other than that, I don't see the point...

So, I backed up my stuff, wiped the hard drive, and installed Feisty yesterday.  I dunno what it is with this new version of Ubuntu, but Firefox crashes like crazy!  Not only that, but it occasionally locks up X completely!  I dunno what the deal is, because Dapper worked just fine...

So today, I went back to Dapper...  You're not alone...

---

### Post by in_flu_ence on 2007-04-21
> **hinne said:**
> Just wondering if others had this experience -- I had everything working on Dapper in October last year. Especially Xgl/Compiz/Beryl and WPA wireless on a Compaq Presario V2000 laptop and it worked like a charm.

In October 2006 I upgraded (through a fresh install) to Edgy and have not been able to get Compiz/Beryl to work since then even though I tried a number of times with a fresh machine etc. 

With an upgrade to Feisty the Wireless broke as well. I use WPA and while the card authenticates with my access point (Dlink 504T), it does not show as 'authorised' and does not get an IP address from the DHCP server. The 'desktop effects' don't work either.

Some browsing of these forums and the launchpad bugs shows me I am not alone in this experience.

I have today rebuilt the laptop on Dapper and got everything working again in a couple of hours. The only thing I really don't like about Dapper is the bootup screen, but I can live with that.

Nevertheless I am puzzled that in my experience the newer releases progessively seem to break functionality I had fairly painlessly on Dapper...

I'm not exactly a newbie either. Been a linux only user since about 1998...

EDIT: The wireles card shows as 'authenticated' but not as 'authorised'.

I use a compaq v2000 and compiz runs ok with it in edgy and feisty. I just download the package from synaptic. wireless is ok for me on various locations so it is strange that yours don't work. I have things working pretty out of the box.

---

### Post by AusIV4 on 2007-04-22
> **RustyWyatt said:**
> Howdy AusIV4,

I am a relatively new Ubuntu user who was very happy with 6.10 until I tried to install Vertualbox.  Now my system is very broken.  I will wait until the dust settle on 7.x before installing it (I'm running on a WinXP partition until then;( ). 

Your statement below really interest me as a future way for my to minimize the impact of having a major system failure.

Could you please expand your comments below so a newbie can duplicate your set up?

All information GREATLY appreciated!

Thanks,
Tom

"...Since I had backed up my root partition, and I keep my home folder on another partition, it was very easy to revert to my edgy install. I'll give it a few weeks, and once the majority of my problems have been fixed, I'll boot back to my feisty partition and see how it does, then consider putting it on my other computers, but for the time being I need it to be reliable...."

I think the next post kind of answered this question, but I'll try and go into a bit more detail.

My laptop's hard drive is 40 GB (small I know, but it's all I need for taking notes in class). When Ubuntu installs, it makes a 39 GB root partition, and a 1 GB swap partition.

I booted up a live CD and opened GParted. I resized the root partition to about 40% of its original size. For me, this included all the essential files, and the data in my home directory. If your home directory is already bigger than 40%, I'd recommend finding some kind of external storage to back it up. I Then format the remaining 60% as ext3. Now you need to copy your data from the home folder on your old partition to the new home partition. Open up a terminal and make two new directories (mkdir <directory>). I'd call these directories 'fs' and 'home'.

Next, you need to mount the partitions to the appropriate mount points. In my case, hda1 is the root file system, and hda 3 is home (I'm not sure what happened to hda2). I would type ```
$ mount /dev/hda1 ~/fs
$ mount /dev/hda3 ~/home

```
Now you have both devices mounted and data is ready to be copied. cd into the fs/home directory. This is where all your user data is held. From this directory, type the following:
```

$ sudo cp -a ./ ~/home/

```
cp is the command to copy files from one location to another. './' is your current location (should be ~/fs/home/), and ~/home/ is where you mounted your new home partition. The -a flag tells cp that it is recursive, and needs to keep the files permissions intact, along with a few other things.

This next part gets a little tricky. It used to be that I would just modify /etc/fstab and tell it to mount /dev/hda3 at the location /home. Since udev has taken off, and you need a device's UUID, I find it easier to use GUI methods. Unfortunately, I'm a KDE user, and don't know how this works in Gnome.

Once you boot back into your normal installation, go to System Settings -> Advanced -> Disks & Filesystems. Here, you will see a list of disks and partitions. Enter administrator mode, and it will allow you to modify mount points for the devices. For the device that represents 60% of your space, click modify, and on the line that says Mount Point: type ```
/home
```

Restart your computer and you should now find that your /home/ directory is on a separate partition from your root directory. To confirm this, in Nautlius or Konqueror, right click somewhere in the home folder and go to properties. It should tell you the maximum amount of data that can be held within a folder. This should vary between your home directory and the root partition.

Once you've confirmed that your home directory is in tact on a separate partition, you can go back to a live CD, mount the file system as we did before, cd into the old ~/fs/home directory, and type ```
$ sudo rm ./ -r
```
This will remove all of the data in that directory, while leaving the directory in place.

Now, if you're wanting to install another copy (or version) of Ubuntu, load up the CD for the version you want to install with. Open up Gparted again, and shrink down your root partition. You'll need to leave a little bit of space for your file system to grow, but 4-5 GB should be enough. Partition the remaining spaces as ext3.

Go through the installation steps as you normally would until you get to the Prepare Disk Space screen.  Slect manual, and continue. This will put you on a screen that allows you to specify mount points for all of your partitions. By default, all will be mounted to /media/<device name>. Select the newly created partition, and hit the Edit Partition button. Specify the mount point as '/'. Then select your home partition, edit, and specify the mount point as '/home'. DO NOT mark the Format checkbox, as this will erase your data.

Continue through the installation process normally. When you reboot, you should find yourself on a familiar desktop, but with a new version of Ubuntu. You'll have to reinstall your programs, and desktop icons that point to programs you haven't installed won't do anything. If you have problems with your new installation, you can use grub to boot back to your familiar installation.

Hopefully all this makes sense. If anyone has questions, PM me, as I don't imagine I'll be back on this thread very often.

---

### Post by RustyWyatt on 2007-04-22
Thanks VERY much AusIV4!

I'll work on this as I rebuild my system as it seems like a GREAT solution for future projects.

Tom

---

### Post by stevieb on 2007-05-05
i went back to dapper as well; having had problems in both edgy (nautilis crashing) and feisty (substandard wireless signal strength/speed).  i have a lenovo 3000 c100.

the only things i miss from feisty are suspend and beryl.  would i get those back by upgrading the kernel to 2.6.20/21?

-steve

---

### Post by in_flu_ence on 2007-05-05
'substandard wireless signal strength'

I am not too sure. I always have only 1 bar in my network manager even though the router is next to my PC.

I think i had similar thing in edgy but apparently internet and download works fine. Fairly good speed.

---

### Post by stevieb on 2007-05-05
i understand, but in my case there was a definite difference.  at first i thought that, since the drivers arent' native, network manager would just show 100% or nothing.  but after switching to feisty, i found i couldn't use my laptop in many places in my house and workplace that i could under dapper, and now that i'm back to dapper, it works in those places again.  i also did speed tests ([www.speakeasy.net](www.speakeasy.net)) and got better results in dapper.

-steve

---

### Post by jerrylamos on 2007-05-05
This is rather telling from the weekly newsletter:

"Tollef Fog Heen has announced that the next release, Gutsy Gibbon, is ready for development. The main purpose of Gutsy is improvement and quality. There will not be much in terms of new or experimental features but stabilising and polishing the existing features."

Reading between the lines, and wishful thinking, they will attempt to "fix the bugs" in Feisty.  On Feisty, they had significant bugs outstanding but chose to stick to the release schedule.  Their choice.  My view some of the bugs introduced with "experimental features" they hastily put in Feisty are technically complicated and will take work to fix.  I'm not convinced 6 months will be long enough to do the job.

From the forums, some systems work better with Feisty, some systems break.  I run Dapper, Feisty, and this partial upgrade to Gutsy - new kernel 2.6.22-1, some new packages, still has most of Feisty's bugs plus.

So whichever release works, "the shoe fits", do it!

Cheers, Jerry:confused:

---

### Post by Pistolla on 2007-05-06
Out of curiosity, when i was wanting to see what the difference with Feisty as opposed to Edgy and not much just more internal. But after i upgraded to feisty of which i have no probs (i suppose my machine is one of the ones that didn't break) However, i kept seeing people reverted back to Dapper. Methinks for the LTS aspect and that has me thinkin' can i revert back to Dapper (and need to know what avenue to go down) and will i "bork" my system? And if i go back to Dapper, will i also have to revert to "older" software? I know picayune at best but more or less curios.
Pistolla

---

