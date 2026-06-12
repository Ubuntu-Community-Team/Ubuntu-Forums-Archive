---
title: "Not a clue....."
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by willie146usa on 2006-10-18
Hello everyone. I am new to this community and I need help. Keep the jokes for later. HAHA
Someone I work with handed me an iBook and said "It won't boot up" So, I turned it on and got the Kubuntu Logo Screen and a message that said " Restarting system log..." and across from that was the letters "OK" . Then it said it again under the first message with the same "OK" after it and it hasn't done anything yet. This is all new territory for me, so if anyone can offer any information, it would be GREATLY APPRECIATED. Willie

---

### Post by raul_ on 2006-10-18
I didn't quite get the problem, but try this:
If u don't have a Live CD, download it, boot from it and then try to repair the system. That should work.

---

### Post by willie146usa on 2006-10-18
I restarted the iBook by hard booting it and I saw it go through loading everything and then it goes to a black screen with the Kubuntu logo and then it will disappear after a few minutes. Basically I am a PC person and this is all very new to me as well as frustrating. Where would I find this Live Disc? I will give it a go.

---

### Post by Mimsy on 2006-10-18
[Here you go.]("http://www.kubuntu.org/download.php") There is some very helpful documentation on that site as well.

Good luck!

/Mimsy

---

### Post by devnulljp on 2006-10-18
> **willie146usa said:**
> I restarted the iBook by hard booting it and I saw it go through loading everything and then it goes to a black screen with the Kubuntu logo and then it will disappear after a few minutes. Basically I am a PC person and this is all very new to me as well as frustrating. Where would I find this Live Disc? I will give it a go.

Sounds like your xorg.conf file is non-functioning
At the black screen, type cntrl-alt-F1     <---the 'F1' key not 'F' + '1'
that should dump you to a terminal
do you have a username (with sudo access) and password? 
If so, log in here (if not, you'll need to do a single user boot and repair there)

type 
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak 
sudo dpkg-reconfigure xserver-xorg
```

That should recreate a (hopefully working) xorg.conf file that will allow you to start X

Easiest thing would be to reboot (sudo reboot) or 
```
sudo /etc/init.d/kdm restart

```
to restart X

---

### Post by arochester on 2006-10-18
You can get a Kubuntu live disk from [http://releases.ubuntu.com/kubuntu/6.06/](http://releases.ubuntu.com/kubuntu/6.06/)

Choose the Desktop CD - Mac (PowerPC) desktop CD  

Note that you will need at least 192Mb of RAM, although how you test that from a non-functioning machine I don't know.

On a Mac, to boot from the CD instead of the Hard Drive, you need to insert the Disk and hold down "C" when booting

---

