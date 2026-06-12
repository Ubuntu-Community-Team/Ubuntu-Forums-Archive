---
title: "COMPLETELY NEW TO LINUX/UBUNTU - how to get DVDs' to play."
date: 2006-04-24
forum: Absolute Beginner Talk
---

### Post by KDOG2007 on 2006-04-24
Please forgive me if this is a repost, etc. Completely new to the Linux world, need the "idiots guide to DVD playback" hence the following request.](*,) 

Just managed to get Unbuntu 5.10 onto a second computer I have in the bedroom that is NOT connected to the internet so any software has to be put on a CD and loaded that way. It has Totem but everytime I try to play a DVD it says it can't, that I need a plug in. I managed to download Xine, burn it to a CD an copy it to the Ubuntu desktop, but how do I get it to work? 

Also, I do have a 56K modem in there, any free ISPs' like Netzero etc., that I can load on there?

Thanks for any help you all can give me.....

---

### Post by izmaelis on 2006-04-24
[QUOTE=KDOG2007]Please forgive me if this is a repost, etc. Completely new to the Linux world, need the "idiots guide to DVD playback" hence the following request.](*,) 

Just managed to get Unbuntu 5.10 onto a second computer I have in the bedroom that is NOT connected to the internet so any software has to be put on a CD and loaded that way. It has Totem but everytime I try to play a DVD it says it can't, that I need a plug in. I managed to download Xine, burn it to a CD an copy it to the Ubuntu desktop, but how do I get it to work? 

Also, I do have a 56K modem in there, any free ISPs' like Netzero etc., that I can load on there?

Thanks for any help you all can give me.....[/QUOTE]
I think that you will find your answer about how to play DVDs [here]("https://wiki.ubuntu.com/RestrictedFormats#head-cd84b8e23927ccdb4bb55ffd3074687abec0cf3b"). It is a good wiki on how to play other multimedia formats too.

---

### Post by KDOG2007 on 2006-04-24
Ok, ummm, what does it mean "type in terminal"? What terminal? :confused:

---

### Post by Iowan on 2006-04-24
Start with this:
[https://wiki.ubuntu.com/BasicCommands?action=show&redirect=TerminalHowto]("https://wiki.ubuntu.com/BasicCommands?action=show&redirect=TerminalHowto")

---

### Post by KDOG2007 on 2006-04-24
Ok, still can't get it to work. I don't understand why there isn't a DVD player you can simply download, open up and install. Sigh. Should just stick to Windows.

---

### Post by mostwanted on 2006-04-24
[QUOTE=KDOG2007]Ok, still can't get it to work. I don't understand why there isn't a DVD player you can simply download, open up and install. Sigh. Should just stick to Windows.[/QUOTE]

Maybe you should...

---

### Post by gr0kzer0 on 2006-04-24
The reason there's no default DVD playing (or MP3 when it comes to it) is because the codecs needed to play these file formats is proprietary - closed - while Ubuntu is Free/Open Source. It's a matter of ethics.

Saying that, many people download the codecs and get their DVD and MP3 players working every day on Ubuntu. It's not a major problem, and whatever is stopping you from doing it is likely easily fixed. Certainly not a reason to abandon Ubuntu! Maybe if you post here what's wrong, someone can help you?

On a broader note, it's very possible that you will run into problems with Ubuntu, indeed with any Linux distro, that won't be instantly solveable. You'll probably need to use the terminal a few more times. I use the command line a lot, and not just for solving problems. It's a better, more powerful way of interacting with the computer, I think, far superior to the graphical interface for many purposes.

What I'm trying to say is, you're not using Windows now, you're using Linux. It's a different kind of operating system, and you have to do things differently. Accordingly, I feel you should have different expectations from it. If you use it right, it'll do everything Windows can, and more. But you have to be ready to learn new stuff, and to try new stuff. It won't just happen by itself.

---

### Post by KDOG2007 on 2006-04-24
Well, I guess I'm being a little hasty. I should just start from the beginning!

I have a computer that is NOT able to connect to the internet that I managed to get Ubuntu 5.10 loaded on. The specs are:
Asus TUSI-M (Sis 630) mobo, has onboard video only - which is fine with me
Celeron 1.3Ghz
128MB PC133 (soon to be 256Mb PC133)
8Gb Western Digital HDD
Lite-On DVD drive
56K modem

I guess what I need is a step-by-step set of instructions on how to get DVD playback enabled on the rig. Keep in mind that whatever software I need, I must download on my main rig then burn to a CD and then load it on.

By the way the link in your sig is very helpful.....

---

### Post by Rinzwind on 2006-04-24
Best thing you can do is download all needed packages and burn them.

- Add your cd-rom to your repository and install from cd (inside synaptic goto Settings/Repositories and click 'add cdrom').

- Before that you need to download some packages:

You need these for multimedia codecs:

gstreamer0.8-plugins
gstreamer0.8-lame
gstreamer0.8-ffmpeg
w32codecs
libdivx4linux
lame
sox
ffmpeg
mjpegtools
vorbis-tools

This for dvd playback:
libdvdcss2

And this for multimedia player:
xine-ui

(you can also use VLC, Totem and/or mplayer)

This guide helps alot:
[http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)


I think you could also download 4.6 Gb in packages and stuff it onto 1 dvd. I've seen people do that on these forums.

---

### Post by KDOG2007 on 2006-04-24
Thanks! Where a good place to get all those files? I'll go tweak Synaptic for cdrom now....

---

### Post by Rinzwind on 2006-04-24
I think that all files are stored here: [http://archive.ubuntu.com/ubuntu/pool](http://archive.ubuntu.com/ubuntu/pool)


But you can also use synaptic and store them on another ubuntu PC ;)

---

### Post by KDOG2007 on 2006-04-24
Well that didn't work either. I burned al the i386 deb files to a CD but when I go to add cdrom, it says its not a deb disk. I brought it back to my main rig to check it, and sure enough they were there. I don't understand what I'm doing wrong.

---

### Post by xiaoxin on 2006-05-02
No offence but i think it would be a good idea to start with a basic linux howto. After that try again.

---

