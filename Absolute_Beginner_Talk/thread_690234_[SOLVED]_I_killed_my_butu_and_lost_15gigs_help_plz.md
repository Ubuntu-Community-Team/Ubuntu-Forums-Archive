---
title: "[SOLVED] I killed my butu and lost 15gigs help plz..."
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by WFGeppetto on 2008-02-07
Ok, begin story of stupidity:

I was very tired...I had Feisty Fawn running dual boot on my laptop with Vista.  It wouldn't boot a live cd, or boot from cd at all regardless of my bios settings, so I used [url=http://wubi-installer.org/]wubi installer.  It worked like a charm.

Important note: I'm a noob.

It doesn't actually partition the drive, it somehow installs on the main partition along with windows, and at boot gives the option of which OS, I don't know exactly how it works, but it begins the install in windows, and you can completely uninstall from windows.  Very user friendly for a linux test driver, and it gives the option of install size.  I suppose a virtual drive or something.  I ran it once, and loved it, but goofed my network manager trying to figure out wireless, and I had done so little that I just decided to uninstall, and start fresh.

With a bit more confidence, and thinking I'm liking Ubuntu, I installed 15gigs the second time around.  I cracked out last night trying to get everything working.  I figured out how to go wireless, but couldn't get it to stick after a boot, and somewhere along the way I lost sound.  My speakers wouldn't do jack, and no, it wasn't muted, or the gain turned down.  I took a break from ndiswrapper hell, and decided to figure out my speakers.  What is it ACDI or something?  Dunno, and I'm not looking right now, I'm frustrated.

1. thing to not do with linux:

browse forums thinking you know what's going on at 4 in the morning with a slew of new jargon and commands swimming in your head.

I found a post with a similar problem, and it mentioned turning off the ACDIwhatever thing at boot.  The guy then answered his own post, and said "Nvm, I just added <ACDI or whatever> = off in the kernel in something or other list file.

Sounds like a good idea.

2. thing not to do with linux:

