---
title: "Ubuntu Feisty in VMware Fusion beta 4 - WOW!"
date: 2007-06-09
forum: Apple Intel Users
---

### Post by thully on 2007-06-09
After having used Ubuntu native for some time and then having to send my MacBook away for repair, I decided to give the newest beta of VMware Fusion a try with Ubuntu.  My reaction - WOW!  I must say that VMware really has a great product, and Ubuntu runs so well that it virtually indistinguishable from running natively.  In fact, it might actually run *better* than native - on VMware my trackpad works fine, there's no need to worry about suspend-to-RAM, it doesn't overheat as it does natively, and wireless uses the superior OS X drivers.  There is even an option to enable paravirtualization in the VMware configuration file, which supposedly speeds things up even more.

Anyone who is frustrated with a native boot - or who wants to switch between OS X and Ubuntu (and Windows if you want) quickly should try it out.  I'm probably going to keep running this way - especially since I want to test Gutsy Gibbon, and Fusion would be a great way to do so without risking my data. I still may go back to a native boot, though - I'd like to see suspend-to-RAM working in the stock kernel (on 1G MacBooks) and see the other issues resolved.  I still want to use OS X, though, and rebooting is undoubtedly annoying...

---

### Post by kzm. on 2007-06-09
i dont want to sound stupid, since from what i read its just a stripped down version of vmware.. but do you tried parallels as well. if so any difference?
and i also wonder about sharing file access? is it possible to have osx and ubuntu share files directly?

---

### Post by kzm. on 2007-06-09
do you have a how-to for setting up vmware to use an existing native ubuntu install as virtual?

---

### Post by thully on 2007-06-09
I tried Parallels, but it seemed noticeably slower than VMware Fusion.
Dunno if this just applies to the live CD (which I tried to install, and got sick of it taking
so incredibly long that I canceled) or to the finished install as well.

As for running an existing Ubuntu partition in VMware, I don't know how to do this or if it's even possible.

---

### Post by kzm. on 2007-06-09
i think its possible to run a native install.. at least its possible to run windows native install in linux. and i read that its possible to do the same with linux and osx.. anybody knows more?

---

### Post by thully on 2007-06-09
Are you thinking of a dual boot?  If so, I've done it, and it can certainly be done, but it gives you a bunch of driver problems (things work, but not as well as OS X) and requires a reboot to switch OSs.  That's why I'm using Fusion now - I don't think I really want to get rid of OS X, I've got a small HD (60GB), and rebooting to switch is a pain.

---

### Post by vh1 on 2007-06-10
is it possible to use composite window managers in the VM? with the news of DirectX 8.1 support, one can dream

---

### Post by cragthehack on 2007-06-10
Fusion is amazing,. Try it. I did a clean install of Ubuntu from an ISO file. Been playing with it all day. No problems and runs like a dream. Granted I have a MBP with 2Gigs of RAM, but still. And Fusion is in oublic beta right now too, I man.. damn - it is really good.

If you have Parallels I suggest you do not upgrade to 3.0 (it was just released). SERIOUS problems with that version (and NO the promised 3D gaming does not work). Ubunto ran for me in Parallels  2.5 but was very choppy. I could not install Ubuntu in Parellels 3.0. Why I hit up Fusion. I wanted to run Ubuntu with OSX. (Though if you need to run Windows Parelles does a fine job of that. I haven't tested Fusion with Windows. And I don't plan too. ;) )

Yeah Fusion it will cost some cash (I think under 200 but not sure).   But I'm more then willing to shell out some cash for this product.

---

### Post by thully on 2007-06-10
I got Ubuntu working in Parallels 3.0 - just following the prompts for installing a new OS and choosing "Ubuntu" worked.  The graphical boot screen (with the progress bar) doesn't work, though, so you stare at a weirdly-corrupted boot screen for 30 seconds or so before finally seeing a desktop.

I wouldn't recommend Parallels 3.0, though - besides this issue, it seems MUCH slower than Fusion.  It seems buggy in general - luckily I was only using the trial version.  As for Fusion's cost, I definitely expect it to be more in line with Parallels' cost than VMware Workstation.  VMware reps have said on the Fusion message board that this is different from Workstation - specifically in that it is targeted at the consumer market.  

Unless I go native with Ubuntu, or Fusion is in the VMware Workstation price range, I'll probably get it - it's a great platform for testing OSs in general, and I hope to eventually start testing Gutsy Gibbon and maybe even work on tweaking the source code of some Ubuntu components.  As it stands, I don't see myself going native - I still want to use OS X a lot, rebooting is a pain, and Ubuntu's trackpad, suspend, and wireless support leave much to be desired.

BTW, for a speed boost, enable paravirtualization in Fusion.  Details can be found at : [http://www.vmware.com/community/thread.jspa?messageID=665417](http://www.vmware.com/community/thread.jspa?messageID=665417)

---

### Post by cragthehack on 2007-06-10
Thanks for the tip to the speed boost. Though Fusion was already fast.

I love OSX. I love Unbuntu too. Also I love Ruby. And, Apple is making serious leaps in the Ruby direction. So OSX wins out as my base OS. But with Fusion I can get the best of both words. I'd like to port a few of my Mac apps to Linux via Unbuntu.

I'll probably end up buying some PC just for Unbuntu at some point. This is like the first time I've ever not had Windows in my life. ALL UNIX now. ;)

