---
title: "Clone Ubuntu"
date: 2005-07-04
forum: Absolute Beginner Talk
---

### Post by peacenew on 2005-07-04
Hi All!  
  I'm a newbie to linux but not windows by any means.  I installed Ubuntu about 3 weeks or so ago and have been having a blast with it.  It works great and enjoy the forums and the learning curve.  
  My question is this.  I installed Linspire on my wifes computer and while its candy pretty it runs like a dog.  It locks up a lot,  its software in cnr is old, the sound with sound jack server is a mess for all or at least a lot using it.  I would like to clone my Ubuntu install with all its software i've added to my wifes computer because Ubuntu runs great and support is excellent.  I'm trying to get her to open up to other possibilities and learn.  Norton ghost won't clone it so is there a utility that I  can use to image to a dvd or cd or clone to hers. Any help would be appreciated.  Should I install on hers and then image to a dvd or cd and copy over and how in linux would this work.
Happy in Linux

---

### Post by jeremy on 2005-07-04
Partimage - [http://www.partimage.org/](http://www.partimage.org/) - is great, and you can install it directly from the repositories.

---

### Post by knewbix on 2005-07-04
Probably a dumb question, but why not just install Ubuntu on her computer? If you clone your Ubuntu, aren't all the settings etc going to be for *your* hardware? I am new to this so apologies if I am wrong.

---

### Post by Lunde on 2005-07-04
[QUOTE=knewbix]Probably a dumb question, but why not just install Ubuntu on her computer? If you clone your Ubuntu, aren't all the settings etc going to be for *your* hardware? I am new to this so apologies if I am wrong.[/QUOTE]
 It should be possible to install a fresh install, then copy the configuration over. If the computers are pretty much the same, you can after do a cp -ax of the root partition from one to the other through the network. Maybe excluding directories like /dev /proc /sys and files like /etc/X11/xorg.conf /etc/fstab. there's probably more. 

There's probably somebody else who knows more about this here then me, but this is the way I would try it.

---

### Post by Darkscot on 2005-07-04
[QUOTE=peacenew]Hi All!  
  I'm a newbie to linux but not windows by any means.  I installed Ubuntu about 3 weeks or so ago and have been having a blast with it.  It works great and enjoy the forums and the learning curve.  
  My question is this.  I installed Linspire on my wifes computer and while its candy pretty it runs like a dog.  It locks up a lot,  its software in cnr is old, the sound with sound jack server is a mess for all or at least a lot using it.  I would like to clone my Ubuntu install with all its software i've added to my wifes computer because Ubuntu runs great and support is excellent.  I'm trying to get her to open up to other possibilities and learn.  Norton ghost won't clone it so is there a utility that I  can use to image to a dvd or cd or clone to hers. Any help would be appreciated.  Should I install on hers and then image to a dvd or cd and copy over and how in linux would this work.
Happy in Linux[/QUOTE]

my feeling on this is that you are storing up potential trouble for yourself (and your wife) unless both PCs are identical.  I suggest you do a clean install and copy the configuration if you REALLY want to.  But in reality there is not much to do to set up the PC from scratch after the install.  Mount your Windows drive and download a few codecs perhaps?

---

### Post by aysiu on 2005-07-04
[QUOTE=Darkscot]my feeling on this is that you are storing up potential trouble for yourself (and your wife) unless both PCs are identical.  I suggest you do a clean install and copy the configuration if you REALLY want to.  But in reality there is not much to do to set up the PC from scratch after the install.  Mount your Windows drive and download a few codecs perhaps?[/QUOTE] I agree. Copying configuration files and even preferences can sometime screw up things. Just do a clean install. She's less likely to run into weird bugs later if it's a clean install.

---

### Post by peacenew on 2005-07-05
Thanks for the advice I went ahead and just installed fresh on her computer.  all went well like I expected except screen resolution and refresh rate was stuck on one so used forums to solve this and its okay, but I also have no sound so i'll postb a new thread on this.
Thanks

---

### Post by Lunde on 2005-07-05
[QUOTE=peacenew]Thanks for the advice I went ahead and just installed fresh on her computer.  all went well like I expected except screen resolution and refresh rate was stuck on one so used forums to solve this and its okay, but I also have no sound so i'll postb a new thread on this.
Thanks[/QUOTE]
 There are plenty of treads here abuot the sound.

Check here first:
[http://www.ubuntuforums.org/showthread.php?t=31094](http://www.ubuntuforums.org/showthread.php?t=31094)

---

### Post by mohaham on 2005-07-05
this thread might help you fix the sound issue..
[http://www.ubuntuforums.org/showthread.php?t=44753](http://www.ubuntuforums.org/showthread.php?t=44753)

---

