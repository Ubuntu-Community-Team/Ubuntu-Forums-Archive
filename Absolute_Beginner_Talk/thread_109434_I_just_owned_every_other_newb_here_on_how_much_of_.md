---
title: "I just owned every other newb here on how much of a newb i am"
date: 2005-12-28
forum: Absolute Beginner Talk
---

### Post by Fffan on 2005-12-28
so i installed Ubuntu Linux 5.1 dual boot alongside WinXPpro, and i thought it was pretty easy, aside from all the time it took to partition the drives and all, but being so late at the time, i accidently skipped one step, screen resolutions, so my first question is how can i change my screen res settings?

when i go to system pref. screen res my only options are 640x480, 800x600, and 1024x768, my moniters native resolution is 1920x1440, although id probably prefer it at 1600x1200 (19.8" screen)

also, heres the major newbage, i cant quite grab the concept of installing anything, i installed aMSN pretty easy, just to see what it was like, i still prefer GAIM, but that was in the preinstalled programs, just had to enable it, i tried installing opera, i prefer it to firefox for different reasons, i followed some simple instructions on it, tried both packages made available on opera.com and entered the command into the terminal and it just didnt work, if you would like specifics on file names and such youll have to give me a little bit, right now im booted into windows to listen to music, thats my other problem

i cant get .wavs, .mp3, .wmas, .oggs, anything to play, im pretty sure it has something to do with my sound card, is it completely possible that when installing it recognized and installed the onboard AC97 soundboard instead of my PCI Envy24 board? so how do install the correct drivers? again, im in no way keen on installing anything

one more thing, bittorrent. i wanna use it to download movies and shows that are otherwise unavailable to me, sealab 2021 amoung them, for use on my PSP, and maybe desktop use if its of highres. i just dont know how to use it

is it all in documetation? i havent got around to reading all of it (not tons of free time lately, but now i have a week of nothing to do, so i figure ill try it) 
i just thought id try to get some straight responses rather than read the whole thing, why read through the entire phonebook to find one person if you can ask someone for it? (yes, sucky analogy as its easy to find the individual # in the phonebook, but my point remains valid, i think)

im excited about learning linux, and downloading movies without worrying about spyware and viruses and such

thanks for any responses!

---

### Post by Kyral on 2005-12-28
Well, multiple soundcards are a pain. Best solution is to go to the BIOS and disable the onboard card, then the installer will pickup on the PCI. As for Codecs... those are sketchy....due to legal reasons

Read more on it here
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by Fffan on 2005-12-28
ill try that on next boot up, i didnt expect it to be something scketchy to play mp3s that i had ripped from original CDs, well, it didnt let me play a CD either (original audio CD) so i expect it was the sound card conflict or something, but after i disable the onboard sound (which i thought i already did) will i have to do something within ubuntu to tell it i switched soundboards?

---

### Post by Nomearod on 2005-12-28
To install programs like Opera and some other, you could try Automatix. It's very simple.

Check this thread:
[http://ubuntuforums.org/showthread.php?goto=newpost&t=66563](http://ubuntuforums.org/showthread.php?goto=newpost&t=66563)

---

### Post by Fffan on 2005-12-28
shame, the automatix was looking really good, but i have amd64 architecture so its not gonna do it

anything similar?

---

### Post by rjwood on 2005-12-28
for your screen resolution-make sure you have your manual or info from the web site of the manufacturer. Then do ```
sudo dpkg-reconfigure xserver-xorg
``` from a terminal accept the default  settings. When you get to the monitor input the information it asks for. Again it is usually best to go with the defaut settings. Read everything carefully. Good luck!!

---

### Post by Fffan on 2005-12-28
yea...so i went through the entire thing and after asking me about color depth is goes back to the standard terminal and says:

xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf.200512281636

what did i do wrong or what do i have to do now?

---

### Post by rjwood on 2005-12-28
[quote=Fffan]yea...so i went through the entire thing and after asking me about color depth is goes back to the standard terminal and says:

xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf.200512281636

what did i do wrong or what do i have to do now?[/quote]

You can back-up your old settings and try the new ones.

---

### Post by Fffan on 2005-12-28
See, i dont really know what that means, is it some copy and pasting of config files?

---

### Post by rjwood on 2005-12-28
[quote=Fffan]See, i dont really know what that means, is it some copy and pasting of config files?[/quote]
no---your done!!!:) I think along the bottom you see the 'f' key options. It has already done the back-up of your old settings. It is just telling you that. Use your common sense, you'll be fine. There is nothing on your computer that can't be fixed.

---

### Post by hashimoto on 2005-12-29
[QUOTE=Fffan]shame, the automatix was looking really good, but i have amd64 architecture so its not gonna do it

anything similar?[/QUOTE]

Did you install the 64 version of Ubuntu? If not, then you can use Automatix.

Otherwise (after you have sorted out the sound card issue) you can find helpful information here: [http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-music-and-movies](http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-music-and-movies)

---

### Post by poofyhairguy on 2005-12-29
[QUOTE=Fffan]shame, the automatix was looking really good, but i have amd64 architecture so its not gonna do it

anything similar?[/QUOTE]

[http://robotgeek.org/blog/easybreezy/](http://robotgeek.org/blog/easybreezy/)

But it won't magically make a chroot for you (aka it won't install 32 bit Opera in 64 bit Ubuntu for you). Honestly the 64 bit Ubuntu is only for super nerds- you have to spend a while with the command line to make 32 bit programs like opera install. I suggest putting the x86/i386 version on if you can- it iwll work fine on your machine.

If you want to stick with 64 bit version please PM me as I do it and I can give advice....but be warned that your patience with be tested on that path.

A bit torrent program is installed by default in Ubuntu. Just click the links in Firefox.

---