*&^(^ with kernel or grub or any of that crap if you are a noob.

So I found the file, opened it, and edited it where it looked good.  I broke my linux.

On boot, it freaked, and would only let me try a command prompt (where be I impotent), and suggested chdsk in the error text above the prompt.

mkay, I figured I'll just uninstall it from windows.  I've done it once, and it worked fine.  Only, this time, it did a half baked uninstall because apparently (not surprisingly - like I said, I was tired) it needed the file I screwed to uninstall properly. 

Now, when I boot it still gives me the option of dual boot, but Ubuntu just craps out, and makes me restart, and in windows, I can no longer uninstall wubi, because it doesn't think it exists, and I can't reinstall either, I completely broke it apparently.  Worst of all, all that data is still there, and locking out my 15 gigs, and I can't even figure out how to see it.  It's not on a separate partition, and it's not like there's just a folder in windows for me to delete.

:(  can I has mah gigz bak plz?

---

### Post by emarkd on 2008-02-07
If I were you, the first thing I would try to do is get that Live CD booting so that I could fix that file and maybe recover everything.  Why won't your Live CD boot?  Will your computer boot any live CD?

If that won't work, there are projects out there that intend to allow you to mount ext filesystems from Windows.  This would allow you to access your Ubuntu files from within Windows and maybe fix that file from there, or at least copy off what you want to save before reinstalling.  I've never tried them, so I'm not recommending anything, but [here's]("http://linuxhelp.blogspot.com/2007/03/mount-ext2-or-ext3-partition-in-windows.html") a tutorial that may or may not work.

---

### Post by WFGeppetto on 2008-02-07
Thanks, I'll start reading, and looking around.

I need a break, a nap, etc.  I'm fully cracked out, and running on too little sleep.  I'll be back.

As for the boot disk, I dunno, I think it's a problem with these Gateway Laptops.  This is the third I got before it had a cdrom that didn't screw up.  It never booted from anything.  I tried several Isos even tried some USB bootable things, nothing would ever boot from my cd or usb.  I have no idea why.  My bios is set to check cd, and usb before HD, but it always reads them, and then just moves on to boot normally. 

Ah well, Thanks for replying, please pay attention to this thread if you have time, and send help this way if you know of it.  I learned a lot of "do nots" and I really want to become proficient with this stuff.  Plus, I'd hate to lose my 15 gigs.

---

### Post by WFGeppetto on 2008-02-07
k, I have a bit more to work with now.  I got a 7.10 live disk working, and am running from it trying to get my gigs back.

Now I'm here:

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

ubuntu@ubuntu:~$ 

I'm in over my head.

If I run my windows recovery, will it get it back?  I'm sure that the only right way is through the terminal, but I had to ask.

---

### Post by alzie on 2008-02-07
I'm confused.   

If this is a Wubi install that is broken, I would try a reinstall of the Wubi.   Wubi creates a virtual disk on your computer and I don't think that you have actually lost any hard drive (other than where the files are)

I don't know if you found the Wubi forums 
[http://ubuntuforums.org/forumdisplay.php?f=234](http://ubuntuforums.org/forumdisplay.php?f=234)

I started with Wubi and what I did like is if I messed it up I could just uninstall and reinstall and at reset what I had broken.

good luck

---

### Post by dsauxier on 2008-02-07
Disclaimer: I've never used wubi, so maybe this doesn't apply.

Can you get to the grub menu at all?
It sounds like adding a boot option is what messed things up, but that would only effect the boot option that changed (presumably the default boot-with-gui section)
If you can press <ESC> while grub is loading up (you have about 3 seconds to do this before it boots the default OS), then you should be able to select <Recovery Mode> (or something like that).
That would get you into command-line-only mode so that you can edit the file.

In command-line mode, you'll use vi to edit the file : 
$ vi /boot/grub/menu.lst

crash course in vi : 
j - move down a line
k - move up a line
x - delete the current character
i - enter insert mode
<ESC> - leave insert mode
I think those commands would give you the bare necessities for editing the file.
You can also search for text by pressing the "/" key, entering your case-sensitive search text, then pressing <ENTER>

---

### Post by WFGeppetto on 2008-03-08
I'm sorry, I should have followed up.  I am going to try to be a bit more responsible forum member.  It annoys me when I find a thread like this, and it isn't resolved, so I will follow up.

The wubi installer is what got me turned on to Ubuntu in the first place.  I can't say anything too bad about it, because I never would have gotten interested enough to follow up, and get a liveCD.  I have also seen threads about how to convert a wubi install into a separate partition, and make it dual boot.  That's all over my head though.

Thank you guys for trying to help, but I solved the problem on my own the hard way.

It was impossible to reinstal wubi correctly, and it was impossible to uninstall and save my lost storage.  A reinstall simply installed it again in a new area of the HDD, so that was out.  It would have been nice to get it back, but then I would probably have just uninstalled it, and reinstalled dual boot from a live CD.

My windows had become bloated (worse than usual) due to my addiction to trying new apps, and I had a little bit of a mess in there, so I decided to simply reinstall everything.  I backed up all the files that I wanted, and simply completely killed my computer.  I made a fresh install of Vista, which was nice, because I blocked the installation of a bunch of crap I didn't want, including annoying bungled Gateway apps, and my new Windows install was much much better.  Then, I just used the GG 7.10 (remarkably better equiped than Fiesty) and make a new install of Ubuntu.

Now, my system is like I want it, other than working out some kinks in Ubuntu that are common (ie: streaming, AWN applet problems, annoying need for multiple apps for dvd conversion and burning.)

For those that decide to use Wubi, I offer this advice:

Do not install anything weird.
Do not mess with the kernel.
Do not mess with boot files.
Do not gedit anything unless you know exactly what you are doing.

I don't know for sure, but I don't think there is an easy, or effective way to fix a busted Wubi install, and if you are using Wubi, rather than a proper installation, you probably don't know enough to mess around with that stuff safely anyway.

I must recommend it to people that are nervous about setup outside of windows, but a real install on a seperate partition is much better, and easier to recover.  Also, running a liveCD, without installing is really all the preview anyone needs.  I'm sure that most people that run live, will end up installing.

One note about a liveCD install.  for some strange reason, when installing as a secondary OS, when the installation asks for the amount of space to be used, it partitions itsself onto the left over portion rather than the size indicated.  I wanted Vista to take 90gigs, and Ubuntu to have the last 30, but when I told it to setup for 30gigs, it shrunk the Vista partition to 30, and installed on the larger side.  I had to reinstall again, and this time, tell Ubuntu to use 90gig, and so it installed itself on the remaining 30, and windows got to keep 90.  It's completely counter intuitive.

That's all folks.

---

### Post by forestpixie on 2008-03-08
> One note about a liveCD install. for some strange reason, when installing as a secondary OS, when the installation asks for the amount of space to be used, it partitions itsself onto the left over portion rather than the size indicated... It's completely counter intuitive.

Indeed it is counter intuitive to many - what it does is resizes the existing partition, which is what the visual representation shows - it could certainly do with a bit of text :D

Glad to see you're sorted though - welcome back :)

---

### Post by 3rdalbum on 2008-03-08
I completely agree about the slider. I prefer to use the manual method (which is more difficult and potentially more dangerous) simply because I can never remember whether it about how much you want to resize it to or how much space you want for Ubuntu.

I've got a 50/50 chance of getting it right, which translates into a 70/30 chance I'll get it wrong. :-)

---

### Post by seshomaru samma on 2008-03-08
I never encountered the "slider" , i usually use the alternate , but it sound like something you might want to post at  ubuntu brainstorm.

---

### Post by ByteJuggler on 2008-03-08
I don't fully understand what your problem recovering the space used by WUBI and unisntalling it is.  

Uninstalling WUBI from Windows is quite simple and does not depend on whether or not your Ubuntu install works or not.  You simply run wubi-uninstall.exe or uninstall it from the control panel. If that for some reason doesn't work, you can also simply delete the "wubi" folder from your hard drive.  All 3 of these methods will reclaim your diskspace.  The latter method (manual delete) may not clear up your bootloader however, but that's also not too hard to fix either.

---

### Post by WFGeppetto on 2008-03-10
The uninstallation of wubi works fine, if you don't completely screw up Ubuntu in the process.  Whatever I did, when I edited that file, completely screwed up Ubuntu, and the installer looks at Ubuntu, to uninstall.  Don't get me wrong, I barely know what I am talking about, but I'll try to explain better what happend to me.

BTW, other guy, I'll mark it as solved.  Thanks.

When the uninstall ran, it started, and then said that the system was corrupted, or some necessary file (probably the one I messed with) did not function properly, or something.  I was under the impression that Ubuntu actually does much of the work uninstalling itself, and then the wubi uninstaller handles clean up or something.

I reinstalled Wubi, in hopes that it would simply rewrite itsself on top of the old install, but it did not, rather, it made a new one, taking up new space on the drive.  A functional wubi install, like the second one I did, and did not mess with, works fine with the uninstall.  I had no problems whatsoever uninstalling the second attempt.

---

### Post by ByteJuggler on 2008-03-10
> **WFGeppetto said:**
> When the uninstall ran, it started, and then said that the system was corrupted, or some necessary file (probably the one I messed with) did not function properly, or something.  I was under the impression that Ubuntu actually does much of the work uninstalling itself, and then the wubi uninstaller handles clean up or something.

To the best of my knowledge, this is not correct.  The uninstaller is entirely Windows based.  If one of the Windows manifest/install log files got corrupted, then of course you would have trouble (un)installing wubi, as you would with any other Windows app if part of the uninstaller gets corrupted.  No file that you edit *inside* Ubuntu (that is part of Ubuntu, and located on the virtual disks) can possibly directly affect what happens when you run (an application) on Windows.  

In essence, the Wubi uninstaller simply offers to save your data and possibly the downloaded CD iso, then deletes the wubi folder, and finally its entry in the Windows installed programs list.  That's all.  The point I was trying to make as well, was that you can even delete the wubi folder yourself, with Windows explorer, after which you'll have your space back.  You would then have to manually remove the stale wubi entry on the Windows programs list, and remove the entry in the boot loader, if you so wished.

Anyway, since you've had several problems with things apparently getting corrupted I'm wondering if your PC is entirely stable or whether it perhaps has some sort of hardware problem.  (I may be way off base with that.) 

> **WFGeppetto said:**
> 
I reinstalled Wubi, in hopes that it would simply rewrite itsself on top of the old install, but it did not, rather, it made a new one, taking up new space on the drive.  A functional wubi install, like the second one I did, and did not mess with, works fine with the uninstall.  I had no problems whatsoever uninstalling the second attempt.

Well like I say, just delete the broken install, and you'll have your space back.  :)

---

### Post by WFGeppetto on 2008-03-10
Nope, that wouldn't work either.  It creates a virtual drive or something, it's not a separate partition, and it isn't accessable from windows, other than through the wubi launcher/installer.  Once there is a problem within the core files (for lack of knowing the proper term, maybe the kernel?) it simply will not recognize that section of the HDD.  The section that holds the wubi install doesn't even show up in the windows drive manager, as it is technically part of the same partition that windows is installed on.  Windirstat (a visual HDD analyzer) shows the room being taken up, but does not classify it as any known format.

I'm sure there would be some kind of way to erase that portion, but not with normal windows tools, unless there are other tricks (I'm sure there are) in windows that I don't know about.