---

### Post by kzm. on 2007-06-10
btw.. anybody tried to run osx on ubuntu in vmware? i saw a video on youtube about it.. was wondering if anybody had any experiences with this...

---

### Post by nebulus-design on 2007-06-11
( for Cragthehack )

Sounds like you have one of the nice new MacBook Pros with the nvidia gpus, do you get OpenGL acceleration when running under VMware?

Also I used spotted that NVidia have released new drivers that should support the new gpu, would be interested to hear if anyone has a native ubuntu installed and working with these...

---

### Post by kzm. on 2007-06-11
does anybody how to use a native ubuntu install under vmware on osx? 
i was looking around and couldnt find it.
i have refit installed with osx and ubuntu. i would like to be able to use my native ubuntu install even if i am under osx. does anybody has any resources on this?

---

### Post by cragthehack on 2007-06-11
> **nebulus-design said:**
> ( for Cragthehack )

Sounds like you have one of the nice new MacBook Pros with the nvidia gpus, do you get OpenGL acceleration when running under VMware?

Also I used spotted that NVidia have released new drivers that should support the new gpu, would be interested to hear if anyone has a native ubuntu installed and working with these...

No I have the gneration before that. Got it last month. A few weeks before they announced the nice new refit (of course). ATI XT1600 card 256MB.

---

### Post by Lacrosse200760 on 2007-06-11
Fusion defiantly does a great job all around, one thing though that I wish I could get to work is beryl or compiz, which right now when starting either of them the screen goes blank and flickers some and the next thing I know im back at the login screen. I've enabled the 3D support in the options although it says it only works on XP SP2 so that could be part of it. This is with the santa rosa mbp

Edit: Maybe its not even possible because of the graphics driver being VMware instead of Nvidia or ATI depending on model

---

### Post by neatokino on 2007-06-11
Can anyone post an easy how-to for installing and running Ubuntu Feisty with VMware Fusion on a macbook pro (2.16 GHZ Intel Core Duo, 1 gig RAM,  ATI Radeon X1600)?

I've downloaded VMware Fusion beta 4 and I have the Ubuntu 7.04 386 iso disk image on my hard drive, and before I try installing and running this, I was wondering if someone can tell me exactly what's involved in making this work.  I'm more or less a newbie to linux (have played with Ubuntu in dual boot on my old PPC 12" powerbook), but I love the idea of running it as a virtual machine on my intel macbook before trying to install a dual-boot on this computer (or instead of dual-booting).  

Is this an easy install?  Will I have to do anything to adjust video settings, wireless, bluetooth or trackpad?  Will it be self-explanatory and idiot-proof if I just double click the Fusion installer and go from there?

Any help would be appreciated before I take the plunge!

M

NEVER MIND-- WENT AHEAD AND JUST TRIED IT AND THE INSTALLATION WAS MORE OR LESS IDIOT PROOF.   Am posting using Ubuntu via VMware Fusion right now and it's very cool!

---

### Post by kzm. on 2007-06-13
i thought i had posted this already, but i cant find it back.. may be it was just in my thoughts..

i noticed a 10 to even more than 20 degrees celcius temperature drop after closing vmware! this might info someone might consider...

---

### Post by kzm. on 2007-06-13
proper english (i have to go to bed):

i noticed a 10 to even more than 20 degrees celcius temperature drop after closing vmware! someone might find this info valuable...

---

### Post by neatokino on 2007-06-13
I also notice that my macbook pro gets very very very scary hot when running vmware fusion for more than a half hour or so.  Anybody have any idea what to do about it?

---

### Post by mixedape on 2007-06-13
Any tips for installing on new macbook?

Is it worth it? Should I wait till I upgrade my RAM to 2g

---

### Post by ramcosca on 2007-06-14
> **mixedape said:**
> Any tips for installing on new macbook?

Is it worth it? Should I wait till I upgrade my RAM to 2g

It's worth it allright. I am using a 2.0 GHz Core 2 Duo with 1 gig of RAM and it runs pretty well. I have it set to 512 MB, which is I think a lot, considering I'm also running OS X. I am going to lower it to 256, I don't think the OS will mind. 

I did order 2GB of RAm today from Crucial.com... I suggest you do the same. Shipped to Puerto Rico it was $102. If you live in the US it should be less.

---

### Post by speedemonV12 on 2007-06-14
is it possible to install beryl inside VMware?

---

### Post by ramcosca on 2007-06-14
Installed the 2 sticks of RAM I ordered yesterday. So much better. I moved the slider to 512 MB dedicated to Ubuntu. makes it run perfectly!

---

### Post by kzm. on 2007-06-15
speedemonV12, you can install beryl, but you wont be able to run it under vmware. :)

---

