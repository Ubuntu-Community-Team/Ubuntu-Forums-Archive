---
title: "iMac without sound"
date: 2011-07-18
forum: Apple Hardware Users
---

### Post by photochuck on 2011-07-18
Does anyone out there know how to get the headphone jack/external speakers working? I have a intel iMac. I have been using ubuntu for about a week and have never had the headphones jack/external speakers working. There is nothing wrong with the speakers or the jack because they work when I boot up in Mac os X.

---

### Post by johnmurrayvi on 2011-07-18
Had the same issue on my 8,1 iMac after installation. This fixed mine:
In the file:
```
/etc/modprobe.d/alsa-base.conf
```
add the following line:
```
options snd-hda-intel model=mbp3
```

You'll need to reboot after that, then open terminal and use the command 'alsamixer' to check for muted lines, e.g. the microphone for one.

After that, it should be all set. This also *significantly* improved the sound quality for me.

---

### Post by photochuck on 2011-07-25
Thank you for your reply, but can you please  be more specific. I have only been using ubuntu (Linux of any kind) for two weeks now. Would it be too much to give step by step instructions?

---

### Post by johnmurrayvi on 2011-07-25
Not a problem, happy to help!
Open a terminal, keyboard shortcut is Ctrl+Alt+T, then type:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```
In the file that opens, go to the bottom and add:
```
options snd-hda-intel model=mbp3
```
Save it and exit. 
Reboot, then open a terminal and type
```
alsamixer
```
Use the left and right arrow keys to move and the 'M' key to toggle mute/unmute. Unmute anything that is muted, and make sure the mic isn't muted or turned way down. Hit Esc to exit the mixer, close the terminal and you should be all set.

---

### Post by photochuck on 2011-07-26
[EMAIL="Screenshot-charles@charlesiMac:.png"]Screenshot-charles@charlesiMac:.png[/EMAIL]Thanks once again, but it did not work. Does this look OK to you? [http://www.flickr.com/photos/pchuck/5977878462/in/photostream/](http://www.flickr.com/photos/pchuck/5977878462/in/photostream/)

---

### Post by johnmurrayvi on 2011-07-28
Hmm, here's what mine looks like:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=198665&stc=1&d=1311825973[/IMG]

However, it did look like yours previous to adding the 'model=mbp3' line and making 

Do you know which version iMac you have? [Run '***sudo dmidecode -s system-product-name***' if you're not sure]

Can you post the output of the command '***lsmod***' as well?

---

### Post by MindFlayer on 2011-07-28
Why do people insist to add the line *"model=mbp3"* in their config? That model is meant for Macbook Pro, not for iMac, or is it compatible with that specific model of iMac or what?

---

### Post by photochuck on 2011-07-29
@Johnmmurrayvi here is the result of Ismod and here is what I see after following you instructions. By the way, I have a iMac 8,1.file:///home/charles/Desktop/Screenshot-charles@charles-iMac:%20~.png
file:///home/charles/Desktop/Screenshot-charles@charles-iMac:%20~-1.png  [http://www.flickr.com/photos/pchuck/5986420437/in/photostream](http://www.flickr.com/photos/pchuck/5986420437/in/photostream)   and   [http://www.flickr.com/photos/pchuck/5986978902/in/photostream](http://www.flickr.com/photos/pchuck/5986978902/in/photostream)

---

### Post by nikobe on 2011-08-09
I'm having the same issue

iMac 2011 24" (think its like 23.5 really) with bootcamp and then just standard 11.04 64-bit installed inside and all updates applied.

the soundcard is the below

Cirrus Logic CS4206/4207
========================
  mbp55		MacBook Pro 5,5
  imac27	IMac 27 Inch
  auto		BIOS setup (default)

so most sites suggest the imac27 settings which I've done in /etc/modprobe.d/alsa-base.conf

and then restarted but still only comes out of the internal speakers.

I've also gone into the mixer to do the level changes to make it less tinny but would like the proper speakers to work.

Any ideas? I can run any tests needed

---

### Post by kaldor on 2011-08-09
Check here: [http://www.omgubuntu.co.uk/2011/05/how-to-fix-low-sound-on-a-macbook-with-ubuntu-11-04/](http://www.omgubuntu.co.uk/2011/05/how-to-fix-low-sound-on-a-macbook-with-ubuntu-11-04/)

Apparently it works with a few different Macs.

---

### Post by nikobe on 2011-08-09
Sadly not but thank you, thats the same fix suggested by the 2nd poster here and it doesn't do anything.

Allot of the websites are getting the two issues, quiet tinny sound mixed up with the no sound from headphone/ext output socket issue.

When you switch the connector under sound preferences it does nothing the same sound comes out of the internal speakers without even a click to suggest its changing anything. Likely just a control tied to nothing (yet).

I'm sure they will fix it eventually.

---

### Post by fdrake on 2011-08-09
try this :

```

sudo cat >> /etc/modprobe.d/local.conf
options snd-hda-intel model=imac27
alsamixer -c0

```
unmute all outputs with "M" key
store your settings with:
```
sudo alsactl store 0 
```
reboot

---

