---
title: "[SOLVED] Can't see you tube videos! Help!"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by Ganda_Melga on 2007-05-30
Well, after experimenting with other distros of linux. I came back where I started, to Xubuntu. Today I re-installed it and I'm still configuring it. 

The problem is I can't see video from [www.youtube.com](www.youtube.com). At first it asked me if I wanted do save the file or open with some program. I did go to add/remove programs and installed a flash plug-in. Still the same thing, didn't solved the problem. Then I did tried the synaptic manager. Searching for "flash" it found another plug-in (for mozzila) e some libs. I installed them too. Synaptic automatically un-installed the first package I has installed. Now, when I access youtube it no longer asks if I want to save the file. It opens a window with a black screen, and two slightly distorted buttons, a red button and a white button, but with no sound nor video.

Also for one of the pages I access of old French music, it was possible to hear the selected music in the background. Now with this new installation says theres a missing plug-in. The plug-in in question seems to be the realmedia plug-in. I did go to the realmedia page and downloaded realmedia 10, wich is a BIN file. There were instructions how to make this bin file executable and how to install. I did installed it in my home directory, because there's no reference where I should install the file. Now firefox no longer says theres a missing plug-in, but still doesn't play sound on that specific page ([www.fhardy.de](www.fhardy.de))


What do I still need to do to tune firefox? How can I see the youtube videos??

Any help will be welcome.

---

### Post by aysiu on 2007-05-30
Which Flash package did you try to install with Synaptic? Was it *flashplugin-nonfree*? Or something else?

Try one of these other methods:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by Ganda_Melga on 2007-05-30
> **aysiu said:**
> Which Flash package did you try to install with Synaptic? Was it *flashplugin-nonfree*? Or something else?

Try one of these other methods:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)


No. The non-free package was the  first I installed with "add/removed programs". Didn't worked. After that I went to synaptic manager and found out some a couple more things relative to flash. Did install that one, and some libs that the manager recommended.

Going to check that site you gave me right now.


Thanks a lot!

---

### Post by aysiu on 2007-05-30
> **Ganda_Melga said:**
> No. The non-free package was the  first I installed with "add/removed programs". Didn't worked. After that I went to synaptic manager and found out some a couple more things relative to flash. Did install that one, and some libs that the manager recommended.

Going to check that site you gave me right now.


Thanks a lot!
I'm surprised *flashplugin-nonfree* didn't work, but the site I linked you to has three other ways to install Flash. Hopefully one of those will work.

---

### Post by Ganda_Melga on 2007-05-30
> **aysiu said:**
> I'm surprised *flashplugin-nonfree* didn't work, but the site I linked you to has three other ways to install Flash. Hopefully one of those will work.

AH...I'm back in the synaptic manager. What it did install is something called "flashplayer-mozzila".  The two can't be installed at the same time. Going to retry flash flashplugin-nonfree, and the manager tells me it necessary to remove the flashplayer-mozilla. I'm going to try it anyway.

If it still doesn't work, I will check the terminal install at the page you gave me.

---

### Post by Ganda_Melga on 2007-05-30
Yes.... It produced some kind of error. Can't paste It here, but I will write it here:

debconfig: not possible to initialize frontend: gnome

debconfig: (unable to load Gnome -- is lib2gnome-pearl installed?)

debconfig: falling to frontend; Dialog

automatic installation failed due to network problems or upstream changes



Since the network seems to be in order, i suppose the problem must be the upstream changes (which I don't know what they are).

Will try another way...

---

### Post by Ganda_Melga on 2007-07-14
After all this time I still can't get youtube videos to work.

I formatted the hd, re-installed xubuntu, install the flash plug-in (for add/remove programs) and still the message from youtube is the same:

[B]Hello, you either have JavaScript turned off or an old version of Macromedia's Flash Player. Get the latest Flash player.

[/B]

I also installed the java plug-in and Java webstart 1.4 and Sunjava 5.0 webstart.

Still nothing.

Should I gave up xubuntu and use anoher distro? Everytime I install xubuntu it's a lot of work. Have to fix the power managment, have to fix the sound, have to fix the restricted formats, and have to fix the flash player.

Is there any easy way to fix this flash issue?


Shoul I upgrade to xubuntu 7.04? Will things work better in 7.04??

---

### Post by mike102282 on 2007-07-14
Try Freespire it is based of of Ubuntu is free and Flash works great!

---

### Post by DBStevens on 2007-07-14
Java and Javascript are not the same thing so you might want to check your browser's javascript settings.

---

### Post by aysiu on 2007-07-14
Maybe you have an old version of Flash.

Any chance you have Flash 7 installed (instead of Flash 9)?

This page should help you:
[http://www.psychocats.net/ubuntu/flash#adobe](http://www.psychocats.net/ubuntu/flash#adobe)

---

### Post by Ganda_Melga on 2007-07-16
> **aysiu said:**
> Maybe you have an old version of Flash.

Any chance you have Flash 7 installed (instead of Flash 9)?

This page should help you:
[http://www.psychocats.net/ubuntu/flash#adobe](http://www.psychocats.net/ubuntu/flash#adobe)



Great help! With that link I managed to update the flash version. At first it only worked in firefox, but after a while i managed to fix opera with the updated flash version.


Many thanks. :popcorn:


(I have another doubt, but I'll open a new thread)

---