You sound as though you are still trying to help me solve my problem.  I have since fixed it all, by doing fresh installs, as I indicated in an earlier post.  It's all fine now, other than the fact that AWN doesn't like applets, and I can't get everything streaming in firefox, but I'll figure that stuff out.

If you are simply trying to understand the problem, so that you may be better prepared to help in the future, then I will continue to relay my experience, but that problem no longer exists.  I will not be able to check anything for you or anything.  Thanks for your diligence, but understand, this is no longer a problem for me.

And I swear, it simply would not uninstall.  It would not boot to Ubuntu, and windows just couldn't uninstall it.  When tried, it would start the removal process, and it would say something like, "starting Ubuntu log" or something, I really don't remember.  Then it would show an error, something like "drive must be corrupted, files cannot be accessed", and quit the process.  The only way to remove it would have required some pretty neat tools, as there was not a place to view that part of the drive.  It just didn't show up anywhere with anything that I knew how to use in windows, even the harddrive manager.  I could shrink the volume, and play with partitioning, but it always locked out that 15gigs.  

Anyway, like I said, It's not a problem anymore, but I'll be glad to *try* to help you figure out what it was, if you have some personal interest.

---

### Post by ByteJuggler on 2008-03-11
> **WFGeppetto said:**
> Nope, that wouldn't work either.  It creates a virtual drive or something, it's not a separate partition, and it isn't accessable from windows, other than through the wubi launcher/installer.  Once there is a problem within the core files (for lack of knowing the proper term, maybe the kernel?) it simply will not recognize that section of the HDD.  The section that holds the wubi install doesn't even show up in the windows drive manager, as it is technically part of the same partition that windows is installed on.  Windirstat (a visual HDD analyzer) shows the room being taken up, but does not classify it as any known format.


Just to be clear about this I'm not guessing about how you would've been able to reclaim your space, I'm telling you how it is.  With respect, don't argue with me about what I do know and you yourself said you knew very little about.  The virtual disk files are *in* the wubi folder.  Look yourself if you don't believe me.  There's nothing special about them.    (Files never show up in Windows drive manager so it's not exactly surprising that you don't see anything on Drive manager related to the Wubi install.  ;-) )

> **WFGeppetto said:**
> 
I'm sure there would be some kind of way to erase that portion, but not with normal windows tools, unless there are other tricks (I'm sure there are) in windows that I don't know about.

You sound as though you are still trying to help me solve my problem.  I have since fixed it all, by doing fresh installs, as I indicated in an earlier post.  It's all fine now, other than the fact that AWN doesn't like applets, and I can't get everything streaming in firefox, but I'll figure that stuff out.

If you are simply trying to understand the problem, so that you may be better prepared to help in the future, then I will continue to relay my experience, but that problem no longer exists.  I will not be able to check anything for you or anything.  Thanks for your diligence, but understand, this is no longer a problem for me.

And I swear, it simply would not uninstall.  It would not boot to Ubuntu, and windows just couldn't uninstall it.  When tried, it would start the removal process, and it would say something like, "starting Ubuntu log" or something, I really don't remember.  Then it would show an error, something like "drive must be corrupted, files cannot be accessed", and quit the process.  The only way to remove it would have required some pretty neat tools, as there was not a place to view that part of the drive.  It just didn't show up anywhere with anything that I knew how to use in windows, even the harddrive manager.  I could shrink the volume, and play with partitioning, but it always locked out that 15gigs.  

Anyway, like I said, It's not a problem anymore, but I'll be glad to *try* to help you figure out what it was, if you have some personal interest.

OK, my apologies, I thought you still had 15GB missing. So you've reclaimed your space then?  (Presumably by deleting the folder?  :P )   

Anyway, to be clear, the whole point I've been trying to make and that you seem to misunderstand, is regarding the nature of the Wubi virtual disks/partitions.  You make the Wubi parititions out to be something special, which they from a Windows point of view are patently not.   Nevertheless you seem to think they are, and as a result, you think you therefore cannot easily reclaim space used by Wubi, which is untrue, even when the uninstaller fails to run.  Let me therefore reiterate the facts: **Wubi's filesystems/partition(s), is/are simply (a) files from Windows point of view, located in c:\wubi\disks\.**  No if's, no but's, no arguments.  The system partition is typically c:\wubi\disks\system.virtual.disk  Consequently, if you delete that folder, then at a stroke you've deleted the majority of your actual WUBI install, and if you install the root c:\wubi folder, you're pretty much deleting the entire WUBI install.  

Best regards and sorry for belaboring the point, but I felt it useful to clarify for the sake of others that might read this thread.

---

### Post by WFGeppetto on 2008-03-11
Aha!  Ok, right.  The uninstallation was definitely screwed, and would not work at all.

You have indeed dispelled my disbelief, however.  I seem to remember a fold as such, but I could not view it, that probably lead to my confusion.  As for the partitions, that explains quite a bit, and I should have known it would not show up in the drive manager, considering the fact that it was not a real partition.

You must be correct, however, I am fairly sure that Itried deleting that folder.  Either, I am mistaken, or there were permission problems in this matter.  I'm sure if it was a matter of permissions, it could have easily been worked out.  

It all makes a bit more sense now, and I did not intend to seem arguementative.  It is however, hard to stay off of the defensive when being told something would work, when it didn't (even if it's through my own ignorance).  I know that windows would not view it, and I am quite nearly certain that I could not simply delete it in the standard sense (ie. highlight-delete, or right-click-delete, dunno if I tried ctrl-del, honestly).  

Now that I think about it, I'm sure it had something to do with the fact that one OS doesn't like to look into the other's files properly without some sort of little program (or is that even what you'd call it?  I had to install something on my Ubuntu side, so that I could look into my windows folders).  Keep in mind, in case it isn't clear, that although I show running 7.10, that was only after a fresh install, the wubi was Fiesty.  I think that makes a difference, when it comes to the ability to look into windows files from Ubuntu,  but I'll let you tell me, and besides, that may be irrelevant.

In any case, it was not quite simple.  I may have been rash, and did not exaust all my options, but I am not particularly upset by that;  I needed to do some house cleaning anyway, and what better way, but to freshly install both systems.

I never did delete the file, I actually backed up all the data important to me, and reinstalled windows from disk, formatting the drive.  Then I used a LiveCD of GG 7.10, and did the installation properly.  My computer is quite nearly exactly as I like it now.  The fresh windows install did it some good (as you may suspect, someone like my self likely had many stray files), as I was able to prevent the installation of many bundled programs, and now both sides run better and faster.

I don't mind debating with you, and I'm sorry if I was too quick to answer negatively, however, I seriously *want* to remember that I couldn't delete it without doing something extra.  Not that it might not have been simple, and more importantly, not that I can't be wrong right now.

Either way, again, thank you for your diligence, and I am glad that we have seen this out, as I hate finding threads like this that did not end in true resolution.  As you may imagine, I am often looking for answers, and there are many threads that are left open ended.  Thank you for following up, as this thread should be much more useful to those that find it.

Please ammend, or correct anything in this post that I have misconceptions about, so as to further help others, or dispel any incorrect notions that I may have given a reader.

+1 for sticking with it, and being serious about helping (also because I just learned how to thank!)

---

### Post by Feivel on 2008-03-11
> **WFGeppetto said:**
> Nope, that wouldn't work either.  It creates a virtual drive or something, it's not a separate partition, and it isn't accessable from windows, other than through the wubi launcher/installer.  Once there is a problem within the core files (for lack of knowing the proper term, maybe the kernel?) it simply will not recognize that section of the HDD.  The section that holds the wubi install doesn't even show up in the windows drive manager, as it is technically part of the same partition that windows is installed on.  Windirstat (a visual HDD analyzer) shows the room being taken up, but does not classify it as any known format.

I'm sure there would be some kind of way to erase that portion, but not with normal windows tools, unless there are other tricks (I'm sure there are) in windows that I don't know about.

You sound as though you are still trying to help me solve my problem.  I have since fixed it all, by doing fresh installs, as I indicated in an earlier post.  It's all fine now, other than the fact that AWN doesn't like applets, and I can't get everything streaming in firefox, but I'll figure that stuff out.

If you are simply trying to understand the problem, so that you may be better prepared to help in the future, then I will continue to relay my experience, but that problem no longer exists.  I will not be able to check anything for you or anything.  Thanks for your diligence, but understand, this is no longer a problem for me.

And I swear, it simply would not uninstall.  It would not boot to Ubuntu, and windows just couldn't uninstall it.  When tried, it would start the removal process, and it would say something like, "starting Ubuntu log" or something, I really don't remember.  Then it would show an error, something like "drive must be corrupted, files cannot be accessed", and quit the process.  The only way to remove it would have required some pretty neat tools, as there was not a place to view that part of the drive.  It just didn't show up anywhere with anything that I knew how to use in windows, even the harddrive manager.  I could shrink the volume, and play with partitioning, but it always locked out that 15gigs.  

Anyway, like I said, It's not a problem anymore, but I'll be glad to *try* to help you figure out what it was, if you have some personal interest.
The default Wubi install is to a folder called Ubuntu. You can delete it but instead you are making matters more difficult than they are.

ETA - Here are the virtual disks Wubi creates...

---

### Post by WFGeppetto on 2008-03-11
Okay...Thanks, but that wouldn't have helped me at all, considering the fact that I couldn't look at it in Ubuntu.  Well, maybe it would have helped, and it looked like that in windows, as well, but I really think the other guy had it right, and in my install the folder was called 'wubi'.

Either way, unless you guys just enjoy reiterating how silly I am, the matter is more or less closed.  I am not sure if you guys aren't reading the posts thoroughly, or if you are just trying to help future users.  I'm done with it.  I have a working partition, properly installed, and currently have ***no problems*** other than some streaming issues.

I have fixed the problem.  I may have done it the hard way, but It's over.  I continue to visit this thread, only because, I like to follow up, and if another user has a similar problem, I'd hate to leave it without thorough explanations.

All this, is actually tempting me to try and recreate my previous problems, just so I can copy/paste things from a machine that is currently suffering from this issue.

In my opinion, this is what's IMPORTANT **If you use a wubi installer, be even more careful than usual about messing with the program files, or anything that might endanger the OS**.  Prevention is much better than solutions.  

I don't mean to sound short, I've just taken some nice ego reducers on a frequent basis lately, several of which I was prescribed in this thread.  I will continue to check, and see if I can relay my experience, *as I remember it*, in hopes that others may benefit.

If you are only here to help me personally, then you aren't reading everything.  If you are here for the future help of others, then keep it up!, and I will too.

---

### Post by Feivel on 2008-03-11
> **WFGeppetto said:**
> Okay...Thanks, but that wouldn't have helped me at all, considering the fact that I couldn't look at it in Ubuntu.  Well, maybe it would have helped, and it looked like that in windows, as well, but I really think the other guy had it right, and in my install the folder was called 'wubi'.

Either way, unless you guys just enjoy reiterating how silly I am, the matter is more or less closed.  I am not sure if you guys aren't reading the posts thoroughly, or if you are just trying to help future users.  I'm done with it.  I have a working partition, properly installed, and currently have ***no problems*** other than some streaming issues.

I have fixed the problem.  I may have done it the hard way, but It's over.  I continue to visit this thread, only because, I like to follow up, and if another user has a similar problem, I'd hate to leave it without thorough explanations.

All this, is actually tempting me to try and recreate my previous problems, just so I can copy/paste things from a machine that is currently suffering from this issue.

In my opinion, this is what's IMPORTANT **If you use a wubi installer, be even more careful than usual about messing with the program files, or anything that might endanger the OS**.  Prevention is much better than solutions.  

I don't mean to sound short, I've just taken some nice ego reducers on a frequent basis lately, several of which I was prescribed in this thread.  I will continue to check, and see if I can relay my experience, *as I remember it*, in hopes that others may benefit.

If you are only here to help me personally, then you aren't reading everything.  If you are here for the future help of others, then keep it up!, and I will too.

This is a great example of why some people refuse to help others. You really should relax your attitude a bit...

BTW, that is the folder from within windows.

---

### Post by WFGeppetto on 2008-03-11
Seriously, am I being rude?  I've reread, and I don't understand why you seem to think I am being rude.  I am simply trying to clarify.

What in particular, do you take offense to?

As for it being a folder viewed from within windows, I am sorry, I made an assumption based on the fact that it looks exactly like Ubuntu with the human theme.  You must have customized your windows themes to make it look that way.  Is that simply an ignorant assumtion?  It did not seem clear to me.

I am very sorry, if I seem put-offish, it just seems to me that we are having miscommunications, and I am trying my best to be clear, not rude.

Edit:  Ok, maybe it was this line:

> If you are only here to help me personally, then you aren't reading everything.

That does sound a bit fussy, doesn't it.  You may be simply trying to help me understand what the problem was, rather than how to fix it now.  Perhaps, I am being short-sighted, because I don't particularly care what the problem was anymore, as it isn't a problem any longer.  I suppose, I should want for the knowledge all the same.

On a similar note, from my point of view (again, I am trying to communicate clearly, not be a jerk)  "you are making things more complicated than they are" may be a statement of fact, but it is unnecessary, and easily taken offense to.  You may not intend it, but you "sound" short, and condescending to me.  I am sure that is not your intention, but inflection is difficult to recognize in text posts.  I suppose that is simply one of the hazards of text communication.  I assure you I am not trying to be a jerk, and I do not mean to exhibit any kind of attitude whatsoever.  I am very sorry that you seem to think otherwise.

Please, do respond, and indicate how I have offended you.  I navigate other forums without issue, but apparently, I have a tone that is not welcome here, and while I don't understand that, I would like to rectify the problem, by avoiding such offenses in the future.  I promise you, my goal here is to learn, and to be a responsible forum user.  Constructive criticism is quite welcome, and encouraged.

---

